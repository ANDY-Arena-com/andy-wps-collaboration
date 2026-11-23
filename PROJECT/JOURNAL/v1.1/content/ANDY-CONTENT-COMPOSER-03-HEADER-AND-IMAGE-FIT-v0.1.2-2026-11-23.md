# ANDY Journal Content Composer 0.1.2 – CONTENT-03 / Header & Image Fit

**Datum:** 23.11.2026  
**Release-Ziel:** Nur `andy-journal-content-composer/`, Version **0.1.2**, Upgrade von **0.1.1**.  
**Status:** Lokale Quell-/ZIP-Prüfung bestanden. **Keine Hostinger-Installation oder reale visuelle WordPress-Abnahme durchgeführt.**  
**Eingriffsgrenze:** Home Composer bleibt unabhängig, seine Dateien **und seine Optionen werden nicht verändert**. Das im WordPress-Admin installierte Content-Composer-Versionslabel vor dem Upgrade nochmals prüfen.

## Nutzerrückmeldung / Ziel

Auf der frisch erzeugten Fight-Night-Contentseite funktionierte die Template-Auswahl, aber:
1. Im Beitragsbild entstehen seitliche Leerräume zwischen Bild und Rahmen.
2. Der neue Artikel verwendet den **alten Aculia-Theme-Header** mit Demo-Adressen/`Join Research` statt des Journal-Headers der aktuellen Home.

## Tatsächliche Umsetzung

### 1. Content-Header statt Aculia-Demo-Header

Die bisherige Content-Datei `templates/single-andy-cc.php` begann mit `get_header()`. Dieser Theme-Aufruf produzierte die alte Aculia-Topbar. Ab **0.1.2** erzeugt ein *opt-in* Content-Post (nur wenn `_andy_cc_template` gesetzt ist) ein eigenständiges WordPress-HTML-Grundgerüst mit **`wp_head()`, `wp_body_open()` und `wp_footer()`** sowie dem Content-Journal-Header aus `includes/class-andy-cc-header.php`. Sonstige WordPress-Beiträge bleiben unverändert.

Die Journal-Header-Ausgabe übernimmt aus der vorhandenen, **nur lesend aufgerufenen** Option **`andy_home_composer_header_v01`**:
- WordPress-Logoanhang `logo_id` inklusive Erkennung von Symbol-/Wortmarkenformat,
- Header-Hintergrundbild `header_image_id`, Farbe, Deckkraft,
- Sticky-Modus,
- aktuelle DE/EN-Flagge und optional explizit konfigurierte Sprachlinks,
- Content-/Header-Maximalbreite.

Verfügbare Bedienung: Logo führt zur Home; Search-Icon führt zu der **vorhandenen A–Z-Seite**; Burger-Flyout enthält Links auf bestehende **aktive Module** der Home (aus `andy_home_composer_config_v01`, ebenfalls nur lesend), Sitemap, A–Z, ANDY Arena. Die Sprachflagge zeigt ohne konfigurierte Sprach-URL keine fiktiv funktionierende Übersetzung. Footer mit Journal-/Sitemap-/A–Z-Links.

**Wichtige Ehrlichkeitsgrenze:** Der Home Composer **0.1.15+** stellt uns aktuell **keine freigegebene, versionsstabile PHP-Header-Render-API** zur Verfügung. Die neue Content-Ausgabe verwendet darum die **gleichen gespeicherten Designwerte und das gleiche Logo**, aber **eine eigene kleine Header-Komponente**, keine gemeinsame Home-JavaScript-Instanz oder identische Suchmodal-Implementierung. Für spätere vollständige Parität braucht es einen versionierten gemeinsamen Header-Vertrag mit dem Home-Thread; keinen ungeprüften Code-Import aus einem veralteten Home-ZIP. **Aculia wird nur auf ausgewählten Content-Posts umgangen.**

### 2. Bildanpassung pro Beitrag, ohne zusätzliche Uploads

Unter **Beiträge → ANDY · Beitrags-Template** gibt es das neue Feld **„Titelbild: Anpassung“**. Meta: **`_andy_cc_image_mode`**, Default `cover`.

| Modus | Verhalten | Geeignet für |
|---|---|---|
| **Rahmen füllen** `cover` | füllt Bildrahmen in Höhe und Breite, ohne Seitenlücken; Bildausschnitt darf beschnitten werden | szenische Fight-Night-Motive / Panorama |
| **Volle Breite / natürliche Höhe** `natural` | Bild in Originalproportion komplett sichtbar, Höhe passt sich an | Grafiken mit Text oder Modellsymbolen nahe Rand |
| **Ganzes Bild + unscharfe Dublette** `backdrop` | Vordergrundmotiv bleibt vollständig, Hintergrund mit unscharfer zweiter *Darstellung desselben WordPress-Bildes*, ohne zusätzliches Asset | Quer-/Hochkantmotive mit bewusstem Vollbild |

Bildquelle bleibt `_thumbnail_id`, kein zweiter Import und keine Bearbeitung der Originalmediendatei. Im Academy-Template bleibt das Hero direkt unter dem Header; bei Fight Night/Research/anderen Vorlagen bleibt das Beitragsbild zunächst unter dem Titel, jedoch ohne leere Seitenstreifen. Für ein scharfes 1440–1800px-Hero ein hochauflösendes Original wählen (früheres L02-Pilotfoto war nur 536×301px).

### 3. Unverändert

- **Home Composer 0.1.15 oder neuer**, seine `andy-home-composer/*`-Quellen und gespeicherten Modulreihenfolgen.
- RGB Pilot, alte Aculia/Elementor-Home #14, Content Manager, Integrator.
- Content-Import: `includes/class-andy-cc-importer.php` ist **byteidentisch zu v0.1.1**.
- WordPress-Posts, Kategorien, Tags und importiertes L02-ZIP; kein Re-Import erforderlich.
- Interaktiver Academy-L02-Renderer: weiterhin **nicht verbunden**.

## Release-Archiv und Kontrollen

**Dateiname:** `ANDY-WP-PLUGIN-Journal-Content-Composer-v0.1.2-CONTENT-03.zip`  
**SHA-256:** `6130b6b95b4286ea92c2d34b867ba848a1631c781b95f2508e06cdf1abaf2ce8`  
**Pluginordner:** `andy-journal-content-composer/` (Upgrade des bestehenden Plugins, **kein neuer Pluginordner**)  
**8 enthaltene Dateien**, neu `includes/class-andy-cc-header.php` und `assets/content-menu.js`, sowie Updates an PHP-Root, Artikeltemplate, Adminmetabox, CSS, README.

Lokale Prüfung: **5/5 PHP-Dateien `php -l` bestanden**, JavaScript `node --check` bestanden, CSS `tinycss2` ohne Parsefehler, ZIP-Integrität/Ordnerkontrolle bestanden, Importer byteidentisch. Der Headless-Chromium-Dateitest ist in der Laufzeitumgebung **hängengeblieben**, daher **kein bestandener Browser-/Responsive-Test behauptet**.

## Installations- & Abnahme-Gate

1. **Zuerst Live-Version prüfen** unter WordPress → Plugins. Upgrade auf 0.1.2 **nur**, wenn `andy-journal-content-composer` bisher 0.1.1 (oder bewusst freigegebener älterer Stand) ist. Wenn höhere Version installiert: **STOP, kein Downgrade.** Das ist ein **anderes** Plugin als `andy-home-composer`.
2. WordPress-Datenbank + Plugin-/Uploads-Dateien sichern. Update-ZIP in **Plugins → hinzufügen/ersetzen**, aktiver Ordner muss `andy-journal-content-composer` sein.
3. Bestehenden Academy-L02-Entwurf (Template **Academy**) und neuen Fight-Night-Testbeitrag öffnen. Der Aculia-Header mit **Demo-Email/-Adresse und Join Research muss verschwunden** sein. Journal-Logo/Farben/Flagge/Burger auf beiden prüfen, Sticky beim Scrollen.
4. Bei Fight Night unter **ANDY · Beitrags-Template → Titelbild: Anpassung** die Varianten `cover`, `natural`, `backdrop` prüfen: keinerlei unerwünschte seitliche Leerräume, Cropping nur in `cover`, keine horizontalen Scrollleisten.
5. Auf Desktop und Smartphone prüfen; Burger schließen per X/Backdrop/Escape, Test-Links Home/A–Z/Sitemap; Logo aus WP-Mediathek.
6. **Öffentliche Homepage und Home Composer kontrollieren: unverändert.** Ebenso regulären WP-Beitrag **ohne ANDY-Template**.
7. Tatsächlich installierte Version und Tests dokumentieren. Bei Fehler: Content-Composer-Version zurück, ursprüngliche Daten beibehalten; **keine Home-Pluginänderung**.

## Folgeschritt

Längerfristig eine **gemeinsame, versionierte Header-Renderer-Schnittstelle** zwischen Home und Content definieren, damit Navigation, Suche und Header-Darstellung nicht als zwei Implementierungen gepflegt werden müssen. Der Home-Thread bleibt der alleinige Eigentümer des Home-Headers; Content-Thread darf dessen aktuelle Plugin-Dateien nicht überschreiben.

**Quellbelege:**
- [Content Composer 0.1.1 / ACADEMY-HERO-02](ANDY-CONTENT-COMPOSER-02-ACADEMY-HERO-v0.1.1-2026-11-23.md)
- [Verbindliches Versions- und Installationsgate](../docs/ANDY-WORDPRESS-RELEASE-UND-IMPORT-GATE-v0.1-2026-11-23.md)
