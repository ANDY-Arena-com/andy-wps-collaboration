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
