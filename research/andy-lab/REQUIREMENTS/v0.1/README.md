# Neues ANDY Lab – Best-of Requirements & iterativer Entwicklungsprozess v0.1

14.11.2026 · Arbeitsstand zur Diskussion, keine Implementierungsfreigabe.
## Ziel und Abgrenzung
Die manuell erstellten Analysen sind fachliche Prototypen und Referenzfälle für das **neue** Lab. Wir sammeln nicht primär für neue Hypothesen, sondern um aus den ergiebigsten Analyseformen wiederverwendbare Anforderungen, Visualisierungen und Interaktionen abzuleiten. Pareto-Prinzip: zuerst die Funktionen mit dem größten praktischen Erkenntnisgewinn. Bestehendes Lab bleibt nutzbar, ist aber keine zwingende UI-Blaupause. Pattern View und Analytical View gleichberechtigt, gemeinsame Datenbasis, Filter und Drill-down. Keine Modellwertung, kein neuer Score, keine automatische Hypothesengenerierung in dieser Phase.

## A/B/C – wiederholbarer Entwicklungszyklus
| Schritt | Aktivität | Ergebnis / Übergabe |
|---|---|---|
| A – Datenbasis erweitern (Games) | Serien spielen, Original-JSON/JSONL und Exporte sichern; Konfigurationen, Farbwechsel, Serien-/Match-/Segment-IDs, Herkunft und Lücken erfassen. Interessante Partien und Muster manuell analysieren. | Versionierte Analyse-Snapshots unter ANALYSES mit Datenbezug und reproduzierbaren Kennzahlen. |
| B – Lab-Prototyping | Best-of aus vorhandenen und neuen Analysen auswählen, konkrete Nutzerfrage, Felder, Filter, Darstellungen, Drill-down, Methoden und Grenzen beschreiben. Interaktive Clickdummies / Offline-Prototypen auf realen Daten entwickeln; synthetische Daten ausdrücklich markieren. | Versionierter Req-Pool, Prototyp-ID, Referenzfall, Testkriterien. Kein produktiver Umbau ohne Freigabe. |
| C – Iterativer Test und Weiterentwicklung | Mensch und KI testen die Prototypen an bekannten Referenzfällen und neuen, abweichenden Serien. Zahlenabgleich, Nutzbarkeit, visuelle Mustererkennung, Filter/Zuordnung und Fehlfälle prüfen; Nutzerfeedback und Abweichungen festhalten. | Entscheidung: behalten, ändern, ergänzen, zurückstellen oder verwerfen; nächste Version der Reqs/Prototypen. Rückkopplung nach A und B. |

A, B und C können parallel laufen. Nicht auf einen vollständigen Datenbestand warten; neue Spiele dienen zugleich als Regressionstest. Keine feste Anzahl von Partien als Eintrittsschwelle; Projektleitung priorisiert nach praktischer Nutzung. Hypothesen und Bewertungen erst in gesondertem späterem Schritt, nicht als Voraussetzung für das neue Lab.

## Quellen / Referenzfälle
- [S150: Argon–Astra 150k/2048 v0.1](../../ANALYSES/andy_83f51171e438/v0.1/README.md), drei logische Partien, vier Segmente, Legacy-Overlap, Endposition und Ressourcen.
- [S350: Argon–Astra 350k/4096 v0.1](../../ANALYSES/andy_cc11a6598bcf/v0.1/README.md), zwei logische Partien, Farbwechsel, Runner-Ergebnisse, Endposition und Ressourcen.
- [G01: Globale JSONL-Auswertung v0.1](../../ANALYSES/GLOBAL/2026-11-14/v0.1/README.md), 24 technische IDs und dokumentierte Event-Aggregate, Quellenüberlappung.
- [Analyseindex](../../ANALYSES/README.md). Diese archivierten Zahlen sind Regressionserwartungen unter den dokumentierten Methoden und Vorbehalten, nicht unabhängig engine-validierte Ground Truth. Vor produktiver Abnahme Originale und Berechnungen erneut prüfen. Kein Addieren von G01 und S150/S350. Räumliche Eröffnungsmuster und alternative Züge sind bisherige Konzept-/Gesprächsprototypen, nicht als reproduzierte Befunde in G01 belegt.

## Best-of: erster Requirements-Pool
Prioritäten sind Vorschläge: P1 = erste Prototypen, P2 = nächste Ausbaustufe, abhängig von Daten-/Engine-Verfügbarkeit. Alle Einträge Status ENTWURF.
| ID | Funktion / Nutzerfrage | Prototyp / Interaktion | Referenz | Priorität |
|---|---|---|---|---|
| LAB-R01 | Welche Partien/Serien sind im Bestand und vergleichbar? | Serienbrowser mit Modell, Farbe, Profil, Budget, cap, Regeln, Endgrund, Abdeckung und Match-/Segment-Drill-down | S150/S350/G01 | P1 |
| LAB-R02 | Wie verteilen sich Aufrufe, ausgeführte Aktionen und Fehler? | Modell-/Serientabelle und Balken; Filter Setup/Chess/Go, Nenner, Retry-Kategorien, Event-Drill | G01/S150/S350 | P1 |
| LAB-R03 | Wo werden Ressourcen verbraucht? | Input, Output, gemeldetes Reasoning, Zeit/Calls, kumulativ und pro Phase/Call; Restbudget, Abdeckung und Providersemantik | S150/S350/G01 | P1 |
| LAB-R04 | Was ändert sich zwischen Partien und Farbwechseln? | Small multiples, modellorientiert oder nach Originalfarbe, gemeinsame Skalen und Phasenfenster, Serie/Runde umschaltbar | S150/S350 | P1 |
| LAB-R05 | Wie unterscheiden sich Serienprofile? | Profilvergleich nebeneinander, vollständiger Config-Diff, gemeinsame Kennzahlen und Warnungen; keine isolierte Budgetwirkung behaupten | S150 vs S350 | P1 |
| LAB-R06 | Wie steht das Brett bei Ende/Abbruch unabhängig vom Ergebnis? | Terminal Position Profile: Brett, klassisches Restmaterial, Schach-Schläge, Go-Kontrolle und Go-Schläge, Restbudget, Endgrund. Geschlagene Figurentypen erst nach verifizierten Capture-Events. Keine gewichtete Gesamtbewertung | S150/S350 | P1 |
| LAB-R07 | Wie entwickeln sich Brett und Ressourcen über die Partie? | Synchronisierte Go-/Material-/Usage-Kurven, Replay/Board an gewähltem Event, Anzeige von Zeitpunkt, Phase und fehlenden Zuständen; Decision vs ausgeführte Aktion klar trennen | S150/S350 go_samples.csv als erste Referenz | P1 |
| LAB-R08 | Welche räumlichen Eröffnungsmuster wiederholen sich? | Brett-Small-multiples, Go-Setup/Chess-Fenster, Platzierungs-/Differenzkarten, Modellperspektive und Originalfarbe; keine illegalen Spiegelungen | bisherige Konzeptentwürfe; neue validierte Daten nötig | P2 |
| LAB-R09 | Was war in einer konkreten Situation möglich? | Vorher/Nachher-Brett, tatsächlich gewählte Aktion, legale Alternativen und Folgezustände; Replay plus Event/Begründung, alternative Verläufe ausdrücklich kontrafaktisch | bisherige Einzelfall-Diskussionen, Legal Action Explorer noch zu prüfen | P2 |
| LAB-R10 | Woher stammen die Zahlen, was fehlt? | Import-/Audit-Ansicht, Hashes, Quellenstatus, Resume/Deduplikation, Methoden-Version, Abdeckung, Export der gefilterten Ansicht | G01/S150/S350 | P1, querschnittlich |

## Erster Prototyping-Vorschlag (kein freigegebener Bauauftrag)
Ein Series Explorer mit Auswahl einer oder zweier Serien, oben gemeinsame Filter und Konfigurationsvergleich, darunter gleichwertige Pattern View / Analytical View. Start mit R01/R05/R06/R07 und verknüpften R02/R03; R10 als Voraussetzung für jede Kennzahl. Eine Auswahl in Tabelle/Kurve/Brett hält dieselbe Match-/Event-Referenz. Globaler Einstieg R02/R03 auf G01 mit expliziter technischer statt logischer Zählung. R08/R09 nach gesicherter Zustandsbasis. Sicherstellen, dass neue Serien ohne manuelle Anpassung der Oberfläche aufgenommen werden können.

## Erste Abnahmetests – Entwurf
| Test | Erwartung |
|---|---|
| T01 Serienidentität | S150 zeigt 3 logische Partien/4 technische Segmente, S350 2; Resume nicht addieren und unsicheren historischen Wert markieren. |
| T02 Ressourcen | S150 R2 Argon 78982 Input + 3091 Output, Astra 69095 + 81829 gemäß archiviertem Snapshot; Reasoning fehlt bei Argon, nicht als 0 darstellen. |
| T03 Terminal | S150 R2 Material 13:10, Go 46:43, berichteter TKO getrennt; S350 R1 Material 0:18, Go 50:65 aus Modellperspektive. Farbwechsel ohne Vertauschung von Modellzuordnung. |
| T04 Config-Diff | 150k/2048/300 vs 350k/4096/500 sowie Retry-Abweichungen zeigen; keine pauschale Gleichvergleichbarkeit. |
| T05 Global | G01 technische IDs, Calls und executed entsprechend archiviertem Snapshot, Abdeckung/fehlende Paare anzeigen; keine Doppelzählung durch späteren Serienimport. |
| T06 Interaktion | Auswahl eines protokollierten Go-Sample-Events verknüpft Kurve, Tabelle und Replay-Referenz; bei fehlendem Brettzustand ausdrücklich nicht verfügbar. |
| T07 Erweiterbarkeit | Neue Serie importieren und dieselben Funktionen verwenden; Export/Filter/Version nachvollziehbar, alte Snapshots unverändert. |

## Iterationsprotokoll
Je Zyklus eine Zeile mit Datum, Analyse-Versionen, Nutzerfrage, Req-ID, Prototyp-Version/Link, Testdaten, Ergebnis (pass/fail/offen), Nutzerfeedback, Entscheidung und nächstem Schritt. Neue Versionen in v0.2 etc.; stabile IDs beibehalten, Änderungen nachvollziehbar machen. Kein stilles Überschreiben. Keine Tests oder Prototypen als erledigt markieren, solange sie nicht tatsächlich ausgeführt wurden.

| Zyklus | A – Basis | B – Prototyping | C – Test | Nächster Schritt |
|---|---|---|---|---|
| 01 – 14.11.2026 | S150, S350, G01 archiviert | Best-of Req-Pool v0.1 | offen, keine Clickdummy-Abnahme | weitere Games parallel; ersten Series-Explorer-Clickdummy entwerfen und mit Projektleitung testen |

Bezug zur bisherigen [Lab-Architektur](../../ANDY_LAB_2_0_RESEARCH_ARCHITECTURE_v1.0.md): dieser Arbeitsstand präzisiert die aktuelle Entwicklungsmethode für das neue Lab, ersetzt keine freigegebenen Schnittstellen oder Schutzanforderungen. Punch Lab und Hypothesenpool weiterhin separat, kein aktueller Implementierungsauftrag.
