# ANDY Journal — EINZIGE AKTUELLE SYSTEMÜBERSICHT

> **Neu: [Plugin-, Werkzeug- und Contentpaketregister vom 22.11.2026](ANDY-JOURNAL-PLUGIN-UND-PAKETREGISTER-2026-11-22.md)** – Nachweis, Zuständigkeit, Keep/Archiv-Kandidaten und offene Identifikationslücken. **Noch keine Deinstallationsfreigabe.**

**Datum:** 22.11.2026 · **Entscheidungsstatus:** Entwicklungs-FREEZE / Architektur-Inventur. **Dies ist ein Ist-/Abweichungsregister, keine Freigabe und keine neue Plugin-Spezifikation.** 

> **Leseregel:** Die älteren Architektur- und Release-Dokumente bleiben als *Historie* erhalten. Diese Datei ist der Einstieg für den **heute bekannten** Stand. Auf diesem Stand darf kein neues Plugin- oder Layout-Release gegründet werden, bevor die aufgeführten offenen Punkte durch Quellcode/Laufzeitprüfung geklärt sind.

## 1. Warum wir in Schwierigkeiten sind

Die Screenshots vom 22.11.2026 zeigen **drei parallel sichtbare Administrationswege** für wesentlich dieselben Funktionen: das **ANDY Journal Cockpit** (fünf Kacheln), die vom **Content Manager** bereitgestellte **Werkzeugübersicht v0.4.6** (acht Kacheln) und die nativen **Werkzeuge → ANDY …**-Menüeinträge. Dazu wurden die eigenständigen Piloten **RGB**, **Launch Control**, **Editorial v2** und **Integrator** ergänzt, deren Zuständigkeiten sich überschneiden.

Es gibt nicht „acht neue Plugins“: Die acht Kacheln des Content Managers bündeln die bereits vorhandenen Module **NAV-01, HEADER-01, CONTENT-01, HOME-02, HOME-01, Redaktion/WP, Inventory, DESIGN-01**. Diese Unterscheidung ist zentral.

**Fehler der jüngsten Entwicklung:** Der Integrator erzeugte Entwurf **#1362** aus Aculia-Home **#14** und korrigierte danach Header/Footer-Metas (2D) und die Darstellung über **vorschaugebundenes CSS/JS (2E)**, während der ursprünglich im Content Manager implementierte Header-/Slider-/Publishing-Workflow nicht als durchgängiges System übernommen wurde. Browserfotos zeigen daher Mischzustände und Aculia-Platzhalter. **2E ist nicht abgenommen.**

## 2. Komponentenkarte / beobachteter Ist-Stand

| Komponente | Eigentümer / tatsächliche Aufgaben | Beobachteter Status | Ziel / Maßnahme |
|---|---|---|---|
| **WordPress + Aculia Child / Elementor / WpSection** | Native Darstellung, originale Elementor-Seite und Theme-Widgets | **#14** veröffentlichte Home; **#26** seitenbezogener Home-Header; **#532** globaler Header; **#455** Footer | Technischer Frontend-Bestand, unverändert sichern; keine weitere Kopie |
| **ANDY Content Manager** `andy-content-manager` | Bereits implementierte Module: NAV-01, HEADER-01, CONTENT-01, HOME-02, HOME-01, Inventory, DESIGN-01, Tools-Dashboard/Redaktion | Version **0.4.6** laut früherem Live-Inventar und aktuellem Screenshot der Werkzeugübersicht; interne Modulansicht teils **v0.4.2** | **Einziger fachlicher Einstieg für vorhandene native Admin-Funktionen**; zuerst Code-/Hook-Audit, nicht durch Integrator neu implementieren |
| **ANDY Journal Cockpit** `andy-journal-cockpit` | Menü-Aggregator: Weiterleitungen zu fünf vorhandenen Werkzeugen, keine eigene Import-Engine | **0.1.0**, fünf Kacheln; bildet 0.4.6-Module unvollständig ab | Später auf **eine** vollständige Admin-Landingpage konsolidieren; bis dahin nicht blind deinstallieren |
| **ANDY RGB Pilot** `andy-rgb-pilot` | Separate, versionierte statische HTML/CSS/JS-Inhaltswelt mit eigenem Root-/Asset-Routing | **0.6.1** laut Nutzer-/Inventurstand; **28** registrierte RGB-Seiten | Geschützte Inhalts-/Modulreferenz; nicht als zweite kanonische öffentliche Home weiterentwickeln. Aktuellen `off/admin/staging`-Modus + Cache prüfen |
| **ANDY Launch Control** | Soll-Ist, Sitemap, Draft-Workflow, QA/Freigabe | **0.1.0** auf Staging laut früherer Pluginliste | QA-/Freigabe-Rolle behalten; keine eigene parallel gepflegte Sitemap-Quelle |
| **ANDY Editorial Sitemap v2 Pilot** | Private Admin-Vorschau für redaktionelle Familien, Bild-/Template-Matrix | **0.1.0**, 14 Demo-Einstiege (darunter ein Konzept) | Nur Planungsreferenz, **keine** kanonische Contentquelle und keine zusätzliche Home |
| **ANDY Journal Integrator** `andy-journal-integrator` | 0.1 Inventur, 2A Feldaudit, 2B Draft, 2C Vergleich, 2D Metaabgleich, 2E CSS-/JS-Vorschau | **0.2.4 / 2E** laut Nutzer-Screenshots in privater Vorschau; Draft **#1362** | Entwicklung **STOPP**. 2E nicht abgenommen; keine weitere optische Runtime-Überlagerung. Für Berichte nur solange nötig behalten |
| **Native WP-Beiträge/Seiten** | Langfristig einzige redaktionelle Inhaltsquelle | **34** Posts/Pages laut Inventur; fünf englische veröffentlichte Demo-Essays sind titelgleiche RGB-Kandidaten, **nicht** als inhaltlich identisch bestätigt | Doppelte Publikation vermeiden; Inhalt, kanonische URL, Taxonomie und Rechte vor Migration prüfen |
| **Replay / Academy / Research-Module** | Spezial-Renderer und Originaldaten/Interaktionen | Historisch separate Plugin-Tests; aktueller Hostinger-Installations-/Integrationsstatus **nicht vollständig bestätigt** | Nicht kopieren/neuerfinden; nur nach tatsächlicher Renderer-/Shortcode-Prüfung einbinden |

**Quelle für die Modulnamen und Status:** Nutzer-Screenshots vom 22.11.2026, WordPress-Live-Inventar 0.1 und Header-/Hook-Audit 2C. Das 2C-Audit wies u.a. `andy-content-manager/publishing.php` mit `elementor/frontend/builder_content_data → andy_s_front`, `navigation.php` sowie `content-header.php` als registrierte Hooks aus. Ein Admin-Hook-Snapshot beweist **nicht** alle Frontend-Scopes.

## 3. Seiten-/Datenrealität: nicht gleichsetzen

| Sachverhalt | Bestätigter Stand |
|---|---|
| Native WordPress-Home | **#14** ist konfiguriert als `page_on_front`, Status `publish` |
| Neue Aculia-Preview | **#1362** ist `draft`, enthält ANDY-Teasertexte; wird durch Integrator-2E-Overlay optisch verändert |
| RGB-Home | Eigenständiger vom RGB-Adapter ausgelieferter HTML-Inhalt, **keine native WP-Seite**; Root/UTM kann abweichend erscheinen, Ursache offen |
| Editorial v2 | Eigenes Admin-Vorschaulabor; weder #14 noch #1362 noch native Beitragsmigration |
| RGB / Editorial / WP | **28** RGB-Einträge, **14** Demos und **34** native WP-Posts/Pages sind **verschiedene Bestände/Zählweisen**, keine Summe und keine bestätigte Migrationsquote |
| Header/Slider 2C | #14 hat expliziten Header **26** und Footer **455**, #1362 fehlten diese sieben Aculia-Metafelder, 2D zielte auf selektive Kopie; 3 Slides beider Seiten nutzten Medien **1324/1325/1326**, Texte divergieren gewollt |
| Verbleibender Altcontent | In #1362 weiterhin Medical-Stock, „CHAMISTRY“, englische Demo-Essays und unpassende Footer-Kontaktangaben sichtbar; **nicht** als Journal fertig |

## 4. Einzige sinnvolle Zielarchitektur (Vorschlag, noch nicht implementiert)

**Redaktioneller Inhalt:** native WordPress Posts/Pages/Media/Taxonomien (**eine** kanonische Instanz pro Inhalt). RGB nur als Import-/Abnahmequelle, keine zweite Datenbank.

**Darstellung:** Aculia-/Elementor-Templates inkl. bestehender originaler Header-/Slider-/Layout-Funktionen; spezialisierte Replay-/Academy-/Research-Renderer eingebunden, nicht durch Ersatzteaser simuliert.

**Backend:** **eine** sichtbare ANDY-Journal-Werkzeugübersicht, die auf echte Content-Manager-Module delegiert. Cockpit- und Tools-Duplikate **erst nach Slug-/Callback-/Rechteaudit** konsolidieren, nicht blind Menüs entfernen. Launch Control bleibt QA/Freigabe. Integrator und Editorial v2 werden nach abgeschlossener Migration archiviert oder klar unter „Experimentell“ geführt, nicht als weitere primäre Steuerzentralen.

**Arena:** `www.andy-arena.com` bleibt eine andere Website und darf nicht zum Journal werden.

## 5. Sofortige FREEZE-Grenzen

1. **Keine weiteren Integrator-2F-/CSS-/Design-Plugins**, keine neue Homepage, keine Reimports von DESIGN-01, HOME-01, CONTENT-01.
2. **#14, #26, #532, #455, #1362 und RGB-Daten nicht löschen oder überschreiben**. Keine Publikation.
3. Für die Betrachtung von **#1362 ohne 2E** den vorhandenen Preview-Schalter `andy_jint02e=off` verwenden; **nicht** Content Manager/RGB/andere Plugins pauschal deaktivieren.
4. Backups/WordPress-Datenstand vor jeglicher schreibender Konsolidierung sichern.
5. Die Frontend-Abweichung `/` gegenüber `/?utm_source=chatgpt.com` getrennt diagnostizieren (RGB-Modus, Cache, WordPress-Redirect), nicht per weiterer CSS-Schicht kaschieren.

## 6. Vor dem nächsten schreibenden Schritt zwingend

- **Ist-Code/Versionen** der tatsächlich auf Staging installierten Pluginverzeichnisse prüfen, speziell `andy-content-manager` **0.4.6**, `andy-journal-cockpit`, `andy-rgb-pilot` sowie den aktuellen aktiven 2E-Stand. GitHub-Release-Memos ersetzen **keinen** Code-/Dependency-/WP-Options-Audit.
- **Menü-Herkunft-Matrix:** Sichtbares Hauptmenü/Cockpit/Werkzeuge → WordPress-Menu-Slug → PHP-Callback → verantwortliches Plugin → Schreib- und Leseaktionen → Abhängigkeiten. Ziel: **eine** Oberfläche, ohne Funktionen zu löschen.
- **Frontend-Besitzmatrix:** Theme/Aculia-Template/Content-Manager-Publishing-Hook/RGB-Router/Integrator-Preview getrennt nach `/auto`, `/`, `/?utm_source=...`, `?preview...` und `?andy_rgb_asset=...` verifizieren.
- **Content-Migration-Matrix:** realen WP-Beitragsbestand, 28 RGB-Inhalte, fünf Essays und konkrete Widgets abgleichen; erst **ein** nachweisbar nativer Beitrag samt Teaser/Player/Breadcrumb/Link als End-to-End-Probe, bevor weitere Inhalte umziehen.
- **Abnahme-Gate:** Backups, Vergleich Original vs. Preview, Bildrechte, funktionierende Links, Mobil/Sticky/Cache, Rollback und explizite Nutzerfreigabe. Bei fehlendem Nachweis stoppen.

**Blocker:** Ein aktueller vollständiger Quellcode-/Hosting-Export von Content Manager 0.4.6 und den übrigen installierten Plugins liegt in diesem GitHub-Dokumentationsbestand nicht vor. Ein Voll-Audit aller Admin-Menüs und Hooks ist daher aus den vorhandenen Memos/Screenshots **nicht möglich**. Nicht als erledigt ausgeben.

## Historische Referenzen (keine aktuellen Implementierungsanweisungen)

- [WP-Baseline 17.11.](docs/ANDY-JOURNAL-WP-BASELINE-2026-11-17.md)
- [Integrator-01-Mapping](docs/ANDY-JOURNAL-INTEGRATOR-01-MAPPING-20261122.md)
- [2C-Bestandsschutz der Header-/Slider-Funktionen](docs/ANDY-JOURNAL-2C-HEADER-SLIDER-BESTANDSSCHUTZ-2026-11-22.md)
- [2E-Releasebericht – **NICHT ABGENOMMEN**](docs/ANDY-JOURNAL-INTEGRATOR-02E-RELEASE-2026-11-22.md)
- [Launch Control](docs/ANDY-JOURNAL-PUBLIC-BETA-LAUNCH-CONTROL-v0.1.md)
- [Plugin-Architektur](docs/ANDY-JOURNAL-PLUGIN-ARCHITEKTUR-v0.1.md)

**Weitere technische Entscheidungen gehören zuerst hierher. Keine gleichberechtigten konkurrierenden „Masterpläne“ fortschreiben.**


## Ergänzung 22.11.2026 – gezielte Korrektur von 2E, noch keine Live-Abnahme

Auf ausdrückliche Nutzeranweisung wurde **kein neues Plugin und keine neue Homepage**, sondern ein lokales Update des vorhandenen `andy-journal-integrator` erstellt: **Version 0.2.5 / `ANDY-WP-PLUGIN-Integrator-v0.2E-KORREKTUR.zip`**, SHA-256 `b8fffaa3e3cc966d408e648e598de17438713cb9de56c88a8a2dfd2f4dd9b859`. Das öffentliche GitHub-Repository enthält weiterhin **keine Binärdatei**; das ZIP wurde im Chat ausgeliefert.

**Genau behobene Code-Mängel des bisherigen 2E:** (1) negative Positionierung der ursprünglichen Owl-Sliderpfeile über der Viererreihe → eigene reservierte Steuerleiste, welche die Originalpfeile auslöst; (2) Flex-/Höhenabgleich bislang nur an Elementor-Außenhüllen → Aculia-Inner-Box/Content/CTA einbezogen; (3) weißer Fight-Night-Titel auf weißer Aculia-Fläche → Titel- und Tab-Sektionen zusammen gekennzeichnet, dunkler Hintergrund, versteckte Elementor-Overlays und lesbare Inhalts-Panels; (4) Behind-ANDY- und Themen-/Sitemap-/A–Z-Einfügung bisher von enger Footer-Klassenliste abhängig → Vorrang für tatsächliches Elementor-Template **#455**, Fallbacks für Theme-Strukturen. Wortlauter Tyson-Claim verbleibt **direkt vor** Fight Night. 

**Tests lokal:** PHP-Lint auf 5 Dateien, Node-Syntax, alte 45 negativen/Static- und 13 positiven PHP-Stubs, 21 neue Scope-/Bestandsschutzchecks und 18 synthetische DOM-Checks, ZIP-CRC und Pluginversionsprüfung **bestanden**. Es gibt **keine** neue reale Hostinger- oder Elementor-Browserabnahme; die Korrektur gilt **nicht als abgenommen**. Screenshot-/Responsivetest mit 2E an/aus erforderlich. 

**Grenzen:** Scope nur im authentifizierten Preview-Draft **#1362**, keine persistente Elementor-/Theme-Änderung und keine Migration der RGB-Inhalte. **Aculia-Demo-Bilder, CHAMISTRY-Posts und Platzhalter-Kontaktdaten bleiben technisch weiterhin vorhanden.** Die frühere LIVE-/FREEZE-Grenze für neue Teilprojekte und Publikation gilt unverändert; diese Reparatur korrigiert ausschließlich das bereits ausgelieferte 2E im bestehenden Plugin und setzt keine öffentliche Änderung frei.
