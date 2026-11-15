# ANDY RULESET v1.2 — GO-SATURATION-01

Datum: 2026-11-15. Regelentscheidung durch Projektleitung freigegeben; DeepSeek Review zustimmend, Qwen ohne Rückmeldung. Implementierung offen (GPT / Thread 1).

## Verbindliche Regelentscheidung
ANDY ist ein gekoppelter Wettbewerb mit alternativen Siegwegen. Definitiver Go-Abschluss beendet die gesamte Partie; kein Chess-only-Folgespiel, unabhängig von Schachstellung oder Spielqualität.

- Formale Sättigung: alle zulässigen Go-Punkte belegt.
- Funktionale Sättigung: für beide Akteure keine legale Go-Steinplatzierung gemäß tatsächlichen ANDY-Regeln möglich.
- Zustand erst nach sämtlichen Aktionseffekten einschließlich Captures prüfen; Hubs und Tabuzonen berücksichtigen.
- Höhere Go-Kontrolle gewinnt durch TKO – Go Saturation; Gleichstand DRAW, kein Schach-Tiebreaker.
- Bestehender freiwilliger PASS ist nicht terminal. Bei einseitiger Blockade Forced PASS ohne zusätzlichen KI-Aufruf, eindeutig protokolliert; regulärer ANDY-Ablauf bleibt bestehen. Bei beidseitiger Blockade sofortige Wertung.
- Priorität: Schachmatt (KO), Go-Schwelle 72 (KO), Go-Sättigung (TKO), Ressourcenerschöpfung (TKO). Weitere bestehende Endbedingungen beim Audit konsistent einordnen.
- Nach Terminalzustand keine Aktion, kein Request, kein Retry.
- Vorgeschlagene Identifikatoren: outcome_class=TKO, termination_detail=go_saturation, winning_layer=GO; bei Gleichstand DRAW ohne Sieger.

## Referenzfall
andy_89e45631d2f6, Qwen 3.8 Max × Qwen 3.8 Max, Ruleset v1.1, 500000 Tokens je Akteur, A2, low, cap 4096, max_illegal_retries 5.
Originalbericht: ABORT/user_stopped, 268 Entscheidungen, 247 ausgeführte Aktionen, Go 67:63, Verbrauch Weiß 468109 / Schwarz 462616. Historisches Ergebnis unverändert.
Nach bisheriger Protokollauswertung: PASS 264, letzter Go-Punkt e1 bei 266, anschließend Qe1+ bei 267 und illegale Go-Platzierung k5 bei 268. Hypothetische neue Wertung: TKO Weiß bei 266 (67:63), vorbehaltlich deterministischer Original-Engine-Rekonstruktion. Vollständige Belegung der 125 Go-Punkte und genaue Eingangsposition beim Audit bestätigen.
Schachqualität ist keine Voraussetzung der Regelentscheidung. Qe1+ mit möglichem Kxe1 nach gewöhnlichen Schachregeln ist ein separater Analysefall, keine Begründung für Sättigungswertung.

## Implementierung
Audit Engine und vorhandenen PASS; Legalitätsprüfung, terminale Prüfung nach relevanten Zustandsänderungen und vor weiteren Requests; Forced PASS; Prompts, JSON/JSONL, Arena, Replay, Serienprofile/Rematches, Lab-Klassifikation und versioniertes Ruleset. Historische Partien unverändert und rückwärtskompatibel.

## Regressionstests
| ID | Fall | Erwartung |
|---|---|---|
| GS01 | Formale Sättigung Weiß führt | TKO Weiß |
| GS02 | Formale Sättigung Schwarz führt | TKO Schwarz |
| GS03 | Gleichstand | DRAW |
| GS04 | Letzter freier Punkt | Sofortige Endprüfung |
| GS05 | Sättigung zugleich 72 Punkte | KO Go |
| GS06 | Letzter Punkt mit Capture | Keine voreilige Endentscheidung; vollständigen Zustand prüfen |
| GS07 | Nur Weiß ohne legale Platzierung | Forced PASS |
| GS08 | Nur Schwarz ohne legale Platzierung | Forced PASS |
| GS09 | Freie Punkte, beidseitig keine legale Platzierung | Funktionale Sättigung |
| GS10 | Freiwilliger PASS | Keine automatische Beendigung |
| GS11 | Forced PASS | Kein zusätzlicher KI-Aufruf |
| GS12 | Terminalzustand | Keine weiteren Aktionen/Requests |
| GS13 | Historisches Replay v1.1 | Unverändert |
| GS14 | Referenzzustand Entscheidung 266 | TKO Weiß sofern Engine-Rekonstruktion bestätigt |

## Separater P0: STOP-02
Nutzer meldet mehr als eine Minute Verzögerung nach Stop-Klick; exakter Klickzeitpunkt nicht protokolliert. Ursache durch Code-Audit prüfen, nicht als erwiesen synchronen Runner behaupten.
Stoppsignal unabhängig vom laufenden Request verarbeiten, keine neuen Requests/Retries nach angenommenem Stoppsignal, laufenden Request soweit möglich abbrechen, verspätete Antworten sicher behandeln. STOPPING/STOPPED unterscheiden, Stoppsignal und tatsächliches Ende separat protokollieren. Regression vor Factory-Freigabe.

## Release
Audit, Offline-Tests, Abnahme 8080, regulärer SYNC-Prozess, GitHub-Dokumentation, Freigabe Sandbox/Factory. Regelentscheidung freigegeben, technische Umsetzung noch nicht durchgeführt. Technische Identifikatoren und konkrete Forced-PASS-Implementierung sind Umsetzungsvorschläge; bestehende Schemas beim Audit berücksichtigen.
