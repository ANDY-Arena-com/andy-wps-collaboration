# ANDY Journal – Integrator 2D: vorlagentreuer Header-/Footer-Abgleich im Entwurf

**Stand:** 22.11.2026 · **Plugin:** ANDY Journal Integrator **0.2.3** · **Status:** lokal implementiert und getestet, Hostinger-Installation/visuelle Abnahme offen; kein Live-Deployment.

## Echte Befunde aus 2C

Das WordPress-Admin-Audit `ANDY-INTEGRATOR-02C-20261122.json` von 22.11.2026 15:59:30 UTC belegt:
- Veröffentlichte Aculia-Homepage **#14**, private 02B-Kopie **#1362**, beide `tpl-default-elementor.php`.
- In beiden **drei** Slides des `wpsection_banner_slider` `1eef5e6`, gleiche Medien-IDs **1324/1325/1326**, aber erwartungsgemäß unterschiedliche Texte.
- **#14** weist seitenbezogen den Home-Header **#26** und den Footer **#455** zu. **#1362** fehlen sämtliche sieben geprüften Aculia-Seitenmetafelder: `banner_elementor_template`, `footer_elementor_template`, `footer_style_settings`, `header_new_elementor_template`, `header_source_type`, `header_style_settings`, `sidebar_elementor_template`. Die globalen Theme-Mods enthalten Header **#532** und Footer **#455**, bleiben unverändert.
- Der historische dynamische Publishing-Hook `andy_s_front` aus `andy-content-manager/publishing.php` ist für `elementor/frontend/builder_content_data` registriert. **Ob er beim Entwurf #1362 dieselbe Ausgabe wie auf #14 erzeugt, ist nicht nachgewiesen.**

**Einordnung:** Die fehlenden Seiteneinstellungen sind ein belegter Konfigurationsunterschied. Ihre Übernahme ist nicht gleichbedeutend mit einer garantierten identischen Frontend-Ausgabe.

## Implementierung 2D

Das Paket **`ANDY-WP-PLUGIN-Integrator-v0.2D.zip`** aktualisiert den existierenden Ordner `andy-journal-integrator` von **0.2.2 auf 0.2.3**, ohne ein zusätzliches Plugin anzulegen. Funktionen 0.1, 0.2A, 0.2B und 0.2C bleiben erhalten.

Neu ist **Werkzeuge → ANDY Integrator → Abschnitt 10** mit:
1. Lesender Gegenüberstellung der sieben Schlüssel und der Meta-Abweichungen.
2. **Nur nach explizitem Admin-POST:** Kopie der genau sieben Original-Postmeta-Werte von **#14** nach **#1362**, zuvor Backup von Existenz und Wert jedes Feldes in speziellen 2D-Metadaten von #1362.
3. Geschützter Rollback nur bei unveränderten sieben Zielwerten; Teilfehler lösen einen Best-Effort-Rollback aus.
4. Strikte Sperren: exakte Testdomain, `manage_options`, Nonce, POST und Bestätigung, `page_on_front=14`, `#14` veröffentlicht, `#1362` unveröffentlichter 2B-Draft mit Original-Marker, vorab eingefrorene 2C-Elementor-Fingerprints und Feld-Hashes sowie ausdrücklich die Header-/Footer-IDs #26/#455. Bei Drift kein Apply.

**Unverändert:** die aktive #14, die Header-/Footer-Template-Objekte #26/#532/#455, globale Theme-/WP-Optionen, Elementor-JSON/Layout, Slider-Texte/-Bilder, Content-Manager-Hooks, RGB-Frontend, A–Z und öffentliche Domains. Kein Reimport früherer HOME-01-/DESIGN-01-Pakete.

## Lokale Prüfung

- PHP-Lint (Main + 2B/2C/2D): **bestanden**
- Bestehende 2C-Regression: **29 Assertions bestanden**
- Neue 2D-Tests mit synthetischen WordPress-Metas: **46 Assertions bestanden** (Apply, Rollback, Doppelausführung, partieller Schreibfehler, Manipulation, Hash-/Host-/Status-/Berechtigungssperren)
- ZIP-Inhalt und CRC: **bestanden**; bereits vorhandene Assets und Klassen 2B/2C byteidentisch mit 2C-Paket
- ZIP-SHA-256: `055206fb5f645be51c1ad7a934d22ef0ac51be3fc7b12c192b6181d7c8428f11`
- **Nicht geprüft:** echte Hostinger-Schreibaktion, visuelle Aculia-Override-Wirkung, `is_front_page`-/Publishing-Render-Scope, Browser und Cache.

## Installation / Abnahme

1. Bestehendes Hostinger-Backup sicherstellen.
2. Nur den bestehenden ANDY Journal Integrator **0.2.2 → 0.2.3** als Plugin-ZIP aktualisieren.
3. Unter **Werkzeuge → ANDY Integrator → Abschnitt 10** den Abgleich prüfen und ausdrücklich **nur für #1362** freigeben.
4. **Denselben Draft #1362** im Browser ansehen, Header/Sticky-Header/Logo und Footer gegen die Original-Home vergleichen. Bei unerwarteter Darstellung die 2D-Meta-Änderung im selben Abschnitt zurücknehmen.
5. Bei gesperrtem Audit oder Fehlermeldung keine forcierte Änderung: aktuellen Status erneut lesend erfassen.

**Folgeentscheidung:** Ist die Darstellung danach weiterhin abweichend, liegt die nächste Untersuchung bei Theme-seitigen `is_front_page`-/Template-Bedingungen bzw. dem nativen Publishing-Hook; daraus **kein weiterer Home-Klon**.
