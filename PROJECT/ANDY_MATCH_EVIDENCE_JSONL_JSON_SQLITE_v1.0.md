# ANDY 2.0 – Match-Evidenz: JSONL + JSON → SQLite → Replay, Rückkampf und Lab

**Version:** 1.0  
**Stand:** 13. November 2026  
**Status:** Technische Referenz / Integration in Arbeit; Audit nachgewiesen, produktiver Nachimport nicht bestätigt  
**Geltung:** ANDY App (8080 Entwicklung / 8082 Integration), Replay, Rückkampfserien, ANDY Lab, Archiv/Leaderboard, Forschungs-Exporte  
**Bezug:** [ANDY 2.0 Masterplan](ANDY_GESAMTKONZEPT_MASTERPLAN_v1.0.md) – Originaldaten unverändert, Evidenzstatus nicht verwischen.

> **Kernentscheidung:** Eine historische Partie ist kumulativ aus mindestens zwei komplementären Primärartefakten zu betrachten: dem Ereignisprotokoll `<match_id>.jsonl` und dem Matchbericht `<match_id>.json`. SQLite ist eine **nachvollziehbare Projektion** dieser Quellen, kein unabhängiger Beweis und keine konkurrierende historische Wahrheit. Weder fehlende Event-Zeilen noch historische Parameter dürfen erfunden werden.

## 1. Rollen der Dateien

| Artefakt | Zuständigkeit | Evidenzstatus |
|---|---|---|
| `runs/<match_id>.jsonl` | Pro API-Entscheidung: Modellantwort, versuchter und ausgeführter Zug, Fehler/Retry, Tokenverbrauch, Zeitstempel und beobachteter Zustand; bei vollständigen neueren Logs auch `match_start`/`match_end` | Primärquelle für tatsächliche Ereignisse |
| `runs/<match_id>.json` | Matchkonfiguration, beide Modellzuordnungen, Strategien, Budgets, Awareness, Reasoning, Regeln, Limits, Laufzeit und **vom Runner berichtetes** Ergebnis | Primärquelle für Konfiguration und Runner-Abschluss |
| `andy_v2_shadow.db` | Indexierung, Zuordnung und Projektion für Replay, Archiv, Rückkampf und Lab; zusätzliche Herkunfts-/Evidence-Daten | Abgeleitete, überprüfbare Arbeitsdatenbank |
| Spätere Engine-Verifikation | Rekonstruktion mit passender historischer Ruleset-/Engine-Version | Separate Validierungsstufe, nicht aus dem Bericht allein ableitbar |

**Dateipaar-Regel:** Zu einer Match-ID die beiden Dateitypen suchen und zunächst gemeinsam prüfen; einen fehlenden JSONL-Endeintrag nicht durch einen erfundenen `match_end` ersetzen. Fehlt eine Quelle, den Mangel sichtbar dokumentieren.

## 2. Konkreter Fall: `andy_1c77f49b3e17`

**Original vom 3.11.2026:** Gemini 3.8 Flash (Weiß) gegen Gemini 4 Argon (Schwarz).

- Die vorhandene JSONL hat **142 `decision`-Events**, davon **70 Weiß / 72 Schwarz**; sie enthält **kein `match_start` und kein `match_end`**.
- Der zusätzlich wiedergefundene originale Matchbericht `.json` enthält die komplette `config`:
  - `engine_white = "Gemini 3.8 Flash"`, `engine_black = "Gemini 4 Argon"`
  - `strategy_white/black = master`, `reasoning_effort_white/black = default`, `awareness_white/black = A2`
  - `token_budget_white/black = 100000`
  - `max_decisions = 300`; `max_illegal_retries = 4`; `output_cap = 2048`; `x_go_moves = 1`
- Der Bericht enthält `termination = "game_over"` und `game_result = "Schwarz gewinnt durch Kontrolle (72 ≥ 72)"`; `decisions = 142`. Das ist ein **zeitgenössischer Runner-Bericht über einen Go-Sieg**, jedoch **noch keine unabhängig engineverifizierte Rekonstruktion**.
- Die Original-JSONL dokumentiert `output_cap_requested = 2048` in allen 142 Entscheidungen. Der bisherige SQLite-`load_replay`-Pfad liefert dafür `None` in 142/142 Fällen. **Nicht fehlende Ursprungsdaten mit einem Verlust im Import-/Projektionspfad verwechseln.**

**Bedeutung:** Die vollständige Originalkonfiguration ist mit dem Fund der `.json`-Datei **nicht mehr unbekannt**. Der zuvor geplante historische Bootstrap mit geratenen/neu festgelegten Parametern ist für dieses Match nicht mehr der bevorzugte Pfad. Die Nachintegration beider Originalquellen hat Vorrang.

### Belegter REMATCH-10-Audit vom 13.11.2026

Auf 8082 mit den Originaldateien im `runs/`-Ordner wurde der schreibgeschützte Abgleich durchgeführt:

- **3/3** Regressionstests von `evidence_sync.py` erfolgreich (Dry Run, idempotenter Apply-Test, Widerspruchssperre).
- Aktive Datenbank laut Audit: `~/Documents/ANDY_2_TEST_DATA/ANDY_8082_eyuqut1_/andy_v2_shadow.db`. Dies ist ein **historisch beobachteter Pfad**, kein fest einzubauender Standard.
- `JSONL SHA256 = e33932b3a66437aeeaa740f83aa73ea4604faff8282ac5ff82c4a5bcfbe5ed23`
- `JSON SHA256 = 1dd022c81b0eb7f6113188bb2e24789b52025acf86ace362bfdf085404702610`
- `sqlite_event_count = 142`; `jsonl_has_match_start = false`; `jsonl_has_match_end = false`.
- Audit-Ausgabe: **`AUDIT OK. Keine Dateien veraendert. Zur Uebernahme: --apply`**.
- **Kein bestätigter produktiver `--apply`-Lauf** im bislang vorliegenden Dialog. Screenshots mit fehlenden Werten belegen keine erfolgreich erfolgte Evidence-Projektion in Replay.

## 3. Importvertrag – REMATCH-10

**Ablauf:** `--audit`/Standard-Dry-Run → Prüfung → explizites `--apply` bei gestopptem 8082-Server → Backup → Transaktion → Verifikation → UI-Anbindung gesondert.

1. **Originaldateien unverändert** einlesen, SHA-256 je Datei berechnen und Quellenherkunft hinterlegen.
2. **Konsistenz** prüfen: identische `match_id`, Modelle/Seiten, Entscheidungszahlen, relevante Token-/Zeitangaben und vorhandene Archiv-Event-Zahlen. Bei Fehlern fail-closed, kein best-effort-Überschreiben.
3. Vollständige `config` aus dem **Matchbericht** als `report_documented` erfassen, beobachtete Event-Felder aus JSONL als `event_documented`. Gleiche Werte aus beiden Quellen bestätigen sich; bei Abweichungen Konflikt protokollieren.
4. Zusatz-Evidence **separat** in SQLite speichern, mit Rohquellen-Hash, Match-ID, Datum und Importwerkzeug/Schema-Version; bestehende Replay-Ereignisse und bestehende Wertungen nicht stillschweigend umschreiben.
5. Ergebnistext des Matchberichts getrennt führen als `runner_reported`; ein unabhängiger Engine-Nachweis setzt eigene Provenienz/`engine_independently_verified` voraus.
6. **Idempotenz**: dieselben Quellen erneut importieren erzeugt keine doppelten Evidence-Einträge; geänderte Quelldateien bei gleicher Match-ID erfordern explizite Revision/Konfliktklärung.
7. Vor jeder Datenbankmutation Backup, ausschließlich erwartete Tabellen, explizite Transaktion, nachvollziehbare Audit-Ausgabe und Rollbackmöglichkeit.

**Status:** Der Audit und die isolierten Tests sind nachgewiesen. **Der Import in die aktive 8082-Datenbank und die Nutzung der Evidence-Tabellen durch die Arena-UI sind noch nicht als abgeschlossen bestätigt.** Namen, genaue Spalten und Migrationen der Evidence-Tabellen sind vor produktiver Schema-Veröffentlichung am tatsächlich eingesetzten `evidence_sync.py` zu verifizieren.

## 4. Replay – allgemeiner Lesevertrag (REMATCH-10B, noch umzusetzen)

Beim Laden einer Partie sollten die Views einen gemeinsamen **Match-Facts-Resolver** benutzen:

1. Vollständigen `match_start.config`, falls vorhanden und konsistent, lesen.
2. Dokumentierten `.json`-Matchbericht mit Quelle/Hash ergänzend heranziehen (auch wenn `match_start` in JSONL fehlt).
3. Ereignisfelder aus JSONL/SQLite für beobachtete Zug- und Tokeninformationen nutzen; bei fehlender SQLite-Projektion nicht behaupten, dass das Ursprungsfeld fehlt.
4. Für jeden angezeigten Fakt **Wert + Quelle + Nachweisstatus** verfügbar halten. Nie durch UI-Defaults eine historische Einstellung „vervollständigen“.
5. **Ergebnisanzeige differenzieren:** `runner_reported`, `engine_independently_verified`, `unverified`, `conflict`. Ein Runnerbericht darf als solcher angezeigt werden, aber nicht als unabhängiger Engine-Beweis etikettiert werden.
6. Das **schreibgeschützte Replay-Konfigurationsmodal** zeigt vor dem Start die tatsächlichen Bedingungen (Weiß/Schwarz, Strategie, Reasoning, Awareness, Budgets, Output-Cap, Retries, Go-Gruppe, Ruleset, maximaler KI-Aufruf). „Replay starten“ spielt lediglich historische Daten ab.
7. Alte Replay-Formate ohne vollständige Quellen bleiben ladbar; fehlende Felder ausdrücklich kennzeichnen.

**Keine automatische KO-Wertung aufgrund eines fehlenden JSONL-`match_end`** allein aus einer Modelläußerung. Eine spätere, separat geregelte Wertung aufgrund eines überprüften Originalberichts benötigt explizite, fachlich freigegebene Provenienzregeln.

## 5. Rückkampfserien – gleiche Evidenzbasis

- Ein Rückkampf ist immer **eine neue Partie vom regulären Startzustand**, keine Fortsetzung und keine Manipulation des Ursprungsspiels.
- Historische Konfiguration aus dem zugeordneten Original-JSON/JSONL-Paar übernehmen; modellgebundene Felder (Modell-ID, Strategie, Reasoning, Awareness, Tokenbudget) beim Farbtausch **mit dem Modell** verschieben. Globale Limits und Regeln konstant halten.
- Im neuen `match_start` und Matchbericht dokumentieren: `match_id`, `parent_match_id`, `rematch_group_id`, `rematch_index`, `color_swap`, **tatsächlicher** `config_snapshot`, `comparability_status` sowie nachweisbare Versionen von Engine, Ruleset und Adapter.
- Mehrere Rückkämpfe behalten dieselbe `rematch_group_id`, der Parent verweist jeweils auf den unmittelbar vorherigen Match. Neue API-Calls erst nach aktiver menschlicher Bestätigung.
- **Vergleichbarkeit:** `controlled_color_swap` nur bei tatsächlich belegter Gleichheit aller relevanten Einstellungen **und** hinreichender Versions-/Umgebungsmetadaten; bei Parameteränderung `modified_configuration`, bei fehlender Versions-/Umgebungsinformation `incomplete_metadata`. Das Vorliegen einer historischen `config` allein beweist keine identische Provider-Modellversion.
- Für `andy_1c77f49b3e17` jetzt Originalwerte verwenden: **300 / 4 / 2048 / Go-Gruppe 1 / 100.000 je Modell**. Das ersetzt die bisherige Pflicht, diese Werte für eine Bootstrap-Serie erst zu raten; technische Serienfreischaltung aus Evidence ist noch ein Folgeschritt.

## 6. Lab / Exporte / Ergebnissemantik

Eine gemeinsame Datenprojektion soll bereitstellen:

- Ursprung je Feld (Original-JSONL, Originalbericht, importierte Evidence-Tabelle, engineverifizierte Rekonstruktion);
- Spielbeleg `decision`, tatsächlicher `executed`-Status, Modellbegründung als **Aussage**, keine faktische Endautorität;
- `KO_CHESS`, `KO_GO`, `TKO`, `ABORT` als **zusätzliche** fachliche Klassifikation, rückwärtskompatibel zu bisherigen `termination`-/`game_result`-Feldern;
- Runnerbericht vs. Engine-Verifikation getrennt, keine implizite Gewinnerwertung ohne dokumentierte Beleg- und Freigaberegeln;
- Serien-ID/Parent/Index für spätere aggregierte Auswertung, ohne sie mit strategischer Kausalität oder Modellleistung gleichzusetzen.

## 7. Betrieb / Testabnahme

**Vorhandenes Paket:** `ANDY_REMATCH_10_EVIDENCE_SYNC` enthält `evidence_sync.py` und `test_evidence_sync.py`, im Entwicklungsdialog unter `~/Downloads/` entpackt.

Beispiel für den nachgewiesenen **Nur-Lesen-Audit** (Pfad zur aktiven DB bei jedem Lauf verifizieren):

```bash
cd ~/Documents/GitHub/cair4_andy_game_integration
python ~/Downloads/ANDY_REMATCH_10_EVIDENCE_SYNC/evidence_sync.py \
  --db "$HOME/Documents/ANDY_2_TEST_DATA/ANDY_8082_eyuqut1_/andy_v2_shadow.db" \
  --jsonl "runs/andy_1c77f49b3e17.jsonl" \
  --report "runs/andy_1c77f49b3e17.json"
```

**Abnahmekriterien für REMATCH-10/10B:**

1. Audit beider Originaldateien erfolgreich; Prüfsummen und Quellen-ID gespeichert.
2. Import nur nach bestätigtem `--apply`, Sicherung und Datenbank-Konsistenzprüfung; Reimport idempotent.
3. Replay-Fight-Card bezieht die vollständige historische Konfiguration nachweisbar aus der zusammengeführten Evidenz; keine „Nicht dokumentiert“-Felder, wenn der Originalbericht den Wert enthält.
4. Der historische Go-Sieg wird als **Runnerbericht** sichtbar, die unabhängige historische Engine-Verifikation als offen.
5. Rückkampf übernimmt exakt die bekannten Settings, vertauscht modellspezifische Werte und erzeugt neue Serie mit prüfbaren IDs; kein API-Aufruf beim bloßen Öffnen.
6. Neue und alte Matches, technische Abbrüche und bisherige Schachmatt-Wertungen bleiben ohne Regression.
7. **Kein Überschreiben** von `.env`, `runs/`, JSONL/JSON-Primärquellen, `andy.db`, Designfreigaben, Git-Metadaten oder produktiven Daten außerhalb der ausdrücklich bestätigten Evidence-Tabellen.

## 8. Offene Entscheidungen

- Einheitliche technische Schema-/API-Definition des Evidence-Resolvers und konkrete SQL-Tabellen am laufenden App-Code verifizieren.
- Batch-Audit für **alle** verfügbaren JSONL+JSON-Dateipaare; fehlende Paare und Konflikte separat ausweisen, nicht verstecken.
- Sichtbare Revisions-/Provenienzlabels in Replay, Lab, Leaderboard und Export.
- Historische Ergebniswertung aus Runnerberichten nur nach festgelegter, dokumentierter Evidenzpolitik.
- Serienansicht und kontrollierte Mehrfachversuche später; zunächst einzelne Rückkämpfe und sichere Datendurchgängigkeit.

---

**Leitsatz:** **JSONL + JSON = gemeinsame historische Match-Evidenz. SQLite = reproduzierbare Projektion. Replay, Rückkampf, Lab und Journal müssen dieselben belegten Fakten lesen.**
