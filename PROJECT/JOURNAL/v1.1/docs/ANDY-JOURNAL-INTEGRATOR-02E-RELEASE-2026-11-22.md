# ANDY Journal Integrator 2E – Preview-Plugin-Release 0.2.4

**Stand:** 22.11.2026. **Status:** lokal erstellt und geprüft, Hostinger-Installation und Browser-Abnahme offen. Kein Publish.

## Der konkrete Build

- **Paket:** `ANDY-WP-PLUGIN-Integrator-v0.2E.zip`; **SHA-256:** `a450c13034c32ac980532bb072717adb8a9b212b261bbeb167fae0286f6ed3db`; 12 ZIP-Dateien.
- **Upgrade:** bestehender WordPress-Pluginordner `andy-journal-integrator` von **0.2.3 → 0.2.4**. Die 2B-Draft-, 2C-Audit- und 2D-Header/Footer-Abgleichfunktionen bleiben erhalten. Alle unveränderten 2D-Dateien sind byte-identisch.
- **Weitere Chat-Artefakte:** `ANDY-DOC-Integrator-v0.2E.md`, `ANDY-JOURNAL-2E-CHECKLIST.md`, `ANDY-JOURNAL-2E-WIREFRAME.md` und das bildfreie `ANDY-JOURNAL-2E-WIREFRAME.html`. Keine Binärdateien oder lizenzierte Themes ins öffentliche Repository geladen.

## Funktionsumfang (ausschließlich zur Laufzeit)

Nur auf der exakt autorisierten Hostinger-Testdomain **in der authentifizierten Admin-Vorschau von Entwurf #1362**:
- Halbtransparenter Overlay-Header über vorhandenem Sliderbild; bestehendes Logo und Flaggen werden nicht ersetzt. Alte horizontale Menüpunkte werden nur visuell verborgen; Burger + rechtes Flyout mit Rubriklinks und separatem externen Arena-Link.
- Originaler Aculia-WpSection-Slider (`1eef5e6`) mit **drei gespeicherten Bildern/Slides** bleibt erhalten; ca. 20 % reduzierte Displayhöhe bei initialer Messung, Bild-„cover“, Pfeile am unteren Rand.
- Vier vorhandene Service-Karten (`2620f9a`, `f66143a`, `fd3a66b`, `054176c`) erhalten visuelle Gleichhöhe und Arena-ähnliche Karten-/Button-Attribute; ihre Inhalte und Links werden nicht überschrieben.
- Freistehender Claim unmittelbar **VOR** Fight Night, wortgleich: **“Every AI has a plan until it gets punched in the Andy-Arena”**; das originale Tab-Widget `87443e1` bleibt erhalten und wird optisch abgesetzt.
- Alle weiteren nativen Aculia-Sektionen, insbesondere Academy, Research, Testimonials und Blog-Grid, bleiben im Design und in ihrer bestehenden Reihenfolge unangetastet.
- Behind ANDY mit Making-of-Verweis unmittelbar vor dem vorhandenen Footer. Ergänzende Themen-/Sitemap-/A–Z-Links verweisen auf bereits registergestützte RGB-Routen. Keine neuen Beiträge, keine neue Tag-Datenbank, kein Fake-Player.

## Bestands- und Zugriffsschutz

Die neue 2E-Klasse ist durch Host-Gate, Administratorberechtigung, `is_preview()`, aktuelle Seiten-ID **1362**, Draft-Status, 2B-Marker, Quelle **#14** und exakte SHA-256 der beiden Elementor-JSONs aus dem 2C-Live-Export geschützt. Bei Abweichung **kein 2E-CSS/JS**. Sichtbare Ausnahme: Vorhandene 2B-/2D-Admin-Schreibaktionen sind weiterhin separat, ausdrücklich nur per Admin-POST erreichbar; 2E selbst schreibt **keine** WP-Inhalte/Metadaten.

2E-Rückweg: gleicher WP-Preview-Link mit `andy_jint02e=off` oder Plugin deaktivieren. Kein neuer WP-Entwurf, keine Home-Umschaltung; Home **14**, Header **26/532**, Footer **455**, Content Manager, RGB und öffentliche Arena bleiben unverändert.

## Lokale Prüfung

- Alle fünf PHP-Dateien `php -l`: **PASS**.
- `node --check` für Vorschau-JS: **PASS**.
- **45** PHP-Stub-/Static-Safety-Checks und **13** positive Preview-Gate-Fixture-Checks: **PASS**.
- ZIP-CRC und Integrität, 12 Dateien: **PASS**, alle bestehenden 2D-Includes/Assets byte-identisch.
- Ein lokaler headless Chromium-Test lieferte **keine belastbare Darstellung** (Timeout): deshalb **keine** Behauptung vollständiger Theme-/Browserkompatibilität.

## Installation und Abnahme

1. Vorhandenes Hostinger-Backup sicherstellen.
2. Nur `ANDY-WP-PLUGIN-Integrator-v0.2E.zip` per **Plugins → Plugin hinzufügen → Plugin hochladen** über die vorhandene Integrator-Version 0.2.3 installieren; kein neues Plugin.
3. **Werkzeuge → ANDY Integrator → Abschnitt 11**: privaten Draft **mit 2E** und denselben Draft **ohne 2E** in zwei Tabs öffnen.
4. Screenshot-Review: Hero mit Burger und Flaggen, **alle drei Slides**; Vierer-Reihe + Tyson-Claim + echtes Tab-Widget; weiter unten Behind-ANDY/Footer mit Themen/Sitemap/A–Z. Desktop und Mobil.
5. Fehlende Theme-Selektoren erst aus den echten Screenshots adressieren. **Nicht** Originalseite 14 bearbeiten oder alte DESIGN-/HOME-ZIPs reinstallieren.

## Querverweise

- [Verbindliche Checkliste](ANDY-JOURNAL-INTEGRATOR-02E-CHECKLIST-2026-11-22.md)
- [Bildfreies One-Pager-Wireframe](ANDY-JOURNAL-INTEGRATOR-02E-WIREFRAME-2026-11-22.md)
- [2D Header- und Footerabgleich](ANDY-JOURNAL-INTEGRATOR-02D-DRAFT-HEADER-SYNC-2026-11-22.md)
