# ANDY Journal Integrator 2C – Header-/Slider-Abgleich (read-only)

**Stand:** 2026-11-22. **Pluginversion:** 0.2.2. **Status:** lokal gebaut und geprüft, Benutzerinstallation auf WordPress steht aus; keine Veröffentlichung.

## Ausgangspunkt
Die laufende Hostinger-Testinstallation enthält laut vorherigen Integrator-Live-Exports die Aculia-Home **#14** mit 37 Widgets, das HOME-01-WpSection-Sliderwidget **1eef5e6** mit drei gespeicherten Slides, den Home-Header **#26**, Global-Header **#532** und Footer **#455**. Zusätzlich ist ein mit Integrator 2B erzeugter privater Homepage-Entwurf visuell vom Benutzer geprüft worden. Die frühere Modulverwaltung (interne Revision 0.4.2) hat die Funktionspakete **DESIGN-01**, **HOME-01** sowie **CONTENT-01 / HOME-02** bereits zur Verfügung gestellt. Der Content Manager ist laut Inventur als 0.4.6 installiert. Ein erneuter Import dieser alten Pakete ist **nicht** vorgesehen.

Die vorangegangene [2C-Bestandsschutzanalyse](ANDY-JOURNAL-2C-HEADER-SLIDER-BESTANDSSCHUTZ-2026-11-22.md) identifizierte eine plausible, noch nicht bewiesene Ursache der Entwurfsabweichungen: Die 2B-Draft-Kopie übernimmt `_elementor_data` und einige Standardmetadaten, jedoch **nicht nachweislich** die Aculia-spezifische Header-Override-Konfiguration. Der vorherige HOME-02-Publishing-Hook könnte auf die Startseiten-ID **14** beschränkt sein.

## Neuer Stand: 2C-Diagnose in bestehendem Plugin

**Artefakt:** `ANDY-WP-PLUGIN-Integrator-v0.2C.zip`, ZIP SHA-256 `8d3631081b957c57c31a53b75e775cd6ce977b0c4b0793e611459c0f6380a65f`.

Es ist ein **Update des vorhandenen Ordners** `andy-journal-integrator` (**0.2.1 → 0.2.2**), kein weiteres paralleles WordPress-Plugin. Beibehaltung von 0.1-Inventur, 0.2A-Feldaudit und der ausdrücklich per Admin-POST ausführbaren 2B-Entwurfserstellung/-Rollbackfunktion.

Neu: **Werkzeuge → ANDY Integrator → Abschnitt 9**, Schaltfläche **„0.2C Header-/Slider-Audit als JSON herunterladen“**. Das Audit selbst ist **read-only** und erfasst ohne Frontend-Auslieferung:

1. WordPress `show_on_front`, `page_on_front`, Originalseite **14**, die von 2B markierte Entwurfskopie (falls vorhanden) und aktuelle Seitentemplates.
2. Elementor-Hashes und drei gespeicherte Slider-Zeilen je Seite (Slide-Title, repeater ID, Attachment-ID und Feldvorhandensein; keine Medien- oder Ziel-URLs).
3. Header **26/532** und Footer **455**: Existenz, Template und Elementor-Fingerprint.
4. Nur ausgewählte mögliche Header-/Layoutzuordnungs-Metafelder mit Schlüsselnamen, Datentyp und Fingerprint. Vergleich Quelle vs. Entwurf ohne rohe Theme-Meta-Werte.
5. Begrenzte Strukturhinweise zu `theme_mods` und `aculia_options-mods`; credentialähnliche Namen ausgeschlossen.
6. Registrierte WordPress-Hooks mit PHP-Callback-Herkunft **andy-content-manager** im **Admin-Kontext** (funktionaler Name, Hook, Priorität und pluginrelativer Dateiname, keine absoluten Pfade).

**Interpretationsgrenze:** Ein Admin-Hook-Snapshot beweist **nicht**, welche Frontend-Hooks mit welchen `is_front_page`-/Seitentypbedingungen laufen; das tatsächlich gerenderte Header-Template, CSS-/OwlSlider-Verhalten und Root-/UTM-Cache-Konflikte können nur gesondert im Frontend überprüft werden. Aus leerem Hook-Inventar darf nicht auf fehlendes HOME-02 geschlossen werden.

## Sicherheitsregeln

- Auf exakte Testdomain begrenzt; `manage_options` + Nonce für Export.
- Keine neue DB-/WP-/Elementor-Schreibaktion aus 2C, kein neuer Router oder globaler Renderhook, keine Änderungen von Seite 14, Header 26/532, Footer 455 oder `page_on_front`.
- Keine alten Design-/Sliderpakete reimportieren; bestehender RGB-Pilot und Editorial-v2-Adminvorschau bleiben unverändert.
- Der JSON-Export kann interne IDs, redaktionelle Slide-Titel und Feldnamen enthalten. **Nicht öffentlich auf GitHub hochladen.** Der User kann ihn im Chat zur Auswertung bereitstellen; danach nur bereinigte Diagnose und Mapping publizieren.
- **0.2B** bleibt ein unveröffentlichter WP-Draft. Die vorhandene 2B-Kopier-/Papierkorbaktion bleibt nur auf ausdrücklichen Klick möglich.

## QA lokal, nicht Live

- `php -l` Hauptdatei, bisherige Klasse 02B und neue Klasse 02C: **bestanden**.
- **29 PHP-Assertions** mit simulierten Elementor-Settings und Theme-Metadaten: Quelle/Draft, fehlender Draft, drei Slides, Media-IDs, Metadifferenzen, registrierter andy-content-manager-Hook, keine absoluten Pfade/URL-/Credential-Werte, UI-Ausgabe: **bestanden**.
- ZIP-CRC/Einträge: **bestanden**, 8 Paketdateien. Legacy-02B-Klassen- und Assets byteidentisch zum vorherigen 2B-ZIP.
- Keine echte Hostinger-Installation, keine Browsersimulation des WordPress-Themes und kein realer Auslöser des 2B-Entwurfs in dieser Releaseprüfung.

## Anwendung & nächster Gate

1. In WP `ANDY-WP-PLUGIN-Integrator-v0.2C.zip` als Upgrade des Integrators 0.2.1 hochladen.
2. `Werkzeuge → ANDY Integrator → 9. Header / HOME-01 / HOME-02` öffnen, **nur JSON-Export** verwenden.
3. Den Bericht `ANDY-INTEGRATOR-02C-<datum>.json` im Chat hochladen.
4. Erst dann die effektiven Header-Override- und dynamischen Slider-Regeln verifizieren und die bestehende private 2B-Entwurfskopie in einem separat abgenommenen 2D-Schritt vorlagentreu weiterentwickeln.

Die installierbare ZIP liegt als Chat-Artefakt vor; **kein Binär-ZIP und kein privater Live-Export** im öffentlichen Repository.
