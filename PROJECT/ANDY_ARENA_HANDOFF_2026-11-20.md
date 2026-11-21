# ANDY 2.0 — Übergabe Arena / Studio, 20.11.2026


> **⚠️ AKTUELLER OBSERVER-STAND 21.11.2026 (BIS ORIENTATION19) — BEI NEUEM THREAD ZUERST LESEN:** [ANDY_OBSERVER_STATUS_HANDOFF_2026-11-21.md](./ANDY_OBSERVER_STATUS_HANDOFF_2026-11-21.md). Observer ist inzwischen ein direkt in Sandbox **8082** integriertes, stabiles **iframe-Research-Werkzeug** mit Replay Pulse/Inspector, Home/Modi, klickbarem Marker→Replay/Brett, 13×13-Geometry, Mirror-Alerts und Spiegel-Stilen für **wenige Steine / große Flächen**. Letzte Fixkette **MIRROR16 → STYLES17 → ORIENTATION18 → ORIENTATION19** (Orientierung des Mini-Bretts; expliziter Umkehr-Browsertest noch offen). **Keine 8080-/8083-Freigabe, keine Signifikanz-Bestätigung der Spiegelverdachtsfälle!** Die funktionierende iframe-Architektur nicht wieder ersetzen. Originaldateien nur mit SHA-Check anfassen; siehe separates Statusdokument.


> **⚠️ PFLICHT-UPDATE 21.11.2026 — VOR JEDEM NEUEN THREAD UND SYNC LESEN:** Der fehlende **neue Start-Launcher auf Studio 8080 ist BEHOBEN und per Browser-Screenshot bestätigt**. Ursache war eine **in beiden Instanzen identische** `pilot`-Feature-Gate-Bedingung in `andy_v1_shell.py`, die nur `sandbox:8082` zuließ. STUDIO-LAUNCHER-01 hat das Gate **ausschließlich in Studio 8080** für `studio:8080` ergänzt; Factory 8083 bleibt ausgeschlossen. **Die Studio-Shell-Datei deshalb keinesfalls blind von 8082 überschreiben!** Die vollständige App-Regressionsabnahme ist weiter **OFFEN**. **Verbindliche Fallanalyse und zukünftige Release-Gates:** [ANDY_SYNC_FEATURE_GATE_CASE_2026-11-21.md](./ANDY_SYNC_FEATURE_GATE_CASE_2026-11-21.md); [ANDY_DEVELOPMENT_REGRESSION_POLICY_2026-11-21.md](./ANDY_DEVELOPMENT_REGRESSION_POLICY_2026-11-21.md).

## Auftrag für den nächsten Thread
LAB-SYNC-01 vorbereiten und durchführen, nachdem der finale Codeabgleich 8082 → 8080 bestätigt wurde. Keine erneute Arena-Neugestaltung. Der Nutzer hat die wiederholten Regressionen und eigenmächtigen Änderungen ausdrücklich beanstandet. Nur konkret beauftragte Änderungen, minimale Diffs, keine neuen Overlays oder Refactorings ohne Freigabe. Praktische ausführbare Batches statt wiederholter Absichtserklärungen.

## Instanzen und Grenzen
- 8082 Sandbox: ~/Documents/GitHub/cair4_andy_game_integration
- 8080 Studio: ~/Documents/GitHub/cair4_andy_game_ui
- 8083 Factory: nicht anfassen.
- conda activate cair4_env. Vor Codeinstallation laufende Partien regulär beenden und betreffende Instanz stoppen.
- Original-JSON/JSONL, Datenbanken, API-Keys und instanzspezifische Konfiguration nicht durch Code-Sync überschreiben. Tests möglichst offline, keine kostenpflichtigen Modellaufrufe ohne ausdrückliche Freigabe.
- Studio-Schreibschutz erhalten. Nicht pauschal Git reset oder sämtliche alten Installer erneut ausführen.

## Arbeitsstand (Implementierung und Abnahme getrennt)
| Paket | Stand |
|---|---|
| HYBRID01–07 | Zentraler Start, aktivitätsspezifische Toolbar, Auswahl vor Navigation, einheitliche Picker; umgesetzt |
| FUNCTION-SYNC01–03 | Auswahl, Navigation, Originalexport-Priorität, Pagination, Refund-Inspector; Replay und Rückkampf laut Nutzer funktionieren; Export/Pagination nicht abschließend nachgetestet |
| ARCHIVE-SYNC02 | 9 Originalpartien nach Sandbox übernommen, Bericht bestätigt |
| DATA-RESOLVER01 | Gemeinsame Match-Facts für Auswahlansichten; Calls = protokollierte Entscheidungen, nicht Billing |
| CORE-SYNC01 | Wegen Regressionen zurückgerollt; nicht erneut als Gesamtpaket installieren |
| SIDEBAR-MINIMAL02 | Arena und Serien aus Sidebar entfernt, Screenshot bestätigt; Leaderboard, Lab, Design, Sprache bleiben |
| RESULT-SYNC02A | Nur Leaderboard-Datenmodul übernommen; vollständige Ergebnissynchronität noch nicht bewiesen |
| MATCHDETAIL-RESTORE02 / LEADERBOARD_SCROLL01 | Details ergänzt, doppelte innere Scrollbereiche entfernt; Nutzer bestätigte Fortschritt |
| RECOVERY-LINK01 / RECOVERY-INLINE01 | Refund-Ergebnis mit ursprünglicher Partie verknüpft, inline Kennzeichnung KO-R/TKO-R; reguläre Rangliste unverändert |
| REFUND-ELIGIBILITY01 | Nicht geeignete Partien herausgefiltert, Nutzer bestätigt Filter und Start |
| Resume / Catch-Up | Grok startete tatsächlich und übergab von Weiß an Schwarz; Ready Check erhalten. Aufruflimit-Logik ausdrücklich unverändert lassen |
| SERIES-MODAL01 | Bestehende Serienansicht als Modal statt Arena-Navigation geliefert; separate Browser-Abnahme nicht protokolliert |
| LIVE-CONFLICT01 | Start-Menü bleibt verfügbar, konkurrierende Spielstarts gesperrt, Replay/Serien/Live Center erlaubt; bestehende Registry-Sperre erhalten; Browser-Abnahme nicht protokolliert |
| CODE-SYNC02 | 8082 → 8080: 11 Module (7 direkte Kopien, 4 mit instanzspezifischer UI-Freigabe); Screenshot aus Studio zeigt synchronisierte UI; finaler SHA-Abgleich noch nicht als Ausgabe vorliegend |
| MATCHDETAIL-ONLY01 / COMPACT01 | Nach Sync auf beiden Instanzen geliefert: Spielerbereiche, Ressourcen und Verlaufsgrafiken, kompakter horizontaler Kopf; ausschließlich Matchdetail-Ansicht. Exakte historische Optik und letzte Installation nicht endgültig bestätigt |

## Konkrete Datenreferenzen
- S350: andy_cc11a6598bcf und andy_0c0f7413fdf6, Astra gewinnt beide gegen Argon.
- Fable vs Astra: Original andy_9cefa30004b6, TKO-Niederlage Fable (350k Budget, 350006 verbraucht); Refund andy_5c6dfd0af579, +150k je Seite, KO-Sieg Fable. Research-Fortsetzung separat kennzeichnen, keine reguläre Ranglistenwertung (regular_ranking_eligible false).
- Argon vs Astra andy_7278d457e3f6: 159 Züge, 166 Entscheidungen, 168 Ereignisse, 3657 s, Serie andy_83f51171e438 Runde 2.
- Historische Konflikte andy_83f51171e438 / andy_032f31d68743 und Checkpoints andy_33c46a13dfb2 / andy_f3ae37f2c735: nicht durch manuelle Originaldatenänderung lösen; Ausschlüsse nachvollziehbar halten.
- Refund-Archive separat unter andy_refund_research. Original-TKO bleibt sportlich gültig; KO-R ist Forschungsresultat.

## Finaler Sync und offene Aufgaben
Vor CODE-SYNC02 zeigte ANDY_CODE_SYNC01.txt 152 identische, 9 abweichende und 2 neue Python-Module in Sandbox, keine Studio-only. Betroffen: andy_analysis_exclusions.py, andy_match_browser_facts.py, Arena UI, Lab Runs, Leaderboard Data/UI, Replay UI, Series UI, Match Picker, Language Flags, V1 Shell.
Letzte Matchdetail-Patches für beide Instanzen bestimmt. Finaler Vergleich der andy/**/*.py sollte nur die vier bewusst instanzspezifisch freigegebenen Module als unterschiedlich zeigen. Ausgabe fehlt; nicht behaupten, dass bytegenaue Abnahme erfolgt ist. Kein erneutes CODE-SYNC02 über aktuelle Details laufen lassen.
LAB-SYNC-01 ist nächste Priorität (Issue #12). SQLite-Projektion und JSON/JSONL-Archiv, Serien und Resume/Refund-Verknüpfungen auf gemeinsame Identität und nachvollziehbare Eignung prüfen. Fehlende Daten nicht erfinden. Erst danach Lab 1.0 gemäß research/andy-lab/REQUIREMENTS/ANDY_LAB_V1_0_PRODUCT_CONSENSUS_2026-11-20.md. Story-driven Lab Development: Configuration Explorer, Recovery Explorer, Resource & Economics Explorer. Usage Accounting bleibt separates Issue #11; Serien-ID überall und Config Modification zurückgestellt.

## Prozess-Learning
Regressionstest ANDY_REGRESSION01: 86 bestanden, 25 fehlgeschlagen (viele ältere String-/Designverträge, drei Mock-Kontextfehler, fehlende AP2-Baseline, Architekturimport). Nicht als grüne Gesamtabnahme darstellen; keine kosmetische Reparatur der Alt-Tests als Ersatz für Browser-Funktionstests. Keine wiederholten manuellen Kompletttests durch den Nutzer. Feature-spezifische Prüfungen, sichtbare Diffs, Backup/rollback und Prüfsummen. Historische Sonderfälle dürfen zugunsten des Fortschritts ausgeklammert werden, systematische Fehler nicht. Keine eigenmächtige Änderung bereits akzeptierter UI. 


## Aktualisierung am Tagesabschluss (20.11.2026, nach Studio-Abnahme)

**Verbindlicher neuer Übergabe- und Sync-Bericht:** [ANDY_ARENA_RELEASE_SYNC_2026-11-20.md](./ANDY_ARENA_RELEASE_SYNC_2026-11-20.md).

Seit der ursprünglichen Übergabe umgesetzt: neue Living-Lab-/Daten-&-Statistik-Modals, Ablösung des alten Lab-Menüpunkts, DATA-PURGE-02C sowie schrittweise Replay-Löschung DATA-PURGE-03 bis 03H. Code-Sync 8082 → 8080 mit PARITY02-Audit und PARITY03 (12 relevante Module), anschließend STUDIO-LAB-NAV-01 für die Studio-Freigabe der Lab-Modals. Studio-Screenshot bestätigt Daten & Statistik auf 8080 mit eigenen Archivdaten (94 Partien). 8083 unverändert. Kein Daten-/DB-/JSONL-/Secret-Sync.

**Offen:** Modellidentitäten (LAB-SYNC-02), Refund-/Research-Löschsonderfälle, abschließende Quellcode-/Laufzeitparität sowie restliche Integritätschecks. Die frühere Formulierung „LAB-SYNC-01 nächste Priorität“ ist historisch: ein lesender LAB-SYNC-01-Abgleich wurde inzwischen durchgeführt; die weitere Modellharmonisierung bleibt offen. Keine erneute Komplettübernahme oder UI-Neugestaltung ohne explizite Freigabe.


## VERBINDLICHE PROZESS-ÄNDERUNG 21.11.2026 — vor jedem weiteren ANDY-App-Eingriff lesen

**Pflichtdokument für alle neuen Threads:** [ANDY_DEVELOPMENT_REGRESSION_POLICY_2026-11-21.md](./ANDY_DEVELOPMENT_REGRESSION_POLICY_2026-11-21.md).

Auslöser: wiederholte Regressionen bei Designer-Test/Preview/Apply, Replay-Slider und Unterschiede im Studio-/Sandbox-Laufzeitverhalten. Die Ursache des Designer-Preview-HTTP-403 wurde auf neue lokale Schreibschutz-/Branch-Gates eingegrenzt; Preview auf 8082 funktioniert nach Rollenfix wieder. **Designer Apply ist am 21.11. weiterhin NICHT abgenommen:** Session `open`, 6 Test-Snapshots, ältere Approval-Datei ist auf Integrationsbranch unversioniert (`?? docs/ui-designer/approvals/active_design.json`), kein neuer Approval-Commit belegt; nach Apply erscheinen bisher wieder alte Figurenpositionen. **Nicht als erledigt melden.**

**Sofortige Arbeitsregel:** Erst Ist-Zustand und vollständige Abhängigkeiten prüfen, dann minimalen Fix mit Dry Run, Backup, Rollback und echten Ende-zu-Ende-Regressionstests. Kein weitergehender Patch, solange eine bestehende Funktion gebrochen ist. Syntax/Installer-Erfolg ist keine Funktionsabnahme. **Keine neuen ANDY-App-Features vor Designer-Stabilisierung und definiertem Regression-Gate.** 8080 und 8083 nicht für diese Reparatur anfassen. Die Verantwortung für Prozess und Testdesign liegt beim Assistenten.
