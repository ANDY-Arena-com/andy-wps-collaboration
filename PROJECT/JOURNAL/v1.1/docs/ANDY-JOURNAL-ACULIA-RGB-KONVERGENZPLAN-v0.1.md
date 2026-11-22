# ANDY Journal — Aculia × RGB × Editorial v2: Konvergenzplan v0.1

**Stand:** 22.11.2026 · **Status:** Arbeitsvorschlag; keine Änderung an WordPress, Hosting oder öffentlicher Website.

## Problem und Ziel
Die native Aculia/Elementor-Homepage (visuell abwechslungsreiche Theme-Module) und der separate RGB-Pilot (28 bestehende redaktionelle Seiten, Module, Breadcrumbs, Navigation, A–Z/Sitemap) sind auseinandergewachsen. RGB 0.6.x liefert eigenständige statische HTML-Seiten über WordPress aus und ist keine native WordPress-Post-/Taxonomiearchitektur. Die neu hinzugekommene Editorial-v2-Vorschau ist ein separates read-only Admin-Labor und keine Integration in die öffentliche RGB-Home. Launch Control legt Entwürfe im nativen WP an, veröffentlicht diese nicht in RGB.

**Ziel:** eine gemeinsame, nachvollziehbare Journal-Frontend-Website mit WordPress/Aculia als visueller und redaktioneller Zielschicht, übernommenen RGB-Inhalten, 5 Content-Familien als redaktioneller Matrix und drei E als ergänzenden Zugangswegen. `www.andy-arena.com` bleibt unverändert.

## Verbindliche Schichten / Zuständigkeit im Zielbild
| Ebene | Zukunft | Regel |
|---|---|---|
| Aculia + Elementor / WpSection | Frontend, visuelle Module, responsive Verhalten | Bestehende Module gezielt weiterentwickeln; lizenzierte Theme-Bestandteile nicht ins öffentliche Repo |
| Native WordPress-Beiträge, Seiten, Medien und Taxonomien | Dauerhafte redaktionelle Quelle | Vorhandene Posts inventarisieren, keine Doppelimporte; Content-Metadaten nach belegten Funktionen von Content Manager/Publishing |
| RGB 0.6.x | Inhaltliche und technische Referenz, temporäre Vorschau | 28 Seiten, 4 Module, URLs, Texte und Verweise auditieren; nicht parallel als zweite kanonische öffentliche Home pflegen |
| Editorial v2 0.1.0 | Sitemap-/Bildwelt-/Layout-Labor | Nur Referenz/administrative Vorschau, keine zweite Content-Datenbank |
| Launch Control 0.1.0 | Soll-Ist-, Draft- und QA-Verwaltung | Weiterverwenden; nicht durch konkurrierenden Draft-Importer ersetzen |
| Replay, Academy, Lab/Tools | Datenbasierte interaktive Einbettungen | Originalmodule und Engine bewahren; keine vorgetäuschte Funktionsfähigkeit |

## Redaktionelle Struktur
Fünf Familien: **Spiele / Fight Night**, **Perspektive**, **Research**, **Academy**, **Tools**. Ergänzend Dokumentation und Making of. Die bisherigen Erleben/Erforschen/Erahnen bleiben über Zuordnungen und Landingpages erreichbar, aber keine konkurrierenden Primärdatenbanken. A–Z/Tags bilden verknüpfte Zugänge; eine reale URL/ein Inhalt ist kanonisch, Teaser sind mehrfach platzierbar.

Pro Inhalt vier getrennte Metadatengruppen: Content-Typ und Status; Originalinhalt/kanonische URL; Medien im Inhalt (echtes Replay, Chart, animiertes Brett, Tool); Teaser-Medien (Hero/Feature/Thumbnail/Text) mit Quelle/Rechten. Forschungsstatus und Quellenangaben aus Publikations-Governance bewahren.

## Start: nur Home auf isolierter Testkopie
Bestehende Aculia-Home (in der technischen Baseline: WP-Seite 14, *vor Schreibzugriff aktuelle ID/Elementor-Struktur prüfen*) **nicht direkt überschreiben**. Kopie oder reversibler Entwurf. Die folgenden Zuordnungen sind redaktionelle Zielbeispiele, keine Behauptungen über sofort vorhandene Widget-Schnittstellen:

| Vorhandener Aculia-Modultyp | Editorial-Nutzung in Home-v2-Test |
|---|---|
| Hero/Slider | Dreiteilige Bilddramaturgie mit bewusst unterschiedlichen Teaser-Welten; Slider-Technik separat entscheiden |
| Services/Tabs mit großem Bild und auswählbaren Themen | Fight-Night-Mediathek: links ein echter Featured Fight, rechts Auswahl anderer echter Matches/Szenen |
| Kleine Editorial-Kacheln | Themenübergreifende aktuelle Einstiege mit asymmetrischer Priorisierung |
| Großes Bild-/Text-Feature | Research-Befund/Chart oder Perspektive/Crossover-Reportage |
| Breitflächiger Themenabschnitt | Perspektive mit externer, rechtegeprüfter Fotografie, nicht zwanghaft Schach-/Go-Bild |
| Kompakte Informationsmodule | Academy-Lernaufgaben und originale animierte Bretter **oder** Tools; keine Wiederholung identischer drei Karten |
| Journal/News-Sektion | Reale aktuelle Artikel aus nativer WP-Quelle (mit eindeutigen Links, ohne fiktive News) |
| Footer | A–Z, Sitemap, Tags, Projektkontext |

Die Reihenfolge wird anhand realer Inhalte bestimmt. Oberer Einstieg → Fight Night; danach deutliche strukturelle Abwechslung in Flächen, Textanteil, Fotografie, Diagrammen und Original-UI. In den Rubriken stets „Alle …“ zur nächsten Gabelseite.

## Migrationsschritte und Gates
1. **Freeze/Backup:** tatsächlichen WP-/Hostinger-/Plugin-/Cache-Stand, Domain-Modus, Datenbank, Theme-, Elementor- und WP-Content-Backup sichern. Kein Reset, kein pauschales Deaktivieren. Ursprüngliche Aculia- und RGB-Home bleiben rückholbar.
2. **Inventur/Mapping:** alle 28 RGB-Seiten, 4 Module und vorhandene native Demo-Posts mit kanonischen IDs/URLs in einer Tabelle erfassen; jeweils Familie, Typ, Kategorie/Tag, Aculia-Template, Bilder im Inhalt, Teaserbild, funktionierender Player/Link, Status, Rechte, Migration/Redirect. Bestehende 5 englische nativen Demo-Posts nicht duplizieren.
3. **Erstes vertikales Slice:** *Astra vs. Gemini 4 Argon* (Fight-Night-Schaufenster → bestehende Story/Replay), *Jenseits des Schachbretts* (Perspektive/Research → Beitrag), Academy L01 (echtes Modul). Originaldaten/Interaktionen nicht kopieren oder nachbauen. Für fehlende Player die Funktion als offen kenntlich machen.
4. **Aculia-Home als isolierte, nicht öffentliche Kopie** mit vorhandenen Widgets in variierenden Kompositionen befüllen. Dort nur bestätigte Interaktion/Links verknüpfen, kein neuer generischer RGB-Home-Layer.
5. **Native Migration über bestehende Verwaltungsfunktionen** nach Ist-Prüfung und Dry Run; spätere Rubrik-/Sub-Home-Templates aus denselben kanonischen Content-Daten. RGB-URLs erst nach Inhalts-/Link-Abnahme umleiten; keine Doppelpflege.
6. **Deterministische Root-Auslieferung:** `/` und `/?utm_source=chatgpt.com` müssen dieselbe gewählte Home ausliefern; Ursache (RGB-Router, Query-Prüfung, Cache/CDN, WP-Redirect) per tatsächlicher Laufzeitdiagnose isolieren. UTM darf nicht zwischen Aculia und RGB wechseln. Vor Freigabe Cache- und Browser-Abnahme.
7. **QA & Entscheidung:** Desktop/Mobil, URLs/Breadcrumbs/A–Z, Bildrechte, Rollback, richtige Match-ID/Replay, Academy-Modul und evidenzgerechte Kennzeichnung prüfen. Erst manuelle Staging-Abnahme, dann gesonderte öffentliche Freigabe.

## Stoppregeln
Keine zweite WP-Engine, kein weiterer universeller Importer, kein komplettes Theme-Fork, keine Löschung originaler HTML-/Medien-/Game-Daten, kein Überschreiben der Aculia-Home 14 ohne Konflikt- und Backupprüfung, keine parallele Pflege zweier kanonischer Homes. Kein direkter Publish an `blog.andy-arena.com` oder `www.andy-arena.com` durch diesen Plan.

**Aktuell beobachtet:** laut Nutzer-Screenshots können Root-Aufrufe mit/ohne UTM-Parameter unterschiedliche Aculia-/RGB-Home-Versionen zeigen. Das ist ein Fehlerbild, keine bereits belegte Ursache. Installiert laut Screenshots: Content Manager 0.4.6, Cockpit 0.1.0, Editorial Sitemap v2 0.1.0, Launch Control 0.1.0, RGB Pilot 0.6.1. Tatsächliche WP-Admin- und Browser-Diagnose steht aus.
