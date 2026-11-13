# ANDY Lab – Strategic Situational Awareness (SSA) v0.1

**Stand:** 13. November 2026 · **Status:** explorativer Methodenentwurf, keine validierten Befunde  
**Einbettung:** [Rückkampf-Hypothesenpool](ANDY_REMATCH_HYPOTHESENPOOL_UND_EXPERIMENTDESIGN_v0.1.md) · [Event-to-Evidence Method](ANDY_EVENT_TO_EVIDENCE_METHOD_v0.1.md)  
**Ziel:** In wiederholten ANDY-Partien messbar untersuchen, ob GPAI-Modelle **eigene Chancen und Gefahren sowie gegnerische Möglichkeiten** korrekt einschätzen, die Situation zutreffend antizipieren und im noch vorhandenen Handlungsspielraum angemessen handeln.

## 1. Konstrukt und vier Dimensionen

**Strategic Situational Awareness (SSA)** bezeichnet hier *beobachtbare, aus protokollierten Äußerungen und Aktionen ableitbare strategische Lageeinschätzung* – keine verifizierte Kenntnis interner Denkprozesse.

1. **Self-assessment:** Was behauptet das Modell über seine eigenen Stärken, Schwächen, Drohungen, Ressourcen und Spielziele? Welche dieser Aussagen sind durch den Boardzustand/Engine überprüfbar?
2. **Opponent assessment:** Wie beurteilt es gegnerische Ressourcen, Chancen, mögliche Siegwege und unmittelbare Gefahren?
3. **Anticipation:** Welche konkret falsifizierbare Entwicklung oder Gegneraktion prognostiziert es, mit welchem Zeitfenster und unter welchen Bedingungen?
4. **Action translation:** Welche tatsächlich ausführbare Handlung folgt auf die Einschätzung, während es noch regelkonforme Alternativen gibt?

**Trennlinien:** korrekt erkannte *Möglichkeit* ≠ eingetretenes *Ereignis*; tatsächliche Bedrohung ≠ nachweislich für Akteur sichtbare Bedrohung ≠ protokolliert erkannte Bedrohung ≠ mögliche Gegenmaßnahme. Erfolgreiche Abwehr kann bewirken, dass eine korrekt erkannte konditionale Gefahr **nicht** eintritt.

## 2. Sechs zusätzliche Hypothesen (SSA-H1 bis SSA-H6)

| ID | Hypothese | Prüfbare Operationalisierung / Gegenhypothese |
|---|---|---|
| **SSA-H1 – Self-Assessment Accuracy** | Modelle unterscheiden eigene strategische Vorteile und Gefahren mit unterschiedlicher Zuverlässigkeit. | Ex ante markierte Selbstaussagen mit objektiven Kontrollwerten, Schachrisiken und tatsächlich verfügbaren Gewinnwegen vergleichen; Gegenhypothese: Unterschiede entstehen durch unterschiedliche Positionen/Claim-Spezifität. |
| **SSA-H2 – Opponent Threat Recognition** | Erfolgreiche Modelle erkennen gegnerische Gewinnchancen früher, bevor diese entscheidend werden. | Früheste dokumentierte Bedrohungsäußerung versus engine-geprüfter Zeitpunkt verfügbarer Drohungen und letzter Abwehrmöglichkeit; Kontrolle für Sichtbarkeit, Matchlänge und Bedrohungsart. |
| **SSA-H3 – Overconfidence under Advantage** | Modelle unterschätzen gegnerische Risiken häufiger, wenn sie in einem Teilspiel deutlich führen. | Gefahrenerkennungsrate/-kalibrierung nach Go-/Schach-Vorsprungsniveau; alternative Erklärung: starke eigene Position verändert objektiv Bedrohungswahrscheinlichkeit. „Überkonfidenz“ nur messen, wenn Wahrscheinlichkeit/Grad ausdrücklich geäußert oder sauber operationalisiert ist. |
| **SSA-H4 – Awareness–Action Gap** | Eine korrekt erkannte Gefahr führt nicht zwangsläufig zu einer angemessenen Gegenmaßnahme. | Für engine-geprüfte Threat-Episoden Claim → letzte verfügbare legale Abwehr → tatsächlicher Zug → Ergebnis kodieren; nicht als Versagen werten, wenn Abwehr unmöglich oder schlechter war. |
| **SSA-H5 – Calibration under Resource Pressure** | Mit sinkendem Tokenbudget verändert sich die Genauigkeit der eigenen Lageeinschätzung. | 100k- und 50k-Arme mit gleichen Modellen/Regeln/Prompt-/Retry-/Outputsettings; Claim-Genauigkeit mit Nenner, Tiefe und nicht geloggten Reasoning-Tokens; TKO-Zensierung berücksichtigen. |
| **SSA-H6 – Within-Match Reassessment** | Modelle passen protokollierte Einschätzungen nach unerwarteten Gegneraktionen innerhalb derselben Partie an. | Konkrete Prognose vor Ereignis, Abweichung, nachfolgende Aussage und Aktion vergleichen; Revision getrennt von echter Verbesserung kodieren. Kein Nachweis persistenten Lernens. |

**Abgrenzung:** SSA-H4 überschneidet sich mit allgemeiner H5 (Anticipation–Action Gap), operationalisiert diese aber auf konkrete Bedrohungserkennung. SSA-H5 erweitert allgemeine H9 (Budgeteffekte) um Einschätzungsgenauigkeit. **Nicht als unabhängige Evidenzen doppelt zählen.**

## 3. Mindestdatensatz pro überprüfbarer Aussage (Claim Card)

| Feld | Anforderung |
|---|---|
| Quelle | match_id, event_id, player/model/color, raw_file_sha256, Zeit, Regel-/Engine-Version |
| Informationen | tatsächlich an Modell übergebener Zustand, verfügbare Historie, Budgetstand, Promptoptionen |
| Claim | **exakte** protokollierte Textspanne, self/opponent/threat/forecast, Referenzziel, Grad der Konkretheit, Kondition und Horizont |
| objektive Lage | Engine-geprüfter Boardzustand (Chess + Go), Go-Kontrolle, unmittelbare Drohungen, Siegbedingungen |
| Feasibility | mögliche ANDY-legale Alternativen und letzter prüfbarer Abwehrzeitpunkt; Suchvollständigkeit ausweisen |
| Reaktion | rohe Ausgabe, normalisierte/ausgeführte Aktion, Parserfehler, Retry; Planrevision/kein sichtbarer Wechsel |
| Nachfolge | eintretendes oder verhindertes Ereignis; eigene/gegnerische Kontrolle, Terminierung, Ressourcenverbrauch |
| Bewertung | verified / refuted / conditional / untestable / unresolved + Gegenhypothese + Beleg |

**Claims vor Sichtung späterer Outcomes kodieren**, soweit möglich (blinded/forward annotation). „Correctness“ nur mit überprüfbarem Referenzziel; subjektive Aussagen oder vage Überlegenheit gesondert als `not_scorable` klassifizieren.

## 4. Erste Vergleichsmetriken

- **Self-assessment agreement:** Anteil **auswertbarer konkreter** Selbstaussagen, die mit vorab definiertem Prüfmaß übereinstimmen; Nenner offenlegen.
- **Opponent threat recall:** korrekt benannte, dokumentiert sichtbare, engine-rekonstruiert relevante Gegnerbedrohungen / alle relevanten Bedrohungsgelegenheiten; nur bei verfügbarer vollständiger Threat-Enumeration.
- **Forecast accuracy:** verifizierte konkrete Prognosen / konkrete aufgelöste Prognosen; nicht testbare und konditional nicht aktivierte Fälle getrennt.
- **Threat-response coverage:** erkannte threats mit rechtzeitig ausgeführter regelkonformer Abwehr / erkannte threats mit verifizierter Abwehrmöglichkeit; Qualität der Abwehr gesondert.
- **Reassessment rate:** dokumentierte Revisionen / auswertbare Überraschungsepisoden, davon zusätzlich „verbessert / verschlechtert / nicht entscheidbar“.
- **Ressourcenstratifizierung:** Größen oben getrennt nach Modell, Gegner, Farbe, Ruleset, Tokenbudget, Output/Reasoning/Retry-Limits und Phase.

**Keine erfundene objektive Gewinnwahrscheinlichkeit:** Ein material- oder kontrollbasierter Vorsprung ist eine definierte Stellungsmetrik, nicht automatisch die Siegchance. Wahrscheinlichkeit nur aus kalibriertem Solver oder ausreichend vergleichbaren empirischen Fortsetzungen ableiten.

## 5. Anwendung auf erste ANDY-Rückkampfserie

**Referenz:** Flash vs. Argon `andy_1c77f49b3e17` (vermuteter Go-KO, terminales `match_end` im derzeit beschriebenen Log nicht verifiziert).  
**Kontrolle:** Gemäß Rückkampf-Pilot gleiche Modelle/Versionen/Prompts/Regeln/Budgets, Farbtausch, Wiederholung; Budgetvariation als separaten Versuchsarm.  
**Vorab konkret festlegen:** Bedrohungsdefinition (Chess/Go), Beobachtungsfenster, letzte Verteidigungsgelegenheit, Coding-Regeln zu vagen Äußerungen, Aggregationsschema und Umgang mit Wiederholungen.  
**Auswertung:** Zunächst **vollständige** Einzelpartie-Codierung; dann Farb-Paare; dann wiederkehrende SSA-Muster; bei zu wenigen Matches nur explorative Tendenzen.

### Fallfenster Astra × Opus `andy_64c8f95436d1`
Ein plausibler SSA-Prüffall ist die Sequenz um Events #141–#147 (Drohung, angekündigte Kombination, gegnerische Reaktion, Matt). Der externe Claude-Review behauptet, vor #141 hätten 17/20 reine Schach-Alternativen Matt in 2 vermieden. **Noch kein durch die vollständige ANDY-Engine bestätigtes Ergebnis**; keinesfalls automatisch in Bedrohungserkennungs- oder Abwehrerfolgsstatistik zählen.

## 6. Wissenschaftliche Qualitätskriterien

1. Ereignis-/Claim-IDs und Rohdaten-Hashes belegen; bei fehlenden Informationen `unknown` notieren.
2. Explizite Modelläußerungen sind keine Beweise innerer Kognition, und Gewinnen ist keine Evidenz korrekter Selbsteinschätzung.
3. Phasenzwang, Informationsasymmetrien, legale Alternativen und TKO-Budgeteffekte trennen.
4. Nicht nur spektakuläre Verlust-/Gewinnfälle auswählen: richtige, falsche und unentscheidbare Einschätzungen aus allen Matchphasen.
5. Doppelannotation / Review-Dissens und negative Gegenbeispiele dokumentieren.
6. Erst nach vorab fixiertem Codebuch größere Stichproben aggregieren; keine Generalisierung aus einem Einzelmatch.

## 7. Working-Paper-Kandidat

**Titel:** *Strategic Self-Assessment and Opponent Anticipation in General-Purpose AI Competition*  
**Leitfrage:** *Can GPAI models accurately identify their own risks and advantages, anticipate an opponent’s opportunities, and act while viable options remain?*  
**Status:** Frage und Forschungsdesign, **keine empirisch belegte These**.

**Implementation-Backlog:** SSA-Claim-Annotator (self/opponent/forecast), unabhängige Engine-Threat-Analyse, Reaktionsfenster/Alternativzugprüfung, pro Match exportierbare SSA-Tabelle und übergreifende Farb-/Budgetvergleichsmatrix.
