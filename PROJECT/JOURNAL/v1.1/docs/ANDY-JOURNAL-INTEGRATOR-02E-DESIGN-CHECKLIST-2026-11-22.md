# ANDY Journal · Integrator 2E — abgestimmte Design- und Abnahmecheckliste

**Stand:** 22.11.2026 · **Status:** Spezifikation / Gesprächsbasis, **kein Code-Release und keine WordPress-Änderung**.

## Ziel & Referenz

Die bestehende **private Aculia-Entwurfskopie #1362** ist der einzige gemeinsame Arbeitsentwurf. Die aktive Aculia-Startseite **#14** und die bestehenden Header-Vorlagen **#26/#532** sowie Footer **#455** bleiben geschützt. Der RGB-Pilot ist Content-/Funktionsreferenz. Die aktuelle **Arena-Homepage** `andy-arena.com/en/` ist visuelle Referenz für Flächen, Karten, Radien, Abstände und Button-Hierarchie, **nicht** zum Übernehmen ihrer Seitenstruktur.

**Widerspruchsanmerkung:** Im Chat wurden zwischenzeitlich sowohl ein schwarzer, nicht überlagernder Header als auch ein halbtransparentes Overlay genannt. Die *letzte ausdrückliche Nutzeranweisung zum Header* lautete: **„header ist nicht mehr halbtransparent, sondern Schwarz. Bild also nicht darunter.“** Der spätere Assistenten-Recap enthielt irrtümlich wieder einen halbtransparenten Header. Bis zu einer expliziten Änderung gilt deshalb: **schwarzer Header, Sliderbild startet darunter.** Vor einem Code-Apply diese Auslegung nochmals im Entwurf visuell abnehmen.

## 2E Aufgaben / Akzeptanzkriterien

- [ ] **Header:** dunkle/nahezu schwarze, eigenständige Leiste; Bild beginnt **unterhalb** des Headers, kein Overlay. ANDY-Journal-Logo bleibt Link zur Journal-Home. Header bleibt gut lesbar auch mobil und sticky; bestehende Logos wiederverwenden.
- [ ] **Navi:** horizontale Menülinks entfernen; rechts ein Burger mit **rechtem Flyout**, untereinander gestapelten Menüpunkten; Eintrag zur separaten `www.andy-arena.com`-Homepage. Redundanten Home-Menüpunkt entfernen, da Journal-Logo bereits Journal-Home öffnet. Tab/Fokus/Escape/Außenklick/Scroll-Lock und Mobile berücksichtigen.
- [ ] **Sprache:** bisherige **Flaggensymbole** beibehalten; Sprachwechsel nicht als Text-only DE/EN ersetzen. Tatsächliche Sprachumschaltung nicht vortäuschen.
- [ ] **Hero:** 3 Slides und bisherige Slider-Komponente; Höhe gegenüber aktuell gezeigter Vorschau um **ca. 20 %** senken, am früheren nativen HOME-01-Zustand gegenprüfen. Einheitliche Bildfläche mit `object-fit: cover` bzw. widgetspezifischem `background-size: cover`; keine Bild-Unterkante oberhalb des Slider-Containers und keine Layoutsprünge. Motiv-/Text-Crop bei mehreren Breakpoints prüfen.
- [ ] **Slider-Steuerung:** Pfeile am **unteren Rand / direkt unter dem Hero**, nicht mitten im Bild oder über dem Inhalt. Navigationsbuttons an der unteren Kante ausrichten, nicht als freischwebende Overlay-Controls.
- [ ] **Vierer-Teaserreihe:** vorhandene vier Aculia-Karten als Sektion erhalten. **Gleich hohe Karten und CTA-Ausrichtung** bei gleichbleibender Inhaltshöhe, mittelgrau/hellgraue umgebende Fläche, weiße Karten, dezente Border/Shadow, **abgerundete Ecken**, konsistente Abstände. Bilder thematisch ersetzen erst in kontrolliertem Medienpass; keine Stock-Medien als finale Freigabe.
- [ ] **Fight Night:** Abschnitt **unmittelbar nach der Viererreihe**, deutlich eigenständiger (z.B. tiefes Rot/Bordeaux), **prominenter/höher** als bisher. Bestehende Tabs/Content-Struktur funktional erhalten, wenn möglich echten Match-/Replay-Hook integrieren statt Demo-Videoplayer zu behaupten. Über dem Abschnitt freistehendes Motto: **“Every AI has a plan until it gets punched in the Andy-Arena”** (redaktionelle Formulierung exakt). Keine falschen Match- oder Forschungszahlen.
- [ ] **Arena-Designattribute:** hellgraue Seitenflächen als Bühne für weiße Cards; sinnvolle Radius-, Spacing-, Schatten- und Border-Tokens, Navy als Primärkontrast. **Blau für Replay/sekundäre Interaktion**, **Grün für primäre positive Aktion**, weitere Tokens am Arena-Original-CSS überprüfen (Screenshots liefern keine belastbaren exakten Farbwerte).
- [ ] **Weitere Home-Sektionen:** Reihenfolge und **bestehende Aculia-Widgets für Academy, Research, Perspectives, Tools etc. nicht neu gestalten und nicht ersetzen**. Nur nötige Integrations- und Strukturkorrekturen; kein Transfer der alternativen Assistant-Bildkomposition.
- [ ] **Behind ANDY:** atmosphärischer, großer eigenständiger Abschlussbereich direkt **vor dem Footer** nach der besprochenen Visual-Referenz; mit echten ANDY-Bezügen und geklärten Medienrechten.
- [ ] **Footer:** wirklich sichtbar; Links zu **Sitemap, A–Z und Themen/Tags** sowie notwendige Kontakt-/Rechtsseiten. Navigation konsistent, keine neu erfundenen Contentseiten.
- [ ] **Ein Zielentwurf:** kein vierter Entwurf, kein eigenes konkurrierendes Frontend. Draft #1362 bleibt privat. Alte Aculia-Templates und RGB-Daten unverändert.
- [ ] **QA:** Desktop / Tablet / Mobile, Sliderbild und -steuerung, Kartenhöhe, Flyout keyboard/Touch, Header-Sticky, Footer/Tags/A–Z, WordPress-Preview, RGB-Links und Root-UTM-Routing getrennt prüfen. Cache-/Theme-/Publishing-Hooks berücksichtigen.
- [ ] **Schreib-Gate:** Vor jeder Änderung Hash-/Status-Abgleich, Backup und explizite Admin-Freigabe; Änderungen ausschließlich auf freigegebenen Draft scope; Rollback. Keine Änderung an öffentlicher Arena oder Journal-Domain.

## Grenzen

Diese Checkliste ist **nur** die Sammlung und Priorisierung der Nutzerwünsche. Weder eine neue Version **Integrator 2E** noch ein Browser-Test oder WP-Apply wurde mit diesem Dokument ausgeführt.

Nächste sinnvolle Umsetzung: die vorhandenen Aculia-Elementor-IDs und -CSS-Klassen lesen, Design-Tokens gegen tatsächlichen Arena-CSS-Bestand abgleichen und erst danach **einen reversiblen 2E-Preview-Patch** für genau #1362 implementieren. CSS-/JS-Overrides nur in der authentifizierten Draft-Vorschau; keine globale Header-/Theme-Änderung.
