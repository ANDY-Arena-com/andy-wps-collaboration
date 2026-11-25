# ANDY Journal – LIVE GUIDED PREVIEW SLIDESHOW 01

**25.11.2026 · Umsetzung für die bisherige LIVE-Home · Installierbares, isoliertes WordPress-Zusatzplugin 0.1.0.**  
**Status: lokal geprüft, noch nicht auf Hostinger/Live installiert oder vom Nutzer abgenommen.**

## Nutzerentscheidung

Während das Journal **nur auf Staging** weiterentwickelt wird, soll **Live unverändert bleiben**, mit **genau einer Ergänzung:** **Unter die aktuelle Home, unmittelbar vor den bestehenden Footer**, wird ein **Guided-Preview-Modul als Slideshow** eingeblendet. **Keine weiteren Coming-Soon-Seiten, Home-Umbauten oder öffentlichen Artikel-/WHY-Freigaben**. Der Home Composer bleibt **0.1.47** auf beiden Sites, keine neue Home-Composer-Version.

## Technische Umsetzung

Eigenständiges, rückbaubares WP-Plugin **`andy-guided-preview` v0.1.0**. Es enqueued eine kleine CSS- und JavaScript-Datei **nur** für die veröffentlichte Home-Composer-Root auf `journal.andy-arena.com`, wenn Home Composer Public Mode aktiv ist; nutzt dessen unveränderten JavaScript-Renderer und hängt die neue Section **direkt vor `.hc-site-footer`** ein. Keine Änderungen an Originaldateien oder Moduleinstellungen. Die Staging-Installation, private Coming-Soon-Vorschau, WP-Posts, Site-Footer, Elementor, Launch Control, Content Composer und RGB-Routen bleiben unberührt.

Slideshow-Stationen: **Fight Night, Research, Perspectives, Academy, Making of**. Inhalt: bewusst **öffentliche, allgemeine DE/EN-Einführungstexte**; **keine automatische Übernahme** von redaktionellen Staging-WHY-Plänen/Entwürfen. Je Slide eine einzeln einstellbare Akzentfarbe, responsive Darstellung mit eigenständigem neutralen navyfarbenem Stil; optional ein Bild aus einem **bereits öffentlich sichtbaren Home-Modul**, kein neuer Contentzugriff. Pfeile, Punkte, Tastatur, Touch-Swipe, zugängliche Beschriftungen; Autoplay standardmäßig **aus**, optional aktivierbar (6–20 s, bei reduzierter Bewegung deaktiviert). Sprungbutton nur, wenn ein passendes **bereits gerendertes Home-Modul** existiert. Texte, Farben und Modul-An/Aus unter **Werkzeuge → ANDY · Guided Preview** bearbeitbar. Deaktivieren des Zusatzplugins entfernt das Modul vollständig.

**Keine neuen Artikel, Links zu nicht freigegebenen Inhalten, Content-Kopien oder Datenmigrationen.** Dieser Code-Release ersetzt das PRE-STAGING-01C2B-Sicherheitsgate nicht. Das Plugin ist **absichtlich ein einzelnes Live-Addon**, kein neuer Versionssprung des Home Composers. Bei späterem ANDY-Bundle-Release nur über die Whitelist eigener ANDY-Plugins berücksichtigen.

## Reale lokale QA

- Haupt-PHP: **PHP-Lint OK**; eigenes JavaScript: **Node-Syntax OK**, ZIP-CRC/WordPress-Single-Plugin-Root OK, vier Dateien.
- **Headless Chromium mit synthetischer Nachbildung der Home-HTML-Struktur**: exakt fünf Slides, **Einfügeposition vor vorhandenem Footer**, bestehende Home-/Footer-DOM erhalten, Pfeilwechsel, Direktwahl per Punkt, DE-Desktop-/EN-Mobile-Darstellung ohne horizontales Overflow, keine JavaScript-Fehler, Nicht-Public-Modus ohne Injection. Eine **reale Hostinger-/WordPress-/Cache-Abnahme** fehlt und wird nicht behauptet.
- SHA-256 ZIP **`67590438fe1b6f8c671a12323242e52bb5be01f2690b37a9801671e4ac61e254`**.
- Installationsartefakt im Chat: `INSTALL-IN-WORDPRESS-ANDY-Guided-Preview-LIVE-0.1.0.zip`. WP-Admin **Plugins → Installieren → Plugin hochladen → Aktivieren**, vor Live-Update Backup.
- Test: `https://journal.andy-arena.com/` ganz nach unten scrollen; fünf Folien, DE/EN, responsive, Originalmodule/Links/Farben unverändert; dann `Werkzeuge → ANDY · Guided Preview` für Textänderungen.
- Rollback: **nur dieses Zusatzplugin deaktivieren**, keine Rücksetzung von Home Composer oder WP-Daten.

**Offen:** WP-Live-Installation und Abnahme durch den Nutzer. **Staging-Entwicklung bleibt unabhängig und darf zwischen Releases weiterlaufen.**
