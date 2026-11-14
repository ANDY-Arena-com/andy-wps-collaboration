# ANDY Lab – API-Kosten und Prompt-Caching
Stand 14.11.2026 · Tarif-Snapshot v0.1 · temporäre Planungsgrundlage, keine Rechnungsdaten.

## Standardpreise USD je 1 Million Tokens
Direkte Text-API, Standard, kurzer Kontext/global, bezahlter Tarif, ohne Steuern, Tools oder Sonderrabatte. Exakte API-Modell-ID, Anbieterroute, Kontextklasse, Tier und tatsächliches Nutzungsdatum vor historischer Kostenberechnung prüfen.

| Modell | Input regulär | Output inkl. abrechenbarem Thinking | Cache Read | Cache Write / Storage |
|---|---:|---:|---:|---|
| gpt-6-astra | 10 | 50 | 1 | 12.50 (30m), 25 (12h) |
| gpt-6.1-sol | 2 | 10 | 0.10 | 2.50 (30m), 5 (12h) |
| Claude Opus 5.5 | 4 | 20 | 0.20 | 5 (5m), 8 (1h) |
| Claude Sonnet 5.5 | 2 | 10 | 0.10 | 2.50 (5m), 4 (1h) |
| gemini-4-argon | 2 | 10 | 0.10 | nur implizit |
| gemini-3.8-flash | 0.75 | 3.75 | 0.075 | explizite Speicherung 0.50/MTok/h |
| gemini-3-flash-preview | 0.50 | 3 | 0.05 | explizite Speicherung 1/MTok/h |
| grok-4.7 | 2 | 6 | 0.50 | hier nicht ermittelt |

Argon ab 01.12.2026 4/20/0.20. Flash 3.8 ab 01.01.2027 1.50/7.50/0.15, Storage 1/MTok/h. OpenAI- und xAI-Kontext-/Service-Tiers abweichend; die kumulierte Matchsumme ist NICHT die Kontextlänge eines Requests. Google Flash Legacy-Label aus ANDY noch mit API-ID abgleichen. Free-Tier nicht unterstellen.

Weitere seltenere Modelle, nur zur Orientierung, keine automatische Zuordnung zu historischen ANDY-Labels: DeepSeek-V4-Pro-0813 (deepseek-v4-pro) Peak Input 1.32/Output 3.96/Cache Hit 0.044, Off-Peak 0.66/1.98/0.022; deepseek-flash (V4.1-Flash-1017) Peak 0.30/1.20/0.006, Off-Peak 0.15/0.60/0.003. Peak werktags 01–04 und 06–10 UTC außer chinesischen Feiertagen laut aktueller Liste. Qwen und Mistral: exakte historische API-ID/Region offen, keine Schätzpreise einsetzen. Zufallsengine: keine Modell-API-Gebühr, Infrastrukturkosten nicht erfasst.

## Quellen (abgerufen 14.11.2026)
- https://developers.openai.com/api/docs/pricing
- https://developers.openai.com/api/docs/guides/prompt-caching
- https://platform.claude.com/docs/en/about-claude/pricing
- https://platform.claude.com/docs/en/models/opus-5-5/whats-new-opus-5-5
- https://platform.claude.com/docs/en/build-with-claude/prompt-caching
- https://ai.google.dev/gemini-api/docs/pricing
- https://ai.google.dev/gemini-api/docs/caching
- https://ai.google.dev/api/generate-content
- https://cloud.google.com/model-garden/pricing (ergänzende Google Cloud Liste; nicht mit Developer API vermischen)
- https://docs.x.ai/developers/pricing
- https://api-docs.deepseek.com/quick_start/pricing/?model_version=DeepSeek-V4-Pro-0813
- https://www.alibabacloud.com/help/en/model-studio/model-pricing

## Warum Caching für ANDY interessant ist
Wiederverwendbare identische Prompt-Präfixe (Regeln, Systemanweisungen, Schema) können bereits berechnete Zustände wiederverwenden; wechselnde Brett-/Zuginformationen bleiben dynamisch. Cache ist keine Wiederverwendung einer fertigen Zugantwort und kein Beleg für gemeinsame Gedanken. Mindestlänge, TTL, Routing, Modell-/Account-Isolation und Präfixgleichheit entscheiden über Treffer. Google 3.8 Flash z.B. 4096 Mindesttokens laut Caching-Doku; derzeitige ANDY-Prompts können kürzer sein, tatsächliche Treffer offen. Argon nur implizit laut Preisübersicht. Cache kann Kosten und Prompt-Verarbeitungszeit senken, nicht notwendigerweise Output-Reasoning. Keine artificial padding ohne Kosten-/Latenztest.

Providersemantik:
- OpenAI GPT-5.6+: Input umfasst Reads/Writes. Uncached = input_tokens minus cached_tokens minus cache_write_tokens; Writes nach TTL-Komponenten aufteilen, nicht erneut addieren. Output-Reasoning soweit enthalten nicht doppelt zählen.
- Anthropic: input_tokens ist nur uncached; Gesamtinput = input_tokens + cache_read_input_tokens + cache_creation_input_tokens. Writes nach 5m/1h aufteilen. Unterschied ist für ANDY-Budgetvergleich kritisch.
- Gemini generateContent: promptTokenCount schließt cachedContentTokenCount ein; candidatesTokenCount und thoughtsTokenCount getrennt; toolUsePromptTokenCount gesondert berücksichtigen gemäß Abrechnung. Interactions hat anderes Usage-Schema. Prüfen, ob historischer Adapter nur sichtbare Ausgabe erfasst hat; fehlendes Reasoning nicht als null behandeln.
- xAI/DeepSeek: native Usage-Semantik erst prüfen, keine pauschale Zuordnung.

## Kostenrechnung / Requirements-Impuls
Kosten = Summe der disjunkten abrechenbaren Tokenkategorien mal jeweiliger Tarif / 1e6 plus separat abgerechnete Storage-/Toolgebühren. Summe requestweise (Datum, Tier, Kontextklasse), dann Akteur, logisches Match, Serie, global. Fehlende Felder = unbekannt, nicht null. Schätzung getrennt von Anbieterrechnung und historischen Tarifständen; Cache Read ist kein kostenloses Token. Rekorde separat in USD und Tokens. Beispiel 175k Input + 175k Output ohne Cache: Astra 10.50 USD, Opus 4.20, Argon/Sol/Sonnet 2.10, Flash 3.8 0.7875. Keine Aussage über reale Matchkosten.

Ergänzung zu LAB-R03 und R11: versionierte Tariftabelle; Bar-/Kurvenansichten uncached/read/write/output, Cache-Hit-Anteil (read / total input), Kosten je Phase/Match/Serie, tatsächliche vs geschätzte Kosten, Tarifdatum und Abdeckung, USD pro ausgeführter Aktion. Für App-Handoff später native usage payload, exakte Modell-ID, Provider/API/Tier, Zeit, Preisversion, Cache-TTL, Prompt-Präfixhash, pseudonyme Account-/Projektgruppe erfassen; keine Schlüssel oder geheimen Prompts veröffentlichen. Vergleich Cache-Hit/Miss bei gleicher Konfiguration und gleichem Promptinhalt kann zur Erklärung von Latenzunterschieden beitragen, ohne daraus mentale Vertrautheit abzuleiten.

**Wichtig:** ANDY-Spielbudget, logische Tokenmenge und finanzielle Abrechnung trennen. Keine rückwirkende Regeländerung oder automatische Budgetentlastung für Cache-Tokens. Vor Änderungen Adapter und aktuelle Logs prüfen, insbesondere Gemini Thinking und Anthropic Cache-Felder. Historische Matchkosten nicht als exakt ausweisen. Kein neuer Implementierungsauftrag, kein API-Aufruf, keine Kostenfreigabe.


## Nachtrag 14.11.2026 – Subquadratic

| Modell | Input USD/MTok | Output USD/MTok | Cache Read USD/MTok |
|---|---:|---:|---:|
| subq-savant-1.4 | 0.10 | 0.50 | 0.01 |
| subq-snap-1.2 | 0.04 | 0 | unbekannt |

Quelle: https://docs.subq.ai/using-the-api/models/ (14.11.2026). Savant Early Access; Snap separate Decisions API, keine direkte Gleichsetzung mit generativen Modellen. Savant Reasoning in completion_tokens enthalten, cached_tokens Teil des Inputs. Cache-Schreib-/sonstige Gebühren hier nicht ermittelt. Details: [Research Memo](SUBQUADRATIC_ECONOMIC_COMPETITION.md).
