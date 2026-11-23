# ANDY Journal Content Composer v0.1.1 – ACADEMY-HERO-02

> **NEUER RELEASE:** [Content Composer 0.1.2 / CONTENT-03](ANDY-CONTENT-COMPOSER-03-HEADER-AND-IMAGE-FIT-v0.1.2-2026-11-23.md) behebt die Aculia-Demo-Header-Zuordnung auf Contentposts und ergänzt Bildanpassungsmodi. Diese Seite bleibt als historische Beschreibung 0.1.1 erhalten.

**Datum:** 23.11.2026  
**Status:** Lokaler WordPress-Plugin-Release, **nicht auf Hostinger installiert oder abgenommen**.  
**Änderungsbasis:** Vorhandenes v0.1.0-Plugin-ZIP; **kein** Home-Composer-Source-Fork.  
**Zielordner im ZIP:** `andy-journal-content-composer/` (gleicher Ordner wie v0.1.0, Versionsupdate statt Zweitinstallation).

## Nutzeranforderung und Umsetzung

Die existierenden RGB-Academy-Seiten zeigen das **Beitragsbild als breite Bildbühne unmittelbar unter dem Journal-Header**. Im ursprünglichen Content Composer v0.1.0 stand es erst **unterhalb von Breadcrumb, H1 und Lead in einer gerahmten Textspalte**. Der Nutzer will den alten Stil übernehmen, insbesondere **Bild nach oben**.

**Neu ausschließlich bei Beiträgen mit `_andy_cc_template='academy'`:**

```text
WordPress Theme Header (unverändert)
→ Full-width Featured Image (hero) mit CSS object-fit:cover, ohne Textoverlay
→ Breadcrumb Home / Erleben / Academy / Beitragsname
→ Rubrik ERLEBEN / ACADEMY
→ H1 / Einleitung / Redaktioneller Importstatus
→ normaler WP-Beitragsinhalt / [andy_cc_interactive]-Slot
→ Themen/Tags und verwandte Beiträge
→ WordPress Theme Footer (unverändert)
```

- Hero: `width:100vw` mit Breakout aus ggf. vorhandenen Contentcontainern, Höhe Desktop `clamp(240px,24vw,430px)`, Mobile `clamp(190px,38vw,280px)`, `object-fit:cover`; schmale Akzentlinie vom zentralen Academy-Theme.
- Bildquelle ist **ausschließlich das WordPress-Beitragsbild**; unveränderte `_thumbnail_id`-Zuordnung. Kein neues Medienimportformat, keine doppelten Bilder, keine Textüberlagerung.
- Academy-Breadcrumb prüft existierende Kategorien `Erleben` und `Academy` und nutzt deren WordPress-Archivlinks; falls eine fehlt, wird sie nur als Text angezeigt.
- Im Beitrags-Template-Metabox steht ein Hinweis zur hohen Bildauflösung. Wenn ein importiertes Academy-Paket gegenwärtig als **Standard** gekennzeichnet ist (so im Nutzer-Screenshot sichtbar), meldet die Metabox eine Warnung: **Template Academy auswählen und Beitrag aktualisieren**.
- **Nicht-Academy** (Fight Night, Research, Perspectives, Standard), Home Composer, Aculia-Originalseite #14, RGB-Pilot, Importer, Renderer-Vertrag und gespeicherte Konfiguration bleiben unverändert.

## Grenzen und Bildqualität

Das bereits importierte L02-Demo-Bild hat nur **536 × 301 px**. Als Titelbild über volle Bildschirmbreite wirkt es bei großen Monitoren zwangsläufig etwas weich; eine hochauflösende Datei in WordPress unter **Beitragsbild** auswählen (möglichst 1600–2400 px Breite). Das Plugin darf Bilddetails nicht erfinden. Bei der Hero-Darstellung ist **Beschnitt (cover)** absichtlich zugelassen, wie beim bisherigen Academy-Template.

**Keine automatische Template-Umstellung**: Im Screenshot des importierten L02-Beitrags steht `STANDARD`. Das ist eine gespeicherte Beitragskonfiguration; die Aktualisierung 0.1.1 überschreibt sie **nicht**. Im Editor unter **ANDY · Beitrags-Template** bewusst **Academy** auswählen.

## Release-Matrix und Tests

| Prüfung | Ergebnis |
|---|---|
| PHP Syntax aller Plugin-PHP-Dateien | **PASS** |
| ZIP-Struktur mit genau einem unveränderten Pluginordner und 6 Dateien | **PASS** |
| ZIP-Integrität | **PASS** |
| Kein Importer-Code geändert (`includes/class-andy-cc-importer.php`) | **BESTÄTIGT** |
| Visueller Preview-Test (Desktop 1440 px) | **PASS**: Bild beginnt direkt nach Header, Breite 1440, Breadcrumb darunter, kein seitliches Overflow |
| Visueller Preview-Test (Mobil 390 px) | **PASS**: Bild beginnt direkt nach Header, Breite 390, kein seitliches Overflow |
| Hostinger/WordPress/Theme-Live-Test | **AUSSTEHEND** |
| Original-Academy-Interaktion | **NICHT verbunden, unverändert gegenüber 0.1.0** |

**Release-ZIP:** `ANDY-WP-PLUGIN-Journal-Content-Composer-v0.1.1-ACADEMY-HERO-02.zip`  
**SHA-256:** `2187c9c04aa99a505110b450e3fc960096a9e1010b0a5688bedf946148a1fc62`

### Upgrade-/Rückweg-Schritte

1. WP-Admin → Plugins: prüfen, dass derzeit `ANDY Journal Content Composer` **0.1.0** installiert ist und kein neuere Version eines anderen Threads läuft. Bei höherem Versionsstand **STOP**, kein Downgrade.
2. DB-/Datei-Backup; Plugin-ZIP 0.1.1 im WP-Updater hochladen, **gleichen Pluginordner ersetzen**.
3. Academy-Demo-Beitrag öffnen, in `ANDY · Beitrags-Template` auf `Academy` stellen (falls gerade Standard), Beitrag aktualisieren.
4. Unter **Beitragsbild** ein hochauflösendes Motiv wählen (für ersten Strukturtest reicht das bestehende, niedrig aufgelöste L02-Motiv); Vorschau öffnen.
5. Kontrollieren: Titelbild direkt unter Theme-Header, Breadcrumb darunter, kein zweites Artikelbild, intaktes Academy-Platzhalter-Modul.
6. Prüfen, dass **Homepage unverändert** blieb und Nicht-Academy-Artikel ihre bisherige Bildposition behalten.
7. Bei Fehler: kompatiblen vorherigen 0.1.0-Pluginstand zurückstellen, DB/Medien unverändert lassen. Live-Abnahme dokumentieren.

### Verwandte Dokumentation

- [Vorversion CONTENT-01 v0.1.0](ANDY-CONTENT-COMPOSER-01-RELEASE-v0.1.0-2026-11-23.md)
- [Verbindliches Release- und Versionsgate](../docs/ANDY-WORDPRESS-RELEASE-UND-IMPORT-GATE-v0.1-2026-11-23.md)

**Home Composer/öffentliche Root** in diesem Release **nicht bearbeitet**.
