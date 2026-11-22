# ANDY Journal Integrator 0.2B – reale Aculia-Home als privater WordPress-Entwurf

**Stand:** 22.11.2026 · **Plugin:** ANDY Journal Integrator 0.2.1 · **Status:** Lokal fertig / WordPress-Installation, Browser- und Funktionstest offen. **Nicht veröffentlicht.**

## Quellen und Ausgangslage

- Originalinventur 0.1: [vollständige Matrix](ANDY-JOURNAL-INTEGRATOR-01-MAPPING-20261122.md), 28 RGB-Seiten, 14 Demos, 34 native Post-/Page-Einträge.
- Originalbericht `ANDY-INTEGRATOR-02A-20261122(1).json` des WordPress-Plugins 0.2.0, Erzeugung **2026-11-22 12:02:05**, private Staging-Instanz `glad-whitesmoke-octopus-16.hostingersite.com`.
- Aculia Homepage (konfigurierte WordPress-Frontpage): WP **ID 14**, `Home Page 01`, 37 Widgets; **0 neu / 0 entfernt / 0 Typ geändert** im Vergleich zu 0.1.
- Header **26** (1 Widget), Header **532** (1 Widget), Footer **455** (19 Widgets): jeweils ebenfalls ohne Widget-Drift. Diese Templates werden in 2B **nicht** verändert.
- Seitenhash des Elementor-Originals aus 2A: `66e95f8576b875ea86d0ff2643564c9f79a4154c996a64959ed369125c4f832f`. Nur der Hash, Widget-IDs und Version stehen im auslieferbaren 2B-Paket; **keine** rohe `_elementor_data`.
- WpSection-`wpsection_banner_slider` **1eef5e6**: 3 `repeat`-Slides, Felder `block_title`, `block_text`, `block_bgimg`, `block_btnlink`, `block_button`.
- `wpsection_service_tab` **87443e1**: 5 `repeat`-Einträge mit Text-/Bild-/Linkfeldern; im Audit überall Medien-ID 113 – Motivvielfalt **noch nicht** belegt.
- Vier `wpsection_service_block`-Widgets mit separaten Medien-IDs 109–112 und bearbeitbaren `title`, `text`, `btnlink`, `bttn`.
- Sechs Elementor-`icon-box`-Widgets mit `title_text`, `description_text`, `link`.
- `wpsection_vedio_image_box` enthält `image` und `vlink`, **nicht nachgewiesen kompatibel mit ANDY-Replay**.
- `wpsection_blog_grid` **ffe9286**: nur `bttn`, `column`, `thumb` erkennbar. Kein belegter Filter auf relevante ANDY-Journal-Posts; **nicht** blind umschreiben.
- Text-/Heading-Widgets ermöglichen zusätzliche redaktionelle Beschriftungen. Testimonials/sekundärer Slider bleiben vorerst unangetastet.

## Umsetzung: kein zusätzlicher Plugin-Ordner

`ANDY-WP-PLUGIN-Integrator-v0.2B.zip` ersetzt nur den bereits vorhandenen Plugin-Ordner `andy-journal-integrator`: Upgrade **0.2.0 → 0.2.1**. Das bisherige Inventory 0.1 und der Read-only-Feldaudit 0.2A samt Exporten bleiben vorhanden.

Neue Admin-Sektion **Werkzeuge → ANDY Integrator → 8. Home-Entwurf 0.2B**:

1. **Read-only Vorprüfung:** feste Host-Domain, tatsächliche WP-Frontpage-ID 14, Status `publish`, originaler `_elementor_data`-SHA-256 gegen Audit 2A, 20 feste Widget-IDs samt Typen, genaue Feldstruktur und Count `26`.
2. **Änderungsplan:** zeigt 26 geplante redaktionelle Inhalts-Slots. Keine Datenbankschreiboperation beim Aufruf.
3. **Expliziter Admin-POST mit Nonce:** erstellt **eine** zusätzliche WordPress-Seite mit `post_status=draft` (kein öffentliches Frontend, kein Startseitenwechsel). Kopiert Original-Elementor-JSON in neuer Seiten-ID und ändert darin nur ANDY-Text/Link-Felder. Verknüpft die Entwurfskopie intern mit Ursprung 14 und Source-Hash.
4. **Keine Dubletten:** vorhandene 02B-Kopie wird angezeigt statt erneut erstellt.
5. **Reversibler Rollback:** nur bei passender spezieller Marker-ID und `draft` kann per geschütztem POST genau dieser Entwurf in den Papierkorb verschoben werden. **Nie Seite 14.**

## Redaktions-/Widget-Mapping 2B

| Widget(s) | Zielinhalte | Editierte Daten |
|---|---|---|
| Hero-Slider 1eef5e6 | Match / Agentic-AI-Crossover / Begründungs-Fall | 3 Slides: Titel, Text, Button, RGB-Link |
| Tab-Widget 87443e1 | Match / 2 Schlüsselszenen / Academy L01 / Tools | 5 Tabs: Titel, Texte, Button, RGB-Link |
| Service-Cards 2620f9a, f66143a, fd3a66b, 054176c | Fight Night / Perspektive / Research / Academy | 4 Cards: Titel, Text, Button, RGB-Link |
| 6 Icon-Boxen | Academy L01–L03 / Tools / Dokumentation / Making of | 6 Teaser: Titel, Beschreibung, RGB-Link |
| 5 bestehende Headings und 3 Text-Editoren | ANDY-Rubriklabels und redaktionelle Intros | 8 reine Textstellen |

**Alle Medien und Bildreferenzen bleiben unverändert.** Globaler Header, Footer, vorhandenes CSS und Aculia-Template, Blog-Grid, Testimonials, Video-Bildbox, Original-RGB-Assets und alle anderen WordPress-Posts bleiben unverändert. Die verlinkten RGB-Routen sind eine **Referenz**, kein Live-Link-Test. Die Aculia-Demo-Medien und -Artikel im Entwurf sind **nicht redaktionell final**.

## Technische Prüfung

- `php -l` auf beiden PHP-Dateien: bestanden.
- 38 alte PHP-Stub-Regressionstests: bestanden.
- 19 zusätzliche 2B-/Safety-Tests mit aus dem realen 2A-Schema synthetisch aufgebauten Elementor-Feldern: bestanden. Dazu 26-Slot-Patchanzahl, Originaldaten-Unveränderlichkeit, Medien-Erhalt, alte Grid-Daten beibehalten, Hash-/Schema-Fail-Closed.
- ZIP-Dateistruktur/CRC: bestanden.
- ZIP SHA256: `0fced415ca2f185d6e6d7ac3cf8475f3bb433bcf64a196e44c98c6a3b4c75871`.
- **Kein** echter Live-WP-Schreib-/Vorschau-/Browser-Test oder verifizierter Replay-Renderer.

## Bedienung / Abnahme

1. Hosting-Backup prüfen.
2. Plugin-ZIP über WordPress als Update des **ANDY Journal Integrators 0.2.0** hochladen (nur diesen ersetzen).
3. **Werkzeuge → ANDY Integrator → Abschnitt 8** öffnen. Erst die Liste mit 26 Änderungen prüfen.
4. Per ausdrücklich ausgelöstem Button eine Aculia-Draftkopie erstellen.
5. Mit WordPress-Anmeldung auf **Entwurf ansehen** klicken; bei RGB-Routing-Problemen über **WordPress bearbeiten / Elementor** öffnen.
6. Entwurfs-ID, Screenshot und sichtbare Blocker zurückgeben. Erst **2C** passt Bildwelten, tatsächliche Replay-/Academy-Module, native ANDY-Artikellisten, Menü, Sitemap/A–Z und responsive Darstellungen an.

**Governance:** keine automatische Live-Auslieferung und keine Änderungen an öffentlicher ANDY Arena, aktiver Hostinger-Startseite oder Blog-Domain. Kein zweites paralleles Home-System durch das Plugin.
