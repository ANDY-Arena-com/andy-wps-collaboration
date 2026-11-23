# ANDY JOURNAL – WordPress Content Manager, Home Composer & Plugin-Handover

> **HISTORISCHER HANDOVER, NICHT ALS UPDATE-ANLEITUNG VERWENDEN.** Am 23.11.2026 zeigt der WordPress-Installationsvergleich **installiert: Home Composer 0.1.15 / hochgeladen: 0.1.13**. Damit sind dieses Dokument und das darin genannte 0.1.13-ZIP **nicht mehr die aktuelle Installationsbasis**. **Downgrade abbrechen.** Vor jeder Änderung das [verbindliche Release- und Import-Gate](ANDY-WORDPRESS-RELEASE-UND-IMPORT-GATE-v0.1-2026-11-23.md) durchführen und den aktuellen Home-Thread-Release prüfen. Die technischen Informationen zu 0.1.13 bleiben als **Quellhistorie** erhalten; 0.1.15-Code wurde hier nicht geprüft.

**Stand:** 23.11.2026, abendlicher Übergabestand nach FIGHT-CMS-10  
**Kanonischer Arbeitsstand Home Composer:** `andy-home-composer` **v0.1.13**, `FIGHT-CMS-10`  
**Zweck:** Technische und operative **Übergabe an einen neuen Chat/Thread**, der ohne ursprünglichen Verlauf die vorhandenen Funktionen erhalten und die nächsten Änderungen *am selben Plugin* durchführen kann.  
**Belegbasis:** Die am 23.11. lokal vorliegenden **Plugin-ZIPs und der Quellcode** (insb. Composer 0.1.13, Content Manager 0.4.8, Cockpit 0.2.0, RGB 0.6.3), GitHub-Inventar/STATUS vom 22.11. und Nutzer-Screenshots/Rückmeldungen der öffentlichen Testsite. **Kein Zugriff auf das live installierte PHP/WordPress-Datenbank-Snapshot**. „Im ZIP vorhanden“ ist nicht automatisch „genau diese Version läuft auf Hostinger“.

> **Operative Leitentscheidung:** Es gibt **keinen zweiten Website-Builder**, keinen separaten Fight-Night-Shortcode und kein zusätzliches Demo-Plugin. Die öffentlich testbare Journal-Homepage entsteht aus den Modulen **im bestehenden ANDY Journal Home Composer**. Der **ANDY Content Manager** ist ein anderes, älteres Plugin für die **native Aculia/Elementor-Schicht**, nicht mit dem Home Composer gleichzusetzen. App/Arena, Analyzer und Journal bleiben technisch und redaktionell getrennt.

## 1. Schnellstart für einen Nachfolge-Thread

1. Aktuelles Quellartefakt **`ANDY-WP-PLUGIN-Home-Composer-v0.1.13-FIGHT-CMS-10.zip`** benutzen und seine enthaltene Plugin-Version/Header **0.1.13** kontrollieren. **Nicht** ein altes 0.1.x-ZIP oder den Einzel-Klickdummy als Ausgangspunkt nehmen.
2. **Niemals gespeicherte WordPress-Optionswerte durch neue Defaults ersetzen.** Die Modulkonfiguration einschließlich Reihenfolge/Farben liegt im CMS und **nicht im Plugin-ZIP**.
3. Vor jeder Änderung aktuellen Hostinger-Stand prüfen (aktive Plugin-/MU-/Theme-Versionen, Options-Snapshot, Medien/Posts); die ZIPs sind nur die zuletzt erzeugten Lieferstände.
4. In WordPress: **ANDY Journal → Home Composer**, ggf. **Werkzeuge → Home Composer**; Modul-Expander starten **geschlossen**. Separate Expander für öffentliche Testseite, Header/Top-Hero und Fight Night CMS-Demo.
5. **Öffentliche Testdomain:** `https://glad-whitesmoke-octopus-16.hostingersite.com/`; die **echte ANDY Arena** `www.andy-arena.com` ist getrennt und darf nicht verändert werden.
6. **Nächster Patch (noch nicht erstellt):** leichtes Layoutspringen beim Wechsel zwischen ein-/zweizeiligen Match-Titeln; Hero-Bild-/Rahmenproportionen und Contain-Größen. Erst danach echte, freigegebene Match-Stories an die Fight-Night-Bühne anschließen.
7. Keine Daten-/Pluginbereinigung, keinen Integrator-Draft (#1362) zur neuen Live-Quelle machen. Den vorhandenen **Composer** verbessern, mit kleinem Regressionstest und reversibler Änderung.

## 2. Komponenten klar auseinanderhalten

| Ebene | Technischer Eigentümer | Zweck | Verhältnis zum aktuellen Composer |
|---|---|---|---|
| **Aculia / Elementor / WpSection** | Theme + WP | Ursprüngliche native Home **#14**, seitenbezogener Header **#26**, globaler Header **#532**, Footer **#455**, Slider-Widget **`1eef5e6`** | Bleibt als Rückweg erhalten; Composer schreibt **kein Elementor JSON** |
| **Content Manager** | `andy-content-manager` | Native Design-, Navigation-, Header-, HOME-01/02-, Publishing-, Inventory-, Content-Migrationsfunktionen | **Separates** Plugin und nativer Workflow; nicht die Modul-Engine der öffentlichen Composer-Home |
| **Home Composer** | `andy-home-composer` | Module sortieren/aktivieren, Layout, Header, Such-/Themenreihen, Fight Night, optionale öffentliche Teststartseite | **Aktuelle aktive Entwicklungsstrecke** |
| **RGB Content Pilot** | `andy-rgb-pilot` mit Content Release **0.6.0** | Versionierte statische Pilotseiten, darunter echte bestehende A–Z-/Sitemap-Funktionen und RGB-Artikel/Tags | Composer-Quellregister & RGB-Verlinkung; öffentliche Root-Freigabe **hängt** von RGB-Status ab |
| **Journal Cockpit** | `andy-journal-cockpit` | Navigation/Aggregator zu bereits vorhandenen Admin-Werkzeugen | Menüzugang; **kein zweiter Content-Store** |
| **Editorial Sitemap v2** | `andy-journal-editorial-v2` | Historische private Preview/Contentregister mit Bildern | Composer nutzt aus dessen Assetordner **Bilddateien per Pfad**; bitte nicht vor Asset-Audit entfernen |
| **Integrator** | `andy-journal-integrator` | Historische Inventur, Audits, Entwurf **#1362**, CSS/JS-Draft-Vorschau | **Nicht die aktuelle öffentliche Composer-Home**; ältere Abnahmeprobleme nicht zurückholen |
| **Launch Control** | `andy-launch-control` (früherer Live-Nachweis) | Soll/Ist, QA, Planung und Freigaben | Nicht mit Composer vermischen; ZIP hier nicht erneut geprüft |
| **Replay/Academy** | Historische separate Prototypen | Spezielle Replay- und Lerninteraktionen | Früherer erfolgreicher isolierter Test; **aktuell installierter Status unbekannt** |
| **WordPress CMS** | `posts`, `postmeta`, `attachments`, WP-Options | Redaktionelle Beiträge, Bilder, Logos, Composer-Speicher | Neue Fight-Night-Demo verwendet **reale WP-Entwürfe und echte Mediathek-Anhänge** |

**Wichtig:** Frühere Inventur sah **14 aktive Plugins plus 2 Must-Use-Plugins** auf der Testinstallation (22.11.); sie enthält nicht die vollständige aktuelle Hostinger-Liste. **Aktivstatus/Versionsstand heute pro Plugin noch verifizieren.** Keine Löschfreigabe.

## 3. Aktuell verfügbarer ZIP-Release-Stand (nicht mit Live-Installationsstand verwechseln)

| Plugin-Ordner | Jüngster hier quellgeprüfter Lieferstand | Rolle / Hinweis |
|---|---|---|
| `andy-home-composer` | **0.1.13** FIGHT-CMS-10 | **Arbeitsbasis**; aktuelle CMS-Fight-Night |
| `andy-content-manager` | **0.4.8** NAV-ALL-SIZES | Enthält auch die in 0.4.7 eingeführte native Aculia-Bridge |
| `andy-journal-cockpit` | **0.2.0** KONSOLIDIERUNG | Menü-/Tools-Konsolidierung; Statusschalter ggf. prüfen |
| `andy-rgb-pilot` | **0.6.3** ROUTING-FIX | Unterstützt Content Release 0.6.0, darf nicht mit Content-Paketversion verwechselt werden |
| `andy-journal-editorial-v2` | **0.1.0** | Private Editorial-Vorschau und Bildassets |
| `andy-journal-integrator` | **0.2.5** 2E-KORREKTUR | Historischer Draft/Audit, **nicht** Home Composer |
| `andy-launch-control` | historisch **0.1.0**, ZIP heute nicht vorliegend | Liveversion offen |

**Sicherungsrelevante Prüfsummen (SHA-256 des ZIP-Archivs):**

```text
Home-Composer 0.1.13    123269fbce56f65bf85c82c68031bebb865778e253194cd84ed1f5c8fb2bd05c
Home-Composer 0.1.12    854a410321bfd382f45220fce8d3d75a236371b70b9b2355c0ee05473040d4f8
Content-Manager 0.4.8  de40317a61d328c9ee9f196e34f968f4c8426c3655349c80b40a93709471ee7b
Content-Manager 0.4.7  6abeb2f6c8aa44d5ae33f29b56dd5949009b05b9f2aeb58d337b3f41057fcbeb
Content-Manager 0.4.6  ee31e73482d00393e4c742fbc3db61444e848baf7aff014665225db5765442d8
Cockpit 0.2.0          366f4ccf8969919c2821c3495fdae688a0ca750eec06e76bd1c2cf81b10ff8e4
RGB Pilot 0.6.3        ea5fbb37f1f02489dbf12fd3bf2a9372ebd041a53556437c845e7d1abab1e68a
Editorial v2 0.1.0    adfca4b0431fd4593cd46f6f7949407812c506c59823d90e84b39192c462e60a
Integrator 0.2.5       b8fffaa3e3cc966d408e648e598de17438713cb9de56c88a8a2dfd2f4dd9b859
```

Dies ist ein **lokales Artefaktregister**, keine Hostinger-Datei-/Versionsmessung. Ursprüngliche Pluginordner beibehalten: **Upload ersetzt Version im selben Verzeichnis**; nicht zwei Varianten parallel installieren.

## 4. Home Composer: genau acht Modultypen in v0.1.13

| `kind` | Funktion | Steuerbarkeit / Besonderheit |
|---|---|---|
| `overview` | **ANDY entdecken**: die drei E – Erleben, Erforschen, Erahnen | Beschriftungen, Ziele, drei Karten, eigene Farben |
| `rail` | **Horizontale Themenreihe** (Highlights, Fight Night, Perspectives, Research, Academy, Making of) | Titel/Intro, Quellen-/Tag-/Manualliste, Anzeigelimit, 2–6 sichtbare Desktopkarten, Breite/Höhe, Zentrierung, Pfeile oben/seitlich, Intro oben/links/rechts/keins, Tags/Bildtitel, Schatten, Farbfelder |
| `stage` | **Themenbühne**: breite Bild-/Textkomposition für einen Inhalt | Titel, Text, Link, Quelle; unabhängig von `fightnight` |
| `fightnight` | **Fight-Night-Erlebnisbühne** | Altmodus `fight_source=rgb`; neu **`fight_source=cms`** mit drei WP-Demo-Stories; Matchwechsel, Logos, Story-Modal, Theme/Farben, Hero ohne Textüberlagerung |
| `claim` | **Claim-/Zitat-/Trennflächenmodul** | Hauptclaim, optional Header-Claim und Subclaim, direkter Textlink/CTA/kein Link, Text-/Hintergrund-/Akzentfarben und Ausrichtung, gemeinsame Inhaltsbreite |
| `search` | **Suche / A–Z** als Modal und direkter Contentzugang | Greift auf vorhandenes RGB-Register zu; keine neue autonome Sitemap-Datenbank |
| `text` | **Text-/Storymodul** | Freier kurzer redaktioneller Bereich |
| `whitepaper` | **Hochkant-Scroller** für Publikationen | Bis 12 Einträge, Cover aus WP-Mediathek, PDF-/Artikel-URL, eigene Farben/Schatten/Intro; zunächst kein automatischer Whitepaper-Bestand |

**Die Module sind Instanzen dieser acht Typen, keine eigenständigen Plugins.** Neue Instanzen lassen sich an-/abschalten und mit Pfeilen sortieren; die Admin-Expander sind **bei jedem Öffnen geschlossen** (UI-Zustand, nicht persistent). Maximal **60** Module in der gespeicherten Konfiguration (Backend-Validierung).

### Standard-Reihenfolge vor dem CMS-Demo-Import (Defaultwerte im 0.1.13-Code)

1. `overview` – ANDY entdecken
2. `highlights` – Entdecke ANDY · Highlights (**rail**)
3. `claim-fight` – Tyson-Claim (**claim**)
4. `fight-stage` – ältere Fight-Night-Themenbühne (**stage**)
5. `fight` – Fight Night · Match Stories (**rail**)
6. `perspectives` – Andere Blickwinkel (**rail**)
7. `claim-research` – Aus dem nächsten Zug … (**claim**)
8. `research-stage` – Fragen, die aus Spielen entstehen (**stage**)
9. `research` – Research · Das ANDY Lab (**rail**)
10. `academy` – Academy · Selber entdecken (**rail**)
11. `making-of` – Making of ANDY (**rail**)
12. `search` – ANDY durchsuchen (**search**)

**Nicht gleichsetzen mit der live gespeicherten Reihenfolge!** Nutzer hat Module mehrfach verschoben, deaktiviert und Farbfelder verändert. **Gespeicherte WP-Option ist die Wahrheit**. Beim manuellen 0.1.13-Demo-Import wird `fightnight-cms-demo` vor `fight-stage` bzw. ersatzweise vor `fight`/nach `claim-fight` eingefügt; **nur `fight-stage` wird deaktiviert**, nicht gelöscht. Die übrigen Module bleiben unverändert. Der Import legt **nicht bei jeder Pluginaktualisierung** neue Inhalte an.

### Optionen / Storage (Quellcode 0.1.13)

| WordPress-Option | Bedeutung |
|---|---|
| `andy_home_composer_config_v01` | **Aktuelle Modulinstanzen + Reihenfolge + Farben + Quelle + `schema=2`** |
| `andy_home_composer_header_v01` | Header-/Hero-Bilder, echtes Journal-Logo, Header-Farbe/Transparenz/Sticky, Seitenrahmen/Max-Width, Sprachanzeige |
| `andy_home_composer_public_v01` | Öffentliches Ausliefern des Composers an der Testdomain Root **ein/aus** |
| `andy_home_composer_pre_fn013_backup` | Unveränderter Vorzustand vor erstmaligem Fight-Night-CMS-Import, nur wenn der Import neue Modulinstanz anlegt |

**Nicht überschreiben** mit `andy_cm_*`-Optionen aus Content Manager oder `andy_rgb_*`-Optionen des Piloten. Die Composer-Speicherung erfolgt per `admin-post.php`, mit Berechtigungs-/Nonce-Prüfung und Validierung.

## 5. Aktuelle Fight Night CMS-Demo 0.1.13 – genaue Vertragsgrenze

Der manuelle Button **„3 Demo-Artikel, Bilder und Fight Night im Composer anlegen“** legt (wiederholbar, soweit vorhandene Demo-Keys erhalten bleiben):

- **3 WordPress-Beiträge als `draft`**, Slugs `andy-fn-demo-astra-gemini`, `andy-fn-demo-claude-grok`, `andy-fn-demo-qwen-llama` (tatsächliche IDs werden **erst auf Hostinger** vergeben);
- **3 Bildmotive:** `match-arena-warm.jpg`, `match-armwrestle.jpg`, `match-finish.jpg`;
- **6 transparente PNG-Demo-Logo-Platzhalter:** `logo-openai.png`, `logo-gemini.png`, `logo-claude.png`, `logo-grok.png`, `logo-qwen.png`, `logo-meta.png`;
- eine neue `fightnight`-Instanz **`fightnight-cms-demo`** mit `fight_source=cms`, IDs der drei Beiträge und Theme `dark`, positioniert an der Fight-Night-Stelle.

Bilder landen in `wp-content/uploads`, nicht nur im Pluginordner. **Nicht** allein anhand des ZIP-Archivs auf vorhandene WordPress-Medien schließen. Der Code benutzt als Wiedererkennungsmerkmale **`_andy_hc_fn_demo_key`** (Beitrag) und **`_andy_hc_fn_demo_asset`** (Medien).

**Mapping WordPress → Fight-Night-Teaser:**

| CMS-Quelle | Darstellung |
|---|---|
| `post_title` | Großer Hook / Matchtitel |
| `post_excerpt` | Untertitel |
| `post_content` | Story-/Artikel-Modal in der öffentlichen Testansicht; nach Publikation eigenständiger WP-Beitrag |
| Featured Image / `_thumbnail_id` | Großes Bild, `object-fit: contain`; **kein zusätzlicher Text darüber** |
| `_andy_hc_fn_why` | **Warum ansehen?** |
| `_andy_hc_fn_left`, `_andy_hc_fn_right` | Modellnamen / VS-Zeile |
| `_andy_hc_fn_left_provider`, `_andy_hc_fn_right_provider` | Anbieter |
| `_andy_hc_fn_logo_left`, `_andy_hc_fn_logo_right` | PNG-/Medien-Logo in den Platzhaltern und Medienkarten |

Die Metabox **„ANDY Fight Night · Teaser-Daten“** erscheint für Beiträge mit dem Demo-Key; Titel, Auszug und Beitragsbild werden mit normalen WordPress-Mitteln gepflegt.

**Alle drei Begegnungen sind fiktive redaktionelle Bildstudien.** Ihre Namen/Bilder dürfen nicht als echte Matchbelege veröffentlicht werden; markierte Logo-PNGs sind **Demo-Platzhalter, keine freigegebenen Original-Logos**. Das Modalfenster gibt Entwurfstexte **bewusst auch auf der öffentlich erreichbaren Testdomain** aus. Entwürfe sind also **hier kein Vertraulichkeitsschutz** – nur hierfür vorgesehene Testtexte verwenden. Vollständige echte Match-Story-Erzeugung/ZIP-Import und Engine-Resultat-Verifikation sind **nicht implementiert**.

### Fight Night Darstellungslogik

- Split: links redaktioneller Text/VS/Reason/CTA, rechts **bildfüllende Fläche mit `contain`**, aber ohne Bildtext und ohne „Schlüsselszenen“-Schaltfläche.
- Unterhalb **Mediathek mit drei anklickbaren Matchkarten**, wechselnder Hauptinhalt; zwei Logos als Medien in Hero-VS und Karten.
- Themes: **dark / brown / pink / light / custom**. Individuell gespeichert: `fight_bg`, `fight_text`, `fight_accent`, `fight_panel`, `fight_muted`, `fight_border` sowie `fight_fit`/Bildposition. Farbvarianten sind **lokale Renderer-Stile**, keine globalen Theme-/Board-Settings.
- Alte `fight_source=rgb`-Instanzen bleiben im bisherigen Renderer nutzbar. `fight_source=cms` darf nur die ausgewählten realen WP-Posts lesen. **Keinen zweiten Content-Store bauen.**
- Im aktuellen Paket siehe `andy-home-composer.php`: `andy_hc_fn_demo_manifest`, `andy_hc_fn_import_demo`, `andy_hc_fn_demo_data`; in `assets/composer.js` der Fight-Night-CMS-Renderer; in `assets/composer.css` die `.hc-fn-*`-Regeln (insbes. Medien-/Kartengeometrie am CSS-Ende).

## 6. Header, maximale Breite, öffentliche Testseite

**Header/Top Hero** im eigenen Expander:

- WordPress-Mediathek: Journal-Logo, Header-Hintergrund, großes Hero-Bild; bitte tatsächliches **ANDY-Journal-Logo**, nicht das Aculia-Logo wählen;
- Farbe, Deckkraft, Overlay/Transparenz und **Sticky** (ab 0.1.12);
- Maximalbreite **960–1800 px**, Default 1440 px;
- Seitenlayout `fluid` (vollbreite Modulhintergründe), `box_below` (Header vollbreit, Seitenrahmen darunter), `box_all` (Header + Content gemeinsam gerahmt), Außenhintergrundfarbe, Seitenabstand;
- Sprachflagge DE/EN und optionale externe Sprachlinks. **Noch kein vollständiges mehrsprachiges Publishing**; ZH ist nur perspektivisch.

**Öffentliche Auslieferung:** WordPress-Option `andy_home_composer_public_v01` aktiv + **exakter Hostname** `glad-whitesmoke-octopus-16.hostingersite.com` + RGB Content **0.6.0 bereit** + RGB-Standardmodus **`content`**; nur `GET/HEAD` am Root `/` mit engen Marketing-Parametern. Composer-Einbindung via `template_redirect` Priorität **-90**; RGB-Pilot hat Priorität **-100** für registrierte `?andy_rgb_asset=...`-Routen. Diese Prioritäts-/Host-Kopplung ist eine **echte technische Abhängigkeit**. Es gibt einen separaten WP-Admin-Schalter zum Rückweg auf die native Aculia-Home.

**Weitere Verfügbarkeit:** Composer verwendet `andy_hc_nodes()` / `andy_hc_public_nodes()` für vorhandene RGB-Content-IDs und greift für bekannte Teaserbilder teilweise auf `WP_PLUGIN_DIR/andy-journal-editorial-v2/assets/img/` zu. **Editorial-v2-Pluginordner nicht löschen**, bevor die Bildquelle migriert ist. Search/Tag- und Sitemap-Verhalten aus RGB nicht blind nachbauen.

## 7. Der ältere ANDY Content Manager ist KEIN Home Composer

Jüngster **hier vorliegender** Content-Manager-Code: `andy-content-manager` **0.4.8** (0.4.7 native Bridge + 0.4.8 Navigation-Fix).

| Interne Datei / Funktion | Historisches Modul | Aufgabe |
|---|---|---|
| `andy-content-manager.php` | Inventory | Native WordPress-/Design-Baseline, Inventur, Export |
| `design-import.php` | DESIGN-01 | Pakete für Logo, Brand-/Site-Identity, Theme-Felder; Preview, Freigabe, Rollback |
| `home-import.php`, `home01.css` | HOME-01 | Native Aculia-Sliderdaten und Styling, Elementor-Zielwidget `1eef5e6` auf Home #14 |
| `publishing.php` | CONTENT-01 / HOME-02 | Native WP-Demo-Artikel, Publishing-Journal und dynamische Slider-Slot-Auswahl per Renderzeit-Hook |
| `navigation.php`, CSS/JS | NAV-01 | Native Aculia-Navigation, mobile Menü-/Sprachumschaltung; 0.4.8 korrigiert Varianten bei verschiedenen Breiten |
| `content-header.php`, CSS | HEADER-01 | Native Content-Page-Header, nicht Composer-Header |
| `native-journal-bridge.php` | NATIVE-JOURNAL-047 | Expliziter, streng geprüft geschriebener Native-Inhaltstransfer auf **#14 / #455**, mit SHA-/Widget-Gates, Sicherungen/Rollback |
| `tools-dashboard.php` | Admin-Werkzeugübersicht | **Kacheln zu Funktionen**, keine zusätzlichen Plugins |

**Vorsicht bei der Bridge:** `NATIVE-JOURNAL-047` verändert im Gegensatz zum Home Composer bei explizitem Apply **gespeicherte Elementor-Daten** der Originalseite **#14** und des Footers **#455**. Der aktuelle Composer verwendet diese Brücke **nicht**. Ein Nachfolge-Thread darf die Bridge nicht versehentlich als „fehlendes Composer-Modul“ ausführen. Die vorhandenen Live-Funktionsstände vor einem Apply erneut prüfen; Baseline-Hashes aus lokalem Quellcode können inzwischen veraltet sein.

**Cockpit** (jüngster vorliegender ZIP-Code 0.2.0) ist ein Aggregator mit optionalem „kompaktem Werkzeuge-Menü“, kein Ersatz für Content Manager oder Composer. **RGB-Pilot** (jüngster vorliegender ZIP-Code 0.6.3) führt eine getrennte **Content-Version 0.6.0**; Plugin-Update bedeutet **keinen** Content-Import. **Integrator** 0.2.5 dient historischen Inventur-/Draft-Vorgängen; Draft **#1362** ist nicht die jetzt öffentliche Homepage.

## 8. Bekannte offene Punkte – bewusst auf nächste Version verschoben

### FN-013-UX-01: Wechselhöhe beim Match-Titel

**Nutzerbeobachtung 23.11.:** Beim Matchwechsel ruckelt die Fight-Night-Bühne geringfügig, insbesondere **einzeiliger ↔ zweizeiliger Titel**. Kein Beleg für Datenfehler.  
**Technischer Kandidat:** Die CMS-Bühne besitzt eine zweispaltige CSS-Grid-Hauptfläche mit links `display:flex; flex-direction:column; justify-content:center`, variablem `h2` und rechts Media-Container `height:100%` / `aspect-ratio:auto` im späten CSS-Override. Ändert sich die Textblockhöhe, kann die ganze Grid-Zeile neu vermessen werden. **Hypothese, erst reproduzieren/messen**, nicht bereits bewiesene Root Cause.  
**Abnahme:** Beim Wechsel 1↔2↔3 an Desktop 1440/1920/2560 und Mobile 390/768 keine sichtbare Verschiebung der Bühne, der Logo-Reihe oder der unteren Mediathek. Titel bleiben lesbar und umbrechen korrekt.

### FN-013-UX-02: Bildfläche / Bildrahmen passen noch nicht exakt

**Nutzerbeobachtung:** Verhältnis von Hero-Bild zu Rahmen noch nicht in allen Fällen passend. Der aktuelle CMS-Hero verwendet `object-fit:contain`; CSS `.hc-fn-visual` und Grid-Höhen stehen teilweise unter konkurrierenden Höhe-/Aspect-Ratio-Regeln, Thumbnail nutzt `object-fit:cover`.  
**Ziel:** Keine abgeschnittenen modellbezogenen Bildtexte/Logos im Originalbild; gleichzeitig kontrollierte Hintergrundfläche/Rahmen, definierte Letterbox nur wenn nötig. **Bilddateien selbst nicht austauschen**, bevor Responsive-Geometrie gefixt ist. Für Contentbilder später optional bildbezogenen Fokus/Seitenverhältnis prüfen.
**Abnahme:** pro Match original dimensions/aspect ratio dokumentieren; Hero vollständig sichtbar, Rahmen ohne unbeabsichtigte Lücken, Thumb-Crop konsistent, Bildwechsel ruckelfrei.

### FN-014-CONTENT: Echte Content-Anbindung

Der aktuelle CMS-Modus ist **funktionierend als Demo-Post-Quelle** – aber **kein vollständiger Fight-Night-Story-Importer**. Nächste fachliche Stufe: aus den wirklich freigegebenen WordPress-Match-Contentseiten Titel, Auszug, Featured Image, Logos, Why Watch, `story_id`, `match_id` und URL übernehmen. Fiktive Demo-Inhalte erhalten bleiben, bis Ersatz geprüft ist. Story-/Quellenmodell aus der separaten **Fight-Night-01-Dokumentation** übernehmen; **Fight Night nach Zuschauerpotenzial**, Research nach wissenschaftlichem Interesse selektieren. Keine automatisch behaupteten Sportergebnisse. Modul zeigt echte Stories erst nach Redaktion/Link-/Bildprüfung.

### Später (nicht morgen blockierend)

Mehrsprachige DE/EN-Inhalte samt Freigabe (ZH ggf. später), echtes Match-Panorama (bildbreiter, optional textfreier Klickteaser), andere Home-Scroller-Varianten, Whitepaper-Cover aus echten Veröffentlichungen, Replay-Deep-Links, Barrierefreiheit/Touch/Performance, WP-Cache und vollständige responsive Hostinger-Abnahme. **Keinen neuen Plugin-Baum** als reflexhafte Lösung erzeugen.

## 9. Sicherung & Rückweg – besonders wichtig, wenn der Thread endet

**Ein Plugin-ZIP ist nicht die aktuelle Website!** Sichern:

1. **Hostinger-Datenbank vollständig**, insbesondere `wp_options`, `wp_posts`, `wp_postmeta`, `wp_term*` und zugehörige WP-Tabellen. Nur dort liegt die **wirkliche gespeicherte Composer-Reihenfolge**.
2. **`wp-content/uploads/`** samt Originalfotos, hero-/brand-medien, drei Fight-Night-Covern und sechs importierten PNG-Logos, generierten Thumbnailvarianten.
3. **Alle tatsächlich installierten** Pluginverzeichnisse **inkl. MU-Plugins**, Theme/Child-Theme, samt PHP-/WP-Version und Liste aktiv/inaktiv. Nicht nur die früher heruntergeladenen ZIPs.
4. RGB Content-Paket **0.6.0** mit Verifikationsstatus, Modus sowie registrierten A–Z-/Sitemap-Dateien; das Plugin-ZIP **allein** enthält diese importierten Inhalte **nicht**.
5. Aculia/Elementor-Seite #14, Header #26/#532, Footer #455, Integrator-Draft #1362, die WP-Home-Einstellung und die im Composer gespeicherten `logo_id`/`hero_image_id`.
6. Screenshots des Composers **bei eingestelltem Theme und Modulreihenfolge** plus tatsächlich eingesetzte Seitenlayout-Variante; wichtig für visuelle Regressionsvergleiche.
7. Ein ZIP-/Artefaktverzeichnis mit **Originaldateinamen, Versionen und SHA-256**, insbesondere Composer 0.1.13 + Rückweg 0.1.12. **Keine Zugangsdaten/API-Schlüssel oder private DB-Dumps in ein öffentliches GitHub-Repo hochladen**.

**Rückweg nur mit konkreter Prüfung:**
- Neue Fight-Night-Demo ausblenden, `fight-stage` wieder einschalten, speichern; WP-Entwürfe und Medien bleiben erhalten.
- 0.1.12-Paket als Code-Rollback möglich, **aber der gespeicherte 0.1.13-CMS-Moduldatensatz bleibt**, sodass vollständiger visueller Rückweg **nicht** automatisch nur durch ZIP-Wechsel entsteht. Vorher Konfiguration sichern/prüfen.
- Öffentlichen Composer-Schalter deaktivieren → normale Aculia-Home an Test-Router zurück, Cache leeren. **Keine Löschung** von RGB-Pilot oder Content Manager.

## 10. Übergabesatz für den nächsten Thread

> Wir arbeiten am **ANDY Journal auf der Hostinger-Testdomain**. Die aktuelle öffentliche Homepage wird durch **ANDY Journal Home Composer 0.1.13 (FIGHT-CMS-10)** ausgegeben. Sie besteht aus gespeicherten, frei sortierbaren Modulen und einem optionalen Seitenrahmen/Sticky-Header. Der neue Fight-Night-CMS-Demoimport erzeugt drei **fiktive** WP-Entwurfsartikel, drei Motive und sechs transparente Demo-Logo-Platzhalter sowie das Modul `fightnight-cms-demo` an der alten Fight-Night-Position. **Nächster Patch: Wechselhöhe bei 1-/2-Zeilen-Titeln und Hero-/Rahmen-Aspektverhältnis stabilisieren; danach echte CMS-Match-Stories integrieren.** Composer-Konfiguration, Medien, RGB-Daten und native Elementor-Site sind verschiedene Speicherschichten. **Nur den bestehenden Composer weiterentwickeln; keine zweite Home, kein neues Plugin, kein ungeprüftes Überschreiben anderer Plugins.** Die Live-Installation/Versionen von Content Manager 0.4.8, Cockpit 0.2.0, RGB 0.6.3 etc. vor Änderungen im Hostinger-WP-Admin prüfen.

## 11. Verbindliche Referenzen

- [Journal-Status, alte Architektur-/Inventur-Chronik](../STATUS.md)
- [Plugin- und Paketregister vom 22.11.](../ANDY-JOURNAL-PLUGIN-UND-PAKETREGISTER-2026-11-22.md)
- [WP-Baseline und Content Manager](ANDY-JOURNAL-WP-BASELINE-2026-11-17.md)
- [Fight-Night-Template: Zuschauererlebnis vs. Research](ANDY-FIGHT-NIGHT-EDITORIAL-TEMPLATE-v0.1-2026-11-23.md)
- [App/Analyzer-Evidenz und Match Panorama](../../../../PROJECT/ANDY_FIGHT_NIGHT_01_JOINT_FINDINGS_AND_MATCH_PANORAMA_2026-11-23.md)
- **Lieferdoku lokal:** `ANDY-HOME-COMPOSER-FIGHT-CMS-10-v0.1.13.md` (mit ZIP übergeben; nicht als Installationsbeweis interpretieren).

**Status:** Dokumentation + vorhandener ZIP-Quellcheck. **Keine neue WordPress-Installation, keine Live-Eingriffe, kein Bugfix und keine Bereinigungsfreigabe** durch diesen Handover.
