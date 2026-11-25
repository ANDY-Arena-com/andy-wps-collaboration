# ANDY Journal · STAGING-HOST-GUARD-01 – Hostinger-Staging korrekt erkennen

**25.11.2026 · Lokaler Release-Candidate (noch nicht auf Hostinger installiert / WordPress-E2E-abgenommen)**  
**Home Composer 0.1.41 → 0.1.42** / **Launch Control 0.2.2 → 0.2.3**

## Anlass / Nutzerbeobachtung

Nach der Hostinger-Staging-Erstellung zeigt der Home Composer auf der Staging-Admin-Site irrtümlich **`LIVE · staging.journal.andy-arena.com`** und eine daraus zusammengesetzte Phantasiadresse **`staging-staging.journal.andy-arena.com`**. Auf der tatsächlichen Live-Site ist weiterhin der alte **geplante** Host `staging-journal.andy-arena.com` als Ziel hinterlegt. **Der korrekte Hostinger-Staginghost ist `staging.journal.andy-arena.com`, nicht der frühere Planname.**

**Wichtig:** Nicht die Hostinger-Domain ändern lassen, sondern den ANDY-Code an die tatsächlich bestehende Staging-Umgebung anpassen. Domain-Migration/WordPress-Home-URL-Korrekturen dürfen ausschließlich auf der zugehörigen Instanz erfolgen, niemals blind auf Live.

## Technische Korrektur

**Home Composer 0.1.42**:
- Kanonische Hosts aus URL-rewrite-robusten Hostbausteinen, statt hartem, im Klon potenziell umgeschriebenem Production-Domainliteral.
- Explizites **Dreifach-Gate** aus HTTP-Host, WordPress-`home_url()`-Host und `wp_get_environment_type()`. Nur `journal.andy-arena.com` mit `production` = LIVE, und `staging.journal.andy-arena.com` mit `staging` = STAGING. Alles andere ist **unverifiziert**.
- Bei unbekanntem/misskonfiguriertem Host **„STOP · WordPress-Umgebung nicht verifiziert“** statt falscher LIVE-Anzeige: keine Composer-Bearbeitungsformulare, keine Composer-Vorschau/Editor-Assets, eigene `andy_hc_*`-POST-Aktionen via `admin_init` 403; automatische Composer-Migration und Fight-Night-Meta-Saves bei unverifizierter Site übersprungen. **Kein globales Schreibverbot für WordPress oder Drittplugins**; zusätzliches Hostinger-Passwort bleibt Pflicht.
- Echte Zwei-Button-Navigation mit DE/EN, Coming Soon privat und Link zu den **jeweiligen lokalen WP-Admins**. Die bereits vorhandene Live-Checkbox zur Staging-Link-Freigabe bleibt **default OFF / nicht automatisch angeschaltet**. Keine Remote-Operation, kein Plugin-Sync, kein öffentliches Release.
- Vorheriges 0.1.41-ZIP: 36 Dateien; **3 geändert + 1 README neu, keine entfernt**. Home-/Hero-/Header-/Elementor-/Module-/WP-Optionen unverändert.

**Launch Control 0.2.3**:
- Der unveränderte **read-only Preflight** erkennt den tatsächlichen Staginghost nach demselben Host/WP-Umgebungs-Vertrag und meldet Konflikte offen. Die bisherigen 15 Zugriffsflächen bleiben **OFFEN**, keine automatisch wirksame Sperre oder Freigabe.
- Vorheriges 0.2.2-ZIP: 11 Dateien; **3 geändert + 1 README neu, keine entfernt**.

## QA und Binärartefakte

| Datei (als Einzel-ZIP im Chat) | SHA-256 |
|---|---|
| `INSTALL-IN-WORDPRESS-ANDY-Home-Composer-0.1.42-STAGING-HOST-GUARD-01.zip` | `8b0e63a3e22452d66ebe588eea1adb4e48b9b25f0ffdf75bf04b79fe940b2fff` |
| `INSTALL-IN-WORDPRESS-ANDY-Launch-Control-0.2.3-STAGING-HOST-GUARD-01.zip` | `f89b1a58c8e6159df2ca1d86c6b9bbf65bb658f3659f19f01aff917cbe89b081` |

**Rollback:** unveränderte ursprüngliche Einzelplugin-ZIPs `INSTALL-IN-WORDPRESS-ANDY-Home-Composer-0.1.41-PIPPI-ENVIRONMENT-SWITCH-01.zip` und `INSTALL-IN-WORDPRESS-ANDY-Launch-Control-0.2.2-SECURITY-PREFLIGHT-01C2B0.zip`.

**Isolierte lokale QA:** 68/68 PHP-Assertions für neun Kombinationen aus Host/Home/WP-Typ, UI/404-Lock, 403-POST-Sperre, Navigation, Live-Staging DE/EN und Launch-Control-Umgebungsidentität. **11/11 Plugin-PHP-Dateien syntaktisch geprüft**, bestehendes Composer-JavaScript syntaxgeprüft; ZIP-CRC, WordPress-Plugin-Root und Datei-Diff bestanden. **Kein Live-Staging-Browser-/PHP-/Cache-/Drittplugin-Test**. Kein Hostinger-Zugriff und keine automatische WP-Konfiguration vorgenommen.

## Sichere Reihenfolge für Hostinger und WordPress

1. Bestehende **zwei tatsächliche Domains beibehalten:** Live `journal.andy-arena.com`, Staging `staging.journal.andy-arena.com`. Nicht die Namen angleichen/umbenennen.
2. Auf Hostinger verifizieren: **separate WordPress-Datenbank und Dateien**, korrekte `home`-/`siteurl`-URLs auf jeder Instanz, SSL, externer Passwort-/Zugriffsschutz, E-Mail-/Cron-/API-Isolation. **Kein** blindes Kopieren der Live-Datenbank oder generelles Suchen/Ersetzen über beide Sites.
3. In **Staging** `WP_ENVIRONMENT_TYPE` als `staging` in eigener WordPress-Konfiguration prüfen; falls fehlt, nur dort `define('WP_ENVIRONMENT_TYPE','staging');` **vor WordPress-Bootstrap, nicht doppelt** setzen (Hostinger-KI darf diese konkrete Konfiguration prüfen/erledigen, niemals Live-WP-Konfig ändern). Live bleibt `production`.
4. Nach erfolgreicher Trennungsprüfung zuerst die beiden **Einzel-ZIPs** auf Staging installieren, echte WP-Ansicht prüfen. Erwartet: `STAGING · staging.journal.andy-arena.com`. Bei falschem WP-Typ: **STOP** statt Editor – Hostinger-Konfiguration korrigieren.
5. Mit Live-Backup dieselben Pluginversionen auf Live aktualisieren. Erwartet: `LIVE · journal.andy-arena.com`. Erst dann im Live-Composer nach eigener Prüfung die **Staging-Verknüpfung** aktivieren.
6. Danach **Staging-only-Änderung** vornehmen, Live vergleichen und getrennte Datenhaltung bestätigen. **Kein Hostinger „Publish“ oder „Push to Live“**; dies kann Live-Dateien und Live-DB überschreiben. Später nur geprüfte selektive Transfers.

## Verbindliche Grenzen

- Diese Updates sind **nur Environment-/UX-/Diagnose-Fixes**. Sie **erstellen keine Staging-Installation**, **setzen nicht** `WP_ENVIRONMENT_TYPE`, **konfigurieren kein HTTP-Passwort** und **implementieren kein PRE-STAGING-01C2B-Publikationsgate**.
- Vor jeder öffentlichen Coming-Soon-Leseprobe bleibt das Gesamtgate für native Permalinks, DE/EN, RGB, Suche, REST, Feeds, Sitemap, Uploads und Caches **OFFEN**.
- Prüfdokument im Chat: `ANDY-STAGING-HOST-GUARD-01-HOME-0.1.42-LAUNCH-0.2.3-RELEASE-2026-11-25.md`.

### Architekturreferenzen
- [Pippi-Environment-Switch](ANDY-JOURNAL-ENVIRONMENT-SWITCH-EDITOR-01-2026-11-25.md)
- [Staging/Live-Sync-Vertrag](ANDY-JOURNAL-STAGING-LIVE-SINGLE-WORKSPACE-SYNC-CONTRACT-2026-11-25.md)
- [Security Preflight](ANDY-JOURNAL-PRE-STAGING-01C2B0-SECURITY-PREFLIGHT-2026-11-25.md)

## Nutzerbestätigung: STAGING-01-Infrastrukturabgleich (25.11.2026)

Hostinger bestätigt eigenständige WordPress-Installationen und Datenbanken, auf Staging `home`/`siteurl` jeweils **`https://staging.journal.andy-arena.com`** sowie ausschließlich dort eine einmalige `WP_ENVIRONMENT_TYPE=staging`-Definition, zur Laufzeit validiert. Live nicht geändert; **kein** „Publish to Live“. **Noch nicht nachgewiesen:** externer Zugriffsschutz durch anonymen HTTP-Test auf HTML, REST, Medien und Cache; Hostinger meldet aktiven internen Staging-Zugriffsschutz, aber keinen separaten Apache-Basisschutz. **Noch offen:** Unterdrückung von `wp_mail()` und ggf. direkten SMTP-/API-Mailern, WordPress-/Hostinger-System-Cron und produktiven Webhook-/API-Nebenwirkungen. Diese Sicherheitsgates vor nichtreversiblen Staging-Tests schließen. Nach Isolationsabnahme beiden Staging-Plugins 0.1.42/0.2.3 installieren; anschließend identische Versionen auf Live nach Backup. Kein Live-Transfer oder Freigabe-Adapter durch diese Bestätigung.

