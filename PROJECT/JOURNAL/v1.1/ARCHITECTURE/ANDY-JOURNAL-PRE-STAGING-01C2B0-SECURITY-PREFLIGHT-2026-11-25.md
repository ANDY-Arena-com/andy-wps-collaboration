# ANDY Journal · PRE-STAGING-01C2B0 – Security Preflight (read-only)

**Stand 25.11.2026 · Implementiertes lokales Update: ANDY Launch Control 0.2.1 → 0.2.2.**  
**Status:** isoliert getestet und WordPress-installierbar verpackt, **nicht** auf Hostinger installiert oder mit echtem WP-/Browser-/Cache-Zugriff abgenommen. **Keine öffentliche Freigabe, kein bereits wirksamer Zugriffsschutz.**

**Kontext:** [Staging/Live Single-Workspace-Sync-Vertrag](ANDY-JOURNAL-STAGING-LIVE-SINGLE-WORKSPACE-SYNC-CONTRACT-2026-11-25.md), [WHY-01A / 01C2A Policy-Kern](ANDY-JOURNAL-PRE-STAGING-01C2A-WHY-01A-RELEASE-2026-11-25.md), [System Map Foundation](ANDY-JOURNAL-SYSTEM-MAP-FOUNDATION-01-TECHNICAL-RELEASE-2026-11-25.md), [private Launch-Preview](ANDY-LAUNCH-PREVIEW-01-HOME-COMPOSER-0.1.40-2026-11-25.md).

## 1. Welche Grenze wir konkret gefunden haben

Launch Control 0.2.1 besitzt mit \`alc_policy_evaluate_post()\` einen **diagnostischen Entscheidungs-Kern**; er ist jedoch **kein** Schutz für bereits öffentliche WordPress-/HTML-/REST-/Mediendateien. Der Quell-Audit belegt unabhängige Auslieferungswege von Home Composer (privater Preview gesondert), Content Composer (native Posts, Fight Night, Academy, Perspectives, DE/EN-Routen), Making of, RGB Pilot sowie WP-Suche, REST, Feeds, Sitemap und Hosting-Caches.

**Die nächste öffentliche Funktion darf nicht allein aus einer positiven Planungsentscheidung abgeleitet werden.** Wir benötigen auf Staging echte Negativtests über **sämtliche** Wege. Ein extern geschütztes Staging ist dafür der sicherere Ort als ein Live-Server, auf dem wir probeweise Routen umschalten.

## 2. Inkrement 01C2B0 (tatsächlich implementiert)

Ein neuer **„Release-Sicherheit“**-Tab im bestehenden Launch Control (keine neue Plugininstanz, keine neuen öffentlichen Hooks, keine Options-/Post-/Meta-Writes). Der Tab:

- erkennt \`journal.andy-arena.com\` nur mit WordPress-Typ \`production\` als Live und \`staging-journal.andy-arena.com\` nur mit WordPress-Typ \`staging\` als Staging; alle abweichenden Kombinationen werden als Konflikt bzw. unbekannt ausgewiesen. **Der private Coming-Soon-Preview-Link ist keine Staging-Instanz.**
- zeigt die fünf geplanten Bereichsmodi und die Anzahl der vorläufigen Leseproben-Kandidaten, **ohne** deren rechtliche/öffentliche Freigabe zu behaupten.
- listet **15 öffentliche Angriffs-/Auslieferungsflächen** mit zuständigem Code und konkretem Abnahmerisiko. \`function_exists()\` bedeutet **Code geladen**, nicht Autorisierung; alle Wege bleiben als **OFFEN** markiert.
- liefert einen **maximal 50 Posts umfassenden** Admin-Diagnoseausschnitt mit lokalem WP-Status, ANDY-Bereich, DE/EN und \`alc_policy_evaluate_post()\`-Diagnose. **Ausschnitt ist nicht die komplette Bestandszählung**.
- zeigt deutlich ein **STOP-Gate**; kein Knopf kann daraus eine öffentliche Freigabe oder Staging-Freischaltung auslösen.

### Flächenmatrix

| Auslieferungsweg | Erforderliche Negativ-/Regressionstests |
|---|---|
| Home und private Coming-Soon-Preview | Header/Hero, Module, DE/EN, Admin-Rechte, anonyme 404 |
| Native WP-Post-Permalinks | Draft/Published, Rückzug, Sichtbarkeit, Sprachfassung, Direktzugriff |
| DE/EN-Sprachpartner | Alternate/hreflang, interne Übersetzung, Permalink |
| Fight Night | Archive, einzelne Posts, versteckte Inhalte |
| Academy | Virtuelle Gabelseite, Lektionen, einzelne Posts |
| Perspectives | Virtuelle Gabelseite, Themen und einzelne Posts |
| Making of | Eigenes Archive-/Detailrouting |
| RGB Legacy | HTML, CSS, JS, direkte HTML-/Asset-URLs |
| WP-Suche/Archive | Treffer, Snippets, Counts, Paginierung |
| WordPress REST | Posts, Search, Embeds, Custom Endpoints |
| RSS/Feeds | Kategorien, Tags, Autor-Feeds, Embeds |
| XML-Sitemaps & A–Z | Freigegebene URLs, Kategorien und Metadaten |
| Öffentliche Mediathek | Direkte Datei-URLs, unabhängig vom Poststatus |
| LiteSpeed, Hostinger, CDN & Browser-Caches | Cache-Ausnahme, Sprachen, Redirects, Invalidierung |
| System Map/Exporte | Nur freigegebene Knoten/Kanten, Belege und WHY; keine internen Counts/URLs |

## 3. Sicherheit, Tests und Rückweg

**Baseline:** Das zuvor erstellte, lokal geprüfte Launch-Control-Einzelplugin **0.2.1** – nicht der historische 0.1.0- oder 0.2.0-Stand. **Datei-Diff:** nur Hauptdatei geändert (Version, Include, Admin-Tab), zwei neue Dateien (Read-only-Modul und Kurz-README); alle sonstigen Dateien bytegleich.

**Tests:** 77/77 neue PHP-Assertions (Umgebungen, Konflikte, 15 Flächen, nur 50 Beispielposts, Admin-Gate, kein Formular, keine neuen Hooks, keine Schreibfunktionen) plus 116/116 bestehende 01C2A-Vertragstests bestanden. **5/5 PHP-Dateien Lint OK**, ZIP-CRC und WordPress-Pluginroot geprüft. **Keine reale Browser-/WordPress-/Staging-/REST-/Cache-Abnahme**.

| Chat-Artefakt, einzeln installierbar | SHA-256 |
|---|---|
| \`INSTALL-IN-WORDPRESS-ANDY-Launch-Control-0.2.2-SECURITY-PREFLIGHT-01C2B0.zip\` | \`60a42a5bf2f04e51c636c511331f4bb765ff3b94e5fa6361dfe582898864877d\` |
| \`ROLLBACK-ANDY-Launch-Control-0.2.1-SECURITY-PREFLIGHT-01C2B0.zip\` | \`9b64dc1ded203472dc87ea012eb1e61092ea7409b2c8b118f528e1786789394c\` |

Das Rollback-ZIP ist **bytegleich** mit dem zuvor ausgelieferten 0.2.1-Update. Binärpakete werden im Chat bereitgestellt, **nicht** in GitHub gespeichert.

### WordPress-Abnahme – nach Backup

1. **Zuerst tatsächliche aktive Pluginversion kontrollieren:** 0.2.2 setzt 0.2.1 als Basis voraus. Bei noch aktivem 0.2.0 zuvor den Releasepfad abstimmen; nicht blind überspringen.
2. Nach vollständigem Hostinger-Backup genau das **0.2.2-Einzel-ZIP** über WordPress installieren und bisherigen Ordner ersetzen.
3. Unter **ANDY Journal → Launch Control → Release-Sicherheit** den Bericht öffnen: Production korrekt erkannt; **alle 15 Auslieferungswege OFFEN**, kein öffentlicher Schalter.
4. Prüfen: **Publication & Coming Soon**, DE/EN-WHY, Kandidaten, die vier alten Pilot-Tabs und aktuelle DE/EN-Home einschließlich privater Launch-Preview sind unverändert. Keine WP-Post-Statusänderung.
5. Bei Problem das Original-0.2.1-ZIP wiederherstellen; keine automatischen Optionslöschungen.

## 4. Präzisierte technische Reihenfolge (Lernkorrektur)

| Phase | Ziel / Stop-Gate |
|---|---|
| **01C2B0 – jetzt** | Read-only Route-/Policy-Preflight, lokal getestet, WordPress-Abnahme offen |
| **STAGING-01 – danach** | Eigenständige, **extern geschützte** WP-Kopie, separate DB/Uploads, korrekter Host-/Environment-Vertrag und Datenbanksnapshot, Mail-/Cron-/API-Grenzen |
| **01C2B1** | Auf geschütztem Staging echte Sperradapter in bestehenden Plugins entwickeln und instrumentierte Testfälle für direkte Beiträge/Sprachen/Overviews/RGB implementieren |
| **01C2B2** | Suche, REST, Feeds, Sitemap, Medien und Caches kontrollieren; automatische Regression und anonymes Browser-/API-Negativtestprotokoll |
| **Public Release Gate** | Erst nach tatsächlicher End-to-End-Abnahme und ausdrücklicher Bestätigung Freigaben/Leseproben auf Live öffentlich wirksam machen |
| **ENVIRONMENT-SWITCH / SYNC-READ** | Zwei-Button-Bedienung und read-only Diff, anschließend selektiver Transfer statt Hostinger-Gesamt-Publish |

**Warum die Reihenfolge angepasst wird:** Ein vollständiger öffentlicher Zugriffsschutz lässt sich ohne eigenständiges Staging nicht verantwortbar live testen. Die bisherige „vor Staging fertigstellen“-Absicht gilt für die **Architektur, installierbare passive Bausteine und Sicherheitschecks**, nicht für das **Aktivieren produktiver Sperr-/Freigabe-Hooks**. Das ist eine bewusste, sicherere Präzisierung, kein heimlicher Architekturwechsel.

**Nicht vorhanden:** Staging-Datenbank, vollständiger Zugriffsschutz, Live-Synchronisation, öffentliche WHY-/Coming-Soon-Inhalte, Live-Publikation von Leseproben oder ein geprüfter System-Map-Export.