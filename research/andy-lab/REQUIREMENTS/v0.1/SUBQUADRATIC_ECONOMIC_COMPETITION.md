# Subquadratic – Kandidat für ökonomische Wettbewerbsfähigkeit
Stand 14.11.2026 · Research Memo v0.1 · Kandidat, keine Freigabe

## Geschäftliche Relevanz
Money: Nicht allein die stärkste KI zählt, sondern welche adaptive Wirksamkeit bei begrenztem Geld-, Zeit- und Tokenbudget erzielt wird. ANDY kann diese Dimensionen in einer gemeinsamen Wettbewerbssituation getrennt sichtbar machen. Ein günstiger Tarif allein ist kein Effizienznachweis: Fehler, Wiederholungen, Abbrüche, tatsächliche Leistung und Folgekosten sind relevant. ANDY ist ein experimenteller Proxy, keine Validierung realer Unternehmensprozesse.

## Anbieter und API (Dokumentationsstand 14.11.2026)
| Modell-ID | Zugang / Aufgabe | Input USD/MTok | Output USD/MTok | Cache Read USD/MTok |
|---|---|---:|---:|---:|
| subq-savant-1.4 | Early Access je Organisation; generatives Reasoning, 4M Kontext | 0.10 | 0.50 | 0.01 |
| subq-snap-1.2 | öffentlich für Accounts; strukturierte Entscheidungen, separater Endpoint | 0.04 | 0 | nicht ermittelt |

API-Basis https://api.subq.ai/v1; Savant Chat Completions und Responses, Snap POST /v1/systemone. GET /v1/models prüft tatsächliche Freischaltung. Versionierte IDs statt latest verwenden. Savant: Temperature 1 fest, Reasoning obligatorisch, Effort low/high/max, Standard high. Reasoning ist bereits in completion_tokens enthalten; Cache Read in prompt_tokens_details.cached_tokens. Endpoint-spezifische Semantik und Limits mit CACHE-01/Usage Normalizer prüfen. Snap 1.2 Release 11.11.2026; strukturiertes Auswahlverfahren nicht mit freier Zugerzeugung gleichsetzen.

Quellen:
- https://docs.subq.ai/using-the-api/models/
- https://docs.subq.ai/using-the-api/
- https://docs.subq.ai/using-the-api/release-notes/
- https://docs.subq.ai/endpoints/models-api/
- https://console.subq.ai

Architektur: Anbieter positioniert sich über subquadratische Sparse Attention für lange Kontexte. Potenzielle Vorteile sind ein Forschungsimpuls, keine unabhängig bestätigte Leistungs- oder Skalierungsaussage. Andere Modelle können ebenfalls sparse/hybride Attention verwenden; Unterschiede im Spiel nicht monokausal der Attention zuschreiben.

## Ökonomischer Vergleich (hypothetisch)
Pro Akteur 175000 Input + 175000 Output, keine Cache Reads oder Zusatzgebühren, Novembertarife aus API_COSTS_CACHE_2026-11.md:
| Modell | USD |
|---|---:|
| Astra | 10.50 |
| Opus | 4.20 |
| Argon | 2.10 |
| Flash 3.8 | 0.7875 |
| Savant | 0.105 |
Savant wäre tariflich bei genau dieser Verteilung 100-mal günstiger als Astra. Kein Nachweis gleicher Qualität oder realer Matchkosten. Snap aufgrund anderer Aufgabe/Ausgabe nicht in diesen Vergleich aufnehmen.

## Drei getrennte Einsatzpfade
A Arena: Savant als GPAI-Kandidat mit identischer Aufgabenstellung, legaler Aktionserzeugung und versioniertem Profil. Zuerst technische Machbarkeit (JSON-Format, Regelbefolgung, Reasoning/Outputlimit, Budget, Fehler, Usage, Latenz) prüfen. Danach kleine wiederholte Serien mit Farbwechsel gegen etablierte Modelle. Einschränkungen dokumentieren; kein erzwungener gemeinsamer Parameter, wenn Provider ihn nicht unterstützen.
B Lab: lange JSONL-/Serienkontexte für explorative Vorauswahl auffälliger Situationen. Originalevents, deterministische Berechnungen und Quellenreferenzen bleiben maßgeblich. Keine privaten Daten ohne Freigabe übertragen.
C Rollenteilige Systeme: Snap als Auswahl-/Bewertungsmodul für engine-validierte Optionen neben generativem Strategiemodell; eigenes Versuchsfeld, keine Vermischung mit regulärem GPAI-Ranking. Gesamtkosten aller Rollen/Calls erfassen.

## Best-of-Erweiterung: Economic Competition View
Anschluss LAB-R03/R11 und CACHE-01. Zwei ergänzende Vergleichsansichten: gleiches Tokenbudget (bisherige Regeln) und separat experimentell gleiches monetäres Budget. Letzteres erfordert eigenes freigegebenes Regel-/Abrechnungsprofil, kein stiller Wechsel der Siegbedingungen.
- Kosten je Match, Serie, Akteur, Phase und ausgeführter Aktion inklusive Fehler/Retry.
- Kosten je erfolgreichem Abschluss bzw. Sieg über wiederholte vergleichbare Versuche (Nenner offenlegen, bei null Erfolgen nicht definiert; keine Abbrüche aussortieren).
- Ergebnis, Kosten, Zeit, Restbudget, Fehlerquote und Brettentwicklung nebeneinander; Streudiagramme und Pareto-Front (z.B. geringere Kosten bei vergleichbarer Erfolgsquote), keine pauschale gewichtete Gesamtnote.
- Rechnung vs tarifbasierte Schätzung, Preisversion, Cache-Hits, Kontext und Abdeckung kennzeichnen. Tokenizer-Unterschiede berücksichtigen.
- Situation Challenge / Punch Lab: bei validiertem S0 und gleichen Versuchsbedingungen Kosten und Reaktion auf Störungen explorieren; keine Kausalbehauptung zur Architektur.
- Sweet Spot: mögliche Balance von ökonomischer Ressourcenbelastung, adaptiver Wirksamkeit und Stabilität, abhängig von Situation und Gegner.

## Nächste Schritte / Status
Zugang zu Savant durch Projektleitung beantragen; Thread 1 kann danach Schnittstellenprüfung und begrenzten Pilot vorschlagen. Keine Zugangsdaten veröffentlichen, keine kostenpflichtige Anfrage ohne Freigabe. Keine tatsächlichen API-Tests, keine unabhängige Architekturvalidierung, keine App-Änderung oder neue offizielle Hypothese. Priorisierung offen. Erleben – Erforschen – Erahnen.
