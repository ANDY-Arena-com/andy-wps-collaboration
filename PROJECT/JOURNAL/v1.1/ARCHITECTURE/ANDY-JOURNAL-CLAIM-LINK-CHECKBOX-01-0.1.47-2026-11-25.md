# CLAIM-LINK-CHECKBOX-01 — Home Composer 0.1.47

**25.11.2026 · lokaler Staging-Release, nicht auf WordPress installiert. Live unverändert.**

**Befund (Nutzer-Screenshot):** Claims zeigen die drei Checkboxen für Dachzeile, Subclaim und Link fälschlich als breite weiße Horizontalbalken. Damit wirkt „Claim mit Link versehen“ verschwunden. Linkstil, Sprungziel, URL und CTA-Feld sind aber **bereits im Plugin vorhanden** und werden nur nach Aktivierung des Schalters eingeblendet.

**Ursache:** Generisches Admin-CSS für `.hc-editor-fields input` (100% Breite) und `.hc-editor-fields label` (Spaltenlayout) greift versehentlich auch bei Claim-Checkboxen.

**Fix:** Home Composer **0.1.47** erweitert 0.1.46 mit gezielten CSS-Regeln: Inline-Zeile und 18×18-px-Checkbox. Kein JavaScript-/Renderer-/PHP-Daten-Schema-Update; individuelle Claim-Farben, Linkziele und Staging↔Live bleiben erhalten.

**Lokal geprüft:** 40/40 gezielte Claim-Link-Tests; erneut 20 Claim-Farbtests, 19 Fight-Night-Tests + 5 Strukturassertions, 46 Resolver- und 26 Renderer-Tests, 23 isolierte PHP-Normalisierungstests; 6/6 PHP-Lints, JS-Syntax und ZIP-CRC. **Chromium-E2E nicht abgeschlossen; visueller Staging-Test ausstehend.**

**Paket:** `INSTALL-IN-WORDPRESS-ANDY-Home-Composer-0.1.47-CLAIM-LINK-CHECKBOX-01.zip`, SHA256 `3ce09448eb38d82caaf08300e4dbcc9dd3e5ae8371d9287a307cb32345f9c71b`. **Rollback:** `ROLLBACK-ANDY-Home-Composer-0.1.46-CLAIM-LINK-CHECKBOX-01.zip`, SHA256 `e9a0e7ca11bbacf275e74e4df3aa17f90ea7c5739f73254b4d07bca7d2933c1d`. ZIPs/ausführlicher Releasebericht im Chat, nicht in GitHub.

**Abnahme:** Ungespeicherte Admin-Änderungen vor Pluginwechsel bewusst speichern/verwerfen; Staging-Backup; nur auf Staging 0.1.47 installieren. Kleine Checkboxen, Link-Optionen, URL/CTA-Werte, DE/EN, individuelle Claim-Farben und Staging↔Live-Navigation prüfen. **Kein pauschaler Hostinger Publish**. Öffentliches 01C2B-Sicherheitsgate bleibt offen.
