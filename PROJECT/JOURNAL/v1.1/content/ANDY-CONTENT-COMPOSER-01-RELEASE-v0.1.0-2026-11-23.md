# ANDY Journal Content Composer 0.1.0 – CONTENT-01 Release

> **NEUER RELEASE:** [Content Composer 0.1.1 / ACADEMY-HERO-02](ANDY-CONTENT-COMPOSER-02-ACADEMY-HERO-v0.1.1-2026-11-23.md) verschiebt auf Academy-Beiträgen das Featured Image **über** den Artikel in ein vollbreites Hero. Diese Seite dokumentiert die historische Basis 0.1.0.

**Stand:** 23.11.2026  
**Zuständigkeit:** Content-Thread. **Home-Thread bleibt allein zuständig für `andy-home-composer/*`.**  
**Status:** Plugin-ZIP lokal erzeugt und PHP-/ZIP-/Importer-Offlinetests bestanden. **Auf Hostinger noch nicht installiert oder abgenommen.**

## 1. Zwei ZIPs – strikt verschiedene Installationswege

| Artefakt | Tatsächlicher Typ | Vorgang | SHA-256 |
|---|---|---|---|
| `ANDY-WP-PLUGIN-Journal-Content-Composer-v0.1.0-CONTENT-01.zip` | **Neues WP-Plugin**: Verzeichnis `andy-journal-content-composer/` | **Plugins → Plugin hinzufügen → hochladen**, danach aktivieren | `9efdc82795cce0d4323c715dd93901ad19250f5ba61ef50df12345c0334eaa11` |
| `ANDY-ACADEMY-L02-CONTENT-PACKAGE-v0.1.zip` | **Nur Content-Daten** | Nach Plugin-Aktivierung **Beiträge → ANDY Content Composer → Academy L02 importieren** | `5c86bfdf1efaeb7df9a17275a1609f704c1232ce0e882d3f2935ed139fb95670` |

Die ZIPs wurden dem Nutzer im Chat zur Verfügung gestellt. **Dies ist eine Release-Dokumentation, kein behaupteter GitHub-Quellcode-Upload.** Das Plugin-ZIP hat sechs Quell-/Asset-Dateien; das L02-Daten-ZIP zehn Dateien. **Kein Downgrade des bestehenden Home Composer.** Aus Nutzer-Screenshot ist für den 23.11. eine installierte Home-Version **0.1.15** bekannt; seitdem etwaige neuere Versionen im WP-Admin erneut prüfen.

## 2. Tatsächlicher Implementierungsumfang

- Opt-in **WP-Post-Templates** per Metabox `ANDY · Beitrags-Template`: `academy`, `fightnight`, `research`, `perspectives`, `standard`. Ist kein Template gesetzt, bleiben die nativen WP-Templates unangetastet.
- Eigene Content-Ansicht **nur für entsprechend konfigurierte WordPress-Beiträge**. Responsiver Beitragstitel, Lead, Featured Image (contain, kein absichtliches Cropping), Artikeltext, Tags, verwandte veröffentlichte Beiträge. Theme-Header und -Footer bleiben WordPress-eigen.
- **Zentrale Farb-Themes je Vorlagentyp**, editierbar unter **Beiträge → ANDY Content Composer**. Post-spezifische `bg`-/`accent`-Overrides möglich; Vorlage ist getrennt von der WordPress-Kategorie.
- **L02-Paketimport:** prüft Whitelist-Paths, Paket-Schema, Status `draft`, Dateitypen, SHA-256 aller deklarierten Dateien, JPEG-MIME, ZIP-/Dekompressionsgröße, Content ohne ausführbaren PHP-/JS-Code; setzt WP-Post mit `draft`, Academy/Erleben-Kategorien, Tags und Medienanhang. Idempotenz über `_andy_cc_package_id`, ohne bereits bearbeitete Artikel zu überschreiben. Import nur für Admins mit `manage_options` und `upload_files`, jeweils mit Nonce.
- **L02 interaktive Einbettung:** `[andy_cc_interactive]` als Slot in der Artikelstruktur. Ausdrücklich **noch nicht spielbar**. Keine Fake-Go-Engine, keine iframe-Notlösung. Der Slot zeigt einen nicht-interaktiven Integrationshinweis, bis der Original-Renderer anhand echter Version/Datenschema via `andy_cc_registered_renderers` angebunden ist.
- **Keine** Änderungen an `andy_home_composer_*`-Optionen, `andy-home-composer/`, Aculia Original-Home #14, Elementor-Daten, Home-Routing, RGB-Assets oder älterem `andy-content-manager`.

**Scope-Grenze:** Fünf Templates sind vorhanden, aber **noch kein frei sortierbarer Modul-Editor auf Contentseiten**. Im ersten Release steuert der normale WP-Artikeltext die Position des interaktiven Shortcodes. Der generische Multi-Modul-Content-Builder, vollständiges Academy-Gameplay, automatische Home-Teaser, neue Match-Story-/Research-Importer und mehrsprachige Artikel werden erst in Folgereleases bearbeitet.

## 3. Konkret installierte Daten und APIs

**Eigene WP-Option:** `andy_cc_themes_v01` mit globalen Farb-Presets je Template.

**Eigene WP-Metafelder:**
- `_andy_cc_template`, `_andy_cc_intro`, `_andy_cc_overrides`
- `_andy_cc_package_id`, `_andy_cc_package_version`, `_andy_cc_imported_sha256`
- `_andy_cc_renderer`, `_andy_cc_renderer_version`, `_andy_cc_lesson_data`, `_andy_cc_layout_data`
- `_andy_cc_asset_for` am Medienanhang

**Renderer-Anschluss:** Filter `andy_cc_registered_renderers`, assoziatives Array je Schlüssel `['version'=>'x.y.z','render'=>callable]`. Wird nur von installiertem **geprüftem PHP-Code** registriert, nicht aus fremden Daten-ZIPs. Pilot-L02 bleibt wegen `_andy_cc_renderer_version='unknown'` bewusst blockiert, auch wenn gleichnamiger Schlüssel auftauchen sollte.

**WP-Frontend:** `template_include` für explizit gekennzeichnete einzelne `post`-Beiträge; Root-Home wird nicht abgefangen. Der Benutzer sieht auf dem ausgewählten Beitrag eine neue ANDY-Content-Vorlage, nicht das HTML-Klickdummy.

## 4. Testprotokoll, was wirklich geprüft wurde

| Test | Resultat |
|---|---|
| PHP Syntax: Plugin-Root, Importer, Admin, Template | **PASS** (`php -l`) |
| ZIP-Inhalt: sechs Dateien unter separatem `andy-journal-content-composer/` | **PASS**, CRC und Struktur |
| L02-Content-Paket anhand Manifest und 10 Dateiinhalten prüfen | **PASS** |
| Import via Offline-WordPress-Funktionsstubs: Draft + Medienreferenz, korrekter Shortcode, kein doppeltes H1 | **PASS** |
| L02-Reimport: keine Duplikate und keine Textüberschreibung | **PASS** |
| Verändertes Artikel-HTML ohne aktualisierte SHA-256 | **BLOCKIERT**, wie beabsichtigt |
| Hostinger/WP-Admin-Installation und reales Theme-Rendering | **NOCH NICHT GEPRÜFT** |
| Echtes Academy-L02-Gameplay | **NICHT IMPLEMENTIERT**, Original-Plugin fehlt als aktuelle Quellgrundlage |

**Sonderfall:** Scheitert Medienupload nach Draft-Erstellung, bleibt der Post als prüfbarer Teilimport erhalten; Bild muss administrativ nachgetragen werden (kein blindes Neuimport-Overwrite). Das ist als Pilotgrenze dokumentiert.

## 5. Abnahme auf WordPress

1. Backup von Datenbank, Plugins, Themes, Uploads; reale Versionsstände erneut prüfen.
2. **Nur Plugin-ZIP** unter Plugins installieren. Im Installationsdialog darf **nicht** `ANDY Journal Home Composer` / `andy-home-composer` erscheinen. Falls doch: **STOP**.
3. Aktivieren → **Beiträge → ANDY Content Composer** → **Content-ZIP** importieren.
4. Entwurf prüfen: Academy-Template, Kategorien/Tags, Featured Image, Untertitel, normaler Artikeltext, klarer Statushinweis bei der Interaktion.
5. Academy-Theme-Farben ändern → Preview aktualisieren; post-spezifische Override testen.
6. Mit **Beiträge → Neu → Research** zweiten Beitrag als Entwurf anlegen, Template wechseln, Vorschau prüfen.
7. Root `/` und Home-Composer-Admin unverändert prüfen; nach Test Screenshot und tatsächliche Version dokumentieren.

## 6. Folgerelease / Ressourcengrenze

Priorität: Original-**ANDY Academy**-Renderer/Plugin samt Szenen-/Regeldaten und ZIP-Vertrag beschaffen, prüfen und mit `[andy_cc_interactive]` verbinden. **Nicht aus Nutzer-Screenshots einen funktionierenden Go-Spieler erfinden.** Der Home-Thread kann parallel mit Home 0.1.15+ weiterarbeiten.

### Referenzen

- [Verbindliches WordPress Release- und Import-Gate](../docs/ANDY-WORDPRESS-RELEASE-UND-IMPORT-GATE-v0.1-2026-11-23.md)
- [Parallele Zuständigkeiten und L02-Content-Pilot](ANDY-CONTENT-COMPOSER-PARALLEL-WORK-AND-ACADEMY-L02-PILOT-v0.1.md)
- [Historisches Journal-Composer-Handover](../docs/ANDY-JOURNAL-CMS-UND-HOME-COMPOSER-HANDOVER-2026-11-23.md)

**Freigabestatus:** Lokale Entwicklung abgeschlossen; **WordPress-Integration steht als Testinstallation aus**.
