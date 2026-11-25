# ANDY Journal – LAUNCH-PREVIEW-01 · Vergleich der aktuellen Home mit Coming Soon

**25.11.2026 · Home Composer 0.1.39 → 0.1.40 · installierbares, lokal geprüftes WordPress-Einzelplugin.**  
**Status:** Release-Candidate **nur im Chat ausgeliefert**, noch **nicht** auf `journal.andy-arena.com` installiert oder live abgenommen. **Keine öffentliche Veröffentlichungssteuerung.**

## Kontext

Die Projektleitung benötigt statt weiterer abstrakter Architekturmodelle zwei unmittelbar vergleichbare **Home-Ansichten**. Die gewöhnliche Home bleibt vollständig unverändert, daneben gibt es eine **read-only, admin-only Coming-Soon-Simulation** in DE und EN. Kein zweiter WordPress-Stand, keine zweite Homepage und kein zusätzlicher Pluginordner.

Fachliche Grundlagen: [WHY & Progressive Content Release](../content/ANDY-JOURNAL-WHY-PROGRESSIVE-CONTENT-RELEASE-01-2026-11-25.md), [Coming-Soon-Redaktionshandoff](../content/ANDY-COMING-SOON-CONTENTKONZEPT-HANDOFF-2026-11-25.md), [PRE-STAGING-Governance](ANDY-JOURNAL-PRE-STAGING-ADMIN-UND-LAUNCH-GOVERNANCE-2026-11-25.md), [Launch Control 0.2.0-Plan](ANDY-JOURNAL-PRE-STAGING-01C1-PUBLICATION-PLANNING-RELEASE-2026-11-25.md).

## Die drei URLs

| Ansicht | Adresse | Zugriff |
|---|---|---|
| **Aktuelle Home** | `https://journal.andy-arena.com/` | Wie zuvor öffentlich |
| **Coming Soon DE** | `https://journal.andy-arena.com/?andy_hc_launch_preview=1&lang=de` | Nur angemeldete Administratoren mit `manage_options` |
| **Coming Soon EN** | `https://journal.andy-arena.com/?andy_hc_launch_preview=1&lang=en` | Wie DE, eigene redaktionelle Sprachfassung |

Die Preview-Links werden zusätzlich im bestehenden **Home Composer** und im **Launch-Control-Backend** als anklickbare Buttons angezeigt. In der Preview gibt es eine Vergleichsleiste, um jederzeit zwischen aktueller Home, DE/EN-Vorschau und dem Editor zu wechseln.

**Wichtig:** Diese URLs sind nach Veröffentlichung dieses GitHub-Dokuments **noch nicht automatisch aktiv**; zuerst muss Home Composer 0.1.40 installiert werden.

## Implementierung

- Update **`andy-home-composer` 0.1.39 → 0.1.40**; DE/EN-Konfiguration, vorhandener Hero-Slider, Branding, globale Headerwerte, Modulpositionen und bestehende Optionen werden aus denselben vorhandenen WP-Daten gelesen.
- Die private Preview zieht DE/EN-Titel, Teaser, geplanten Zustand und ggf. die im bestehenden Launch Control ausgewählte WP-Bild-ID über `alc_pub_areas`, `alc_pub_teaser` und `alc_pub_mode` aus **Launch Control 0.2.0+**. Bei installiertem Launch Control **0.2.1** können außerdem die dort bereits gepflegten WHY-Modi und Kurz-/Langtexte eingeblendet werden. Fehlt 0.2.1, wird WHY ohne Fehler weggelassen; es entsteht keine zweite Quelle.
- Die bereits gespeicherte Home-Modulfolge bleibt gleich; in der **privaten Simulation** ersetzen gebrandete Teaser-/WHY-Flächen die bis zur Freigabe ungeeigneten Artikelkarten. Header und Hero verwenden den **unveränderten Composer-Renderer**. Dies ist eine **visuell prüfbare Content-Simulation**, keine Pixelidentitätsbehauptung für Spezialmodule; ihre Gestaltung wird anhand von echten Browser-Screenshots iteriert.
- Vorschau rendert **keine echten Artikel-/Draft-/Fight-/Academy-/Perspectives-Datasets** und öffnet keine neuen Contentziele; tatsächliche Inhaltslinks/CTAs sind in der Simulation deaktiviert. **Keine** WordPress-Post-/Option-Writes, keine Theme-/Elementor-Änderung, keine neue Inhaltsregistrierung und keine öffentlichen Preview-Routen.
- Preview greift auf `template_redirect` **Priorität −110**, vor RGB (−100) und öffentlicher Home (−90). Nur `GET/HEAD` auf Root, `lang=de|en`, exakt erlaubte Query-Schlüssel, anerkannte Production-/Staging-Umgebung und angemeldete `manage_options`-Berechtigung. Unbekannte Hosts, Anonyme, ungültige Sprachen und Pfade werden ohne Fallback **404**.
- `DONOTCACHEPAGE`, `Cache-Control: private, no-store`, `X-Robots-Tag: noindex,nofollow,noarchive`, `Referrer-Policy: no-referrer` sowie keine öffentlichen Sitemap-/REST-Einträge im Plugin. **LiteSpeed-/Hostinger-Caches müssen dennoch in realen Tests geprüft werden.** `noindex` ersetzt keine Berechtigungsprüfung.

## Code-Diff und lokaler Nachweis

**ZIP:** `INSTALL-IN-WORDPRESS-ANDY-Home-Composer-0.1.40-LAUNCH-PREVIEW-01.zip`  
**SHA-256:** `f53a0d11e30ef817afbf0d7c104ddaa02399fc8d2fb4f3977b54897392f4d361`  
**Rollback (unverändert aus dem tatsächlichen Nutzer-Quellpaket):** `ANDY-WP-PLUGIN-Home-Composer-v0.1.39-PRE-STAGING-01B.zip`  
**Rollback SHA-256:** `8847b0c5bd73021f4387f627b036ec7aaa2fd16edb9d9977650e2fba94d45d87`

Archive sind **nur im Chat verlinkt**, nicht als Binärdateien in GitHub gespeichert. 0.1.40 ist ein ZIP mit genau einem WordPress-Pluginordner `andy-home-composer/`; 33 Dateien, CRC und Plugin-Header geprüft.

**Diff gegenüber 0.1.39:** drei vorhandene Dateien verändert (Plugin-PHP, Composer-JS, readme.txt) und drei neue hinzugefügt (private Vorschau-PHP, CSS, Release-README); kein alter Pluginbestandteil entfernt.

**QA:** 23/23 isolierte PHP-Autorisierungs-/Datenvertragstests, 2/2 simulierte DE-/EN-HTML-Auslieferungen, PHP-Lint aller 5 Plugin-PHP-Dateien und Node-Syntaxcheck des Composer-JS bestanden. Ein Chromium-Headless-Screenshot-Lauf konnte in der lokalen Testumgebung nicht fertiggestellt werden: **Real-WordPress-Rendering, Responsive-Darstellung, LiteSpeed-Cache und Hostinger-Integration bleiben offene Abnahmen.**

## Installation / Abnahme

1. Vollständiges Production-Backup inklusive Datenbank, Uploads, Pluginstände, RGB-Options und Rollbacks. Vorher prüfen, ob Home Composer **0.1.39** installiert ist.
2. **Nur das 0.1.40-Einzelplugin-ZIP** über WordPress installieren und die vorhandene Version ersetzen.
3. Unter **ANDY Journal → Home Composer** bzw. **Launch Control** die drei direkten Links öffnen.
4. Als Administrator beide Preview-Sprachen mit der öffentlichen Home vergleichen: Logo/Header, Hero-Slider, Modulreihenfolge, Farben, Texte, optionale Bilder. Änderungen an Coming-Soon-Texten nach Neuladen müssen in der privaten Preview erscheinen, **ohne die öffentliche Home zu verändern**.
5. Im anonymen Browserfenster beide Preview-URLs öffnen: erwartete **404**. Die aktuelle öffentliche Home muss unverändert verfügbar sein. Cache/SEO/Header nachprüfen.
6. Erst nach positiver Nutzer-Rückmeldung visuelle Verbesserungen als nachgelagertes Inkrement; bei Fehler Home Composer 0.1.39 aus dem Original-Rollback wiederherstellen.

**Nicht enthalten:** öffentlicher Coming-Soon-Modus, direkte Artikelfreigabe, 01C2B-Routen-/REST-/Feed-/Sitemap-/Cache-Autorisierung, Veröffentlichung erster Leseproben oder öffentliche System Map. **Diese Sicherheitsgates haben unverändert Vorrang vor einer öffentlichen Aktivierung.**

**Projekt-Gedächtnis / Making-of:** Die Projektleitung fordert ein **visuell überprüfbares Doppelbild**, bevor abstrakte Freigabekonzepte weiterentwickelt werden. Das ist eine Lernkorrektur: Ein Konzept braucht eine erfahrbare, testbare Oberfläche; eine private Simulation ist jedoch keine Produktionsfreigabe.
