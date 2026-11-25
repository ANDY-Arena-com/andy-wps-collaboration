# 02 — Metric Registry V1 / Zähler, Nenner und Semantik

**Prinzip:** erst Definition, dann Zahl, dann Grafik. Alle Metriken benötigen `metric_id`, `version`, `scope`, `unit`, `numerator`, `denominator` (sofern Rate), `coverage`, `method` und `evidence_status`. Verzeichnis ist ein **fachlicher Vertragsentwurf**, keine Behauptung bestehender gleichnamiger App-Funktionen.

## Identität / Grundgesamtheit

| Metrik | Definition | Einheiten / Grenze |
| --- | --- | --- |
| `logical_match_count` | Anzahl unterschiedlicher logischer Matches, in denen das Modell beteiligt war; Fortsetzungs-/technische Segmente desselben Matches deduplizieren | Spiele. Self-play = 1 Match, 2 Rollen. Refund-Branch getrennt |
| `model_appearances` | Anzahl individueller Rollen-/Teilnahmespuren dieses Modells | Vorkommen; kann bei Self-play größer als Matchzahl sein |
| `api_decision_count` | Anzahl verarbeiteter `decision`-Events / Providerantworten, inkl. abgewiesener Versuche, soweit zum Modell identifiziert | Entscheidungen, nicht notwendigerweise gleich mit HTTP-Requestanzahl bei Adaptern |
| `executed_action_count` | Summe `executed=true`-Entscheidungen und ggf. sauber zugeordneter ausgeführter Systemaktionen | Aktionen, nicht automatisch Schach-Vollzüge |
| `unexecuted_decision_count` | `api_decision_count - executed_action_count`, sofern vollständige Coverage | Nichtausführung, nicht gleich „illegal“ |
| `execution_rate` | `executed_action_count / api_decision_count` bei `decisions>0` und identischem Scope | Prozent. Keine Qualitäts-/Strategieskala |
| `chess_action_count`, `go_action_count`, `setup_action_count` | Tatsächlich ausgeführte Aktionen je korrekt interpretierter `phase` | Phase vor der Aktion aus Decision-Event; keine Doppelzählung |
| `failures_by_class` | Regelwidrig/Format/Outputlimit/Budget/Adapter/Core/Unbekannt nach versionierten Regeln | Klassen können Ableitung erfordern; keine pauschale Gleichsetzung aller nicht ausgeführten Calls mit Modellfehler |

**Zählvertrag:** Match-ID, Root/Parent/Segment/Refund, Rolle/Seite, Self-play und archivierte Source-Hashes dedupliziert. Ein Match mit fehlendem Start-/Endrahmen bleibt ggf. zugelassen, aber mit `frame_status=partial` und gesonderten Qualitätsflags.

## Zeit und Geschwindigkeit

| Metrik | Definition | Welche Zeit? |
| --- | --- | --- |
| `own_api_seconds` | Summe der relevanten `latency_ms / 1000` der **eigenen Modellentscheidungen** | Laufzeit des Provider-/Adapter-Call-Pfades, soweit tatsächlich geloggt |
| `actions_per_own_api_hour` | `3600 * executed_actions_in_time_covered_calls / own_api_seconds` | Aktionen pro Stunde *eigener aufsummierter API-Zeit*; keine gesamte Matchdauer |
| `mean_api_seconds_per_decision` | `own_api_seconds / time_covered_decision_count` | Durchschnitt über die tatsächlich abgedeckten Calls |
| `median_api_seconds`, `p95_api_seconds` | definierte Quantile der per Call geloggten `latency_ms` derselben gültigen Stichprobe; Quantilalgorithmus/version fixieren | Verteilung wichtiger als bloßer Mittelwert |
| `wall_clock_match_seconds` | Zeitspanne des vollständigen Matches aus Start/End oder Bericht | enthält die gegnerischen Calls, Stop/Pausen/Verzögerungen und Systemzeiten; **nicht als eigene Denkzeit ausgeben** |
| `time_coverage_games` | Anzahl logischer Matches mit vollständigen validierten Eigen-Latenzen / gewählte Matchzahl | immer als `n/N` zeigen |
| `time_coverage_calls` | Anzahl gültiger eigener Latenzwerte / eigene Decision-Events | aus fehlenden Calls keine Nullen interpolieren |

**Abdeckungsregel:** Eine Kennzahl mit der Beschriftung „Aktionen/Stunde über N Spiele“ darf nur N tatsächlich vollständig zeitabgedeckte Matches umfassen. Bei partiellen Daten können Call-Statistiken aus gültigen Calls angezeigt werden, aber **ohne die per Match berechnete Geschwindigkeit auf nicht abgedeckte Aktionen hochzurechnen**. Null, negativ, NaN, nicht plausible/fehlerhafte Timingwerte -> Qualitätsflag / Ausschluss aus Tempo, nicht stiller Ersatz durch Matchdauer. `elapsed_match_ms` und `cumulative_api_ms` der gesamten Partie nicht auf eine einzelne Seite buchen.

## Ressourcen

| Metrik | Formel / Semantik |
| --- | --- |
| `input_tokens`, `output_tokens` | Summe dokumentierter Usage-Felder eigener Calls, getrennt; unbekannte Felder nicht als 0 behandeln; Coverage nennen |
| `output_input_pct` | `100 * output_tokens / input_tokens`, wenn identische vollständige Call-Stichprobe und `input_tokens>0` |
| `input_per_decision`, `output_per_decision` | jeweilige Tokenmenge / Calls derselben vollständig abgedeckten Auswahl |
| `tokens_per_executed_action` | gesamte Tokens **einschließlich fehlgeschlagener Calls** / ausgeführte Aktionen der Auswahl, falls >0; klar etikettieren „einschl. Fehlversuche“ |
| `reasoning_tokens_reported` | separat gemeldeter Wert samt Semantik/Abdeckung, evtl. im Output enthalten; niemals unbesehen zusätzlich aufsummieren |
| `cached_tokens_reported` | sofern im Usage vorhanden, mit Provider-/Route-/Schema-Kontext; nicht pauschal von Input abziehen |
| `tokens_by_phase` | Setup, CHESS, GO anhand protokollierter Phasenzugehörigkeit; alle echten Calls mitrechnen |
| `remaining_budget` | historisches sportliches Konto gemäß jeweiligem Matchregelsystem; von Provider-Abrechnung/Preis trennen |

**I/O-Kennzahl:** `Output/Input` ist eine *Beobachtung der protokollierten API-Usage*, **kein direktes Thinking-Maß**, kein Effizienzscore und keine universelle Eigenschaft des Modells. Steigende Inputmengen können schlicht längere Spielhistorie/Promptkontexte abbilden. Erfolgsabhängige Wirkung wird als separate Evidenzspur geführt.

## Erhebungsaufwand / Ökonomie

- `sample_collection_own_api_seconds`: aufsummierte belegte eigene API-Laufzeit aller tatsächlich abgedeckten Partien plus Coverage; kein Vergleich zu anderen Modellen.
- `estimated_cost_usd` nur falls Kostenbasis vorhanden: Preis-/Tarifkarten-Version, Gültigkeit, Modell-/Routebezug, Input/Output/Cache/Reasoning-Semantik und Usage-Abdeckung nennen. **Schätzung**, nicht Providerrechnung; andernfalls `null`.
- Gesamtspiel-Wandzeit als separaten experimentellen Aufwand dokumentieren, nicht additiv über überlappende/parallel ausgeführte Partien ohne Zeitfensterabgleich.
- Teure/langsame Modelle können weniger Spiele in der Stichprobe haben: **Datenaufnahme-/Auswahlbias**, kein negatives Attribut.

## Klassifikation / methodische Register

- Outcomes: **Runner-reported** vs. **engine-independently-verified** und `unverified/conflict`. KO Chess, Go-KO, TKO Ressourcen, Go-Sättigungs-TKO (nur im passenden Ruleset), DRAW, ABORT, STOP, TECH je historischer Version unterscheiden.
- Interpretationsfelder: `bonoma_transition`, `sweet_spot_hypothesis`, `ssa_claims`, `recovery_episode` etc. dürfen zunächst `null` oder `not_evaluated` sein. Keine Pflicht, die Theorie „auszufüllen“.
- Series/Resume/Refund/Root-ID sind Teil des Scopes; Forschungs-Fortsetzung nicht in die reguläre Wettkampfzählung schmuggeln.
- Keine implizite Genauigkeits-/Vergleichbarkeitsgarantie aus steigender Spielzahl.

## Beispiel mit belegtem Denominator

Gemini 4 Argon, historischer S350-Match `andy_0c0f7413fdf6`: **132 eigene API-Entscheidungen, 116 ausgeführte Aktionen, 2.664,3 s eigene API-Zeit** aus lokalem Observer-Beleg. Daraus **156,7 ausgeführte Aktionen/Stunde eigener API-Zeit**; **20,2 s/Call**. Dies ist **nur 1 Spiel**, keine 5-Spiele-Geschwindigkeit und kein reiner Hardware-/Modellbenchmark.

Quellen: [S350](../ANALYSES/andy_cc11a6598bcf/v0.1/README.md) ist unter diesem Verzeichnislink nicht direkt erreichbar; kanonisch [S350-Matchanalyse](../../ANALYSES/andy_cc11a6598bcf/v0.1/README.md) und [Observer-Handoff](../../../../PROJECT/ANDY_G_ANALYZER_THREAD_HANDOFF_2026-11-23.md). Ein vollständiger eigener JSONL-Latenzaudit steht noch aus.
