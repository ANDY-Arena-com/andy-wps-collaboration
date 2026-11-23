# ANDY Live Observer → Data / Living Lab — Qwen Review 2

**Eingang:** 23.11.2026; vom Projektleiter als Textdatei zum DS-Feedback übergeben.  
**Quelle:** externes Qwen-Review, hier redaktionell strukturiert und in den Kernformulierungen dokumentiert; **keine neue Modellabfrage** und kein Code.  
**Status:** fachlicher Review, nicht Implementierungs-/Release-Abnahme.

## 1. Kurzfazit

Der Observer ist integrationsreif **als Renderer gemeinsamer Verträge und als eng begrenzter Annotationsproduzent, nicht als neue Datenwahrheit**. Zentraler Vorschlag: *deterministische Ableitungen* (Kosten, Kurven, Formationen) aus Original-Events mit versionierter Methode neu berechnen; **nicht erneut als unveränderliche Matchfakten archivieren**. Eigenständige manuelle GI-Urteile, ausgewählte Annotierungen und Qualitäts-/Lückenbefunde bleiben als versionierte append-only-Annotationen erhalten. **USD-/EUR-Summen und kumulative Verläufe sind berechnete Ansichten**, keine Originalereignisse. Zwei vorbereitende Audit-/Spezifikationsschritte im Umfeld des 8080/8082-Syncs, danach sehr kleine sichere Umsetzung.

## 2. Drei Stärken

1. **UI-Invarianten als Datenvertrag:** keine erfundenen Zwischenpunkte; Lücken sichtbar; unbekannt ≠ 0; Formations-/Spiegelungsmuster beweisen keine Intention.
2. **Manuelle Game Intelligence bei X:** Ein KI-Urteil ist eine Äußerung von Bewertungsmodell M zum fixierten Matchzustand X, angefragt zur Zeit T — keine intrinsische Wahrheit über X; X/Y-Zuordnung muss erhalten bleiben.
3. **Tarifkarten als versionierte Metadaten:** Die editierbare Tarif-SQLite darf getrennt von Spiel-Originalen bleiben, sofern jede Berechnung den angewendeten Tarif und Wechselkurs nachvollziehbar referenziert.

## 3. Drei Risiken und überraschende Gegenperspektive

1. **Berechnungs-Drift:** Wenn iframe und Lab eigene Summen-/Kostenformeln entwickeln, werden unterschiedliche Werte für dieselbe Quelle entstehen. Q nennt den sich fortschreibenden Screenshot-Beleg (32/32 bei 0,03062/0,31063 USD vs. später 36/36 bei 0,03485/0,36256 USD): andere Datenstände sind nicht notwendigerweise widersprüchlich, verdeutlichen aber Versionierung und As-of-Grenzen.
2. **Falsche Forschungseinheit:** Viele Events einer Partie sind nicht viele unabhängige Matches. Spiegelungen können durch hohe Brettdichte erklärt werden; von unterschiedlichen Bewertungsmodellen stammende GI-Kurven dürfen nicht zu einer „wahren“ Durchschnittskurve vermischt werden.
3. **Attempt-vs.-Action:** Fehlversuche, Retries und nicht ausgeführte Aktionen verzerren insbesondere „USD pro erfolgreichem Zug“.
4. **Überraschende Gegenperspektive:** Die **Lücken und Fehler** sind ebenso interessant wie die Kurven. Ein fehlendes Provider-Usage-Feld, ein nicht ausgeführter Zug, eine Retryfolge oder ein Resume-Segment sollte im Datenmodell als fehlende/abweichende Evidenz sichtbar bleiben, nicht als Null oder stillschweigend entfernte Zeile. Die manuelle „Bewerten“-Schaltfläche ist ein dokumentierbarer Sampling-Plan, kein Defizit, das durch automatische API-Aufrufe zu beseitigen wäre.

## 4. Vorgeschlagener Daten-/Analysefluss

```text
Original-JSONL/JSON  (read-only, source SHA)
    → versionierter Normalizer → Event-Ledger
                                ├→ eine gemeinsame Metric Engine
                                │    + Tarifkarten/FX als referenzierte Inputs
                                │    ├→ Observer (Render/Kurven)
                                │    └→ Living Lab (Kohorten, Match-Einheit)
                                └→ append-only Annotationen
                                     manuelle GI-Urteile, ausgewählte Pattern-Marker, Lücken-/Qualitätsflags
                                     Korrektur durch neue Version/supersedes
```

**Invarianten:** Ein fachlich autorisierter Schreibpfad pro Store; berechenbare Ableitungen dürfen als Cache existieren, sind dann aber löschbar/rebuildable; jede Ableitung kennt ihre Quelle und Versionskette. Observer und Lab dürfen keine unabhängig abweichenden Metric-Formeln führen. Reviewer schlägt minimal R1 `events.read`, R2 `metrics.query`, R3 `provenance.get` sowie W1 `annotations.append` vor. Das sind **Zielverträge**, nicht bestätigte existierende APIs.

## 5. Wichtige Felder / Metriken

| Feld oder Gruppe | Einheit, Qualität und Regel |
|---|---|
| `logical_match_id / segment_id / event_id(X)` | Originalereignis + Resume-Kontext; idempotente Zuordnung |
| `api_call_id / attempt_kind / executed_action_id` | Aufrufe/Fehler/Retry/ausgeführte Züge nicht verwechseln |
| `input/output/reasoning/cache + usage_profile` | Providersemantik; Reasoning `null` wenn nicht gemeldet; nicht doppelt berechnen |
| `cost_usd_estimate` + `tariff_version / FX(rate,as_of)` | Tarifschätzung; EUR aus Rate ableiten; nicht als Original-Rechnung verbuchen |
| `state_hash / fen_source` | reconstructed vs. independently engine_verified unterscheiden |
| `gi_tendency / uncertainty / evaluator_model_id / snapshot_fp / knowledge_cutoff / backfill` | KI-Urteil gehört zu X und Modell; spätere Y-Information ausgeschlossen |
| `mirror_marker` mit Achse, Serienlänge und Brettdichte | Heuristische Versionsableitung, nicht „KI-Strategie bewiesen“ |
| `gap_record` | fehlende Coverage als eigenes Qualitäts-/Lückensignal, kein falsches 0 |

## 6. Drei konkrete Forschungsfälle

1. **Kosten je ausgeführter Aktion**, aufgeteilt nach Anbieter/Modell, Phase und Farbe. Gegenhypothese: Unterschiede sind Retry-/Nenner-Effekte. Minimaler Prüfstein: vergleichbare 16-Steine-Go-Setups, Boxplots nach Match statt nur gepoolte Calls.
2. **Spiegelungsmuster über unabhängige Partien.** Gegenhypothese: vermeintliche Spiegelung ist durch Brettdichte erklärbar. Match als Einheit; dichte-kontrollierte Permutation/Baseline; Small Multiples statt unkritisch gepoolter Ereignisse.
3. **GI-Urteilswechsel und Economy-Ausreißer** zum selben Ereignishorizont. Gegenhypothese: beobachtete Änderungen sind Positionsrauschen oder ein Wechsel des Bewertungsmodells. Erforderlich: knowledge-cutoff-sichere Joins, Modell als Faktor, Lücken sichtbar.

## 7. Kleine Schritte / Tests

1. **Jetzt, während des Syncs:** Ein reproduzierbares Golden Fixture (vom Reviewer vorgeschlagen: `andy_cc11a6598bcf@X=37`) mit exaktem Dataset-/Tarif-/FX-Stand verankern; Ist-Schreibziele für GI-Historie und Tarife untersuchen; aus Original-JSONL/Tarifständen die Screenshot-Werte unabhängig reproduzieren.
2. **Nach Sync:** Idempotente persistente Annotationen über kontrollierten Write-Path; Duplikatimport ergibt genau ein Ereignis; `supersedes`-Kette und Zeitcutoff korrekt. **Keine automatische Änderung offizieller Matchhistorie**.
3. **Dann:** dieselben versionierten Metrikfunktionen sowohl Observer als auch Lab zur Verfügung stellen. Test: Golden Fixture sowie gleiche Matchwerte in 8080 und 8082 unter denselben Bedingungen.

**Ausdrücklich nicht bauen:** zweite Matchdatenbank, unveränderliche gespeicherte Gesamtkosten- oder EUR-Kurven, universelle Modell-Rankings, automatisch für jeden Zug angeforderte GI-Einschätzungen, unmarkiertes Backfill, vorgetäuschte Cent-/Rechnungsgenauigkeit, voreilige große Metric Registry ohne zweiten Consumer.

## 8. Offene Fragen

- Welche Provider-Felder sind je Modell tatsächlich abgedeckt, welche Kosten sind Legacy-Schätzungen? Grok #11 mit provider-abhängigem Reasoning-Verhalten.
- Sind Replayzustände pro Ereignis unabhängig verifiziert oder teilweise rekonstruiert?
- Wo liegt die GI-Historie aktuell auf 8082 und welches ist ihr Lebenszyklus?
- Wie werden verfügbare Annotationen und Replay-Snapshots versioniert, damit eine spätere Neubewertung den alten Erkenntnisstand nicht überschreibt?

## Koordinationshinweis

Die Qwen-Vorschläge sind als **eigenständige Review-Position** zu lesen, nicht als automatisch freigegebene Architektur. Zur DS-Position besteht weitgehender Konsens für einen kanonischen Datenvertrag; Unterschiede bestehen vor allem beim Umfang der persistierten abgeleiteten Events. Beides wird separat zusammengeführt.

**Originalantwort wurde im Chat als beigefügter Text übermittelt; diese GitHub-Datei ist eine inhaltstreue Arbeitszusammenfassung und keine wortgetreue Archivkopie.**
