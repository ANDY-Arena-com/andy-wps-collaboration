# ANDY Content Composer – Parallele Entwicklung & Academy L02 Pilot v0.1

> **Installations- und Versions-Gate (23.11.2026):** Der Nutzer hat auf Hostinger **Home Composer 0.1.15 installiert**; ein Upload von 0.1.13 wäre ein unzulässiger Downgrade. Der Content-Thread darf **kein** Home-Composer-ZIP ausgeben oder installieren. Dieses L02-ZIP ist ein **Daten-/Content-Paket**, kein WP-Plugin; Import erst bei geprüftem Academy-/Content-Renderer und kompatibler Importfunktion. **Verbindliches Vorgehen:** [WordPress Release- und Import-Gate](../docs/ANDY-WORDPRESS-RELEASE-UND-IMPORT-GATE-v0.1-2026-11-23.md).

**Stand:** 23. November 2026  
**Typ:** Arbeitsvertrag + konkretes Content-Beispiel  
**Status:** Content-Prototyp/ZIP und visuelle Vorschau lokal erzeugt, **keine Hostinger-/WP-Installation und kein funktionsfähiger Academy-Player im Paket**.

## 1. Parallelarbeit ohne Seiteneffekte

| Eigentümer | Bearbeitet | Bearbeitet ausdrücklich NICHT |
|---|---|---|
| **Home-Thread** | vorhandener Pluginordner `andy-home-composer/*`, öffentliche Root-Homepage, Home-Module, Header, Rail/Fight-Night-Bühne, bestehende Options `andy_home_composer_*` | Academy-Datenpakete / artikelbezogene Templates / neue Content-Importlogik |
| **Content-Thread** | `PROJECT/JOURNAL/v1.1/content/*`, Content-Package-Schema, Musterartikel, Story-/Academy-Daten, Kategorie-Theme-Konzept, später **in separater abgenommener Datei** Content-Importer/Renderer-Adapter | Home-Composer-PHP/CSS/JS, Root-Router, bestehende Home-Options, native Elementor-Home #14 |
| **Gemeinsame Grenze** | WordPress-Post-ID / Story-ID, Attachment-ID, Tags, freigegebener Teaser, Theme-Token-Kontrakt | Kein zweiter Post-Store; keine stillen Updates der jeweils anderen Plugin-Dateien |

**Regeln:** Keine parallelen Änderungen an identischen GitHub-Pfaden, WordPress-Options oder Pluginordnern. Content-Thread darf Daten-ZIPs und ein **separat versioniertes Content-Template** vorbereiten; kein Composer-Release durch diesen Thread. Home-Thread kann die neue Content-Schnittstelle erst **nach gemeinsamer Prüfung/Freigabe** verwenden. Versionen und Quellcode ausschließlich an konkreten ZIPs/Hostinger-Stand festmachen.

**Eingriffsfreier Handover:** Home benötigt künftig nur `story_id/content_id`, `post_id`, `featured_image`, `short_teaser`, `tags`, `permalink` und ggf. `renderer_key`. **Kein Content-HTML in Home-Optionen kopieren.**

## 2. Erster Pilot: Academy L02

**Bestehende ID:** `l02` im RGB-Content-Register; Editorial-Demo-ID `D10`.  
**Historischer Titel:** „Wie kann ein Stein sechs gegnerische Steine schlagen?“  
**RGB-Route:** `?andy_rgb_asset=l02.html` (historisch; aktuell erreichbare URL und Modulstatus erneut prüfen).  
**Editorial-Motiv:** `andy-journal-editorial-v2/assets/img/academy-l02.jpg` (Original im lokalen Editorial-ZIP).  
**Bild-/Textreferenz:** Benutzer-Screenshots der bestehenden L02-RGB-Seite und des separaten interaktiven Academy-Moduls, inklusive Aufgabe `a1 setzen`, Anzeigeoption `Kontrollflächen aus`, Neustart, Mini-Quiz, Quelle-/Prüfstatus.

**Lokal erstellt:**
- `ANDY-ACADEMY-L02-CONTENT-PACKAGE-v0.1.zip` (10 geprüfte Dateien, kein ausführbares PHP/JS): `manifest.json`, `data/lesson.json`, `data/layout.json`, `data/theme.json`, `content/article-de.html`, `media/academy-l02.jpg`, `reference/academy-interaction-layout-reference.png`, `evidence/sources.json`, `README.md`, `SHA256SUMS.txt`.
- `ANDY-ACADEMY-L02-CONTENT-TEMPLATE-PREVIEW.html` (eigenständige **visuelle** Preview; Light/Dark-Umschaltung; **kein** reproduzierter Regeln-/Board-Renderer).

**Wichtig:** Diese beiden Dateien sind derzeit lokale Gesprächsartefakte, **nicht** automatisch Teil dieses GitHub-Commits. Originaldaten und der tatsächliche Academy-Plugin-Quellstand wurden noch **nicht** als aktuelle, verifizierte Eingabe vorgelegt. `renderer_key=andy.academy.lesson` ist **nur ein vorgeschlagener Adaptername**, kein nachgewiesener bestehender API-Key. Keine funktionsfähige L02-Board-Engine aus dem Screenshot ableiten.

## 3. Datenvertrag des ersten Pakets

```text
manifest.json                         sichere Paket-ID, Status=draft, Dateihashes, Renderer-unresolved
content/article-de.html               redaktionelle WP-Beitragskopie; nur erlaubtes HTML
data/lesson.json                      Aufgaben-/UI-Kontext aus Belegen; NICHT vollständige Spielmechanik
data/layout.json                      Hero → Artikelintro → interaktiver Slot → verwandte Inhalte
data/theme.json                       global → Kategorie-Theme → individuelle Override-Tokens
media/academy-l02.jpg                 vorhandenes originales L02-Editorialbild
reference/academy-interaction-layout-reference.png  nur UI-/QA-Referenz, nicht publizieren
evidence/sources.json                 Quellenlage, fehlende Renderer-/Board-Informationen
SHA256SUMS.txt                         Dateiintegrität
```

Die Daten stehen unter **`andy.content_package.v0.1-draft`**. Das ist **noch keine bereits installierte WordPress-Importschnittstelle** und muss mit dem vorhandenen Academy-Plugin (welches historisch schon ZIP-Import/Library/Block/Shortcode bot) abgeglichen werden. Wenn dessen ursprüngliches Format ausreichend ist, **adapterfähig bleiben**, statt es zu ersetzen.

## 4. WordPress-Zielablauf (als nächster Scope)

1. WP **Beiträge → Neu**, Template `Academy` wählen; Template bestimmt Standard-Modulreihenfolge, Kategorie `Academy` bleibt redaktionell unabhängig.
2. **Content-Paket importieren** oder vorhandene Academy-Lektion auswählen. Importer kontrolliert Berechtigung, Nonce, Größenlimits, sichere ZIP-Pfade, erlaubte Dateitypen, SHA-256 und Paket-/Renderer-Kompatibilität.
3. **DRAFT**-Post und Mediathek-Verknüpfung erstellen oder nach stabiler Paket-ID idempotent aktualisieren. **Keine ungefragten Überschreibungen bearbeiteter Texte**, keine öffentliche Auto-Publikation.
4. Bestehenden Academy-Player als registrierten Renderer in das interaktive Modul einsetzen; **kein iframe als Ersatz und keine eigenmächtige Neuprogrammierung der Originalinteraktion**.
5. Wenn Originalrenderer/Boarddaten fehlen: im Editor klaren Prüfstatus anzeigen und Veröffentlichung mit „interaktiv“ nicht freigeben; KEIN leeres transparentes Board auf der öffentlichen Seite.
6. Speichern / Vorschau / freigeben. Homepage fragt nur veröffentlichte Post-Teaserdaten ab und bleibt unabhängig vom Artikel-Layout.

**Version- und Theme-Vererbung:** globale Journal-Tokens → `academy-light` (Vorlagenstandard) → Beitrag-Overrides. Änderungen von Farben/Spacing wirken zentral; strukturelle Änderungen an vorhandenen Beiträgen erst nach Preview+Freigabe. **Das Original Academy Board Theme** bleibt Eigentum seines spezialisierten Players.

## 5. Abnahme & nächste erforderliche Quelle

Die bestehende GitHub-Architektur-Doku vom 15.11. beschreibt **ANDY Academy v0.1** als installierbares Plugin mit ZIP-Import, Demo Library, Gutenberg-Block und Shortcode; der Nutzer meldete damals einen erfolgreichen isolierten Praxistest. **Für einen echten Content-Import brauchen wir das ursprüngliche Academy-Plugin-ZIP/den Original-Renderer-Vertrag** plus den aktuell installierten Stand (falls noch vorhanden). Dessen genaue API-Version ist aus den hier vorliegenden Unterlagen nicht belegbar.

- [Historische Architektur und Academy-Plugin-Praxistest](../docs/ANDY-JOURNAL-PLUGIN-ARCHITEKTUR-v0.1.md)
- [Composer-/Content-Manager-Handover Stand 23.11.](../docs/ANDY-JOURNAL-CMS-UND-HOME-COMPOSER-HANDOVER-2026-11-23.md)
- [RGB-Inhaltsmapping `l02` / `D10`](../docs/ANDY-JOURNAL-INTEGRATOR-01-MAPPING-20261122.md)

**Resultat Pilot v0.1:** Konkreter vorhandener Academy-Inhalt und Bild in einem validierten ZIP samt Vorlage und Quellenstatus; WordPress-Import/echte interaktive Funktion **noch ausstehend**. Keine Änderung der laufenden öffentlichen Homepage und kein Konflikt mit dem Home-Thread.
