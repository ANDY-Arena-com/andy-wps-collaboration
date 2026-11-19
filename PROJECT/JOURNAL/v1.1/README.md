# ANDY Journal — Gesamtkonzept v1.1

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
