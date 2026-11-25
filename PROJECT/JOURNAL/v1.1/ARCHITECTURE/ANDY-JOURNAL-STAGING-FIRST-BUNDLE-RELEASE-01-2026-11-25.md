# ANDY Journal – STAGING-FIRST BUNDLE RELEASE 01

25.11.2026 – Fachlicher Nutzerimpuls, als Architekturvorschlag dokumentiert. Noch keine Implementierung.

## Neues Betriebsmodell

Der Nutzer möchte künftig längere Zeit ausschließlich auf **Staging** weiterentwickeln, ohne für jede Pluginänderung Live aktualisieren zu müssen. Die Unterschiede während dieser Arbeitsphase sind **gewollt**. Live bleibt auf dem zuletzt abgenommenen Stand, derzeit Home Composer 0.1.47 (vom Nutzer auf beiden Instanzen installiert).

Erst zu einem ausdrücklich gewählten Release-Termin wird **ein einziges ZIP mit allen eigenen ANDY-Plugins** aus Staging exportiert und auf Live eingespielt. Ziel für die Administration: **Staging: „ANDY Release exportieren“ → Datei herunterladen → Live: „ANDY Release importieren“ → Unterschiedsvorschau → Backup/Prüfung → bestätigtes Update**. Keine automatische Fern-Synchronisation.

## Technische Grenzen und Umsetzung

- Ein gewöhnlicher WordPress-Plugin-ZIP-Upload installiert/aktualisiert ein Plugin, nicht mehrere beliebige Plugin-Unterordner als Gesamtpaket. Für einen Ein-ZIP-Bundle-Import ist ein **einmalig installierter schlanker Release-Importer/Exporter** notwendig; alternativ ist ein manueller, vorsichtiger Server-Dateitransfer möglich, aber nicht die gewünschte Pippi-Bedienung.
- Enthalten sein dürfen nur eigene, inventarisierte ANDY-Plugins einschließlich abgestimmter projektinterner Abhängigkeiten. Externe Plugins, WordPress-Core, Theme, Medien, wp-config und Geheimnisse werden **nicht** automatisch übertragen.
- Export erzeugt Plugin-Liste, Versionsmanifest, SHA-256-Dateiprüfsummen und ein geschütztes Archiv. Import prüft Admin-Rechte, Nonce, Plugin-Slugs und ZIP-Pfade, PHP/WP-Kompatibilität und Abhängigkeiten, bietet Dry-Run und zwingend Live-Backup, übernimmt nur explizit erlaubte Pluginverzeichnisse; Rollback muss vorgesehen sein. Keine stillschweigenden Löschungen.
- **Plugin-Code-Synchronisation ist keine Daten-Synchronisation**: Home-Composer-Module, manuelle Artikel-IDs, Launch-Control-WHY, redaktionelle Einstellungen, Posts, Sprachen, Freigaben und Medien liegen in separaten WP-Datenbanken/Uploads. Dafür braucht es später einen **selektiven** Export/Import mit Vorher/Nachher-Vorschau und Mapping. Kein kompletter DB-Push und kein Hostinger-Publish-Staging.
- Öffentliche Coming-Soon-Inhalte bleiben an PRE-STAGING-01C2B (Permalinks, RGB, Suche, REST, Feeds, Sitemap, Medien, Cache, DE/EN) gebunden. Der Release-Importer erteilt **keine** Veröffentlichungsrechte.

## Nächste Schritte

1. Auf Staging weiterarbeiten, Live stabil lassen; **keine Pflicht zu jedem Zwischenversions-Update**.
2. Einmalige Bestandsaufnahme der eigenen ANDY-Plugins und Abhängigkeiten vor Festlegung der Bundle-Whitelist.
3. Die einfache Release-Export/Import-Funktion auf beiden Installationen unabhängig von den fortlaufenden Home-Composer-Versionen einrichten und mit Testbundle und Rollback abnehmen.
4. Wenn redaktionelle Home-Einstellungen mitziehen sollen: gesondertes, selektives Konfigurationspaket als späteren Schritt definieren.

Status: Konzept und Entscheidungsvorschlag, **kein neuer Plugin-Build, kein Remote-Export/Import behauptet**.