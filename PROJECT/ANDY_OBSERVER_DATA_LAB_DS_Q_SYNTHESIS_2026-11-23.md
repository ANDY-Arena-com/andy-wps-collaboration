# ANDY 2.0 — DS/Q-Konsolidierung: Observer → Data → Living Lab

**Stand:** 23.11.2026 · **Status:** redaktionelle Konsolidierung zweier unabhängiger externer Reviews, **Architekturvorschlag, noch keine endgültige Produkt-/Codefreigabe**.  
**Ziel:** Während der lokalen 8080/8082-Synchronisierung eine kleine, testbare Verbindung zwischen dem funktionierenden Live-/Replay-Observer und dem bestehenden Data-/Living-Lab-System vorbereiten, ohne produktive Daten, 8080/8082-Code oder 8083 anzufassen.

## 1. Primäre Quellen

- [Observer/GI/Economy-Zwischenstand vom 23.11.](ANDY_LIVE_OBSERVER_ECONOMY_STATUS_2026-11-23.md)
- [DeepSeek Review (redaktionell strukturierter Eingang)](../research/andy-lab/REVIEWS/ANDY_LIVE_OBSERVER_DS_REVIEW_2026-11-23.md)
- [Qwen Review (redaktionell strukturierter Eingang)](../research/andy-lab/REVIEWS/ANDY_LIVE_OBSERVER_Q_REVIEW_2026-11-23.md)
- [Data-/Match-Evidenzvertrag](ANDY_MATCH_EVIDENCE_JSONL_JSON_SQLITE_v1.0.md)
- [Lab-Forschungsarchitektur](../research/andy-lab/ANDY_LAB_2_0_RESEARCH_ARCHITECTURE_v1.0.md)
- [USAGE Audit #11](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/11) / [DATA-SYNC #12](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/12)

## 2. Konsens

1. **Eine Datenbasis, keine zweite Observer-Match-Wahrheit.** Original-JSONL und Matchbericht bleiben Primärquellen. Bereits existierende Data-/Evidence-Projektionen integrieren statt eine parallele Observer-Datenbank für Spiele zu eröffnen.
2. **Identität und Provenienz sind grundlegend.** Logische Partie, Resume-Segment, Raw-Event X, API-Attempt/Retry und ausgeführte Aktion auseinanderhalten. Original-/Modell-/Methoden-/Tarif-/FX- und Datenstandsreferenzen nachvollziehbar erhalten.
3. **Datenqualität ist eine Eigenschaft der Ableitung.** Rekonstruierte Bretter nicht stillschweigend verifizieren; fehlendes Reasoning/Usage nicht als Null interpretieren; Spiegelmarker keine Aussage über tatsächliche KI-Intention; LLM-Bewertung keine offizielle Sportwertung.
4. **Observer und Lab müssen dieselben Metrikdefinitionen nutzen.** Unabhängig nachgebaute Frontend-/SQL-Formeln würden bei Zeit-, Kosten- und Erfolgsquoten auseinanderlaufen.
5. **Langzeitforschung statt einer Siegerliste.** Match/Serie/Kohorte sind primäre unabhängige Vergleichseinheiten; eine Kurve über mehrere KI-Evaluator-Modelle ist keine homogene Zeitreihe derselben Messinstanz.
6. **Klein anfangen und laufenden Sync schützen.** Zuerst Spezifikation und read-only Audit; Implementierung nur nach Release-/Regressionsfreigabe.

## 3. Wichtigster Unterschied und empfohlene pragmatische Auflösung

**DeepSeek:** kanonische `observation`-Events mit `observation_type`; die Datenintegration darf nicht an drei separaten UIs/Schemata scheitern. Befürwortet eine einheitliche Ingestion/Eventschnittstelle.

**Qwen:** nicht jede aus denselben Rohdaten erneut berechenbare Kurve, Kosten- oder Formationsmetrik als neues unveränderliches Datenereignis speichern. Stattdessen **gemeinsame versionierte Metric Engine** und **sparsame append-only Annotationen**, besonders für tatsächliche manuelle GI-Urteile.

**Empfohlene Synthese (noch kein Codebeschluss):**

- **Kanonischer Observation-Vertrag als *logisches* Schema** für alle abgeleiteten Messgrößen — unabhängig davon, ob sie *on demand* berechnet, in einem regenerierbaren Cache materialisiert oder als eigenständige Annotation aufbewahrt werden.
- **Rohdaten** (JSONL + JSON, Hash, Modell-/Rule-Konfiguration) bleiben unverändert.
- **Normalisierte Events/Read-Model** bauen auf der bestehenden Evidence-Projektion auf. Ob eine geeignete Event-Tabelle, API oder ein Event-Bus tatsächlich existiert, **muss im lokalen Code geprüft werden**; keinesfalls eine solche Schnittstelle voraussetzen.
- **Deterministische Werte** (Aufruf-Latenz, Input-/Output-Cost nach Tarif, kumulierte USD/EUR-Kurven, wiederberechenbare Geometry-/Mirror-Samples) aus *einer* versionierten Bibliothek. Materialisierung ist optional und **rebuildable**. Kein kanonisches Archiv jeder dargestellten EUR-Gesamtsumme.
- **Nicht aus Quellen neu berechenbare Beobachtungen** (tatsächlich angefragte KI-Bewertungen, ggf. manuelle Analystenhinweise/Klassifikationen/Anomalie-Annotationen) append-only mit Provenienz; Überarbeitung über neuen Satz + `supersedes`, nicht Historie überschreiben.
- **Lücken-/Coverage-Informationen als First-Class-Qualitätsangaben** (z. B. fehlende Provider-Usage, fehlender Brett-Snapshot, nicht ausgeführter Zug). Das muss nicht zwingend eine zweite Roh-Eventzeile sein; darf aber in Abfragen und Filtern nicht verschwinden.
- **Tarifkarten** dürfen im bestehenden separaten, lokal editierbaren Metadatenstore bleiben. Für reproduzierbare Lab-Fälle muss der **tatsächlich angewendete Tarifwert/Snapshot oder unveränderlich auflösbare Tarif-Revision, Gültigkeitszeit und FX-Rate** referenziert werden. Diese Referenz ist kein weiterer Matchdatensatz.
- **Viewer-Prinzip:** iframe ist UI; nicht technische Eigentümerin des Datenbestandes. Observer und Lab konsumieren dieselbe Metrikbibliothek.

## 4. Konkreter Minimalvertrag (Vorschlag)

| Einheit | Pflichtreferenz / Identität | Gültigkeitsregel |
|---|---|---|
| Match | `logical_match_id`, `source_json_sha`, `source_jsonl_sha`, `ruleset_version`, `config_fingerprint` | Keine Resume-Doppelzählung |
| Ereignis | `segment_id`, `source_event_id`, `event_x`, `event_timestamp` | Originalindex ≠ ausgeführter Zug |
| API-Aufruf | `api_call_id`, `actor`, `provider`, `actual_api_model_id`, `attempt_status` | Aufruf ≠ erfolgreiche Aktion |
| Ausführung | `executed_action_id` (nullable), `legal_status`, `phase` | Für USD/erfolgreiche Aktion korrekt zählen |
| Usage | Input, Output, Cache, Reasoning nullable; `usage_profile`; `source_status` | Provider-Inklusion ohne Doppelzählung |
| Kosten | `metric_method_version`, `tariff_revision`, `fx_rate/as_of`, `cost_component` | Berechenbare Schätzung, nicht Originalrechnung |
| GI-Annotierung | **`assessment_request_id`**, Match, X, `snapshot_fingerprint`, tatsächliches Evaluator-Modell, `knowledge_cutoff`, `assessment_timestamp`, Methode, Urteil | Zwei Abfragen für dasselbe X/Modell dürfen **nicht kollidieren**; keine Y→X-Leakage |
| Pattern/Lücke | Quellzustand + Algorithmusversion + Data-Quality-Flags + ggf. Klassifikations-ID | `reconstructed`/heuristisch/fehlend getrennt |

**Präzisierung gegenüber dem ersten DS-Vorschlag:** Ein Schlüssel nur aus `source_hash + event_x + observation_type` ist für mehrfaches manuelles KI-Bewerten nicht eindeutig. Für authentisch wiederholte Bewertungen eine stabile **Request-/Assessment-ID** als Identität vorsehen; für Retries derselben Netzwerkübermittlung dieselbe ID zur Idempotenz wiederverwenden. Das gilt analog für mehrere Spieler, Segmentereignisse oder verschiedene Algo-Versionen.

**Qualität ist möglicherweise mehrdimensional:** Ein auf rekonstruiertem Brett basierendes LLM-Urteil ist *gleichzeitig* `source=reconstructed` und `derivation=llm_assessment`; nicht auf genau ein Enum reduzieren. Fachliche Regelbestätigung ist ein weiterer, unabhängiger Status.

## 5. Erste Forschungsfälle als Vertrags-/Abnahmetests

### UC1 — Setup-Benchmark: Zeit, USD und erfolgreiche Setzung

**Frage:** Welche Unterschiede zeigen Modelle bei der 16-Steine-Go-Setup-Aufgabe über Anbieter, Uhrzeit und Konfiguration hinweg?  
**Gegenhypothese:** Der beobachtete Unterschied verschwindet nach Anpassung für API-Retries, Modell-Updates, Thinking/Prompt-Umfang und Setup-Abbruch.  
**Metriken:** Setup-Dauer, Calls, ausgeführte Setzungen, Retries, Input/Output/Reasoning, USD/erfolgreiche Setzung; Match als Beobachtungseinheit. Kurze/abgebrochene Tests behalten, klar klassifizieren.  
**MVP:** einige mit gleichen Konfigurationen belegte Setups und ihre Quellen vergleichen.

### UC2 — Spiegelungsverdacht vs. Brettdichte

**Frage:** Bleiben Geometry-/Mirror-Signale in wiederholten Match-/Farbtausch-Konstellationen auffällig?  
**Gegenhypothese:** Hohe Brettdichte erzeugt den Effekt bei zufälliger/geometrischer Belegung.  
**Metriken:** Musterhäufigkeit/Serienlänge/Achsentyp/Brettdichte pro Match; dichteangepasste Gegenkontrolle und Originalevent-Drilldown. Keine direkte Behauptung einer KI-Strategie.

### UC3 — Bewertung, Kosten und Lagewechsel

**Frage:** Stehen LLM-Urteilswechsel zu bestimmten X häufiger in zeitlichem Zusammenhang mit API-Latenz/Thinking/Kosten-Ausreißern?  
**Gegenhypothese:** Unterschiedliche Bewertungsmodelle, Stichprobenauswahl oder positionsbedingte Änderungen erklären die Unterschiede.  
**Metriken:** X-bindende GI-Samples mit Modell-/Prompt-Fingerprint, daneben zeitgleiche Economy-Werte, **sichtbare echte Lücken**. Keine Änderung zu einem automatischen GI-Timer und kein unkritisches Modellmittel.

## 6. Drei kleine Inkremente und Gates

### P0 — Während 8080/8082-Sync: nur read-only
1. **Ist-Datenfluss und Schreiborte auditieren:** Wo liegen GI-Samples heute (Browser/Python/Archiv)? Wo werden Pattern-Marker erzeugt? Welche existierenden Data-/Evidence-API-/SQLite-Tabellen und Metriken gibt es tatsächlich? Provider-Usage pro Modell, Tarifrevision, FX und fehlende Werte zählen. Keine Live-DB-Migration.
2. **Verträge und Golden Fixture festlegen:** vorgeschlagenes Match `andy_cc11a6598bcf@X=37` nur nach realer Verfügbarkeit und Quellenhash-Abgleich als Golden Fixture markieren; ergänzend ein älteres Legacy-Match, ein Grok-Reasoning-Fall und ein Replay-Rekonstruktionsfall. Zwei unabhängige Leser müssen **dieselben Match-/X-Werte** aus denselben Quellen/Tarifen berechnen.

### P1 — Erst nach erfolgreichem Sync und gesonderter Freigabe
3. **Ein minimaler versionierter Metrik-/Annotation-Pfad:** zuerst *eine* exemplarische Economy-Metrik (z. B. USD/erfolgreiche Setup-Setzung) und *einen* Annotationstyp (z. B. manuelles GI-Sample) über die bestehende Data-Evidence-Projektion für Observer **und** Lab abfragbar machen. Idempotenz, Provenienz, Snapshot-Cutoff und Regression nachweisen; dann weitere Metriken/Marker schrittweise anschließen.

**Keine sofortigen** zweiten Datastores für Matchdaten, unkontrollierten dual-write, automatischen Full-GI-Backfill, Schema-Big-Bang, offenen API-Aufrufen, Spielregel-/Accounting-Mutationen oder Änderungen der Factory 8083.

## 7. Konkrete nächste Arbeitsaufträge (DS/Q-Arbeitsteilung)

- **DS, während Sync:** Normalisierungs-/ID-Schema, Quality-/Coverage-Profil, mögliche bestehende Data-Schreib-/Lesewege, minimalen Import-/Idempotenzvertrag und eine schmale Golden-Fixture-Testliste als Dokument vorbereiten.
- **Q, während Sync:** Drei Forschungsfälle in kontrollierte Variablen, Nenner, Kohorten, Konfounder, Gegenhypothesen und aussagekräftige Views übersetzen; besonders die Einheiten Match/Serie vs. Event klar spezifizieren.
- **App/Integration nach Sync:** gemeinsam kleinsten ausführbaren Datenweg anhand lokal geprüfter Quellen und Diffs entscheiden, erst nach Regression freigeben.

## 8. Geltung

Dieser Text hält **Review-Konsens, Dissens und eine empfohlene Anschlusslösung** fest. Er ersetzt **keine** Abstimmung über den produktiven Datenbank-Vertrag und ist **keine** Freigabe für Commit/Installer/Sync/Migration. Die funktionierende Live-/Replay-/Economy-Oberfläche auf 8082 sowie die Studio-Gates bleiben geschützt.

**Praktische Leitlinie:** *Eine Quelle. Ein nachvollziehbarer Datenvertrag. Berechnungen einmal definieren. Neue Erkenntnisse als Annotationen. Das Living Lab fragt dieselben Daten ab wie der Observer.*
