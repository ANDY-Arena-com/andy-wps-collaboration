# GUIDED-IN-COMPOSER-01 · Home Composer 0.1.48

**25.11.2026 · Nutzerwunsch umgesetzt, Staging-first Release-Candidate. NOCH NICHT auf Hostinger installiert.**

## Nutzerkorrektur

Die erste `andy-guided-preview` v0.1.0 ist ein separat verwaltetes Live-Zusatzplugin unter „Werkzeuge“, dessen Slideshow **nachträglich** vor dem Footer erscheint. Der Nutzer möchte sie stattdessen **als nativen Typ auf derselben Home-Composer-Seite**, weil dort **Claim-Teaser und alle anderen Home-Module angeordnet und gestaltet** werden. Ein bloßer Link zum separaten Editor reicht nicht.

**Home Composer 0.1.48** integriert `guided` als **nativen Modul-Typ**: **„+ Guided Preview · Slideshow“** in der Modulbibliothek, Aktiv-Schalter, ↑/↓ und normale Home-Vorschau. Fünf DE/EN-Folien (Fight Night, Research, Perspectives, Academy, Making of), je Titel, Untertitel, Erklärung und Akzentfarbe, optionales Autoplay 6–20 s, Standard aus. **Die vorhandenen Claim-Module bleiben unverändert**, mit individuellen Farben, Links und CTA. Sie können direkt vor/nach der Slideshow platziert werden. Folien-Untertitel übernehmen die Botschaft innerhalb der einzelnen Folie; es werden keine zusätzlichen Claim-Module pro Folie generiert. Header/Hero/Footer und WordPress-Posts unverändert.

## Migration / keine Doppelung

Beim **ausdrücklichen Hinzufügen** des neuen Guided-Moduls in **DE** zieht der Editor als Seed die bislang auf **derselben** WordPress-Installation gespeicherten Texte aus `andy_guided_preview_live_v01` (falls vorhanden), sonst beigefügte öffentliche Defaults. Die Texte werden **erst bei Home-Composer-Speichern** in dessen vorhandene Option `andy_home_composer_config_v01` übernommen. Danach bearbeitet man **beide Sprachen im DE-Modul**; EN übernimmt Modulreihenfolge und hat separat den Aktiv-Schalter. Kein automatischer Options-/DB-Transfer zwischen Live und Staging.

Das alte eigenständige Zusatzplugin erkennt **`#andy-guided-preview`** nach dem Native-Rendern und fügt dann **keine zweite Slideshow** hinzu. **Erst nach Bestätigung, dass das native Modul gespeichert ist und auf Live in DE/EN korrekt gerendert wird**, das alte Add-on deaktivieren. Wird der alte Renderer zu früh deaktiviert, bleibt die Home zunächst ohne Slideshow, solange noch kein natives Modul angelegt wurde. Ein technischer Rollback auf 0.1.47 macht das neue `guided`-Modul für die ältere Version unbekannt; dann altes Add-on wieder aktivieren und vor neuer Modul-Speicherung ggf. WP-Backup wiederherstellen.

## QA / Grenzen

- **6/6 PHP-Dateien `php -l`**, JS-Syntax, ZIP-CRC/Pluginroot OK.
- **7 isolierte PHP-Sanitizer-Assertions** für neue Guided-Modul-Daten inkl. DE/EN, Farbe, Text, Autoplay, Limit.
- **Headless Chromium-Tests** in synthetischer Composer/Home-DOM: Native-Modul zwischen Claim und Footer, fünf Slides, Pfeile/Dots, DE Desktop/EN Mobile ohne Horizontalscroll bei 390px, Original-Claim-Link/Farben erhalten, altes Add-on-Frontend-Skript gleichzeitig aktiv **ohne zweite Slideshow**, Modul-Admin „+ Guided“, keine doppelte Erstellung, Folien-Editor-Änderung im Formular-JSON, keine JS-Pageerrors.
- **Diff zu 0.1.47:** 5 geänderte Dateien (Haupt-PHP, multilingual-home.php, composer.js, composer.css, readme.txt), 2 neue (Default JSON, README), 37 unverändert, 0 entfernt. Keine Änderungen an den bestehenden Environment-/Preview-/Hero-/Highlights-/Typography-Dateien.
- **Kein echter Hostinger-/WP-Plugin-/Cache-End-to-End-Test**; alle Ergebnisse lokal/synthetisch. Keine automatische öffentliche Freigabe interner Artikel oder WHY-Daten; PRE-STAGING-01C2B bleibt offen.

**Installations-ZIP** im Chat: `INSTALL-IN-WORDPRESS-ANDY-Home-Composer-0.1.48-GUIDED-IN-COMPOSER-01.zip` SHA-256 `0522cb64aab6af3a91c61ce2459fb551e72529b0848587ec9d6306e2b2821770`.

**Rollback** im Chat: `ROLLBACK-ANDY-Home-Composer-0.1.47-GUIDED-IN-COMPOSER-01.zip` SHA-256 `3ce09448eb38d82caaf08300e4dbcc9dd3e5ae8371d9287a307cb32345f9c71b` (bytegleich zu gemeinsam installiertem 0.1.47).

**Einmaliger gemeinsamer Release-Zug:** Zuerst 0.1.48 nach Backup auf Staging testen, dann dieselbe ZIP nach Live-Backup auf Live installieren; dort im DE Home Composer ein Guided-Modul hinzufügen und speichern. Live-Site mit nur einer Slideshow + Claims prüfen, anschließend das alte Guided-Preview-Zusatzplugin deaktivieren. **Danach kein weiterer Live-Zwangsupdatezyklus**; sonstige Journal-Weiterentwicklung weiter auf Staging. Separater Release-Bundle-Vertrag bleibt gültig.

**Detailbericht im Chat:** `ANDY-GUIDED-IN-COMPOSER-01-HOME-COMPOSER-0.1.48-RELEASE-2026-11-25.md`.