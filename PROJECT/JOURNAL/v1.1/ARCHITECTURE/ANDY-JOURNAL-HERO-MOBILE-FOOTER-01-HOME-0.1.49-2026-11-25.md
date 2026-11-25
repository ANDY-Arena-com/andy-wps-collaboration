# ANDY Journal – HERO-MOBILE-FOOTER-01 / Home Composer 0.1.49

**25.11.2026 · Lokal getesteter Merge-Kandidat auf Basis Home Composer 0.1.48; nicht auf WordPress/Hostinger installiert oder final abgenommen.**

## Nutzerauftrag und Klärung

1. Die vorhandenen **drei Hero-Teaser** müssen auf Mobiltelefonen gut lesbar und bedienbar sein, **auf Staging und Live gleichermaßen**.
2. Aus dem **Composer-Footer** sollen **Sitemap** und **A–Z** verschwinden. An ihre Stelle soll das Impressum der Haupt-ANDY-Arena.
3. Der Nutzer bestätigt: **Das Impressum ist ein Modal auf `www.andy-arena.com` und keine eigenständige URL**. Er hat den Inhalt im Technik-Thread bereitgestellt. Einen URL-Hash/Query-Parameter, der das Modal beim Seitenaufruf öffnet, gibt es nach jetzigem Kenntnisstand **nicht als geprüften Endpunkt**.
4. Parallel überarbeitet ein zweiter Thread die Guided Preview. Keine unbeabsichtigte Überschreibung dieser neuen Änderungen.

## Lokale Implementierung

- Auf Basis des vom Nutzer bereits installierten 0.1.48 ein **reiner CSS-Mobile-Hero-Patch** in `assets/composer.css`: responsive Typografie, umbruchsichere Headlines und Beschreibung, vertikale Buttons unter 480px, Touchgrößen/Abstände und Nav-Abstand bis 720px. Gespeicherte Texte, Farben, Slide-Reihenfolge und Transition-Logik **unverändert**, Desktop unverändert.
- In `assets/composer.js` **nur der generierte Journal-Composer-Footer**: ursprüngliche Sitemap- und A–Z-Anker werden durch **einen** DE/EN-beschrifteten Impressumslink auf die **originale Arena-Root-URL `https://www.andy-arena.com/`** ersetzt. **Wichtig: Der Link öffnet zunächst die Arena-Home, dort muss der Nutzer das Impressumsmodal anklicken.** Kein erfundener `#impressum`-Hash und keine unbestätigten `/de/`/`/en/`-Pfade. **Keine doppelte Impressumsdatenpflege** im Journal.
- Die **originale Aculia-Footer-Template-Instanz #455** und der separate `hc-top-drawer-footer` werden von diesem Patch **nicht** verändert. Die Haupt-Arena bleibt unangetastet.

## Lokale Testabdeckung

- Headless Chromium: **12/12 DE/EN + 320/375/390/430/720/1024px** Szenarien erfolgreich; in jedem Test **3 Hero-Slides** mit absichtlich langen Headlines/CTA-Labels (36 Hero-Zustände). Kein horizontales Overflow; CTA-/Headline-Container liegen innerhalb des Viewports; Foliensteuerung verwendbar; genau ein Arena-Footer-Link und kein Sitemap-/A–Z-Link dort; keine JS-Fehler. Screenshots wurden nach Abschluss der Slide-Animation erstellt.
- **6/6 PHP-Lint**, JavaScript-Syntax, ZIP-CRC erfolgreich. **Keine reale WordPress-Abnahme** mit den gespeicherten Live-/Staging-Inhalten. Ein bereits auf 0.1.48 bestehender schmaler Header-Navigationsabstand bei 320px wurde erkannt und **nicht** im Hero-Patch verändert (geschützter Header, gesondert abnehmen).
- Komplett-ZIP: `INSTALL-IN-WORDPRESS-ANDY-Home-Composer-0.1.49-HERO-MOBILE-FOOTER-01.zip` SHA-256 `a44c75d991e3d5762b608057fba74a7eee5dfd22c81e5c075f806b3de46b464b`.
- Quellcode-Patch **nur** für `assets/composer.css` und `assets/composer.js`: `ANDY-HOME-0149-MOBILE-HERO-FOOTER-CHANGES.patch` SHA-256 `f47954439f53a278ab3ba7ab9436c55eb9c3570dfe0103a920992d1e1d3c2b29`.
- Basis/Rollback: bestätigtes 0.1.48-ZIP SHA-256 `0522cb64aab6af3a91c61ce2459fb551e72529b0848587ec9d6306e2b2821770`. Vollständiger Releasebericht mit Testergebnissen im Chat.

## Verbindliche Release-Sicherheit

**Das Komplett-ZIP 0.1.49 nicht blind über einen neueren Guided-Preview-Stand des parallelen Threads installieren.** Für die gemeinsame Releasebasis nur die zwei Änderungen des Patchs **in die zuletzt vom anderen Thread gelieferte Home-Composer-Version mergen**, dann **eine** neue endgültige ZIP-Datei von Staging auf Live übertragen, jeweils mit Backup/visueller Prüfung. Keine komplette Staging-DB-Veröffentlichung, kein Verlust individueller Colors/Claims/Guided-Daten, keine neue Content-/WHY-Freigabe; PRE-STAGING-01C2B bleibt offen.

## Direktlink für das Arena-Impressum (später, optional)

Ein echter One-Click-Link aus dem Journal zum **Arena-Modal** setzt voraus, dass die Haupt-Arena selbst eine geprüfte URL-Konvention, etwa den Hash `#impressum` **zuerst implementiert**, auswertet und dort ihr vorhandenes Modal mit Fokus/Close-Handling öffnet. Erst **nachdem** diese Route auf der Haupt-Arena getestet ist, das Footer-Href darauf ändern. **Das ist keine Anweisung, die Haupt-Arena jetzt ungefragt umzubauen.**
