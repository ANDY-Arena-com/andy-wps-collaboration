# ANDY 2.0 — Handoff an den G-Analyzer-Thread
**Stand: 23. November 2026, nach dem aktuellen Economy-/Studio-Sync-Screenshot**  
**Ziel:** Die **forschende Interpretation** im eigenen G-Analyzer-Thread auf die inzwischen belegte Arena-/Observer-/Economy-Evidenz bringen. **Keine zusätzliche Lab-/Data-Implementation aus diesem Handoff.**

## 1. Neuester empirischer Fall: Astra vs. Gemini 4 Argon

Vom Nutzer am 23.11.2026 im Entwicklungs-Chat per Observer-Screenshot gezeigt:

| Größe im gewählten vollständigen Ausschnitt | Weiß — Astra (`gpt-6-astra`) | Schwarz — Gemini 4 Argon (`gemini-4-argon`) |
|---|---:|---:|
| API-Aufrufe | 117 | 132 |
| protokollierte API-Zeit | 5.727,5 s | 2.664,3 s |
| Input-Tokens | 102.342 | 134.220 |
| Output-Tokens | 137.594 | 4.834 |
| separat ausgewiesene Reasoning-Tokens | 131.745 | nicht vorhanden / unbekannt |
| tarifbasierte Kosten (USD) | **7,90312** | **0,31678** |
| Umrechnung bei 1 USD = 0,91 EUR | 7,19184 EUR | 0,28827 EUR |
| Input-Kosten | 1,02342 USD | 0,26844 USD |
| Output-Kosten | 6,87970 USD | 0,04834 USD |

Match im Screenshot: **`andy_0c0f7413fdf6`**, Observer **Ereignis X=251/251**, **249/249** API-Aufrufe mit Kostenwert. Kumulierte Gesamtkosten: **8,21990 USD** (Summe beider im Screenshot angezeigter Kostenwerte). Astra kostet in diesem konkreten Ausschnitt **ca. 24,95-mal** so viel wie Argon, bei **15 weniger API-Aufrufen**, aber **ca. 28,5-mal so vielen Output-Tokens**. Verhältnis = rein deskriptiver Vergleich, **keine Aussage über Gewinn/Spielstärke oder universelle Anbieterpreise**.

**Wichtige Grenzen:**
- Der Screenshot zeigt **kein hier verifiziertes offizielles Endergebnis**. Nicht behaupten, wer gewonnen hat.
- Die Preise stammen aus **freigegebenen November-2026-Tarifkarten** und berechneten Legacy-/Usage-Werten; **nicht** mit einer geprüften Provider-Rechnung gleichsetzen.
- Novemberkarten gelten zeitabhängig und Provider-/API-Route-abhängig; EUR-Zahl beruht auf im UI eingestellter Rate 0,91, **kein historischer FX-Marktnachweis**.
- Bei Argon ausgewiesenes Reasoning „–“ ist **kein Beweis von 0 Thinking-Tokens**. Bei Astra können Reasoning-Tokens in den Output-Tokens enthalten sein; **keine Doppelzählung**.
- `Ereignis X`, API-Aufruf, Attempt/Retry, ausgeführte Aktion und Spielzug bleiben verschiedene Einheiten. **Kein „Kosten pro Zug“ ohne sauber definierte Denominator.**
- Das Screenshot-UI zeigt einen gespeicherten Replay-/Observer-Zustand. Die ursprüngliche JSONL war im vorangegangenen Audit am erwarteten Ort **nicht auffindbar**: `SKIPPED_NO_MATCH_EVENTS`; direkte Neubewertung einzelner 249 Events und eventgenaue Datenqualität **noch nicht unabhängig validiert**.

## 2. Was die App inzwischen tatsächlich kann

Am 23.11. lokal im Browser gezeigt: **ein gemeinsamer, verschiebbarer, skalierbarer iframe-Observer** für Live/Replay, umschaltbar zwischen **Muster/Spiegelung**, **Game Intelligence / KI-Einschätzung**, **Economy / Zeit / Token / USD/EUR**.

- **Muster:** Live- und Replay-Verläufe, geometrische/Spiegelungsmarker, Mini-Brett. Marker sind Heuristiken; sie beweisen keine strategische Intention.
- **KI-Einschätzung:** expliziter Benutzerauftrag **„Bewerten“ bei Ereignis X**, unabhängiges Evaluator-Modell, Perspektiven Schach/Go/ANDY Gesamt, Modell-/X-Provenienz; subjektives Urteil, keine offizielle Wertung, keine automatische Bewertung jedes Zugs.
- **Economy:** protokollierte Dauer, Token/Usage, getrennte Ein-/Ausgabe-/Cache-/Reasoning-Felder, kostenbasierte Zeitreihen pro Spieler; ohne neue LLM-Calls. **Tarifbasierte Schätzung**, kein Live-Billing.
- **Studiosync:** Der SYNC02-Codepfad wurde für 8080 vorbereitet und vom Nutzer später in der App sichtbar getestet. Ein anschließender read-only Tarif-Audit zeigte: 8080-Tarif-DB fehlte, 8082 hatte 15 Karten (13 approved, 2 draft). Daraufhin wurde ein einmaliger **approved-only** Transfer für 8080 mit Dry Run vorbereitet. Der aktuell gezeigte Browserstand **249/249 mit Kostenschätzung** belegt funktionierende Kostenanzeige im beobachteten App-Stand; **der eigentliche --apply-Log, Herkunft aller Werte, gesamte 8080-Regression und Git-Code-Commit sind damit nicht automatisch nachgewiesen**.
- Keine pauschale Neuimplementierung von Living Lab / Data: Produktplan ist dokumentiert, operative Priorität bleibt Studio-Sync, Browser-/Designer-/Replay-Regression und Tech-Debt-Audit.

## 3. Forschungsinterpretation für den G-Analyzer — keine Tatsachenbehauptung

**Erleben → Erforschen → Erahnen**: Die Beobachtung hoher Kosten/Thinking-Output öffnet neue Fragen, aber noch keine kausale Schlussfolgerung.

**Drei prüfbare Fragen aus dem neuen Fall:**
1. **Ressourceneffizienz:** Welche Teilphasen (Go-Setup, Chess, spätes Go), Fehlversuche und erfolgreichen Aktionen verursachen den Kostenvorsprung? Vergleich nur nach gleicher oder kontrollierter Spielsituation und nachvollziehbarem Usage-Profil.
2. **Thinking und Wirkung:** Wann korreliert mehr Output/Reasoning und API-Zeit mit *tatsächlich ausgeführten legalen Aktionen*, Stellungsverbesserung oder sportlichem Ergebnis? Kein automatisches „mehr Thinking = stärker“.
3. **Kosten gegen Spielkonfiguration:** Sind die Unterschiede stabil über Farbwechsel, Budget, Output-Cap, Modellspezifikation, Provider-Route, Matchup und Zeitfenster? Eine einzige Partie erlaubt noch keine universelle Modellwertung.

**Weiterführender Analyzer-Kontext aus dem separaten G-Analyzer-Gespräch:**
- Wahrnehmung / **Eindruck vs. Ausdruck** nicht vermischen: vom Betrachter zugeschriebene strategische Stärke ist keine direkt nachgewiesene innere Eigenschaft.
- Die **Logo-/Geometrie-Philosophie** als *explorative Hypothese* behalten: Können Form, Spiegelung und Muster mit späteren Ergebnissen oder Rollenwechseln korrelieren? *Keine* Behauptung über einen bisher verifizierten Kausalzusammenhang oder „bewusste Absicht“ des Modells.
- **Wirkung, tatsächliche Stärke und zugeschriebene Macht** getrennt betrachten: Beobachtete Muster werden erst durch wiederholbare Evidenz belastbar.
- Frühere Fälle **S150 vs. S350**, **Fable nach Refund**, **Grok ANDY-Tokens vs. Provider-Usage**, **Qwen-Stop/Deadlock** weiter als Forschungsfälle belassen, jedoch Daten/Status nicht ohne Originale oder neue Validierung aktualisieren.

## 4. Methodische Leitplanken

- Primärbelege: unveränderte `<match_id>.jsonl` plus `<match_id>.json`; abgeleitete SQLite-Ansichten, Observerkurven und LLM-Urteile sind unterschiedliche Evidenzstufen.
- Match-ID, Episode/Resume-Segment, Original-Zeitstempel, Event X, tatsächliche Modell-ID/Provider-Route, Tarifversion, Evaluator-Modell, Rechenmethode und Datenqualität je Auswertung nachvollziehbar halten.
- Unterschied zwischen `runner_reported` und `engine_independently_verified`, zwischen rekonstruierter und geprüfter Brettstellung, zwischen `decision` und `executed`.
- Nicht verifizierte oder alte Fälle explizit als solche markieren; keine stillschweigende Korrektur von Ergebnissen, Original-JSONL oder historischem Usage.
- Kein zweiter unabhängiger Analysedatenbestand; zukünftiges Living Lab benutzt bei Freigabe denselben Evidence-/Metric-Vertrag.
- **Keine neuen Modelle anrufen, keine Partien spielen, keine neue UI/DB bauen**, nur um diesen Thread-Handoff zu verarbeiten.

## 5. Konkrete Bitte an den Analyzer-Thread

1. Diesen Stand in seiner laufenden Forschungs-/Hypothesenübersicht **als neuen datierten Beobachtungsfall** aufnehmen; bestehende Theorien nicht rückwirkend bestätigen.
2. **Maximal drei** kurze, falsifizierbare Hypothesen benennen, insbesondere zu `Thinking/Output/Kosten ↔ sportlicher Wirkung`, `Muster/Logo-Geometrie ↔ Ergebnis` und `Wahrnehmung ↔ zugeschriebene Modellstärke`.
3. Als nächstes **eine** bereits vorhandene Partie oder kontrollierte Serie wählen, an der eine der Hypothesen ohne neue kostspielige API-Aufrufe prüfbar wäre. Falls Rohquelle nicht vorliegt: als Datenlücke dokumentieren.
4. Erkenntnis-/Methodenarbeit im Analyzer lassen; **kein neuer Lab-/Data-Implementierungsauftrag**.

## Verknüpfte Projektquellen

- [Observer/GI/Economy Stand, 23.11.](ANDY_LIVE_OBSERVER_ECONOMY_STATUS_2026-11-23.md)
- [DS/Q-Konsens und Evidence-Metrik-Vertrag](ANDY_OBSERVER_DATA_LAB_DS_Q_SYNTHESIS_2026-11-23.md)
- [Tarifapproved-only Sync02: Befund, Vorsicht und Grenzen](ANDY_TARIFF_SYNC02_STUDIO_APPROVED_ONLY_2026-11-23.md)
- [Sync-/Regressionprozess](ANDY_DEVELOPMENT_REGRESSION_POLICY_2026-11-21.md)
- [Lab-Requirements v0.1](../research/andy-lab/REQUIREMENTS/v0.1/README.md)
- [G-Anaylzer Casebook-/Thread-Übergabe] — falls ein separates Analyzer-Dokument existiert, diesen Handoff dort **nur nach Identifikation des korrekten Pfads** referenzieren.

**Status des Handoffs:** In GitHub dokumentiert. **Nicht automatisch als Nachricht in einen anderen ChatGPT-Thread übertragen**; der Link ist zur manuellen Weitergabe bestimmt.
