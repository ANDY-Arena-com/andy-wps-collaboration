# ANDY Journal – Staging/Live: Single Workspace & Selective Sync Contract

**25.11.2026 · Architektur- und Workflowentscheidung der Projektleitung · Status: verbindliches Zielbild, noch kein implementierter Zwei-Wege-Transfer.**

> **Arbeitsprinzip:** **Staging ist der normale redaktionelle und technische Arbeitsplatz. Live ist die freigegebene Publikationsumgebung.** Änderungen wandern nach ausdrücklicher Prüfung **selektiv Staging → Live**; umgekehrt können konkrete Live-Korrekturen **selektiv Live → Staging** zurückgeholt werden. Keine automatische Datenbank-Synchronisation, kein unkontrollierter „Publish staging“-Klick.

Bezug: [ENVIRONMENT-SWITCH-EDITOR-01](ANDY-JOURNAL-ENVIRONMENT-SWITCH-EDITOR-01-2026-11-25.md), [PRE-STAGING-Governance](ANDY-JOURNAL-PRE-STAGING-ADMIN-UND-LAUNCH-GOVERNANCE-2026-11-25.md), [WHY & Progressive Content Release](../content/ANDY-JOURNAL-WHY-PROGRESSIVE-CONTENT-RELEASE-01-2026-11-25.md), [System-Map-Foundation](../content/ANDY-JOURNAL-SYSTEM-MAP-FOUNDATION-01-2026-11-25.md).

## 1. Was „Single Source of Truth“ für ANDY bedeutet

„Eine Betriebszentrale“ und „ein redaktioneller Workflow“ bedeuten **nicht eine physisch gemeinsame WordPress-Datenbank**. Die Quellen der Wahrheit sind nach Objektart getrennt:

| Objektart | Autoritative Quelle | Transferregel |
|---|---|---|
| Plugin-Code, Releases und technische Dokumentation | GitHub / geprüfte Release-Artefakte | Getestete **identische Version** gezielt auf beiden Installationen ausrollen; kein Kopieren des Pluginzustands über die Datenbank |
| Neue redaktionelle Änderungen, neue Home-Module, DE/EN-Texte, WHY und Relationen | Staging als **führende Arbeitsumgebung** | Nach Review objektweise zur Live-Instanz übertragen |
| Öffentlich wirksamer Publikationsstand und Rückzüge | **Live** ist autoritativ für tatsächlich öffentlich Gewesenes | Nicht durch importierte Staging-Planungsstände überschreiben |
| WordPress-Posts / Medien | Jede WordPress-Installation lokal | Stabile fachliche Story-/Sprach-IDs und Medien-Mapping; **WP-Post-ID und Attachment-ID nie als globale Identität** |
| WHY, Launch-Plan, System-Map-Relationen | Bereits vorhandene Owner: Launch Control / Content Composer | Versionierter selektiver Export/Import der gespeicherten Objekte; **keine Kopie von `wp_options` insgesamt** |
| Zugangsdaten, Benutzer, Domain, WP-Environment, SMTP, Cron, Secrets, Cache | **Jeweilige Umgebung** | Niemals pauschal zwischen den Sites kopieren |

**Die bestehende Arena unter `andy-arena.com` bleibt unabhängig.** Die Journal-Live-Site ist `journal.andy-arena.com`. Die geschützte Staging-Site `staging-journal.andy-arena.com` ist weiterhin **geplant**, nicht als installiert und isoliert bestätigt.

## 2. Gewünschte Bedienoberfläche

Die Betriebszentrale bzw. der Home Composer zeigt in dieser Reihenfolge:

1. **Umgebung:** `Staging` / `Live`, eindeutiger Host-/Umgebungsstatus. Bis Staging real besteht, darf der Button **nicht** so tun, als sei die private Coming-Soon-Vorschau eine zweite WordPress-Installation.
2. **Sprache:** `DE` / `EN`, ausschließlich innerhalb der gewählten Umgebung.
3. **Ansicht:** `Bearbeiten` / `Home-Vorschau` / `Coming-Soon-Vorschau`.
4. Später **selektiver Transfer:** `Unterschiede prüfen` → `Übertragen` mit Ziel, Vorschau, Freigabe, Konfliktprotokoll und Rollback-Referenz.

**Implementierung zuerst:** Gleiche Cockpit-/Composer-Oberflächen auf beiden WordPress-Instanzen; Staging/Live-Auswahl navigiert zur jeweiligen WP-Admin-Adresse, überträgt nur Navigationskontext (ggf. Sprache/Ansicht), **keine Formulardaten, Nonces, Sitzungen oder Remote-Schreibrechte**. Dies ist ein sicherer „ein Bedienkonzept, zwei Instanzen“-Workflow, noch kein echter Inline-Ferneditor.

Ein wirklicher **Editor für zwei Sites innerhalb derselben geladenen Browserseite** benötigt später getrennt authentifizierte APIs, Umgebungsprüfung, revisionsgeprüfte Schreiboperationen, CSRF-Schutz, Rechte, Konfliktmanagement, Audit und Rollback. **Nicht** Voraussetzung für den Launch.

## 3. Selektive Transfers in beide Richtungen

### A. Staging → Live – der normale Freigabeweg

1. **Gegenstand auswählen:** genau benannte Plugin-Version, Home-Modul-Einstellung, Story-Sprachfassung, Gabelseiten-/WHY-Text, System-Map-Kante oder Medienobjekt.
2. **Diff gegen Live:** Identität, tatsächliche Live-Fassung, Versions-/Revisionshash, Änderungszeit, Sprachpartner, Medien/Links und Veröffentlichungsstatus **zuerst lesen**.
3. **Einzelprüfung:** Redaktion bzw. Administrator bestätigt pro Objekt und Sprache. Konflikte stoppen den Vorgang; niemals stillschweigend „zuletzt gespeichert gewinnt“.
4. **Gezielt übernehmen:** Inhalte/IDs/Medien-Referenzen korrekt zuordnen, fehlende Abhängigkeiten nur explizit mitnehmen; keine neue WP-Post-ID als kanonische Story-ID setzen.
5. **Publikationsfreigabe bleibt getrennt:** Ein Staging-Entwurf bleibt in Live Entwurf. `coming_soon` oder WHY-`prominent` macht keinen Artikel automatisch öffentlich. Publikation/Preview-Leseproben benötigen separat geprüfte 01C2B-Sicherheit.
6. **Nachkontrolle:** Sprache, Darstellung, direkte URLs, Suche, REST, Feeds, Sitemap und Cache nach Zieländerung prüfen; Zielbackup/Revision und Transfer-Audit sichern.

### B. Live → Staging – gezielte Rückübernahme

- Für akute Live-Textkorrekturen, veröffentlichte Ist-Stände oder spezifische Abweichungen: gezielte Objekte per **demselben Diff- und Konfliktmechanismus** zurückholen.
- **Kein** blindes Zurückkopieren der Live-Datenbank über parallel weiterentwickelte Staging-Inhalte.
- Die **erste Kopie Live → Staging** ist eine kontrollierte **Bootstrap-Ausnahme** nach Vollbackup und bevor Staging eigenständig bearbeitet wird. Nach diesem Moment wird synchronisiert **nur selektiv**, oder ein kompletter Reset muss ausdrücklich alle betroffenen Staging-Änderungen benennen und bestätigen.

### C. Unterschiede nach Objektart

| Transfer | Erste realistische Methode | Nicht verwenden |
|---|---|---|
| PHP/JS/CSS-Plugin-Code | Versionierte ZIPs / GitHub-Release mit Dateivergleich | Hostinger-Staging-Publish zum Nachziehen von Code und DB zusammen |
| WordPress-Artikel, DE/EN-Stories | Export/Import nach stabiler Story-/Locale-ID, Revision, Status, Konflikt | Rohes `wp_posts`-Dump über laufende Live-DB |
| Medien | Datei + Metadaten/Alt-Text/Provenienz, Attachment-ID-Mapping | Nummerngleiche Post-/Media-IDs voraussetzen |
| Home-/WHY-/Launch-Konfiguration | Kontrollierte, schema-versionierte objektbezogene Optionen | Gesamte `wp_options` überschreiben |
| System-Map-Relationen | Relation-ID + Revision + autorisierte Endpunkte nach Registry | Kanten-IDs ohne Endpunkt-/Sprachprüfung importieren |
| Veröffentlichungshistorie / Rückzüge | Explizites Merge und geschütztes Audit | Staging-Flags übernehmen und Live-Historie verlieren |

## 4. Hostinger-Gefahr und Sicherheitsgates

Die Hostinger-Funktion **„Publish staging“** kann die Dateien **und die Datenbank** der Live-Site durch die Staging-Version ersetzen, statt einzelne redaktionelle Änderungen zu mergen. **Daher kein pauschales Hostinger-Gesamt-Publish** bei divergierenden Inhalten. Vor jedem Transfer Backup, klare Quell-/Zielidentität, Diff, Freigabe und Rollback-Plan. Prüfen, welche Hostinger-Optionen in der konkreten Installation tatsächlich verfügbar sind, bevor wir sie in den Workflow übernehmen.

Die zwingende technische Priorität bleibt **PRE-STAGING-01C2B**: korrekte Zugriffsentscheidung durchsetzen für Home, Gabelseiten, native Posts, DE/EN-Partner, RGB-Legacy-Routen, Suche, REST, Feeds, XML-Sitemaps und Cache/Medien. Ein eingebauter „Sync“-Knopf darf **keinen** Freigabe- oder Datenschutzschutz umgehen. `noindex` ist keine Zugriffssperre. **Keine automatische Publikation.**

## 5. Geordnete Umsetzung

| Phase | Ergebnis | Stand |
|---|---|---|
| **SYNC-CONTRACT-01 (dieses Dokument)** | Fachliche Ownership, stabile Objekt-IDs, Transfer-Gates, UI-Ziel | **Dokumentiert; noch kein Sync-Code** |
| **PRE-STAGING-01C2B** | Vollständige Zugriffskontrolle / Sicherheitstest | Ausstehend; Voraussetzung für öffentlich wirksame Freigaben |
| **STAGING-01** | Geschützter eigenständiger WP-Klon mit eigener DB, Environment-/Host-Vertrag, validierten DE/EN-Editoren | Noch nicht bestätigt |
| **ENVIRONMENT-SWITCH-01** | Gleiche Bedienoberfläche, bewusste Navigation zwischen WP-Instanzen, keine Remote-Writes | Geplant |
| **SYNC-READ-01** | Read-only Inventur-/Objekt-Diff Staging↔Live über stabile fachliche IDs | Geplant; sicherer erster Sync-Inkrement |
| **SYNC-TRANSFER-01** | Selektiver, revisionsgeprüfter Import/Export und Protokoll in eine Richtung, dann geprüfter Rückweg | Später, nach E2E und Berechtigungsabnahme |
| **RELEASE-CHECK-01** | Ziel-Smoketest, Cache-Invalidierung, Rolling Handoff und Rollback | Vor jedem Live-Transfer |

## 6. Abnahme

- Echte getrennte Datenbanken/Medien und geschützte Staging-Instanz; Buttons zeigen korrekte Hosts.
- Eine Änderung an einer DE/EN-Home-Einstellung auf Staging verändert Live **nicht**, bis sie explizit freigegeben/übertragen wird.
- Ein auf Live korrigierter Text kann zurückgeführt werden, **ohne** parallele Staging-Arbeit zu verlieren.
- Alte WP-IDs und Medien-IDs werden **nicht** als globale Identitäten verwechselt.
- Kein Transfer von Secrets/Domain-/Staging-Flags/WordPress-Benutzern oder ungewollten Beitragsstatus.
- Editorial Withdrawn, Sprachfreigaben und WHY-hidden bleiben geschützt; Beziehungen/Map/Export nur autorisiert.
- Diff, Freigabe, Zielrevision und Rollback-Referenz für jede reale Übertragung nachvollziehbar.
- Keine gleichzeitige automatische Zwei-Wege-Replikation und kein impliziter Publikationsstatuswechsel.

**Status dieses Vertrags:** Architektur dokumentiert; weder ein installiertes Transferplugin noch eine produktive Synchronisation ist damit behauptet.

## Iststand der echten Staging-Instanz (25.11.2026)

Hostinger hat inzwischen **`staging.journal.andy-arena.com`** als echte eigenständige WordPress-Installation mit separater Datenbank bestätigt; WordPress `home`/`siteurl` sind auf diesen Host eingestellt und `WP_ENVIRONMENT_TYPE=staging` wurde ausschließlich dort gesetzt/verifiziert. **Der ältere Planname `staging-journal.andy-arena.com` in früheren Abschnitten ist historisch und nicht die aktive Ziel-URL.** Externer, auch für REST/Uploads/Cache wirksamer Anonym-Schutz noch nicht separat getestet; ausgehende WordPress-/direkte SMTP-/API-Mailer und WP-/System-Cron noch nicht vollständig isoliert. Bis zum erfolgreichen Side-Effect-/Zugriffstest keine automatisierten oder nicht reversiblen Staging-Experimente. **Kein** pauschaler Staging→Live-Publish; selektiver Diff-/Transfervertrag bleibt unverändert.

