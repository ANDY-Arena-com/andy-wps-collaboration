# ANDY Journal – Plugin-, Werkzeug- und Contentpaketregister

> **Aktueller Entwicklungscheckpoint 24.11.2026 (Tagesabschluss): [WP-ARCH R0.5](ARCHITECTURE/WP-ARCHITECTURE-R0.5.md).** Home Composer 0.1.37; Content Composer 0.1.26 nutzerseitig erfolgreicher Academy-Import und Content→Overview, 0.1.28 jüngstes Perspectives-Paket (positives Nutzerfeedback, detaillierte Live-Abnahme offen). 22 Release-Schritte samt ZIP-Prüfsummen; Academy A–D (18 Lektionen/Vorlagen), Perspectives (6 DE/EN-Paare und Overview), **problem-driven Crossover vor Research**, gemeinsame Content-Quelle. Ältere Versionsangaben unten sind historische Referenzen, keine Installationsanweisung. Release-Gate gilt unverändert; keine öffentliche Freigabe.


**Stand 22.11.2026, 18:49 CET · Status: Bestands- und Bereinigungsvorschlag, KEINE Deinstallation.**

Dieses Dokument ist die aktuelle, **nachgewiesene Teilinventur**. Es trennt installierte Plugins, in Plugins enthaltene Module, durch Pakete einmalig vorgenommene Änderungen, redaktionelle Bestände, WordPress-Objekte und sichtbare Menüs. Es ist keine Behauptung, dass ein vollständiger, aktueller WP-Plugin-Export vorliegt. **Nicht durch Screenshots/Live-Inventur belegte Details sind ausdrücklich offen.**

## 0. Die wichtigsten Zahlen und die Reichweite der Quellen

- WordPress-Plugins-Screenshot vom 22.11.: **14 Einträge, 14 aktiviert**, sowie **2 Must-Use-Plugins** als separate Kategorie; die Aufnahme zeigt nur einen Teil der Plugin-Liste.
- **6 namentlich und mit Pluginpfad identifizierte aktive ANDY-Plugins** im Live-Integrator-01-Export vom 22.11., 11:43 Uhr; danach wurde derselbe Integrator bis 0.2.5 aktualisiert bzw. als Update bereitgestellt (aktuellen Live-Versionsstand nochmals prüfen).
- **8 Karten der Content-Manager-Werkzeugübersicht** sind **nicht** acht eigene WordPress-Plugins.
- **5 Karten des Journal-Cockpits** sind **Weiterleitungen**, nicht fünf eigene Engines.
- **9 ANDY-bezogene Einträge unter Werkzeuge** aus Screenshot, teils zum selben Content Manager gehörig. Zusätzlich existieren WP-/Drittanbieter-Werkzeuge wie Scheduled Actions.
- Statische RGB-Inhaltsbasis **28 registrierte Seiten**, redaktionelle Sitemap-v2-Demoregistrierung **14 Einträge**, **34** native WordPress-Posts/Pages im Inventur-Snapshot, darunter **5** englische veröffentlichte Essay-Demos. Diese Zahlen **nicht addieren**, da verschiedene Speicher-/Zählweisen.

**Belege:** Nutzer-Screenshots der Pluginseite, des Cockpits, der Werkzeugübersicht v0.4.6 und des Werkzeuge-Menüs; echter Live-Export `ANDY-INTEGRATOR-01-20261122.json`; Live-Hook-/Header-Export `ANDY-INTEGRATOR-02C-20261122.json`; bisherige [WP-Baseline](docs/ANDY-JOURNAL-WP-BASELINE-2026-11-17.md), [Mapping](docs/ANDY-JOURNAL-INTEGRATOR-01-MAPPING-20261122.md) und [Systemstatus](STATUS.md). Quellcode des lokal vorhandenen Editorial-v2- und Integrator-Pakets wurde zusätzlich überprüft. **Kein Zugriff auf die aktuellen WordPress-Pluginordner bei Hostinger.**

### Legende

- **ERHALTEN:** technisch wichtig, keine Deaktivierung.
- **ZENTRALISIEREN:** Funktion behalten, aber doppelte Verwaltungslinks abbauen – später nach Callback-/Rechteprüfung.
- **ARCHIV-KANDIDAT:** nicht Teil des dauerhaften Betriebs; *nach* Backup/Abhängigkeitsprüfung ggf. Plugin deaktivieren.
- **PRÜFEN:** Funktionsumfang/Nutzung zu unvollständig belegt, keine Löschfreigabe.

## 1. Installierte ANDY-Plugins – sechs identifizierte Programme

| Plugin / Pfad | Version / Nachweis | Technischer Zweck | Empfehlung | Was passiert bei Deaktivierung? |
|---|---|---|---|---|
| **ANDY Content Manager** · `andy-content-manager/andy-content-manager.php` | **0.4.6**, Live-Export, Werkzeugübersicht | NAV-01, HEADER-01, CONTENT-01, HOME-02, HOME-01, Inventory, DESIGN-01, native Admin-/Publishing-Hooks | **ERHALTEN**, zentrale Funktionsquelle | Verwaltungsfunktionen, Header-/Slider-/Navigation-/Publishing-Hooks können entfallen: **nicht deaktivieren** |
| **ANDY Journal Cockpit** · `andy-journal-cockpit/andy-journal-cockpit.php` | **0.1.0**, Live-Export | Hauptmenü **ANDY Journal** mit fünf Weiterleitungen zu bestehenden Funktionen | **ZENTRALISIEREN**: ein zentraler Einstieg ist sinnvoll; dieses Cockpit ist unvollständig | Der ANDY-Journal-Menüzugang fehlt; Funktionen im Content Manager existieren weiter, aber Link-/Abhängigkeitsprüfung nötig |
| **ANDY RGB Content Pilot** · `andy-rgb-pilot/andy-rgb-pilot.php` | **0.6.1**, Live-Export | Liefert separaten HTML/CSS/JS-Contentbestand, Root-/Asset-Routing, private Vorschau | **ERHALTEN** bis Content-Migration und vollständiger Linkabnahme | RGB-Pilotseiten und ggf. gegenwärtige Root-Auslieferung verschwinden; **nicht deaktivieren** |
| **ANDY Launch Control** · `andy-launch-control/andy-launch-control.php` | **0.1.0**, Live-Export | Soll-/Ist-Sitemap, Contentplan, Redaktion/QA, Freigabeentwürfe | **ERHALTEN** | Admin-Workflow/QA-Zugänge entfallen; nicht voreilig deaktivieren |
| **ANDY Journal – Editorial Sitemap v2 Pilot** · `andy-journal-editorial-v2/andy-journal-editorial-v2.php` | **0.1.0**, Live-Export, ZIP-Code geprüft | Admin-only Vorschau: Home-Komposition, Sitemap v2, 14 Demo-Einstiege | **ARCHIV-KANDIDAT** nach Dokument-/Asset-Sicherung | Der geprüfte Code erzeugt keine Posts/Optionen; deaktivieren entfernt seine privaten `?andy_jv2=`-Vorschau-Routen, **nicht** RGB- oder native Inhalte |
| **ANDY Journal Integrator** · `andy-journal-integrator/andy-journal-integrator.php` | **0.1.0** im frühen Export; **0.2.5** als jüngstes Update ausgeliefert / Nutzer-Vorschau; Liveversion gesondert bestätigen | Inventur 0.1; Feldaudit 2A; Entwurfskopie **#1362** 2B; Header-/Slider-Audit 2C; Entwurfs-Meta-Sync und Rollback 2D; Runtime-CSS/JS-Vorschau 2E | **ARCHIV-KANDIDAT**, **jetzt nicht löschen** | Nach Deaktivierung entfallen Admin-Inventur, Undo-Funktionen und 2E-Vorschau-Overlay; **Entwurf #1362 und einmal geschriebene Metadaten bleiben**, sofern nicht getrennt zurückgenommen. Vorher Export/Backup nötig |

**Beachte:** `Integrationswerkzeug` und `Editorial v2` sind wirklich eigene Pluginordner; `ANDY Navigation` und `ANDY Global Header` dagegen **keine separaten Plugininstallationen**.

## 2. Was „ANDY Journal“ im linken WordPress-Menü anbietet

| ANDY-Journal-Cockpit-Menü | Ziel / Eigentümer | Anderweitig sichtbar? | Empfehlung |
|---|---|---|---|
| **Home** | Cockpit 0.1.0 – Übersicht mit 5 Kacheln | Content-Manager-Werkzeugübersicht mit 8 Kacheln | **Nur eine** zentrale Übersicht behalten |
| **Content Manager** | `andy-content-manager`: Inventory, Export | Werkzeuge → ANDY Content Manager; Werkzeugübersicht → Inventory | Link dupliziert – funktional behalten |
| **Publishing** | `andy-content-manager/publishing.php` | Werkzeuge → ANDY Journal Publishing; Übersicht → CONTENT-01/HOME-02 | Link dupliziert – funktional behalten |
| **Journal Module / Home** | `andy-content-manager/home-import.php` | Werkzeuge → ANDY Journal Module; Übersicht → HOME-01 | Link dupliziert – funktional behalten |
| **Design Import** | `andy-content-manager/design-import.php` | Werkzeuge → ANDY DESIGN Import; Übersicht → DESIGN-01 | Link dupliziert – funktional behalten |
| **RGB Pilot** | `andy-rgb-pilot` | Werkzeuge → ANDY RGB Pilot | Link dupliziert – Plugin erhalten |
| **Launch Control** | `andy-launch-control` | Eigener zusätzlicher Cockpit-Untereintrag | Nur **eine** QA-Position anzeigen |

Das Cockpit implementiert nach der ursprünglichen Quellcode-Analyse **keine eigene Import- oder Rollback-Engine**; es verlinkt vorhandene Admin-Callbacks.

## 3. Was die acht Karten der Content-Manager-Werkzeugübersicht 0.4.6 sind

| Kachel | Modul / Code-Familie | Weitere Oberfläche | Empfohlener Betrieb |
|---|---|---|---|
| **Navigation · NAV-01** | `andy-content-manager/navigation.php` – Menü-Labels, Responsiv-/Sprachwahl | Werkzeuge → ANDY Navigation | **ERHALTEN** |
| **Global Header · HEADER-01** | `andy-content-manager/content-header.php` – Inhaltsheader / Typseiten | Werkzeuge → ANDY Global Header | **ERHALTEN** |
| **Publishing · CONTENT-01** | `andy-content-manager/publishing.php` – native Posts, Publish/Withdraw | Werkzeuge → ANDY Journal Publishing | **ERHALTEN** |
| **Slider Manager · HOME-02** | Ebenfalls Publishing-/Slider-Logik, kein eigenes Plugin | Publishing / Werkzeugübersicht | **ERHALTEN**, keine zweite Slider-Engine |
| **Home & Layout · HOME-01** | `andy-content-manager/home-import.php` – Elementor-Module, Slider-Fixes | Werkzeuge → ANDY Journal Module | **ERHALTEN** |
| **Redaktion** | WordPress-Beiträge, Seiten, Mediathek und Kategorien | WP-Kernmenüs | **ERHALTEN**, keine zweite Content-Verwaltung |
| **Inventory** | `andy-content-manager/andy-content-manager.php` – Bestandsbericht | Werkzeuge → ANDY Content Manager | **ERHALTEN** |
| **Design · DESIGN-01** | `andy-content-manager/design-import.php` – Logo, Farben, Design-Import | Werkzeuge → ANDY DESIGN Import | **ERHALTEN**, keine erneute Paketinstallation |

Die `Werkzeugübersicht` selbst stammt laut Hook-Bericht aus `andy-content-manager/tools-dashboard.php` (`admin_notices`). Sie ist **kein** achtes eigenständiges Plugin und sollte als Oberfläche mit dem Cockpit zusammengeführt werden.

## 4. „Werkzeuge“ – tatsächliche Herkunft der ANDY-Menüpunkte

| Sichtbarer Eintrag | Eigenes Plugin? | Verantwortlicher Ordner | Ziel |
|---|---|---|---|
| ANDY Content Manager | **Nein, Teilfunktion** | `andy-content-manager` | Einer zentralen Admin-Navigation zuordnen |
| ANDY DESIGN Import | **Nein, Teilfunktion** | `andy-content-manager` | Redundanten Link später entfernen, Funktion bewahren |
| ANDY Journal Module | **Nein, Teilfunktion** | `andy-content-manager` | Redundanten Link später entfernen |
| ANDY Journal Publishing | **Nein, Teilfunktion** | `andy-content-manager` | Redundanten Link später entfernen |
| ANDY Navigation | **Nein, Teilfunktion** | `andy-content-manager` | Einmalig in die zentrale Übersicht aufnehmen |
| ANDY Global Header | **Nein, Teilfunktion** | `andy-content-manager` | Einmalig in die zentrale Übersicht aufnehmen |
| ANDY Editorial v2 | **Ja** | `andy-journal-editorial-v2` | Admin-Pilot, später archivieren |
| ANDY RGB Pilot | **Ja** | `andy-rgb-pilot` | Behalten; nur eine sichtbare Verlinkung |
| ANDY Integrator | **Ja** | `andy-journal-integrator` | Temporär für Entwurf/Undo; später archivieren |
| Scheduled Actions | **Nicht als ANDY belegt** | Drittanbieter/WP-Background-Jobs | Nicht in die ANDY-Bereinigung aufnehmen |
| Import / Export / Website-Zustand / Datenschutz | **WP-Kern-/Drittanbieter-Funktionen** | Unabhängig von ANDY | Nicht entfernen |

**Vorsicht:** „Menülink ausblenden“ ist nicht „Plugin deaktivieren“; beides ist nicht „Inhalte löschen“. Keiner dieser drei Schritte wurde bisher durchgeführt.

## 5. Inhalte, Importpakete und Paketcode – keine zusätzlichen Plugins

| Paket / Bestand | Tatsächliche Rolle | Status | Empfehlung |
|---|---|---|---|
| **DESIGN-01.zip** | Einmaliger, kontrollierter Import von Logo/Site-Identität und ausgewählten Farben | Frühere Adminansicht: **applied** | **Archivieren**, nicht erneut installieren; Änderungen leben in Theme-/WP-/Medien-Einstellungen |
| **ANDY-HOME-01.zip** | Native Anpassungen am Slider von WP-Seite **#14**, `wpsection_banner_slider` | Frühere Adminansicht: **applied** | **Archivieren**, vorhandene Struktur erhalten, kein Reimport |
| **ANDY-CONTENT-01.zip** | Native Demoartikel/Publishing-Slots, insbesondere fünf Essays | Frühere Adminansicht: **applied** | **Archivieren**, echte Posts behalten; keine doppelten Importe |
| **HOME-02** | Dynamischer Publishing-/Slider-Modus des Content Managers | Frühere Oberfläche: Konfiguration gespeichert, Browser-/Runtime-Test separat nötig | **Code-Funktion erhalten**, kein eigenständiges Installationspaket |
| **NAV-01 / HEADER-01** | Laufende Navigation-/Header-Module innerhalb Content Manager | NAV-01 `Aktiv`, HEADER-01 `Aktiv · Frontend prüfen` in der alten Werkzeugübersicht | **Erhalten**, keine zusätzliche Header-Lösung |
| **ANDY RGB Content 0.6.0** | Versionierte HTML-/JS-Inhaltswelt, **28 Seiten** und darin genutzte interaktive Originalmodule | Aktiver Adapter **0.6.1**, Content-Stand **0.6.0** laut früheren Frontend-Screenshots; Byte-/Paketvollständigkeit nicht live erneut bestätigt | **Erhalten** bis gesicherter Migration aller URLs/Module. Inhaltspaket ist **nicht** ein zweites Plugin |
| **Editorial Sitemap v2 / 14 Demos** | Redaktionsregister und statischer Vorschau-Bestand, 13 bestehende Einstiege plus ein Konzept | Adminpilot; **keine** 14 neuen nativen WP-Posts | **Matrix/Dokumentation erhalten**, Pilotruntime später archivieren |
| **5 native Essays** | WordPress-Posts **1329, 1331, 1333, 1335, 1337**, veröffentlicht | Titelgleich zu fünf RGB-Einträgen; Inhaltsgleichheit ungeprüft | **Posts erhalten**, nicht löschen/doppelt importieren |
| **Aculia-Theme-Demo-Content** | Labor-/Medizin-Bilder, Demo-Beiträge, „CHAMISTRY“, Platzhalter-Footer | Screenshots zeigen diese Inhalte weiterhin | **Erst nach redaktionellem Ersatz** und Abhängigkeitsprüfung bereinigen |
| **Aculia-Home #14** | Tatsächliche konfigurierte native WP-Startseite | `publish`, `page_on_front=14` | **Geschützt erhalten** |
| **ANDY-Entwurf #1362** | Vom Integrator 2B erzeugte separate Draftseite | `draft`; 2E nur Overlay | **Als nicht veröffentlichte historische Testkopie erhalten**; später archivieren, nicht zum dritten Frontend machen |
| **ANDY Academy / Replay Pilot 0.1** | Historisch separat getestete Renderer und Datenpakete | Alte Doku bestätigt Tests; **aktueller Plugin-/Shortcode-Status auf Hostinger nicht belegt** | **PRÜFEN**, nicht als installiert, integriert oder entbehrlich behaupten |

### Weitere installierte WordPress-Plugins

Der Screenshot der WordPress-Pluginliste vom 22.11. zeigt insgesamt **14 aktive Plugins** und separat **2 Must-Use-Einträge**, aber **nicht die ganze Namensliste**. Neben den sechs ANDY-Plugins sind namentlich mindestens diese vier Drittanbieter erkennbar:

- **aculia Plugin (1.0)** – wahrscheinlich für WpSection-/Aculia-Theme-Komponenten erforderlich: **ERHALTEN**, technische Abhängigkeit vor jeder Entscheidung prüfen.
- **Elementor (4.4.1)** – aktive native Seiten-/Template-Engine: **ERHALTEN**.
- **Contact Form 7 (6.2.5)** – Formularfunktion: **PRÜFEN**, ob aktive Formulare/Shortcodes sie verwenden; dann erhalten.
- **Hostinger Hub** – Hosting-Verwaltungsintegration: **PRÜFEN**, keine pauschale Deaktivierung.

Die verbleibenden **vier der 14 aktiven Plugins** sind mit den uns vorliegenden Bildern **nicht namentlich belegt**. Menüindikatoren wie `MC4WP` können auf weitere Plugins hinweisen, ersetzen aber keinen vollständigen Pluginexport. Die **zwei Must-Use-Plugins** sind ebenfalls nicht identifiziert. **Keine Lösch-Empfehlung dafür ohne Listennachweis.**

## 6. Was kann weg? Priorisierte und sichere Entscheidung

### A. Ohne Verlust von Funktionen aus der täglichen Navigation entfernen – NACH Menü-/Callbackprüfung
1. Die **doppelten ANDY-Werkzeuge-Links** zu Content Manager, Publishing, Module, Design Import, Navigation, Global Header und RGB: **nur Menüanzeige konsolidieren**, nicht die zugrunde liegenden PHP-Module deaktivieren.
2. Die zweite **Content-Manager-Werkzeugübersicht als parallele Landingpage** abschaffen: Ihre acht Funktionen in **eine** zentrale ANDY-Journal-Übersicht integrieren. Dazu wäre vermutlich Cockpit als einziges Navigationsmenü geeignet; tatsächliche Slugs/Callbacks vor Änderung verifizieren.
3. **Editorial-v2 und Integrator** später unter „Archiv/Experimente“ verschieben oder nach Sicherung deaktivieren, statt als aktive Alltagswerkzeuge zu zeigen.

### B. Kandidaten für spätere Plugin-Deaktivierung
- **Editorial v2**: derzeit stärkster Kandidat. Im vorliegenden ZIP nur adminseitige Vorschau-Routen, keine persistenten Contentwrites. Vor Deaktivierung Sitemap-/Bild-/Demo-Register und wichtige Referenzen sichern; Sichtprüfung, dass keine Nutzerlinks darauf zeigen.
- **Integrator**: erst nach Export der Inventuren, Dokumentation des **Drafts #1362**, Prüfung der in **2D** auf #1362 kopierten Metadaten und Sicherung der Rücknahme. Nach Abschalten verschwinden die 2E-Optikeffekte, **aber es erfolgt kein automatisches Zurücksetzen von bereits geänderten Metafeldern**.
- **Cockpit**: als eigenständiger Pluginordner nur dann entbehrlich, wenn **alle** Einstiegspunkte auf einer funktionierenden anderen Übersichtsseite erhalten sind. Derzeit **nicht** einfach deaktivieren.

### C. Explizit NICHT entfernen
**Content Manager, RGB Pilot, Launch Control, Aculia-Theme-Unterstützung, Elementor, WordPress-Inhalte, Original-Header 26/532, Footer 455, Original-Home 14, vorhandene Game-/Academy-/Replay-Daten**; unabhängig vom späteren Layout-Entscheid.

## 7. Konkrete Prüfliste vor tatsächlicher Bereinigung

- [ ] Vollständigen **Plugins → Installierte Plugins**-Export/Bildschirm inklusive aller 14 aktiven und 2 MU-Einträge sichern; aktuelle Pluginversionen/Ordnernamen feststellen. Kein Ratespiel zu den übrigen Plugins.
- [ ] Content-Manager-Quellcode **0.4.6** und Cockpit-0.1.0-Laufzeitstand nach Slug, Callback, Capability, Hooks und Speicherung auditieren; aus 2C sind `publishing.php`, `navigation.php`, `content-header.php`, `home-import.php`, `design-import.php` und `tools-dashboard.php` belegt.
- [ ] WordPress-/Hostinger-Backup, Home #14, Entwurf #1362 und Optionen (insbesondere RGB-Standardmodus) sichern.
- [ ] Menü-Herkunft/Umleitung prüfen und **nur einen** Cockpit-Einstieg als Admin-Standard auswählen.
- [ ] Archivkandidaten zunächst **ausblenden**, nicht gleichzeitig deinstallieren; danach Browser-/Frontend-Prüfung, auch mit `/` und `/?utm_source=...`.
- [ ] Erst nach funktionsgleicher Abnahme separat über **Deaktivieren/Uninstall/Datenbereinigung** entscheiden.

**Entscheidungsregel:** „Nicht mehr im Alltag sichtbar“ heißt **nicht** „technisch entbehrlich“ oder „Daten dürfen gelöscht werden“. Diese drei Entscheidungen getrennt freigeben.

## 8. Offene Blocker und ehrliche Grenze

Eine **vollständig autoritative aktuelle Plugin-/MU-Liste und der vollständig installierte Code aller Komponenten** sind bislang nicht exportiert. Die Screenshots und JSON-Berichte erlauben die obige fachlich belastbare **Teilübersicht**, aber **keine sichere Aussage, dass jedes Plugin erkannt wurde**, keine konkrete Liste aller vier unbekannten Drittanbieter und keine sofortige Uninstall-Freigabe. **Bis dahin: keine Deinstallation.**

Dies ist bewusst **kein** neuer Plugin-Release. Frühere Produktiv-/Vorschauabweichungen sind durch diese Dokumentation nicht behoben. Der Benutzer entscheidet nach Sichtung, was tatsächlich aus der Navigation verschwindet oder technisch deaktiviert wird.

## 9. Korrektur aus tatsächlichem RGB-Frontend (18:55) – Bestehende Funktion NICHT neu bauen

Die Nutzer-Screenshots vom 22.11.2026 um 18:55 **belegen konkret den vorhandenen Funktionsstand der RGB-Inhaltswelt**; dies korrigiert jede Interpretation der früheren Tabellen, die diese Funktionen als „nur geplant“ oder „noch zu entwickeln“ behandeln könnte.

| RGB-Runtime 0.6.0 / UI 0.6.1 | Sichtbarer bereits vorhandener Bestand | Verbindliche Einordnung |
|---|---|---|
| RGB-Home / Perspectives | bereits publizierte Pilot-Teaser zu „When Chess Meets Go“, „The Fragility of Balance“, „When the Rules Change“ mit Bildern, Rubrik-/Alle-Inhalte-Navigation | **Existierender Content**, keine Pflicht zu neuen Demo-Posts oder neuem Grid |
| `?andy_rgb_asset=a-z.html` | **28 Schlagwörter**, **15 zugeordnete Pilotseiten**; Suche, Filter nach den drei E, Buchstabenfilter, thematische Verweise | **Existierende A–Z-Funktion**; nicht als neues Plugin/Tag-Datenmodell erneut entwickeln |
| `?andy_rgb_asset=sitemap.html` | **28 vorhandene Pilotseiten** als Hierarchie mit Home, drei E, Gabelseiten und Beiträgen | **Existierende Sitemap**; nicht als neue öffentliche Funktion erneut entwickeln |
| RGB-Home-Footer | **Sitemap** und **A–Z / Themen** verlinkt | Funktion ist bereits umgesetzt; der Integrator-2E-Footer ist dafür **keine neue Inhaltsfunktion**, sondern allenfalls eine *visuell/nativ noch nicht übernommene Linkplatzierung* |

**Architekturrelevante Unterscheidung:** Die sichtbare RGB-Implementierung ist eine eigenständige HTML-/CSS-/JS-Runtime und funktioniert in **deren** Oberfläche. Sie ist **nicht automatisch** Bestandteil der nativen Aculia-/Elementor-Seite #14 oder des Drafts #1362. Unsere Aufgabe ist **Übernahme/Anbindung mit belegtem Quellbezug**, nicht paralleler Neubau. Die Editorial-v2-Sitemap ist eine **alternative redaktionelle Zuordnung**, keine bereits migrierte Ablösung der RGB-Sitemap. Falls später andere Oberrubriken verwendet werden, ist ein dokumentiertes Mapping zu den 28 bestehenden Seiten erforderlich.

**Wichtige technische Sperre:** RGB-Quellregister (Keys/Routen/Tag-Zuordnungen) vor einer nativen Migration unverändert sichern; keine zweite A–Z-Datenbank, keine doppelte Sitemap, keine Neuanlage identischer Beiträge, keine erneute Footer-Sitemap. Zuerst echte Funktionszuordnung und Linktest, *danach* Darstellungswechsel. **Kein Plugin-Update / kein WP-Apply durch dieses Register.**
