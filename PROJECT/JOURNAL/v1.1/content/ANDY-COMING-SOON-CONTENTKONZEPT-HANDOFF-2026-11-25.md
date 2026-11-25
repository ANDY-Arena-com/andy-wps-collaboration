# ANDY Journal – Coming Soon: redaktioneller Content-Handoff (DE/EN)

**25.11.2026 · Auftrag für den separaten Content-/Konzept-Thread · v0.1 · Redaktionelles Briefing, keine öffentliche Freigabe**

> **Konkreter Auftrag:** Ein konsistentes, hochwertiges, zweisprachiges **Coming-Soon-Contentkonzept** für die *bereits vorhandene* ANDY-Journal-Home und ihre fünf öffentlichen Themen-/Gabelbereiche ausarbeiten. **Kein neues WordPress-Plugin, keine separate Coming-Soon-Homepage, kein Eingriff in Website oder Veröffentlichungszustände.**

**Aktueller, nutzerseitig belegter technischer Meilenstein:** Am 25.11.2026 zeigt ein WordPress-Backend-Screenshot auf **\`journal.andy-arena.com\`** die Überschrift **„ANDY Journal · Launch Control 0.2.0“** und den fünften Tab **„Publication & Coming Soon“**, darin den Abschnitt **„ANDY Publication & Coming Soon · PRE-STAGING-01C1“**. Im sichtbaren Beispiel steht **Fight Night** im Zielzustand (Planung) **„Intern“**; DE/EN-Titelfelder sind sichtbar. **Belegt ist damit die Installation und Erreichbarkeit der Oberfläche**, nicht das Speichern aller Felder, eine erfolgte Publikation oder eine Freigabewirkung. Screenshots gehören zum Gespräch, nicht als öffentliche Assets ins Repository.

## 1. Verbindliche Architektur / Stand

- **Live:** \`journal.andy-arena.com\` – WordPress-Backend, Editing und Frontend nach Nutzerbericht funktional. **Arena:** \`andy-arena.com\` bleibt eigenständige HTML-Website und wird nicht ersetzt.
- **Staging:** \`staging-journal.andy-arena.com\` ist eine **geplante** geschützte eigenständige WordPress-Kopie, nicht als eingerichtet bestätigt. **Vor dem Klon** werden die gemeinsame technische Grundlage und die spätere Freigabelogik vorbereitet.
- **Gleicher Auftritt:** Live und Staging sollen dieselbe **Home in DE und EN mit denselben vorhandenen Plugins, Modulen, Bild- und Layoutregeln** nutzen. Nur Daten, Inhalte und Veröffentlichungszustände unterscheiden sich.
- **Ein Datenfluss:** **Native WordPress-Inhalte → Gabelseiten → Home**. Kein doppeltes CMS, kein zweiter Home-Builder, keine eigenen parallelen „Coming-Soon-Artikel“ als notwendige Voraussetzung.
- **Eine technische Steuerung:** Das bestehende **ANDY Launch Control 0.2.0** ist jetzt die *redaktionelle Planungsoberfläche*; die eigentliche Freigabe-/Zugriffsintegration (**PRE-STAGING-01C2**) ist noch **nicht** implementiert oder abgenommen.
- **Betriebszentrale:** Journal Cockpit (vom Nutzer mit 0.2.3 installiert gemeldet) bündelt Fachwerkzeuge; Home Composer 0.1.39 nutzerseitig positiv gesichtet, RGB Pilot 0.6.4 bestätigt, Content Composer 0.1.29 laut vorheriger Pluginliste. Hier **keine technische Änderung** verlangen.

**Technischer Source of Truth:** [Launch-Control-01C1-Releasevertrag](../ARCHITECTURE/ANDY-JOURNAL-PRE-STAGING-01C1-PUBLICATION-PLANNING-RELEASE-2026-11-25.md), [PRE-STAGING-Governance](../ARCHITECTURE/ANDY-JOURNAL-PRE-STAGING-ADMIN-UND-LAUNCH-GOVERNANCE-2026-11-25.md), [WP-ARCH R0.5 als historische Content-Architektur](../ARCHITECTURE/WP-ARCHITECTURE-R0.5.md). Ältere technische Statusangaben in historischen Dokumenten gelten nicht als installierter Versionsbeweis.

## 2. Zielbild: keine Baustellen-Website, sondern ein wachsendes ANDY Journal

Die Live-Home zeigt **dieselbe visuelle ANDY-Identität** wie die künftige Staging-Home. Für noch nicht geöffnete Bereiche erscheint im jeweiligen *bestehenden* Modul eine **inhaltlich interessante Einladung**: Was ist das Thema? Welche Frage treibt ANDY dabei an? Was werden Besucher künftig tatsächlich erleben oder erforschen können? Wodurch unterscheidet es sich von den anderen Bereichen?

Die öffentliche Ankündigung soll **einen eigenständigen Nutzen** haben, ohne unfertige Inhalte oder Ergebnisse als verfügbar auszugeben. Keine reine „Coming soon…“-Platzhalterflut. Der Dreiklang **„Erleben. Erforschen. Erahnen.“ / „Experience. Explore. Envision.“** ist eine mögliche kommunikative Klammer, die zur bestehenden ANDY-Marke passen muss; Sprachfassungen sind *redaktionell eigenständig*, keine automatisch wörtlichen Übersetzungen.

**Wichtig:** Ein Bereich darf im Konzept auch komplett **intern** bleiben. „Coming Soon“ ist keine redaktionelle Pflicht für jedes Modul, sondern eine bewusste Freigabeentscheidung. „Live“ bedeutet nicht, dass jeder thematisch zugeordnete Entwurf öffentlich werden muss.

## 3. Fünf Bereiche: Redaktionsbriefing

| Bereich | Was sollte die Ankündigung *erklären*? | Mögliche Leitfrage (Arbeitsvorschlag, nicht freigegeben) | Qualitätsgrenze |
|---|---|---|---|
| **Fight Night** | KI-Duelle, dokumentierte Entscheidungen, Replays, Spannungsmomente und die Möglichkeit, statt nur des Resultats den Verlauf zu verstehen | „Was erzählen uns die Wendepunkte einer Partie?“ | Keine erfundenen Matchausgänge, Turniere, Sieger, Videos oder Live-Features versprechen |
| **Academy** | ANDY-Spielidee Schach × Go, Regeln, Übungen, didaktische Pfade und eigene Entdeckungen | „Wie lernt man, auf einem Brett in zwei Logiken zu denken?“ | Fertige Lektionen/Player nur als verfügbar bezeichnen, wenn tatsächlich veröffentlicht und geprüft |
| **Research** | Aus Spielereignissen werden prüfbare Fragen: Methodik, Datenbasis, Unsicherheit, Evidenz, Grenzen | „Wie wird aus einem beobachteten Zug ein belastbarer Befund?“ | Keine Forschungsergebnisse, Validierungen oder Zitationen erfinden |
| **Perspectives** | Problemgetriebener Transfer über die Arena hinaus; Crossover-Themen als **Fragen/Hypothesen**, nicht nachgewiesene Anwendungen | „Was lassen sich durch ANDY für Fragen außerhalb der Arena neu stellen?“ | Health, Token Economy, Agentic Commerce, Co-Creation, Adaptive Systems, Cybersecurity, Compliance/XAI und Datenresonanzpunkt nur passend zur belegten Quellenlage nennen; Letzterer im Bestand noch ohne eindeutig bestätigte Definition |
| **Making of** | Die Entstehung von ANDY als beobachtbare Mensch-KI-Zusammenarbeit: Rollen, Experimente, Irrtümer, Übergaben, Entscheidungen | „Wie wird aus vielen Werkzeugen und Perspektiven ein gemeinsames Projekt?“ | Keine privaten Rohdialoge, Systemzugänge, personenbezogenen Daten oder unterstellten KI-Erlebnisse veröffentlichen |

**Perspectives ≠ Research:** Externe, nachvollziehbare Fragen zuerst; mögliche ANDY-Analogie und deren Grenzen klar markieren. **Making of** ist die reflektierende, gestalterisch eigenständige Meta-Ebene, nicht nur eine Unterkategorie von Research/Perspectives.

## 4. Konkreter redaktioneller Lieferumfang (für den anderen Thread)

**A. Home-Ebene (DE + EN):**
1. Vorschlag für eine **übergreifende kurze Journal-Launch-Botschaft**, die zur bestehenden Home/Brand passt und keine zusätzliche Landingpage benötigt (je Sprache Hauptzeile, Unterzeile, optional redaktioneller Statushinweis).
2. Für **jeden der fünf Bereiche**: DE-/EN-Titel, kurzer **Home-Teaser** (ca. 25–50 Wörter je Sprache), optional sehr kurze 1-Zeilen-Fassung, ein verständlicher Statushinweis und eine geeignete CTA-Formulierung für den *späteren* Freigabemodus (z. B. „Bereich kennenlernen“ statt falscher „Jetzt starten“-Versprechen).
3. Für jedes Home-Modul klären: **Was ist der Nutzwert bereits jetzt**, was soll erst künftig erscheinen, und welche direkte Verlinkung wäre unter \`internal\` / \`coming_soon\` / \`live\` korrekt?

**B. Gabelseiten-Ebene (DE + EN):**
4. Pro Bereich eine **redaktionelle Coming-Soon-Vorstellung** (ca. 100–200 Wörter je Sprache): Grundidee, Besucherversprechen, geplante Inhaltsformen, Beispiel-Fragen, was noch nicht öffentlich ist, behutsamer Ausblick ohne falsches Datum. Die Texte sind **zunächst Konzeptmaterial**; die tatsächliche öffentliche Gabelseiten-Integration ist Teil von 01C2.
5. Pro Bereich 2–4 konkrete künftige **Contentformate oder exemplarische Themen**, eindeutig als geplante Formate statt verfügbare Artikel markiert.

**C. Bild-/Design-Ebene:**
6. Für die fünf Bereiche je eine knappe Bildidee bzw. ein **Image-Brief** (Motiv, Stimmung, Verhältnis zur bestehenden Farbwelt, gewünschter Ausschnitt, Alt-Text DE/EN, Rechte-/Provenienzbedarf). **Kein Bild generieren oder Assets austauschen**, solange die Gestaltung nicht gemeinsam abgestimmt ist.
7. Vorschlag, wie „Coming Soon“, „in Vorbereitung“ und bereits freigegebene Inhalte in den **bestehenden Karten/Modulen** unterscheidbar sind – ohne neues Navigations- oder Layoutkonzept.

**D. Redaktionelle Abnahme:**
8. Eine kompakte **DE/EN-Redaktionsmatrix** (fünf Bereiche × beide Sprachen) mit vorgeschlagenem Zielzustand, Home-Teaser, Gabelseiten-Text, CTA, Bildidee, offenen Aussagen/Quellen, Freigabestatus (**Entwurf**).
9. Kennzeichnung der Aussagen als **belegt**, **projektintern geplant**, **Hypothese** oder **noch offen**. Konkrete Daten/Leistungsversprechen nur, wenn verifiziert.

## 5. Exakte Schnittstelle zum derzeit installierten Launch Control 0.2.0

| Element | In 01C1 schon als editierbares Planungsfeld vorhanden? | Empfehlung |
|---|---|---|
| Fünf Bereiche | **Ja** | Namen unverändert beibehalten |
| Modus \`internal\`, \`coming_soon\`, \`live\` | **Ja – Planung, keine öffentliche Wirkung** | Anfangs keine aktiven Publikationsfreigaben annehmen |
| DE-Titel + DE-Kurz-Teaser | **Ja** | Nach redaktioneller Freigabe dort einpflegbar |
| EN-Titel + EN-Kurz-Teaser | **Ja** | Eigenständige Fassung, kein blindes Übersetzen |
| Optionale WordPress-Bild-ID | **Ja** | Nur geprüftes vorhandenes Mediathek-Asset eintragen; nicht aus Image-Brief herleiten |
| Längere Gabelseiten-Vorstellung | **Nein (nicht in diesem Launch-Control-Tab belegt)** | Als redaktionelles Material separat ausarbeiten; technische Einbindung in 01C2 planen |
| CTA-/Link-Ziele je Modus | **Nein (nicht als Feld dieses Tabs belegt)** | Erst konzipieren; keine direkten URLs/Links publizieren, bevor Routing freigegeben |
| Veröffentlichungshistorie / Rückzugsmarker | **Ja, separat vorbereitet** | Keine Veröffentlichung oder Datenmigration durch den Content-Thread |

**Release-Gate:** 01C1 speichert lediglich **Planungsdaten**. Ein ausformulierter Teaser **schaltet weder Home noch Gabelseiten noch Artikel frei**. Die Sicherheitsintegration für Direktaufrufe, Legacy-RGB, Suchergebnisse, REST, Feeds, Sitemaps, Sprachpartner und Cache ist **PRE-STAGING-01C2**, eigener technischer Auftrag. Noindex ist kein Zugriffsschutz. **Keine automatische Veröffentlichung**; bestehende WordPress-Post-Status/Entwürfe bleiben unverändert.

## 6. Arbeitsmodus / Handoff zwischen den Threads

- **Der Content-Thread ist Owner des redaktionellen Konzepts**, nicht des Plugin-Codes, der WordPress-Publikationssteuerung oder des Hostinger-Klons.
- **Lieferformat:** redaktionelles, reviewbares Markdown in \`PROJECT/JOURNAL/v1.1/content/\`, bevorzugt ein eigenständiges Dokument mit einem **DE-/EN-Paar pro Bereich** und einer vorgeschalteten Home-Klammer. Offene Texte/Entscheidungen klar kennzeichnen; frühere Story-Arbeit erhalten.
- **Keine direkte WordPress-Änderung** und keine öffentlichen Publikationsversprechen ohne explizite Abnahme. Eine spätere manuelle Übernahme der Kurztexte in Launch Control ist möglich; technische Auslieferung erst nach 01C2.
- **Keine Doppelarbeit:** Die technischen Implementierungsaufgaben (Home/Overview-/Content-Adapter, Zugriffsschutz, Historie, Staging) bleiben beim Entwicklungs-Thread. Der Content-Thread kann dem Technik-Thread benötigte zusätzliche Felder melden, ohne sie selbst zu implementieren.
- **Synchronisation:** Nach redaktioneller Iteration im Content-Thread den GitHub-Link samt freigegebenen, offenen und zurückgestellten Texten an den Technik-Thread geben; kein stiller Umbau beider Systeme.

## 7. Direkt verwendbarer Startauftrag für den anderen Thread

> Bitte übernimm das **Coming-Soon-Contentkonzept für das ANDY Journal** anhand dieses Handoffs. Erarbeite zuerst die **übergreifende Launch-Botschaft und fünf DE/EN-Bereichsprofile** für Fight Night, Academy, Research, Perspectives und Making of. Die vorhandene Home und ihr Design bleiben exakt bestehen; wir brauchen **redaktionelle Inhalte für die bestehenden Module** sowie Konzepte für spätere Coming-Soon-Gabelseiten, keine zweite Website und keinen Plugin-Code. Unterscheide kurze Launch-Control-Teaser von längeren Gabelseiten-Vorstellungen, markiere vorläufige Vorschläge und unbewiesene Aussagen, und liefere ein reviewbares Markdown inklusive DE/EN-Matrix, CTAs und Bildbriefings. **Nichts in WordPress veröffentlichen oder umstellen.**

### Quellen zur Fortsetzung

- [Launch Control 0.2.0: 01C1 Planungs- und Sicherheitsgrenzen](../ARCHITECTURE/ANDY-JOURNAL-PRE-STAGING-01C1-PUBLICATION-PLANNING-RELEASE-2026-11-25.md)
- [PRE-STAGING-Governance: ein System, Home/Gabelseite/Content](../ARCHITECTURE/ANDY-JOURNAL-PRE-STAGING-ADMIN-UND-LAUNCH-GOVERNANCE-2026-11-25.md)
- [WP-Architektur R0.5 / dynamischer Contentfluss](../ARCHITECTURE/WP-ARCHITECTURE-R0.5.md)
- [Making-of-Story-Katalog, MO01–MO12](ANDY-MAKING-OF-STORY-KATALOG-v0.1-2026-11-25.md)
- [Journal-Fachkonzept v1.1 (historischer strategischer Unterbau)](../docs/ANDY-JOURNAL-GESAMTKONZEPT-v1.1.md)

**Status zum Abschluss dieses Handoffs:** redaktioneller Auftrag und technische Grenzen dokumentiert; **keine Texte freigegeben, kein öffentlicher Launch, keine WordPress-Änderungen durch dieses GitHub-Dokument**.
