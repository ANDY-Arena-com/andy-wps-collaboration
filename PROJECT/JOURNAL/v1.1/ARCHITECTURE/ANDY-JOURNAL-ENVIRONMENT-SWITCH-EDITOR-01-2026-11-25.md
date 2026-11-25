# ANDY Journal – ENVIRONMENT-SWITCH-EDITOR-01

**25.11.2026 · UI-/Architekturentscheidung aus der Live-Home-/Coming-Soon-Vorschau · Status: Konzept, noch keine Plugin-Implementierung, kein Domain-/Staging-Test.**

**Anlass:** Beim real installierten Home Composer **0.1.40 LAUNCH-PREVIEW-01** sieht die Projektleitung in der Administration aktuell drei große nebeneinanderliegende Links **„Aktuelle Home“, „Coming Soon · DE“, „Coming Soon · EN“** sowie darunter die vorhandene Sprachwahl „DE · Design & Inhalte / EN · Inhalte“. Gewünscht wird statt dieser Mischung ein **eindeutiger Selektor nach Umgebung: „Staging“ versus „Live“**. Darunter soll die jeweilige **DE/EN-Auswahl** und die zur Umgebung gehörende Home-/Modulbearbeitung erscheinen: *„So könnte ich quasi zwei Seiten in einem View editieren.“* Die visuelle Anregung ist ein Konzeptinput, keine Freigabe für Remote-Schreibzugriffe oder Live-Datenänderungen.

## 1. Verbindliche Unterscheidung von drei Zuständen

| Dimension | Werte | Aufgabe |
|---|---|---|
| **WordPress-Umgebung** | **Staging** / **Live** | Zwei eigenständige WordPress-Installationen mit unabhängigen Datenbanken, Uploads, WP-Optionen, Rollen, Backup- und Freigabeständen |
| **Sprache** | **DE** / **EN** | Lokalisierte Home-/WHY-/Coming-Soon-Inhalte und Sprachpartner innerhalb der **gewählten** Umgebung |
| **Ansicht/Veröffentlichungsplanung** | Aktueller öffentlicher Inhalt / **Coming-Soon-Vorschau** / später je Bereich internal, coming_soon, live | Darstellung/Freigabestatus innerhalb derselben Umgebung; **kein Synonym für Staging/Live** |

**Aktueller Iststand:** `journal.andy-arena.com` funktioniert laut Nutzer und beherbergt Home Composer 0.1.40 mit privater Coming-Soon-Vorschau. Die Domain `staging-journal.andy-arena.com` ist ein **geplanter** Host, noch **nicht** als separate, geschützte WordPress-Installation und Datenbank bestätigt. Der bestehende private Coming-Soon-Preview-Link auf Live ist **kein Staging**. Ihn weder in Code noch im UI als echte Staging-Installation ausgeben.

## 2. Bedienziel

```text
ANDY Journal · Home Composer
┌──────────────────────────────────────────────────────────────────┐
│ UMGEBUNG:   [ STAGING ]  [ LIVE ]   → klar erkennbarer Iststand    │
│ SPRACHE:    [ DE ]  [ EN ]                                        │
│ ANSICHT:    [ Home bearbeiten ]  [ Coming Soon ansehen ]          │
├──────────────────────────────────────────────────────────────────┤
│ Gewählte Umgebung: URL · WP-Environment · Version · Freigabeinfo  │
│ Darunter: bestehende Module, Teaser, WHY und Editoren dieser Site │
│ [Speichern für diese Umgebung] · getrennte Vorschau & Historie     │
└──────────────────────────────────────────────────────────────────┘
```

- Die existierenden Composer, Modul-Editoren, Optionen, nativen WP-Posts, Sprachregister und Launch-Control-Felder **unverändert als Eigentümer** belassen. Keine geklonten Editor-Engines oder zweite Home.
- Die DE/EN-Sprachauswahl wirkt **innerhalb** des gewählten Standorts und darf nicht unbemerkt die Umgebung wechseln.
- **Live** deutlich als öffentlich wirksame Umgebung kennzeichnen. Speichern im aktuellen Home Composer kann unmittelbar öffentliche Änderungen auslösen; ein zukünftiger Live-Edit-Schutz (warnende Bestätigung/Revisionsvergleich) ist sinnvoll, aber **noch nicht implementiert**.
- **Staging** nach tatsächlicher Einrichtung mit denselben Plugins/Layouts, **eigenen** Daten/Optionen/Assets und zunächst nur Admin-Preview bzw. externem Site-Passwortschutz.
- Coming-Soon-Vorschau bleibt eine **separate Ansicht** in der gewählten Umgebung; ein Preview-Button veröffentlicht keine Inhalte.

## 3. Technische Realisierbarkeit, ohne die Datenhaltung zu vermischen

**Schritt A – einfach und robust, nach Staging-Klon:** Beide Installationen haben dieselbe Cockpit-/Composer-Oberfläche. Der Umgebungsselektor navigiert zur **passenden WP-Admin-URL**, überträgt nur Navigation/Sprachauswahl/Ansicht als URL-Parameter und **keine Inhalts- oder Formulardaten**. Jeder Site-Editor schreibt ausschließlich in die **eigene** WordPress-Datenbank. Benutzer müssen ggf. bei beiden WordPress-Instanzen separat angemeldet sein. Die einheitliche Bedienlogik vermittelt „ein View“, technisch findet jedoch ein **kontrollierter Sitewechsel** statt. Keine iframes, keine Cross-Site-CSRF oder Remote-DB-Abfragen.

**Schritt B – echte Inline-Remote-Bearbeitung (optional, später):** Für Staging und Live innerhalb **einer tatsächlichen Browserseite** wären eigene, minimal berechtigte, beidseitig abgesicherte API-Endpunkte mit Session-/Auth-Management, Nonces/CSRF-Schutz, Revisions- und Konfliktkontrolle, erzwungener Zielumgebung, getrennten Asset-IDs, Audit und Rollback nötig. Keinen solchen Zugriff durch ein URL-Label, iframe oder einen ungeprüften REST-Aufruf simulieren. **Nicht PRE-STAGING-Launch-Voraussetzung.**

**Schritt 0 – vor Staging-Klon:** UI-Konzept und rein **navigationelle** Vorbereitungen sind möglich; aber keinen funktionierenden Staging-Tab vortäuschen oder mit Production-Optionen füllen. Bis zur echten Umgebung ausdrücklich `Staging · noch nicht eingerichtet` zeigen. Die vorhandenen Links `Aktuelle Home`, `Coming Soon DE/EN` bleiben als sichere lokale Optionen, bis ihr Ersatz vollständig abgenommen wurde. **Kein zusätzlicher „Staging-Konfigurationssatz“ in der Production-Datenbank als vermeintliche getrennte Website.**

## 4. Sicherheit / Abnahme

- Nach Klon für `staging-journal.andy-arena.com`: `WP_ENVIRONMENT_TYPE=staging`, korrekter Host-/WP-URL-Vertrag, getrennte Datenbank, geschützter Login und externer Zugriffsschutz (Noindex genügt nicht).
- Navigation aus Live zu Staging und umgekehrt: keine Übernahme von Session-Token, Bearbeitungsformularen, Nonces oder WP-Medien-IDs als global eindeutige IDs; Anzeigen eindeutiger Hostnamen/Status.
- Innerhalb beider Sites: DE↔EN-Wechsel mit eigenen Inhalten; bestehende Home/Coming-Soon-Ansichten, Header/Hero, Modulreihenfolgen und Launch-Control-Planungsdaten bleiben korrekt.
- Formularspeicherung auf einer Site ändert die andere **nicht**. Kein automatischer Staging→Live-Abgleich; spätere Promotion benötigt eigenes Paket-/Diff-/Backup-/Freigabegate.
- Freigabeschutz für native Posts, RGB-Assets, Suche, REST, Feeds, Sitemaps und Cache bleibt **PRE-STAGING-01C2B**. Ein Umgebungs-Selektor ersetzt dieses Gate nicht.
- Beim Ausfall/Fehlen von Staging wird keine private Vorschau als produktiver Staging-Zustand ausgegeben. Rückschaltbar auf die vorhandene 0.1.40-Linknavigation.

## 5. Einordnung und Reihenfolge

**Jetzt:** UX-Ziel dokumentieren und als neues Cockpit-/Home-Composer-Inkrement aufnehmen, ohne an der Live-Publikationslogik zu drehen. **Technischer nächster Schritt:** 01C2B-Sicherheitsadapter unter geschütztem Test, Staging-Klon und Abnahme; danach den einfachen Zwei-Site-Navigator einführen. Optional schon vorher eine *passive* Anzeige des aktuellen Standorts vorbereiten.

**Making-of-Lernpunkt:** Die Projektleitung fordert eine räumlich verständliche Oberfläche statt drei technisch unterschiedlich motivierter Links: Nicht Funktionen/Sprachen/Umgebungen vermischen; die visuelle Metapher muss die tatsächliche Datentrennung abbilden, nicht nur suggerieren.

## Implementierungsnachtrag – Home Composer 0.1.41 / 25.11.2026

**Status:** Ein reales, einzelnes WordPress-Update **Home Composer 0.1.40 → 0.1.41 (PIPPI-ENVIRONMENT-SWITCH-01)** wurde auf Grundlage des vollständigen vorherigen 0.1.40-ZIPs gebaut. **Lokal geprüft, noch nicht in Hostinger installiert oder browserseitig abgenommen.**

Der bestehende Home-Composer-Admin zeigt jetzt die gewünschte Reihenfolge **1. Umgebung (Staging / Live), 2. Sprache (DE / EN), 3. Ansicht (Bearbeiten / Home-Vorschau / Coming Soon · privat)**. Die zwei großen Umgebungsbuttons ersetzen die Home-Composer-Ansicht mit drei konkurrierenden Preview-Links. Die früheren lokalen Preview-URLs bleiben erhalten. Der Launch-Control-Admin verlinkt kompakt in den Home Composer, anstatt nochmals drei große Vergleichsbuttons zu zeigen.

**Live solange Staging fehlt:** Klick auf **Staging** öffnet im selben Home-Composer-Admin eine explizit gekennzeichnete **nicht editierbare Zwischenansicht**. Der eigentliche Live-Editor wird dort **nicht** ausgeliefert, damit keine Production-Daten fälschlich unter „Staging“ bearbeitet werden. Beim Rückwechsel auf Live bleiben die echten DE/EN-Editoren/gespeicherten Module wie vorher. **Staging ist weiterhin nicht bestätigt eingerichtet.**

**Nach dem tatsächlichen geschützten Klon:** Der Administrator kann unter **Staging-Verknüpfung** den festen Ziel-Link `https://staging-journal.andy-arena.com/wp-admin/admin.php?page=andy-home-composer` manuell einschalten (Option `andy_hc_stage_link_ready_v01`, Default **aus**, separate Bestätigungscheckbox/Nonce/Adminrecht). Diese Bestätigung ist **keine technische Remote-Sicherheitsprüfung**. Auf der echten Staging-Instanz, die bereits durch die bisherige Host-/WP-Umgebungskontrolle erkannt wird, ist Staging aktiv und Live verlinkt zum getrennten Live-Backend. **Keine** Remote-API, Cross-Site-Datenbank, Übertragung, Synchronisation oder Statusänderung durch die Buttons.

**Quelländerungen:** drei vorhandene Dateien geändert (Haupt-PHP, Admin-Hinweis der privaten Vorschau, readme) und drei kleine neue Dateien (PHP-Navigation, CSS, Release-README); übrige Originaldateien bytegleich. **31/31 isolierte PHP-Assertions**, alle **6 PHP-Dateien** Syntax OK, bestehendes JS Syntax OK, ZIP-CRC, WordPress-Pluginroot und bytegleiches 0.1.40-Rollback erfolgreich geprüft. Ein headless Chromium-Visuallauf war lokal **nicht abschließbar**; reale WP-/Browser-/Responsive-/Cache-Abnahme steht aus.

**Chat-Artefakte (Binär-ZIPs nicht in GitHub):**
- `INSTALL-IN-WORDPRESS-ANDY-Home-Composer-0.1.41-PIPPI-ENVIRONMENT-SWITCH-01.zip` · SHA-256 `eba3a99c65cb917a84a38212c974ff0307b140b1545fe4a818a5bc899f80a4e6`.
- `ROLLBACK-ANDY-Home-Composer-0.1.40-PIPPI-ENVIRONMENT-01.zip` · SHA-256 `f53a0d11e30ef817afbf0d7c104ddaa02399fc8d2fb4f3977b54897392f4d361`.
- `ANDY-ENVIRONMENT-SWITCH-01-HOME-COMPOSER-0.1.41-RELEASE-2026-11-25.md`.

**Nächste Abnahme:** vollständiges Hostinger-Backup, reales Installieren des einzelnen 0.1.41-ZIPs, in Live beide Sprachen/Editoren/Previews vergleichen, Staging-Platzhalter auf fehlende Bearbeitungsformulare prüfen; noch **keinen** Staging-Link als real freischalten. Erst nach eigenständigem, extern geschütztem STAGING-01 und Host-/DB-Prüfung zur echten Zwei-Site-Navigation wechseln. Release-Gate PRE-STAGING-01C2B für wirksame öffentliche Inhalte bleibt unverändert.

