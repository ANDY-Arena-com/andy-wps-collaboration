# ANDY Journal — Editorial Sitemap v2 & Demo-Pilot

**Stand:** 22.11.2026 · **Status:** isolierter Pilot erstellt, nicht auf WordPress installiert oder öffentlich freigegeben.

## Entscheidung

ANDY Arena Home und ANDY Journal Home bleiben eigenständig und werden inhaltlich vernetzt. Die neue Editorial-Architektur für das Journal arbeitet mit fünf Content-Familien, ohne die drei früheren Zugänge und ihre URLs zu löschen.

- **Spiele / Fight Night:** Match-Dokumentationen, Replays, Schlüsselszenen, Serienanalysen
- **Perspektive:** Essays, Crossover-Fragen, Gesellschaft, Medizin, Commerce
- **Research:** Ergebnisse, Fallstudien, interaktive Modelle und Daten
- **Academy:** Regeln, animierte Zugfolgen, Lernmodule, Quiz
- **Tools:** echte ANDY-Anwendungen, Observer, Lab, Daten und unterschiedliche Themes
- Projekt, Dokumentation, Making of als ergänzende Inhalte; Erleben/Erforschen/Erahnen, A–Z/Tags/Sitemap bleiben als Zugangswege erhalten.

## Trennung für jeden redaktionellen Inhalt

1. Content-Typ und Evidenzstatus
2. Konkreter Inhalt / kanonische URL
3. Medien **im** Inhalt (Original-Replay, interaktiver Chart, Animation, echtes Tool)
4. Medien **für den Teaser** (Hero, Feature, Thumbnail, reine Textvariante) samt Herkunft/Rechten

Designziel: **Strukturvielfalt und Bildvielfalt zugleich**. Science dient als redaktioneller Benchmark, nicht als zu kopierendes Design. Home ist kuratierter Haupteinstieg; Sub-Homes werden über „Alle …“-Links erreicht. Der Top-Slider ist gestalterisch noch nicht entschieden. Direkt darunter Fight-Night-Schaufenster mit auswählbaren Fights. Keine Pflicht zu gleichartig angelegten fünf Rubrikblöcken.

## Vorhandener Bestand / Pilot

- Die im RGB-Pilot dokumentierten **28 redaktionellen Seiten** wurden einer Content-Familie zugeordnet. Sitemap und A–Z sind Verzeichnisse, nicht zusätzliche Artikel.
- **14 Editorial-Demo-Einstiege** mit Metadaten zur Bildwelt (13 bestehende Pilotinhalte / Verweise und 1 noch unveröffentlichtes Datenresonanzpunkt-Konzept). Keine neuen empirischen Befunde oder Spielzüge erfunden.
- Ausschließlich Ausschnitte bereits vom Projektleiter bereitgestellter Screenshots, darunter authentische ANDY-UI. Keine Live-Funktionen vorgetäuscht. Bildrechte vor Veröffentlichung prüfen.
- Alternativer Home-Prototyp: drei verschiedenartige Bildaufmacher, Fight-Night-Mediathek, textdominierte Perspektive, Forschungsfeature, Academy-Lernstrecke und Tool-Showcase. Layouts sollen nicht mehrfach identisch wiederholt werden.

## Technische Integration v0.1.0

**ANDY-WP-PLUGIN-Editorial-v2-v0.1.0.zip** – zusätzliches, lokal gebautes WordPress-Plugin nur für eine fest definierte Staging-Instanz, administrative read-only Vorschau. Es erstellt keine WordPress-Posts, verändert keine vorhandenen RGB-Seiten, Menüs, Themes, Optionen oder Datenbanken und aktiviert keine öffentliche Ausgabe. Admin-Vorschau unter Werkzeuge → ANDY Editorial v2 (Home, Sitemap, Demo-Bibliothek, Demo-Details). Vorliegendes Plugin-ZIP: SHA-256 `adfca4b0431fd4593cd46f6f7949407812c506c59823d90e84b39192c462e60a`.

**ANDY-HTML-DEMO-Editorial-v2-v0.1.0.zip** – eigenständiger statischer Klickdummy für lokale Sichtprüfung. SHA-256 `cb1a1abeed9eccf2bbe1e05f0d35f66ad4c616878ce6272082ec46be7a31ebce`.

Die privaten ZIP-Artefakte sind im Chat bereitgestellt, **nicht** im öffentlichen GitHub-Repository gespeichert. Staging-Adresse, Screenshots und Lizenzmaterial nicht öffentlich archivieren.

## Verifikation und offene Gates

Lokal geprüft: 28 eindeutige Knoten mit gültigen Parents, 14 Demo-Einträge, vorhandene Bilddateien, valide Referenz-IDs, ZIP-CRC, PHP-Lint, JS-Syntax. Eine echte WordPress-Laufzeitprüfung, browserbasierte visuelle Abnahme und ein produktiver Hostinger-Einsatz sind **nicht** erfolgt; lokale Chromium-Navigation war in der aktuellen Ausführungsumgebung gesperrt.

**Als nächstes nach privater Sichtabnahme:** Die neue Ordnung und Bild-/Template-Metadaten konfliktgeprüft in das bestehende RGB-Paket bzw. die native WP-Content-Schicht integrieren. Den festen RGB-Content-Importer nicht mit einem unpassenden ZIP überschreiben. Verfügbare Launch-Control-Funktionen verwenden statt einen zweiten Draft-Importer zu implementieren. Öffentliche Freigabe bleibt unabhängig und manuell.
