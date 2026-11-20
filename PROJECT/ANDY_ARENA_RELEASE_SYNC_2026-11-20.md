# ANDY 2.0 — Arena / Lab / Data: Tagesabschluss und Studio-Sync (20.11.2026)

**Dokumentationsstand:** 20.11.2026, nach Browser-Abnahme von „Daten & Statistik“ auf Studio (8080).  
**Geltungsbereich:** lokaler App-Code und beobachtete Daten auf Sandbox 8082 und Studio 8080; dieses Protokoll ist **kein** Upload lokaler Partiedaten oder Python-Quellcodes nach GitHub.

## 1. Ergebnis des Tages

- **Arena und Fightnight:** bestehende abgenommene Darstellung beibehalten; keine weitere Arena-Neugestaltung. Die heute behandelten Arena-/Board-/Broadcast-/Shell-Änderungen wurden beim Studio-Code-Sync berücksichtigt.
- **Living Lab:** nativer NiceGUI-Lab-Prototyp, Archivadapter und Dashboard/Explorer/Builder/Workspace; Navigation/Header an die Designreferenz „Daten & Statistik“ angenähert (LAB-DATA-03D bis 03G).
- **Daten & Statistik:** bestehendes HTML-Design als datengebundene Ansicht mit SQLite-Replay-Archiv, Kohorten-/Suchfiltern, Analyseansichten, Methodik. Alter Lab-Menüpunkt zugunsten „Living Lab“ und „Daten & Statistik“ entfernt (LAB-DATA-03H). Frühere Methoden/Analysen, soweit einfach wiederverwendbar, in den neuen Statistikbereich überführt; alte Code-Abhängigkeiten nicht blind gelöscht.
- **Datenlebenszyklus:** Benutzer entscheidet über endgültige Löschung. Abbruch, kurze Partie oder Fehler sind **kein** automatischer Löschgrund; explizite Löschung wirkt auf passende Partiedaten und eigene Originaldateien. Gemeinsam genutzte Quellen und fremde Instanzen werden geschützt.
- **Studio-Sync:** Codeauswahl 8082 → 8080 übertragen und den bislang nur auf 8082 freigeschalteten Lab-Zugang mit STUDIO-LAB-NAV-01 auf 8080 aktiviert. Browser-Screenshot auf 8080 zeigt neues Statistik-Modal mit Studio-eigenen Archivdaten (94 Partien). Das bestätigt die konkrete Ansicht, **nicht** die vollständige Laufzeit-/Dateiparität.

## 2. Lab-/Statistikpakete (lokale Entwicklung 8082)

| Paket | Inhalt / Beobachtung |
| --- | --- |
| LAB-V02-01 / 02 / 02A | Living-Lab-Grundgerüst, Archivanschluss, Filter/Scroll; zuvor 128 archivierte Treffer bei Abnahme eines Zwischenstands. |
| LAB-DATA-03 / 03A | Separate Statistikansicht, Kohortenfilter, Modalabstände. |
| LAB-DATA-03B | Erster nativer Statistiknachbau optisch nicht akzeptiert; **nicht** als finaler Designstand verwenden. |
| LAB-DATA-03C | Original-HTML-Statistikansicht in Modal eingebettet, echte Archivdaten. |
| LAB-DATA-03D / 03E | Header/Sidebar angenähert, Logo-Sonderblock entfernt. |
| LAB-DATA-03F / 03G | Lab-Navigation/Header angepasst; 03G nutzt native HTML-Buttons statt Quasar-Buttons für konsistente Ausrichtung/Typografie. Screenshotvergleich positiv. |
| LAB-DATA-03H | Alten Lab-Einstieg aus Navigation entfernt, unkompliziert übertragbare historische Analyse-/Methodikfunktionen konsolidiert. |

**Bewusste Grenzen:** Living Lab noch kein vollständig produktiver Forschungs-Workflow. Story-driven Lab Development (Configuration, Recovery, Resource/Economics) bleibt weiterer Produktweg. Keine automatischen KI-Interpretationen oder zusätzlichen kostenpflichtigen Modellaufrufe.

## 3. Datenabgleich, Löschregel und Bereinigung

### LAB-SYNC-01 (rein lesender lokaler Bericht)

- Gemessene Ausgangswerte: Leaderboard **153** Match-IDs, Statistik **128**, Schnittmenge **127**, nur Leaderboard **26**, nur Statistik **1** (Teilsegment).
- 26 Leaderboard-only-Partien waren im Replay ausgeblendet; die im V2-Replay geführte Löschung war zunächst nur `replay_hidden_matches`, nicht physisches Entfernen.
- Unterschiedliche Modellidentitäten: historischer Modell-ID-/Alias-Vergleich statt einfacher Gleichsetzung von Anzeigenamen. **Mehrdeutig:** `DeepSeek V4 Pro` (IDs 19/31/8), `glm-5.3` (12/23), `kimi-k3.1-pro` (24/25). Nicht blind zusammenführen.
- Zahlengleichheit bedeutet nicht identische Match-Auswahl oder Modellidentität.

### DATA-PURGE-01 / 02A / 02B / 02C

- 8082 bindet `andy.db` und `andy_v2_shadow.db` als **Symlinks** auf getrennte Testdaten außerhalb des Code-Repositories ein. Keine Umverlegung der Datenbanken.
- Preflight identifizierte **27** explizit versteckte/gelöschte Match-IDs und **56** Kandidatendateien. Zwei verknüpfte Fälle wurden zunächst zurückgestellt; **25** Partien und **51** Dateien waren für die einmalige Bereinigung freigegeben.
- Dry Run DATA-PURGE-02C zeigte u. a. je **25** DB-Matches und Revisionen, je **247** Events, **238** V2-Brettzustände, **247** Replay-Payloads.
- Nach bestätigtem `--apply` zeigte das Leaderboard **128** statt **153** Partien, **25** statt **29** Modelle, **41** statt **51** Selbstpartien, technische Abbrüche **30** statt **32**; KO **6**, TKO **32** unverändert. Statistik zeigte damals ebenfalls **128** Partien. Dies waren **zeitgebundene Screenshots**, keine fest zu erwartenden Werte für künftige Datenstände.

### DATA-PURGE-03 / 03A–03H (Löschung aus Replay)

- DATA-PURGE-03: zentraler physischer Löschpfad für V1/V2 und eindeutig eigene JSON-/JSONL-Artefakte; Codebackup, aktive Partien und Quellenabhängigkeiten berücksichtigt.
- 03A: Löschbutton im tatsächlich verwendeten HYBRID-Replay-Dialog neben JSONL/JSON-Export statt in einer unsichtbaren Tabellenaktionsspalte.
- 03B/03C: zu strenge Match-ID-Textsuche bei Teil-/Resume-Aufzeichnungen schrittweise korrigiert.
- 03D: gleichnamige Dateien in **8080** dürfen eine Löschung in **8082** nicht blockieren.
- 03E: benannte zusätzliche Sandbox-Originale (Continuation-/Refund-Research-Verzeichnisse) in den Löschplan aufnehmen.
- 03F: archivierte Aufzeichnungen können auch ohne V1-/V2-Matchzeile gelöscht werden.
- 03G: fehlende JSONL-Datei ist kein pauschaler Blocker; vorhandene eindeutig zugeordnete Quellen bleiben geschützt.
- 03H: historische externe Quellen in V1 nicht mehr pauschal als Löschhindernis; externe Dateien werden **nicht** gelöscht, fremde/teils gemeinsam genutzte Sandbox-Dateien bleiben geschützt.
- Browserbeobachtung: Replay-Sichtbestand fiel über mehrere bewusst manuell bestätigte Löschungen von **160 → 159 → 158 → 137 → 136 → 106**. Der Nutzer bestätigte, dass Löschungen auch Leaderboard und Statistik aktualisieren. **Nicht** aus Differenzen der Zähler allein ableiten, wie viele vollständige Partien gelöscht wurden; die Sichten zählen teils unterschiedliche Aufzeichnungsarten.
- **Offen:** Refund-/Research-Sonderfall `andy_7cbd420f9667` (Grok gegen Grok) sowie verbleibende Referenz-/Resume-Fälle. Keine Behauptung, dass jede Löschung bereits garantiert funktioniert. Nachfolgender Read-only-Konsistenzcheck auf aktuellem Stand noch offen.

### Verbindliche Löschsemantik

- Nur **explizite Benutzerentscheidung** erlaubt endgültige Löschung; niemals automatisch nach Zügen, Abbruchgrund, Fehler oder vermeintlichem Forschungswert.
- Bei eigener Aufzeichnung: passende Datenbankeinträge, Revisionen, Ereignisse, Replay-Payloads, Evidenzkopien und eindeutig eigene Dateien entfernen; gegen Reimport sichern.
- Tatsächliche API-Kosten nicht rückwirkend verändern. Gemeinsame Quellen/Resume-/Refund-Bezüge anderer Partien nicht beschädigen; Studio-/Factory-Daten nicht löschen.
- Ein später bewusst neu gespielter Forschungsfall ist **neue** Evidenz mit neuer Match-ID, keine rückwirkende Wiederherstellung.

## 4. SYNC 8082 → 8080: tatsächliche Schritte

| Schritt | Beobachtung / Abnahme |
| --- | --- |
| ANDY_SYNC_8080_RELEASE01 | Konservativer Allowlist-Sync von **10** Dateien. Nach erstem Versuch waren noch zentrale UI-Differenzen sichtbar; die reine Dry-Run-Ausgabe ist **kein** Beweis einer Ausführung. |
| AUDIT_SYNC_8080_PARITY02 | Read-only-Verzeichnisvergleich: **244** relevante 8082-Dateien gegenüber **241** auf 8080, **13** Unterschiede; davon **12** relevante App-Module und eine zusätzliche Testdatei in 8080 (`runs copy/test_andy_db.py`). |
| ANDY_SYNC_8080_PARITY03 | Gezielter Sync der **12** relevanten Module, SHA-gesichert, mit Codebackup. Zwei zuvor fehlende Module: `andy/features/arena/views/andy_arena_ui.py`, `andy/presentation/shared/components/andy_match_picker.py`. Die Studio-only-Testdatei blieb unberührt. |
| STUDIO-LAB-NAV-01 | Drei Studio-Code-Stellen öffneten neue Lab-Modals vorher nur auf Port **8082**. Für **8080** freigeschaltet; Benutzer bestätigte Statistik-Modal auf 8080 durch Screenshot. |

### Bei PARITY03 berücksichtigte Module

```text
andy/features/arena/views/andy_arena_ui.py
andy/features/lab/models/andy_lab_v02_archive.py
andy/features/lab/views/andy_lab_v02_preview.py
andy/features/lab/views/andy_stats_original.py
andy/features/replay/views/andy_replay_ui.py
andy/infrastructure/archives/andy_match_purge.py
andy/presentation/shared/board/andy_board.py
andy/presentation/shared/broadcast/andy_arena_web02.py
andy/presentation/shared/components/andy_match_picker.py
andy/presentation/shared/components/andy_ui_components.py
andy/presentation/shared/components/game_view.py
andy/presentation/shared/shell/andy_v1_shell.py
```

### Isolationsgrenzen und Studio-Ergebnis

- 8082 Sandbox: `~/Documents/GitHub/cair4_andy_game_integration`
- 8080 Studio: `~/Documents/GitHub/cair4_andy_game_ui`
- 8083 Factory: **nicht anfassen**.
- Nur Code übertragen, **keine** Datenbanken, Symlinks, JSON/JSONL-Partien, API-Schlüssel, sonstige instanzspezifische Konfigurationen.
- Letzter Studio-Browser-Screenshot (20.11.2026, ca. 23:26): `Daten & Statistik` in 8080 sichtbar, **94 Archivpartien**, **35 Modellbezeichnungen**, **7.039 Entscheidungen**, **6.344 ausgeführte Entscheidungen**. Andere Datenzahlen als 8082 sind **erwartet**, da Datenbestände getrennt sind.
- **Keine vollständige finale SHA-Paritätsprüfung nach STUDIO-LAB-NAV-01 belegt.** Drei absichtliche Port-Freigabeunterschiede zwischen Studio und Sandbox sind zulässig; keine bytegenaue Identität behaupten.
- Studio-Navigation/Living-Lab-Einstieg: Freischaltung implementiert; Statistik visuell bestätigt, weitere interaktive Studio-Pfade separat bei Bedarf prüfen.

## 5. Offene Aufgaben / priorisierte Fortsetzung

1. **LAB-SYNC-02: Modellidentitäten** anhand evidenzbasierter stabiler Modell-ID und Match-/Seitenbezug harmonisieren; problematische Aliaszuordnungen nicht automatisch verschmelzen.
2. **DATA-PURGE-03 Restabnahme:** Einzelfall Refund/Research und Read-only-Konsistenzprüfung (inkl. Import-Reaktivierung und ggf. verbleibender Löschmarker) ohne neue pauschale Sperren.
3. **Code-Parität/Studio-Abnahme:** read-only erneuter Quellcodevergleich **mit dokumentierten instanzspezifischen Ausnahmen**, Test von Lab-Zugang, Replay, Fightnight, Leaderboard auf 8080 ohne kostenpflichtige API-Aufrufe.
4. **Externe Kommunikation und Dokumentation:** Story-driven Lab Development, Arena/Lab/Journal-Verknüpfung, Demos/Academy als nächster Schwerpunkt. Kein zusätzliches UI-Redesign ohne Auftrag.
5. Langfristig: gemeinsamer Data-&-Evidence-Layer, definierte Partienselektion je Auswertungszweck, eindeutige Modellidentitäten, Replay-/Refund-/Resume-Provenienz und reproduzierbare Forschungsversuche.

## 6. Release-Gate / Prozess

- **Abgenommen:** Darstellung Daten & Statistik auf 8080; neue Lab-/Statistikstruktur auf 8082; Replay-Löschung für viele Fälle einschließlich sichtbarer Aktualisierung der betroffenen Auswertungen.
- **Teilabnahme:** Studio-Code-Sync und Portfreigabe, aber ohne vollständigen finalen SHA- und Browsertest aller Funktionen.
- **Offen:** vollständige Modellalias-Harmonisierung, bestimmte Refund-Löschfälle, Wiederimport-Sperre und abschließender datenbankübergreifender Konsistenznachweis.
- Minimal-Diffs, prüfbare Skripte mit Backup/Rollback, keine automatischen Kosten, keine eigenmächtigen Änderungen bereits akzeptierter UI.
