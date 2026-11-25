# 07 — Pilotdaten und belastbarer Stand / Gemini 4 Argon

**Datenstand:** bekannte S150-/S350-Analysen vom 14.11.2026 plus Observer-Beobachtung vom 23.11.2026. **Weder neue vollständige Original-JSONL-Abfrage noch frische produktive API-Liveprüfung** für die V1-Card vorgenommen. Die Werte sind dokumentierte historische **deskriptive Sekundäranalyse**; Publikationsfreigabe pro Fakt separat.

## Aktueller V1-Clickdummy: Gemini 4 Argon als EIN modellbezogenes Beispiel

| Scope / Match-ID | Argon-Farbe | Argon-Calls | Argon ausgeführt | Input | Output | Rahmen |
| --- | --- | ---: | ---: | ---: | ---: | --- |
| S150 R0 `andy_83f51171e438` | Weiß | 79 | 78 | 73.235 | 3.240 | partial, Segment-Overlap deduplizieren |
| S150 R1 `andy_93f0d66382aa` | Schwarz | 84 | 80 | 79.308 | 3.142 | partial |
| S150 R2 `andy_7278d457e3f6` | Weiß | 84 | 80 | 78.982 | 3.091 | vollständigerer Rahmen, Ruleset v1.1 |
| S350 R0 `andy_cc11a6598bcf` | Weiß | 107 | 104 | 101.775 | 4.002 | framed, Ruleset v1.1 |
| S350 R1 `andy_0c0f7413fdf6` | Schwarz | 132 | 116 | 134.220 | 4.834 | framed, Ruleset v1.1 |
| **Gesamt** | – | **486** | **458** | **467.520** | **18.309** | gemischte Rahmen/Voraussetzungen |

**Berechnet aus den Summen:** Ausführungsquote `458/486 = 94,24 %`; Output/Input `18.309/467.520 = 3,92 %`. Beides eigene Argon-Zähler/Verhältnisse, **nicht** ein Vergleich zu einem Gegner und **kein** Qualitäts-/Thinking-Score.

**Zeit (nur explizit eigener Modellpfad):** S350 R1 `andy_0c0f7413fdf6`: 2.664,3 Sekunden protokollierte eigene API-Zeit bei 132 Calls und 116 ausgeführten Aktionen, laut Observer-/Economy-Handoff vom 23.11. Das ergibt `116*3600/2664.3 = 156,7` eigene Aktionen pro aktiver API-Stunde und `2664.3/132 = 20,2` s je Call. **Tempoabdeckung nur 1/5 Partien!** Ein vollständiger JSONL-Timingaudit steht noch aus; keine 5-Partien-Geschwindigkeit behaupten.

**Keine Kosten-Summe** über diese fünf historischen Spiele abgeleitet: Tarifgültigkeit, Provider-/Route-Identität und Coverage für alle Spiele nicht belegt. `unknown != 0`.

## Ausdrückliche Grenzen

- S150 R0 beinhaltet überlappendes Segment, nicht als sechste Partie zählen; S150 R0/R1 unvollständiger Start-/Endrahmen. Historische Ruleset-/Engine-Version S150 R0/R1 offen. S150 R2 v1.1. S350 beide v1.1.
- S150 mit 150.000 Tokens, Outputcap 2.048 und Retry 4/5/4. S350 mit 350.000 Tokens, Outputcap 4.096 und Retry 5. Bedingungen **nicht als identisch** bezeichnen.
- Gleicher Displayname in alten Logs sichert nicht die exakte API-Checkpointidentität, Providerroute, Modellversion oder Account-/Netzwerkbedingungen.
- S350 ist eine Serie mit Farbwechsel und zwei Runner-Matt-Ausgängen; diese erscheinen auf einer Standalone-Argon-Card nicht als direkte Performance-Gegenüberstellung zu Astra. Gegner/Ergebnis nur Matchdetailkontext.
- Keine Reasoning-Tokens für Argon separat gemeldet: **unbekannt**, nicht null kognitiver Aufwand.
- Schach-/Go-Kontrolle aus Snapshotwerten und Phasenoutput ist keine unmittelbar vergleichbare Intelligenz-/Strategiepunktzahl.
- Das ursprüngliche HTML-V1 ist **kein neuer Originaldatenexport** und **kein WordPress-Plugin**.
- Neuere Ruleset-v1.2-GO-Saturation-Regel nicht auf diese historischen v1.1-Matches übertragen.

## Quellen (Github, überprüfbar)

- [S150 – drei logische Spiele, vier technische Segmente](../../ANALYSES/andy_83f51171e438/v0.1/README.md)
- [S350 – zwei reale logische Spiele](../../ANALYSES/andy_cc11a6598bcf/v0.1/README.md)
- [S350 – pro Match und Modell eigene Phasen-/Tokenwerte](../../ANALYSES/andy_cc11a6598bcf/v0.1/data.csv)
- [S350 – gemeldete Go-Kontrollstichproben](../../ANALYSES/andy_cc11a6598bcf/v0.1/go_samples.csv)
- [Observer – Argon-eigene API-Zeit und 249er Matchkontext](../../../../PROJECT/ANDY_G_ANALYZER_THREAD_HANDOFF_2026-11-23.md)
- [Evidenzvertrag – JSONL + Match-JSON + SQLite](../../../../PROJECT/ANDY_MATCH_EVIDENCE_JSONL_JSON_SQLITE_v1.0.md)

## QA-Voraussetzung vor Public

1. Mindestens einen realen lokalen APP-Export mit diesen 5 Match-IDs und deren Hashes/Deduplikation neu erzeugen; historische Summen abgleichen.
2. Eindeutige Modellidentität/Version, Eigen-API-Latenzen aller tatsächlich verfügbaren Dateien erneut aus Originalen lesen; vollständige Coverage erst dann behaupten.
3. Fehlende Werte und Konflikte als solche übergeben; Datenstände und Schema-/Metrikversionen fixieren.
4. WordPress-Rechte und separate redaktionelle Prüfung; keine direkte Übernahme dieser Pilotdatei als öffentliche produktive Card.

**Produktfrage:** Das Ziel ist nicht, andere Modelle zu übertreffen, sondern aus wiederholten Spielen dieses einen Modells *bedingt robuste, dokumentierte Verhaltensaussagen* zu entwickeln — und zugleich den Aufwand sowie die Grenzen unserer Beobachtung offenzulegen.
