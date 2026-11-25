# ANDY Journal – LIVE-RIGHT-NAV-RETIRE-01

**25.11.2026 · Nachkontrolle unmittelbar nach erstem öffentlichen Launch.**

## Nutzerentscheidung

Der rechts über das Hamburger-Symbol erreichbare **Home-Composer-Navigationsdrawer** wird auf der öffentlichen Journal-Home **nicht mehr benötigt**. Er enthält noch obsolete Links **A–Z** und **Sitemap**, obwohl diese bereits aus dem regulären Footer entfernt wurden. Staging soll unabhängig weiterentwickelt werden.

## Technischer Befund

Im Home-Composer-Quellstand 0.1.50 befinden sich die Navigation und die Links weiterhin in `assets/composer.js`: `hcSharedHeader()` rendert `[data-burger="1"]`; `hcSharedDrawer()` erzeugt `.hc-top-drawer` mitsamt A–Z / Sitemap. Der vorherige Footer-Fix betrifft **nicht** diesen Drawer. Suche (`[data-search="1"]`) und DE/EN-Sprache liegen daneben und müssen sichtbar bleiben.

## Sofortige, konfliktfreie Live-Korrektur

**Keine neue Pluginversion und kein ZIP-Überschreiben während der parallelen Guided-Preview-Entwicklung.** Stattdessen **nur auf Live** in WordPress `Design → Customizer → Zusätzliches CSS` folgendes CSS speichern:

```css
body .andy-hc .hc-topbar [data-burger="1"],
body .andy-hc .hc-top-drawer,
body .andy-hc .hc-top-shade {
  display: none !important;
}
```

Diese Änderung entfernt **visuell** das Hamburger-Symbol und verhindert die Nutzung des rechten Drawers, ohne Home-Composer-Einstellungen, Sprache, Suche oder Footer zu verändern. **Nicht auf Staging einfügen.** Die Navigationslinks bleiben als toter Quellcode im ausgelieferten JavaScript; das ist eine Zwischenlösung, keine vollständige inhaltliche Entfernung.

## Nächstes gebündeltes Code-Release

Bei der nächsten konsolidierten Home-Composer-Version `hcSharedHeader()` und `hcSharedDrawer()` an einer einzigen Stelle anpassen: auf Live den Hamburger-Button und den Drawer erst gar nicht rendern; keine A–Z-/Sitemap-Links mehr im öffentlichen HTML. Andere Websites, private Vorschauen und Staging-Möglichkeiten nicht blind mitentfernen. Vorher auf Staging testen und dann eine freigegebene Dateiversion nach Live übertragen, **kein Staging-DB-Push**.

## Abnahme

- Live Home DE/EN: kein rechter Hamburger und kein Drawer.
- Logo, Header, Suchbutton und Sprachwahl bleiben.
- Footer zeigt weiterhin das Arena-Impressum und nicht A–Z/Sitemap.
- Staging-Home unverändert. Live-Änderung sofort durch Entfernen des CSS rückbaubar.

Status: **CSS-Hotfix zum manuellen Einfügen bereitgestellt**, keine Remote-Installation oder Browserabnahme behauptet.