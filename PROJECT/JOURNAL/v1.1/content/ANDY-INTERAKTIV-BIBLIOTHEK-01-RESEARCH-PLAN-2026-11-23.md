# ANDY Content Composer – Interaktive Bibliothek v0.1 / Research-Pilot

**Stand:** 23.11.2026, Konzept und technische Vorbereitung für den nächsten Content-Entwicklungsschritt.  
**Implementierungsstand:** **Noch nicht implementiert.** Aktueller quellgeprüfter Content Composer **0.1.2 (CONTENT-03)**. Home Composer bleibt eigenständiges Plugin und gehört dem Home-Thread; dessen aktuelle installierte Version bei jedem Release erneut prüfen (früherer Beleg 0.1.15).  
**Ziel:** Vom einmaligen Academy-L02-Import zu einer **wiederverwendbaren, versionierten WordPress-Bibliothek interaktiver Inhalte** für Academy, Research, Fight Night und weitere Inhaltstypen. **Keine zweite Homepage, keine zweite Bild-Mediathek, keine Duplikation des Game- oder Lab-Codes.**

## 1. Quellen und Grenzen

- Nutzer bestätigt am 23.11. funktionierende **Content-Templates** mit Testseiten `/das-ist-ein-test/` und `/andy-academy-l02-sechs-steine/`.
- Als nächstes Research-Beispiel ist die bestehende RGB-Seite `?andy_rgb_asset=research.html` genannt. Im **lokalen RGB-Pilot-discovery.json (Pluginpaket 0.6.3, Content-Register 0.6.0)** ist sie **Content** (keine Rubrik) mit Titel **„Wenn der Zug nicht zur Begründung passt.“**, unter `Entscheidungsverhalten` → `Research` → `Erforschen`. Registrierte Tags: `entscheidungen`, `validierung`, `schach`, `go`, `strategie`, `schluesselszenen`.
- Die **drei Hostinger-URLs ließen sich aus dieser Laufzeit nicht direkt als Seite abrufen**. Dass der Research-Artikel ein registrierter Inhalt ist, belegt das RGB-Register; **welche Interaktion auf der Live-Research-Seite tatsächlich läuft** und welche Engine/Daten/Skripte sie nutzt, ist **nicht verifiziert**. Es darf kein selbst erfundenes Research-Tool als „Originalmodul“ ausgegeben werden.
- Aktueller **Content Composer 0.1.2**, lokal quellgeprüft: `andy_cc_render_interactive($post_id)` lädt `_andy_cc_renderer`, `_andy_cc_renderer_version`, `_andy_cc_lesson_data` **am aktuellen Post**. Shortcode **`[andy_cc_interactive]` hat keine ID-Attributverarbeitung** und ist an `is_singular('post')` gebunden. Der Renderer-Vertrag ist der Filter `andy_cc_registered_renderers` mit `version`/`render`. Fehlender Renderer zeigt bewusst „nicht verbunden“. **Es gibt aktuell keine frei wählbare, mehrfach verwendbare Modulsammlung.**
- Aktueller **`ANDY_CC_Importer`** ist absichtlich **L02-spezifisch**: `schema=andy.content_package.v0.1-draft`, `kind=academy.lesson`, fixe Pfade u.a. `content/article-de.html` und `media/academy-l02.jpg`. **Nicht** aus einem neuen Research-ZIP als bereits akzeptiertes Dateiformat schließen.

## 2. Drei verschiedene Bibliotheken – klar getrennt

| Ebene | Eigentümer | Zweck | Gemeinsame Verwendung |
|---|---|---|---|
| **WordPress-Mediathek** | WP Core | Bilder, Cover, Logos, PDFs, sonstige Medien | über `attachment_id` referenziert |
| **ANDY Interaktive Bibliothek** (NEU) | Content Composer | Registrierte **Inhaltsinstanzen**: L02, konkrete Lab-Studie, Replay einer Match-ID usw. mit Titel, Kategorie, Vorschau, Renderer-Vertrag, Status, Datenversion | Ein Element in mehreren Artikeln / im selben Artikel mehrfach verwendbar |
| **Renderer-Registry** (geprüfter ausführbarer Code) | installierte spezialisierte Plugins bzw. freigegebene Adapter | Ein **Renderer-Typ** je Mechanik: Academy Player, Arena Replay, Lab Explorer; Version/Schemata/Assets/Runtime | Viele Inhaltseinträge können **denselben Renderer** verwenden |

**Nicht „für jeden Artikel ein neues Plugin“, nicht „alle Module als Dateien in einem ZIP ausführbar machen“.** Content-ZIP bleibt reines Daten-/Medienpaket; nur freigegebene installierte PHP/JS-Plugins können interaktive Mechanik liefern.

## 3. Vorgeschlagene Speicherung im Content Composer

- **WordPress Custom Post Type** `andy_interactive`, `public=false`, im Admin unter **Beiträge → ANDY Content Composer → Interaktive Bibliothek** sichtbar, zunächst ohne öffentliche Einzel-URL; mit WordPress-REST-Editoransicht für Gutenberg-Auswahl.
- Jeder Datensatz hat eine stabile `interactive_id` (z.B. `andy.academy.l02`, `andy.research.decision-001`), eine **numerische WP-ID** und `renderer_key` (z.B. `andy.academy.lesson`, `andy.lab.explorer`, `andy.arena.replay`). Diese IDs **nicht verwechseln**.
- Verwendete Metafelder (vorläufig): `_andy_ic_content_id`, `_andy_ic_kind`, `_andy_ic_renderer_key`, `_andy_ic_renderer_version_range`, `_andy_ic_schema`, `_andy_ic_payload` bzw. kontrollierte Payload-Referenz, `_andy_ic_source_rgb`, `_andy_ic_source_game_id`, `_andy_ic_package_sha256`, `_andy_ic_package_version`, `_andy_ic_review_status`, `_andy_ic_primary_attachment_id`, `_andy_ic_editorial_locale`.
- Redaktioneller Status **importiert / Renderer fehlt / prüfbereit / freigegeben / archiviert**. *Nur freigegebene Inhalte mit verifiziertem Renderer* dürfen als interaktiv produktiv ausgegeben werden. Ein Beitrag kann als Entwurf weiter existieren, aber **keine funktionslose Fläche als vermeintlich spielbar** zeigen.
- Bild-/Video-/Coverdaten bleiben in **`wp_posts`/Attachments**, keine redundanten Binärdateien als Meta oder in Home-Optionen.
- Änderungen an einer Bibliotheksinstanz können mehreren verknüpften Beiträgen zugutekommen; zur Vermeidung redaktioneller Überraschungen **Version/Pins und Vorschau** für breaking data changes unterstützen.

## 4. Einbindung in den WordPress-Artikel (MVP)

**Editor-Ziel:**

```text
Beiträge → Neu → Seitentemplate „Research“
Artikel schreiben → Block „ANDY · Interaktiver Inhalt“
Bibliotheksfilter: Alle | Academy | Research | Replay
Eintrag „Zug und Begründung“ wählen
Darstellung: Standard | Breit | Vollbreit
Optional: Einleitung, Bild/Caption, Quellen-/Prüfstatus
Speichern → Vorschau → Freigabe
```

Für ein erstes Update ist ein **schlanker Shortcode/Block-Adapter** genug: vorgeschlagen **`[andy_interactive id="123"]`** (WordPress `andy_interactive` Post-ID). Später ein Gutenberg-Auswahlblock, der intern denselben sicheren Renderer verwendet.

**Wichtig:** Der neue Block ist **mehrfach in einem Beitrag verwendbar**, verweist auf ein **bereits registriertes Bibliothekselement**, unterstützt optionale lokale Layout-/Breitenvarianten, verändert aber weder zentrale Daten noch CSS des Originalplayers. Der alte **`[andy_cc_interactive]`** bleibt aus Gründen der Rückwärtskompatibilität in L02-Beiträgen bestehen, kann später intern auf die Bibliothek abgebildet werden. **Keine stille Migration** der Bestandsbeiträge.

### Verantwortungsgrenze beim Layout

- **Content-Template:** gesamte Artikelhierarchie (Header/Bild/Breadcrumb/H1/Text/Tags), Inhaltsbreite, Theme-Tokens und Modulabstände.
- **Interaktiver Block:** einbettender Rahmen, Breite, ggf. Vollbild/Resize/Prüfstatus/Caption.
- **Renderer:** Spiellogik, Arena-/Lab-Steuerung, Board-/Diagramm-Komponenten, eigene zugelassene Scripts/Styles. Kein globales CSS des Content Composers darf seine eigentlichen Steuerelemente überschreiben.
- Bei eingebetteten Legacy-Plugins mit kollidierendem CSS oder JS muss erst der **Originalrenderer-Vertrag** untersucht werden. Keine ungeprüfte Kopie fremder Inline-Skripte in den CMS-Post oder ein ungesicherter iframe als Standardlösung.

## 5. Sichere Importlogik / neue ZIP-Familie

Neues allgemeines passives **`andy.interactive_package.v0.1`** nur **nach** Review des aktuellen L02-Formats. Beispiel `research`:

```text
ANDY-RESEARCH-DECISION-001.zip
├── manifest.json               id, kind, schema, renderer + version contract, source
├── data/
│   └── interactive.json        typed data / configuration, keine ausführbaren Skripte
├── content/
│   └── article-de.html         redaktioneller Text, optionaler Beitrag-Entwurf
├── media/
│   ├── cover.webp
│   └── chart-preview.webp      optionale Medien, WordPress Attachments
├── evidence/
│   └── sources.json            Herkunft, Prüfbarkeit, Status
└── SHA256SUMS.txt
```

**Import-Gate:** capability+Nonce, ZIP-Größe/Dateizahl/dekomprimiertes Limit, Pfad-Whitelist, MIME- und Medientests, Dateihashes, erlaubte Tags im HTML, nur JSON/Medien/Plaintext, **keine PHP/JS-Ausführung aus importierten Daten**, explizite `kind`-/`schema`-/Renderer-Kompatibilität (nicht nur „Version größer gleich“), idempotente `content_id`+Version, Konfliktabfrage bei redaktionell bearbeiteten Daten, **Entwurfsstatus und Quarantäne**, Fehlerreport; vorab Backup gemäß [Release-/Import-Gate](../docs/ANDY-WORDPRESS-RELEASE-UND-IMPORT-GATE-v0.1-2026-11-23.md).

**Bestehender L02-Importer** bleibt in seiner Version erhalten, bis der generische Import mit echten Testpaketen bestanden und der alte Import unverändert regressionsgetestet ist. **Keine automatische erneute Erzeugung von Beiträgen oder Plugin-Dateien.**

## 6. Erster Research-Pilot: „Wenn der Zug nicht zur Begründung passt.“

**Belegbare redaktionelle Identität aus dem RGB-Pilot-Katalog:**

```text
RGB-Key       research.html
Titel         Wenn der Zug nicht zur Begründung passt.
Rubrik        Erforschen / Research / Entscheidungsverhalten
Typ           Content
Tags          Entscheidungen, Validierung, Schach, Go,
              Strategie, Schlüsselszenen
Original-URL  https://glad-whitesmoke-octopus-16.hostingersite.com/?andy_rgb_asset=research.html
```

**Konkreter Testablauf:**
1. Original-Research-Seite und gegebenenfalls originales **Research-Interaktionsplugin/Quellpaket** aus dem zuständigen Thread/Hostinger-Export **prüfen**; **Quelle, Datensatz, Engine und Modulzustand** identifizieren. Das RGB-Discovery-Register enthält Metadaten, **nicht** den ausführbaren Research-Renderer.
2. Beitrag als **normalen WordPress-Entwurf** erstellen, Template `Research` zuordnen, vorhandene redaktionelle Texte/Quellen/Bilder **unverändert** übernehmen. Keine Doppelexemplare des bestehenden veröffentlichten Materials erzeugen, ohne eine vorherige WP-Suche auf denselben Titel/Source-Key.
3. Zu diesem Beitrag einen Eintrag in der **Interaktiven Bibliothek** anlegen: z.B. `kind=research.explorer`, `source_rgb=research.html`, zunächst **„Renderer fehlt“**, falls Original-Modul nicht vorliegt.
4. Einen **Research-Interaktivblock** innerhalb des Artikeltexts platzieren. Bei verifiziertem Originalrenderer Anzeige des funktionalen Elements; sonst klarer Hinweis **und Link zur Originalquelle** (kein falsches Spielbrett/Diagramm).
5. Darstellung prüfen: Header-/Hero-Standard, Inhaltsbreite, Theme-Vererbung, responsive Darstellung, kein Ausfall beim deaktivierten Renderer. Zwei unabhängige Instanzen in einem Beitrag testweise möglich.
6. Umgekehrten Weg prüfen: Ein und dasselbe Bibliothekselement **ohne erneuten Datenimport** in einem zweiten Entwurf referenzieren.

### Mindestabnahme für einen ersten technischen Library-Release

- **Ein** Bibliothekseintrag mit Quelle/Prüfstatus sichtbar in WP-Admin.
- **Ein** bestehender Academy-L02-Beitrag bleibt nach Update unverändert.
- **Ein** Research-Beitragsentwurf nimmt den Bibliothekseintrag auf.
- Bibliothekseintrag in **zwei** Entwürfen einsetzbar, zentrale Änderungen sichtbar, keine Kopie der Daten.
- Unbekannter oder nicht kompatibler Renderer zeigt **sauberen Status**, niemals eine leere Bühne.
- Bestehende Homepage, Home Composer, RGB-Originalroute, Standard-WP-Beiträge bleiben unverändert.
- Kein Import exekutierbaren Codes; keine versehentliche Live-Publikation.

## 7. Entwicklungsschritte und Ownership (kein zweiter Website-Builder)

**A – Bibliotheksunterbau im vorhandenen Content Composer:** CPT `andy_interactive`, Admin-Liste/Filter/Status, manuelle Testregistrierung, `[andy_interactive id="..."]` oder gleichwertiger sicherer Adapter. **Nicht** in Home Composer einbauen. Keine Änderung der aktuellen Root-Router-Logik. Einsetzbar auch wenn noch keine interaktive Engine verfügbar ist (sichtbar als pending).

**B – Original-Renderer-Adapter prüfen:** Academy L02 und Research-Live-/Pluginquellen **quellprüfen**. Nur freigegebenen Mechaniken registrieren; Adapter möglichst kleine, versionierte Erweiterung innerhalb der Content-Schiene. Kein blindes Kopieren des alten Academy-/RGB-Dummys.

**C – Verallgemeinerter ZIP-Import:** Weitere Arten (Academy/Research/Replay), wobei der bestehende L02-Import und seine ursprünglichen Sicherheitsgrenzen weiter funktionieren. Nicht jeder Dateityp braucht seinen eigenen Importer.

**D – Redaktioneller Komfort:** Gutenberg-Auswahlblock, Vorschau/Thumbnail, Einbettungsoptionen, öffentliche Freigabe-/Kompatibilitätsanzeige, spätere Home-Teaser aus freigegebenen WP-Inhalten.

**Explizite Trennung:** `andy-home-composer/*` und `andy_home_composer_*`-Optionen gehören dem Home-Thread. Content-Entwicklung auf Basis des **tatsächlich zuletzt installierten `andy-journal-content-composer`-Plugins**, zuletzt hier v0.1.2. Vor Release neues **Versions-/Installations-Gate**; keine alten Home-ZIPs installieren.

## Kurzfassung für den Folge-Thread

> Die **Interaktive Bibliothek** ist ein Katalog **wiederverwendbarer Inhaltsinstanzen**, nicht die WP-Mediathek und nicht ein weiterer Webseitenbauer. Content Composer v0.1.2 kann aktuell nur einen an den Post gebundenen `[andy_cc_interactive]`-Slot; der L02-Importer ist bewusst fixiert. Daher als nächstes einen **opt-in Custom Post Type `andy_interactive` plus referenzierbaren Einbettungsadapter** im bestehenden Content Composer entwickeln. Danach die **Original-Renderer** (Academy, Research, Replay) anhand ihres echten Codes einbinden und erst anschließend den passiven ZIP-Import verallgemeinern. Research-Pilot = bestehende RGB-Contentseite `research.html`, **„Wenn der Zug nicht zur Begründung passt.“**. Keine Änderung am Home Composer, keine ungeprüften Interaktionen, keine automatischen Live-Veröffentlichungen.

**Entscheidungsstatus:** Architekturvorschlag dokumentiert. **Noch kein Update-ZIP und kein WordPress-Eingriff** aus diesem Dokument.
