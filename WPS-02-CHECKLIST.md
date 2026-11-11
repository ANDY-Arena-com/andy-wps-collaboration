# WPS-02 · Gemeinsame Arbeitscheckliste

**Projekt:** ANDY verstehen – interaktives HTML-Handbuch  
**Quelle der Wahrheit für geplante Änderungen:** diese Datei  
**Stand:** 11. November 2026 · HTML-Durchmarsch V1.1  
**Status:** Arbeitsfassung / keine fachliche G1-Freigabe

> **So arbeiten wir:** Oliver und GPT machen zunächst einen schnellen gemeinsamen Durchmarsch. Wir führen Änderungswünsche hier dauerhaft zusammen, setzen sie direkt im HTML um und prüfen die Darstellung im Browser. Qwen und DeepSeek kommen bei konkreten Fachfragen hinzu. **Ein Häkchen bedeutet „umgesetzt“, nicht automatisch „im Browser geprüft“ oder „als offizielle ANDY-Regel bestätigt“.**

## Laufender gemeinsamer Test

- [x] **T01 · Review-Auftrag an Qwen und DeepSeek vorbereitet:** [T01 – HTML V1.5, Kapitel 03/04](reviews/T01-QWEN-DEEPSEEK.md)
- [ ] **T01-Q · Qwen-Feedback erhalten:** Setup 8+8, Leitpunkte, Doppelwirkung, drei Demo-Schachzüge
- [ ] **T01-D · DeepSeek-Feedback erhalten:** Verständlichkeit, didaktische Führung und fehlende Visualisierung
- [ ] **T01-I · Rückmeldungen mit Oliver priorisieren und in HTML + Checkliste übernehmen**

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
