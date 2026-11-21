# ANDY 2.0 — Verbindlicher Entwicklungs-, Regression- und Release-Prozess (21.11.2026)

> **NEUER BESTÄTIGTER REGRESSIONSFALL (21.11., 15:39):** [SYNC-FEATURE-GATE-01: identischer Code, unterschiedliche Funktion](./ANDY_SYNC_FEATURE_GATE_CASE_2026-11-21.md). **Studio 8080 neuer Aktivitäts-Launcher repariert und im Browser bestätigt.** Ursache: `pilot = instance().role == 'sandbox' and instance().port == 8082 ...` stand identisch auf beiden Instanzen und deaktivierte 8080. **Künftig jedes Feature-Gate für tatsächlich konfigurierte Rollen/Ports/Modi als Laufzeitvertrag prüfen, nicht nur Hash-Diffs.** Studio-Shell-Änderung nicht beim nächsten Sync überschreiben. Designer-Apply/Replay/Gesamtregression **nicht pauschal als abgenommen** kennzeichnen.

**Status:** verbindliche Arbeitsanweisung für künftige ANDY-App-Arbeit und Threadwechsel.  
**Entscheidender Grundsatz:** **Ein Schritt vorwärts zählt erst, wenn die bereits funktionierenden Abläufe nachweislich erhalten bleiben.**

> Dieses Dokument protokolliert die am 21.11.2026 festgestellten Fehler der bisherigen assistenzgestützten Entwicklung. Es ist **keine** Behauptung, dass alle offenen Regressionen bereits behoben wurden. Die Einhaltung der unten beschriebenen Gates ist künftig vor jeder Freigabe nachzuweisen.

## 1. Warum dieser Prozess erforderlich ist

Der Nutzer hat wiederholte Rückschritte bei bereits funktionierenden ANDY-Funktionen ausdrücklich beanstandet: „1 Meter vor, 3 Meter zurück“. Die Verantwortung für die Qualität vorgeschlagener Änderungen, Installer und Tests liegt beim Entwicklungsprozess des Assistenten — nicht beim Nutzer, der nach jeder Änderung die ganze App manuell erneut testen müsste.

**Nachgewiesene Prozessfehler:**
1. Änderungen an einzelnen Funktionen wurden ohne vollständige Analyse abhängiger Workflows vorgenommen.
2. Instanz- und Schreibschutzänderungen wurden eingeführt, ohne den vollständigen Designer-Lebenszyklus Ende-zu-Ende zu testen.
3. Syntax-, Dry-Run- und Backup-Erfolg wurden zu früh als funktionale Lösung bewertet.
4. Statt die Ursache zuerst im Ganzen zu rekonstruieren, entstanden aufeinanderfolgende Symptom-Patches.
5. Codeparität, Laufzeitparität, Instanzkonfiguration und Browser-Abnahme wurden nicht konsequent voneinander getrennt.
6. Vorhandene Regressionstests waren zum Teil rot; Testergebnisse wurden nicht als wirksames Release-Gate verwendet.

**Nicht bewiesen:** Welcher historische Installer die erste problematische Designer-Freigabebedingung eingeführt hat. Lokale uncommittete Änderungen beweisen den aktuellen Diff, nicht Verursacher oder Änderungszeitpunkt. Keine Spekulation als Tatsache dokumentieren.

## 2. Konkreter Vorfall: Designer-Regression vom 21.11.2026

### Sollverhalten (seitens Nutzer bestätigt)
**Designer → „Testen“ → ANDY-App zeigt unverbindliche Preview → „Apply“ innerhalb der App → dauerhaft freigegebenes Design → beim erneuten Öffnen identische Darstellung.**

Die Preview ist **keine** Freigabe. „Apply“ gilt erst dann als erfolgreich, wenn die Freigabe gespeichert, neu eingelesen und im unabhängigen neuen ANDY-Tab sichtbar ist.

### Beobachtungen und Ursachen
- 8082: „Testen“ lieferte HTTP 403 „Designer-Schreibzugriff nicht freigegeben“. Die lokal geänderte Funktion `_local(request, write=False)` in `andy/presentation/shared/components/andy_ui_release.py` enthielt eine neue Branch-/Rollen-Sperre.
- Historische Designer-Konstante: `BRANCH = "feature/ui-designer-1.0"`; aktueller lokaler Integrationsbranch: `integration/ui-lab-20261109`.
- `andy/application/andy_instance.py`: `instance()` ohne gesetztes `ANDY_ROLE` liefert standardmäßig `studio`. Ein **separater Terminaltest ohne die Startumgebung beweist daher nicht die Rolle des laufenden 8082-Prozesses**.
- DESIGNER-PREVIEW-01 prüfte fälschlich `role == 'studio'` für 8082. DESIGNER-PREVIEW-02 korrigierte auf `role == 'sandbox'`. Danach bestätigte der Nutzer: „Testen“ öffnet die App und überträgt die Preview.
- Apply hatte eine weitere feste Prüfung: `git branch --show-current == feature/ui-designer-1.0`. Für 8082 wurde ein gezielter Apply-Branch-Fix vorgeschlagen. **Nachfolgend war die dauerhafte Übernahme weiterhin nicht erfolgreich.**
- Der Designer-Apply-Endpunkt prüft zusätzlich einen leeren Git-Index und eine unveränderte aktive Freigabedatei. Der Nutzerbericht zeigte `git status --short -- docs/ui-designer/approvals/active_design.json` = `?? docs/ui-designer/approvals/active_design.json`: auf dem lokalen Integrationsbranch liegt eine **unversionierte, bereits vorhandene** Freigabedatei. Die Prüfung lehnt diesen Zustand ab.
- Der dokumentierte Diagnosezustand: `.andy_ui_designer/session.json` hatte `phase: open`, **6** Test-Snapshots und keinen `winner`; `docs/ui-designer/approvals/active_design.json` enthielt einen älteren `candidate_id` (`v44b0bbf045093068bfa72db9`); kein neuer Approval-Commit in der angezeigten Historie.
- Screenshots zeigten: Preview mit veränderter Figurenposition; nach „Apply“ Rückkehr zur vorherigen Figurenposition. **End-to-End-Apply nicht abgenommen.**
- Ein zeitweiliger 8080-Verdacht wurde korrigiert: Prozessausgabe bestätigte später 8080 aus `cair4_andy_game_ui` auf Port 8080. **Richtiges Arbeitsverzeichnis im Terminal beweist nicht die gestartete App; tatsächliche PID/Commandline/Port prüfen.**
- Separate Replay-Regression: Interaktiver Scrubber war durch `ui.linear_progress` ersetzt; `ui.slider` mit `go_to()` wurde auf 8082 funktional wiederhergestellt. Theme-Farbe, Abstand und Handle-Größe wurden danach angepasst; vollständige Theme-Browserabnahme nicht behaupten.

### Aktueller offener Blocker / nächste Arbeit
**DESIGNER-APPLY-02 noch nicht implementiert oder abgenommen.** Es muss geprüft werden, wie der Apply-Endpunkt eine bereits vorhandene, unversionierte Freigabedatei sicher behandeln kann, ohne sie zu verlieren oder fremde Änderungen zu committen. Die **gespeicherten Werte und die anschließende Arena-Ladekette** müssen nach erfolgreichem Apply gesondert geprüft werden. Keine pauschale Entfernung der Branch-, Request- oder Git-Schutzregeln.

## 3. Verbindliche Entwicklungsregeln

### Gate 0 — Ist-Zustand sichern, bevor ein Patch entsteht
- Tatsächlich gestartete Instanz/PID/Port/Umgebungsprofil, Git-Branch/HEAD, Git-Status und betroffene Dateien feststellen.
- Funktionierenden Ablauf durch Nutzerbeobachtung oder reproduzierbaren Test **als Baseline** erfassen. Erwartete Eingaben, Klickfolge und sichtbare Ergebnisse dokumentieren.
- Bei Änderungen an Code außerhalb des Git-Index: zuerst **vollständigen Diff** und die Herkunft vorhandener Änderungen erfassen; kein blindes `git restore`, `git reset` oder Overwrite.
- Umgebungsabhängiges Verhalten mit **denselben Umgebungsvariablen wie der reale Prozess** prüfen; Defaults aus einem isolierten Terminalprozess sind kein Laufzeitbeleg.

### Gate 1 — Wirkungsanalyse vor der Änderung
- Explizit notieren: Auftrag, betroffene Datei/Funktion, Import-/Aufrufstellen, abhängige Workflows, Daten-/Config-/Git-/API-Seiteneffekte und berührte Instanzen.
- **Ziel ist der gesamte Nutzer-Workflow, nicht nur die abstürzende Codezeile.**
- Keine ungefragte UI-Neugestaltung, Navigation, neue Abstraktion oder Sonderarchitektur.
- Erst Root Cause und Schutzbedingung nachweisen, dann minimalen Fix vorschlagen. Bei unklarer Ursache weitere read-only Diagnose statt Patch-Kette.

### Gate 2 — Sicherer, reproduzierbarer Installer
- **Nur explizit erlaubtes Ziel**, kanonischer Realpath, strikter Allowlist-Pfad und erwarteter Ausgangsinhalt/Hash; bei Abweichung **fail closed**.
- Default = Dry Run mit lesbarem Diff. `--apply` nur nach kontrollierter Freigabe.
- Backup vor jeder Änderung, dokumentierter Rollback, Wiederholung idempotent, keine verdeckten Nebeneffekte.
- Kein Löschen/Überschreiben von Originalpartien, JSON/JSONL, SQLite, Symlinks, Secrets, Instance-Launchern oder anderen Instanzen; niemals durch pauschalen Code-Sync.
- Syntax-/Unit-Tests **zusätzlich**, nicht anstelle von Integrations- und Browser-Tests.
- Kein automatischer kostenpflichtiger KI-Modellaufruf ohne explizite Zustimmung.

### Gate 3 — Vollständiger Regressionstest
Pro geändertem Ablauf vorher festgelegte Positiv- und Negativtests ausführen:
- **Designer:** Entwurf verändern → Testen → App-Preview sichtbar → Apply → HTTP/API-Erfolg und Commit/Approval prüfen → unabhängige App neu öffnen → Werte einschließlich BD-02-Figurenposition **identisch** → geschützte Instanzen/Anfragen weiterhin abgewiesen.
- **Replay:** Datensatz laden → vorwärts/rückwärts scrubben → Buttons und Slider konsistent → Theme-Farbe und Handle in allen relevanten Themes → keine Datenmutation.
- **Navigation/Arena/Lab:** vereinbarte Header-/Sidebar-Elemente und Modals auf Zielport, Live/Replay-Ausstieg; vorhandene Arbeitsabläufe unverändert.
- **Daten:** keine ungewollte Änderung an Originaldaten, DB oder Archiv; getrennte Zähler/Archive pro Instanz.
- Wird ein Test nicht ausgeführt, explizit `OFFEN` notieren; nicht als bestanden formulieren.

### Gate 4 — Release/Sync
- Reihenfolge: **8082 prüfen → funktionsspezifische Tests grün → Browser-Abnahme → expliziter Freigabestand → gezielter Code-Sync nach 8080 → Studio-Tests → Dokumentation**.
- 8080 Studio: `~/Documents/GitHub/cair4_andy_game_ui`. 8082 Sandbox: `~/Documents/GitHub/cair4_andy_game_integration`. **8083 Factory nicht anfassen.**
- Nur freigegebene Codeänderungen synchronisieren; Studio-Instanzconfig und externe Daten grundsätzlich getrennt halten. Bewusst instanzspezifische Codeunterschiede dokumentieren.
- Datei-Hash-Parität **≠** identische Navigation, Laufzeitkonfiguration, Datengrundlage oder funktionale Abnahme.
- Nie einen ganzen alten Installer-Stapel wiederholen. Rollback und Nachtest nur gezielt auf betroffene Dateien.

### Gate 5 — Dokumentation und Threadwechsel
Jede Änderung erhält einen kurzen Eintrag mit:
1. Problem/Sollverhalten und vorherige funktionsfähige Baseline.
2. Root Cause (**bewiesen** / **Hypothese** getrennt).
3. Betroffene Instanz/Dateien, Ausgangs- und Zielstand, Diff/Installer/Backup.
4. Tests als **PASS / FAIL / NOT RUN**, inkl. Browser-Abnahme.
5. Offene Risiken, Rollback-Anleitung und **konkrete nächste Aktion**.
6. GitHub-Link auf dieses Prozessdokument in jedem relevanten Handoff.

**Verpflichtung für jeden neuen Thread:** Zuerst dieses Dokument und die aktuelle Übergabe lesen; keine stillschweigende Wiederaufnahme alter Patches. Der nächste Thread übernimmt offene Punkte mit deren Status, nicht als angeblich abgeschlossene Features.

## 4. Stop-Kriterien

Sofort stoppen, Ursachenanalyse statt Weiterpatchen, wenn:
- eine bislang funktionierende Funktion nach Änderung ausfällt;
- Testergebnisse oder Laufzeitprofil nicht zur Annahme des Installers passen;
- der Git-Index nicht sauber oder die Zieldatei unversioniert/unerwartet geändert ist;
- ein Fix weitere unabhängige Module/Instanzen treffen würde;
- keine belastbare Möglichkeit besteht, den Zustand vor der Änderung wiederherzustellen.

**Keine Freigabe**, solange der vollständige geänderte Workflow nicht bestanden hat. Das Wort „installiert“ darf nie mit „abgenommen“ gleichgesetzt werden.

## 5. Priorität nach diesem Vorfall

1. **Stabilisierung vor neuen Features.** Vorhandene lokale 8082-Änderungen und den unveröffentlichten Designer-Approval-Zustand sichern; **keine** Daten- oder Konfig-Synchronisation auf 8080.
2. **Designer Apply reparieren und vollständig abnehmen**, ohne Preview-Freigabe erneut umzubauen: unversionierte Approval-Datei sicher berücksichtigen, Snapshot/Commit prüfen, neue App-Ansicht gegen Entwurf vergleichen.
3. **Smoke-/Regression-Suite für kritische Workflows** als echtes Gate einführen (Designer, Replay, Navigation, Arena, Lab, Datenintegrität).
4. Erst danach neue Features und 8082→8080-Sync wieder freigeben.

## 6. Quellen und Anknüpfungspunkte

- Vorherige Handoff-Dokumentation: [ANDY_ARENA_HANDOFF_2026-11-20.md](./ANDY_ARENA_HANDOFF_2026-11-20.md)
- Sync-/Integrationsstand: [ANDY_ARENA_RELEASE_SYNC_2026-11-20.md](./ANDY_ARENA_RELEASE_SYNC_2026-11-20.md)
- Vorfalldiagnose: Terminalausgaben und Screenshot-Abnahmen aus ANDY-App-Thread vom 21.11.2026; lokale Daten und Screenshots **nicht** durch dieses Dokument in GitHub hochgeladen.

**Prozess-Eigentümerschaft:** Der Assistent muss diese Gates aktiv durchführen und korrekt über nicht ausgeführte Prüfungen berichten. Der Nutzer entscheidet über neue Funktionalität, kritische Änderungen und die Browser-Abnahme; er ist nicht der Ersatz für eine fehlende automatische Teststrategie.

## 7. Verbindlicher Zusatz: FEATURE-GATE-01 / Runtime-Contract nach erfolgreich behobenem Fall

Die Untersuchung vom 21.11.2026 hat eine im klassischen Dateiabgleich **unsichtbare** Fehlerklasse nachgewiesen: `andy_v1_shell.py` enthielt in 8082 und 8080 dieselbe `pilot`-Bedingung, die ausschließlich `sandbox:8082` freigab. Daher war der neue Start-/Aktivitäts-Launcher in 8080 trotz vorhandenem Code nicht aktiv. Nach dem minimalen Installer `STUDIO-LAUNCHER-01` bestätigte der Nutzer im Screenshot von 15:39 Uhr den neuen Dialog „Aktivität auswählen“ auf 8080.

**Zusätzliche verpflichtende Release-Prüfung:** Unabhängig von Diffs **alle aktivierenden Bedingungen** (Rolle, Port, Mode, Feature-Gates, Launcher-Argumente, angewendete Designer-Freigaben) unter dem echten gestarteten Profil und unter Negativprofilen auswerten. Für jede betroffene Funktion Aufrufweg und Browser-Ergebnis prüfen. Jede bewusste Instanzabweichung mit Begründung und Regressionstest dokumentieren; `factory:8083` nicht verändern. Synonyme wie „identischer Code“ niemals als „identisches Verhalten“ ausgeben.

[**Fallprotokoll mit Beweiskette, Installer-Kontrakt und offenem Teststand**](./ANDY_SYNC_FEATURE_GATE_CASE_2026-11-21.md).

**Chronologie beachten:** Die Diagnose in Abschnitt 2 und die Prioritäten in Abschnitt 5 sind der Zustand **vor** der späteren Studio-Launcher-Reparatur. Der Launcher auf 8080 ist jetzt gezielt bestätigt; vollständiger Designer-Apply-/Replay-/App-Regressionsabschluss dagegen weiterhin nicht nachgewiesen. Bei Threadwechsel diese aktuelle Ergänzung als maßgeblich verwenden.
