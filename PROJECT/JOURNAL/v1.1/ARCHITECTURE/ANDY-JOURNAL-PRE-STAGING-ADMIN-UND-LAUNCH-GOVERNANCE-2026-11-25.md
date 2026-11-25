# ANDY Journal – PRE-STAGING-01: Admin-Harmonisierung, Launch & Publication Governance

**Beschlossen am:** 25.11.2026 · **Status:** Architektur- und Betriebsentscheidung der Projektleitung; Implementierung, Live-Audit und Freigabe offen.  
**Bezug:** [WP-ARCH R0.5](WP-ARCHITECTURE-R0.5.md), [Systemstatus](../STATUS.md), [Plugin- und Paketregister](../ANDY-JOURNAL-PLUGIN-UND-PAKETREGISTER-2026-11-22.md), [Making of / MO12](../content/ANDY-MAKING-OF-STORY-KATALOG-v0.1-2026-11-25.md#6-mo12--vom-werkzeug-wildwuchs-zur-betriebszentrale-25112026).

> **Leitentscheidung:** **Eine ANDY-Journal-Betriebszentrale, vorhandene Fachfunktionen behalten, nur eine redaktionelle Contentquelle, Live und Staging mit derselben Website-Architektur.** Kein zweiter Home-Builder und keine Parallelverwaltung von Beiträgen. Änderungen schrittweise, reversibel und erst nach Quell-/Hostinger-Prüfung.

## 1. Anlass und abgeglichener Stand

Die Projektleitung bestätigte am 25.11.2026, dass die Umstellung der WordPress-Site auf **journal.andy-arena.com** im Backend, Editing und Frontend funktioniert. **andy-arena.com** bleibt die eigenständige Arena-HTML-Site. Die unabhängige, geschützte Testumgebung **staging-journal.andy-arena.com** ist Zieladresse, **nicht als bereits eingerichtet oder isoliert bestätigt**.

Die bereitgestellten WordPress-Screenshots und die aktive Pluginliste vom 25.11. dokumentieren **20 Plugin-Einträge, davon 18 aktiv und 2 inaktiv**. Dies ist ein **Nutzer- und UI-Befund, kein vollständiges aktuelles Quell- oder Laufzeit-Audit**. Ausgewählte Stände:

| Bestandteil | Angezeigter Stand | Entscheidung |
|---|---|---|
| ANDY Journal Home Composer | **0.1.38**, aktiv; anderer Admin-Screenshot beschriftet **0.1.37** | Bestehenden Home-Renderer erhalten; Versionsdiskrepanz im tatsächlichen Admin-/Code-Stand prüfen |
| ANDY Journal Content Composer | **0.1.29**, aktiv; zusätzlich **0.1.4, inaktiv** | Aktive Version beibehalten; alten Parallel-Eintrag sichern und Slug/Pfad prüfen; noch keine Löschfreigabe |
| ANDY Content Manager | **0.4.8**, aktiv | Bestehende Module, Publishing, Theme- und Integrations-Hooks erhalten; keine Überschneidung blind eliminieren |
| ANDY Journal Cockpit | **0.2.0**, aktiv | **Ein zentraler Admin-Einstieg**; vorhandene 0.2.0-Navigationskonsolidierung zuerst testen |
| ANDY Launch Control | **0.1.0**, aktiv | Aktuell private Sitemap-/Content-/QA-Planung, **noch keine belegte produktive Publication Control**; Erweiterungsfähigkeit quellenprüfen |
| ANDY RGB Content Pilot | **0.6.3**, aktiv | Legacy-Routen und Originalmodule bis zur geprüften Migration schützen |
| ANDY Journal Integrator | **0.2.5**, aktiv | Experimenteller/diagnostischer Bestand; Archivkandidat **erst nach Staging- und Abhängigkeitsprüfung** |
| ANDY Editorial Sitemap v2 | **0.1.0**, aktiv | Historischer Pilot; Archivkandidat erst nach Bestands- und Quellenprüfung |
| ANDY Journal Making of | **0.1.0**, aktiv | Bestehendes eigenständiges Add-on; GitHub-Katalog dokumentiert auch 0.1.1, **nicht als installiert behaupten** |
| Aculia, WpSection, Elementor | aktiv | Theme-/Layout-Abhängigkeiten schützen |
| LiteSpeed Cache | **7.9.4**, aktiv | Erst Cache-/Asset-/Query-Messung, dann gezielt optimieren |
| Contact Form 7 | **6.2.6, inaktiv** | Kein ungeprüfter Aktivierungsbedarf |
| MC4WP / Hostinger Reach / Hostinger Tools und weitere | aktiv | Nutzung/Notices/Abhängigkeiten separat prüfen; keine pauschalen Deaktivierungen |

Der Admin bietet derzeit überlappende Zugänge unter **ANDY Journal**, **Beiträge** und **Werkzeuge**. Die Cockpit-Werkzeugzentrale zeigt wiederverwendete Funktionen; ihre Kacheln sind nicht gleichbedeutend mit zusätzlichen Plugins. Im Menü heißen zudem zwei fachlich verschiedene Komponenten **ANDY Content Manager**. Unklare Bezeichnungen sind eine **Navigations- und Zuständigkeitsfrage**, nicht automatisch doppelte Laufzeitlogik.

## 2. Verbindliche Ziel-Zuständigkeiten

| Einheit | Autoritative Rolle | Nicht neu bauen / nicht überschreiben |
|---|---|---|
| **ANDY Journal Cockpit** | **Eine sichtbare ANDY-Betriebszentrale:** Systemstatus, Versionen, Links und Gruppen **Home & Design**, **Content & Redaktion**, **Sprache & Medien**, **Publication & Launch**, **System & Werkzeuge** | Kein zweiter Importer, kein Frontend-Renderer, keine Kopie fremder Options/Posts |
| **Home Composer** | Bestehende DE/EN-Home, Reihenfolgen, Module, Designwerte, Anzeigeadapter | Keine separate Coming-Soon-Home; keine neue Modulengine |
| **Content Composer** | Redaktionelle Posts, Themen-/Template-/Sprachmetadaten, Gabelseiten, Content-Adapter | Keine neue WP-Post-Datenbank und kein Auto-Publish durch Bereichsschalter |
| **Launch Control / Publication-Schnittstelle** | Perspektivisch zentral: Freigabestatus, Coming-Soon-Inhalte, Audit, QA. **Vor Implementierung zuerst Launch-Control-0.1.0-Quelle und öffentliche Route prüfen.** | Kein unbelegtes „bereits implementiert“; kein paralleles zweites Launch-Plugin, wenn sichere Erweiterung möglich |
| **Content Manager 0.4.8 / ältere Fachwerkzeuge** | Native Theme-/Publishing-/Inventory-/Design- und Diagnosefunktionen, soweit tatsächlich genutzt | Keine Hook-/Template-Abschaltung allein wegen doppelter Menüpunkte |
| **RGB Pilot / Originalinteraktionen** | Geschützte Legacy-Inhalte/-Routen bis zur nachweisbaren Ablösung | Kein unbeabsichtigtes Abschalten von direkten RGB-Assets/Playern |

**Benennungen im Admin schärfen:** den älteren eigenständigen Content Manager z. B. **System & Inventory**, das fachliche Content-Composer-Modul z. B. **Story & Content Management** nennen – **Labels erst nach Slug/Callback-Audit ändern**, nicht die Funktionen. Native WP-Menüs Beiträge, Medien und Seiten bleiben verfügbar.

Der Cockpit-0.2.0-Release dokumentiert bereits einen **standardmäßig abgeschalteten, reversiblen Schalter** zum Verbergen redundanter Einträge unter „Werkzeuge“ sowie der doppelten Werkzeugübersicht. **Diesen vorhandenen Mechanismus vor neuer Menülogik überprüfen und in Staging regressionsprüfen.** Sichtbare Menülinks ausblenden ist *nicht* Plugin deaktivieren und *nicht* Daten löschen. Berechtigungs-/Direkt-URL-Zugriff erhalten.

## 3. Einheitliche Home: Intern, Coming Soon, Live

**Designentscheidung:** Live und Staging verwenden **dieselben Home- und Content-Composer, dieselben DE/EN-Layouts und Module**. Unterschiede entstehen aus **getrenntem Daten-/Freigabezustand**, nicht aus zwei Home-Implementierungen.

| Bereichszustand | Home | Gabelseite | Content / Direktzugriff |
|---|---|---|---|
| **Intern** | Modul bzw. Themenkarte nicht öffentlich | Nicht öffentlich | Nur Berechtigte sehen Vorschau |
| **Coming Soon** | Originalmodul mit redaktionell gepflegtem DE/EN-Teaser und Bild | Freigegebene Bereichsvorstellung | Nicht freigegebene Beiträge gesperrt |
| **Live** | Originalmodul mit freigegebenen echten Inhalten | Dynamische Overview mit Filter/Counts | Ausschließlich explizit veröffentlichte und im Bereich freigegebene Beiträge |

Optional später: **Teilweise live** als *abgeleitete Anzeige* statt viertem widersprüchlichem Status. **Nicht jedes Plugin** braucht eine Coming-Soon-Funktion; **öffentliche ANDY-Module/Bereiche** beziehen ihren Anzeigezustand aus *einer* zentralen Steuerung. Die Gabelseite und der Home-Teaser dürfen nicht unabhängig falsche Verfügbarkeiten melden.

**Publikationsgedächtnis:** Bereichs-Freigabe ist von \`post_status\` getrennt. Dauerhaft und revisionsfähig erfassen, ob/wann ein Beitrag erstmals öffentlich war, wann er pausiert wurde und ob er *redaktionell zurückgezogen* wurde. **Neue Entwürfe werden nie durch Bereichsaktivierung veröffentlicht; zurückgezogene Beiträge nie ungefragt reaktiviert.** Bei historisch unbekannten Altfällen „ungeklärt“ statt „nie publiziert“ annehmen. Ein/aus betrifft Anzeige und Zugriff, nicht automatische Statusmutation.

Prüfen: Home, Gabel-/Sub-Gabelseiten, direkte Permalinks, WP-Suche, REST, Feeds, XML-Sitemaps, Sprachpartner/DE-EN, Preview-Rechte, CDN/LiteSpeed-Cache sowie alte RGB-Routen. Eine „versteckte Karte“ allein schützt keinen bereits öffentlichen Inhalt.

## 4. Zielarchitektur

\`\`\`mermaid
flowchart TD
    R["Redaktion: native WP-Posts / DE+EN"]
    R --> C["Content Composer: Templates, Metadaten, Sprache"]
    C --> O["Gabelseiten: dynamische Overviews"]
    O --> H["Home Composer: bestehende Module"]
    L["Publication & Launch Control: Freigabe, Coming Soon, Historie"] --> C
    L --> O
    L --> H
    K["Journal Cockpit: EIN Admin-Einstieg"] --> L
    K --> C
    K --> H
    K --> X["Bestehende Fachwerkzeuge / Diagnose / RGB"]
\`\`\`

**Entwicklungsweg:** GitHub als Projektgedächtnis → geprüftes Handoff/Quellstand → lokales Plugin-ZIP → **geschütztes Staging mit eigener Datenbank** → QA/DE-EN/Mobil/Sicherheit → ausdrückliche Freigabe → gezieltes Deployment auf Live → Monitoring/Abnahme → GitHub + Rolling Handoff. **Kein vollständiges Hostinger-Staging-Publish ohne separates Datenbank- und Inhalts-Diff-/Backup-Gate**, da Live-Inhalte sonst überschrieben werden können.

## 5. PRE-STAGING-01: Reihenfolge und Stop-Gates

1. **Bestand sichern:** tatsächliche installierte Plugins/Ordner/Versionen, Options, Hooks, relevante WP-Daten und Backups. UI-Befund gegen Hostinger-Quelle und aktuelle Plugin-ZIPs prüfen. Home-Composer-Anzeige 0.1.37/0.1.38 sowie zwei Content-Composer-Einträge klären.
2. **Admin-Harmonisierung planen:** vollständige Menü-/Callback-/Capability-/Besitzmatrix; Cockpit-0.2.0-Schalter und Rollback in einer sicheren Vorschau testen. Erst danach eindeutige Labels, Gruppen und eine Admin-Landingpage.
3. **Publication-Control-Vertrag implementieren** nach Quellprüfung von Launch Control 0.1.0, RGB 0.6.3, Content Manager 0.4.8 und Composern. Fail-closed für unbekannte Freigaben, separate DE/EN-Teaser, Historie, sichere Routen. Keine Duplikation einer schon vorhandenen Funktion.
4. **Same-Home-Launch-Modus** auf vorhandenen Modulen in sicherem, standardmäßig nicht öffentlich schaltendem Zustand; keine neue Home. Produktions- und Staging-Freigaben später separat konfigurieren.
5. **Lokale Regression und WordPress-Backup**; nur geprüfte, reversible Änderungen auf dem bestehenden Journal. Danach **erst** die unabhängige Staging-Kopie erstellen, Schutz/DB-Trennung/Noindex/Cron/E-Mail/Cache prüfen.
6. **Auf Staging experimentell archivieren**, was nach Quellen-/Abhängigkeitsprüfung entbehrlich scheint (Integrator, Editorial v2, alter CC 0.1.4); auf Production keine Entfernung ohne Freigabe und Rückweg.

**Performance:** 20 Plugins bedeuten nicht 20 Frontendbelastungen. Erst Query-/Asset-/Hook-/Cache-Profiling auf Staging und Live in vergleichbarem Zustand; Menübereinigung allein ist keine Geschwindigkeitsoptimierung. LiteSpeed Cache und aktuelle noindex/nocache-Entwicklungsregeln vor Live-SEO-/Cache-Freigabe prüfen.

## 6. Nicht-Ziele, Nachweise und Veröffentlichung

- **Kein** in diesem Dokument erstelltes Plugin, keine Installation, kein Löschen, keine Produktivschaltung, kein automatisches Veröffentlichen.
- **Keine** neue Home, kein Theme-/Elementor-Overwrite, kein Aufgeben vorhandener Academy-/Perspectives-/Making-of-/RGB-Inhalte.
- Kein Rückschluss aus einem Pluginlisten-Screenshot auf vollständige Hooks, Performance, Zugriffsschutz oder vorhandene WP-Objekte.
- Eine vollständig gleiche Pluginversion beider Umgebungen bedeutet **nicht** identische redaktionelle Daten oder Produktionsfreigaben.
- Der hier beschlossene **Zielzustand** wird erst nach Implementierung, isolierten Tests, WordPress-Integration, Sicherheitsprüfung und Projektleitungs-Abnahme als **betriebsbereit** bezeichnet.

**Redaktionelle Einordnung:** Diese Entscheidung ist zugleich ein *Making-of*-Fall zu Governance und human–AI coordination: [MO12](../content/ANDY-MAKING-OF-STORY-KATALOG-v0.1-2026-11-25.md#6-mo12--vom-werkzeug-wildwuchs-zur-betriebszentrale-25112026).