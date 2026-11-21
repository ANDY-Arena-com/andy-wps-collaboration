# ANDY 2.0 — SYNC-FEATURE-GATE-01: Identischer Code ≠ identische Funktion (21.11.2026)

**Status:** Root Cause nachgewiesen; gezielter Studio-Fix vom Nutzer im Browser **bestätigt**. **Gesamter Sync und alle Regressionstests sind dadurch NICHT automatisch abgeschlossen.**

> **PFLICHTLEKTÜRE FÜR NEUE THREADS UND JEDEN 8082→8080-SYNC.**
> Nur SHA-256-Identität oder das Kopieren aller Dateien garantiert keine gleiche Funktion. Immer auch **Instanzrolle, Port, Feature-Gates, aktivierte Aufrufpfade, Release-Artefakte und Browser-Verhalten** prüfen. Niemals pauschal Factory- oder Archivgrenzen aufweichen.

## 1. Beobachteter Fehler und Bestätigung

- Ziel: Den auf Sandbox 8082 bereits vorhandenen neuen **Start-/Aktivitäts-Launcher** auch in Studio 8080 anbieten.
- Vorher zeigte 8080 weiterhin den alten Einstieg mit Dialog **„NEUE PARTIE // KONFIGURATION“**, trotz mehrfachen Code-Syncs, Hash-Abgleichen, Python-Cache-Löschung, Neustart und Designer-Approval-Übernahme.
- Der neue Launcher-Code und der alte Dialog-Code existierten in **beiden** App-Verzeichnissen. Das war kein „fehlender Dateisync“.
- Der Nutzer bestätigte nach dem Fix mit Screenshot auf `127.0.0.1:8080` vom **21.11.2026, 15:39 Uhr**, dass der neue Dialog **„Aktivität auswählen“** erscheint. Sichtbar sind „Neue KI-Partie“, „Replay öffnen“, „Live Center öffnen“, „Partie fortsetzen“, „Rückkampf vorbereiten“, „TKO Refund · Research“ und „Serien öffnen“. Das ist eine **gezielte Browser-Abnahme des Launchers**, kein Nachweis aller dahinterliegenden Workflows.

## 2. Nachgewiesene Root Cause (nicht Hypothese)

In **beiden** Instanzen stand in `andy/presentation/shared/shell/andy_v1_shell.py`, Zeile 311 vor dem Fix:

```python
pilot = instance().role == 'sandbox' and instance().port == 8082 and mode in ('arena', 'replay', 'series')
```

Der neue Header-Launcher wird nur im Block `if pilot:` angelegt (ca. Zeile 353); der sichtbare Start-Button dort öffnet `activity_dialog.open()`. Bei Studio gilt `instance().role == "studio"`, Port `8080` – `pilot` war daher **False**, obwohl der Code vollständig vorhanden war. Die alte Arena-Konfiguration in `andy/features/arena/views/andy_arena_ui.py` war noch über den bisherigen Pfad erreichbar.

**Folge:** Dateihashes können vollständig identisch sein, während für die gewollte Instanz andere Funktionen aktiv sind. Ein Diff-Bericht, der nur **unterschiedliche** Dateien untersucht, übergeht diese Klasse von Fehlern grundsätzlich.

## 3. Minimaler Fix STUDIO-LAUNCHER-01

- Betroffen: **nur** `~/Documents/GitHub/cair4_andy_game_ui/andy/presentation/shared/shell/andy_v1_shell.py` (Studio 8080).
- Der lokale Installer `INSTALL_ANDY_STUDIO_LAUNCHER_01.py` änderte nur die `pilot`-Bedingung; Sandbox und Factory wurden nicht editiert.
- Neue Bedingung im Studio-Modul:

```python
pilot = ((instance().role == 'sandbox' and instance().port == 8082) or (instance().role == 'studio' and instance().port == 8080)) and mode in ('arena', 'replay', 'series')
```

- Vertrag: **nur** `sandbox:8082` und `studio:8080` in `arena`, `replay`, `series` erhalten den Launcher. `factory:8083`, vertauschte Rollen/Ports und andere Modi erhalten ihn **nicht**.
- Installer-Absicherungen: erwarteter Studio-Hash `1dae365c3494828c6ff6aeae0275ac43acb55b4de50582f742f5a7a73e936d3d`, Dry Run, AST/Syntax, Rollen-/Modus-Kontrakttest, Backup und Rollback-Anweisung. Der Nutzer meldete nach Anwendung den korrekten Dialog per Screenshot. **Nicht belegt:** vollständige Tests der Aktivitäts-Buttons, Replay, Designer-Apply und aller weiteren Funktionen nach diesem Fix.
- Studio-Datei ist **ab jetzt beabsichtigt anders** als Sandbox-Datei. Ein neuer Hash-Diff darf sie **nicht blind wieder überschreiben**.

## 4. Generelles verpflichtendes Modell — keine vorweggenommene Lösung für unbekannte Fehler

Jeder neue Entwicklungsschritt und jede neue Synchronisation muss **alle fünf Ebenen** abdecken:

1. **Inventar:** vollständiges relevantes Dateiinventar; Datenbanken, Originalspiele, JSON/JSONL, Secrets, Backups und Symlinks schützen. Unberücksichtigte Dateien ausdrücklich ausweisen.
2. **Code:** Hashes, Diffs, Syntax, importierte und aufrufbare Funktionen; deklarierte und absichtliche Unterschiede nicht automatisch kopieren.
3. **Instanz-/Feature-Vertrag:** tatsächlich gestarteten Prozess und seine Rolle, Port, CWD, Entrypoint und konfigurierten Feature-Gates erheben; **jedes Gate für jede erlaubte Rolle/Port-/Moduskombination auswerten**, einschließlich **gleicher Code auf beiden Seiten**. Gegen Fehlfreigaben der Factory testen.
4. **Aktiver Zustand:** freigegebene Designer-Snapshots, Frontend-Themes, lokaler Session-/Browser-Zustand, versionierte versus nicht versionierte Approvals und andere aktive Release-Artefakte differenzieren. Diese Zustände **separat** und nur freigegeben übertragen – niemals automatisch mit Code/Spieldaten gleichsetzen.
5. **Verhalten:** reale UI-Aufrufpfade, sichtbare Elemente, Klickergebnis, Funktionalität und Negativfälle im Browser/Integrationstest abnehmen. Erfolg erst nach **dem vollständigen vereinbarten Nutzer-Workflow**.

**Normative Freigaberegel:** Jede abweichende UI-Funktion muss mit einer reproduzierbaren, belegten Erklärung als `EXPECTED_PER_INSTANCE`, `FIXED_AND_TESTED` oder `BLOCKED_UNEXPLAINED` markiert werden. `BLOCKED_UNEXPLAINED` verhindert die Gesamtfreigabe. „Gleicher Hash“ ist **keine** ausreichende Erklärung.

## 5. Was die Audits tatsächlich ergaben

- `ANDY_SYSTEM_SYNC_AUDIT08`: 1.040 Unterschiede im großen Dateiinventar; zahlreiche historische Backups/Laufzeitdateien/geschützte Daten. Diese Zahl bedeutete **nicht** 1.040 aktive Programmfehler.
- `ANDY_SYNC_RELEASE_GATE09`: nur vier aktive Python-Diffs, vor allem Lab, Designer-Freigabe und Shell-Instanzgates. Auch vier identische Dateien mit unterschiedlichem Verhalten sind möglich. Gate blieb `BLOCKED_PENDING_RUNTIME_AND_VISUAL_CONTRACT`.
- `ANDY_SYNC_APPROVAL_RELEASE10`: Freigabezustand von Sandbox 8082 (PINK, 21.11.) gegenüber Studio 8080 (älter, 12.11.) verschieden. Der Nutzer bestätigte Übernahme der PINK-Figurenposition; **fehlende Navigation blieb** – Approval war nicht deren Ursache.
- `STUDIO-LAUNCHER-01`: Gate-Bedingung korrigiert, neuer Launcher auf 8080 im Browser bestätigt.

Diese Erfahrungen begründen ein **generelles Freigabe-Gate**, nicht nur einen Header-Sonderfall.

## 6. Stand für Fortsetzung / Threadwechsel

**Bestätigt:** neuer Start-Launcher ist auf 8080 sichtbar und öffnet „Aktivität auswählen“. Die Sidebar mit Living Lab und Daten & Statistik wurde zuvor als funktionsfähig bestätigt. PINK-Figurenversatz wurde zuvor als übernommen bestätigt.

**Noch offen / nicht als PASS kennzeichnen:** vollständige Aktivitäts-Navigation in jedem Modus; Replay-Slider auf 8080 nach FINAL07; Designer Test → Preview → Apply → erneutes Öffnen auf 8080; Studio-/Sandbox-Instanzintegrität in allen Negativtests; vollständige App-End-to-End-Abnahme; finale Übertragung der Prozess-Gates in automatisierte Regressionstests.

**Kritische Arbeitsanweisung:** Vor neuem Installer zuerst dieses Dokument und [ANDY_DEVELOPMENT_REGRESSION_POLICY_2026-11-21.md](./ANDY_DEVELOPMENT_REGRESSION_POLICY_2026-11-21.md) lesen. Den behobenen Launcher-Fehler **nicht** wieder öffnen und keine Vollkopie von `andy_v1_shell.py` 8082→8080 durchführen. 8083 nicht anfassen. Keine Originalpartien, DB, Secrets oder Instance-Launcher synchronisieren. Keine kostenpflichtigen Modellaufrufe ohne Zustimmung.

**Provenienz:** Terminal-Diffs, PILOT-Gate-Ausgaben und Nutzer-Screenshot aus ANDY-App-Thread am 21.11.2026. Dieses GitHub-Dokument enthält weder lokale Spielinhalte noch private Verzeichnisinventare oder Screenshots.
