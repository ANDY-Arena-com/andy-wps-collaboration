# ANDY 2.0 – SERIES-03: Serienverwaltung in der Sidebar
**Technisches Implementierungsmemo v0.1 · 13. November 2026**  
**Status:** Entwurf / zur Implementierung; **noch kein installierter Sidebar-Patch**  
**Geltung:** 8082 (Integration), anschließend 8080 (Entwicklung), Replay, Rückkampf, Matcharchiv, Lab  
**Grundlage:** [ANDY Match-Evidenzvertrag JSONL + JSON → SQLite](ANDY_MATCH_EVIDENCE_JSONL_JSON_SQLITE_v1.0.md) und [ANDY Masterplan](ANDY_GESAMTKONZEPT_MASTERPLAN_v1.0.md).

> **Entscheidungsvorschlag:** Ein eigenständiger Sidebar-Eintrag **„Serien“** führt zu einem Multi-Play Control Center. Einzelspiel und Replay bleiben separat; Serien sind der Ort für zusammenhängende Partien, bestätigte Beziehungen, Farbtausch-Kandidaten, Ergebnisvergleiche und die Vorbereitung weiterer Rückkämpfe.

## 1. Anlass und gesicherter Ausgangspunkt

Der Nutzer hat mit SERIES-02 einen schreibgeschützten Bericht aus dem `runs`-Archiv vorgelegt: **98 Matchberichte**, **2 explizite Serien** inklusive Ursprungspartie (Runde 0) und **25 unbestätigte Farbtausch-Kandidaten**. Die Berichte belegen das gewünschte Konzept, aber noch **keine integrierte NiceGUI-Serienseite**.

**Explizite Referenzen:**
- `andy_1c77f49b3e17` (Gemini 3.8 Flash weiß / Gemini 4 Argon schwarz; Runnerbericht: Argon gewinnt durch Go-Kontrolle 72 ≥ 72) → `andy_b94759f1b232` (Argon weiß / Flash schwarz; `budget_overshoot` des weißen Argon, TKO zugunsten des schwarzen Flash nach ANDY-Wertung).
- `andy_64c8f95436d1` (OpenAI Astra weiß / Claude Opus 5.5 schwarz; Schachmatt für Weiß) → `andy_740a81fdbcc9` (Farben vertauscht, `user_stopped`).
- Historische Astra–Argon-Farbtausch-Kandidaten: `andy_cc11a6598bcf` (Argon weiß / Astra schwarz; Astra gewinnt durch Matt) und `andy_0c0f7413fdf6` (Astra weiß / Argon schwarz; Astra gewinnt durch Matt). **Gleiche Paarung und Farbtausch beweisen keine explizite Rückkampfbeziehung.**

**Wichtige Defizite:**
1. SERIES-02 schreibt beim Gemini-Rückkampf noch `budget_overshoot · TKO-Verursacherprüfung offen`, obwohl der konkrete Verursacher für diesen Match bekannt ist.
2. Bereits explizit mit einer Serie verknüpfte Matches werden nochmals als mögliche Kandidaten anderer Serien ausgegeben; explizite Zuordnung muss Vorrang haben.
3. Der bestehende Archiv-/Replay-Bereich bietet noch keinen eigenen, direkten Serienaufruf.
4. Gleichzeitige *Verwaltung* mehrerer Serien ist nicht identisch mit technisch paralleler *Ausführung* mehrerer Match-Runner.

## 2. UX: ein eigener Sidebar-Eintrag

Im gemeinsamen ANDY-Shell-Navigationsmenü einen einzigen Eintrag **Serien** (Icon z. B. `account_tree`) ergänzen. Separat bleiben **Arena**, **Archiv / Replay**, **Lab**. Keine weiteren redundanten Sidebar-Einträge für „Rückkämpfe“, „Testreihen“ oder „Experimente“.

**Seite /series – Multi-Play Control Center:**
- Übersicht über bestätigte Serien, aktive/geplante Serien, historische Zuordnungskandidaten;
- Suche nach Match-ID, Modell und Serien-ID; Filter aktiv/historisch;
- je Serie: eindeutige Serien-ID, **Ursprung als Runde 0**, chronologische Rückkämpfe mit Index, Weiß/Schwarz, Endtyp, Sieger, Quellen-/Verifikationsstatus, Vergleichbarkeitsstatus;
- je Match: **Replay öffnen** (direkter validierter Match-ID-Einstieg);
- je Serie: **Nächsten Rückkampf vorbereiten** (bestehender Rematch-Flow, Farbtausch und unveränderte modellgebundene Einstellungen; **kein API-Aufruf** beim Vorbereiten);
- historische Kandidaten anzeigen und getrennt **manuell bestätigen**; kein automatischer Schreibvorgang beim Seitenaufruf;
- Status `geplant`, `läuft`, `beendet`, `abgebrochen`, `prüfbedürftig`, mit tatsächlichem Laufstatus aus dem Runner und nicht aus bloßer Dateiexistenz.

Die visuelle Darstellung nutzt die vorhandene Arena-Shell einschließlich responsive Themes. Das frühere Chat-UI-Modell war ausdrücklich ein **Konzept**, kein laufender NiceGUI-Screen.

## 3. Technischer Aufbau (vorgeschlagene Dateien, vor Umsetzung prüfen)

```text
andy/application/adapters/
    andy_rematch.py                 # vorhanden, wiederverwenden
    andy_match_evidence.py         # vorhanden, wiederverwenden
    andy_series_catalog.py         # neu: Serien- und Kandidaten-Resolver
    andy_result_resolver.py        # neu/vereinheitlichen: KO/TKO/Abbruch
andy/features/series/
    controllers/andy_series_controller.py
    views/andy_series_ui.py
andy/infrastructure/persistence/
    andy_series_repository.py
andy/presentation/shared/shell/
    [bestehende Navigation gezielt erweitern]
```

Die Pfade sind **Implementierungsvorschläge**; die aktuelle Navigation und der tatsächliche Branch-/Dateistand von 8082 und 8080 müssen vor Patch-Erstellung geprüft werden.

**Routenvertrag:** Seite unter `/series`, analog zum bestehenden Replay-Registrierungsmuster (NiceGUI `@ui.page` / vorhandener Installer / `create_game_shell(...)`, abhängig vom realen Quellstand). Sidebar-Eintrag ausschließlich über den zentralen Navigationsbuilder. Direkter Replay-Einstieg konzeptionell `/replay?match_id=<ID>`; Parameter validieren, Datensatz laden, sonst verständliche Fehlermeldung. Bestehende manuelle Archivauswahl bleibt intakt.

**Datenpfad:** `runs/<match_id>.jsonl` + `runs/<match_id>.json` → SQLite-Evidence/Archiv → gemeinsamer Series Catalog & Result Resolver → NiceGUI, HTML-/JSON-Export, Lab. **Keine separate Ergebnislogik im UI.** Der standalone `series_registry_v2.py` liefert die Ausgangslogik, wird aber nicht bei jedem Seitenaufruf als HTML-Generator ausgeführt.

## 4. Einheitliche Ergebnisauswertung – RESULT-02 als Abhängigkeit

- Die rote TKO-Cockpit-Anzeige von `andy_b94759f1b232` gilt als korrekte Referenz: **Weiß Argon überschritt 100.000 Tokens um 275; Schwarz Flash gewinnt durch TKO**.
- `budget_overshoot` ist ein technischer Terminationscode; sportliche Gewinnerzuordnung wird mit belegtem Verursacher und geltender TKO-Regel **abgeleitet**, nicht in die Original-JSON/-JSONL zurückgeschrieben.
- `illegal_retries_exhausted` und `output_limit_retries_exhausted` fachlich gemäß den tatsächlichen Regeln prüfen und Verursacher aus Events belegen; bei unklarer Beweislage keine erfundene Gewinnerseite.
- `unknown_token_usage`, `user_stopped`, `max_decisions` und `model_or_move_error` nicht pauschal in TKO umdeuten.
- Schachmatt- und Go-Resultate erhalten; **Runnerbericht** vs. **unabhängige Engine-Verifikation** unterscheidbar anzeigen.
- Cockpit, Endmodal, Replay, Leaderboard, Serienregister und Lab müssen denselben zentralen Resolver verwenden.

## 5. Datenhaltung für historische Serienzuordnung

Automatisch übernommene Verbindungen brauchen nachweisbare `parent_match_id`, `rematch_group_id`, `rematch_index`, `color_swap`, vorzugsweise aus den originalen Match-Start-/Matchberichten. Diese haben Vorrang vor bloßer Paarungs-/Farbähnlichkeit.

Für **nachträglich manuell bestätigte** Beziehungen eine **additive SQLite-Tabelle** vorsehen, z. B.:

```sql
CREATE TABLE IF NOT EXISTS match_series_links (
    match_id TEXT PRIMARY KEY,
    series_id TEXT NOT NULL,
    parent_match_id TEXT,
    series_index INTEGER,
    link_status TEXT NOT NULL,
    confirmed_at_utc TEXT,
    evidence_note TEXT
);
```

Dazu Transaktions-/Auditlog und Validierung: keine Mehrfachzuordnung, keine Zyklen, keine ungültigen Parent-IDs, eindeutiger Index je Serie, explizite Bestätigung. Dies ist ein **Schemaentwurf**, noch keine freigegebene Migration. Bestehende Matchdatenbank, `runs/`, JSONL und JSON bleiben historisch unverändert.

Serienzugehörigkeit und wissenschaftliche **Vergleichbarkeit** getrennt bewerten: Farbtausch allein beweist keine identische Modell-/API-/Regelversion.

## 6. Parallelität: Verwaltung ≠ Ausführung

Die Serienansicht darf mehrere geplante oder laufende Serien gleichzeitig darstellen. Technisch parallele API-Matches erfordern unabhängige Runner-Zustände, Budgets, Logs, Lifecycle, Error-Handling, Isolation und Stop-/Resume-Berechtigungen. **SERIES-03 verspricht keine automatische parallele Matchausführung.** Neue kostenpflichtige Läufe stets einzeln durch den Benutzer auslösen.

## 7. 8082-Abnahme und kontrollierte 8080-Synchronisation

**Reihenfolge:**
1. **8082 Baseline:** Branch, Git-Status, SHA-256 der realen Shell-/Navigation-, Replay-, Rematch-, Ergebnis- und Datenzugriffsmodule erfassen; laufende API-Spiele nicht durch Neustart gefährden.
2. **RESULT-02 abschließen:** zentrale Ergebnissemantik anhand echter JSON/JSONL und Regressionstests belegen.
3. **SERIES-03 implementieren:** gemeinsamen Catalog und Repository, `/series`-Route, Sidebar-Link, direkte Replay-Auswahl und Rematch-Vorbereitung; Kandidatenkorrektur (bekannte Zuordnung vor Vorschlag).
4. **8082 Abnahme:** Gemini, Astra–Claude, historische Astra–Argon-Kandidaten, ungeklärte TKOs, Go/Matt, `user_stopped`, fehlende Dateien, doppelte IDs; keine API-Aufrufe beim Seitenaufruf.
5. **8080 Sync:** **nur freigegebene Code-, Test- und Schemaänderungen** nach SHA-/Diff-Abgleich übertragen; keine pauschale 8082-Dateikopie und **keine Datenbank-/runs-Synchronisation**. Lokale Änderungen, Themes, Designerfreigaben und Git-Metadaten schützen.
6. **Beide Umgebungen prüfen:** Tests getrennt auf 8082 und 8080; Sidebar, Replay-Direktaufruf, Rematch-Preflight, Ergebnisdarstellung und Rollback.

**Abnahmekriterien:** Sidebar „Serien“ auf 8082 und 8080; Gemini-Ursprung Runde 0 plus TKO-Runde 1; Astra–Claude-Matt plus manuell abgebrochener Rückkampf; Astra–Argon als **unbestätigter** historischer Kandidat; Replay je Match-ID; nächster Rückkampf zunächst nur vorbereitet; einheitliche TKO-Anzeige; Originalquellen unangetastet.

## 8. Umsetzungsstatus / nächster Auftrag

- **Vorhanden und beobachtet:** SERIES-02-HTML/JSON-Register mit 98 Berichten, zwei expliziten Serien, 25 Kandidaten; Evidence-Integration für Gemini-Original; funktionierender Farbtausch-Rückkampf.
- **Noch ausstehend:** Ergebnis-Resolver für das gesamte Archiv, echter NiceGUI-Sidebar-Button, Serienroute, manuelle Bestätigungsdatenbank, Direktnavigation, Tests an beiden aktuellen Codebasen.
- **Nächster technischer Auftrag:** aktuelle 8082-/8080-Shell, Replay- und Rematch-Dateien SHA-geschützt abgleichen; RESULT-02 + SERIES-03 auf 8082 integrieren, visuell abnehmen; anschließend **SYNC-01** nach 8080.

**Architekturleitsatz:** **Eine Serienzugehörigkeit ist eine belegte Beziehung zwischen unveränderlichen historischen Partien – keine neue Geschichte, die wir in die alten Logs hineinschreiben.**
