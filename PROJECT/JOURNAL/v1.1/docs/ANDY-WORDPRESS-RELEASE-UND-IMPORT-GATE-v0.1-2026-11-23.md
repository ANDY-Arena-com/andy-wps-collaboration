# ANDY Journal – Verbindliches Release-, Versions- und Import-Gate v0.1

**Erfasst am:** 23.11.2026  
**Verantwortungsgrenze:** Home-Thread = `andy-home-composer`; Content-Thread = Artikel/Templates/Content-ZIPs; WordPress-Betreiber = Installation/Freigabe.  
**Geltungsbereich:** Alle künftigen ANDY-Plugin-Updates, Content-Imports, Theme-/Template-Anpassungen und Übergaben zwischen Threads.  
**Status:** Vereinbartes Arbeitsverfahren / **kein** installierter Code und kein eigenständiges Plugin.

> **STOP-Fall 2026-11-23:** Die WordPress-Installationsmaske auf der Hostinger-Testseite zeigt **aktuell installierten Home Composer 0.1.15**, aber **hochgeladenes ZIP 0.1.13**. WordPress warnt ausdrücklich vor dem Einspielen einer **älteren** Version. **Nicht fortfahren, nicht überschreiben.** Dies ist der durch Nutzerscreenshot belegte Versionsstand **zum Aufnahmezeitpunkt**, kein Nachweis des Quellcodes von 0.1.15 und keine Aussage über künftige Versionen. Ein altes Handover/ZiP kann einen zwischenzeitlichen Release aus einem anderen Thread niemals ersetzen.

## 1. Erst identifizieren: Was ist die Datei?

**Jede ZIP-Datei bekommt vor irgendeinem Upload einen Typ:**

| Typ | Beispiele | Ziel / Vorgehen | Niemals |
|---|---|---|---|
| **WP-Plugin-Release** | `ANDY-WP-PLUGIN-Home-Composer-v0.1.15-...` | Plugins → hinzufügen/ersetzen, **nach Versions- und Kompatibilitätsgate** | Eine ältere Version aus einem anderen Thread ungeprüft hochladen |
| **Content-Paket** | `ANDY-ACADEMY-L02-CONTENT-PACKAGE-v0.1.zip` | Erst nach Vorliegen eines **kompatiblen, freigegebenen Content-Importers** über dessen Importfunktion | Als Plugin unter Plugins → Installieren hochladen |
| **Sicherung/Export** | Hostinger-Files/DB, Modulkonfiguration | Nur durch dokumentierten Restore-/Importweg | Als Plugin missdeuten |
| **Klickdummy / HTML-Vorschau** | `...PREVIEW.html` | Lokal im Browser öffnen | Mit Live-Homepage oder Composer-Release gleichsetzen |

**Paketname allein ist kein Beweis:** Vor Einspielen ZIP-Inhalt (`Plugin Name`, `Version`, Hauptdatei/Pluginordner, Manifest, Zweck, Quelle, SHA-256) prüfen. Ein `manifest.json` macht ein Archiv nicht automatisch zum installierbaren WP-Plugin.

## 2. Versions-Gate vor *jeder* Installation

### A. Ist-Stand aus WordPress erfassen

1. **WordPress → Plugins:** Pluginordner/Slug, **installierte Version**, aktiver/inaktiver Status, abhängige Plugins und MU-Plugins erfassen.
2. **Bei Composer:** Aktuelle `andy-home-composer`-Version beim zuständigen Home-Thread erfragen/aus dessen **aktuellen** Releaseartefakten überprüfen; Screenshot als Beobachtung, **Originalquelle/ZIP der installierten Version als Referenz** beschaffen.
3. **Konfiguration getrennt sichern:** WP-Optionen `andy_home_composer_config_v01`, `andy_home_composer_header_v01`, `andy_home_composer_public_v01`; verwendete Beiträge, Mediathek, Theme/Child-Theme und ggf. Router/RGB-Mode. Plugin-Version ≠ Options-Schema-Version ≠ Daten-/Content-Paket-Version.
4. **Reproduzierbares Manifest:** Zeitpunkt, Standort (Test/Live), WP/PHP-Version, Plugin-Slug, installiertes Versionslabel, zugehöriger ZIP-Hash, Schema-Version, Änderungsverantwortlicher, letzte erfolgreiche Abnahme. Ohne Original-Archiv: Hash **unbekannt** markieren, nicht erfinden.

### B. Soll-Stand des ZIPs prüfen

5. Plugin-Hauptdatei und Manifest lesen: Slug/Zielordner, exakte Version, Build-/Release-ID, zugrunde gelegte vorherige Version, Änderungsdateien, erwartete WordPress-/PHP-/Abhängigkeitsstände, etwaige Option-/DB-Migrationen.
6. **Abgleich:** Ist `installed_version` **größer** als `candidate_version` → **BLOCKIERT** (kein stiller Downgrade). Gleich → nur bei eindeutig dokumentiertem Neu-Build + Hash-/Änderungsprüfung; andernfalls **STOP**. Neuer → nur mit dokumentiertem Änderungsdiff, Backup, Migrations-/Rollbackplan und Abnahme. Wenn keine eindeutig vergleichbare Version vorhanden ist → **STOP**.
7. **Cross-Thread-Gate:** Ein anderer Thread darf keine neue Plugin-ZIP als „aktuelle Composer-Version“ ausgeben, solange er nicht den **jüngsten** Basisstand (Code, Optionen/Schema, Konfliktdateien) nachweislich eingelesen hat. **Kein Versionsnummern-Hochzählen ohne Merge des tatsächlichen Codes.**
8. **Dateikollisionen:** Keine gleichzeitigen Änderungen an `andy-home-composer/*`, Home-Routing, öffentlichen Root-Options oder gemeinsamen CMS-Tabellen. Übergebene Content-Daten sind **kein Anlass**, Home-Code zu überschreiben.

### C. Sichere Durchführung und Abnahme

9. Vor Änderung **DB + `wp-content/uploads/` + Plugin-Dateien** sichern und Wiederherstellung prüfen (nicht nur altes ZIP aufheben); bei sensiblen Daten keine öffentlichen GitHub-Uploads.
10. Ziel zuerst auf **Staging/Testseite**; bewusstes Freigabe-/Installationsereignis, keine heimliche Aktivierung. Danach WordPress-Admin und öffentliche Route prüfen, Cache leeren, Moduleinstellungen/Reihenfolge gegen Snapshot prüfen, Such-/Modal-/Bilder-/Responsive-/Linktests und kritischen Content prüfen.
11. **Abnahmebericht:** Installiert/abgebrochen, tatsächlich bestätigte Version und Zeitpunkt, getestete Features, Screenshots, neue/alte Daten-/Optionsversion, Rollback-Status. Dokumentation **erst danach** auf „live installiert“ setzen.
12. Bei Fehler: **Rollback aus gesichertem konsistentem Code+DB/Options-/Mediensnapshot**, nicht nur Plugin-ZIP zurückspielen (neuere Optionsmigrationen können inkompatibel sein).

## 3. Konkrete Blocker-Klassifikation

| Befund | Entscheidung |
|---|---|
| Installiert **0.1.15**, hochgeladen **0.1.13** | **STOP; Installation abbrechen.** Nicht überschreiben, nicht „trotzdem fortfahren“ |
| Neuer Home-Thread baut **0.1.16** auf nachgewiesener Basis **0.1.15**, Konfig-Diff / Test vorhanden | **Review → Backup → Staging-Abnahme → ggf. Freigabe** |
| Content-ZIP L02 v0.1 | **NICHT** über Plugins; warten auf/prüfen des existierenden kompatiblen Academy-/Content-Importers; zuerst Daten- und Renderer-Version abgleichen |
| „Plugin-Stand 0.1.13“ in älterer Doku, Admin zeigt 0.1.15 | **Dokument ist historisch**, nicht Release-Autorität; verlinkten Handover entsprechend kennzeichnen |
| Gleiches Plugin mit gleichem Versionslabel, aber anderem ZIP | **STOP** bis Hash, Herkunft, Diff und Freigabe geklärt |
| Version kompatibel, aber Options-/Renderer-/Content-Schema unbekannt | **STOP** bis Vertrag/Migrationsregel getestet |

## 4. Besitz- und Dateigrenzen zwischen Home und Content

**Home-Thread:** alleiniger Code-Owner von `wp-content/plugins/andy-home-composer/*` einschließlich Composer-PHP/CSS/JS, Root-Rendering, Header, Rail, Fight-Night-Bühne, Home-Admin, gespeicherten `andy_home_composer_*`-Optionen. **Lieferrelease muss auf neuestem tatsächlich vorliegenden Stand aufbauen.**

**Content-Thread:** erstellt WordPress-Beitrags-/Template-Designs, Content-Schema, ZIP-Manifeste, Academy-/Match-/Research-Inhalte und **Adapter-Spezifikation**; der bestehende Academy-Renderer muss durch Quellcode/Version verifiziert werden. Kein Anfassen des Home-Pluginordners. Für eine neue WP-Content-Adapter-Implementierung zunächst **separates Modul unter klar abgegrenztem Owner** und gemeinsame Schnittstelle prüfen; keine parallelen Änderungen an Root-Routing und Home-Options.

**Gemeinsamer Vertrag:** Nur freigegebene WordPress-Beiträge/Medien sowie dokumentierte IDs, Permalinks, Teaser, Kategorien, Tags, `renderer_key` und Theme-Tokens. Renderer-/Content-Schema müssen vor dem Import als **kompatibel** bestätigt sein. Keine „Version >=“ als alleiniger Beweis für Kompatibilität.

## 5. Release-Protokoll: bei jedem Build ausfüllen

```text
Projekt/Host:       ...
Artefakttyp:        plugin | content-package | backup | preview
Owner/Thread:       ...
Zielslug/-ordner:   ...
Installierte Version / Codequelle / ZIP-SHA: ...
Kandidaten-Version / ZIP-SHA: ...
Parent-Version/-Commit: ...
Options-/DB-Schema: ...
Renderer-/Content-Schema: ...
Geänderte Dateien & Risiken: ...
Backup-Referenz & Restore-Test: ...
Migrationsplan und Rückweg: ...
Abnahmetests: ...
ENTSCHEIDUNG: BLOCKED | REVIEW | APPROVED | INSTALLED | ROLLED_BACK
WP-Iststand nach Installation: ...
```

Das Gate endet erst mit einem **sichtbaren Ist-Abgleich nach der Installation**. Ein ZIP-Download, GitHub-Commit oder gelungenes lokales Browserpreview allein ist **keine Hostinger-Abnahme**.

## 6. Anschlussquellen

- [Operativer Handover vom 23.11. / Composer 0.1.13 **historisch**](ANDY-JOURNAL-CMS-UND-HOME-COMPOSER-HANDOVER-2026-11-23.md)
- [Content-/Home-Thread-Grenze und Academy-L02-Datenpaket](../content/ANDY-CONTENT-COMPOSER-PARALLEL-WORK-AND-ACADEMY-L02-PILOT-v0.1.md)
- [Journal-Systemübersicht](../STATUS.md)

**Sofortige Konsequenz:** Nutzer-Screenshot belegt am 23.11.2026 **Home Composer 0.1.15 in WordPress**, **0.1.13 wäre Downgrade**. **Kein** Composer-Update aus diesem Content-Thread. **Keine** Installation von Academy-L02-Content-ZIP als WordPress-Plugin. Sicher weiterarbeiten nur mit Versions-/Schemavertrag und klarer Eigentümerschaft.
