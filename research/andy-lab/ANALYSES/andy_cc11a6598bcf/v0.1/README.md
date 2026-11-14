# Serienanalyse v0.1 – Argon × Astra / 350k / 4096

Stand 14.11.2026. Deskriptiver Analysebestand, keine neuen Hypothesen oder Bewertungen. Frühere Einzelmatch-Auswertung (insbesondere Rückkampf) anhand der Originalprotokolle rekonstruiert und um gleichartig erfasste Kennzahlen der ersten Partie ergänzt; keine wortgetreue Kopie des früheren Chats.

Serie `andy_cc11a6598bcf`, zwei logische Partien laut PROJECT/ANDY_APP_LAB_SERIES_HANDOFF_2026-11-14.md. Quelle: Archiv(2).zip, SHA-256 ad5ad8fb04b3642dd4b26e284232e99cb3357e3af0d43637b7d97daeebaa73d3. Vier Originaldateien erneut gelesen; berechnete Einzeldateihashes in sources.csv. Kein ursprüngliches Manifest in diesem ZIP; Hashes dienen der Identifikation, nicht der unabhängigen Authentifizierung. Beide JSONL enthalten match_start und match_end; 210 bzw. 249 Decision-Events. Serienzugehörigkeit aus Handoff, nicht aus historischen Start-Events. Kein Resume in diesen beiden Logs sichtbar.

Konfiguration beider Partien: je 350000 Tokens, output_cap 4096, max_decisions 500, max_illegal_retries 5, A2, master, x_go_moves 1, reasoning_effort default, ruleset v1.1; Engine-Build unbekannt. Farbwechsel. Beide am 10.11.2026. A = Gemini 4 Argon, S = OpenAI Astra (historische Logbezeichnungen).

## Ressourcen und Ergebnis
| Runde | Match-ID | A Farbe | A Input | A Output | S Input | S Output | A Calls/ausgeführt | S Calls/ausgeführt | Ergebnis laut Runner |
|---|---|---|---:|---:|---:|---:|---|---|---|
| 0 | andy_cc11a6598bcf | W | 101775 | 4002 | 87329 | 89015 | 107/104 | 103/103 | Astra Matt, Schwarz |
| 1 | andy_0c0f7413fdf6 | B | 134220 | 4834 | 102342 | 137594 | 132/116 | 117/117 | Astra Matt, Weiß |

Gesamtverbrauch A/S: 105777/176344 und 139054/239936. Restbudget A/S: 244223/173656 und 210946/110064. Dauer laut match_end 5411.40 bzw. 8392.84 Sekunden. 207/210 und 233/249 ausgeführte Aktionen/Entscheidungen. Keine Budgetüberschreitung. Summen aus Decision-Events stimmen mit match_end und JSON-Konten überein. Ergebnis laut Runner, keine unabhängige Engine-Validierung.

## Endposition
| Runde | A Schach-Schläge | S Schach-Schläge | A Material | S Material | A Go-Kontrolle | S Go-Kontrolle | A Go-Schläge | S Go-Schläge |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| 0 | 11 | 15 | 0 | 8 | 45 | 52 | 5 | 16 |
| 1 | 11 | 15 | 0 | 18 | 50 | 65 | 3 | 15 |

Schach-Schläge = ausgeführte CHESS-Events mit x in gemeldeter SAN; Go-Schläge = Summe gemeldeter geschlagener Steine in ausgeführten Events. Material P1 N3 B3 R5 Q9 aus finaler FEN, König ohne Wert. Keine gewichtete Gesamtbewertung. Beide Endpositionen: Argon nur König. Astra R0 König, Turm, drei Bauern; R1 König, Dame, Turm, Läufer, Bauer.

- R0 FEN: `8/p1p5/2p5/r7/8/K1k5/8/8 w - - 16 49`; Decision 210, b5a5 / Ra5#.
- R1 FEN: `3Q4/3R1k2/8/2K2B2/2P5/8/8/8 b - - 2 55`; Decision 249, d2d7 / Rd7#.

## Phasen und Verlauf
data.csv: Ressourcen nach Phase sowie Endposition; Summen einschließlich fehlgeschlagener Calls. Astra Reasoning gemeldet 84136 bzw. 131745, 101/103 bzw. 115/117 Calls mit Angabe. Argon Reasoning nicht ausgewiesen (nicht als null interner Verbrauch interpretieren). go_samples.csv: protokollierte Go-Kontrollwerte an Decision-Indizes 40er-Schritte und Ende; keine vollständige Positionsbewertung. Finalwerte stammen aus match_end. 

## Beobachtungsstand
Astra in beiden Partien laut Runner Matt-Sieger, mit jeweils höheren gemeldeten Go-Kontrollwerten und klassischem Schachmaterial am Ende. Argon mit geringerem gemeldetem Input+Output in beiden Partien; Astra höherer absoluter Output in GO als CHESS. Dies sind Beschreibungen dieser zwei Partien, keine modellübergreifende Wertung. Früher besprochene Einzelzug-Deutungen werden hier nicht als bestätigte Befunde übernommen; frühere Chatfassung nicht vollständig verfügbar. Die 150k-Serie bleibt separat; Budget, Outputcap, max_decisions und teilweise Retry-Limits unterscheiden sich. Kein kausaler Budgetvergleich, keine Hypothesenbildung, keine App-Änderung. Rohdaten verbleiben im Originalarchiv.
