# Globale JSONL-Bestandsanalyse – v0.1
Stand 14.11.2026. Rekonstruktion des früheren globalen Analysebestands anhand der erneut gelesenen Originalarchive; keine wortgetreue Chatabschrift. Deskriptiv, keine neuen Hypothesen oder Bewertungen.

## Quellen und Abdeckung
- Archiv(2).zip SHA256 ad5ad8fb04b3642dd4b26e284232e99cb3357e3af0d43637b7d97daeebaa73d3
- ANDY_SERIES_20261114T154542187465Z(1).zip SHA256 0894b5c2b1de73ef9b5d4fdb2881b37f9a826bb6e1eb397eebce70725d164405
- ANDY_SERIES_20261114T154556646525Z(1).zip SHA256 08fd5ed13cb687f37abcbd50e0eb4904a2a1363b750f15b6e308347187fcd86a ist hinsichtlich Matchdateien vollständig redundant zum größeren Serienexport; nicht zusätzlich gezählt.
- Späterer 19:05-Export nicht Bestandteil dieses historischen Snapshots.
- Nur andy_*.json/jsonl-Matchdateien, im Serienexport unter matches/; Mac-Metadaten und derived-Dateien ausgeschlossen. Deduplikation nach Dateiname und Bytegleichheit: 11 redundante Dateien aus den ersten zwei Archiven, keine Inhaltskonflikte. 46 eindeutige Matchdateien, 24 technische IDs, 22 vollständige Paare, 23 JSONL und 23 JSON. Fehlend: andy_83f51171e438.json und andy_88563f63f440.jsonl.
- 3261 Decision-Ereignisse, 3080 executed=true, 181 übrige; 17 match_start, 17 match_end, 2 resume. Technische IDs sind keine unabhängigen logischen Partien. Keine Rekonstruktion logischer Resume-Ketten hier. 
- Neun beobachtete Engine-Labels einschließlich Zufall, acht KI-Labels; neun beobachtete (engine,model)-Paare. Keine Gleichsetzung mit allen konfigurierten Engines.
- Ein Astra-Decision-Ereignis mit fehlendem Input/Output (index 75); gemeldete Summen ohne fehlende Werte.

## Ergebnisse
model_counts.csv enthält Calls, Ausführungen, gemeldete Input-/Output-Summen, Anzahl Calls mit beiden Usage-Werten sowie Summe gemeldeter Latenzen in ms. phase_counts.csv enthält dieselben Zählungen je Engine und Phase ohne Latenz/Usage-Abdeckungsfeld. Historische Konfigurationen unterscheiden sich; absolute Summen und Ausführungsanteile sind keine Stärkerangliste. Latenzen keine gemessene Gesamtdauer; keine Provider-Normalisierung. Zufall: beide Spiele andy_7d906e7322b4 und andy_a2fb40f17427 je 100 Decisions, A0/free, x_go_moves 1 bzw. 2, Budget 50000, cap 2048, max_decisions 100, Retry 2. Null gemeldete Tokens; keine kostenpflichtige Modellreferenz. Nicht mit zufälliger Modellauswahl verwechseln.

Reproduzierbare Beobachtungen: stark unterschiedliche gemeldete Output-Summen je Engine; Phase GO und CHESS getrennt erfasst; Ausführungen und Versuche unabhängig gezählt. Keine Aussage über kausale Analysetiefe, Spielstärke, interne Reasoning-Kosten oder optimale Budgetwahl. Keine unabhängige Engine-Validierung. Frühere Detailauswertungen zu räumlichen Eröffnungsmustern, konkreten Alternativzügen und semantischen Begründungen sind in diesem Snapshot nicht erneut reproduziert und bleiben offen; keine ungeprüfte Übernahme. Frühere vorläufige Zahlen bei Abweichung nicht als validiert behandeln. 
## Fortführung
Eigener globaler Snapshot neben Einzelserien. Nicht mit Serienanalysen addieren (überlappende Quellen). Neue Exporte und normalisierte logische Matches in späterer Version; Rohdaten nicht veröffentlichen. Keine Änderung der Forschungsagenda oder App. Erst sammeln, später Muster verdichten und bewerten.
