# ANDY JOURNAL – Public Beta: Arbeitspakete 1.0
15.11.2026 · Planung, keine Live-Umstellung. Basis: [Guidelines 1.0](ANDY-JOURNAL-GUIDELINES-v1.0.md), [Gesamtkonzept v1.1](ANDY-JOURNAL-GESAMTKONZEPT-v1.1.md), [Themenspeicher](REDAKTIONELLER_THEMENSPEICHER_AUS_ANDY_DIALOGEN_v0.1.md).

## Ziel
Früh eine nutzbare offizielle Public Beta mit realen redaktionellen Pilotinhalten aufsetzen. WordPress laut Projektleitung installiert, weitergehende Umsetzung noch offen. Lab-Prototyping vorläufig pausiert bis Factory Daten liefert; bestehende Konzepte und geprüfte Daten können unabhängig davon journalistisch bearbeitet werden. Kein Warten auf Factory für konzeptionelle Artikel.

## 1. Arbeitspakete (Vorschlag zur Priorisierung)
| ID | Aufgabe | Lieferung / Abnahme | Status / Abhängigkeit |
|---|---|---|---|
| JRN-01 | Brand & Asset Audit | Original-Logo, CSS/Farben/Schriften, Bildrechte, verfügbare SVGs; verbindliche Tokens | offen, parallel zu JRN-02 |
| JRN-02 | WordPress-Bestand & sichere Vorschau | Versionen, Theme/Plugins, Hosting, Backup/Restore, Staging-Plan; keine produktive Änderung | offen, zuerst |
| JRN-03 | Magazin-Design | Home-, Rubrik-, Artikel- und Teaser-Mockups mit Original-Assets, Desktop/Mobile; Guidelines-Review | offen, JRN-01 |
| JRN-04 | WordPress-Templates & Patterns | schlanke Basis, vier Rubriken, Header/Footer, Sprachwechsel, responsive Templates, Quellen/Grafik/Match-Facts/News-Module; Staging | offen, JRN-02/03 |
| JRN-05 | Editorial Pilot | Can AI Think Too Much? als vollständiger erster Entwurf mit Sweet Spot?-Grafik und Darstellungsvarianten | offen, parallel zu 01–04 |
| JRN-06 | Startredaktion & Medien | weitere vier Artikel, passende Teaser, Rechte/Provenienz/ALT, DE/EN; Originaldatenprüfung für Match-Story | offen, parallel |
| JRN-07 | Vermittlungstest | konkrete Texte/Bilder/Interaktionen in Staging bewerten; Varianten, Feedback, Änderungen dokumentieren | offen, JRN-04/05 |
| JRN-08 | Beta-QA & Launch | Quellen/Freigaben, Sprachwechsel, Links, Mobile, Datenschutz, Accessibility, Performance, Backup, Rollback; explizite Projektleitungsfreigabe | offen, nach relevanten Gates |
| JRN-09 | Beta-Iteration | Feedback, redaktionelle Verbesserungen, gelegentliche News Activation; weitere Factory-Stories nach Datenprüfung | später |

Keine Fortschrittsbehauptung aus dieser Planung. Konkrete Zuständigkeiten/Hosting-Zugänge und Theme-/Pluginwahl noch klären. Keine Änderungen an App/Factory.

## 2. Redaktionelles Startpaket
Fünf Artikel als Ziel, keine zwingende Launch-Anzahl; ungeprüfte Beiträge bleiben Entwurf. Arbeitstitel, keine Veröffentlichung.
| Titel | Rubrik / Bezug | Darstellungsversuch | Grundlage / Gate |
|---|---|---|---|
| Every AI Has a Plan. Until It Gets Punched. | Arena Stories A01 | dramatischer Einstieg, Reaktionszyklus | verifizierte Regeln, konzeptionelle Illustration; keine erfundenen Matches |
| Zwei Spiele. Ein Sieger. | Arena Stories A02 | echte Brettgrafiken, Zeitverlauf, Match Facts | Original-JSON/JSONL, Engine-/Ergebnisprüfung, Match-Checkliste |
| Can AI Think Too Much? | Research & Insights, Pilot | Text + Sweet Spot?-Grafik; optional interaktive Erklärung | Analysekompass/CORE; unkalibriertes Denkmodell, keine Messkurve oder Modellklassifikation |
| One Human. Multiple AIs. One Arena. | Behind ANDY B01 | Making-of, echte Artefakte, Rollen | belegte Entwicklungsbeiträge, menschliche Freigabe, Zitate/Rechte |
| Lokale Intelligenz. Globale Wirksamkeit. | Beyond the Arena | visuelle Metapher, Essay, ANDY-ABC | Nested Competitive Networks und DOMAIN-Memo; explorative Frage, kein Unternehmensleistungsnachweis |

Vorhandene Ressourcen: [Analysekompass](../../../../research/andy-lab/ANALYSEKOMPASS/v0.1/README.md), [CORE](../../../../research/andy-lab/CORE/v0.1/README.md), [Analysen](../../../../research/andy-lab/ANALYSES/README.md), [ANDY-ABC](../../../../research/andy-lab/REQUIREMENTS/v0.1/ANDY_ABC_DOMAIN_ISOLATION_MEMO.md). Archivierte quantitative Auswertungen vor Publikation gegen Originale nachprüfen; keine privaten philosophischen Primärtexte veröffentlichen. Nur freigegebene öffentliche Konzepte verwenden.

## 3. Vermittlungstest: Das Wie als eigener Testgegenstand
Je Beitrag Hypothese zur Darstellung, Zielgruppe, Variante A/B als redaktioneller Vergleich (kein automatisiertes Tracking vorausgesetzt), Feedback und Entscheidung festhalten. Beispiel Pilot: statische Sweet Spot?-Grafik mit knapper Erklärung versus ergänzende interaktive Version; keine fiktiven Modellwerte als Messdaten. Prüfen, ob Nutzer den Unterschied zwischen Denkmodell und Messbefund erkennen, die offene Forschungsfrage wiedergeben können und auf Mobilgeräten gut lesen. Auch Headline/Teaser, Bildausschnitt, Reihenfolge von Text und Grafik, Quellenzugang testen. Kleine qualitative Reviews, keine statistisch repräsentative Wirkung behaupten.
Protokoll: Datum | Artikel/Version | Variante | Testperson/Rolle (sparsam, keine unnötigen personenbezogenen Daten) | Beobachtung | Feedback | Änderung/Entscheidung | offener Punkt.

## 4. Nächster Schritt
JRN-01/02 und JRN-05 parallel vorbereiten. Erstes Artikelmanuskript, reale Grafik und Homepage-/Artikelmotiv als gemeinsame Designreferenz. Anschließend Templates auf sicherer Vorschau umsetzen, echte Entwürfe einpflegen und iterativ testen. Die öffentliche Coming-Soon-Seite samt DirectoryIndex bleibt bis ausdrücklicher Freigabe geschützt. News Activation gemäß §5.2 optional, kein Newsfeed und keine Pflichtfläche. Publikationsfreigabe bleibt getrennt von fachlicher Prüfung/WPS-Gates.
