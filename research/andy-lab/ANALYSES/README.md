# ANDY Lab – versionierter Serienanalysebestand

14.11.2026 – primärer aktueller Zweck: manuelle Analysen als fachliche Prototypen und Referenzfälle für Requirements des **neuen** ANDY Lab sammeln. Hypothesen und Bewertungen erst später. [Best-of Requirements & iterativer A/B/C-Prozess v0.1](../REQUIREMENTS/v0.1/README.md).

## Ablagekonvention
`ANALYSES/<series_id>/v<major>.<minor>/`: README.md mit Quellen-ID/Hash, Match-/Segment-IDs, Konfiguration, Methoden, Beobachtungen, Grenzen; maschinenlesbare CSV/JSON für belegte Kennzahlen und ggf. Verlaufspunkte. Jede neue Version als separater Snapshot, keine stille Überschreibung. Neue Exporte explizit referenzieren; identische Match-IDs nicht doppelt zählen. Fehlend ≠ null; Rohdaten getrennt halten, keine API-Secrets oder ungeprüfte Originalpakete veröffentlichen. Spätere Hypothesen/Interpretationen getrennt von Beobachtungsbestand und mit Versionsreferenz. Kein neuer App-Auftrag.

## Index
| Serie | Modelle | Profil | Analyse |
|---|---|---|---|
| andy_83f51171e438 | Gemini 4 Argon × OpenAI Astra | 150k, A2, master, historical_category_2 | [v0.1 – 3 logische Partien](andy_83f51171e438/v0.1/README.md) |
| andy_cc11a6598bcf | Gemini 4 Argon × OpenAI Astra | 350k, 4096, A2, master | [v0.1 – 2 logische Partien](andy_cc11a6598bcf/v0.1/README.md) |
Weitere Serien bei tatsächlicher Auswertung ergänzen. Dieser Index beansprucht keine vollständige Erfassung aller bisherigen Serien.

## Serienübergreifende Analyse-Snapshots
- [Globale JSONL-Bestandsanalyse 14.11.2026 – v0.1](GLOBAL/2026-11-14/v0.1/README.md): 24 technische IDs, 3261 Decision-Ereignisse; überlappt Einzelserien, nicht addieren.
