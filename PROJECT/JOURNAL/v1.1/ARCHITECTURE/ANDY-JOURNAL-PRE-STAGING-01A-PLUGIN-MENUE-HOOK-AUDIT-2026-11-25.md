# ANDY Journal · PRE-STAGING-01A – Plugin-Menü-, Hook- und Zuständigkeitsaudit

**25.11.2026 · Read-only-Codeaudit abgeschlossen; WordPress-/Hostinger-E2E offen.**

**Belegbasis:** Der am 25.11. aus WordPress/Hostinger exportierte Quellbestand `ANDY-WP-PLUGIN-Package.zip`, SHA-256 `4277fcb18aa60d55b3e7e940d23143088b402addf7344abf8432610ed0fe420a`. Die vorhandene Screenshot-Pluginliste belegt daneben Nutzer-seitig 20 Plugin-Einträge: 18 aktiv, 2 inaktiv. Das Paket enthält 10 ANDY-Pluginordner, darunter den inaktiven Content Composer 0.1.4. **22/22 gezielte statische Quellprüfungen bestanden; keine Live-Datenbank, echte WordPress-Menühooks, Performance oder Staging-Umgebung geprüft.**

Verbindlicher Architekturkontext: [PRE-STAGING Governance](ANDY-JOURNAL-PRE-STAGING-ADMIN-UND-LAUNCH-GOVERNANCE-2026-11-25.md) · [Making of MO12](../content/ANDY-MAKING-OF-STORY-KATALOG-v0.1-2026-11-25.md#6-mo12--vom-werkzeug-wildwuchs-zur-betriebszentrale-25112026).

## 1. Kernergebnisse

- Die **neun als aktiv gemeldeten ANDY-Plugins** enthalten **22 explizite Registrierungen von Admin-Menüs** (nicht 22 neue Plugins). Sechs entstehen aus Content Manager 0.4.8, acht aus Content Composer 0.1.29, zwei aus Cockpit 0.2.0, je eine aus Home Composer, Launch Control, RGB Pilot, Making of, Editorial v2 und Integrator. Einige sind vom Host oder einer aktiven Option abhängig.
- **Zwei „ANDY Content Manager“ sind fachlich verschieden**: `tools.php?page=andy-content-manager` führt zu `andy_cm_screen` in `andy-content-manager/andy-content-manager.php` (Inventory/Theme/Native); `edit.php?page=andy-content-manager` zu `andy_cm_page` in `andy-journal-content-composer/includes/content-manager.php` (Match Stories/Home-Freigaben/Dublettenkandidaten). Sichtbare Namen schärfen, technische Slugs/Callbacks erhalten.
- **Cockpit 0.2.0 hat schon einen umkehrbaren Kompaktmodus**: Option `andy_jc_compact_tools_menu_v020`, standardmäßig aus; `andy_jc_compact_menu()` entfernt neun doppelte `tools.php`-Untermenülinks per `admin_menu` Priorität 999. POST/Nonce/Bestätigung existieren. Der Modus unterdrückt auch die zusätzliche acht-Karten-Darstellung von `andy-content-manager/tools-dashboard.php`. Das ist eine reine Navigationsmaßnahme, keine Löschung/Deaktivierung; **Direktzugriff unter WordPress live prüfen**.
- **Cockpit ist noch unvollständig**: `andy_jc_tools()` listet 11 historische Zielzugänge, aber die modernen Content-Composer-Submenüs (Academy, Perspectives, Language Routing/E2E, Asset & Language Lab, Editorial Workflow, Story Management) und Making of nicht vollständig; seine Versionsanzeige erfasst nur sechs alte Pluginlinien.
- Die inaktive ältere Content-Composer-Version **0.1.4** liegt zusätzlich zum aktiven **0.1.29** auf dem Server. Gleichnamige PHP-Funktionen machen eine gleichzeitige Aktivierung riskant; erst sichern, später auf Staging als Archivkandidat prüfen.

## 2. Zuständigkeitsmatrix nach Admin-Elternmenü

| Admin-Einstieg | Owner / wesentliche Menüs | Strategie |
|---|---|---|
| **ANDY Journal** | Cockpit `andy-journal-cockpit.php:83–84`; Home Composer `andy-home-composer.php:919–925`; Launch Control `andy-launch-control.php:50` | Haupt-Einstieg; ergänzen, keine Funktionen neu implementieren |
| **Werkzeuge** | Content Manager: Inventory `andy-content-manager.php:54`, DESIGN `design-import.php:139`, HOME-01 `home-import.php:106`, CONTENT-01/HOME-02 `publishing.php:79`, Navigation `navigation.php:36`, Header `content-header.php:45`; außerdem RGB `andy-rgb-pilot.php:29`, Editorial v2 `andy-journal-editorial-v2.php:22`, Integrator `andy-journal-integrator.php:38` | Neun redundante Links durch bestehenden reversiblen Cockpit-Modus harmonisieren; Funktionen/Hooks erhalten |
| **Beiträge** | Content Composer `class-andy-cc-admin.php:12`, Story Content Manager `includes/content-manager.php:4`, Asset & Language Lab `experience-mvp.php:23`, Language Routing `language-routing.php:24`, Language E2E `language-e2e.php:112`, Academy `academy.php:75`, Perspectives `perspectives.php:83`, Editorial Workflow `editorial-workflow.php:90`; Making of `andy-journal-making-of.php:70` | Native WP-Beiträge/Medien/Seiten belassen; neuere ANDY-Fachlinks im Cockpit gruppiert ergänzen |

Vorgesehene Cockpit-Rubriken: **Übersicht**, **Home & Design**, **Content & Redaktion**, **Sprache & Medien**, **Publication & Launch**, **System & Werkzeuge**.

## 3. Kritischer Staging-Blocker aus echtem Code

Die Migration nach `journal.andy-arena.com` wurde von der Projektleitung als im Backend, Editing und Frontend funktionsfähig bestätigt. Für die künftig geplante `staging-journal.andy-arena.com` sind dagegen mehrere **harte Hostbedingungen** vorhanden:

| Quellstelle | Harte Voraussetzung / Auswirkung |
|---|---|
| Cockpit `andy-journal-cockpit.php:12` | `andy_jc_allowed()` verlangt **exakt** `https://journal.andy-arena.com`; auf Staging entfällt das Cockpit-Menü |
| Launch Control `andy-launch-control.php:11` | `alc_allowed()` verlangt zusätzlich `andy_jc_allowed()`; fällt mit Cockpit aus |
| RGB Pilot `andy-rgb-pilot.php:10,16,53` | Festes `ARGB_SITE` **und** exakter HTTP-Host; Staging-RGB-Admin/Legacy-URL nicht nutzbar |
| Home Composer `andy-home-composer.php:935–955` | Öffentliche Home verlangt **exakten Journal-Host** sowie RGB bereit in Modus `content`; auf Staging derzeit nicht gleicher Home-Renderer |
| Älterer Content Manager `design-import.php:6` und Child-Module; Editorial/Integrator | Historische Testinstanz-Schutzbedingungen; nicht blind auf alle Hosts öffnen, da DESIGN-/HOME-/Publishing-Writes betroffen |

**Folge:** Ein unveränderter Staging-Klon würde seine Kernfunktion „identische Home und Werkzeuge“ nicht erfüllen. **Zuerst** verifizierten, umgebungsspezifischen Host-/Rollenvertrag entwickeln und lokal mit Production-/Staging-/fremden Hosts testen. Dabei Adminrechte, Staging-Passwortschutz und den bestehenden Produktionsschutz erhalten. Ein einfaches Löschen der Hostprüfung ist keine Lösung.

Weitere harte Abhängigkeit: `andy_hc_public_dependencies()` verlangt `argb_ready('060')` und `argb_standard_mode()==='content'`. Der RGB-Pilot-Route-Handler ist auf `template_redirect` Priorität **−100**, Home Composer auf **−90**. Beide Plugins/deren `wp_options`-Content nicht vor dem Klon deaktivieren oder löschen. Die RGB Originaldateien liegen in WP-Options, nicht vollständig im Plugin-ZIP.

## 4. Frontend- und Performance-Abgrenzung

- Home Composer: `wp_enqueue_scripts`, `template_redirect`; derzeit `DONOTCACHEPAGE` und `noindex,nofollow` auf ausgelieferter Home; öffentliche Indexierung und Seiten-Cache **später getrennt freigeben**.
- Content Composer: `parse_request`, `template_redirect`, `template_include`, `wp_enqueue_scripts` für native Artikel, DE/EN, Academy, Perspectives, Fight Night.
- Content Manager 0.4.8: `elementor/frontend/builder_content_data`, `wp_nav_menu_*`, Navigation-/Header-/Theme-Hooks und konditionale CSS/JS; nicht wegen Menüdopplungen deaktivieren.
- Making of 0.1.0: eigene Gabel-/Detailrouten über `parse_request`, `template_redirect`, `template_include`; benötigt Content Composer **≥0.1.28**.
- RGB Pilot: direktes Legacy-Asset-Routing; `content` erhält RGB-Unterseiten bei WordPress-Home. **Publication Control** muss später Direktzugriffe, REST, Search, Feeds, Sitemaps und Cache separat sperren. Ein fehlender Home-Teaser allein ist kein Zugriffsschutz.
- Cockpit/Launch Control: primär Admin; Menübereinigung ist UX-Arbeit, **kein gemessener Frontend-Performancegewinn**.

## 5. Sichere Folgeinkremente

1. **PRE-STAGING-01B1:** Host-/Umgebungsvertrag und reversible Anpassung der notwendigen Bestand-Plugins; Staging-/Production-Host, WP-Umgebung, Rollen und Routing testen, keine globalen Testschranken abschalten.
2. **PRE-STAGING-01B2:** Bestehendes Cockpit erweitern, nicht ersetzen. Moderne Content-/Language-/Making-of-Links und alle aktuellen Pluginstände aufnehmen; beide Content-Manager-Namen unterscheiden. Kompaktmodus reversibel beibehalten.
3. **PRE-STAGING-01C:** Publication-/Launch-Control-Vertrag auf Basis vorhandener Launch-Control-/Composer-/RGB-Codepfade: `internal`, `coming_soon`, `live`, DE/EN-Teaser, unveränderter WP-Publikationsstatus, Erstpublikationsgedächtnis, sichere Direktaufrufe.
4. **STAGING-01:** Erst nach vollständigem Backup klonen; WordPress-DB/Uploads separat, Staging geschützt; Live und Staging mit identischen Composer-Funktionen aber eigenen Freigabe-Optionen testen. Keine komplette Staging-Datenbank auf Live überschreiben.
5. **ARCHIV-01:** Erst danach alte inaktive CC 0.1.4, Integrator und Editorial v2 als Archivkandidaten in Staging prüfen. Live-Deaktivierung nur nach Abnahme. Reale Query-/Asset-/Cache-Messungen für Performance.

**Nicht Gegenstand dieses Commits:** Quellcodeänderung, Plugin-ZIP, automatische Veröffentlichung, Hostinger-Datenbankzugriff, Staging-Installation, Deaktivierung oder Cleanup. Die 22 statischen Tests beweisen nur die genannten Quellbedingungen.

**Making-of-Bezug:** [MO12 „Vom Werkzeug-Wildwuchs zur Betriebszentrale“](../content/ANDY-MAKING-OF-STORY-KATALOG-v0.1-2026-11-25.md#6-mo12--vom-werkzeug-wildwuchs-zur-betriebszentrale-25112026) kann nun von einer angenommenen Redundanz zu einem belegten Source-Audit fortgeschrieben werden: 22 Menüregistrierungen, zwei gleichnamige unterschiedliche Werkzeuge und ein zuvor vorhandener reversibler Konsolidierungsschalter.