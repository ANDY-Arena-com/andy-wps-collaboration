# ANDY Journal — Behavior Model Card V1 / APP→WP Handoff

**Stand 25.11.2026.** **Status:** Produkt-/Schnittstellenkonzept zum Abstimmen mit APP- und Journal-Threads. **Keine Plugin-Installation, kein WordPress-Datenimport, kein Live-Release.**


**Zentrales Umsetzungsticket:** [GitHub Issue #15 – APP-Exporter → Journal/WordPress](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/15) (Planung, keine technische Abnahme).

## Auftrag und Navigationsziel

Ein Modell erhält eine **eigenständige**, aus realen dokumentierten ANDY-Spielen kumulierte **Behavior Model Card**: Spiele, eigene Aktionen/API-Entscheidungen, Geschwindigkeit, Input-/Output-Relation, Ressourcen, Versuchsbedingungen, Evidenzqualität und ggf. revidierbare Bonoma-/Sweet-Spot-/Nested-Networks-Hypothesen. **Kein Modellranking, keine direkte Gegenüberstellung mit anderen Modellen.** Gegnernamen nur in den Details einer konkreten realen Partie.

**Reise der Leser:** Instagram/LinkedIn → Model Card → Fight Night / Match Story → Replay (bei vorhandener Event-URL) → ANDY Lab / Research → weitere echte Spiele.

### Canonical technische Unterlagen

- [Behavior Model Card – **vollständige Produkt-/Requirements-Dokumentation**](https://github.com/ANDY-Arena-com/andy-wps-collaboration/tree/main/research/andy-lab/BEHAVIOR_MODEL_CARD/v1.0)
- [Product Requirements](https://github.com/ANDY-Arena-com/andy-wps-collaboration/blob/main/research/andy-lab/BEHAVIOR_MODEL_CARD/v1.0/01_PRODUCT_REQUIREMENTS.md)
- [Metric Registry / Speed & I/O](https://github.com/ANDY-Arena-com/andy-wps-collaboration/blob/main/research/andy-lab/BEHAVIOR_MODEL_CARD/v1.0/02_METRIC_REGISTRY.md)
- [Evidenzkompass](https://github.com/ANDY-Arena-com/andy-wps-collaboration/blob/main/research/andy-lab/BEHAVIOR_MODEL_CARD/v1.0/03_EVIDENZKOMPASS_UND_METHODIK.md)
- [APP→WP Export Contract DRAFT](https://github.com/ANDY-Arena-com/andy-wps-collaboration/blob/main/research/andy-lab/BEHAVIOR_MODEL_CARD/v1.0/04_EXPORT_CONTRACT_DRAFT.md)
- [UI, WP, Journal, Social](https://github.com/ANDY-Arena-com/andy-wps-collaboration/blob/main/research/andy-lab/BEHAVIOR_MODEL_CARD/v1.0/05_UI_WP_JOURNAL_SOCIAL.md)
- [Engineering / 25 QA Cases](https://github.com/ANDY-Arena-com/andy-wps-collaboration/blob/main/research/andy-lab/BEHAVIOR_MODEL_CARD/v1.0/06_ENGINEERING_ROADMAP_TESTS.md)
- [Bisherige Demo-/Pilotdaten](https://github.com/ANDY-Arena-com/andy-wps-collaboration/blob/main/research/andy-lab/BEHAVIOR_MODEL_CARD/v1.0/07_PILOTDATEN_QUELLEN_STATUS.md)
- [V1 JSON Schema DRAFT](https://github.com/ANDY-Arena-com/andy-wps-collaboration/blob/main/research/andy-lab/BEHAVIOR_MODEL_CARD/v1.0/schema/behavior_card_v1_draft.schema.json)

## Datenhoheit & WordPress

**APP = Daten und Berechnungen.** Match-Paar `<id>.jsonl` + `<id>.json` ist Primärgrundlage; vorhandener Evidence-/Match-Identity-/Metric-Resolver wird read-only genutzt. Ein `andy.behavior-card/1.0-draft`-Snapshot führt eindeutige Modellidentität und *logische* Spiele (Self-play / Resume / Refund richtig gezählt), metrisch definierte Werte mit Quellen/Coverage und historische Bedingungen. **Keine neue zweite JSONL-Interpretation in WordPress**.

**WP = Redaktion und Darstellung.** Bestehende Content-/Language-/Template-/Launch-Control-/Staging-Infrastruktur weiternutzen. Erst nach Plugin-/Content-Composer-Ist-Audit entscheiden, ob das Import-/Renderingmodul im vorhandenen Content Composer oder als isolierter Adapter läuft. **Content bestimmt Übersicht/Gabelseite, diese bestimmt Home.** Gemeinsame Zahlen für DE/EN, separater Text, Thema/Verweise, Bildredaktion, Review, SEO/Social-Preview.

**Sicherheit:** JSON-Import zunächst ausschließlich auf `staging.journal.andy-arena.com`, Schema- und Versionsprüfung, Dry-run/Preview, Idempotenz/Revisionskonflikte, Rollback, Adminautorisierung, Schutz von REST/Feeds/Caches. Kein Hostinger-Gesamt-Publish und kein blindes Stage↔Live-DB-Sync. Live nach bewusster redaktioneller und technischer Freigabe über bestehendes Launch Control.

## Gemeinsamer Info-Expander „Warum ANDY?“ (neue Must-Anforderung BMC-R16)

Alle Cards allgemeiner KI-Modelle erhalten vor/bei den KPIs einen **globalen, standardmäßig zugeklappten DE-/EN-Bereich**: Was ist die gemeinsame Aufgabe? Wie müssen allgemeine Modelle die gekoppelten Schach-Go-Regeln und einen neuen Spielzustand verarbeiten und mit begrenzten Ressourcen/ihren zugelassenen Werkzeugen Aktionen umsetzen? Warum ist das im Unternehmenskontext eine interessante Frage, ohne dass ANDY Geschäftseignung beweist? **Gleiche Basisregeln bedeuten nicht nachweislich identisches Vorwissen, tatsächliche Modellversion, Providerroute, Budgets oder Toolzugriff.** Kein als Tatsache behauptetes „nie trainiert/nie gesehen“.

Linkziel vom Nutzer: [ANDY-Dokumentation · Einführung](https://andy-arena-com.github.io/andy-wps-collaboration/andy-dokumentation-regeln-lab.html#intro), weitere Kapitel: Regeln `#rules`, Lab `#lab`, Komplexität `#challenge`, AQP `#score`. In Repo-HTML sind diese Anker vorhanden; **externe GitHub-Pages-Funktion vor Staging-Release browserprüfen**, weil der öffentliche Abruf in der Recherche nicht gelang. AQP erklärt auch, warum nicht alle Modelle gleich viele Partien erreichen.

**Eine einzige zentrale Content-/WHY-Redaktionskomponente für alle Karten**, kein Modell-/Match-JSON-Duplikat. Die individuellen Versuchsbedingungen verbleiben in den Card-/Matchdetails; das APP-Exporter-Format bleibt faktenzentriert. **Volltext DE/EN, Links, Accessibility und QA:** [BMC-R16 / Info-Expander](https://github.com/ANDY-Arena-com/andy-wps-collaboration/blob/main/research/andy-lab/BEHAVIOR_MODEL_CARD/v1.0/08_GEMEINSAME_HERAUSFORDERUNG_INFO_EXPANDER.md).

## Visuelle Anforderungen für eine Website-Card

- **Hero:** Modellname, Zeitraum, Anzahl echter Partien, Aktionenzähler, eigener API-Entscheidungszähler.
- **Evidenzkompass direkt danach:** Umfang und Versuchsbedingungen, Stabilität nur bei hinreichender und vergleichbarer Datenbasis, **Erhebungsaufwand** (Zeit/Kosten-Coverage). Seltener Spieler ≠ schlechteres Modell.
- **Tempo:** Aktionen/Stunde eigener aktiver API-Zeit mit echtem Nenner und `abgedeckte Spiele / alle Spiele`; die Gesamtmatchdauer enthält beide Seiten und darf nicht als eigene Antwortzeit ausgegeben werden.
- **Ressourcen:** eigener Input, Output und **Output/Input**, Reasoning/Cache sofern separat gemeldet; keine Overthinking-Diagnose aus dieser Ratio.
- **Verhalten:** Bonoma-/Sweet-Spot- / Adaptive-Stabilitäts-Felder mit Status BEOBACHTET/BERECHNET/INTERPRETIERT/OFFEN; default „noch nicht untersucht“.
- **Originale:** nach Fight-Night-Vorbild „Details der Partie“ mit Ruleset, Engine, tatsächlicher Modell-ID/Route soweit belegt, Budget, Limits, Retry, Quelle, Match-ID, Code-Revisionsstand, prüfbaren Links.

## Konkrete Verknüpfungen

1. Modell-Name einer belegten Fight-Night-Story → veröffentlichte Behavior Card (falls existent).
2. Model Card → passende reale Match Story(s), mit stabiler Match-ID und dem geprüften Journal-Permalink.
3. Schlüsselszene → Replay-Event X **nur**, wenn App-/WP-Router diesen Deep-Link tatsächlich unterstützt; sonst belegte Replay-Landingpage.
4. Card → Lab-/Research Edition mit Methoden-/Evidenzstand; nicht vom WP-Template neu berechnen.
5. Social-Teaser → **eingefrorener, geprüfter Card-Snapshot**. Eine valide Kennzahl mit Umfang/Zeitraum/Einschränkung, keine Rankings/Marketing-Behauptung.

## Abgrenzung der aktuellen Journal-Demo

Die gezeigte Fight-Night-Seite `/andy-fn-demo-claude-grok-2/` ist **eine fiktive Layout-Demo mit Beispielwerten**, keine Primärquelle für Behavior Cards. Die Statushinweise („fiktiv“/„nicht vorhanden“) müssen in allen kontextuellen Vorschaudaten erhalten bleiben. Echte Matches dürfen erst aus validierten APP-Exports kommen.

## Status / nächster freizugebender Schritt

**Jetzt dokumentiert:** gemeinsamer Produktansatz, Requirements, Metro-/Time-/I/O-Definitionen, JSON-DRAFT, UX-/Social-/Research-Ziele und Akzeptanztests. HTML-V1-Clickdummy wurde im zugehörigen APP-Chat als Offline-Datei getestet, ist **nicht** durch diese GitHub-Dokumentation als installiert oder produktiv erklärt.

**Offen:** aktuelle WP-Pluginversionen und Metafelder auditieren, APP-Exporter aus echten Originalen bauen und prüfen, Importmapping an vorhandenem Content Composer testen, Links/DE/EN/Cache/Sicherheit im Staging testen, bewusste Freigabe.

**Beachte bestehende Journal-Release-Gates:** `PROJECT/JOURNAL/v1.1/STATUS.md` und die Staging-First-/Launch-Control-Dokumente haben Vorrang vor einer neuen Feature-Installation.
