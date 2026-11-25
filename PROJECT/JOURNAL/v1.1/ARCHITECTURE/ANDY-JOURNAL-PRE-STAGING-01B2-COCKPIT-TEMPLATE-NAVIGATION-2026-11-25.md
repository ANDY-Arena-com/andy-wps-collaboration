# ANDY Journal · PRE-STAGING-01B2 – Template-Navigation im Cockpit

**25.11.2026 · Lokaler Installationskandidat, nicht auf Hostinger installiert · kein WP-/Browser-Abnahmetest.**

**Vorgeschichte:** [PRE-STAGING-01B](ANDY-JOURNAL-PRE-STAGING-01B-UMGEBUNGEN-UND-COCKPIT-RELEASE-2026-11-25.md) wurde mit Cockpit 0.2.1 installiert und durch die Nutzerin/den Nutzer im Admin bestätigt: 21/21 vorhandene Werkzeugzugänge verfügbar. Anschließend zeigten Screenshots fünf zusätzliche Top-Level-Template-Menüs: **Block Tmplt, Footer Tmplt, Header Tmplt, Slider Tmplt, Section Tmplt**. Die Projektleitung bestätigte eine sichere Bündelung im Cockpit unter **Home & Design**, nicht die Zusammenlegung oder Deaktivierung der zuständigen WpSection-/Theme-Komponenten.

## Implementierung

Gezieltes Update **`andy-journal-cockpit` 0.2.1 → 0.2.2**. Gleicher Pluginordner, keine neuen Pluginabhängigkeiten.

1. **Aculia / WpSection · Templates** als eine zusätzliche Karte unter **Home & Design**, mit direkten Links auf die tatsächlich von WordPress registrierten Template-Editoren.
2. **Dynamische Identifizierung** der fünf Menüeinträge aus dem WordPress-Menü: exakte sichtbare Bezeichnung, registrierter `post_type` und dessen `edit.php?post_type=…`-Pfad, valider `menu-posts-*`-ID. **Keine hartkodierten Slugs**, da der aktuelle WpSection-Code nicht im ANDY-Baseline-ZIP liegt.
3. **Separater, explizit zu bestätigender Opt-in-Schalter** `andy_jc_compact_template_nav_v022`, standardmäßig ausgeschaltet. Nach Erkennung **aller fünf** Menüeinträge blendet ein gezielter CSS-Selektor nur deren fünf ursprüngliche Sidebar-Links aus. **Keine** `remove_menu_page()`-Aufrufe auf Post-Type-Editoren: WordPress-Menüregistrierungen, Berechtigungen, Edit-URLs und CPTs bleiben unangetastet.
4. Bei fehlendem/einseitigem/doppeltem Menülabel oder geänderter CPT-Registrierung: **nichts ausblenden**. Vor Aktivierung im Cockpit werden die Erkennungsresultate angezeigt. Jederzeit wieder deaktivierbar.
5. Die bisherigen **21 Cockpit-Ziele**, der separate reversible Schalter für **neun redundante Werkzeuge-Links**, WordPress-Environment- und Host-Checks von 0.2.1 bleiben **unverändert**.

## Lokale Prüfung und Artefakte

- **13 gezielte PHP-Stubs/Assertions bestanden** (5/5 Erkennung; Link des registrierten CPT; Off-by-default; 5 valide CSS-Regeln; fremde/nicht-Administrator-Menüs unberührt; fehlende/duplizierte/falsche CPTs und ungültige IDs führen zu keinem Ausblenden). PHP-Syntax und ZIP-CRC bestanden. Bestehende 21 Tool-Registrierungen, Umgebungsprüfung und 9-Link-Kompaktfunktion aus 0.2.1 im Quellcodevergleich unverändert.
- **Installations-ZIP:** `INSTALL-IN-WORDPRESS-ANDY-Journal-Cockpit-0.2.2.zip`, SHA-256 `4eb6af2ceec3630f97c93a72231b670c17818b078084efe49200e352c9ddac62`.
- **Rollback-ZIP:** `ROLLBACK-ANDY-Journal-Cockpit-0.2.1.zip`, SHA-256 `288e1a959c64d95f98666921f645adabb06cab424d77a943eaeea12a9b946bdb`. Bytegleich mit dem einzeln erfolgreich bereitgestellten 0.2.1-Installationspaket.
- Beide ZIPs bestehen aus genau **einem WordPress-Pluginordner** `andy-journal-cockpit/` mit `andy-journal-cockpit.php` und `README.txt`; keine Transport-ZIPs zum WP-Upload verwenden. **Binärarchive nur im Chat geliefert, nicht im Git-Repository abgelegt.**

## Nächster Abnahmeschritt

1. Vollständiges Hostinger-Backup; **nur das 0.2.2-Einzel-ZIP** in WordPress hochladen und vorhandenes Cockpit ersetzen.
2. 21 bisherige Werkzeugzugänge und bestehenden 9-Link-Kompaktmodus auf unveränderte Funktion prüfen.
3. In **Home & Design** fünf Aculia/WpSection-Links öffnen. Cockpit muss **„5 von 5 Template-Menüs erkannt“** melden.
4. Nur dann auf Wunsch den **eigenen Template-Sidebar-Kompaktmodus** aktivieren und bestätigen; prüfen, dass Design, Plugins, Benutzer und die tatsächlichen Template-Editoren erhalten bleiben.
5. Bei Abweichungen Kompaktmodus ausschalten oder bytegleiches 0.2.1-ZIP wiederherstellen. Wenn 5/5 nicht erreicht wird, vor Eingriff die tatsächlichen WpSection-Menü-Slugs und -Registrierungen prüfen.

**Nicht behaupten:** Bereits erfolgte WP-Installation 0.2.2, WordPress-/Editor-E2E-Abnahme, Staging-Isolation, Contentveröffentlichung, Daten-/Plugin-Deaktivierung, Änderung am WpSection-Code oder Performanceverbesserung.

**Making-of-Bezug:** [MO12 – Vom Werkzeug-Wildwuchs zur Betriebszentrale](../content/ANDY-MAKING-OF-STORY-KATALOG-v0.1-2026-11-25.md#6-mo12--vom-werkzeug-wildwuchs-zur-betriebszentrale-25112026): Ein weiteres Beispiel, wie administrative Einfachheit durch **Links, reversible Zustände und Eigentumsgrenzen** entsteht, nicht durch neue parallele Funktionen.