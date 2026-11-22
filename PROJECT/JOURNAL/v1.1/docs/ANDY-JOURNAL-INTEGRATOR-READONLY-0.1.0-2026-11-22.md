# ANDY Journal Integrator — Read-only Inventur 0.1.0

**Stand:** 22.11.2026 · **Status:** lokal erstellt und geprüft; reale Installation, WP-Laufzeit- und Browser-Abnahme offen. **Kein Deployment, keine Freigabe.**

## Zweck

Erster technischer Schritt des [Aculia/RGB-Konvergenzplans](ANDY-JOURNAL-ACULIA-RGB-KONVERGENZPLAN-v0.1.md). Erfasst die bestehende Aculia-/Elementor-Homepage, die native WP-Beitragslage und die 28 RGB-Bestandsseiten als Mappingkandidaten zur neuen Editorial Sitemap v2. Eine zweite öffentliche Homepage oder neue Content-Datenbank wird **nicht** angelegt. Der bereits vorhandene Content Manager, Launch Control, RGB Pilot und Editorial Sitemap v2 bleiben unverändert.

Da der tatsächlich laufende Quellcode des Content Managers 0.4.6 hier nicht als überprüfbare ZIP vorliegt, ist 0.1.0 ein eigenständiges **lesendes Companion-Plugin** anstelle eines unkontrollierten Updates des bestehenden Plugins. Spätere Integration in den Content Manager erst nach Prüfung der echten WordPress-Codebasis.

## Enthalten

- Nur auf der explizit vorgesehenen privaten Journal-Testinstanz aktivierbare Adminansicht **Werkzeuge → ANDY Integrator**; Zugriff `manage_options`.
- Native WordPress-`post`/`page`-Metadaten; keine Artikelvolltexte.
- Systemstatus: WordPress-Startseitenmodus/-ID; aktive ANDY-Plugin-Versionsnummern.
- Elementor-Widget-Inventar aus `_elementor_data` der tatsächlich konfigurierten statischen Startseite sowie historischen Aculia-Objekt-IDs 14/26/532/455. Historische IDs sind Hinweise, keine sicheren Schreibziele.
- Register: **28 RGB-Seiten / 14 Editorial-Demos**, fünf Content-Familien, Kanonische RGB-Routen als Verweise.
- Titelbasierte native Matchingkandidaten; keinerlei automatische Gleichsetzung, Migration oder Doppelimport.
- Getrennte In-Content-/Teaser-Bildwelt-Metadaten und geplante Aculia-Home-Modulrollen (Slider, Services/Fight Night, Research, Perspektive, Academy, Tools).
- Adminseitige JSON-Inventur und CSV-Mappingexporte mit Capability + Nonce; keine Roh-Elementor-Daten, Credentials oder geheimen Einstellungen.

## Bestandsschutz

Keine Veränderung der WordPress-Optionen, Beiträge, Menüs, Theme-/Elementor-Daten, RGB-Inhalte, Startseiten-Routen oder Cache-Einstellungen. Keine Frontend-Hooks, keine Aktivierungsmigration, keine Autodeaktivierung anderer Plugins. Die Ausgabedifferenz zwischen `/` und `/?utm_source=chatgpt.com` bleibt ein separates Diagnose-Thema; keine unbelegte Ursachenzuschreibung.

## Erzeugte Artefakte (nur Chat, nicht GitHub-Binärarchiv)

- `ANDY-WP-PLUGIN-Integrator-v0.1.0.zip` — ZIP-CRC erfolgreich, **SHA-256:** `cde29c6aedd740048d9eeeb2d4f1d65db2c9fbacc71caaf5e4b5d60abd32ff00`
- `ANDY-DOC-Integrator-v0.1.0.md` — Installation, Scope, Grenzen und nächster Schritt

## Lokale technische Prüfung

- PHP-Syntaxcheck (`php -l`) bestanden.
- **20 PHP-Stub-Assertions** bestanden: 28 eindeutige Seiten, 14 Demos, Matching-Report, Startseitenmetadaten, aktive Pluginstände, Elementor-Widgettypen, Admin-Rendering, keine Schreib-/Frontend-Hooks, Referenz-Reihenfolge.
- ZIP-Inhaltsstruktur/CRC bestanden.
- Kein Live-WP-Admin-Test, kein Hosting-/Cache-Test, keine Browserabnahme; tatsächliche Plugin-Interaktion und bestehende Elementor-Sonderformate noch offen.

## Nächster Schritt

1. Plugin ausschließlich auf der Journal-Testinstallation als Administrator installieren, unter **Werkzeuge → ANDY Integrator** öffnen.
2. **JSON-Inventur** herunterladen und intern prüfen; keine öffentliche Weitergabe.
3. Tatsächliche Startseiten-ID, Widgettypen/IDs und Titelkandidaten verifizieren.
4. Erst in **Integrator 0.2** eine private, reversible **Aculia-Home-Kopie** mit vorhandenen ANDY-Beispielen (Fight Night, Crossover/Research, Academy L01) umsetzen – nach Konfliktprüfung/Backup, ohne zweite öffentliche Home.

Keine Änderung an Arena oder öffentlicher Journal-Domain durch diesen Dokumentationsschritt.
