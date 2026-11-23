# ANDY 2.0 — TECH-DEBT-AUDIT-01: Auswertung und Sync-Gate

**Datum:** 23.11.2026  
**Grundlage:** vom Nutzer hochgeladene lokale Reports `ANDY_TECH_DEBT_AUDIT_01_SUMMARY.md` und `ANDY_TECH_DEBT_AUDIT_01_REPORT.json`, generiert `2026-11-23T12:50:18.648486+00:00`.  
**Methodik:** rein lesende lokale Datei-/Git-/SHA-/statische Import- und Dateinamenanalyse. **Keine Quellcode-Diffs im Audit-JSON; keine Runtime-/Browser-Regression; kein automatisches Löschen.**  
**Status:** Berichtseingang ausgewertet; **kein Code gesynct, gelöscht oder committed**. Die Quellen-JSON/MD liegen lokal beim Nutzer beziehungsweise im Entwicklungs-Chat, nicht als Spiel-Datensatz im Repo.

## 1. Inventar und Befunde

| Metrik | Studio 8080 | Sandbox 8082 |
|---|---:|---:|
| Quellcode-/Skriptdateien im Scope | 253 | 258 |
| Weitere Konfiguration-/Metadateinamen (ohne Inhaltsaudit) | 23 | 23 |
| Git-untracked Source-Dateien | 107 | 117 |
| Git-modified, tracked Source-Dateien | 37 | 43 |
| Statisch referenzierte Source-Dateien | 129 | 132 |
| Dateien ohne vom Scanner erkennbare Referenz (nur Review) | 6 | 7 |
| Dateigleiche Gruppen pro Instanz | 0 | 0 |
| Python-AST-Syntaxfehler im geprüften Scope | 0 | 0 |

- **Gemeinsame relative Pfade und identische SHA-256**: **240**
- **Gemeinsamer Pfad, unterschiedlicher SHA-256**: **9**
- **Nur Studio 8080**: **4**
- **Nur Sandbox 8082**: **9**

Gegenstand nur des Source-Scopes; **nicht** als vollständige Dateisystem-/Environment-Parität interpretieren. Keine Aussage über funktionale/semantische Duplikate. AST-Prüfung = Syntax, nicht Browser-/Spielregression.

**Lokale Git-Metadaten zum Auditzeitpunkt:** Studio Branch `feature/ui-designer-1.0` @ `8fce4ef9b7e4`; Sandbox Branch `integration/ui-lab-20261109` @ `447f691ceb20`. Ein neuerer funktionierender 8082-Browserstand kann weiterhin teilweise aus untracked Dateien bestehen. **GitHub ist kein vollständiges Abbild des Live-Stands.**

## 2. Neun gemeinsam vorhandene, inhaltlich unterschiedliche Dateien — P0 vor Sync

| Datei | Risikobereich | Sync-Regel |
|---|---|---|
| `andy/features/arena/views/andy_arena_ui.py` | Arena-/Replay-/Observer-Aufrufe, Match-Worker, Models | Inhaltlicher Diff, Aufrufpfad/Role Gate, Live-Browser-Test |
| `andy/features/lab/views/andy_lab_v02_preview.py` | Lab-/Daten-Pilot und UI | Kein blindes Überschreiben; Lab/Data aktuell keine neue Baustelle |
| `andy/features/lab/views/andy_stats_original.py` | Alt-Lab, Weiterleitung und Statistiken | Unterscheiden: noch benötigte Funktion vs. Legacy-Modul |
| `andy/features/replay/views/andy_observer_pulse01.py` | zentraler Observer, GI und Economy-Integration | 8082-Funktion sichern, nicht durch alten 8080-Stand überschreiben |
| `andy/features/replay/views/andy_replay_ui.py` | Replay, Observer-Einstieg, Archiv | Event-X, Replay-Slider, Sortierung/Filter separat testen |
| `andy/infrastructure/providers/andy_llm_bridge.py` | Provider-Usage, Model Identity, GI-Bewertung | Modell-/API-Trennung und Reasoning-/Usage-Verhalten regressionstesten |
| `andy/presentation/shared/broadcast/andy_broadcast.py` | Bühne/Broadcast, Größe und Positionierung | 8082 top-aligned UX und Studio-Ansicht prüfen |
| `andy/presentation/shared/components/andy_ui_release.py` | Designer Preview/Apply, Freigaben | **Studio-spezifische Designer-Gates bewahren; nicht blind ersetzen** |
| `andy/presentation/shared/shell/andy_v1_shell.py` | Launcher/Observer/Header, Rollen-/Port-Gates | **Studio 8080 Launcher-Fix und Sandbox 8082 Freigaben gezielt mergen** |

Dies ist eine *Risiko-Klassifizierung nach Pfad und bekannten Funktionen*, **kein bereits erfolgter Inhaltsdiff**.

## 3. Nur auf einer Seite vorhandene Source-Dateien

### Nur Sandbox 8082 — funktionaler Integrationskandidat, nicht pauschal technische Schuld

1. `andy/features/replay/views/andy_observer_economy01.html`
2. `andy/features/replay/views/andy_observer_economy01.py`
3. `andy/features/replay/views/andy_observer_economy_tariffs02.py`
4. `andy/presentation/shared/components/andy_game_intelligence_eval02.py`
5. `andy/presentation/shared/components/andy_game_intelligence_live02.html`
6. `andy/presentation/shared/components/andy_game_intelligence_live02_panel.py`
7. `andy/presentation/shared/components/andy_observer_gi_unify01.py`
8. `andy_app_subq.py`
9. `semantic_pilot.py`

**Erste sieben** bilden den offensichtlichen codebasierten GI-/Economy-/Observer-Anschluss und sind aufgrund der statischen Verweise plausibel für die funktionierende 8082 relevant. Nicht automatisch Löschkandidaten.  
**Letzte zwei** gesondert als mögliche CLI-/Pilot-Entrypoints bewerten; keine behauptete Nichtnutzung.

### Nur Studio 8080 — nicht als störende Dateien behandeln

- `ZYKLOPEN_LIVE_REPORT.html`
- `ZYKLOPEN_OFFLINE_REPORT.html`
- `andy_zyklopen_test.py`
- `test_zyklopen.py`

Als Studio-spezifische Tests/Reports einstufen und bewusst entscheiden, ob sie erhalten/archiviert werden; **nicht einfach mit Sandbox-Sync löschen**.

## 4. Review-Kandidaten ≠ Loeschliste

**In beiden Instanzen statisch nicht referenziert:**  
`andy/features/leaderboard/views/andy_arena_leaderboard_bridge_ui.py`,  
`andy/infrastructure/archives/andy_replay_archive.py`,  
`andy/infrastructure/persistence/andy_db_import.py`,  
`andy/infrastructure/reporting/andy_report_cli.py`,  
`andy/presentation/shared/components/andy_ui_preview.py`,  
`docs/examples/andy_app.example.py`.

**Zusätzlich 8082:** `andy/presentation/shared/components/andy_game_intelligence_v01.py`.

**Wichtige Einordnung:** CLI-/Importmodule können als direkte Entrypoints gestartet werden und werden dann von keiner Python-Datei importiert. `andy_ui_preview.py` kann von Designer-Lebenszyklen benötigt werden; `docs/examples` ist bewusst ein Beispiel. Die alte GI-v01-Ansicht wird auf 8080 statisch vom Shell importiert, auf 8082 nicht; ein globaler Löschschluss wäre damit falsch. In 8082 referenziert die dazugehörige HTML-Datei weiterhin v01-Name/-Komponenten; die Abhängigkeit ist separat zu prüfen.

**Namen wie `pilot`, `preview`, `original` sind nicht „tot“:** Der Bericht nennt die folgenden *statisch genutzten* Kandidaten: `andy_resume_live_pilot.py`, `andy_lab_v02_preview.py`, `andy_stats_original.py`; weitere Tests/Paketscaffolds und `semantic_pilot.py` als Sonderfälle.

**Keine inhaltlich exakten Dubletten** im Scope entdeckt; semantisch überlappende Legacy-/Neufunktionen sind durch SHA-Inventar nicht zu erkennen.

## 5. Weitere zum Sync relevante Details

- `andy/presentation/shared/broadcast/arena_stage.webp` und `theater_stage.svg`, drei i18n-`.json` Dateien sind **in beiden Instanzen als untracked Asset-/Metadatennamen** vorhanden. Da der Audit dort keinen Inhalt las, vor Freigabe auf Existenz, Referenz und SHA prüfen, nicht nur Python-Dateien mergen.
- `docs/ui-designer/contracts/andy-ui-design-session-v1.schema.json` ist laut Scope in Sandbox **modifiziert**, im Studio unverändert. Designer-Verträge gezielt vergleichen.
- `README.md` ist auf beiden Instanzen untracked und unterschiedlich groß; `requirements.txt` als untracked Metadatei nur auf 8082 erfasst. Kein blindes pip freeze oder Requirements-Overwrite.
- Original-Spielartefakte, SQLite, Secrets, `.env`, `runs`, Approvals, `.andy_sync_backups`, Research-Ordner und Symlinks waren aus dem Source-Inhaltsscan ausgeschlossen und bleiben bei allen Sync-Operationen geschützt.
- Die Dateien `andy_observer_pulse01.py`, `andy_broadcast.py`, `andy_lab_v02_preview.py` und `andy_stats_original.py` sind trotz untracked-Status auf **beiden** Seiten vorhanden, teilweise bewusst unterschiedlich. Eine reine Git-Diff-Auswahl ist daher unvollständig.

## 6. Empfohlene Reihenfolge und Go/No-Go-Gates

### P0 – Sichern, nicht löschen (vor Sync)
1. Laufende Partie/Archivierung beenden und beabsichtigte lokale Source-Stände **ohne Datenbanken, Secrets und Originalspiele** sichern. Bisherige Rollback-Pakete nicht mit ihrem aktuellen Inhalt überschreiben.
2. Aktuelle SHA-/Dateilisten und beide Branch-/Rollen-Konfigurationen als unveränderliche Quelle für die nächsten Schritte festhalten.
3. **22 differierende/instanzexklusive Source-Dateien** (9 Diff + 9 nur 8082 + 4 nur 8080) gezielt in einem **Code-only, read-only Source-Bundle** für semantische Diffs und Merge-Entscheidungen sammeln; einschlägige Rolle-/Designer-/Release-Verträge plus relevante HTML-/Assets ergänzen. Nur nach Prüfung gegen sensible Inhalte. **Dieser Audit allein enthält keine Quelltexte**, daher sind konkrete Patches noch nicht seriös möglich.

### P1 – Selektiver Sync
4. Neun Diff-Dateien einzeln dreiseitig bewerten: Studio-Verhalten, Sandbox-Verhalten, gewünschter Ziel-Vertrag. **`andy_v1_shell.py` und `andy_ui_release.py` als besonders schützenswert**.
5. Sandbox-only Observer-/GI-/Economy-Quellen bewusst integrieren; 8080-only Studio-Tests bewusst erhalten.
6. Kleinste mögliche reversible Sync-Einheiten mit Dry Run, Schutz von live-Daten, unabhängigen Backups und genauem Diff. Kein `git reset/checkout` oder `git add -A`.

### P2 – Vollständige Regression
7. Runtime-/Browser-Gates **je Instanz**, nicht nur SHA: Arena, Live-Match mit/ohne Observer, Replay, GI Bewerten X, Modellwahl getrennt vom Spieler, Time/Token/USD/EUR, Tarifeditor, Designer Preview→Apply→Persistenz, Launcher, Role-/Port-/Mode-Gates, Abschluss/KO/TKO.
8. Git-Sicherung der freigegebenen Code-Dateien via explizite, nachvollziehbare Pfadlisten. Kein untracked Source-Verlust.

### P3 – Tech-Debt-Cleanup separat
9. Review-Kandidaten einzeln mit Belegen `KEEP / CONSOLIDATE / ARCHIVE / REMOVE` einordnen. Nur manuell genehmigte Löschungen in separaten reversiblen Cleanup-Commits.
10. Kein neues Lab-/Data-Feature, kein 8083-Change und keine Altspiel-Rewertung in diesem Durchlauf.

**Go/No-Go:** Solange es keinen semantischen Diff und sicheren Source-Snapshot gibt, ist das blinde Kopieren aller 8082-Dateien **NO-GO**. Das Read-only-Inventar hat seine Aufgabe erfüllt; der nächste Schritt ist ein gezieltes Source-Bundle und kein weiterer breiter Scanner.

## 7. Offene Verifikation

- Welche der neun geänderten Quellen enthalten tatsächliche Feature-Unterschiede, instanzspezifische Gates oder historische Reste? **Noch nicht aus Quelltext verglichen.**
- Welche 8082-only Observer-Dateien sind über realen Browserpfad notwendig? Die Referenzstruktur spricht für 7 Dateien, aber verlangt noch Regression.
- Sind Asset-Byteinhalte und Designer-/Approval-Verträge zu 8080/8082 kompatibel?
- Sind die lokal installierten Tarife aus dem externen SQLite-Store verfügbar, und bleibt dieser nach Studio-Sync unabhängig und korrekt zugeordnet?
- Liegen seit Auditzeitpunkt weitere lokale Änderungen vor? Hashes vor jedem Installer erneut prüfen.

**Quellenstatus:** Diese Dokumentation ist eine Auswertung des konkret hochgeladenen Audit-JSONs, **keine neue Live-Inspektion des Mac**. 
