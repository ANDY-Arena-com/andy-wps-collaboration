# ANDY Journal – JOURNAL-IN-PLACE-PREVIEW-01

**25.11.2026 · Home Composer 0.1.42 → 0.1.43 · LOKAL GETESTET · Staging-first**  
**Status:** installierbares WordPress-Einzelplugin und geprüfter Rollback. **Noch nicht auf Hostinger installiert, kein Browser-/WordPress-End-to-End-Test und keine öffentliche Veröffentlichungsfreigabe.**

## Ausgangspunkt: ein echtes konzeptionelles Missverständnis

Die Projektleitung stellt beim Vergleich fest, dass die private Coming-Soon-Simulation **wie eine eigene Website mit anderer Struktur** wirkt – das war **nicht** das Ziel. Der Quellcode des vorherigen Previews ersetzte zwar die Inhalte in derselben Reihenfolge, erzeugte jedoch generische `.hc-launch-preview`-Sections und ein neues Überblicksraster anstelle der bestehenden Journal-Modularten.

**Verbindliche Korrektur:** **Eine Journal-Architektur, eine gespeicherte Home, dieselben Modulrenderer.** Beim Launch dominieren WHY und Coming-Soon-Erläuterungen, später wachsen diese Originalmodule durch freigegebene Artikel, Erlebnisse und Lab-Inhalte. Kein zwischenzeitliches Zweit-Layout, keine separate Coming-Soon-Website, kein Copy-Paste von Contentdaten. **Staging und Live sind zwei getrennte WP-Umgebungen**, nicht zwei gestalterische Journal-Versionen.

## Implementierung 0.1.43

Im bestehenden **Home Composer**:
- Die private Vorschau verwendet wieder die **regulären Renderer** für Claim, Highlights-Rail, Fight Night, Themenbühnen, Overview, Research-Rail, Academy, Perspectives, Making of und Suche. Originalmodule, Reihenfolge, Layoutklassen, Modulfarben, Header, Hero und bestehende DE/EN-Slides bleiben aus derselben gespeicherten Konfiguration.
- Die vorherige Umwandlung in `.hc-launch-preview`-Spezial-Sections wurde entfernt. Bereichs-Teaser und WHY werden in **vorhandene** Originalmodul-Container ergänzt, mit maximal einem voll ausgeführten WHY je Bereich; andere Stellen können als Leerzustand oder kleiner Platzhalter erscheinen.
- Weiterhin **keine echten Artikel-Datasets** in der privaten Vorschau und keine öffentlich gültige Leseprobenfreigabe. Bei Leerständen nicht anklickbare Karten statt erfundener Artikel. Academy-/Perspectives-**Struktur** kann aus der bereits bestehenden Themen-/Bereichsregistrierung kommen; öffentlichkeitsrelevante Artikel-URLs/Titel/Counts werden nicht in den Vorschau-Datensatz übernommen.
- Links zu Artikel-/externen Inhalten, Suche und CTA-Aktionen werden in der privaten Vorschau deaktiviert. Textinhalte gegen HTML-Injektion escaped. DE/EN-Sprachwechsellinks der privaten Vorschau bleiben erhalten.
- Die bestehende **GET/HEAD-, Login-/Admin-, Host-/Pfad-, 404-, Private-No-Store- und Noindex-Sicherung** der Vorschau bleibt unverändert. Noindex ist dabei nicht die Zugriffssperre; die Berechtigungsprüfung bleibt erforderlich.
- Die **funktionierende Staging↔Live-Adminnavigation bleibt vollständig unverändert**; `environment-switch.php`, `multilingual-home.php` und `highlights.php` sind gegenüber 0.1.42 bytegleich. Keine Home-/Option-/WP-Post-/Theme-/Elementor-/RGB-Writes oder Veröffentlichungshooks neu.

**Technische Begrenzung:** Originale Modul-Renderer ohne bereits freigegebene Artikel können andere Höhen als fertig befüllte Module haben. Ein **pixelidentisches** Endbild wird nicht behauptet, die **Komponenten-/Designstruktur** ist aber dieselbe. Ein WordPress-Browserabgleich ist zwingend.

## Artefakte und lokale QA

| Artefakt | Hash / Status |
|---|---|
| `INSTALL-IN-WORDPRESS-ANDY-Home-Composer-0.1.43-JOURNAL-IN-PLACE-PREVIEW-01.zip` | SHA-256 `219eaa1625cf581d4c372bd7410ee7234e9d1ab9f40e9baf4409ff9aa8ac6e53` |
| `INSTALL-IN-WORDPRESS-ANDY-Home-Composer-0.1.42-STAGING-HOST-GUARD-01.zip` | **unverändertes vorheriges Release, sofortiger Plugin-Rollback** |
| `ANDY-JOURNAL-IN-PLACE-PREVIEW-01-HOME-COMPOSER-0.1.43-RELEASE-2026-11-25.md` | Lokaler detaillierter Prüfbericht im Chat |

- **61/61 JS-Contract-Assertions** bestanden, darunter **15/15 Original-Modulrenderer** mit Original-IDs, keine neuen Replacement-Sections, Escaping, vorhandene DE/EN-Struktur, maximal ein Haupt-WHY je Bereich und deaktivierte private Preview-Linkaktionen.
- **6/6 PHP-Dateien Lint OK**, Node-JavaScript-Syntax OK; Plugin-ZIP-CRC und Dateistruktur geprüft.
- **Bytevergleich zu 0.1.42:** 37 bisherige Dateien; **5 geändert, 1 neue README, keine entfernt, 32 unverändert**. Keine Änderungen am eigentlichen Staging-/Live-Environment-Guard.
- Chromium-Headless-Screenshot lokal nicht erfolgreich abgeschlossen. **Keine erfolgreiche visuelle E2E-Abnahme behaupten.**

## Abnahme (nur auf geschütztem Staging!)

1. Nach Staging-Backup **Home Composer 0.1.43 ausschließlich auf `staging.journal.andy-arena.com`** installieren; Live auf bestehender Version belassen.
2. Aktuelle Staging-Home `https://staging.journal.andy-arena.com/` mit der privaten Vorschau `https://staging.journal.andy-arena.com/?andy_hc_launch_preview=1&lang=de` und EN vergleichen. **Gleicher Header, Hero, Modularten/-reihenfolge, Farben und gestalterische Logik**; Unterschied: tatsächliche Artikel vs. interne WHAT/WHY-/Coming-Soon-Einordnung.
3. Bereiche Fight Night, Academy, Research, Perspectives, Making of – vorhandene Modulrahmen, nicht neue Seitenabschnitte – kontrollieren. Testweise DE/EN-Teaser in Launch Control ändern und ohne Live-Effekt im selben Modul neu laden.
4. Anonyme Preview-URL muss 404 liefern. **Normale Staging-Home** und **Staging↔Live-Navigation** müssen unverändert bleiben. Kein WP-Status-/Global-DB-/Hostinger-Publish.
5. Bei Abweichungen unverändertes **0.1.42-ZIP** als Rollback. Erst nach Nutzerabnahme Live-Installation erwägen.

## Weiterhin offene öffentliche Freigabegates

PRE-STAGING-01C2B: Inhalte, native Posts, Gabelseiten, Sprachpartner, Legacy RGB, REST, Suche, Feeds, Sitemaps, Medien und Cache müssen vor öffentlicher Coming-Soon-Leseprobe als einheitliche Autorisierungsprojektion gesichert sein. WHY und System Map sind separate redaktionelle und semantische Datenquellen – keine zweite HTML-Website.