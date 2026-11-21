# ANDY 2.0 — Observer Research: Status und technische Übergabe (21.11.2026)

> **PFLICHTLEKTÜRE FÜR JEDEN NEUEN OBSERVER-THREAD.** Dies ist der Stand **nach Installer ORIENTATION19**, nicht mehr Observer 0.7 / 1.4. Ziel ist **Sandbox 8082** (`~/Documents/GitHub/cair4_andy_game_integration`). **Studio 8080 und Factory 8083 nicht ändern.** Diese Datei dokumentiert den Arbeitsstand und ersetzt weder eine lokale Browser-Abnahme noch einen gesonderten Release-/Sync-Prozess.

## 1. Arbeitsziel und Produktlogik

**Leitidee: „Taschenlampe im dunklen Raum“.** Der Observer macht ausgewählte beobachtbare Muster innerhalb **einer** Partie sichtbar, ohne versteckte KI-Prozesse zu behaupten oder die Engine zu beeinflussen. **Arena** erzeugt Ereignisse; **Observer** untersucht eine Partie; **Living Lab** sucht Meta-Muster über viele, etwa 100, Partien; **Journal** erzählt überprüfte Erkenntnisse. Observer-Ergebnisse sollen später mit Partie-ID, Originalereignis-ID, Algorithmus-/Parameter-Version und Datenqualität übergreifend vergleichbar auswertbar sein. Ein konkreter Lab-Exportvertrag ist **noch offen**.

**Grundinteraktion (im Browser bestätigt):** auffälligen Marker im Observer anklicken → bestehender Replay-Slider springt → Hauptbrett zeigt passende Stellung → bei Textwechsel Originalbegründungen im Inspector vergleichen. Fehlversuche zählen als Originalereignisse, sind aber nicht zwangsläufig ausgeführte Brettzüge. Replay besitzt `go_to(index)`; die bestehende Navigation ist verbindlich, kein zweiter Stepper.

## 2. Gegenwärtige technische Architektur

- Observer als eigener **iframe** in einem browserseitig verwalteten, verschiebbaren, skalierbaren Fenster. **Das hat einen zuvor reproduzierten Resize-Flackerloop durch NiceGUI-Updates behoben.** iframe und Fenstergeometrie nicht zurück in einen reaktiven `ui.card()`-Replay-Container verlagern.
- Ständiger Einstieg **„Observer“** unter LAB / RESEARCH in der Sandbox-Sidebar, auch ohne laufende Partie.
- **Home** oben links wählt Research-Modus; keine permanente Modus-Topnavigation. Spielerfilter Beide / Weiß / Schwarz bleiben zugänglich. Die gleiche Partie und aktuelle Replay-Position werden beim Moduswechsel beibehalten.
- **Replay Pulse:** Textwechsel-Fingerabdruck getrennt nach Weiß/Schwarz, Marker für starke Textwechsel und nicht ausgeführte Aktionen; vorhandener Textwechsel-Inspector mit den Originalbegründungen desselben Spielers und derselben Phase. Fehlende Textvergleichswerte bleiben echte Kurvenlücken.
- **Geometry:** 13×13-Go-Brett und Formationstimeline, diagonal angeordnete Steine, Anker/Verlängerung/Verdichtung/heuristischer Richtungswechsel. **Mirroring** nutzt sieben Transformationen: horizontal, vertikal, Haupt- und Gegendiagonale sowie 90°/180°/270°-Rotation. Für Antwortmuster enthält der Pilot exakte und approximative (≤ 1 Gitterfeld) Treffer, Serienhinweise und eine experimentelle Bayes-Evidenzspur. 
- **Geometry Styles 17:** innerhalb des Geometriemodus wählbar: bisherige Formationen, **Spiegel · wenige Steine** (exakte Gegenfarben-Partner) und **Spiegel · große Flächen** (annähernde Zuordnung mit max. einem Gitterfeld Abweichung; jedes Gegenfarben-Gegenstück höchstens einmal verwenden). Die Beziehung von Weiß und Schwarz ist eine andere Metrik als eine Diagonale innerhalb einer Farbe. Im Browser sichtbar und positiv bewertet.
- **Andere Modi** wie Semantic Dynamics, Process und Observer Compare/SubQ/GPT waren zunächst ausdrücklich **Clickdummy-Vorschauen**. Keine automatischen KI-API-Aufrufe und keine erfundenen Modellbefunde. Demos sind keine Live-Analysen.
- Für die Geo-Darstellung werden vorhandene Replay-`frames` / 13×13-Go-Matrizen verwendet. Historische Brettzustände sind teils **rekonstruiert**, nicht als Original-Snapshots unabhängig verifiziert; Original-GO- und Replay-Zeitachsen gegen Fehlversuche/Resume/Refund absichern.

## 3. Neueste Fixkette (nicht blind überschreiben)

| Folge | Gegenstand | Stand |
|---|---|---|
| MIRROR16 | Antwort-Mirroring, sieben Transformationen, Verdachtszähler, Mini-Brett-Referenz/Ziel/Antwort | Explorer im Browser gezeigt |
| STYLES17 | Exakte Gegenfarben-Paare für wenige Steine; approximative großflächige Muster | UI im Browser gezeigt |
| ORIENTATION18 | 90° Grunddrehung des Mini-Bretts | Nutzer meldete anschließend **um 180° gegensinnige Darstellung** |
| **ORIENTATION19** | Drehrichtung von Fix18 korrigiert; dieselbe Transformation für Mini-Brett-Steine und Highlight-Ringe | letzter bereitgestellter Installer; Nutzer antwortete „ok super“, **explizite Umkehr-Button-/Koordinaten-Abnahme noch nicht protokolliert** |

**Letzter Zielpfad:** `andy/features/replay/views/andy_observer_pulse01.py` auf Sandbox 8082.  
**Erwarteter SHA-256 nach ORIENTATION19:** `3ff2e39838db3dcc53943cd95a2762865b2b494ec8fc0875efcab59c7e383500`.  
Vorheriger SHA-256 nach ORIENTATION18: `54ed59c4804b850070fd3ad034b8a60d1851095851880bb554720d171647a0f6`.

**Wichtig:** Die Python-Installer `INSTALL_ANDY_OBSERVER_MIRROR16.py`, `INSTALL_ANDY_OBSERVER_STYLES17.py`, `INSTALL_ANDY_OBSERVER_ORIENTATION18.py` und `INSTALL_ANDY_OBSERVER_ORIENTATION19.py` wurden im Chat als Downloads bereitgestellt. **Ihre Ablage im Repository oder aktuelle Präsenz auf dem lokalen Mac ist hier nicht bestätigt.** Nicht aus diesem Dokument folgern, dass Quellcode bereits in GitHub committed ist. Der jeweilige Installer prüft vor dem Patch den erwarteten Quellhash, startet als Dry Run, erzeugt bei `--apply` Backups unter `.andy_sync_backups` und unterstützt gesicherten Rollback. Wenn der lokale SHA abweicht, **stoppen und prüfen**, nicht erzwingen.

## 4. Forschung: Was die Anzeigen aussagen – und was nicht

**Formationslänge** zeigt geometrische Linien, nicht bewusstes strategisches Vorgehen. **Gegenfarben-Paare** zeigen räumliche Entsprechungen unter Transformation, nicht zwingend reaktive Nachahmung. **Antwort-Mirroring** zeigt passende zeitliche Einzelzüge oder Serien, nicht automatisch ein überzufälliges Gesamtmuster. Statische und dynamische Spiegelung können für dieselbe Partie unterschiedliche bevorzugte Achsen zeigen.

Claudes experimentelles Bayes-Update berücksichtigt acht Hypothesen (sieben Transformationen + keine Spiegelung), mit Startprior 1/8, `Q=0.6` und `LEAK=0.03` als **provisorischen** Annahmen. Für ein wissenschaftlich interpretierbares Posterior fehlen derzeit insbesondere ein belastbares, phasen-/geometrie- und legalitätsabhängiges `p_null`, geprüfte Likelihoods und Kalibrierung. **Weder Posterior noch Ampelfarbe als Beweis für Agentenintention ausgeben.**

Zweiter zentraler offener Punkt (vom Nutzer ausdrücklich auf später vertagt): **Wann ist die beobachtete Spiegelstruktur gegenüber zufälligen Anordnungen bei gegebener Steindichte und Brettgeometrie auffällig?** Große Flächen erzeugen viele Partner durch Belegung, Konstruktionssymmetrie und Hubs. Zu prüfen: besetzungs-/farbenbedingt erwartete Treffer, Spielphase, lokale Flächengröße, einfache Zufallskontrollen, Nullmodell über legale Züge und spätere multiple Vergleiche über 100 Partien. Aus anderen Experimenten wurde berichtet, dass bei 42 statischen Mehrfachtests kein Befund nach Korrektur signifikant blieb; **keine Bestätigung** einer Spiegelstrategie daraus ableiten.

## 5. UI-/Orientierungsvertrag (sehr wichtig)

**Mini-Brett und großes ANDY-Brett müssen in der aktuellen Ansicht exakt gleich orientiert sein.** Der Hauptnavigations-**Umkehr-Button** ist Teil des Vertrags. Berechnungen laufen in festen Brettkoordinaten; erst das Zeichnen transformiert Steine, Referenzzug, Spiegelziel, tatsächliche Antwort, Achse, Partnerringe und Formationshighlights. Nach Orientation18 war die Ansicht **180° gegensinnig**; Fix19 soll das korrigieren.

**Nächste Browser-Abnahme:** dieselbe auffällige Partie in normaler und umgekehrter Hauptbrettansicht öffnen, mindestens 3 asymmetrische Steinpositionen im Mini- und Hauptbrett vergleichen, Ring-/Achsenlage prüfen und Marker→Replay testen. Kein stummes Raten der Blickrichtung. Bei unbekanntem Zustand „Orientierung ungeprüft“ melden.

## 6. Noch offene Aufgaben in sinnvoller Reihenfolge

1. **Orientation19 in Browser verifizieren**, inklusive Hauptbrett-Umkehr und Highlights; Screenshot-Beleg ergänzen. Keine Spiegelmetriken ändern, solange es nur um Darstellung geht.
2. **Belegbarkeit im Geometry-Modus verbessern:** Auswahl eines statischen Gegenfarben-Musters auch ohne neues Antwortzugereignis; konkrete Partnerpositionen auf dem kleinen Brett und optional später Hauptbrett markieren. Dieselbe Replay-Position behalten.
3. **Metriken schärfen:** Bei wenigen Steinen Paar- und Antwortmuster; bei vielen Steinen großflächige Übereinstimmung getrennt nach Dichte, Transformation, Toleranz und Spielphase auswerten. Auf Mehrfachmatching und Doppelerfassung achten.
4. **Lab-Schnittstelle definieren:** Versionierte Ergebnisdaten für **alle** Fälle, einschließlich Nicht-Treffer und Unsicherheiten, nicht nur Alerts. Einheitliche Parameter und Kontrollbeispiele für übergreifende Auswertung von 100 Partien.
5. **Weitere KI-Observer (SubQ/GPT)** erst schrittweise auf belegte Ereignisse anwenden; keine automatischen API-Aufrufe im Replay-Steuerpfad.
6. **Verbindliche Regression:** Replay vorwärts/rückwärts/Slider/Autoplay, Matchwechsel, Home/Moduswechsel, Spielerfilter, iframe-Größe und -Position, Umkehr, Marker→Brett sowie Factory-Schutz prüfen.

## 7. Technische Sicherheitsregeln

- Nur Sandbox `8082`; **8080/8083 nicht patchen oder synchronisieren**.
- Keine DBs, JSONL-Originalpartien, Konfigurationen, Secrets oder Symlinks zwischen Instanzen kopieren.
- Engine und tatsächliche Spielaktion unverändert, read-only Analyse; kein Observer-Rückkanal an spielende Agenten.
- SHA-geschützte Minimalpatches mit Dry Run, Backup, Rollback; tatsächliches Browser-Verhalten prüfen.
- **Feature-Gates nach realen Rollen/Ports testen** – identischer Code kann zwischen 8082 und 8080 unterschiedlich wirken; siehe [Feature-Gate-Fall](./ANDY_SYNC_FEATURE_GATE_CASE_2026-11-21.md) und [Regression-Policy](./ANDY_DEVELOPMENT_REGRESSION_POLICY_2026-11-21.md).
- Dieses Dokument ist der **Dokumentations-Snapshot** des Forschungs-/Entwicklungsstands, **keine bestätigte 8080-Freigabe**.

## 8. Für einen neuen Thread

**Arbeitsstand: ORIENTATION19, nicht 0.7.** Beim nächsten Schritt zuerst den Quellhash und die echten Replay-/Go-Datenadapter lesen. Bestehende iframe-Fenstertechnik und die in der Arena funktionierende Klicknavigation **bewahren**. Kein erneutes Grundsatz-Brainstorming statt konkreter Weiterentwicklung. Die explizit verschobene Forschung zur statistischen Spiegel-Schwelle nicht als bereits erledigt darstellen.
