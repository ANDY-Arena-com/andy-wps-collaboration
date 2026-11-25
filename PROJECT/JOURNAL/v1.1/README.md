# ANDY Journal — Gesamtkonzept v1.1

> **MODULE-SOURCE-PARITY-01 / HOME 0.1.44 · 25.11.2026:** [Konkreter Staging-Fix für Fight-Night-Auswahl und Farb-Editor](ARCHITECTURE/ANDY-JOURNAL-MODULE-SOURCE-PARITY-01-HOME-COMPOSER-0.1.44-2026-11-25.md), ausgelöst durch Nutzer-Screenshot mit `1419,1423,1427` gegenüber aktuell angebotenen CMS-IDs `1469,1466,1471,1473,1475`, Limit 2 und Nature-Farbpreset. Quell-Audit bestätigt Content-Bridge-Bypass von IDs/Limit und zwei nicht kompatible `wpfn-`/`wpstory-`-ID-Formate. **Home Composer 0.1.44** liefert explizite **Automatik/Manuell**-Wahl, einheitliche CMS-ID-Auflösung und Obergrenze auch im Bridge-Modus, sichtbare Warnungen statt stiller Ersatzartikel sowie deaktivierte individuelle Farbfelder unter Preset-Themes. Alte Module bleiben bis bewusster Umstellung standardmäßig Auto. **19/19 Runtime-Tests + 5 Strukturprüfungen, 6/6 PHP-Lint, ZIP-CRC** bestanden; installierbares Staging-ZIP und originaler 0.1.43-Rollback im Chat. **Noch nicht auf WordPress installiert oder visuell abgenommen; Live nicht ändern.** Zentrale 1–2-Content-Home-Auswahl für alle fünf Bereiche sowie Academy/Perspectives/WHY-Tour **noch nicht implementiert**; separater Vertrag und 01C2B-Sicherheitsgate bleiben.

> **JOURNAL-IN-PLACE-PREVIEW-01 / HOME 0.1.43 – KORREKTUR DES COMING-SOON-MISSVERSTÄNDNISSES / 25.11.2026:** [Private Coming-Soon-Vorschau wieder auf die **echten Journal-Modulrenderer** umgestellt](ARCHITECTURE/ANDY-JOURNAL-IN-PLACE-PREVIEW-01-HOME-COMPOSER-0.1.43-2026-11-25.md). Fachliche Rückmeldung: Die bisherige Simulation war wie eine **andere Site mit anderer Struktur** gestaltet – das widerspricht **„Am Anfang dominiert das Warum, später das Was“**. Künftig **eine Home, ein Design, eine Modulreihenfolge**; vorhandene Claims/Rails/Bühnen/Rubriken/Academy/Perspectives/Research/Making of/Save-Daten werden nicht durch eigene Coming-Soon-Sections ersetzt. WHY/Teaser nur innerhalb dieser Module; nicht freigegebene Posts bleiben private nicht anklickbare Platzhalter, kein Public Release. **0.1.43 nur lokal geprüft (61 Assertions, 6 PHP-Lints, ZIP-CRC), noch nicht auf Staging installiert oder visuell abgenommen; Live unverändert**. 0.1.42 weiterhin sofortiger Rollback, Staging↔Live-Navigation bytegleich. 01C2B-Gate weiterhin offen.

> **STAGING-HOST-GUARD-01 / HOME 0.1.42 + LAUNCH 0.2.3 · 25.11.2026:** [Technisches Korrektur-Release nach echtem Hostinger-Klon](ARCHITECTURE/ANDY-JOURNAL-STAGING-HOST-GUARD-01-RELEASE-2026-11-25.md). Hostinger hat **`staging.journal.andy-arena.com`** erstellt; unser alter Planname `staging-journal.andy-arena.com` war falsch. Nutzerbeobachtung auf Staging: `LIVE · staging.journal.andy-arena.com` und unmöglicher Folgehost `staging-staging.journal.andy-arena.com`. **Keine Hostinger-Domainänderung!** Die beiden lokalen Einzelplugin-ZIPs beheben die Umgebungsidentität über Host + WordPress-Home + `WP_ENVIRONMENT_TYPE` und melden unbekannte Klone als **STOP statt LIVE**. 68/68 isolierte Checks, 11 PHP-Lints, ZIP-CRC; **noch nicht installiert oder auf Hostinger E2E-geprüft**. Staging muss separate DB, externen Passwortschutz, richtige `home`/`siteurl` und `WP_ENVIRONMENT_TYPE=staging` nachweisen; Live bleibt production. Zuerst Staging verifizieren/Updates testen, dann dieselben Pluginversionen auf Live aktualisieren und Staging-Navigation bewusst freigeben. **Kein Remote-Write oder öffentliches 01C2B-Gate.**

> **PIPPI-ENVIRONMENT-SWITCH-01 / HOME 0.1.41 – 25.11.2026:** [Zwei-Button-Umgebungsnavigation im Home Composer als lokales WordPress-Update umgesetzt](ARCHITECTURE/ANDY-JOURNAL-ENVIRONMENT-SWITCH-EDITOR-01-2026-11-25.md). **Staging / Live → DE / EN → Bearbeiten / Home-Vorschau / Coming Soon privat**. Auf Production zeigt Staging zunächst einen **nicht editierbaren Platzhalter**, keine als Staging getarnten Live-Formulare. Nach unabhängiger, extern geschützter Staging-Einrichtung kann ein Administrator den **reinen Navigationslink** unter expliziter Bestätigung aktivieren. 31/31 isolierte Checks, PHP 6/6, JS-Syntax und ZIP-CRC bestanden; originales Home-0.1.40-ZIP bytegleich als Rollback. **0.1.41 noch nicht installiert, kein Hostinger-/Browser- oder visueller End-to-End-Nachweis.** Keine gemeinsamen WP-Datenbanken, Remote-Writes oder öffentliche Freigabe; 01C2B-Gate bleibt offen.

> **PRE-STAGING-01C2B0 · SECURITY-PREFLIGHT / 25.11.2026:** [Launch Control 0.2.2 mit read-only „Release-Sicherheit“-Tab](ARCHITECTURE/ANDY-JOURNAL-PRE-STAGING-01C2B0-SECURITY-PREFLIGHT-2026-11-25.md). 15 öffentliche Auslieferungswege, fünf geplante Bereichsmodi, vorbereitete Leseproben und maximal 50 repräsentative WordPress-Post-Diagnosen. **Jeder Weg bleibt explizit OFFEN: Das Plugin implementiert KEINEN neuen öffentlichen Zugriffsschutz oder Aktivierungsschalter.** 77/77 neue und 116/116 bestehende Tests bestanden, 5/5 PHP-Lint, ZIP-CRC; ZIP/0.2.1-Rollback im Chat. **Noch nicht auf Hostinger installiert.** Release setzt installierten LC-Stand 0.2.1 voraus – vor Update prüfen. **Nächste sichere Reihenfolge:** WordPress-Preflight abnehmen → unabhängiges, extern geschütztes STAGING-01 erstellen → dort 01C2B1/B2 Freigabe-/Routen-/REST-/Cache-Adapter entwickeln und negativ testen → erst nach Abnahme Live-Freigabe. Bisherige Live-Home bleibt unverändert.

> **STAGING-FIRST / SELECTIVE-SYNC · 25.11.2026:** [Verbindlicher Architekturvertrag für eine gemeinsame ANDY-Bedienlogik mit getrennten WordPress-Instanzen](ARCHITECTURE/ANDY-JOURNAL-STAGING-LIVE-SINGLE-WORKSPACE-SYNC-CONTRACT-2026-11-25.md). **Staging als führender Arbeitsort**, **Live als autoritativer öffentlicher Publikationsstand**; gezielter, geprüfter Transfer **Staging→Live** und bei Bedarf **Live→Staging** mit Diff, stabiler fachlicher Objekt-/Sprachidentität, Revisionsschutz und Rollback. **Keine** gemeinsame Datenbank, automatische 2-Wege-Replikation, blindes Hostinger-Gesamt-Publish oder Übertragung von Secrets/Umgebungsflags. Künftige Zwei-Button-UI wechselt zunächst sicher zwischen den lokalen WP-Admins; echter Remote-Editor/Sync ist **noch nicht implementiert**. **PRE-STAGING-01C2B und Staging-Isolation bleiben Stop-Gates** für öffentlich wirksame Freigaben.

> **LAUNCH-PREVIEW-01 / 25.11.2026 – HOME COMPOSER 0.1.40 (LOKAL GEPRÜFT):** [Geschützte direkte DE/EN-Coming-Soon-Home zum Vergleich mit der unveränderten öffentlichen Home](ARCHITECTURE/ANDY-LAUNCH-PREVIEW-01-HOME-COMPOSER-0.1.40-2026-11-25.md). Ein Einzel-ZIP und originaler 0.1.39-Rollback im Chat; 23/23 PHP-Sicherheits-/Datenprüfungen, 2/2 DE-/EN-HTML-Smoketests, PHP-/JS-Syntax und ZIP-CRC bestanden. `/?andy_hc_launch_preview=1&lang=de|en` ist **erst nach Installation** auf `journal.andy-arena.com` für angemeldete Administratoren erreichbar; ungeprüfte Artikel und Leseproben werden in der privaten Simulation nicht verlinkt. Bisherige Home-/Editor-/Launch-Control-Einstellungen unverändert. **Nicht** als öffentliche Coming-Soon-Aktivierung oder als vollumfängliche Hostinger-/Cache-Abnahme behandeln; PRE-STAGING-01C2B weiterhin ausstehend.

> **SYSTEM-MAP-FOUNDATION-01 · TECHNISCHER RELEASE-KANDIDAT / 25.11.2026:** [Content Composer 0.1.30 mit internem Typen-/Identitäts-/Relationen-Register](ARCHITECTURE/ANDY-JOURNAL-SYSTEM-MAP-FOUNDATION-01-TECHNICAL-RELEASE-2026-11-25.md). In bestehendes Plugin integriert, DE/EN-Prüfung, bestehende kanonische Story-Registry und WHY als separate Quellendaten, keine zweite Datenbank/Graph-Engine. Update und Rollback sind nur lokal geprüft; **WordPress weiter mit letzter nutzerseitig bestätigter Version 0.1.29**, bis Updateinstallation bestätigt wird. Öffentliche System Map/Exporte erst nach durchgängigem PRE-STAGING-01C2B-Sicherheitsgate und separater Abnahme.

> **PRE-STAGING-01C2A / WHY-01A · 25.11.2026 – LOKALES RELEASE:** [Launch Control 0.2.1 – dauerhafter DE/EN-WHY-Editor und reine Leseproben-Planung](ARCHITECTURE/ANDY-JOURNAL-PRE-STAGING-01C2A-WHY-01A-RELEASE-2026-11-25.md). Fünf Bereiche, vier WHY-Darstellungsmodi, read-only Policy und individuell geplante Post-/Sprach-Kandidaten; **keine öffentliche Durchsetzung**. 116/116 isolierte Tests, zwei einzelne Plugin-ZIPs (Update / 0.2.0-Rollback) im Chat. **Laut letztem bestätigtem WordPress-Screenshot ist noch 0.2.0 installiert.** Nächster technischer Schritt 01C2B: vollständige Zugriffskontrolle auf eigenständigem geschütztem Staging mit E2E-/Cache-Tests, erst dann Freigabeschalter.

> **WHY / PROGRESSIVE CONTENT RELEASE 01 – 25.11.2026:** [Dauerhafte WHY-Ebene und Coming-Soon-Leseproben: aktueller Konzeptstand](content/ANDY-JOURNAL-WHY-PROGRESSIVE-CONTENT-RELEASE-01-2026-11-25.md). DE/EN Home/Gabelseite/Content, vier WHY-Modi unabhängig vom Bereichsstatus, ausgewählte native WP-Leseproben in Coming Soon, Flywheel als Zielmodell. Umsetzung erst unter 01C2-Route-/Zugriffsgate, ohne zweite Home/Pluginsystematik. **Noch kein Feature-Release / keine Publikationsfreigabe.**

> **COMING-SOON CONTENT-HANDOFF / 25.11.2026:** [Arbeitsauftrag an den Content-Thread](content/ANDY-COMING-SOON-CONTENTKONZEPT-HANDOFF-2026-11-25.md) für die DE/EN-Coming-Soon-Home und die fünf Bereiche. **Neuer Nutzerscreenshot bestätigt:** Launch Control **0.2.0** ist in WordPress installiert, der fünfte Tab und die DE/EN-Planungsfelder sind sichtbar; **Speicherung/Freigabe nicht belegt**. Im bestehenden Home-Design bleiben die Bereiche zunächst redaktionelle Pläne; echte öffentliche Freigabe erst nach PRE-STAGING-01C2. Frühere Aussagen „noch nicht installiert“ unten sind historische Release-Einträge **vor dem Screenshot**.

> **PRE-STAGING-01C1 – PASSIVE PUBLICATION PLANUNG / 25.11.2026:** [Launch Control 0.2.0 als lokales Plugin-Update](ARCHITECTURE/ANDY-JOURNAL-PRE-STAGING-01C1-PUBLICATION-PLANNING-RELEASE-2026-11-25.md). Neuer Tab **Publication & Coming Soon**, fünf geplante Bereiche, DE/EN-Teaser und eine separat einschaltbare, nur vorwärts beobachtende Veröffentlichungshistorie. **42/42 isolierte Tests**, WordPress-Einzel-ZIP + Original-0.1.0-Rollback im Chat. **Noch NICHT installiert oder auf Hostinger abgenommen; Zustände sind reine Planung, keine öffentliche Home-/Routen-/Content-Sperre.** PRE-STAGING-01C2 mit durchgängigem Routing-/REST-/Legacy-RGB-/Cache-Gate offen.

> **PRE-STAGING-01B · 25.11.2026 – LOKALE RELEASES ERSTELLT:** [Production/Staging-Umgebungsvertrag und Cockpit-Harmonisierung](ARCHITECTURE/ANDY-JOURNAL-PRE-STAGING-01B-UMGEBUNGEN-UND-COCKPIT-RELEASE-2026-11-25.md). Cockpit **0.2.1** (21 Werkzeuge in 5 Gruppen), RGB **0.6.4** und Home Composer **0.1.39** als drei updatefähige WordPress-ZIPs einschließlich drei Original-Rollbacks aus Nutzerexport erstellt; **103/103 isolierte Prüfungen bestanden**. Launch Control 0.1.0 und Content Composer 0.1.29 unverändert. Stage nur auf definiertem Host mit `WP_ENVIRONMENT_TYPE=staging`, externen Passwortschutz separat prüfen. **Weder Installation noch WordPress-/Staging-Abnahme erfolgt.** Aktuell in WordPress laut letztem Nutzerscreenshot weiterhin HC 0.1.38, RGB 0.6.3 und Cockpit 0.2.0, bis eine Neuinstallation tatsächlich bestätigt wird.

> **PRE-STAGING-01 · 25.11.2026 – ARCHITEKTURBESCHLUSS:** [Admin-Harmonisierung, Launch/Publication Governance und künftige Staging-Trennung](ARCHITECTURE/ANDY-JOURNAL-PRE-STAGING-ADMIN-UND-LAUNCH-GOVERNANCE-2026-11-25.md). Eine Cockpit-Betriebszentrale, vorhandene Fachplugins behalten, DE/EN-Home identisch in Live und Staging, Coming-Soon-/Freigabelogik mit Veröffentlichungsgedächtnis. Nutzer bestätigt Domainmigration nach `journal.andy-arena.com` für Backend/Editing/Frontend; Staging noch nicht abgenommen. Pluginliste 25.11.: 20 Einträge (18 aktiv, 2 inaktiv); HC 0.1.38 und CC 0.1.29 laut Pluginliste. **Beschluss, noch kein Plugin-Release oder Bereinigungsfreigabe.** [Making-of-Kommentar MO12](content/ANDY-MAKING-OF-STORY-KATALOG-v0.1-2026-11-25.md#6-mo12--vom-werkzeug-wildwuchs-zur-betriebszentrale-25112026).

> **Making of · 25.11.2026:** [Story-Katalog und Entwicklungsstand v0.1](content/ANDY-MAKING-OF-STORY-KATALOG-v0.1-2026-11-25.md). 10 vorbereitete DE/EN-Paare MO01–MO10, neuer Entwurf MO11 „Der Mensch als Orchestrator“ (noch nicht importiert), separates Add-on 0.1.0/0.1.1 mit Home-Bridge, SHA-256 und offene Abnahme; Rolling Handoff und Staging-Aufbau dokumentiert. Keine Publikationsfreigabe.


> **Aktueller Entwicklungscheckpoint 24.11.2026 (Tagesabschluss): [WP-ARCH R0.5](ARCHITECTURE/WP-ARCHITECTURE-R0.5.md).** Home Composer 0.1.37; Content Composer 0.1.26 nutzerseitig erfolgreicher Academy-Import und Content→Overview, 0.1.28 jüngstes Perspectives-Paket (positives Nutzerfeedback, detaillierte Live-Abnahme offen). 22 Release-Schritte samt ZIP-Prüfsummen; Academy A–D (18 Lektionen/Vorlagen), Perspectives (6 DE/EN-Paare und Overview), **problem-driven Crossover vor Research**, gemeinsame Content-Quelle. Ältere Versionsangaben unten sind historische Referenzen, keine Installationsanweisung. Release-Gate gilt unverändert; keine öffentliche Freigabe.


**Status:** Historische Konzeptbasis; aktueller Teststand siehe Nachtrag 19.11.2026  
**Stand:** 13. November 2026  
**Sprache:** Deutsch (Masterdokument)  
**Ziel:** Eine versionierbare Grundlage für Konzeption, Design, Redaktion und spätere technische Realisierung des eigenständigen ANDY Journal.

> **Leitsatz:** ANDY Journal ist die redaktionelle Schwester der ANDY Arena. Es erzählt die Geschichten hinter den KI-Duellen – vom faszinierenden Moment bis zur überprüfbaren Forschungsfrage.

## Launch-Plan und Research-Erweiterung – 19.11.2026 (aktueller Arbeitsstand)

- [Public Beta / Launch Control v0.1](docs/ANDY-JOURNAL-PUBLIC-BETA-LAUNCH-CONTROL-v0.1.md) – Zielbild, BETA und Orientierung, 30 Basis-Inhalte, Interaktionsprofile, Soll-/Ist-Sitemap, interner WP-Entwurfsworkflow und Design-QA. Separates Plugin v0.1.0 bereitgestellt; tatsächliche WP-Abnahme offen. 
- RGB Content / UI 0.6.0 als neuer Teststand mit drei Research-Dossiers (Crossover-Muster, AI Continuity Research, Entscheidungsverhalten), vollständigem Crossover-Artikel und reversibler Versionswahl 0.5.0/0.6.0. 28 Ist-Seiten; keine Publikationsfreigabe. Endgültige Rubrikensortierung offen. Artefakt-Hashes im Launch-Memo.
- [ARP und Resume Research](../../ANDY_RESUME_RESEARCH_ARP_v0.1.md) als fachliche Grundlage für AI Continuity Research; die Journal-Inhalte und Befunde benötigen gesonderte redaktionelle/fachliche Prüfung.

Die frühere Baseline 17.11. bleibt als Rückweg und Referenz erhalten. Die Launch-Planung ersetzt keine Masterplan-/WPS-Gates. BETA-Kennzeichnung im öffentlichen Frontend, echte Replay-Anbindung und native Publikationsintegration sind noch offene Launch-Aufgaben.

## Arbeitsstand – 17.11.2026 (historische Baseline)

**WordPress-Testbaseline:** RGB Content 0.5.0 / RGB UI 0.5.3 / Journal Cockpit 0.1.0. Die neue RGB-Ansicht wurde nutzerseitig auf der Testinstallation erprobt; Burger/Accordion positiv bestätigt. Die native Aculia-Struktur bleibt erhalten. Keine öffentliche Freigabe.

- [RGB-Informationsarchitektur und Designbaseline](docs/ANDY-JOURNAL-RGB-DESIGN-BASELINE-2026-11-17.md) – Home, sieben Slider-Teaser, Drei-E-Navigation, zehn Gabelseiten, Breadcrumbs, Mobile-Accordion, Key-Visuals und inline Interaktionen.
- [WordPress-Implementierungsstand und Übergabe](docs/ANDY-JOURNAL-WP-BASELINE-2026-11-17.md) – Inventory, DESIGN-01, HOME-01, Publishing, Cockpit, RGB-Pilot, Paket-/Importlogik und Sicherheitsgrenzen.
- [Match Stories – Play-first Blueprint v0.4](docs/ANDY-JOURNAL-MATCH-STORIES-v0.4.md) – Hook als Hauptaktion, Arena statt Sci-Fi, individuelle Match Cards, historische Modellklassen, progressive Spoiler-Logik, Zeitstempel; separates HTML-Experiment, nicht Teil der WP-Baseline. Vollständiger Originalplayer fehlt in diesem Pilot.
- [Artefaktregister](docs/ANDY-JOURNAL-ARTEFAKTE-2026-11-17.md) – tatsächliche ZIP-Dateinamen, Versionen, Dateianzahlen, erneut berechnete SHA-256-Prüfsummen und QA-Nachweise. Keine Binärarchivierung erfolgt.

**Geltung:** Die folgenden älteren Konzept- und Übergabedokumente bleiben als historische Entwicklungsgrundlage erhalten. Für die gegenwärtige Journal-Navigation, Rubriken, UI und WP-Implementierung gelten die neueren, oben verlinkten Memos; insbesondere ist die alte Vier-Rubriken-Navigation nicht der aktuelle Pilotstand. Masterplan, WPS-Governance und ursprüngliche Daten-/Freigaberegeln gelten unverändert. Arbeitsbaseline ≠ vollständige technische Abnahme ≠ öffentliche Publikationsfreigabe.

## Dokumente

- [Gesamtkonzept](docs/ANDY-JOURNAL-GESAMTKONZEPT-v1.1.md) — Leitbild, Zielgruppen, Informationsarchitektur, Design, Content, Multimedia, Wissenschaftlichkeit, technische Leitplanken, Roadmap.
- [Offene Entscheidungen](docs/ENTSCHEIDUNGEN-UND-OFFENE-PUNKTE.md) — Vorschläge, die vor Implementierung gemeinsam freigegeben oder geprüft werden müssen.
- [Redaktioneller Themenspeicher aus ANDY-Dialogen](docs/REDAKTIONELLER_THEMENSPEICHER_AUS_ANDY_DIALOGEN_v0.1.md) — 27 priorisierte Story-Kandidaten, Serien, Belegbedarf und Ideen für die Making-of-Dokumentation (Backlog, keine Freigabe).
- [Redaktionelle Match-Checkliste](docs/MATCH-ARTIKEL-CHECKLISTE.md) — Qualitätsprüfung für dokumentierte Partien.

## Geltungsbereich

Diese Version ist ein **Konzept**, keine fertig implementierte Website. Sie trifft keine ungesicherten Aussagen über Plugin-Kompatibilität, verwendete Originalfarben oder die Verfügbarkeit einzelner Originaldaten. Illustrative frühere Designentwürfe und Beispieltexte sind **keine** Nachweise realer Matches.

## Sicherheitsgrenze

Die bestehende ANDY Arena und die öffentliche Coming-Soon-Seite unter `https://blog.andy-arena.com/` bleiben unverändert. Insbesondere gilt bis zur ausdrücklichen Freigabe weiterhin die vorhandene Startdatei-Priorität `DirectoryIndex index.html index.php`.

## Versionierung

- **v1.1 — 2026-11-13:** Abgleich mit Masterplan und WPS-Governance.
- **v1.0 — 2026-11-13:** Konsolidiertes Gesamt- und Umsetzungskonzept basierend auf Projektübergabe, Designreferenzen und Abstimmungen zu Zielgruppen und Multimedia.

Vorgeschlagene Commit-Nachricht nach Review: `docs(journal): align concept v1.1 with ANDY masterplan`

## Einordnung / Referenzen

- ANDY Arena: https://andy-arena.com/
- ANDY Journal (öffentliche Vorschauseite): https://blog.andy-arena.com/
- ANDY Docs (in der Unterhaltung gezeigte GitHub-Pages-Seite): https://andy-arena-com.github.io/andy-wps-collaboration/andy-dokumentation-regeln-lab.html#arena

**Hinweis:** Masterplan und WPS-Governance wurden über die GitHub-Anbindung gelesen; originale Game-Code-Dateien, Datenendpunkte und Match-JSONL sind damit noch nicht geprüft. Screenshots liefern Designreferenzen, keine unabhängigen Matchvalidierungen.

## Projektübergreifender Abgleich

Die Version 1.1 ist auf den ANDY-2.0-Masterplan und die Governance der Working Paper Series abgestimmt. Sie ersetzt diese **nicht**. Siehe [`docs/ABGLEICH-MASTERPLAN-v1.1.md`](docs/ABGLEICH-MASTERPLAN-v1.1.md). Die Statusangaben bezeichnen einen Konzeptentwurf, **keine** technische Umsetzung oder Publikationsfreigabe.

## Public Beta – Guidelines und Arbeitsplan (15.11.2026)

- [Design & Editorial Guidelines 1.0](docs/ANDY-JOURNAL-GUIDELINES-v1.0.md) – erlebbar, erforschbar, erahnbar; Arena-Verwandtschaft und eigenständige Magazinbildwelt; Vermittlungsqualität als Testgegenstand.
- [Public Beta – Arbeitspakete 1.0](docs/ANDY-JOURNAL-PUBLIC-BETA-ARBEITSPLAN-v1.0.md) – JRN-01–09, fünf Pilotartikel und iterative Abnahme; keine Live-Freigabe.

## Plugin-Architektur und Match Library (15.11.2026)

- [ANDY Journal – Plugin-Architektur v0.1](docs/ANDY-JOURNAL-PLUGIN-ARCHITEKTUR-v0.1.md) – erfolgreiche erste Praxistests von Academy und Replay, zentraler Player mit Match Center und individueller Artikeleinbindung, Game Packages und Roadmap; weitere Implementierung und Theme-Kompatibilitätsprüfung offen.

## Content Manager und Publishing Workflow (16.11.2026)

- [ANDY Content Manager – Workflow v0.1](docs/ANDY-CONTENT-MANAGER-WORKFLOW-v0.1.md) – Aculia-Transformation, modulare Design-/Content-Pakete, Inventory und Herkunftsregister, Dry Run, Rollback und späterer Demo-Cleanup nach Ersatz- und Abhängigkeitsprüfung. Konzept, Implementierung offen.

## Content Manager – historische Übergabe (16.11.2026, durch Nachtrag 17.11. ergänzt)

- [Übergabe DESIGN-01](docs/ANDY-CONTENT-MANAGER-HANDOVER-2026-11-16.md) – Inventory v0.1.1 erfolgreich, Backup nutzerseitig bestätigt, 211 Referenzobjekte und unveränderte Hash-Paare über beide Exporte. Schreibender Import v0.2 und DESIGN-01 nicht erstellt; Release-Gate BLOCKED. Der neue Thread übernimmt die konkrete Implementierung und Prüfung. Keine Live-Freigabe.
