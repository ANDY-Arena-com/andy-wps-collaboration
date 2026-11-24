# ANDY JOURNAL · WP-ARCH R0.4
**24.11.2026 | Journal v1.1 | Entwicklungscheckpoint und Roadmap**
Fortschreibung von [R0.3](WP-ARCHITECTURE-R0.3.md). R0.3 bleibt als historischer Architekturstand erhalten.

## 1. Baseline und Evidenz
Home Composer (HC) 0.1.30 EN-EDITOR-UI-ALIGN-01 und Content Composer (CC) 0.1.13 EDITORIAL-WORKFLOW-01 sind die im Entwicklungschat zuletzt vom Nutzer abgenommenen Versionen. Die Abnahme beruht auf Nutzerberichten und Screenshots der Hostinger-Testumgebung, nicht auf einer unabhängigen Live- oder Codeprüfung für dieses Dokument. Frühere im Chat berichtete Syntax-/isolierte Tests sind keine erneute Prüfung. Dieser Commit dokumentiert die Entwicklung, er enthält keine Plugin-Binaries und ändert keine Website.

## 2. Chronologie seit R0.3
| Version | Inkrement | Ergebnis / Grenzen |
|---|---|---|
| CC 0.1.8 | EXPERIENCE-MVP-01 | Asset & Language Lab: gemeinsame JSON-Zahlenreihe, lokalisierte Ausgabe, zwei Research-Posts #1489 / #1490; kein beliebiger ausführbarer Upload |
| CC 0.1.9 | LANGUAGE-ROUTING-01 | Flaggen, Sprachfilter, Sprachbox in nativen WP-Listen, Shared Header, optionales Routing veröffentlichter zugeordneter Posts |
| CC 0.1.10 | LANGUAGE-ADMIN-02 | Sprachpaarsortierung, ANDY-Template-Spalte, schmale Sprachspalten |
| HC 0.1.27 | FRAME-SHADOW-01 | Rahmenschatten abschaltbar; Außenfarbe und Abstand weiterhin konfigurierbar |
| HC 0.1.28 / CC 0.1.11 | LANGUAGE-E2E-01 | /de/, /en/, sprachabhängige Fight-Night-Mediathek, Koi-Übersetzungsentwurf, abschaltbares Routing |
| CC 0.1.12 | SHARED-MEDIA-01 | Bild/Titel/CTA in Mediathek verlinkt; gemeinsame WP-Beitragsbilder, keine automatische Synchronisierung eingebetteter Artikelbilder |
| CC 0.1.13 | EDITORIAL-WORKFLOW-01 | Gemeinsame Statusinformationen, DE-Zuordnung und fehlende EN-Arbeitskopien als Entwurf, interne Freigabe getrennt von Vorbereitung, Home-Vormerkung, Story-Identität/Dublettenlogik, Sprachwechsel nach Verfügbarkeit |
| HC 0.1.29 | MULTILINGUAL-HOME-01 | Ein Editor, EN-Textebene, verknüpfte native WP-Home-Entwürfe, zusätzliche obere Speichern-Buttons |
| HC 0.1.30 | EN-EDITOR-UI-ALIGN-01 | Gleiche Modulhülle, Typ/ID, Aktiv-Checkbox, alle öffnen/schließen, Sticky-Save, gesperrte Strukturcontrols in EN; Nutzer bestätigt Farbübernahme DE → EN |

## 3. Architekturprinzip: Shared Design – Localized Content
- Eine Modulstruktur und gemeinsame Gestaltung: Farben, Schriftgrößen, Bilder, Abstände, Übergänge, Reihenfolge und Layout werden im DE/Basis-Editor gepflegt. DE ist aktuell die Bedienoberfläche für gemeinsame Einstellungen, nicht ein eigenständiges zweites Design.
- Sprachabhängig: Titel, Texte, Button-Beschriftungen/-Ziele, Modulsichtbarkeit und Beitragsauswahl. EN kann unabhängig redaktionell bearbeitet werden. Neue Module, Reihenfolge und Entfernen bleiben in der Basis. Nicht unterstützte Altmodule in EN bleiben zunächst deaktiviert.
- WordPress-Seiten sind redaktionelle Anker (Home-Identität andy.journal.home); der Composer bleibt Quelle der Home-Konfiguration. Keine zweite Inhaltspflege und keine Kollision mit öffentlichen Routen. Entwurfspaare für weitere Gabelseiten sind offen.
- Native WP-Beiträge/Seiten und Content Manager greifen auf dasselbe Sprachregister zu. Story-ID + Sprache sind die fachliche Identität, separate WP-IDs bleiben erhalten. Sprachpaare sind keine Dubletten. DE/EN unabhängig veröffentlichen und Home freigeben.
- Gemeinsames Beitragsbild als Attachment-Referenz, gemeinsame registrierte Assets, Match-ID. Änderungen ungeprüfter Partner dürfen öffentliche Bilder nicht ungefragt überschreiben. Vollständig zentrale Faktenhaltung und rollenbasierte eingebettete Medien sind noch offen.
- Öffentliche Sprachwechsel nur zu verfügbaren freigegebenen Gegenstücken; Entwürfe nur für berechtigte Redakteure. Nicht vorhandene Übersetzungen nicht vortäuschen. EN-Arbeitskopien sind keine automatisch fertigen Übersetzungen.
- Globaler Shared Header, DE/EN für gesamte Journal-Kette; weitere Sprachen später ausschließlich Home, mit definiertem Einstieg nach DE/EN.
- Bestehende URLs erhalten, keine erzwungene Migration. Vollständige canonical/hreflang-, Such-, Cache- und Legacy-Strategie noch offen.

## 4. Modulregister / aktueller Umfang
| ID | Modul | Stand |
|---|---|---|
| MS-00 | Shared Shell | Nutzerabnahme; kontextbezogener DE/EN-Wechsel erprobt |
| MS-01 | Home Composer | DE/EN-Editor abgenommen |
| MS-02 | Gabelseiten | Fight Night Referenz; Research, Academy, Perspectives und native Seitenpaare ausbauen |
| MS-03 | Shared Content Core | Identität/Sprachworkflow erprobt; vollständiger gemeinsamer Faktenvertrag offen |
| MS-04 | Fight Night | Demo-Kette erprobt; echte öffentlich freigegebene evidenzbasierte Story offen |
| MS-05 | Academy | Interaktives Beispiel vorhanden; vollständige Kette offen |
| MS-06 | Research | DE/EN-Zahlenreihen-MVP erprobt; echte APP-basierte Analyse offen |
| MS-07 | Perspectives | Home-Modul / Konzept; erster vollständiger Beitrag offen |
| MS-08 | Social | Konzept |
| MS-09 | Content Manager | Editorial Workflow abgenommen |
| MS-10 | Content Bridge | Fight Night DE/EN erprobt; weitere Kategorien ausbauen |
| MS-11 | Asset Manager | JSON-MVP, gemeinsame Assets; Versionen, Typen, Inventar, sichere Uploads ausbauen |
| MS-12 | Language Manager | DE/EN-MVP abgenommen; vollständige Routing-/SEO-/Sucharchitektur offen |
| MS-13 | Evidence Bridge | APP-Anbindung und Freigabe echter Daten offen |
| MS-14 | Editorial Studio | Workflow-Basis vorhanden; Content-ZIP und Editorial Bible offen |

## 5. Making-of: Umwege als Erkenntnisquelle
| Beobachtung / Umweg | Konsequenz |
|---|---|
| Shared Header und unterschiedliche Templates mussten zusammengeführt werden | Eine globale Shell, keine konkurrierende Sprachsteuerung |
| Sprachverwaltung zunächst getrennt von WP-Listen | Gewohnte Flaggen, Filter, Sortierung und Template-Spalte in Beiträgen und Seiten |
| Änderungsdaten trennen Sprachpaare | Story-Identität statt Datum als Gruppierung |
| Aktiv wirkender Sprachwechsler ohne EN-Gegenstück | Existenz und Publikationsstatus entscheiden über Wechsel |
| Koi-Übersetzung zunächst Einzelfall; andere Beiträge ohne EN | Generischer Entwurfsworkflow, keine automatischen Veröffentlichungen |
| Interner Reiher-Pilot #1466 konnte nicht für Home vorgemerkt werden | Redaktionelle Vorbereitung von Freigabe und Publikation trennen; private Daten bleiben geschützt |
| Bild zunächst nur kopiert | Gemeinsame Bildreferenz und kontrollierte Synchronisierung |
| Englische Home zunächst fest definierte Pilotkonfiguration | Editierbare Sprachebene auf gemeinsamem Design |
| Lange Editor-Formulare erfordern Scrollen | Speichern oben an Expandern und unten |
| EN-Modulzeilen wirken anders als DE | Einheitliche UI, Strukturcontrols in EN sichtbar aber gesperrt |
| KI kündigte LANGUAGE-E2E-01 zweimal an, ohne installierbare ZIPs zu liefern; Nutzer intervenierte | Auslieferung nur mit überprüfbarem Artefakt, Teststatus und Grenzen; keine Ankündigung als Umsetzung ausgeben |

Making ANDY / Perspectives: Co-Creation im Selbstversuch, nicht nachträglich geglättete Erfolgsgeschichte. Menschliche Beobachtungen, Entscheidungen, KI-Fehler und Korrekturen sind Teil des Erkenntnisprozesses. Das Journal ist sowohl Instrument als auch möglicher Untersuchungsgegenstand. Agile Mona Lisa: iterativ und inkrementell in die Breite, nicht isolierte Module bis zur Perfektion ausbauen.

## 6. Nächste Schritte: priorisierte Roadmap (Vorschlag)
Ursprüngliches Ziel aus R0.3: Asset/Language/Core → Content-ZIP/Editorial Bible → echte Story → Research E2E. Inzwischen sind Asset- und Language-MVP sowie Fight-Night-Demo-Kette vorhanden; jetzt FIRST COMPLETE EXPERIENCE in die Breite statt weiterer Home-Kosmetik.
1. **GABEL-E2E-02 (MS-02/10/12)**: Research, Perspectives und Academy als schlanke dynamische DE/EN-Gabelseiten mit nativen WP-Seitenpaaren; gleicher Header; veröffentlichte passende Posts; verlinkte Bilder/Titel/Teaser/CTA; Home separat freigegeben. Test: Home → Gabelseite → Beitrag → Sprachpartner → zurück. Keine leeren oder erfundenen Inhalte; fehlende Übersetzungen transparent.
2. **FIRST COMPLETE EXPERIENCE (MS-03/04/06/07/13)**: eine tatsächliche APP-Beobachtung als verknüpfte Fight-Night-Matchstory, Research-Analyse und Perspectives-Reflexion; Academy optional als erklärender Baustein. Story-driven Lab Development. Reiher-Pilot #1466 ist Kandidat, nicht automatisch freigegeben; Matchidentität, Evidenz, Bild, Replay und Veröffentlichungsrechte prüfen. Bestehende Demo-Koi-Story bleibt technischer Referenzfall, keine echte Partie behaupten.
3. **ASSET/EVIDENCE-02 (MS-11/13)**: gemeinsamer Faktenvertrag, reale validierte Brettposition/Replay oder interaktive Analyse, Asset-ID/Version/Rolle, Herkunft und Freigabe, Inventar und Verwendungsübersicht. Keine vertraulichen JSONL oder ungeprüften ausführbaren Uploads veröffentlichen. Nur für die erste echte Erfahrung nötige Renderer bauen.
4. **CONTENT-PACKAGE-01 / Editorial Bible (MS-03/14)**: verbindlicher versionierter ZIP-Vertrag mit shared, media, languages/de, languages/en, assets und editorial-check; idempotenter Import; KI-Redaktion in anderem Thread produziert einen überprüfbaren Beitrag, Mensch gibt frei. R0.3-Format bleibt Vorschlag bis Implementierung.
5. **Härtung und Wachstum**: SEO (canonical/hreflang), Legacy-Redirects, Sitemap/Suche/Cache je Sprache, umfassendere Fakten-/Medienzuordnung, Inventar bestehender Academy-Demos, weitere Home-Sprachen, Social-Verknüpfung. Nach Bedarf vor öffentlichem Produktionsstart priorisieren.

## 7. Abnahmeprinzip
Pro Inkrement ein echter Besucherweg und ein redaktioneller Workflow, keine automatischen Freigaben. Ausgangs-ZIPs behalten, installierbares Update mit dokumentierten Prüfungen liefern, Nutzer-Live-Abnahme separat. Versionsnummern zukünftiger Plugins erst nach Umsetzung vergeben. Keine weiteren Änderungen an der abgenommenen Home-Oberfläche ohne konkreten Bedarf.

**Erleben. Erforschen. Erahnen. – Shared Design, Localized Content, Shared Evidence.**
