# WPS-02 · Gemeinsame Arbeitscheckliste

**Projekt:** ANDY verstehen – interaktives HTML-Handbuch  
**Quelle der Wahrheit für geplante Änderungen:** diese Datei  
**Stand:** 11. November 2026 · HTML-Durchmarsch V1.7  
**Status:** Arbeitsfassung / keine fachliche G1-Freigabe

> **So arbeiten wir:** Oliver und GPT machen zunächst einen schnellen gemeinsamen Durchmarsch. Wir führen Änderungswünsche hier dauerhaft zusammen, setzen sie direkt im HTML um und prüfen die Darstellung im Browser. Qwen und DeepSeek kommen bei konkreten Fachfragen hinzu. **Ein Häkchen bedeutet „umgesetzt“, nicht automatisch „im Browser geprüft“ oder „als offizielle ANDY-Regel bestätigt“.**

## Neue Dokumentationsstruktur · 11.11.2026

- [x] **DOC-01 · Neue HTML-Demo mit fünf Hauptbereichen:** [ANDY / Docs](https://andy-arena-com.github.io/andy-wps-collaboration/andy-dokumentation.html) (Intro, Arena, Lab, Regeln, Schwierigkeit). Separat unter `docs/andy-dokumentation.html`.
- [x] **DOC-02 · Bisherige Prototypen erhalten:** `docs/durchmarsch.html` und `docs/verstehenstest.html` nicht gelöscht; Links in der neuen Demo vorhanden.
- [x] **DOC-03 · Erste Demobefüllung vorhanden:** responsive Seitenleiste, Überblick, Start-/Replay-Anleitungen, Cockpit-Orientierung, Lab-Begriffe, APS-Struktur und Schwierigkeitsthema.
- [ ] **DOC-04 · Oliver prüft neue Struktur im Browser:** Reihenfolge, Informationsmenge und Auffindbarkeit testen.
- [ ] **DOC-05 · Bedienungsseiten an aktuelle Arena/Lab-Oberfläche angleichen:** konkrete Schaltflächen, Ansichten und Screenshots verifizieren.
- [ ] **DOC-06 · Kanonisches, engineverifiziertes Markdown-Regelwerk erstellen und inhaltsgleich als HTML veröffentlichen.**

## Direkte Integration der Qwen-/DeepSeek-Inputs

- [x] **I01 · Kapitel 03 mit Rosetta-Eckenbeispielen ergänzt:** A1 ↔ c3/d3/c4/d4 und E4 ↔ g6/h6/g7/h7 als Qwens vorläufige Koordinatenhypothese; noch nicht Engine-bestätigt.
- [x] **I02 · Kapitel 05 als vierteilige Mechanik-Demo erweitert:** Ausgangslage (Läufer E4), Go-Stein, mögliche Diagonalwirkung, ANDY-Synthese; vor/zurück innerhalb der Beispielsequenz.
- [x] **I03 · Geprüfte vs. hypothetische Inhalte sichtbar getrennt:** Diagonalblockade ausdrücklich **nicht** als gültige ANDY-Regel ausgegeben.
- [ ] **I04 · Oliver testet Verständlichkeit direkt am überarbeiteten HTML-Durchmarsch V1.7** und benennt Unklarheiten an konkreten Bildern/Erklärungen.
- [ ] **I05 · Vor fachlicher Veröffentlichung:** Ecken-Koordinaten und die Go-Schach-Diagonalwirkung am Engine-State prüfen; Verifikationsprotokoll [TEST-KOPPEL-01](tests/TEST-KOPPEL-01.md).

## Verständnistest für unvorbereitete Leser

- [x] **U01 · Eigene Demo veröffentlicht:** [HTML-Verständnistest V0.1](https://andy-arena-com.github.io/andy-wps-collaboration/verstehenstest.html) · eigenständige Teststrecke mit fünf Fragen, einer Erklärung erst nach der eigenen Antwort und Selbstbeurteilung „verstanden / noch unklar“.
- [x] **U02 · Bestehendes Handbuch unverändert erhalten:** Link zum neuen Test ist im HTML-Header ergänzt, Hauptnavigation und bisherige Kapitel bleiben bestehen.
- [ ] **U03 · Oliver als erster Testleser:** Alle fünf Schritte ohne Hilfe durchgehen und zum Schluss den Ergebnistext aus dem Test hier zurückgeben.
- [ ] **U04 · Erkenntnisse aus dem Test:** Für jeden Schritt festhalten, was bereits ohne Erklärung klar ist, was die Erklärung verbessert und was auch danach unklar bleibt.
- [ ] **U05 · Erst auf Grundlage von U03/U04 über Reihenfolge, zusätzliche Grafiken und Fachdetails entscheiden.**
- [ ] **U06 · Browserfunktion prüfen:** Interaktive 16-Go-/3-Schach-Demo und Bericht-Kopierfunktion ausführen; Quelltext-Syntax allein ist kein Browsertest.

## Laufender gemeinsamer Test

- [x] **T01 · Review-Auftrag an Qwen und DeepSeek vorbereitet:** [T01 – HTML V1.5, Kapitel 03/04](reviews/T01-QWEN-DEEPSEEK.md)
- [x] **T01-Q · Qwen-Feedback erhalten:** Quelltextzugriff nur eingeschränkt; keine Engine-Verifikation oder tatsächliche Demo-Bedienung. Hinweis zu vorläufigen Koordinaten und Doppelrolle.
- [x] **T01-D · DeepSeek-Feedback erhalten:** Website-Text und Quelltext gelesen, keine Bedienung der Demo; Vorschläge für visuelle Koordinatenerklärung, Vorher-Nachher-Wirkung und Übergang Go → Schach.
- [ ] **T01-I · Rückmeldungen mit Oliver priorisieren und in HTML + Checkliste übernehmen:** V1.6 enthält vorläufige Koordinatenkennzeichnung, präzisierte Doppelrolle und sichtbaren Ebenenübergang; regelgeprüfte Diagramme sind noch offen.**

### Erkenntnisse aus T01 · 11.11.2026

- [x] **T01-01 · Transparenz des Zugriffs:** Beide Reviewer haben weder die animierte Seite bedient noch die Demo im Browser vollständig getestet. Qwens Zugriff bezog sich teils auf frühere/andere Inhalte; daraus folgt **keine** Bestätigung von V1.5.
- [x] **T01-02 · Koordinaten vorsichtig formulieren:** In HTML V1.6 als vorläufig gekennzeichnet; `E4` (Schachfeld) und `e4` (Go-Knoten) nicht als identischer räumlicher Ort darstellen.
- [x] **T01-03 · Demo-Übergang beschriften:** In V1.6 ab 16/16 Steinen sichtbare Statuszeile Go-Setup abgeschlossen → Schachphase, Go-Steine bleiben.
- [x] **T01-04 · Quelle der Demo transparent machen:** In V1.6 am Kapitel 04 ausdrücklich als nicht engineverifizierte Illustration erläutert.
- [ ] **T01-05 · Exaktes Doppelwirkungsbeispiel:** Verifiziertes Vorher-Nachher-Diagramm zeigen; **keine** ungeprüfte Annahme „Go-Stein blockiert Turmzug“.
- [ ] **T01-06 · Koordinaten direkt am Diagramm illustrieren:** Eine konkrete Feld-/Knoten-Markierung auf *tatsächlich unterschiedlichen geometrischen Elementen*. DeepSeeks Formulierung „gleicher Ort“ ist ungeprüft und potenziell falsch.
- [ ] **T01-07 · Technische Fachbestätigung:** Qwen braucht die tatsächlichen Engine-/Controller-Quellen oder getestete Zustandsdaten; HTML-Lesezugriff allein reicht nicht.
- [ ] **T01-08 · Browser-Durchlauf:** Oliver und GPT müssen die tatsächliche 16+3-Demo anhand der gerenderten Website prüfen; reine Syntax- und Source-Checks reichen nicht.

### Arena-Referenz · 11.11.2026

Zwei Screenshots der **laufenden ANDY-Arena** zeigen die Standardansicht mit Weiß unten und die um 180° gedrehte Ansicht. Sie dienen ab jetzt als visuelle Referenz für die HTML-Koordinaten.

- [x] **R01 · Schach-A1 / Go-a1 klar unterscheiden:** In Standardansicht liegen beide aus Weiß-Perspektive links unten, aber **A1** ist das untere linke Schachfeld innerhalb der 8×8-Zone, **a1** der untere linke Go-Gitterknoten. Groß-/Kleinschreibung trennt die Geometrien.
- [x] **R02 · Brettdrehen ändert nur Ansicht, nicht Adresse:** Bei 180°-Drehung erscheinen A1 und a1 auf dem Bildschirm oben rechts; ihre festen logischen Adressen bleiben unverändert.
- [ ] **R03 · Kapitel 03: Drehbutton als didaktische Ergänzung:** Erst nach korrekter Standardansicht einbauen; bei Drehung Schach- und Go-Koordinaten samt Figuren/Leitpunkten gemeinsam transformieren.
- [ ] **R04 · Screenshot-Abgleich:** Aktuelle HTML-Standardansicht mit beiden Arena-Screenshots vergleichen, insbesondere fünf Leitpunkte, Schachzone, Abstand der Beschriftungen und Ausrichtung. Bildreferenzen liegen in Olivers Chat, nicht im Repository.

### Zweite Rückmelderunde · Kandidat für die erste echte Kopplungsregel

- [x] **K01 · Hypothesen H1/H2/H3 und didaktisches Vier-Bilder-Konzept dokumentiert:** [TEST-KOPPEL-01](tests/TEST-KOPPEL-01.md).
- [x] **K02 · Geometrische Unstimmigkeit markiert:** Aus Qwens A1-Eckenregel folgen für E4 die Go-Ecken g6/h6/g7/h7; g7 grenzt damit an D4/E4/D5/E5. Qwens abweichende Zuordnung nicht ungeprüft übernehmen.
- [ ] **K03 · Ecken-/Offset-Zuordnung gegen Arena/Engine prüfen:** Qwens „Rosetta-Tabelle“ erst nach Bestätigung in Kapitel 03 übernehmen.
- [ ] **K04 · TEST-KOPPEL-01A/B:** Die Diagonalblockade (H1) mit reproduzierbaren Engine-Zuglisten und Kontrollstellung bestätigen oder widerlegen.
- [ ] **K05 · TEST-KOPPEL-01C:** Prüfen, ob Schachfiguren Go-Freiheiten beeinflussen (H2); nicht voraussetzen.
- [ ] **K06 · Verifiziertes Lehrbeispiel:** Nach erfolgreichen Tests DeepSeeks vier Schritte (Vorher, Go-Aktion, Wirkung, ANDY-Synthese) mit echten Zustandsdaten in das HTML-Handbuch integrieren.
- [ ] **K07 · Weitergabe an Qwen/DeepSeek:** Gezielt das korrigierte Testprotokoll mit Hinweis auf den Koordinatenfehler schicken; noch keine Engine-Abnahme behaupten.

## A · Jetzt prüfen und korrigieren (höchste Priorität)

- [ ] **A01 · Hauptnavigation im Browser prüfen:** Linke Kapitel-Navigation muss auf Desktop sichtbar bleiben; auf Mobilgeräten gut bedienbar. In V1.1 im Code vorhanden, aber nach Olivers Meldung über eine verschwundene Navigation noch nicht visuell bestätigt.
- [ ] **A02 · Fünf Go-Leitpunkte auf allen Brettansichten prüfen:** dauerhaft sichtbar, korrekt auf Kreuzungen und ohne Konflikt mit gesetzten Steinen; exakte Koordinaten mit dem Arena-Brett abgleichen.
- [ ] **A03 · Go-Steine auf Schnittpunkten prüfen:** keine Steine mitten in Schachfeldern; Position und Größe bei responsivem Layout prüfen. Falls nötig das Brett als durchgängige SVG-Ebene statt CSS-Raster umsetzen.
- [ ] **A04 · Demo in Kapitel 04 vollständig im Browser durchlaufen:** ein Start-Klick, automatisch 8 schwarze + 8 weiße Go-Steine, danach exakt 3 Schach-Demozüge, dann Schlussstellung / Ende. Keine manuelle Platzierung oder Rückwärtsbuttons.
- [ ] **A05 · Doppelte Bedeutung der Go-Steine anschaulich machen:** früh erklären, welche konkreten Wirkungen dieselben Steine auf Go **und** Schach haben. Keine bloße Behauptung „zählen doppelt“ ohne belegte Regel und Bildbeispiel.
- [ ] **A06 · Startaufstellung und Koordinaten gegen die echte Arena vergleichen:** Weiß unten; Schach A–H und 1–8, Go a–m und 1–13; Schachzone und Figurenpositionen müssen exakt stimmen.

## B · Inhalt des HTML-Durchmarschs ausbauen

- [x] **B01 · HTML-first festgelegt:** interaktives Handbuch vor PDF-Export; später ggf. von der Homepage verlinkt.
- [x] **B02 · Kapitel 03 vereint Brett und Koordinaten:** kein eigenständiger Koordinaten-Menüpunkt.
- [x] **B03 · Brett konsequent monochrom:** nur die 8×8-Schachfläche kariert, äußere Brettfläche einheitlich grau.
- [x] **B04 · Kapitel 04 als automatische Demo statt manuelles Spiel:** Vorwärtsablauf im Quellcode umgesetzt; Browserprüfung unter A04 offen.
- [x] **B05 · Vorläufig 2 × 8 Go-Steine im Setup:** Code setzt acht schwarze und acht weiße Steine; Browserprüfung unter A04 offen.
- [ ] **B06 · Kapitel 01–02 kürzen und verständlich verdichten:** Pitch vollständig und ungeteilt; Ziel und Ergebnisarten konkret, ohne ungeprüfte Definitionen.
- [ ] **B07 · Kapitel 05 „Zugablauf“:** exakter ANDY-Aktionsrhythmus mit Go-/Schach-Abfolge, Legalität und Folgewirkungen.
- [ ] **B08 · Kapitel 06 „Anfang“:** nachvollziehbare reale oder enginegeprüfte Zugfolge mit Stellung davor/danach.
- [ ] **B09 · Kapitel 07 „Mitte“:** echte hybride Situation mit Wechselwirkung und getrennten Schach-/Go-Ebenen.
- [ ] **B10 · Kapitel 08 „Ende“:** reale Endstellung inkl. Ergebnisursache und Matchcode.
- [ ] **B11 · Kapitel 09 „Ergebnisarten“:** KO / TKO / TECH, Aufgabe, Remis und neutrale Abbrüche anhand Controller- und Engine-Code erklären.
- [ ] **B12 · Titel/Marke:** offizielles ANDY-Arena-Logo integrieren; Titel darf farbig sein, Brettdiagramme im Inhalt bleiben grau/schwarz-weiß.
- [ ] **B13 · Didaktische Qualität:** kurze Texte direkt neben Brett, schrittweise Vorher-/Nachher-Animation, keine erfundenen ANDY-Regeln.

## C · Fachliche Verifikation (gezielt mit Qwen / bei Bedarf DeepSeek)

- [ ] **C01 · Aktuelle Engine und Matchcontroller-Revision feststellen** (Commit/Version/Regelkonfiguration).
- [ ] **C02 · Go-Setup klären:** Sind 8 Steine pro Seite und alternierende Setzungen exakt implementiert? Gibt es Startknoten-/Abstands-/Besetzungsregeln?
- [ ] **C03 · Doppelwirkung definieren:** Wie beeinflussen Go-Steine konkret Schachfelder, Figuren und Zuglegalität? Mit Codepfad und Beispielen.
- [ ] **C04 · Go-Siegprüfung:** Existiert eine feste Kontrollschwelle? Wenn ja: tatsächlicher Zahlenwert, Messung, Prüfzeitpunkt und Ergebniscode.
- [ ] **C05 · Matt vs. Go-Sieg, gleichzeitige Endbedingungen, Patt und Remis** anhand der Implementierung klären.
- [ ] **C06 · KO / TKO / TECH / illegale Züge / Budget / API-Abbruch:** Engine-Status, Controller-Endursache, Arena-Anzeige und Leaderboard-Wertung auseinanderhalten.
- [ ] **C07 · Verlässliche Replay-Zustände** für Anfang, Mitte und Ende bereitstellen. Kein Schema-Diagramm als reales Match ausgeben.
- [ ] **C08 · Fachfreigabe G1** erst nach fachlich geprüften Regeln, Beispielen und Olivers ausdrücklicher Zustimmung.

## D · Veröffentlichung und Weiterverwendung

- [x] **D01 · Öffentliches Repository als lesbare gemeinsame Arbeitsbasis** angelegt: `ANDY-Arena-com/andy-wps-collaboration`.
- [x] **D02 · GitHub-Lesetest mit Qwen** erfolgreich.
- [ ] **D03 · GitHub Pages im Browser inkl. Navigation und Demo gegenprüfen** – GitHub-Datei/JS-Syntax allein beweisen keinen Laufzeittest.
- [ ] **D04 · Link von ANDY-ARENA.COM** auf den HTML-Leitfaden, sobald Oliver die öffentliche Darstellung akzeptiert.
- [ ] **D05 · Später HTML → druckbares PDF**, mit statischen, monochromen Diagrammen aus denselben Quellen.
- [ ] **D06 · Langfristig Kapitelmaterial in die private, verbindliche Redaktion** `andy-working-papers` übernehmen und freigeben.

## Entscheidungen, die wir bereits getroffen haben

- **Durchmarsch statt kapitelweisem Freeze:** Erst Gesamtverständlichkeit erreichen; redaktionelle Detailfreigaben folgen später.
- **HTML-first:** Interaktivität ist erwünscht. PDF bleibt späterer Veröffentlichungsweg.
- **Schach/Go getrennt:** Schachfelder A–H / 1–8; Go-Knoten a–m / 1–13, Weiß unten.
- **Kapitel 03:** gesamte Bretterklärung **einschließlich** Koordinaten.
- **Kapitel 04:** automatische Vorführung, nur ein Start-Klick; erst Go-Setup (8 + 8), dann drei Schachzüge, dann Ende.
- **Brettgestaltung:** nur das Schachfeld kariert; alle Lehrbretter monochrom; fünf Go-Leitpunkte sichtbar.
- **Team:** Oliver und GPT treiben den Durchmarsch. Qwen für konkrete Engine-/Regelfragen; DeepSeek nur bei Bedarf.

## Neue Punkte ergänzen

Neue Anforderungen bitte mit fortlaufender ID als Checkbox ergänzen, möglichst mit **Kapitel**, **beobachtetem Problem**, **gewünschtem Ergebnis** und **Prüfkriterium**. Bei Umsetzung Häkchen setzen; bei fehlendem Browser-/Engine-Test ausdrücklich offen lassen.

**Aktuelle HTML-Fassung:** [Durchmarsch](https://andy-arena-com.github.io/andy-wps-collaboration/durchmarsch.html)  
**Fachprüfung Ziele/Sieg:** [Kapitel-1-Entwurf](../content/wps-02/01-ziele.md)
