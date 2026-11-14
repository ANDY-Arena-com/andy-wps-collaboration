# ANDY App → Lab: Serienbetrieb, Evidence Builder und Experiment-Profile

**Stand: 14.11.2026 · V1.0 · Operative Übergabe an den Lab-Thread und App-Entwicklung.**

Leitprinzip: **GAME 4 LAB**. Arena erzeugt Aufmerksamkeit und Motivation für kontrollierte Experimente; das Lab untersucht die Daten. Transparente Forschungsabsicht, Datenaufbereitung strikt getrennt von Interpretation. Berechnung automatisieren, Deutung unterstützen, Erkenntnis offenhalten.

Diese Übergabe aktualisiert den Ist-Stand gegenüber der [Research Pipeline V0.1](ANDY_SERIES_RESEARCH_PIPELINE_SPEC_v0.1.md) und der [App-Übergabe vom 13.11.](ANDY_APP_8082_SERIES_HANDOFF_2026-11-13.md). Der [Evidenzvertrag](ANDY_MATCH_EVIDENCE_JSONL_JSON_SQLITE_v1.0.md) bleibt gültig. Masterplan und Lab CORE gelten weiterhin. Kein App-Quellcode und keine Rohprotokolle in diesem Dokumentationscommit.

## 1. Status und Entwicklungsstränge

- **8082 (Integration/Forschungsbetrieb):** produktive Partien, Serien, kontrollierte Rückkämpfe, Evidence-Export. Live-Resume-Pilot an einer echten Partie bestätigt. Neueste historische Rückkampfvorbereitung wird gerade vom Projektleiter getestet; Ausgang noch nicht bekannt.
- **8080 (Development):** Arena, Designer, Animationen; gemeinsame Archivdaten von 8082 ausschließlich lesend. Lokale Testpartien möglich, keine produktiven Schreibaktionen auf 8082-Daten. SYNC-02 und die späteren zielgetrennten Pakete sind bereitgestellt; vollständige lokale Installation und Browser-Abnahme auf 8080 müssen noch bestätigt werden. Auf 8080 keine produktive Live-Fortsetzung. Varianten und historische Rückkämpfe führen zum produktiven 8082-Pfad.
- **Lab-Thread:** Explorativer Forschungsstrang P2. Kein Umbau des Labs nötig, um ZIPs auszuwerten. P3 (halbautomatisierte Research Engine) erst nach methodischer Freigabe.
- **Verifikation:** "operativ bestätigt" bezeichnet beobachtete Screenshots/Terminalausgaben oder die Rückmeldung des Projektleiters. Patch-Tests liefen auf rekonstruierten Quellen, nicht sämtlich auf dem realen Mac. Die Dokumentation wurde gegen vorhandene Patch-READMEs, aktuelle Exportadapter und zwei tatsächliche Export-ZIPs geprüft. Keine Behauptung eines einheitlichen aktuellen App-Git-Commits.

## 2. Was die App inzwischen bietet

| Funktion / Paket | Bedienung und Verhalten | Abnahme |
|---|---|---|
| RESULT-02, SERIES-02/03 | Evidenzbasierte TKO-Zuordnung, bestätigte Serien vs. Farbtausch-Kandidaten; Serienübersicht, Replay-Verweise, Rückkampfvorbereitung | Auf 8082 eingesetzt |
| SERIES-07 | Durchsuchbare/sortierbare Fortsetzungsauswahl statt Dropdown; Filter nach Unterbrechung, Technik, Serie; Spielstand, Tokenbilanz, Offline-Prüfung | Browser auf 8082 bestätigt |
| SERIES-07B.1/B.2 | Rekonstruktion des Zustands, kumulierte Konten, korrekter nächster Spieler; explizite Startbestätigung, kein automatischer API-Aufruf; Live-Pilot auf konkrete Referenzpartie beschränkt | Astra–Claude tatsächlich fortgesetzt und beendet; generelle Live-Freigabe anderer Fälle offen |
| SERIES-07B.3 REV2 | Logischer Match-Resolver, generische lineare Fortsetzungsketten, Ergebnisprojektion in Serien und Leaderboard; widersprüchliche/verzweigte Ketten ohne neue Siegwertung | 11/11 Installer-Tests auf Mac; Serien-TKO und Leaderboard-Eintrag sichtbar |
| Evidence Builder | Einzelserien- und gemeinsamer Export aller bestätigten Serien, automatische Vorprüfung, Originaldateien + normalisierter Index | Zwei echte ZIPs erhalten und erneut verifiziert (Abschnitt 5) |
| RESEARCH QUEUE / RESEARCH-TODO | Sieben Forschungsaufträge; offene Paarungen dynamisch, vorhandene bestätigte Serien im geschlossenen Bereich „Bereits angelegt“; mehrere Serien einer Paarung zählen einmal | 8082 UI beobachtet; keine automatisch gestarteten Matches |
| SERIES-COMPARE-01 | Historische Partien vergleichen und ausdrücklich als Kategorie 2 verbinden; nachgewiesene Legacy-Überlappung berücksichtigen | Verknüpfung der 150k Astra–Argon-Serie vom Projektleiter bestätigt |
| SERIES EXPANDERS / DARK-01 | Alle vier Reiter kompakt, Expander default closed; Dark-Theme, stärkere Kontraste und Abstand zum Sidebar-Opener | 8082 Screenshots bestätigt |
| SYNC-02 | Selektiver Merge, GAME/LAB-Navigation, Schutz gemeinsamer Daten, Arena/Designer erhalten | 34 Tests in rekonstruierter Kopie; vollständige lokale Abnahme offen |
| SERIES-PROFILES-01 | Konfigurationsübergreifender Subcontainer im Serienreiter; gleiche Modellpaarung mit belegten unterschiedlichen Profilen, exakte Serien-ID, Vergleich nach Farbtausch | 32 Tests je Ziel laut Patch; kein eigenständiges Profilregister |
| SERIES-PROFILES-02 | Aus jeder Serie Konfiguration als Vorlage duplizieren/variieren; Dublettenprüfung vor bewusster Startfreigabe; neue eigenständige Serie nach Abschluss der Ursprungspartie | 44 Tests je Ziel laut Patch; echte Variantenstarts noch nicht allgemein abgenommen |
| SERIES-UX-01 | Kompakte Profilzeilen, rechts Details, unten Vergleichen/Neue Konfiguration; zentrales Serienmodal mit Partien, Profil, Evidenz | 48 Tests je Ziel einschließlich UI-Wiring; reales Modal auf 8082 sichtbar |
| SERIES-HISTORICAL-REMATCH-01 | Historische Serie mit eingefrorenen Konstanten gezielt erweitern; Auswahl ausschließlich ursprünglich belegter Werte; Regelversionhinweis und Backend-Prüfung | 60 Tests je Ziel laut Patch; Projektleiter testet aktuell, Live-Ergebnis offen |

**Bedienprinzip:** Übersicht draußen, Funktionalität im Modal. Alle neuen Serien sollen automatisch dieselben Aktionen erhalten. Forschungsplan = offene Aufgaben, Serien = vorhandene Versuchsreihen, konfigurationsübergreifender Subcontainer = unterschiedliche Profile der gleichen Modellpaarung. Kein zweiter redundanter Serienbestand. GAME / PLAY & WATCH: KI vs. KI, Replay, Leaderboard; LAB / RESEARCH: Serien, ANDY Lab; Experiment Designer später.

## 3. Datenmodell für die Analyse

Forschungsvorhaben → Versuchsprofile → Serien → logische Partien → technische Protokollsegmente. Das ist das konzeptionelle Modell, keine bereits implementierte relationale Profil-DB.

- Serien-ID ist die Wurzel-ID. Runde 0 = Original, anschließend rematch_index und Parent-Zuordnung. Bei Farbtausch wandern modellspezifische Einstellungen mit dem Modell.
- Eine technische Fortsetzung erhält eine eigene Match-ID. Die logische Partie behält ihre ursprüngliche ID, Serienrunde und Identität. Der letzte validierte Abschnitt liefert Ergebnis und kumulierte Ressourcen. Nicht Segmentabschlusskonten addieren!
- Bei einem normalen modernen Resume sind die Segmentereignisse getrennt und können für die Analyse in Kettenreihenfolge gelesen werden. Bei älteren Resume-Formaten können Originale überlappen; niemals pauschal konkatenieren oder Züge/Tokens doppelt zählen.
- Kategorie 2 = **historische, manuell bestätigte Forschungszuordnung**, nicht Nachweis gleicher Konfigurationen, vollständiger Ressourcen oder verifizierter Sieger. Kein Ausschluss von der Forschung. Nicht für unsichere Fälle Siegwerte erfinden. Die Kategorie wird im aktuellen Exportadapter in Manifest, Serienindex und derived-Index ausgewiesen.
- Reguläre Rückkämpfe behalten das Serienprofil. Historische Rückkämpfe verwenden nur ursprünglich bestätigte Wertesets, Konstanten gesperrt, Abweichungen hervorgehoben und per Auswahl (nicht Freitext) änderbar. Unbekannte Pflichtparameter oder Konflikte blockieren; nicht dokumentierte historische Regelversion wird nicht rückwirkend ergänzt. Aktuelle Regeln v1.1 müssen ausdrücklich bestätigt werden. Der Startserver validiert Quellhashes, Parent, Runde, Auswahl und aktuelle Archivlage erneut.
- Neue Konfiguration: dokumentiertes Profil als Vorlage, Modelle bleiben dieselbe Paarung; Variantenprüfung berücksichtigt auch Einzelpartien und bereits protokollierte Starts, Farbtausch und Self-Play. Identisches oder nicht sicher unterscheidbares Profil blockiert neuen Variantenstart; bestehende Serie öffnen. Neue Werte führen zur neuen Ursprungspartie, nicht zur Änderung der bestehenden Serie. Derzeit keine Freigabe unabhängiger Replikationsserien mit identischem Profil aus dem Variantenpfad.
- Historische Serienzuordnung im Sidecar `andy_series_confirmed_links.json`, Variantenwurzeln unter `runs/series_variant_roots/<match-id>.json` (hashgebunden). Diese Metadaten mit Archiv sichern. Keine Änderungen alter JSON/JSONL, keine neue Profil-DB; Leaderboard-Projektion ist lesend, keine SQLite-Migration. Historische Auswahlmetadaten werden im neuen Matchkontext protokolliert.

## 4. Export anfordern und verwenden

Auf **8082 → Serien**:
1. Gewünschte Serie aufklappen; rechts Details, Tab **Evidenz**.
2. Seriendaten exportieren; automatische Vorprüfung lesen und bewusst ZIP herunterladen.
3. Alternativ oben „Alle bestätigten Serien exportieren“. Offene Forschungsaufträge und unbestätigte Kandidaten sind keine bestätigten Serien. Bekannte laufende/unvollendete Starts werden als Ausschlüsse dokumentiert, soweit erkennbar.
4. Vor Weitergabe Originale manuell auf sensible Inhalte prüfen. Kein automatischer Upload. ZIP im Lab-Thread bereitstellen, nicht unkontrolliert öffentlich committen.

CLI aus dem Projektverzeichnis (explizite Auswahl einer oder mehrerer Serien, `--runs` optional; aktuelle Implementierung gelesen):
```bash
conda activate cair4_env
cd "$HOME/Documents/GitHub/cair4_andy_game_integration"
python -m andy.application.adapters.andy_series_export --series andy_1c77f49b3e17 andy_64c8f95436d1 --out "$HOME/Downloads"
```
Weitere bestätigte IDs können in derselben Liste mitgegeben werden. Auf 8080 das richtige Archiv explizit mit `--runs` wählen; UI nutzt den konfigurierten lesenden 8082-Pfad. Nicht unbesehen lokale Testdaten mit Forschungsdaten mischen.

### Tatsächliches Paketformat (Schema 1, Resolver 07B3-rev2)

```text
ANDY_SERIES_<UTC timestamp>.zip
  manifest.json
  audit.json
  README.md
  series/<series_id>/series.json
  matches/<segment_id>/<segment_id>.json
  matches/<segment_id>/<segment_id>.jsonl
  derived/matches.jsonl
```

| Datei | Verwendung |
|---|---|
| manifest.json | schema_version, export_id, exported_at, resolver_version, series, files mit SHA-256/byte_count/source_kind/status, privacy_policy. Manifest selbst nicht in seiner Prüfsummenliste. Neuere Revision ergänzt research_category je Serie. |
| audit.json | series_count, logical_match_count, segment_count, complete_pairs, warnings, coverage, privacy, sqlite_comparison, engine_verification |
| series.json | series_id, root_match_id, ordered_match_ids (logisch), matches, exclusions, warnings; neuere Revision research_category und historical_confirmations |
| matches/... | Originaldateien byteidentisch, technische IDs bleiben getrennt. Bei fehlenden/ungültigen/geblockten Quellen Status beachten. |
| derived/matches.jsonl | Eine Zeile je logischem Match/Serienmitglied; keine doppelte Zählung von Fortsetzungen. Als Einstieg in Analyse verwenden, Originale für Ereignis- und Brettanalyse. |

Wichtige Felder im normalisierten Index:
- Identität: series_id, logical_match_id, match_id, segment_ids (in Kettenreihenfolge), terminal_match_id, rematch_index, parent_match_id, rematch_group_id, membership_source, color_swap.
- Parameter: config, config_by_color, comparison_to_root, comparison_reasons, comparability_status, ruleset_version, engine_version, start_position_id. config enthält engine/strategy/token_budget/awareness/reasoning_effort je Farbe sowie x_go_moves, max_decisions, output_cap, max_illegal_retries. Konfiguration aus Wurzelbericht, Ergebnis/Konten aus terminalem Bericht. Model-Ausrichtung bei Self-Play oder asymmetrischen Profilen selbst nochmals prüfen; Exportvergleich ist noch kein vollständiger Fingerprint.
- Ergebnis: termination, runner_reported_result, resolver_verdict. Quellen getrennt halten. Unverifizierter TKO bedeutet nicht automatisch Sieg.
- Ressourcen: decisions, executed_moves, cumulative_api_ms, cumulative_local_ms, accounts (white/black mit budget, used_input, used_output, unknown_usage, decisions, legal_moves). Unbekannt ist nicht null Verbrauch. Abschlusszähler nicht addieren.
- Provenienz: coverage, engine_verification, segments mit Dateistatus, Hash/relativem Pfad, Segmentwarnungen, beobachteten Entscheidungs-/Ausführungszahlen, ggf. resume_from, Zeitstempeln und Segmentdauer. Neuere Revision: research_category, variant_source_series_id, bei belegter Legacy-Überlappung legacy_overlap, resource_accounting, counts_status. Letztere nicht für jeden Datensatz vorhanden; alte Exporte kennen diese Felder noch nicht.

**Was derzeit nicht exportiert wird:** normalisierte derived/events.jsonl, CSV, SQLite-Datenbank, unabhängige Engine-Rekonstruktion, komplette Profil-DB. Keine Annahme, dass schema_version oder resolver_version allein alle neuen optionalen Felder kennzeichnen; aktuelle Pakete prüfen.

### Automatische Vorprüfung und Grenzen

Datei-/ID-/JSON(L)-Prüfungen, Start-/Endrahmen, Ergebnisabgleich gegen Endereignis, Serienreihenfolge/Parent, Konfigurationsabdeckung und Farbtausch, Mehrfachzuordnung, Dateiänderung während Snapshot, heuristische Geheimnissuche und abschließende ZIP-Hashprüfung. Ein fehlender Rahmen wird bei historischen Partien nicht künstlich rekonstruiert. Fehler-/Warnstatus complete, partial, conflict, aggregiert complete oder partial_or_conflict; nicht mit wissenschaftlicher Gesamtqualität verwechseln. Ungültige Originale können als solche gekennzeichnet enthalten sein, sensible Verdachtsdateien werden blockiert. Vor Weitergabe menschlich prüfen. Keine Garantie der Geheimnisfreiheit. Vollständig fehlende, undokumentierte Serienstarts sind nicht automatisch erkennbar.

## 5. Reale Exportabnahme – 14.11.2026, vor Erweiterung auf vier Serien

Beide Original-ZIPs wurden in dieser Dokumentationsrunde nochmals geöffnet, ZIP-CRC geprüft und die SHA-256-Werte und Bytezahlen aller Manifest-Einträge neu berechnet.

| Export | Serien | Logische Partien | Segmente / Originalpaare | Hashes |
|---|---:|---:|---:|---:|
| ANDY_SERIES_20261114T154542187465Z.zip | 2 | 7 | 8 / 8 | 21/21 gültig |
| ANDY_SERIES_20261114T154556646525Z.zip | 1 | 4 | 4 / 4 | 12/12 gültig |

ZIP-SHA256:
- Mehrserie: `0894b5c2b1de73ef9b5d4fdb2881b37f9a826bb6e1eb397eebce70725d164405`
- Einzelserie: `08fd5ed13cb687f37abcbd50e0eb4904a2a1363b750f15b6e308347187fcd86a`

Beide Pakete melden partial_or_conflict wegen historisch fehlenden Start-/Endrahmens beim Ursprung andy_1c77f49b3e17 (142 Entscheidungsdatensätze, ausgeführte Züge im Index null). Das ist ein dokumentierter historischer Mangel, nicht automatisch ein defekter Export. Es erfolgte kein SQLite-Abgleich und keine unabhängige Brettrekonstruktion. ZIPs wurden nicht in GitHub hochgeladen; der Projektleiter übergibt sie nach Datenschutzprüfung an das Lab.

**Referenzfall moderne Fortsetzung:** Serie andy_64c8f95436d1 (Astra × Claude). Runde 1 bleibt andy_740a81fdbcc9; terminales Segment andy_b46041d24049. Original gestoppt nach 3 Entscheidungen/3 Zügen. Gesamt 249 Entscheidungen/237 ausgeführte Züge, Claude Weiß 351.618 von 350.000, Astra Schwarz 224.858; TKO zugunsten Astra (1.618 Überlauf). Neue Runde 2 andy_9d6c4f553b09 bleibt separat. Original und Runde 2 ebenfalls Astra-Siege, somit 3:0; keine Doppelwertung durch Resume. Serien- und Leaderboard-Eintrag operativ gesehen; vollständiger unabhängiger Abgleich aller Leaderboard-Zähler offen.

### Späterer sichtbarer Bestand (vor dem jüngsten historischen Testlauf)

| Serie | IDs | Bestand |
|---|---|---|
| Flash × Argon | andy_1c77f49b3e17 | 4 |
| Astra × Claude | andy_64c8f95436d1 | 3 |
| Argon × Astra, 350k | andy_cc11a6598bcf | 2 (zweite andy_0c0f7413fdf6) |
| Argon × Astra, 150k, Kategorie 2 | andy_83f51171e438 | 2 (zweite andy_93f0d66382aa) |

11 logische Partien in vier sichtbaren Serien; neuer gemeinsamer Export nach der Erweiterung nicht in dieser Dokumentationsrunde erhalten. Kein aktueller Bestandsanspruch während laufender Tests. Bei historischer 150k-Serie: Wurzel andy_83f51171e438 und terminaler Abschnitt andy_032f31d68743 mit nachgewiesener Log-Überlappung und unsicherer Tokenbilanz (zwei Originalsegmente, eine logische Partie). Kein verifizierter Sieger für diese Kette. Vergleich mit 350k: 150k je Seite, 300 Aufrufe, Output 2048 gegenüber 350k, 500, Output 4096; 4/5 Korrekturversuche innerhalb der 150k-Serie. Mehrere unabhängige Parameter unterscheiden sich, daher kein kausaler reiner Budgeteffekt ableitbar.

## 6. Forschungsplan und Analyseempfehlung

Sieben geplante Paarungen (Modellbezeichnungen wie in der App):
1. Astra × Argon: strategische Adaptivität, Ressourcenökonomie. Bereits zwei Serien angelegt, daher ein erledigtes Vorhaben.
2. Flash × Astra: Geschwindigkeit/Ressourcenökonomie vs. strategische Tiefe.
3. Argon × Opus: Interaktion verschiedener Modelle.
4. Flash × Opus: Ressourceneffizienz und strategische Nachteile.
5. Astra × Astra: Selbstähnlichkeit, Competitive Mirroring.
6. Argon × Argon: Selbstähnlichkeit, räumliche Muster.
7. Flash × Flash: Stabilität wiederkehrender Handlungsmuster.

Forschungsplan dynamisch: Eine bestätigte Paarung mit mindestens zwei logischen Partien und vorhandener Serienwurzel gilt als angelegt (auch Kategorie 2). Angelegt bedeutet nicht, dass Stichprobe oder Forschungsfrage abgeschlossen ist. Der vorläufige Startstandard für neue Paarungen: master, A2, default, 350k je Seite, max_decisions 500, Output 4096, max_illegal_retries 5, x_go_moves 1; vor Start prüfen. Kein Beleg, dass dieses Profil wissenschaftlich optimal ist.

**Auftrag Lab jetzt:** 
- ZIP und Quellhashes prüfen; logische IDs als Beobachtungseinheiten, Segment-IDs als Provenienz verwenden.
- Abdeckung/fehlende Werte und Quellenkonflikte getrennt von tatsächlichen Ergebnissen dokumentieren. Kategorie 2 separat stratifizieren, bei unklarer Ressourcenbilanz keine belastbare Effizienz- oder Siegerwertung.
- Innerhalb einer Serie wiederkehrende Go-Setup-Muster, Schachentwicklung, Ressourcen und Divergenzen untersuchen; Farben und Modellrollen normalisieren. Entscheidungen vs. ausgeführte Aktionen und Ausfälle unterscheiden.
- Zwischen Serien derselben Paarung unterschiedliche Parameter vergleichen; bei gleichzeitig veränderten Faktoren deskriptiv, keine kausale Zuschreibung.
- Cross-Model und Self-Play nur unter klar dokumentierten Vergleichsbedingungen. Kleine Stichproben, Modellversionen, technische Ausfälle, Provider-/API-Effekte berücksichtigen. Legalitätsprüfung alternativer Züge mit Engine, nicht allein Modellbegründung. Modelltexte sind Aussagen, keine inneren Gedanken.
- Erst nützliche Analyseverfahren und Visualisierungen im Chat erproben, danach für die App spezifizieren (P3). Pattern View und Analytical View gleichberechtigt. BEOBACHTET / BERECHNET / INTERPRETIERT / OFFEN trennen.

## 7. Nächster Architekturblock: Experiment Designer (TBD, nicht implementiert)

Dauerhaft versionierte Versuchsprofile als eigenständige Datenobjekte. Vorschlag für Entitäten: research_projects, experiment_profiles, series, series_members, match_segments. Relationen und Migration erst nach Prüfung des vorhandenen DB-Schemas. Originaldaten bleiben autoritativ. Kein derzeitiger Anspruch auf diese Tabellen.

- Profil duplizieren und exakt einen oder mehrere Parameter kontrolliert ändern. Bestehende Serie über ihre exakte ID öffnen/erweitern. Bei neuer Variante separate Serie. Geplante Profile nicht als gespielte Matches ausgeben.
- Vollständiger kanonischer Config-Fingerprint inklusive regel-/engine-/providerbezogener Parameter, modellspezifischer Einstellungen, Startposition und dokumentierter Versionsinformationen; Farbtausch normalisieren, Self-Play mit asymmetrischen Rollen korrekt behandeln. Unbekannt ≠ identisch. Bestehender Variantenvergleich prüft nur dokumentierte Pflichtparameter und Regelversion, kein vollständiger Fingerprint.
- Dublettenwarnung, bewusst unabhängige Replikation als späterer Sonderfall. Atomare Startreservierung/Idempotenz und Versionshistorie. DB- und Exportvertrag gemeinsam entwickeln.
- Grundprinzip: **Freeze the constants. Highlight the variables.** Historische Kategorie-2-Hinweise niemals durch neu gespielte Partien rückwirkend aufwerten.

## 8. Technische Orientierung / Installationshistorie

Wichtige Adapter unter `andy/application/adapters/`: andy_series_catalog.py, andy_logical_resume.py, andy_resume_chain.py, andy_series_export.py, andy_historical_series.py, andy_series_profiles.py, andy_variant_profiles.py, andy_historical_followup.py, andy_rematch.py, andy_research_series.py. UI: `andy/features/series/views/andy_series_ui.py`, Arena-Startpfad `andy/features/arena/views/andy_arena_ui.py`, Leaderboard-Projektion in dessen models/andy_arena_leaderboard_data.py. Gemeinsame Navigation im Shell-Code; aktuelle lokale Quellen vor Änderungen prüfen.

Lieferfolge (ZIP-Artefakte im App-Thread bzw. lokal beim Projektleiter, nicht Binärdateien dieses Repos): SERIES07_RESUME_PICKER → SERIES07B1_RESUME_RUNNER → SERIES07B2_REV2 → SERIES07B3_REV2_EVIDENCE → RESEARCH_QUEUE → SERIES_EXPANDER → SERIES_COMPARE → SERIES_EXPANDERS_ALL → SERIES_DARK01 → RESEARCH_TODO → SYNC02 → SERIES_PROFILES01 → SERIES_PROFILES02 → SERIES_UX01 → SERIES_HISTORICAL_REMATCH01. Letzte vier als zielgetrennte Pakete 8082/8080. Ersetzte erste B3-Revision nicht installieren. Nicht blind alle alten Patches erneut ausführen. Hash-/Ankerprüfung und Rollback bei Installerfehler; Backups behalten; cair4_env; keine laufenden Partien unterbrechen. Keine API-Anfragen bei Installation/Offline-Tests. Kein Hochladen von .env, DB, privaten Pfaden/Logs oder API-Schlüsseln.

**Arena-Parallelstrang:** Homepage V0.8.4.2 als visuelle Referenz. ARENA-01 Szene/Podium, ARENA-02 Web-SVG-Figuren, Hybrid-Corners, Provider-Logos, gespiegelte Anordnung, Alerts (66 % tatsächliche Brettbreite, mittig darunter, nur objektive Ereignisse). Installer ARENA-02 auf 8080 meldete fünf bestandene Smoke-Gruppen; abschließende Browser-Abnahme offen. Fight Card, Bewegung/Animation, Lichtwechsel, Alerts/Finale und Designer-Anbindung weiterentwickeln. SYNC-02 schützt diese Arbeit; keine kompletten App-Verzeichnisse überschreiben.

## 9. Offene Gates

- Aktuellen historischen Rückkampf live abnehmen (4/5 Auswahl, tatsächlicher Start und neu protokollierte Serienrunde), danach Export erneut prüfen.
- Neueste Pakete auf 8080 und 8082 lokal abgleichen; 8080 bleibt read-only gegenüber gemeinsamen Daten. Keine parallelen Starts derselben Reihe/Variante aus mehreren Browsern, derzeit keine atomare prozessübergreifende Startreservierung.
- Neue Variante live abnehmen; gemeinsamer Export des inzwischen erweiterten Bestands, einschließlich Kategorie 2 und Metadaten. Export der jüngsten Serie nicht bereits als real geprüft behaupten.
- Vollständige Engine-Rekonstruktion / unabhängiger SQLite-Abgleich und segmentübergreifendes Replay bleiben offen. Generalisierung der Live-Resume-Freigabe über den Pilot hinaus gesondert entwickeln. Historische unsichere Ketten nicht automatisch werten; weitere Legacy-Formate prüfen.
- Datenschutz/Providerbedingungen vor Veröffentlichung oder Trainingsdatennutzung prüfen. Keine Original-ZIPs aus diesem Auftrag öffentlich publizieren.
- Lab arbeitet jetzt mit den vorhandenen Exports; App kehrt nach Sync und Abnahme zur Arena zurück. Experiment Designer und P3 erst als eigenes Arbeitspaket.

**Kurzauftrag an den Lab-Thread:** Die Datenbasis ist verfügbar und exportierbar, einschließlich moderner Resume-Ketten. Prüfe zuerst die gelieferten ZIPs. Fordere weitere Serien und Profile gezielt anhand eines konkreten Analysebedarfs an. Keine allgemeine Theorie oder endgültige Modellbewertung aus diesen wenigen Partien ableiten.


## 10. Abnahme-Nachtrag 14.11.2026, 20:12 MEZ

Projektleiter meldet: Der historische Rückkampf auf 8082 lief vollständig durch und wurde korrekt in die bestehende Serie aufgenommen. Damit ist der konkrete Kategorie-2-Live-Referenzfall operativ bestätigt (Benutzerbericht; neues Originaldateipaar und Export noch nicht unabhängig geprüft). Auf 8080 ist SERIES-PROFILES-01 installiert, Terminalnachweis 32/32 Tests bestanden. Die drei Folgepakete PROFILES-02 → UX-01 → HISTORICAL-REMATCH-01 müssen dort noch bestätigt werden. Paketmanifeste geprüft: 8080-Zielkette konsistent, 32 erwartete Dateien einschließlich SYNC-02; historischer Rematch-Adapter hat seinen eigenen lokalen Vorversionshash. Kein produktiver Schreibzugriff auf gemeinsames 8082-Archiv. Arena- und Designer-Code bleiben separat. Dieser Nachtrag hat Vorrang vor den älteren Statusangaben zum konkreten historischen Live-Test.

## 11. SYNC-02 FINAL – technischer Abnahmecheckpoint (14.11.2026, abends)

**Status: technisch abgeschlossen; Browser-Abnahme auf 8080 noch offen.** Dieser Nachtrag ersetzt die offenen Installationspunkte in Abschnitten 9 und 10, nicht die noch ausstehenden unabhängigen Daten-/Engine-Prüfungen.

Terminalnachweise des Projektleiters auf dem lokalen Mac:

| 8080-Paket | Ergebnis |
|---|---|
| SERIES-PROFILES-01 | 32 passed |
| SERIES-PROFILES-02 | 44 passed |
| SERIES-UX-01 | 48 passed |
| SERIES-HISTORICAL-REMATCH-01 | 60 passed |
| CHECK_ANDY_8080_SYNC_FINAL.py | 32/32 erwartete Dateien bestätigt |

Die letzten drei Installer wurden im Environment cair4_env nacheinander erfolgreich ausgeführt und meldeten Backups sowie keine Änderungen an Originaldaten/DB und keine API-Aufrufe. Die Testzahlen sind aufeinanderfolgende Regressionsläufe, keine Summe unabhängiger Tests. Die abschließende 32-Dateien-Prüfung ist durch die Rückmeldung des Projektleiters bestätigt, nicht durch einen direkten Zugriff auf seinen Mac. Sie belegt den erwarteten Patch-Dateistand, nicht die Identität sämtlicher App-Dateien oder einen vollständigen Git-Merge.

### Arbeitsfreigabe und bewusst unterschiedliche Rollen

- **8082:** stabiler Forschungsbetrieb, Serien und Varianten spielen, kontrollierte historische Rückkämpfe, Evidence-ZIPs für das Lab. Konkreter historischer Live-Rückkampf erfolgreich und laut Projektleiter korrekt eingeordnet; neuer Export noch nicht unabhängig geprüft.
- **8080:** Arena-Entwicklung auf synchronisierter Serien-/Evidenzbasis. ARENA-01/02 und Designer nicht durch Gesamtverzeichnis-Kopie ersetzen. Gemeinsames 8082-Archiv ausschließlich lesend; Schreibaktionen/produktive Starts bleiben auf 8082. Lokale Testpartien getrennt halten.
- **Lab:** vorhandene und neue Evidence-Exporte explorativ auswerten; konkrete Forschungsprofile bei Bedarf anfordern. Serienverwaltung funktional vorerst einfrieren; Experiment Designer, persistente Profil-DB und weitergehende Forschungsautomatisierung separate Arbeitspakete.

### Nächster Schritt

8080 starten und Serienansicht (inkl. Detailmodals, Profile, Kategorie 2), Leaderboard, lesenden Archivzugriff sowie Arena visuell prüfen. Abweichungen gezielt beheben; laufende 8082-Partien nicht unterbrechen. Danach ARENA-02 visuell abnehmen, Fight Card, Figurenbewegung, gespiegelte Corners/Logos, objektive Alert-Zone (66 % Brettbreite), Licht/Finale und Designer-Anbindung entwickeln. Spätere Synchronisierung 8080 → 8082 nur selektiv nach Abnahme. Kein ungeprüfter Vollmerge.

**GAME 4 LAB: 8082 produziert Evidenz, 8080 entwickelt die Experience, das Lab entwickelt Erkenntnisverfahren.**
