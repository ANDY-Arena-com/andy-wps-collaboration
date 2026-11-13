# ANDY App – Übergabe 8082 / RESULT-02 / SERIES-02 / SERIES-03
**Stand: 13.11.2026.** Fix lokal eingespielt, drei gezielte Tests bestanden; vollständige Archiv-/Live-UI-Abnahme offen.

## 1. Einstieg und Quellen
Zuerst [Masterplan](ANDY_GESAMTKONZEPT_MASTERPLAN_v1.0.md), [Match-Evidenzvertrag](ANDY_MATCH_EVIDENCE_JSONL_JSON_SQLITE_v1.0.md), [SERIES-03-Memo](ANDY_SERIES_03_SIDEBAR_INTEGRATION_MEMO_v0.1.md) und [Thread-Start](ANDY_THREAD_START_HIER.md) lesen.

Lokale macOS-Projekte unter ~/Documents/GitHub:
- cair4_andy_game_integration = 8082 (Integration/Test)
- cair4_andy_game_ui = 8080 (Entwicklung, vorerst unangetastet)

Das GitHub-Repository andy-wps-collaboration enthält nicht nachweislich den vollständigen aktuellen App-Code. Die hier geprüfte Basis stammt aus einer im Chat hochgeladenen 8082-ZIP (cair4_andy_game_integration.zip, ca. 6,3 MB), NICHT aus einem GitHub-Code-Release. In neuen Threads für Codeänderungen aktuelle App-Dateien/ZIP benötigt, falls der Chat-Anhang nicht verfügbar ist.

## 2. Bereits vorhandene Serienfunktion (in 8082-ZIP nachgesehen)
- andy/application/adapters/andy_series_catalog.py – Serienkatalog
- andy/application/adapters/andy_result_evidence.py – Ergebnis-Evidenz
- andy/application/adapters/andy_rematch.py – Rückkampf
- andy/application/adapters/andy_match_evidence.py – Match-Evidenz
- andy/features/series/views/andy_series_ui.py – NiceGUI-Seite /series, schreibgeschützt
- andy/features/replay/views/andy_replay_ui.py – registriert install_series_page()
- andy/presentation/shared/shell/andy_v1_shell.py – Sidebar-Link „Serien“ (account_tree)

WICHTIG: Sidebar und /series sind also im gelieferten Quellstand bereits implementiert, anders als im älteren SERIES-03-Memo. Das Dashboard hat Serien/Kandidaten/Matches, Suche und Replay-Schaltflächen. „Nächsten Rückkampf vorbereiten“ leitet derzeit auf Replay weiter; kein eigener Multi-Runner. Der tatsächliche /replay?match_id-Direkteinstieg, Rematch-Preflight, Statistiken und UI-Verhalten sind LIVE noch nicht abgenommen.

## 3. Eingespieltes Patch-Paket
Name des im Chat erstellten ZIP-Patches: ANDY_8082_RESULT02_SERIES02_FIX_PATCH.zip

Enthaltene Python-Dateien:
1. andy/application/adapters/andy_tko_verdict.py (neu) – konservative TKO-Attribution. Decision-Events ohne eigene match_id dürfen durch bestätigte Match-Start/End-Grenzen zugeordnet werden; ausdrücklich widersprüchliche IDs verhindern die Attribution.
2. andy/application/adapters/andy_series_catalog.py (angepasst) – Vorrang expliziter Serienbeziehungen, keine doppelten Kandidaten; HTML-Export verwendet beleggestützte TKO-Ergebnisauflösung.
3. tests/series/test_series_result_02.py (neu) – drei Tests: Legacy-Event-IDs samt Konfliktprüfung; Budgetabbruch ohne Spielerbeweis bleibt offen; echte Archivfälle, falls runs vorhanden sind.
Ferner PATCH_NOTES.md im ZIP. **Die Fix-Quelldateien selbst wurden NICHT in dieses GitHub-Repo committed**; diese Übergabe ist nur Dokumentation.

Lokale Installation per Terminal durch Benutzer auf 8082 bestätigt. Backup: .andy_patch_backups/RESULT02_SERIES02_20261113_190249. Syntaxprüfung erfolgreich. Erstes pytest scheiterte an falschem/fehlendem Interpreter-Modul, nicht am Patch. In Conda base (Python 3.12.2, /opt/anaconda3/bin/python) wurde pytest 9.1.1 installiert; Benutzer meldete als Testausgabe:
**3 passed in 0.15s** bei python -m pytest -q tests/series/test_series_result_02.py.
Noch KEIN vollständiger Testsuite-/Live-UI-Test und KEIN 8080-Sync nachgewiesen.

## 4. Archivstand der gelieferten ZIP, nicht pauschal der Live-Datenbank
- 100 Matchberichte, 2 explizite Serien, 24 unbestätigte Farbtausch-Kandidaten, 0 Katalog-Prüfhinweise.
- 24 Berichte mit budget_overshoot; 6 vom konservativen Resolver attribuiert, 18 bleiben zur Einzelprüfung offen.
- andy_b94759f1b232: Gemini 4 Argon (Weiß) 100.275 / 100.000 Tokens, TKO-Verursacher; Gemini 3.8 Flash (Schwarz) gewinnt. Original andy_1c77f49b3e17 = Runde 0 dieser expliziten Serie.
- andy_b94759f1b232 darf nicht zusätzlich Kandidat zu andy_c8c5be9a44d0 sein.
- andy_cc11a6598bcf und andy_0c0f7413fdf6: Astra–Argon-Farbtausch, dokumentierte Matts zugunsten Astra, **keine bestätigte Serienbeziehung**.
- illegal_retries_exhausted und output_limit_retries_exhausted noch fachlich zu klären; user_stopped, unknown_token_usage, max_decisions usw. nicht pauschal zu TKO umdeuten.
- Runner-Ergebnis nicht als unabhängig engine-verifiziert ausgeben.

## 5. Nächste Schritte in Reihenfolge
1. Aktuellen 8082-Branch, Prozess, Interpreter/Conda-Umgebung, Status, betroffene Dateien und Backups prüfen. Aktive API-Matches nicht unterbrechen.
2. RESULT-02 am kompletten Archiv prüfen: die 18 ungeklärten Budgetfälle evidenzbasiert beurteilen; gemeinsame Ergebnissemantik für Cockpit, Replay, Serien, Leaderboard und Lab sicherstellen.
3. SERIES-03 auf 8082 LIVE testen: Sidebar, /series, Ursprung als Runde 0, Suche/Filter, Replay-Direktaufruf, Ergebnisstatistik, Rematch-Vorbereitung, responsive Themes. Keine neuen API-Calls beim Vorbereiten.
4. Nach Freigabe separate auditierbare manuelle Serienzuordnung entwickeln, ohne Originaldaten zu verändern, keine automatische DB-Mutation beim Anzeigen; Zyklen/Mehrfachzuordnung verhindern.
5. Regressionen erweitern: 100 Reports, 2 Serien, Kandidaten, fehlende Quellen, unklare TKO, Go/Matt, user_stopped, Replay/Rematch, keine ungewollten Kosten.
6. SYNC-01 NUR nach Abnahme 8082: Freigabe, SHA-/Diff-Vergleich mit 8080, nur Code/Tests/Schema, keine pauschale Kopie und KEINE .env/runs/DB-Synchronisation.

## 6. Betriebs- und Sicherheitsregeln
- Der Benutzer bevorzugt direkt kopierbare **macOS-zsh-Terminalbefehle** ohne Kommentarzeilen (zsh meldete bei eingefügten #-Zeilen: command not found: #). Keine Windows-Batches.
- Python-Interpreter explizit wählen: macOS-System-python3 und Conda-python waren verschieden; Conda-Umgebung cair4_env ist vorhanden, aber nicht als tatsächliche App-Laufzeit verifiziert.
- Originale JSONL und JSON unverändert; belegte abgeleitete Interpretation separat; Farbtausch allein ist kein Serienbeweis.
- Die App-ZIP enthielt eine .env: niemals Secrets, .env, lokale Datenbanken, vollständige Runs oder das komplette ZIP ungeprüft in dieses öffentliche Repo committen.
- Live-App 8082 und 8080 nicht automatisch starten/ersetzen; keine kostenpflichtigen API-Aufrufe ohne Zustimmung.

## 7. Startprompt für Folgethread
„Übernimm die ANDY-App-Weiterentwicklung ab diesem Dokument und SERIES-03-Memo. RESULT-02/SERIES-02 sind auf 8082 eingespielt und drei Regressionstests bestanden. Die /series-Sidebar existiert im ZIP bereits. Prüfe vor weiteren Änderungen den realen lokalen Code und die tatsächliche Laufzeit. Danach Serien-UI/Replay/Rematch abnehmen; 8080 vorerst schützen.“

**Regel:** GitHub-Dokumentation != installierter App-Code; drei bestandene Tests != vollständige Produktabnahme.
