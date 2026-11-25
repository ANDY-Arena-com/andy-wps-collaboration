# ANDY Journal – MOBILE-HERO-IMAGE-01 · Hero-Bild auf Smartphones

**25.11.2026 · Nutzerbefund: Footer passt, Hero-Bild trotz 0.1.49 noch XXL.**  
**Status:** Lokaler CSS-Fix mit Test und WordPress-ZIP als **Merge-Kandidat**, nicht als auf Staging/Live installiert oder real abgenommen behauptet.

## Ursache

Home Composer 0.1.49 hatte den mobilen **Text-/CTA-/Abstandsteil** repariert, aber die Hero-Hintergrundbilder in `assets/composer.css` weiter mit **`background-size: cover`** versehen. Auf Smartphone-Hochformat wird ein breites Hero-Bild auf die Höhe der Bühne aufgezoomt und horizontal stark beschnitten. Der Nutzer sieht deshalb weiterhin ein übergroßes Motiv, obwohl der Text schon reagiert.

## Gezielter Fix

**Nur** am Ende von `andy-home-composer/assets/composer.css` ergänzen:

```css
/* MOBILE-HERO-IMAGE-01 */
@media (max-width:720px) {
  .andy-hc .hc-top-reference .hc-hero-slide .hc-top-hero-bg {
    background-size: 100% 100%, contain;
    background-repeat: no-repeat, no-repeat;
    background-position: center center, var(--hc-hero-pos-x,50%) var(--hc-hero-pos-y,50%);
  }
}
```

Das Background-Image hat **zwei Layer**: zuerst das bisherige Overlay/Gradient (**füllt** die gesamte Fläche), danach das Medienbibliotheksbild (**contain**, vollständig sichtbar statt Cover/Zoom). Mobile Bildposition, Farbe, Slide-Text und Farben bleiben erhalten, Desktop behält `cover`. Durch `contain` darf dunkel hinterlegter Freiraum um das Motiv auftreten. Kein neues CMS-Element, keine Backend-/DB-Änderung.

## Lieferung im Chat

- **Bevorzugt für parallelen Guided-Preview-Thread:** `ANDY-MOBILE-HERO-IMAGE-0150-CSS-ONLY.patch` SHA256 `32e1d4bee5ca567de444fd5c9e3167bf38a32f06cb03694ad80c576b0a5933ed`, reiner CSS-Hunk, 849 Byte.
- **Komplett-ZIP nur bei unveränderter Basis 0.1.49:** `INSTALL-IN-WORDPRESS-ANDY-Home-Composer-0.1.50-MOBILE-HERO-IMAGE-01.zip`, SHA256 `713251dd6b331e4ac109f8d218d35d31bb2e6dec1923d28a7f990db425bb186a`; Basis SHA256 `a44c75d991e3d5762b608057fba74a7eee5dfd22c81e5c075f806b3de46b464b`.
- `ANDY-MOBILE-HERO-IMAGE-01-HOME-COMPOSER-0.1.50-RELEASE-2026-11-25.md` mit QA und Testanweisung.

**Nicht unbesehen komplettes 0.1.50-ZIP über den in einem anderen Thread bereits geänderten Home Composer installieren.** Dort CSS-Hunk in den jeweils neuesten Quellstand mergen und ein einziges konsolidiertes Release bauen. Live/Staging mit bewusst identischem Code ausliefern, wenn beide die Bildkorrektur brauchen; kein DB-Push.

## Lokale Abnahme

**Chromium 18/18:** drei DE-Hero-Slides × 320/375/390/430/720/1024 px mit einer **realen 1600×700 JPEG-Datei** aus dem Plugin: bis 720px `100% 100%, contain`, bei 1024px unverändert `cover, cover`. Sliderbuttons, Footer-Arena-Link, kein horizontaler Overflow, keine JS-Fehler. PHP-Lint/JS-Syntax, ZIP-CRC OK. Diff zu 0.1.49: nur Composer-CSS als Funktionsänderung, Versionsheader und Readme plus 1 neue README, 42 alte Dateien bytegleich.

**Keine Prüfung der aktuellen Nutzerbilder auf Hostinger möglich; endgültiger visueller Vergleich DE/EN auf echtem Staging und Live sowie Cache-Invalidierung erforderlich.** PRE-STAGING-01C2B unverändert offen.