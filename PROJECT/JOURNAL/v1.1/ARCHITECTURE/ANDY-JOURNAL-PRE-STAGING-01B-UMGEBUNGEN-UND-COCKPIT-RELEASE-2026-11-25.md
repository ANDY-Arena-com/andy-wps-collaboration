# ANDY Journal · PRE-STAGING-01B – Umgebungsvertrag & Cockpit-Harmonisierung

**Stand 25.11.2026 · Status: Quellcode-Release lokal erstellt, isoliert geprüft; WordPress-/Hostinger-Installation, Staging- und Live-Abnahme ausstehend.**

**Basis:** [PRE-STAGING-01A Quell-Audit](ANDY-JOURNAL-PRE-STAGING-01A-PLUGIN-MENUE-HOOK-AUDIT-2026-11-25.md) · [Verbindlicher Architekturvertrag](ANDY-JOURNAL-PRE-STAGING-ADMIN-UND-LAUNCH-GOVERNANCE-2026-11-25.md) · [Making of MO12](../content/ANDY-MAKING-OF-STORY-KATALOG-v0.1-2026-11-25.md#6-mo12--vom-werkzeug-wildwuchs-zur-betriebszentrale-25112026).

## Ergebnis

Aus dem vom Nutzer aus WordPress exportierten Bestand `ANDY-WP-PLUGIN-Package.zip` (SHA-256 `4277fcb18aa60d55b3e7e940d23143088b402addf7344abf8432610ed0fe420a`) wurden **drei unabhängige, gezielte Updates derselben bisherigen Pluginordner** vorbereitet:

| Owner | Vorher | Nachher | Technische Änderung |
|---|---:|---:|---|
| `andy-journal-cockpit` | 0.2.0 | **0.2.1** | 21 vorhandene Werkzeugziele (statt 11 historische), fünf Gruppen; eindeutige Trennung von „System & Inventory“ vs. „Story & Content Management“ bei **unveränderten WP-Slugs/Callbacks**. Bestehender reversibler Kompaktmodus `andy_jc_compact_tools_menu_v020` mit neun optional ausgeblendeten `tools.php`-Links unverändert. Admin-Gate auf explizite Stage erweitert. Versionsübersicht erfasst Home/Content/Making of. |
| `andy-rgb-pilot` | 0.6.3 | **0.6.4** | Stage-Host-/Environment-Gate für Admin und Legacy-RGB-Routen. Direkte RGB-Asset-Anfragen werden bei fehlender Staging-Vorschau-Freigabe 404 statt durchgereicht. Der bisherige `argb_front_decision()`-Routingalgorithmus, Verifizierung/Contentkeys und Production-Standardmodus bleiben unverändert. |
| `andy-home-composer` | 0.1.38 | **0.1.39** | Stage-Host-/Environment-Gate für bestehende DE/EN-Home; Production-Hostprüfung bewahrt bisherige Parsing-Semantik. Unveränderter Renderer, CSS/JS, Modulkonfiguration, Layout und WordPress-Option `andy_home_composer_public_v01`. |

**Nicht geändert:** Launch Control 0.1.0 (nutzt bereits `andy_jc_allowed()`), Content Composer 0.1.29, Content Manager 0.4.8, Making of 0.1.0, Editorial v2, Integrator, Elementor, WpSection, Aculia, RGB-Contentdaten. Keine neue Datenhaltung, keine automatische Publikation, keine Datenbank- oder Medienänderung.

## Strikter Host-/Vorschau-Vertrag

- **Production:** `journal.andy-arena.com` bleibt in den untersuchten Codepfaden wie zuvor zugelassen. Die eigenständige Arena unter `andy-arena.com`, `blog.andy-arena.com` und fremde Hosts werden dadurch nicht freigeschaltet.
- **Staging:** ausschließlich `https://staging-journal.andy-arena.com` mit passend konfigurierter WordPress-Home-URL, passendem Request-Host und **`WP_ENVIRONMENT_TYPE=staging`** (WordPress `wp_get_environment_type()`).
- **Staging-Admin:** ausschließlich mit `manage_options`. **Staging-Frontend bei Auslieferung der Composer-/RGB-Routen:** nur mit `manage_options`, solange kein externer Hostinger-Passwortschutz bestätigt wurde. Nach echter Prüfung einer wirksamen HTTP-Basic-Auth bzw. Hostinger-Site-Sperre kann **nur in der Staging-Konfiguration** explizit `ANDY_STAGING_HTTP_AUTH_CONFIRMED=true` gesetzt werden. **Die Konstante verifiziert nicht selbst den Host-Schutz.** Alle anderen WordPress-Routen bleiben auf tatsächlichen Hostschutz angewiesen; `noindex` ist nicht ausreichend.
- **Abweichende temporäre Staging-Systemdomain:** nicht vorab als gültiger Host freischalten; die neue Instanz benötigt dann einen eigenen eng begrenzten Hostvertrag. Kein Wildcard-Check.

Die historisch hostgebundenen Content-Manager-DESIGN-/Publishing- sowie Integrator-/Editorial-Pilot-Werkzeuge bleiben vorerst absichtlich auf ihrer bisherigen Domain. Das ist **keine vollständige funktionale Parität aller Legacy-Tools** nach dem Klon. Die Home-/RGB-/Cockpit-Kernfunktionen sind code-seitig vorbereitet; echte Tests auf Staging bleiben zwingend.

## Download-Artefakte und SHA-256

Installierbare ZIPs wurden **nur im Chat**, nicht als GitHub-Binaries veröffentlicht. Drei Original-Pluginstände wurden jeweils aus **derselben Nutzerexport-Baseline** als eigene Rollback-ZIPs gesichert:

| Paket | SHA-256 |
|---|---|
| `ANDY-WP-PLUGIN-Journal-Cockpit-v0.2.1-PRE-STAGING-01B.zip` | `c8c6011c313973e8e2de89c08641114c653f00cef69973e8a2b3fc42536c7dd9` |
| `ANDY-WP-PLUGIN-Journal-Cockpit-v0.2.0-ROLLBACK.zip` | `5151866cf010deb563e375760cdf75f5f192a62886d61d9df47e97a3fa3ae3b5` |
| `ANDY-WP-PLUGIN-RGB-Pilot-v0.6.4-PRE-STAGING-01B.zip` | `d82347367411fa0f9e920db8020f697d42ae2bfe29cd774c6f3501116c3b1cc6` |
| `ANDY-WP-PLUGIN-RGB-Pilot-v0.6.3-ROLLBACK.zip` | `801907db27a3a64f90fa86d1cb4e66fea2f46faee383b38eddeb16ddf094fa1e` |
| `ANDY-WP-PLUGIN-Home-Composer-v0.1.39-PRE-STAGING-01B.zip` | `8847b0c5bd73021f4387f627b036ec7aaa2fd16edb9d9977650e2fba94d45d87` |
| `ANDY-WP-PLUGIN-Home-Composer-v0.1.38-ROLLBACK.zip` | `647050880609ed3d12a6ff38dfa710e6e0e8c4adb092a7faab5955e192e5aca2` |

Transport-ZIP: `ANDY-PRE-STAGING-01B-UPDATE-ROLLBACK-BUNDLE-2026-11-25.zip`. **Nicht direkt als WP-Plugin installieren**; die drei enthaltenen Release-ZIPs separat installieren und Rollbacks behalten. Releasebericht im Bundle: `ANDY-PRE-STAGING-01B-RELEASE-UND-ROLLBACK-2026-11-25.md`.

## QA – was bewiesen ist und was nicht

- **103/103 lokale Checks bestanden:** PHP-WordPress-Stubs für 14 Kombinationen (Production / Staging / fremder Host × Rollen × Environment × Previewflag), 21 Cockpit-Ziele in fünf Gruppen, beidseitige Content-Manager-URLs, erhaltene Kompaktoption, Main-Routingfunktionen und unveränderte Asset-Datei-Hashes, PHP-Syntaxchecks. ZIP-Dateianzahl, Rootordner, CRC und Prüfsumme nach Packen geprüft.
- **Kein WordPress-End-to-End-Nachweis:** Weder Update in Hostinger noch WP-Admin-/Browser-/Mobil-/Cache-/Staging-Test durchgeführt. Plugin-Codeversion ist **nicht** identisch mit installiertem Versionsstand; der Nutzer entscheidet über Einspielen und Abnahme.

## Installation (separater Schritt, noch offen)

1. **Vorher ein echtes vollständiges Production-Backup** inkl. DB/Uploads, WordPress-Plugins, Options, Site-URLs und Rollback-Möglichkeit. Bereits gespeicherte RGB-HTML/JS/CSS leben in **WordPress `wp_options`**, nicht im Plugin-ZIP.
2. **Cockpit 0.2.1** einzeln installieren; Original-Adminnavigation, die 21 Links und den unveränderten Kompaktmodus prüfen.
3. **RGB 0.6.4** installieren; `content`-Modus, Root, verifizierte `?andy_rgb_asset`-Sitemap/A–Z, Admin-RGB und Trackinglinks prüfen.
4. **Home 0.1.39** installieren; DE/EN, `/`, `/?utm_source=...`, Academy/Perspectives/Making-of, Assets, Header, mobiles Menü und Cache per Inkognito testen.
5. Bei Abweichung: **jeweiligen Original-Pluginordner aus passendem Rollback-ZIP wiederherstellen**, Cache leeren und WordPress-Zustand kontrollieren. Keine Installation/Deinstallation durch diesen Commit.
6. Erst nach tatsächlicher Production-Abnahme und vollständigem Backup den geschützten Staging-Klon erstellen, WordPress-Environment/Host und Datenbanktrennung prüfen, dann Staging-E2E ausführen. Für spätere Releases ausschließlich gezielte Plugin- und Datenübertragungen, kein blindes Hostinger-Publish der gesamten Staging-DB.

## Fortsetzung

**PRE-STAGING-01C:** zentrale, vom WordPress-Veröffentlichungsstatus getrennte Freigaben `internal` / `coming_soon` / `live` für Home–Gabelseite–Content, DE/EN-Teaser und Publishing-Historie. Erst nach zusätzlicher Code-/Routingprüfung (inkl. Legacy-RGB, REST/Sitemap/Feed/Cache) implementieren; nicht als bereits vorhandene Funktion bezeichnen.

**Making-of-Lehre:** Die Kompaktansicht existierte bereits, aber ihr Geltungsbereich war unvollständig; der Umgebungswechsel machte lokale Host-Sicherheitsbedingungen zum globalen Integrationsproblem. Das ist ein konkretes Ergebnis von [MO12](../content/ANDY-MAKING-OF-STORY-KATALOG-v0.1-2026-11-25.md#6-mo12--vom-werkzeug-wildwuchs-zur-betriebszentrale-25112026).