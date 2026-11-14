# Serienanalyse v0.1 – Argon × Astra / 150k

Stand: 14.11.2026. Status: deskriptiver Analysebestand; keine neue Hypothese, Bewertung oder Rangliste.
Serie: `andy_83f51171e438`, historical_category_2. Drei logische Partien, vier technische Segmente.
Quelle: ANDY_SERIES_20261114T190541599122Z.zip; SHA-256 d5d5909848993c6739f7dad508b18d46b62134bdb781d7be727072428c06f6a1. 12/12 Manifest-Dateihashes beim erneuten Lesen geprüft. Rohdaten verbleiben im ursprünglichen Export, nicht in diesem öffentlichen Analyseordner. Resolver 07B3-rev2. Quelle: derived/matches.jsonl, matches/<segment>/<segment>.jsonl; finale FEN/Go-Werte aus letzter Decision (R0/R1, nicht ausgeführt) bzw. match_end (R2).
Modelle: A = Gemini 4 Argon, S = OpenAI Astra. Je 150000 Tokens, master, A2, x_go_moves=1, max_decisions=300, output_cap=2048, reasoning_effort default. Retry 4/5/4. R0/R1 historische Regel-/Engine-Version unbekannt, R2 v1.1. Keine isolierte Kausalinterpretation.

## Partien und Ressourcen
| Runde | Match-ID | A-Farbe | A Input | A Output | S Input | S Output | A Calls / ausgeführt | S Calls / ausgeführt |
|---|---|---|---:|---:|---:|---:|---|---|
| 0 | andy_83f51171e438 | W | 73235 | 3240 | 73690 | 76874 | 79/78 | 88/77 |
| 1 | andy_93f0d66382aa | B | 79308 | 3142 | 74225 | 76359 | 84/80 | 87/80 |
| 2 | andy_7278d457e3f6 | W | 78982 | 3091 | 69095 | 81829 | 84/80 | 82/79 |

R0: überlappendes Segment andy_032f31d68743 nicht addieren; Ressourcen und Counts nur berichtet, unsicher. Summen A/S: 76475/150564; 82450/150584; 82073/150924. A Restbudget 73525*/67550/67927, S 0 jeweils. Alle drei budget_overshoot, S zuletzt am Zug; nur R2 Resolver-TKO für A belegt (924 Überschreitung), R0/R1 kein Resolver-Verdikt/Runner-Sieger. R2 letztes Event match_end, 166 Calls, 159 ausgeführt, 7 fehlgeschlagen; 3657.55 s Dauer. R0/R1 fehlende Start-/Endrahmen. Keine unabhängige Engine-Prüfung.

## Abbruchposition
| Runde | A Schach-Schläge | S Schach-Schläge | A Material | S Material | A Go-Kontrolle | S Go-Kontrolle | A Go-Schläge | S Go-Schläge |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| 0 | 11 | 10 | 9 | 8 | 66 | 62 | 2 | 8 |
| 1 | 8 | 5 | 26 | 23 | 47 | 66 | 2 | 3 |
| 2 | 11 | 8 | 13 | 10 | 46 | 43 | 4 | 1 |
| Summe (deskriptiv) | 30 | 23 | 48 | 41 | 159 | 171 | 8 | 12 |

Schach-Schläge = ausgeführte CHESS-Events mit x in gemeldeter SAN; Go-Schläge = Summe gemeldeter Stein(e) in ausgeführten Events. Material = FEN-Bestand mit P1 N3 B3 R5 Q9, König nicht bewertet. Keine Positionsbewertung, kein ANDY-Score; Schläge sind nicht zwingend mit Materialverlust identisch (z.B. Umwandlungen). R0 Werte aus Root-JSONL einschließlich Resume-Eintrag, keine Addition des zweiten Logs.

| Runde | A Bestand P/N/B/R/Q | S Bestand P/N/B/R/Q | FEN (Originalfarbe) |
|---|---|---|---|
| 0 | 3/1/1/0/0 | 3/0/0/1/0 | 2r3k1/5ppp/8/3K4/3P4/4N1B1/5P1P/8 w - - 6 36 |
| 1 | 6/1/1/1/1 | 3/1/1/1/1 | 1r4k1/8/1n1p2pp/1pbP1p2/8/3Q2NP/2B2pPK/4qR2 w - - 2 37 |
| 2 | 5/1/0/1/0 | 2/0/1/1/0 | 8/R3b2p/2p5/4k3/5N2/PP2rP1P/6PK/8 w - - 0 37 |

## Output pro Phase und Go-Zeitpunkte
Siehe data.csv, go_samples.csv. Phasenwerte über alle Decision-Events einschließlich fehlgeschlagener Aufrufe. Astra Reasoning gemeldet 73324 / 72571 / 78107; vorhanden bei 85/88, 84/87, 80/82 Aufrufen. Argon Reasoning in allen Aufrufen null (nicht ausgewiesen, nicht null Verbrauch). Providersemantik nicht harmonisiert. Go-Samples sind protokollierte Entscheidungspunkte, keine vollständige Positionsbewertung.

## Beobachtungen / bisheriger Gesprächsstand
A hat in allen drei Abbruchpositionen numerisch mehr klassisches Schachmaterial und mehr protokollierte Schach-Schläge. Go-Kontrolle A in R0/R2 höher, S in R1 höher. A gemeldeter Output liegt jeweils zwischen 3091 und 3240; S zwischen 76359 und 81829. S gemeldeter Output für GO ist in jedem Match höher als für CHESS (absolute Summen, nicht pro Aktion normalisiert). R2 Screenshot 14.11.2026 20:03:16 lokal entspricht den Endwerten. Der Gesprächsimpuls, A hätte möglicherweise auch ohne TKO gewonnen, bleibt unbewertete Frage, kein Befund. Frühere Sweet-Spot-/Rangumkehr-Deutungen sind Gesprächsideen, werden hier nicht als Hypothesen übernommen. Terminal Position Profile bleibt deskriptive Darstellung, keine Gewichtung oder Siegprognose.

## Grenzen und Fortführung
Historischer Overlap, fehlende Metadaten, unterschiedliche Retry-Limits, kein unabhängiger Replay/Engine-Check, keine harmonisierte Reasoning-Messung. Keine Aussage über geschlagene Figurentypen ohne gesonderte Capture-Validierung. Neue Exporte oder Auswertungen als neue Version hinzufügen; v0.1 erhalten. Keine Änderung der Forschungsagenda oder App.
