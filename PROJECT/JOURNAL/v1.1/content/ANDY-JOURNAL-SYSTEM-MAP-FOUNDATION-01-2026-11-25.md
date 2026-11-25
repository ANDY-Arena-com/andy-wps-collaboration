# ANDY Journal – SYSTEM-MAP-FOUNDATION-01
**25.11.2026 · Fachlicher Handoff Content-/Konzept-Thread an Technik-Thread · v0.1 · Anforderung, keine Implementierungs- oder Publikationsfreigabe**

> **Technischer Eingangsnachtrag (25.11.2026):** Der Technik-Thread hat die schlanke Foundation als [**lokales Content-Composer-0.1.30-Update**](../ARCHITECTURE/ANDY-JOURNAL-SYSTEM-MAP-FOUNDATION-01-TECHNICAL-RELEASE-2026-11-25.md) implementiert: vorhandene Story-/Sprach-/Themen-IDs lesen, DE/EN-Relationen mit Prädikaten, Aussagearten, Belegreferenzen, Provenienz und Revisionen **intern** pflegen. WHY bleibt in Launch Control, WordPress-Posts bleiben Contentquelle. **74/74 isolierte Tests**, Plugin-ZIP und 0.1.29-Rollback lokal geprüft; **noch keine WP-Installation oder öffentliche Map/Exporte**. Lokale `andy.native.<WP-ID>`-Keys werden nicht als portable Graph-IDs verwendet. 01C2B-Sicherheitsgate bleibt vorrangig.


Ergänzt [WHY & Progressive Content Release 01](ANDY-JOURNAL-WHY-PROGRESSIVE-CONTENT-RELEASE-01-2026-11-25.md) und [Coming-Soon-Content-Handoff](ANDY-COMING-SOON-CONTENTKONZEPT-HANDOFF-2026-11-25.md). **Bitte die semantische Basis früh in die aktuelle Konsolidierung einplanen**, damit die ersten DE/EN-Leseproben bereits vernetzte Inhalte sind. Kein zweites CMS und kein komplexes Graph-System als Launch-Voraussetzung. Aktuelle Plugin-Stände und technische Ownership im Technik-Thread prüfen. Der Content-Thread ändert keine Plugins.

## 1. Kommunikative Leitlinie und Zielbild

**ANDY – Actor. Network. Dynamics. | Erleben. Erforschen. Erahnen. | Der Weg ist das Ziel.**

ANDY gestaltet Voraussetzungen für neue Erfahrungen, Fragen und Erkenntnisse. Es behauptet keine Emergenz und keinen Zugang zu internen Denkprozessen von KI-Modellen. Erleben, Erforschen und Erahnen sind gleichberechtigte Erkenntnisregister, keine zwingende Pipeline. Wissenschaftliche Prüfung ist ein optionaler Modus des Erforschens; empirische Aussagen benötigen dennoch geeignete Evidenz. Philosophische Analogien bleiben Analogien. Die Reviews DS1/DS2 und Q1/Q2 führten zur Unterscheidung zwischen **Ermöglichen** und **Nachweisen**. Provenienz, Revidierbarkeit, Widersprüche und Offenheit bleiben wesentlich; die Literaturhinweise der Reviews sind hier nicht unabhängig verifiziert.

GAME 4 LAB: Erlebnis kann Nutzung motivieren, Nutzung erzeugt Daten, Daten eröffnen Untersuchungen, Erkenntnisse und Kommunikation können weitere Nutzung und Fragen anregen. Konzept, kein gemessener Motivationseffekt. CONTENT 4 KNOWLEDGE als zweite konzeptionelle Schleife: Inhalte → Beziehungen → Exploration → neue Fragen → neue Inhalte/Revisionen. Menschen und KIs können verschiedene Wege verfolgen. Das Netzwerk wächst und verändert sich durch redaktionelle Arbeit; nicht alle Knoten müssen miteinander verbunden sein. Partielle Vernetzung, Gegenbeispiele und alternative Perspektiven erhalten. Kein autonomes Veröffentlichen und keine Behauptung eines selbstlernenden neuronalen Netzes.

## 2. WHY bleibt dauerhafter Basis-Content

Bestehende WHY-Modi prominent / compact / optional / hidden unverändert. Anfangs dominiert WHY, später der Content. Home-Modul erklärt die Systemfunktion, Gabelseite die Themen/Formate, Artikel seine Relevanz und konkrete Beziehungen. DE/EN getrennt bearbeiten und freigeben; eine Sprachfreigabe ist keine Freigabe der anderen. Kein redundantes Kopieren von Texten in Map, Home, Footer oder Export. Darstellung und Autorisierung bleiben strikt getrennt.

## 3. Früh benötigte gemeinsame Datenbasis (Zielvertrag, keine vorhandenen Feldnamen behauptet)

- Stabile sprachübergreifende fachliche IDs für Bereich, Thema, Story; existierende Story-ID/Registry und native WP-Posts bzw. Sprachpartner nutzen. WP-Post-ID bleibt lokale Referenz, keine alleinige umgebungsübergreifende Identität. Keine Duplikate bei Import/Update; keine erzwungene Neuanlage vorhandener Stories.
- WHAT = vorhandener Inhalt/Titel/Intro; WHY = lokalisierte Relevanz; RELATIONS = gerichtete semantische Beziehungen; EVIDENCE = Quellen-/Match-/Methodenreferenzen und Geltungsbereich, wo einschlägig; PERSPECTIVE = Erkenntnisregister/Art der Aussage; NEXT = offene Fragen/weitere Möglichkeiten. Nur notwendige Felder früh vorsehen, fehlende optionale Werte zulassen, niemals Belege erfinden. Ein Artikel muss nicht zwangsläufig eine Hypothese oder neue Kante liefern.
- Beziehungen als eigenständige revidierbare Datensätze mit stabiler ID, Quell-ID, Ziel-ID, typisiertem Prädikat, DE/EN-Erklärung, optionalen Belegreferenzen und Geltungsbereich, Aussage-/Evidenzstatus, redaktionellem Freigabestatus je Sprachfassung, Revision und Herkunft. Funktionale Beziehung, dokumentierte Beobachtung, abgeleiteter Befund, Hypothese, Analogie, offene Frage und Widerspruch unterscheidbar halten. Erkenntnisregister ist nicht automatisch Evidenzstatus. Redaktionelle Freigabe macht eine Hypothese nicht wahr.
- Kleines erweiterbares Prädikatsvokabular, z.B. provides_events_for, investigates, raises_question, enables_learning, suggests_transfer, contradicts, reflects_development, is_based_on. Keine automatische Kausalität aus Tags, Ähnlichkeit, Korrelation oder Graph-Konnektivität. Rückverweise aus denselben Kanten ableiten, nicht doppelt pflegen.
- Rechte/Revisionen an vorhandenen Editorial Workflow und Launch Control anschließen. Vorschläge durch KI zunächst Entwurf; gezielte menschliche Prüfung, Änderung, Ablehnung oder Rückzug. Auch abgelehnte oder revidierte Beziehungen intern nachvollziehbar halten; kein öffentliches Revisionsarchiv geschützter Inhalte.
- Den späteren Content-Paketvertrag versionieren und an bestehende Importer/Identitäten anschließen, keine neue parallele Importschnittstelle jetzt erzwingen. Passive Daten, kein ausführbarer Code. Keine automatischen Überschreibungen.

## 4. Drei öffentliche Zugänge, ein Datenbestand

Sitemap = hierarchisch; A–Z = alphabetisch/thematisch; **System Map = funktional-relational**. Optionaler Footer-Link neben bestehenden Sitemap- und A–Z-Zugängen, erst nach Freigabe. Keine Umgestaltung des globalen Footers ohne Abstimmung.

System Map v0.1: kleines RGB/Neutral-Netz in vorhandener Design-Shell, zunächst Bereichsknoten Fight Night, Research, Perspectives, Academy, Making of sowie Arena/Data/Lab als funktionale Referenzen (nur tatsächlich autorisierte öffentliche Ziele verlinken). WHY pro Knoten und verständliche Richtung/Bedeutung von Kanten. Selektion eines Knotens hebt Nachbarschaft hervor; zugängliche Listen-/Textansicht, Tastaturbedienung, Mobilansicht. Vorgesehene Macro-/Meso-/Micro-Tiefe: Bereiche → Themen → einzelne Inhalte/Beobachtungen. Erst Macro plus freigegebene Leseproben erforderlich; spätere Filter/Zoom/Layouts keine Launch-Blocker. Neu freigegebene vernetzte Artikel sollen ohne separate Map-Redaktion als Knoten/Kanten erscheinen. Keine frei erfundenen Kanten oder Leistungswerte.

## 5. Machine-readable – gleiche Quelle, andere Projektion

Aus dem selben freigegebenen Bestand serverseitig ableitbare, sprachbezogene öffentliche Ansichten:
- /system-map/ (HTML/visuell, tatsächliche DE/EN-Routen mit bestehendem Router abstimmen);
- system-map.md (lesbare Orientierung mit stabilen IDs, WHY, Beziehungen, Quellen, Status und kanonischen URLs);
- system-map.json (versioniertes passives Knoten-/Kantenformat, locale, Stand/Revision; Feldnamen erst mit Technik abstimmen);
- optional später /llms.txt als Einstieg mit Link auf die autorisierten Exporte. Kein Anspruch, dass externe KI-Systeme diese tatsächlich nutzen.

Keine manuell parallele Markdown-/JSON-Datenhaltung. Rendering/Export aus derselben gemeinsamen autorisierten Projektion. Exporte nur öffentlich freigegebene und in der jeweiligen Sprache zulässige Daten; WHY hidden bzw. separat geschützte Texte nicht über Markdown, JSON, HTML-Quelltext, Metadaten oder API offenlegen. Früh eine interne Testprojektion mit neutralen Fixtures ermöglichen, öffentliche Endpunkte erst nach Sicherheitsgate.

## 6. Freigaben und Sicherheit sind Voraussetzung

01C2-/Nachfolge-Gate bleibt vorrangig. Map, Export, Backlinks und Suchergebnisse verwenden dieselbe zentrale Autorisierungsentscheidung wie Artikel/Gabelseite: Bereichsmodus, WP-Status, redaktionelle und sprachbezogene Freigabe, Rückzug, explizite Preview-Allowlist. Kanten nur ausgeben, wenn beide Endpunkte und die betreffende Kante/Sprachfassung autorisiert sind; geplante Funktionen dürfen als ausdrücklich freigegebene allgemeine Beschreibungen erscheinen, niemals als Titel/ID/URL/Metadaten eines geschützten Beitrags. Keine Leaks über Counts, Filter, Tooltips, verwaiste Links, Cache, REST, Feeds, Sitemap oder öffentliche Medien. Unbekannt/mehrdeutig standardmäßig nicht ausgeben. Cache-Invaliderung bei Freigabe, Rückzug, Sprach-/WHY-/Kantenänderung. Staging und Live strikt getrennt; kein automatischer Transfer. Keine Änderungen vorhandener WP-Post-Status durch Graph-Generierung. Kein noindex als Zugriffsschutz. Keine automatische Veröffentlichung oder öffentliche Agenten-Schreibrechte.

## 7. Anschluss an Lab – früh referenzierbar, später analytisch

Competitive Knowledge Graph als spezialisierte Perspektive auf dasselbe übergeordnete Erkenntnisnetzwerk: Akteur/Modellversion, Konfiguration (Gegner, Farbe, Budget, Ruleset, Build), Match/Event, Messgröße, Beobachtung, Forschungsfrage, Methode, Evidenz, Artikel. Stabile IDs und Provenienzreferenzen statt Kopien privater Rohdaten. Model Cards/Interaction Profiles bleiben kontextabhängig. Keine synthetischen Performance-Scores, keine universelle Intelligenzrangliste; fehlende Daten bleiben unbekannt. Korrelation, Beobachtung, Hypothese und geprüfter Befund auseinanderhalten. Lab-Datenadapter und analytische Visualisierung erst bei ausreichender Datenbasis, eigener Freigabe. Die System Map ist kein Ersatz für Arena- oder Lab-SSOT.

## 8. Reihenfolge / Abnahme für den Technik-Thread

| Inkrement (Vorschlag) | Inhalt |
|---|---|
| SYSTEM-MAP-FOUNDATION-01 | Bestehende IDs, WHY-Daten, Sprach-/Freigabe-Adapter und Relation-Metadaten prüfen; schlanken versionierten Zielvertrag mit Content-Thread abstimmen. Vorsehen in bestehenden Plugins, nicht blind neues Plugin anlegen. |
| SYSTEM-MAP-MVP-01 | Intern editierbare Bereichsbeziehungen und erste Artikelbeziehungen; gemeinsame autorisierte Projektion, einfache visuelle Map + zugängliche Textansicht. |
| SYSTEM-MAP-EXPORT-01 | Aus gleicher Projektion DE/EN Markdown und JSON, ggf. llms.txt; öffentliche Aktivierung erst nach 01C2-/Nachfolge-Gate und Freigabe. |
| SYSTEM-MAP-GROWTH-01 (später) | Themen-/Artikel-Drilldown, versionierte Content-Pakete, geprüfte KI-Vorschläge, Entwicklung des Graphen über Zeit. |
| COMPETITIVE-KNOWLEDGE-GRAPH (später) | Lab-Evidenz und kontextabhängige Akteursprofile anbinden; eigene methodische und technische Abnahme. |

Abnahme: fünf Bereichs-WHYs und vernetzte DE/EN-Leseproben ohne Duplikate möglich; ein zusätzlicher freigegebener Artikel mit geprüfter Kante erscheint in den berechtigten Ansichten ohne manuelle Map-Kopie; Rückzug von Artikel oder Kante entfernt ihn bzw. sie auch aus Export und Cache; fremde Sprache, interne Beiträge, hidden WHY, ungeprüfte Beziehung, fehlendes Ziel und unbekannter Status werden nicht geleakt; Rückverweise konsistent; bestehendes Home-/Gabelseiten-/Content-Design, Daten, Sitemap/A–Z, Launch-Control-Modi bleiben erhalten. Keine öffentliche Aktivierung ohne ausdrückliche Abnahme. Reihenfolge mit aktuellen PRE-STAGING-Arbeitspaketen abstimmen.

## 9. Redaktion / externe Kommunikation

Content-Thread liefert Gesamtstory DE/EN, WHY für fünf Bereiche, erste eigenständig lesbare Artikel mit geprüften Beziehungen, Evidenz/Erkenntnisstatus, optionale offene Fragen. Launch-Kandidaten sind keine freigegebenen Beiträge. Instagram/LinkedIn etc. führen über interessante Fragen/Erlebnisse zu tatsächlich freigegebenen Zielseiten; WHY/Map bieten freiwillige Vertiefung, Philosophie als optionaler Zugang. Kein wissenschaftlicher Überlegenheits- oder Emergenzclaim. Spätere agentische Exploration: read-only Navigationsraum, begrenzte Ressourcen/Schleifen, Vorschläge statt automatischer Writes; Zukunftsvision, keine bereits nachgewiesene Funktion. Redaktionelle Beobachtungen und explorativer Nutzen dürfen untersucht werden; kontrollierte Empirie optional für eng abgegrenzte Behauptungen.

## Quellen / Anschluss

- [ANDY Philosophy – Optimierung der Voraussetzungen](../../../../research/andy-lab/CORE/v0.1/07_ANDY_PHILOSOPHY.md)
- [GAME 4 LAB / Produktkonsens](../../../../research/andy-lab/REQUIREMENTS/ANDY_LAB_V1_0_PRODUCT_CONSENSUS_2026-11-20.md)
- [Making of / Story-driven Lab Development](../../../ANDY_MAKING_OF_LIVING_LAB_MULTI_PERSPECTIVE_DEVELOPMENT_v0.1.md)
- [WHY & Progressive Content Release 01](ANDY-JOURNAL-WHY-PROGRESSIVE-CONTENT-RELEASE-01-2026-11-25.md)
- [Coming-Soon-Handoff](ANDY-COMING-SOON-CONTENTKONZEPT-HANDOFF-2026-11-25.md)
- [PRE-STAGING Governance](../ARCHITECTURE/ANDY-JOURNAL-PRE-STAGING-ADMIN-UND-LAUNCH-GOVERNANCE-2026-11-25.md)

**Bitte aus technischer Sicht zunächst Datenmodell/Ownership, Schnittstellen, Sicherheitsgate und minimale Inkremente rückmelden. Dieses Dokument ist der fachliche Arbeitsauftrag, kein Plugin-Release.**

## Redaktionelle Fortschreibung (25.11.2026)
[Coming Soon Editorial Guideline v0.1](ANDY-JOURNAL-COMING-SOON-EDITORIAL-GUIDELINE-v0.1-2026-11-25.md): Zielgruppen und Contenttypen, Astra–Argon als erstes vernetztes Beispiel, Erkenntnishistorie (Festigung/Relativierung), Academy-Auswahl und Außenkommunikation. Redaktionelle Ergänzung, keine Änderung der technischen Gates.
