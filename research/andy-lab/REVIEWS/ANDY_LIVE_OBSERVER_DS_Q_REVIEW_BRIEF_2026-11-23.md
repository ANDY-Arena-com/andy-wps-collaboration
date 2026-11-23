# ANDY 2.0 — unabhängiger Review-Auftrag DeepSeek & Qwen

**23.11.2026 · Status: versandfertiges Briefing, noch keine Antwort von DS oder Q.**  
**Ziel:** Während das App-Team die lokale Studio-Instanz 8080 und die Sandbox 8082 kontrolliert synchronisiert, sollen DeepSeek und Qwen unabhängig beurteilen: **Wie integrieren wir die funktionierende Live-/Replay-Observierung in ANDY Data und das Living Lab, um übergeordnete Erkenntnisse über viele Partien zu gewinnen?**  
**Leitidee:** Erleben. Erforschen. Erahnen.

## 1. Gemeinsame Faktenbasis: bitte vor dem Review lesen

**Aktuell und verbindlich:** [Observer / Game Intelligence / Economy: Browser-Zwischenstand vom 23.11.](https://github.com/ANDY-Arena-com/andy-wps-collaboration/blob/main/PROJECT/ANDY_LIVE_OBSERVER_ECONOMY_STATUS_2026-11-23.md).

**Bestehende Architektur und Methodik:**

- [Lab Research Architecture](https://github.com/ANDY-Arena-com/andy-wps-collaboration/blob/main/research/andy-lab/ANDY_LAB_2_0_RESEARCH_ARCHITECTURE_v1.0.md)
- [Lab V1.0 / Living Lab Produktkonsens](https://github.com/ANDY-Arena-com/andy-wps-collaboration/blob/main/research/andy-lab/REQUIREMENTS/ANDY_LAB_V1_0_PRODUCT_CONSENSUS_2026-11-20.md)
- [Event-to-Evidence Method](https://github.com/ANDY-Arena-com/andy-wps-collaboration/blob/main/research/andy-lab/METHODIK/ANDY_EVENT_TO_EVIDENCE_METHOD_v0.1.md)
- [Match-Evidenzvertrag JSONL + JSON → SQLite](https://github.com/ANDY-Arena-com/andy-wps-collaboration/blob/main/PROJECT/ANDY_MATCH_EVIDENCE_JSONL_JSON_SQLITE_v1.0.md)
- [Resource & Game Records LAB-R11](https://github.com/ANDY-Arena-com/andy-wps-collaboration/blob/main/research/andy-lab/REQUIREMENTS/v0.1/RESOURCE_GAME_RECORDS.md)
- [API-Kosten / Caching / Novembertarife](https://github.com/ANDY-Arena-com/andy-wps-collaboration/blob/main/research/andy-lab/REQUIREMENTS/v0.1/API_COSTS_CACHE_2026-11.md)
- [USAGE-AUDIT #11](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/11), [Daten-/Leaderboard-Sync #12](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/12), [Replay-UX #13](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/13)

**Was bereits in 8082 browserseitig beobachtet wurde:** Ein einziges verschiebbares Observer-iframe mit (1) Muster-/Spiegelung/Geometry/Pulse, (2) manueller KI-Einschätzung für den fixierten Matchpunkt X mit drei Tendenzen Schach/Go/Gesamt und Modell-/Sample-Historie, (3) Economy-Analyse von API-Zeit, Input/Output, gemeldetem Reasoning, Cache und tarifbasierten USD/EUR-Kosten. Diese Analyseansichten sind für Live und Replay gedacht. Der GI-Aufruf ist ausdrücklich manuell; die Economy-Ansicht benötigt keinen eigenen KI-Aufruf. Bestehende Partien, einschließlich kurzer Setup-Tests, sind wertvolle potenzielle Daten. Der 8080↔8082-Code-Sync ist **nicht** bereits abgeschlossen.

**Grenzen:** Eine Spiegelungsheuristik beweist keine Intention. Eine LLM-Spieleinschätzung ist keine sportliche Regelentscheidung. Bei Replay können historische Bretter rekonstruiert statt unabhängig verifiziert sein. Nur tatsächlich abgefragte X haben GI-Bewertungen; zwischen Messpunkten keine erfundenen Werte. Anbieter melden Reasoning/Cache verschieden; nicht doppelt zählen. Ein Tarifwert ist eine zeitbezogene rechnerische Kostenabschätzung, nicht automatisch ein Rechnungsbetrag. Historische Resume-/Refund-Segmente dürfen nicht doppelt zählen.

## 2. Gemeinsame Leitfragen – beide bitte unabhängig beantworten

1. **Observer → Data → Lab:** Was ist der kleinste saubere Datenfluss von Original-JSONL/Matchbericht über normalisierte Events und Observer-Annotationen in die **bestehende** Data & Evidence Engine, Metric Registry und Lab-Explorer/Builder, ohne zweite konkurrierende Datenwahrheit?
2. **Identität:** Wie verknüpfen wir logische Partie, technische Segmente, Replay-Event X, API-Aufruf/Retry, tatsächlich ausgeführten Zug, annotierte Muster, KI-Bewertungsmodell und Snapshot-/Quellhash? Wie verhindern wir Datenleckage von Y nach X und Doppelzählung?
3. **Provenienz und Zeit:** Welche Informationen sind geloggt, rekonstruiert, engine-verifiziert, heuristisch, LLM-bewertet, tarifgeschätzt oder rechnungsbelegt? Wie speichern wir Versionsstand von Spielregeln, Modell, Berechnung, Tarif, FX und Zeitpunkt, ohne Originale zu verändern?
4. **Übergreifende Erkenntnisse:** Welche 3–5 ersten, **testbaren** Forschungsfragen lohnen sich? Beispiele: Spiegelungen/Responsivität, Setup-Geschwindigkeit der 16 Go-Steinsetzungen, Kosten pro erfolgreicher Aktion, Reasoning vs. Nutzen, Fehler und Recovery, zeitabhängige Provider-Latenzen. Für jede Frage Gegenhypothesen nennen.
5. **Vergleichbarkeit:** Wie kontrollieren wir Modell-/API-Version, Spielphase, Konfiguration, Gegner, Farbe, Tageszeit, individuelle Match-/Serienabhängigkeit und unterschiedliche Usage-Abdeckung? Keine angeblich universelle Modellrangliste.
6. **GI-Bewertungen:** Wie trennt man Schätzungen verschiedener Bewertungsmodelle von echtem Stellungseffekt? Ist Replay-Backfill für X=1..N sinnvoll, und wenn ja wie sparsam?
7. **Living Lab und Journal:** Wie geht eine auffällige Live-Beobachtung in einen Hypothesen-/Gegenhypothesen-Katalog, über kontrollierte Wiederholungen in eine belastbare Lab-Evidenz und dann in eine reproduzierbare Research Edition oder Journal-Story über?
8. **Pragmatischer MVP:** Was können wir **während des 8080/8082-Syncs als Spezifikation/Testvorbereitung** tun, und welche maximal drei kleinsten Implementierungsschritte sind erst **nach** geprüfter Synchronisation sinnvoll? Was ausdrücklich nicht bauen?

## 3. DeepSeek: besonderer Schwerpunkt Daten-/Integrationsarchitektur

Bitte gewichte besonders **Datenverträge, idempotente Ableitung und Regression-/Migrationsrisiken**.

- Entwerfe ein kleines **Daten-/Eventschema** mit Identifikatoren, Zeit, Source-Hash, X, API-Attempt vs. executed action, Observations-Type, Model-/Method-/Tarif-Version, Quality und passender Sample-Granularität.
- Wie werden Live-Updates, Replay-Import, historische Legacy-Usage, Resume/Refund und Tarifkorrekturen ohne redundante/konkurrierende Datenbanken zusammengeführt?
- Welche Berechnungen sollten deterministisch sein, welche ausschließlich Annotationen/LLM-Urteile? Wie verhindern wir neue Writers auf produktiven Originalen?
- Prüfe speziell Grok/Reasoning vs. sportliches Tokenkonto (#11), zeitabhängige Tarife und die Trennung von tatsächlichem Spielende gegenüber subjektiven GI-Tendenzen.
- Liefere ein **minimales Architekturdiagramm**, drei klare Inkremente mit Tests und den größten vermeidbaren Fehler.

## 4. Qwen: besonderer Schwerpunkt Forschung und Erkenntnisgewinn

Bitte gewichte besonders **Kohorten, unabhängige Beobachtungseinheiten, Gegenhypothesen und erkenntnisfördernde Visualisierung**.

- Entwirf **3–5 Hypothesen/Gegenhypothesen**, jeweils Metrik, Einheit/Nenner, notwendige Quellen, kontrollierte Variablen, kleinste Testserie und geeignete Grafik.
- Wie unterscheidet das Lab Muster *innerhalb* eines Matches von wiederkehrenden Mustern *zwischen* unabhängigen Matches, Modell-/Versionsgruppen und Zeiträumen? 100 Events derselben Partie sind nicht 100 unabhängige Partien.
- Welche Dashboard-/Explorer-Ansichten zeigen Zusammenhänge zwischen Kosten, Zeit, Token-/Reasoning-Struktur, Ausführungsquote, Setup und Spielausgang **ohne** triviale Gewinner-Rangliste? Beispielsweise Verteilungen, Zeitreihen, Cluster-Small-Multiples und Event-Drilldowns.
- Wie lässt sich eine **Competitive Behavior Model Card** laufend aktualisieren, mit Datenstand, Evidenzstatus, Gegenbeispielen und nachvollziehbaren Quellen?
- Bewerte Replay-GI-Backfill (jedes Ereignis / 5er-Abstand / adaptive Auswahl) und sage, wann der Aufwand echten Erkenntnisgewinn liefert.

## 5. Antwortformat – gleicher Kern für beide

1. Kurzfazit in maximal sechs Sätzen.
2. Drei Stärken, drei Risiken und mindestens eine überraschende Gegenperspektive.
3. Empfohlener **Observer → Data → Living-Lab-Workflow**.
4. Tabelle der **5–8 wichtigsten Datenfelder/Metriken** inklusive Einheit, Nenner, Quelle, Versions-/Qualitätsstatus.
5. Drei priorisierte Research Use Cases: Hypothese, Gegenhypothese, Daten/Kontrollen, Grafik, Minimalexperiment.
6. **Drei kleine Schritte**, zuerst als Dokument-/Datenaudit (während Sync), später als sichere Implementierung; Testkriterien.
7. Offene Fakten/Fragen und Punkte, die zu komplex, unpraktisch oder wissenschaftlich irreführend wären.

**Unabhängigkeit:** DeepSeek und Qwen sollen zuerst jeweils eigenständig antworten. Erst danach Konsens, Dissens und kleinsten Anschlussplan vergleichen. **Noch keine Datenbankschreibaktionen, Git-Code-Commits, API-Tests oder UIs durch die Reviewer.** 8080/8082-Sync/Regression bleibt eigenständiger operativer Strang.

**Status:** Briefing auf GitHub dokumentiert und **zur Weitergabe vorbereitet**, nicht als bereits an DS/Q übermittelt oder von ihnen beantwortet ausgeben.
