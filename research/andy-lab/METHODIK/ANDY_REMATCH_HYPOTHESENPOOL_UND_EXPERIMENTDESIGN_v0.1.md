# ANDY Lab – Rückkampf-Hypothesenpool und experimentelles Studiendesign v0.1

**Datum:** 13.11.2026  
**Status:** Forschungsentwurf / explorativ; **keine validierten Befunde**  
**Gegenstand:** Wiederholte GPAI-vs.-GPAI-Partien auf dem gekoppelten Schach-Go-Brett, einschließlich Farbtausch, Variation von Ressourcenbudgets und späterem matchübergreifendem Vergleich.  
**Basis:** Im ANDY-Lab-Dialog am 13.11.2026 formulierte 15 Hypothesen und ein 12-Match-Pilotdesign.  
**Methodenbezug:** [ANDY Event-to-Evidence Method v0.1](ANDY_EVENT_TO_EVIDENCE_METHOD_v0.1.md) · [Individual Research Edition](../INDIVIDUAL_RESEARCH_EDITION_001_ANTIZIPATION_ADAPTIVITAET_LEARNINGS_BLUEPRINT_v0.1.md) · [Comparative Research Edition](../COMPARATIVE_RESEARCH_EDITION_001_24_SEITEN_BLUEPRINT_v0.1.md)

> **Leitthese (zu prüfen):** GPAI models competing under novel, coupled rules and constrained resources exhibit identifiable patterns of strategic anticipation, adaptation and resource allocation that cannot be adequately explained by winning outcomes alone.

> **Deutsch:** Allgemeine KI-Modelle zeigen in einem Wettbewerb unter neuartigen, gekoppelten Regeln und begrenzten Ressourcen möglicherweise charakteristische Muster strategischer Antizipation, Anpassung und Ressourcenverteilung, die sich nicht allein aus Sieg und Niederlage erklären lassen.

## 1. Forschungslogik und Interpretationsgrenzen

Ein Matchresultat beschreibt nicht zuverlässig die zugrunde liegende Strategie. Deshalb werden **explizit dokumentierte Aussagen**, **tatsächliche Entscheidungen**, **regelbasierter Handlungsspielraum**, **Gegnerreaktionen**, **Ressourceneinsatz** und **Ergebnis** getrennt untersucht. Pro Match zuerst vollständige Event-to-Evidence-Kodierung; dann Vergleich von Partien mit gleichem Schema.

- Ein wiederholter Go-KO beweist allein **keine** bewusst gewählte Go-Strategie. Wiederkehrende **Go-Orientierung** wird anhand zeitlicher Verläufe, freier Wahlmöglichkeiten und dokumentierter Absichten geprüft.
- Strategische Änderung ≠ Adaptivität: Phasenwechsel, Zwangszüge, feste Regelreihenfolgen oder Gelegenheiten können das Muster erklären.
- Keine Aussagen über internes Denken, Bewusstsein oder persistentes Lernen aus Modelltexten ableiten.
- Vorzeichen und Größe eines Ergebnisses können von Farbe, Gegner, Ruleset, Provider, API-/Reasoning-Einstellungen, Output-/Retry-Grenzen, Startzustand und Modellupdates abhängen.
- **Explorative Pilotstudie ≠ Präregistrierung ≠ bestätigtes Working Paper.** Für konfirmatorische Aussagen spätere Studien und Analyseplan vor dem Start einfrieren.
- Fehlende oder unvollständige Token-/Reasoning-Metadaten offen ausweisen; keine scheingenaue Provider-übergreifende Effizienzrangfolge.

## 2. Hypothesenpool: strategische Schwerpunktsetzung

### H1 – Strategische Siegweg-Präferenz (priorisiert)
**Hypothese:** Bestimmte GPAI-Modelle zeigen über mehrere Partien hinweg eine stabile Präferenz für einen der beiden Siegwege, unabhängig von der Spielfarbe.  
**Messung:** Anteil *frei wählbarer* Chess-/Go-Entscheidungen, konkrete Zieläußerungen, Verlauf der Go-Kontrolle, Chess-Bedrohungen; KO-Typ **separat** als Ergebnisvariable.  
**Alternativerklärung:** Farbe oder positionelle Gelegenheiten bestimmen die Aktionen; Siegweg ist bloß nachträgliches Ergebnis.

### H2 – Adaptive Siegweg-Umschaltung (priorisiert)
**Hypothese:** Modelle wechseln ihren Schwerpunkt von Schach zu Go oder umgekehrt, wenn sich die relativen Erfolgsaussichten verändern.  
**Messung:** Zeitpunkt dokumentierter oder verhaltensseitiger Schwerpunktwechsel, vorangehende Zustandsänderungen, danach ausgeführte Aktionen und verfügbare regelkonforme Alternativen.  
**Alternativerklärung:** Vorgeschriebene Zugphasen, Zwangsfolge oder Zufall statt adaptiver Neuausrichtung.

### H3 – Farbabhängigkeit der Go-Strategie
**Hypothese:** Der Go-Fokus eines Modells verändert sich systematisch durch die Zuweisung von Weiß oder Schwarz.  
**Messung:** Gleiche Modellpaarungen unter getauschten Farben mit sonst gleicher Konfiguration.  
**Alternativerklärung:** Matchvarianz, Startvorteil, Modell-/Providerdrift.

### H4 – Strategische Spezialisierung versus Verwundbarkeit
**Hypothese:** Ein ausgeprägter Schwerpunkt auf Go ist mit höherer Go-Kontrolle verbunden, kann aber gleichzeitig die Anfälligkeit gegenüber Schachmatt erhöhen.  
**Messung:** Gleichzeitige Zeitreihen von Go-Kontrolle, Chess-Risiken, Verteidigungsalternativen und Schwerpunktkodierung.  
**Alternativerklärung:** Die Schachgefahr war unabhängig vom Go-Fokus entstanden.

## 3. Hypothesenpool: Antizipation und Adaptivität

### H5 – Anticipation–Action Gap (priorisiert)
**Hypothese:** Modelle erkennen eine konkrete Gefahr, reagieren jedoch nicht rechtzeitig, obwohl noch regelkonforme Abwehrmöglichkeiten bestehen.  
**Messung:** Früheste explizite Bedrohungsäußerung, tatsächlich verfügbare Informationen, letzte engine-verifizierte Abwehrgelegenheit, ausgeführte Aktion, Folge.  
**Alternativerklärung:** Abwehr war in ANDY gar nicht legal/realistisch; erkannte Gefahr war anders oder nur konditional.

### H6 – Gegnerabhängige Adaptivität
**Hypothese:** Dasselbe Modell verändert seine Strategie systematisch abhängig von gegnerischen Spielmustern.  
**Messung:** Modell über Gegner/Matchverläufe vergleichen, jeweils gleicher Regel-/Konfigurationsraum.  
**Alternativerklärung:** Unterschiedliche Stellungen, Farben und Budgets erklären die Variation.

### H7 – Strategische Konsistenz
**Hypothese:** Erfolgreichere Modelle setzen dokumentierte mehrzügige Ziele häufiger konsequent um, sofern neue Informationen keine Anpassung erfordern.  
**Messung:** Vorab deklarierte Ziele und Zeitfenster mit Aktionen und überprüften Gründen für etwaige Abweichungen abgleichen.  
**Alternativerklärung:** Starre Konsequenz war in der Situation schlechter als ein Strategiewechsel; keine Erfolgsdefinition aus Siegerstatus allein.

### H8 – Reaktion auf Überraschungen
**Hypothese:** Modelle, die nach unerwarteten Gegneraktionen angemessen reagieren, erreichen häufiger strategische Ziele.  
**Messung:** Überraschung als dokumentierte Abweichung von spezifischer Vorhersage kodieren; Reaktionsqualität anhand zuvor festgelegter, regelgeprüfter Kriterien beurteilen.  
**Alternativerklärung:** Die Position war schon entschieden; scheinbare Anpassung ist nicht handlungswirksam.

## 4. Hypothesenpool: Ressourcenökonomie

### H9 – Budgetabhängige Strategie (priorisiert)
**Hypothese:** Bei geringerem Tokenbudget verändern Modelle ihre bevorzugten Siegwege oder die Länge ihrer strategischen Planung.  
**Messung:** Kontrollierte Budgetserien bei gleichen Modellen, Regeln, Reasoning-/Output-/Retry-Parametern; dokumentierte Schwerpunkt- und Planungshorizonte.  
**Alternativerklärung:** Zensierung durch frühe TKO-Enden statt geänderter Strategie.

### H10 – Effizienz adaptiver Entscheidungen
**Hypothese:** Modelle, die ihre Strategie frühzeitig anpassen, benötigen für vergleichbare Ergebnisse weniger Tokens oder API-Entscheidungen.  
**Messung:** Vergleichbare Match-/Positionscluster, Zeitpunkt der Anpassung, Gesamt- und Outputtoken, Retrykosten, erreichte Ziele.  
**Alternativerklärung:** Kürzere Partien oder leichterer Gegner; daher Normalisierung/Kontrollen nötig.

### H11 – Thinking ist nicht gleich Effektivität
**Hypothese:** Höherer Reasoning-Aufwand geht nicht zwangsläufig mit besseren Entscheidungen oder höherer Gewinnwahrscheinlichkeit einher.  
**Messung:** Reasoning-/Outputbudget sofern technisch kontrollierbar, vollständige Usage und definierte Entscheidungsqualität.  
**Alternativerklärung:** Verdeckte/anders deklarierte Thinking-Tokens oder providerabhängige Abrechnung.

### H12 – Ausführungszuverlässigkeit
**Hypothese:** Bei strengeren Retry- und Outputlimits beeinflussen Formatfehler und illegale Aktionen die Matchresultate stärker.  
**Messung:** Rohantworten → Parser-/Normalisierung → Legalität → ausgeführter Zug; Fehlerkategorien, Retrypfade, Terminierung.  
**Alternativerklärung:** Provideradapter-/Loggerverhalten statt strategischer Modelleigenschaft.

## 5. Hypothesenpool: Stabilität und Reproduzierbarkeit

### H13 – Modelltypische strategische Muster (priorisiert)
**Hypothese:** Dasselbe Modell zeigt bei identischen Spielbedingungen über mehrere Begegnungen wiederkehrende Entscheidungs- und Verhaltensmuster.  
**Messung:** Innerhalb-Modell-Variation vs. Zwischen-Modell-Variation, farbgepaarte Wiederholungen, Konfigurationsgleichheit, Verhaltenszeitreihen.  
**Alternativerklärung:** Gemeinsamer Prompt/Rollenvorgaben, dominantes Ruleset oder zu wenige unabhängige Partien.

### H14 – Gegnerabhängige Muster statt fester Rangfolge
**Hypothese:** Die relative Stärke zweier Modelle hängt vom Gegner ab und kann nichttransitiv sein.  
**Messung:** Mehrere Modellpaarungen, Farbwechsel und Wiederholungen; Paarungs-/Interaktionseffekte vor globaler Rangfolge.  
**Alternativerklärung:** Sampling-Unsicherheit und unkontrollierte Konfigurationsunterschiede.

### H15 – Abnehmende Vorhersagbarkeit unter Störung
**Hypothese:** Je stärker eine Partie vom erwarteten Verlauf abweicht, desto häufiger scheitern konkrete Vorhersagen der Modelle.  
**Messung:** Störung als vorab operationalisierte Abweichung von dokumentierter, testbarer Vorhersage; Vorhersagehorizont und Schwierigkeit kontrollieren.  
**Alternativerklärung:** Allgemein sinkende Claim-Spezifität oder spätere schwierigere Stellung, nicht Störung selbst.

## 6. Erste Prioritäten und überprüfbare Kernfragen

| Priorität | Hypothese | Pilotfrage |
|---|---|---|
| P0 | **H1** | Zeigt Argon in Wiederholungen einen Go-Schwerpunkt? |
| P0 | **H2** | Verschiebt Argon diesen Schwerpunkt nach Gegneraktionen? |
| P0 | **H5** | Werden erkannte Bedrohungen beantwortet, solange Abwehr legal möglich ist? |
| P0 | **H9** | Ändert ein niedrigeres Gesamtbudget den beobachtbaren Fokus? |
| P0 | **H13** | Bleiben Verhaltensmuster nach Farbtausch und Wiederholung erhalten? |

**Empfehlung:** Die Messdefinitionen und Ausschlussregeln für diese fünf Hypothesen **vor Datenerhebung** fixieren. Andere Hypothesen im Pilot **explorativ** führen. Kein p-Wert- oder Signifikanzversprechen bei 12 Partien.

## 7. Pilotdesign: Flash × Argon

**Bezugsmatch:** `andy_1c77f49b3e17` (Gemini 3.8 Flash vs. Gemini 4 Argon). Im bisherigen Material wird ein Go-KO vermutet; **noch nicht als engine-verifizierter KO behandeln**, da im verfügbaren Log das terminale `match_end` fehlt.

| Serienmatches | Farbzuordnung | Gesamt-Tokenbudget je Modell | Zweck |
|---|---|---:|---|
| M1–M2 | Flash Weiß / Argon Schwarz; danach Argon Weiß / Flash Schwarz | 100.000 | Ausgangspaar mit Farbtausch |
| M3–M4 | gleiche zwei Farbzuordnungen | 100.000 | erste Wiederholung |
| M5–M6 | gleiche zwei Farbzuordnungen | 100.000 | zweite Wiederholung |
| M7–M8 | beide Farbzuordnungen | 50.000 | kontrollierte Budgetvariation |
| M9–M10 | beide Farbzuordnungen | 50.000 | erste Wiederholung |
| M11–M12 | beide Farbzuordnungen | 50.000 | zweite Wiederholung |

**Präzisierung:** Dies ist ein *geplantes* Pilotdesign, nicht zwölf bereits vorliegende Partien. Das historische Ausgangsmatch kann als M1 nur gelten, wenn seine tatsächliche Konfiguration mit dem fixierten Design übereinstimmt und vorhandene, fehlende oder geänderte Settings dokumentiert werden. Bei nicht kontrollierbarer API-/Modellversion als **historischer explorativer Referenzfall** ausweisen statt kontrolliertem Versuchsmitglied.

**Sonst konstant halten:** Aufgelöste Modellversion, Strategie-/Promptmodus, A0/A1/A2, Reasoning-Einstellungen, Max-Output je Aufruf, Retries, Entscheidungslimit, Ruleset und Engine, Startzustand, falls möglich Zufallsparameter. Andere Änderungen explizit als separaten Versuchsarm kennzeichnen.

**Auswertung:** Jede Match-Paarung zunächst einzeln und mit Farbtausch beschreiben; Nenner und Unsicherheiten benennen, bei knappen Daten keine generalisierte Rangfolge. Frühzeitige TKO-Enden als zensierte Strategie-Beobachtung ausweisen, nicht automatisch als „kein Go-Fokus“.

## 8. Erforderliche Messgrößen / Datenschema

| Variable | Definition / Kernanforderung |
|---|---|
| **Strategic Orientation** | Explizite Zieläußerungen + Anteil wirklich optionaler Schach-/Go-Aktionen; Phasenzwang getrennt |
| **Strategic Switching** | Zeitstempel/Events, Anlass, vor-/nachher-Zielorientierung, alternative Erklärungen |
| **Anticipation Accuracy** | verifizierte konkrete Claims / auswertbare konkrete Claims, mit Horizont und Konditionen |
| **Adaptive Response** | dokumentierte Revision oder Verhaltensänderung nach neuem Ereignis; Legalität/Handlungsspielraum |
| **Execution Reliability** | rohe Ausgaben, Parsernormalisierung, gültig/ungültig, Retrys, API-Fehler |
| **Resource Efficiency** | Input-/Output-/Reasoning-Tokens getrennt soweit vorhanden; API-Zeit; bis Terminierung |
| **Victory Path** | KO_CHESS / KO_GO / TKO / ABORT, terminaler Nachweis und Engineprüfung |

**Pflicht-Metadaten:** `match_id`, `parent_match_id`, `rematch_group_id`, `rematch_index`, `color_swap`, tatsächlicher `config_snapshot`, Ruleset-/Engine-/Adapter-/Modellversion, `termination_reason`, `raw_file_sha256`, verfügbarer Startzustand, timestamp. Keine Felder für historische Matches erfinden; Unbekanntes ist `unknown`.

**Qualitätssicherung:** Exakte Event-Verweise, Codebook-Version, optional Doppelannotation/Dissensmarker, reproduzierbare Engine-Verifikation für zentrale Alternativzugclaims, unabhängige Prüfung von GO-KO (72 Punkte laut betrachteter Regelkonfiguration).

## 9. Validierungslogik für die Auswertung

1. **Vorab:** primäre Hypothesen und Messregeln fixieren; ggf. erwartete Richtung, Entscheidungsregel, Mindestdaten und Ausschlüsse ausdrücklich präregistrieren.
2. **Pro Match:** JSONL-Integrität, Spieler/Konfigurationssnapshot/KO-TKO-Status, Eventsequenz und Ressourcen prüfen.
3. **Pro Episode:** Information → Claim → verfügbare legale Optionen → Aktion → Gegnerantwort → Folge bewerten. Keine Outcome-Rückprojektion.
4. **Pro Farb-Paar:** Kennzahlen mit gleichen Definitionen tabellieren, Unterschiede und Störfaktoren dokumentieren.
5. **Übergreifend:** Muster und Gegenbeispiele zusammenführen, Unsicherheit sichtbar machen; erst bei größerer Stichprobe robuste Hypothesentests erwägen.
6. **Working Paper:** Beobachtung / Interpretation / Mechanismus-Hypothese / Einschränkung strikt trennen; Quellen und Rechenartefakte veröffentlichungsfähig versionieren.

## 10. Nächste Aufgaben

- [ ] Abschluss/Go-KO des Referenzmatches `andy_1c77f49b3e17` mit Original-JSONL und Engine klären.
- [ ] Rückkampf-Button: Modellspezifische Konfigurationen **mit dem Modell** zwischen Farben tauschen, nicht an Farbfelder koppeln.
- [ ] Verknüpfte Matchmetadaten `parent_match_id`, `rematch_group_id`, `config_snapshot` speichern.
- [ ] Terminierungsgründe KO_CHESS / KO_GO / TKO / ABORT strukturiert loggen.
- [ ] H1/H2/H5/H9/H13-Codebuch mit Messnennern und Entscheidungsregeln fixieren.
- [ ] Erste Farbtausch-Paare durchführen; 100k- und 50k-Arme sauber trennen.
- [ ] Fallbasierte **Individual Research Editions** erstellen, danach **Comparative Research Edition** und experimentelle Working Papers.

---

**Forschungsleitfrage:** *Do GPAI models display stable or adaptive preferences for different victory paths under novel coupled rules and constrained resources?*

**Nicht behaupten:** Nachgewiesener Go-KO im Referenzmatch, nachgewiesene Modellstrategie, kausale Budgetwirkung, allgemeine Modellintelligenz oder Neuheit ohne externe Literaturprüfung.


## 11. Ergänzung 13.11.2026 – Strategic Situational Awareness (SSA)

**Neues eigenständiges Methodenblatt:** [ANDY Strategic Situational Awareness v0.1](ANDY_STRATEGIC_SITUATIONAL_AWARENESS_SSA_v0.1.md).

Die ursprünglichen **15 Hypothesen H1–H15** bleiben unverändert. Ergänzend werden **sechs SSA-Hypothesen (SSA-H1–SSA-H6)** als neues, teilweise überlappendes Forschungsmodul aufgenommen. **21 bezeichnete Hypothesen**, aber **nicht 21 statistisch unabhängige Tests** (SSA-H4/H5 überschneiden sich thematisch mit H5/H9).

| ID | Kurzthese / Fokus |
|---|---|
| **SSA-H1** | Self-Assessment Accuracy: Stimmt die protokollierte Einschätzung eigener Vorteile und Gefahren mit überprüfbaren Zuständen überein? |
| **SSA-H2** | Opponent Threat Recognition: Wie früh werden gegnerische Gewinnchancen im vorhandenen Handlungsspielraum erkannt? |
| **SSA-H3** | Overconfidence under Advantage: Werden gegnerische Risiken bei eigenem Teilspielvorsprung unterschätzt? |
| **SSA-H4** | Awareness–Action Gap: Wird eine erkannte Gefahr rechtzeitig und angemessen beantwortet? |
| **SSA-H5** | Calibration under Resource Pressure: Ändert sinkendes Tokenbudget die Lageeinschätzung? |
| **SSA-H6** | Within-Match Reassessment: Revidieren Modelle Einschätzungen nach unerwarteten Gegneraktionen? |

**Vier SSA-Ebenen:** (1) eigene Lage, (2) gegnerische Lage, (3) überprüfbare Prognose, (4) tatsächliche Handlung innerhalb der noch verfügbaren legalen Alternativen. Korrekte Bedrohungserkennung ist nicht dasselbe wie eine korrekt vorhergesagte konkrete Gegneraktion; erfolgreich verhinderte Risiken nicht als Falschprognose zählen.

**Erforderliche Zusatzfelder für Matchauswertung:** Claim-Typ/self/opponent, exakte Äußerung und Event-ID, Sichtbarkeit/Informationsstand, Bedrohungs-/Alternativenprüfung mit echter ANDY-Engine, Forecast-Kondition und Horizont, unmittelbare und spätere Reaktion, Validierungsstatus. Vollständiges Codebuch, Messgrößen und Gegenhypothesen im verlinkten SSA-Methodenblatt.

**Status:** Entwurf; bisher keine SSA-Claims aus den Rückkämpfen validiert. Zunächst bei 100k-Farbtauschserie explorativ messen; später präregistriert und mit unabhängigen Wiederholungen testen.


## 12. Ergänzung 13.11.2026 – Infrastrukturabhängigkeit und Go-Spiegelantworten (INF)

**Auslöser:** Die Projektleitung berichtet als **subjektive, bisher nicht systematisch vermessene Beobachtung**, dass diagonale Go-„Spiegelzüge“ besonders häufig erscheinen könnten, wenn beide Kontrahenten über **denselben API-Schlüssel** desselben Anbieters aufgerufen werden. Daraus folgt ausdrücklich **weder** ein nachgewiesener Zusammenhang **noch** ein Nachweis gemeinsamer Modellzustände oder Kommunikation zwischen Modellaufrufen.

**Querverweis:** [ANDY Series Explorer & Opening/Pattern Atlas](../ANDY_SERIES_EXPLORER_OPENING_PATTERN_ATLAS_BLUEPRINT_v1.0.md) – künftiger Offline-Batch-Detektor für symmetrische Opening-Muster.

### Ergänzende, konkurrierende Hypothesen

| ID | Hypothese / Alternative | Status |
|---|---|---|
| **INF-H1 – Shared API Key Mirror Effect** | Bei gleicher Modellpaarung und konstanten Spielbedingungen treten in Go-Eröffnungen mehr **zeitlich nachvollziehbare diagonale Antwortspiegelungen** auf, wenn beide Modelle denselben API-Key verwenden, als wenn sie getrennte Keys verwenden. | Explorativ, ungeprüft |
| **INF-H2 – Shared Project vs. Shared Key** | Beobachtete Unterschiede korrelieren eher mit gemeinsamem Providerprojekt, dessen Routing-/Quota-/Konfigurationseffekten als mit der Identität des API-Schlüssels selbst. | Konkurrierende Mechanismushypothese, ungeprüft |
| **INF-H3 – Model-Family / Heuristic Confounding** | Spiegelmuster werden primär durch verwandte Modellfamilien, ähnliche Instruktionen oder unabhängige räumliche Heuristiken erklärt und bleiben auch bei getrennten Keys/Projekten bestehen. | Alternativerklärung, ungeprüft |
| **INF-H4 – Rules/Position Baseline** | Häufige diagonale Go-Antworten entstehen überwiegend aufgrund der ANDY-Regeln, des Startzustands, der verfügbaren legalen Setzpositionen und der Zugreihenfolge – unabhängig vom Zugangskontext. | Null-/Alternativerklärung, ungeprüft |

**Wichtige technische Trennung:** Ein API-Key authentifiziert Zugriffe; gemeinsame Nutzung desselben Keys ist **kein Beleg** dafür, dass zwei Aufrufe Speicher, Prompt-Historie oder Spielentscheidungen teilen. Quoten/Projektlimits können gegebenenfalls gemeinsam gelten. Unterschiedliche Anbieterpaare sind **kein isolierter Test** des Key-Effekts, weil gleichzeitig Modell und Provider wechseln.

### Mess- und Codebuchvorschlag

- **Betrachtungseinheit:** tatsächliche, ausgeführte Go-Antwortgelegenheiten in einer vorab fixierten Eröffnungsphase (z. B. erste 5/10/16/20 Go-Setzungen); nicht alle API-Calls und nicht alle Steine eines Endboards.
- **Spiegelabbildungen auf 13×13 (0-basiert):** Hauptdiagonale `(x,y) -> (y,x)`; Gegendiagonale `(x,y) -> (12-y,12-x)`. Zusätzlich exakte Gegenfarbe- und Eigenfarbe-Varianten getrennt erfassen. Symmetrie-Transformationen nur vergleichen, soweit die vollständigen ANDY-Regeln sie zulassen.
- **Mirror Response Rate (MRR):** Anzahl nach definiertem Reaktionsfenster tatsächlich gespielter spiegelkorrespondierender Go-Antwortzüge / Anzahl aller **regelkonform möglichen und vollständig beobachteten** Go-Antwortgelegenheiten. Reaktionsfenster (z. B. nächster eigener Go-Zug oder innerhalb 1–3 eigener Go-Züge) **vor** Serienprüfung festlegen; gleiche Antworten nicht mehrfach zählen.
- **Von bloßer Brettsymmetrie trennen:** `static_occupancy_symmetry` ≠ `temporal_mirror_response`. Gespiegelte Stelle muss zum betreffenden Zeitpunkt zulässig gewesen sein, sonst nicht als „verpasste Antwort“ werten.
- **Ausgabe:** MRR und zugehöriger Nenner, Anzahl Match-/Seriencluster, Unsicherheitsbereich, Haupt-/Gegendiagonalvariante, Effektgröße zwischen Versuchsarmen, Go-Setup-Fenster, Roh-Event-IDs und Konfigurationsklasse.
- **Nullvergleich:** Regelkonforme, zustandsbedingte Zufalls-/Permutationstests oder geeignete Kontrollserien; keine Rückkehr des Zufallsspielers in die Arena notwendig. Nach Symmetrie und mehrfachen Hypothesenprüfungen Korrekturen/Sensitivitätsprüfung vorsehen.

### Experimentdesign zur Unterscheidung der Erklärungen

| Arm | Modelle und Matchbedingungen | Providerzugang |
|---|---|---|
| **A** | Flash × Argon, Ruleset/Prompts/Reasoning/Output/Retry/Budget identisch | Beide Aufrufe **derselbe API-Key** |
| **B** | Dieselbe Paarung und Settings | **Zwei Keys, ein Anbieterprojekt** |
| **C** | Dieselbe Paarung und Settings | **Zwei Keys, getrennte Anbieterprojekte** |
| **D (optional, anderes Erkenntnisziel)** | Vergleichbare Spiele mit anderen Modellfamilien/Anbietern | Untersucht Modell-/Provider-Effekte, **nicht** isoliert den Key-Effekt |

- Pro Arm mehrere **unabhängige** Matchserien mit Farbtausch; Zuordnung von Arm und Spielreihenfolge möglichst randomisieren/blocken, um Tageszeit, Quoten-/Serverlast und Modellupdates zu entkoppeln.
- Effektive Modellversion, Adapter, API-Endpunkt, Account-/Projekt-Konfigurationskennung, Budget, Retry, Outputlimit, Prompt, Regeln, Sampling-Einstellungen und relevante Zeitstempel protokollieren; **niemals echte API-Keys in JSONL, GitHub, Logs oder Exporte schreiben**. Nur nicht-geheime, pseudonymisierte `key_group_id` und `project_group_id` verwenden.
- Prüfen, ob projektübergreifende Versuchsarme technisch/organisatorisch zulässig und tatsächlich unabhängig sind; Kosten und Projektregeln berücksichtigen.
- Bereits beobachtete Serien dienen zur **Hypothesengenerierung**; zukünftige Kontrollserien nach fixierter Operationalisierung zur Prüfung. Keine nachträgliche p-Wert-„Bestätigung“ am Entdeckungsdatensatz.
- Entscheidungen innerhalb eines Matches und Rückkämpfe einer Serie sind korreliert; Clusterstruktur bei Unsicherheit und Aggregation berücksichtigen.
- **Interpretationsgrenze:** Ein stabiler Unterschied zwischen Armen kann mit Infrastrukturbedingungen zusammenhängen, beweist ohne Mechanismenprüfung aber weder geteilte Gedanken noch koordinierte Entscheidungen.

### Umsetzung im Offline Series Explorer

**P1/Pattern-Detektor:** `static_diagonal_symmetry`, `temporal_mirror_response`, exakte vs zonenbasierte Spiegelung; separat nach Haupt-/Gegendiagonale, Akteur-/Farbperspektive, Go-Setup-Fenster.

**P2/Serienvergleich:** Nach `key_group_id` und `project_group_id` gruppierte, anonymisierte Intra- und Cross-Series-MRR-Verteilungen sowie Konfigurationsvergleich; Nullmodell und Unsicherheit sichtbar.

**P3/Semantik:** Erst später prüfen, ob Modelläußerungen explizit einen Spiegelplan ankündigen. Fehlende Äußerung ≠ fehlendes geometrisches Muster.

**Übergreifender Forschungsstatus:** vier neue benannte INF-Hypothesen; zusammen mit H1–H15 und SSA-H1–H6 nun **25 Hypothesenbezeichnungen**, mit thematischen Überschneidungen und **ohne** Anspruch auf 25 unabhängige Tests.


## 13. Ergänzung 14.11.2026 – Vermeidbare Instabilität / Avoidable Instability (VI)

**Forschungsfrage:** Wann erzeugt ein GPAI-Akteur durch eine eigene Entscheidung zusätzliche, vermeidbare Instabilität, obwohl eine regelkonforme und im Gesamtsystem günstigere Handlung verfügbar gewesen wäre? Nicht jede Nichtnutzung einer Gelegenheit ist ein Fehler: bewusster Verzicht, Opfer, langfristige Strategie oder verdeckte Risiken können lokale Nachteile rechtfertigen.

**Explorativer Ausgangsfall VI-CASE-001:** Screenshot der laufenden 8082-Arena vom 14.11.2026, 15:46:56 (Dateiname). Weiß Claude Opus 5.5, Schwarz GPT-6 Astra; Anzeige 179 KI-Aufrufe, 171 ausgeführte Züge, 8 Fehler/ungeklärt; Go-Kontrolle 48:45; Budget je 350.000, angezeigt verbraucht Weiß 246.852, Schwarz 150.523. Schwarzer König wurde laut sichtbarer Markierung verschoben; angezeigte Modellbegründung: „Weicht dem Schach aus und aktiviert den König zur Unterstützung des Freibauern f5.“ Projektleitung vermutet als Alternative, den weißen Turm mit dem schwarzen Bauern zu schlagen. Die konkrete Schlagnotation ist **nicht ohne Koordinaten-/Zustandsprüfung festlegbar**; maßgeblich sind der Zustand vor dem Königszug und die tatsächliche ANDY-Engine. Screenshot ist ein Hinweis, kein Nachweis einer verpassten legalen Gelegenheit. Match-ID, Event-ID, exakte Koordinaten, Chess-/Go-Aktionsphase, Legalität, Bedrohungslage vor der Aktion, Folgen und Matchresultat offen. Keine Aussage über die interne Absicht oder Qualität des Zuges. Screenshot bleibt lokale Referenz; nicht als Original-JSONL ausgegeben.

| ID | Hypothese / Gegenhypothese | Status |
|---|---|---|
| VI-H1 | Modelle lassen in vergleichbaren Situationen verfügbare, robust günstigere Handlungsmöglichkeiten ungenutzt; daraus kann zusätzliche Verwundbarkeit oder Ressourcenbelastung entstehen. | Explorativ |
| VI-H2 | Häufigkeit und Folgen solcher Entscheidungen unterscheiden sich mit Gegner, Spielphase, Budget und verfügbarer Information. | Explorativ |
| VI-H0 | Die vermeintlich bessere Alternative ist illegal, erfordert eine nicht verfügbare Aktion, verschlechtert Schach-Go-Gesamtlage, ist strategisch riskanter oder nicht robust besser; keine vermeidbare Instabilität nachweisbar. | Gegenhypothese |

**Prüfpfad:** Original-JSONL + JSON und historische Engine-Version zuordnen; Vorher-Zustand rekonstruieren; alle legalen Reaktionen auf das Schach prüfen (einschließlich Bauernschlag, falls legal); gespielte und alternative Aktion mit gleichen Annahmen über Gegnerantworten und Go-Kopplung untersuchen. Unmittelbare Folgen (Schachgebot, Material, Go-Kontrolle, neue Bedrohungen) und mittelfristige Folgen über ein vorab definiertes Fenster getrennt beurteilen. Alternativverläufe sind kontrafaktische Analysen, keine gespielten Ereignisse; bei unklarem Trade-off keine Dominanz behaupten. Beobachtete Modellbegründung getrennt von Interpretation und tatsächlichem Folgeverlauf ausweisen.

**Klassifikation (Entwurf):** externe Störung; unvermeidbare Instabilität; strategisch in Kauf genommene Instabilität; potenziell vermeidbare Eigeninstabilität; unentscheidbar. Auch korrekt ausgeführte legale Züge können strategisch ungünstig sein (Dynamic Bonoma), aber nicht allein anhand ihres späteren Ergebnisses klassifizieren. Kein automatischer Fehlerpunkt oder Score-Abzug.

**Serienanalyse:** Anzahl belastbar geprüfter Gelegenheiten als Nenner, Anteil potenziell vermeidbarer Entscheidungen, Folgen für Handlungsoptionen, Bedrohungen, Ressourcen und Erholungsdauer; Match-/Seriencluster, Alternativen und Unsicherheit anzeigen. Vergleich mit zustandsbedingt regelkonformer Zufallsreferenz nur bei gleicher Ausgangslage und Auswahlregel. Visueller Einstieg: Vorher-Brett, tatsächliche Aktion, alternative Aktion und Folgeposition nebeneinander; analytische Ansicht mit Legalität, Konsequenzen, Nennern und Gegenfällen. Beide Ansichten greifen auf dieselben Zustände und Event-IDs zu. Anonymisierte menschliche und KI-Deutungen optional vor Kenntnis des Ausgangs erfassen.

**Bezüge:** H5, H7, H8, H10, SSA-H1/H2/H4; Forschungsfelder 02 Lageeinschätzung, 03 Adaptivität, 04 Ressourcen, 05 Stabilität; [Dynamic Bonoma](../CORE/v0.1/05_DYNAMIC_BONOMA.md), [Erkenntniskern](../CORE/v0.1/README.md). Bestehende IDs unverändert. VI-H0 ist Gegenhypothese, VI-H1/H2 sind zwei neue explorative Arbeitshypothesen, keine unabhängigen bestätigten Tests.


## 14. Forschungsagenda – PUNCH LAB / Controlled Destabilization & Adaptive Recovery (PL)

**14.11.2026 · Eigenständiges zukünftiges Forschungsfeld · explorativer Entwurf, keine validierten Befunde.** 
Claim: **Every AI has a plan until they get punched in the ANDY Arena ...**
Leitidee der Projektleitung: Chaos gezielt verursachen und beobachten, wie ein Akteur aus der veränderten Situation heraus neue Stabilität erzeugt. Experimentelle Anwendung des ANDY-Meta-Modells (Chaos – Muster – Ordnung); neue Ordnung muss nicht der alten entsprechen. Chaos bezeichnet hier metaphorisch erhöhte Unvorhersagbarkeit, keinen Nachweis mathematischen Chaos. Erleben. Erforschen. Erahnen.

### Forschungsfragen
| ID | Frage / Arbeitshypothese |
|---|---|
| PL-H1 | Wie viele zusätzliche Tokens, API-Aufrufe und Zeit benötigt ein Akteur zur korrekten Lageerfassung und Neuorientierung nach einer kontrollierten Störung? |
| PL-H2 | Wie zutreffend ist die Lageanalyse (eigene und gegnerische Chancen, Gefahren, legale Optionen, Schach-Go-Kopplung), und wie angemessen ist die tatsächlich ausgeführte Reaktion? |
| PL-H3 | Wie schnell, nachhaltig und ressourcenökonomisch stellt ein Akteur relative Wettbewerbsstabilität wieder her? Alte Ordnung, neue Ordnung, Teiladaptation oder Kollaps? |
| PL-H4 | Wie verändern Intensität, Zeitpunkt, Art und Dauer der Störung sowie Gegner und Budget die Reaktion? Gibt es einen situativen Sweet Spot? |
| PL-H5 | Beeinflusst eine plausible technische Fehlererklärung oder fingierte strategische Deutung die Lageanalyse gegenüber derselben tatsächlichen Stellung ohne Erklärung? Wird eine fremdbestimmte Aktion nachträglich als eigene begründet? |
| PL-H0 | Unterschiede können natürliche Samplingvarianz, Gegnerantworten, veränderte Kontextlänge, Positionseffekte, technische Grenzen oder unvollständige Information statt adaptive Fähigkeit widerspiegeln. |

### Experimentdesign
Aus einem vollständig rekonstruierbaren, versionierten Zustand getrennte Experimentzweige erzeugen. Zuerst einmalig einen vom Modell vorgeschlagenen Zug durch einen anderen **nach vollständigen ANDY-Regeln legalen** Zug ersetzen; plausible simulierte Koordinaten-/Ausführungsabweichung. Keine realen produktiven Fehler einbauen. Spätere Varianten: ungewöhnlicher Gegnerzug, Kontextverlust, Ressourcenschock, Gegnerwechsel, widersprüchliche Statusmeldung; je Versuch einen Faktor isolieren, Kombinationsversuche separat. Eingriffsstärke vorab über objektive Zustandsmerkmale (z.B. Verlust legaler Optionen, Bedrohungen, Go-Kontrolle, Material) beschreiben, nicht pauschal aus Zugdistanz oder Ergebnis ableiten.

| Arm | Aktion | Modellinformation |
|---|---|---|
| A | Unverändert | Normale Meldung; wiederholte neue Kontrollfortsetzungen neben historischem Original |
| B | Legal ersetzter Zug | Tatsächlicher Zustand und ausgeführter Zug, keine zusätzliche Erklärung |
| C | Derselbe Alternativzug | Zusätzlich plausible simulierte technische Fehlererklärung |
| D | Derselbe Alternativzug | Zusätzlich fingierte strategische Erklärung |

Ursprüngliche Absicht und tatsächlich sichtbaren Kontext pro Aufruf erfassen; ohne Kenntnis der eigenen früheren Wahl keine Nichterkennung oder Nachrationalisierung unterstellen. Gleiche Ausgangslage, Gegner, Regelversion, Budget, verfügbare Historie und übrige Parameter soweit möglich; Promptlängen und Usage-Effekte separat dokumentieren. Wiederholungen, Farb-/Rollenwechsel, randomisierte Reihenfolge und vorab definierte Horizonte. Historischer Originalverlauf allein ist keine ausreichende Kontrolle. Kein erzwungener neuer Analyseprompt nur im Interventionsarm; einheitliche Messbedingungen.

### Messgrößen (Entwurf, keine feste Gesamtpunktzahl)
| Dimension | Operationalisierungsvorschlag |
|---|---|
| Recognition | Erste explizite, nachprüfbare Erkennung der Abweichung; nur unter ausreichender Information; nicht erkannt / unentscheidbar getrennt |
| Situational Awareness | Korrekte, falsche, fehlende und unprüfbare Claims zu Brett, Regeln, Gefahren, Chancen und verfügbaren Optionen; Engine und blind annotierte Kriterien |
| Reorientation | Erste nachvollziehbare Aktualisierung des Plans bzw. kontextgerechte Verhaltensänderung; begründetes Beibehalten kann angemessen sein |
| Execution & Reaction Quality | Illegalitäts-/Retry-Rate, tatsächliche Handlungen, unmittelbare und spätere Folgen, Vergleich zu legalen Alternativen; keine Gleichsetzung von Legalität mit strategischer Güte |
| Recovery Cost | Input-/Output-/Reasoning-Usage nach Providersemantik ohne Doppelzählung; kumulierte Tokens vom ersten für das Modell sichtbaren Punch bis Erkennung, Neuorientierung und bestätigter Restabilisierung jeweils separat; Zeit, Calls, ausgeführte Aktionen, Retrykosten; Mehrverbrauch gegenüber vergleichbaren Kontrollen, auch negativer Mehrverbrauch möglich |
| Recovery Quality / Time | Zeit und Aktionen bis vorab definierter, über ein festgelegtes Fenster anhaltender relativer Handlungsfähigkeit; Brett-/Ressourcen-/Bedrohungsmerkmale getrennt, Vergleich mit Ausgangslage und Kontrollverläufen; neue wirksame Ordnung zulässig |
| Failure / Overshoot | Keine Erholung bis Horizont, KO/TKO, externe Abbrüche, erneute Destabilisierung; zensierte Fälle und verbleibende Ressourcen sichtbar, nicht als null Zeit/Kosten behandeln |

Mögliche Ergebnisprofile: Festhalten, Eskalation, Wiederherstellung, Neuorganisation, adaptive Verbesserung oder unentscheidbar. Keine inneren Denkmechanismen aus Modelltext ableiten. Bei nicht messbarer Stabilität keine künstliche Stabilitätskurve als Ergebnis; Einzelmetriken zeigen. **Tokens zur Lageerfassung/Neuorientierung sind beobachteter Verbrauch in definierten Phasen, keine direkt messbaren internen Denkanteile.**

### Evidenz, Architektur und nächste Schritte
Eigene experiment_id, branch_id, parent_logical_match_id, source_event_id, pre/post_state_hash, intended/executed_action, intervention_type, simulated_reason, actual_model_visible_message, trigger, intensity, random_seed soweit verfügbar, control_arm, config_snapshot, rule/engine versions, timestamps und Usage. Originale unverändert; experimentelle Partien eindeutig markieren und vom regulären Arena-Leaderboard ausschließen. Keine heimliche Änderung produktiver Infrastruktur, kein automatischer API-Start; Kostenfreigabe. Pattern View (Vorher/Nachher, alternative Verläufe) und Analytical View (Recovery-Kennzahlen, Verlauf, Streuung) gleichberechtigt. Adaptive Recovery Fingerprint erst nach Methodenvalidierung, kein universeller Intelligenzscore. Bezüge SSA, VI, H5/H8/H10/H11/H15, Dynamic Bonoma, Sweet Spot?, Competitive Mirroring, Nested Competitive Networks. 

**Priorität:** zunächst natürliche Serien als Vergleichsbasis sammeln; Board State Export und Legal Action Explorer sowie sichere experimentelle Verzweigung prüfen. Danach kleiner Pilot mit einmaligem legalem Zugersatz und wiederholten Kontrollen, erst anschließend Experiment Designer / automatisierte Auswertung. Kein aktueller Entwicklungsauftrag an Thread 1, keine Implementierungsbehauptung. Bestehende Hypothesen und Agenda bleiben erhalten.


## 15. Forschungsagenda – ANDY Situation Challenge / Problemlösefähigkeit (SC)

14.11.2026 · Eigenständiges zukünftiges Forschungsthema, exploratives Experimentdesign. Von der Projektleitung angeregt und zur Aufnahme freigegeben.

**Leitfrage:** Wie gut kann ein GPAI-Akteur eine vorgegebene, nicht von ihm selbst entwickelte Wettbewerbssituation erfassen und unter begrenzten Ressourcen das Beste daraus machen? Nicht nur eine eigene Strategie fortsetzen, sondern eine laufende Partie übernehmen, Chancen und Gefahren erkennen, Ziele priorisieren und wirksam handeln. Erleben. Erforschen. Erahnen. Keine universelle Messung von Intelligenz oder Problemlösefähigkeit außerhalb der untersuchten ANDY-Konfiguration.

### Versuchsformat
- Eine regelgültige, nicht terminale Midgame-Konstellation S0 aus einer realen Partie auswählen und unveränderlich versionieren. Mehrere Modellpaarungen treten aus exakt demselben vollständigen Ausgangszustand gegeneinander an; die sichtbare Brettposition allein genügt nicht.
- Ausgangsseite, Aktionsphase, Schach- und Go-Zustand, Zugrechte, regelrelevante Historie (einschließlich Wiederholungs-/Ko-Information, soweit nach Regelversion benötigt), Zähler, Siegbedingungen, Konfiguration und Engine-Version sichern. Zustandshash und deterministischen Import/Replay prüfen; Modell-, Farb- und Budgetzuordnung getrennt vom Brettzustand dokumentieren. Fehlende Zustandsinformationen blockieren den Start.
- Erste Pilotvariante mit neu zugeteiltem, für alle gleichen Weiterführungsbudget; historische Restbudgets als gesonderte Variante. Beide Modelle erhalten gleiche Informationsbedingungen; vergleichbare Caps, Calls, Retries und sonstige Einstellungen. Farben/Rollen tauschen durch Modellzuordnung zu den vorhandenen Seiten, nicht durch stillschweigende Brettspiegelung. Wiederholte Paarungen, gleiche Ausgangslagen und möglichst randomisierte Reihenfolge. Gegnermodell und Seite separat ausweisen; ergänzend feste Referenzgegner und Self-Play möglich.
- **Cold Start:** vollständiger regelrelevanter Zustand und Regeln, ohne zusätzliche strategische Vorgeschichte. **Warm Start:** zusätzlich standardisierte bisherige Partiehistorie, ohne nachfolgende Ereignisse oder Ergebniswissen. Regelrelevante Historie bleibt in beiden Armen erhalten. Unterschiede in Promptlänge und Usage ausweisen. Keine Behauptung, dass Modelle die ursprüngliche Absicht früherer Spieler kennen.
- Die erste Entscheidung je Modell gesondert erfassen. Nur die erste handelnde Seite sieht unverändertes S0; die zweite reagiert bereits auf die erste Aktion. Für isolierten Vergleich identischer Erstentscheidungen derselben Seite separate unabhängige Entscheidungspiloten aus S0 verwenden; kein zusätzlicher Analyseprompt ausschließlich für einzelne Modelle.

### Forschungsfragen (noch keine bestätigten Hypothesen)
| ID | Frage |
|---|---|
| SC-Q1 | Wie zutreffend und vollständig erfasst das Modell die vorgegebene Situation (Fakten, akute Gefahren, Chancen, legale Optionen, Schach-Go-Kopplung)? |
| SC-Q2 | Wie angemessen sind Zielwahl, erste Entscheidung und folgende tatsächlich ausgeführte Handlungen, insbesondere bei widersprüchlichen Teilspielzielen? |
| SC-Q3 | Wie viel gemeldete Usage (Input, Output, Reasoning soweit ausgewiesen), Zeit, Calls und Retries werden zur Orientierung und weiteren Problembearbeitung benötigt? |
| SC-Q4 | Wie entwickeln sich Handlungsfähigkeit, Brettmerkmale, Ressourcen und Endgrund über gleiche vorab definierte Folgefenster? Werden Chancen genutzt, Nachteile begrenzt oder neue Probleme erzeugt? |
| SC-Q5 | Welche Muster verändern sich mit Rolle, Situation, Gegner, Ressourcenprofil oder verfügbarer Historie? Welche bleiben über Wiederholungen erkennbar? |

### Situation Library
Versionierte Situationen aus realen Partien, z.B. nominell ausgeglichene Position, Material-/Go-Rückstand, Vorsprung, gegenläufige Schach-/Go-Vorteile, akute Matt- oder Go-KO-Gefahr, Ressourcenknappheit (separates Budgetprofil), strategisch mehrdeutige Lage. Labels nur anhand dokumentierter beobachtbarer Merkmale vergeben, nicht als bestätigte Positionsbewertung oder vorweggenommene optimale Lösung. Auswahlkriterien und Gegenbeispiele festhalten; nicht ausschließlich spektakuläre Fälle selektieren.
Vorgeschlagene Metadaten: situation_id, version, source_logical_match_id, source_segment_id, source_event_id, state_hash, state_schema_version, rule/engine_version, full_state_ref, history_ref, selection_reason, observed_features, validation_status. Experiment-ID, Wiederholung, Rollen-/Modellzuordnung, Konfiguration, tatsächlich sichtbarer Kontext, Budgetmodus, Ergebnis und Endgrund getrennt speichern. Keine Originaldaten verändern; keine experimentellen Fortsetzungen dem regulären Arena-Leaderboard zurechnen.

### Auswertung
Lageanalyse (prüfbare zutreffende, falsche, fehlende, unentscheidbare Aussagen), tatsächliche Legalität und Execution, Reaktions- und Strategieverlauf, Ressourcenverbrauch nach dokumentierter Providersemantik, Go-Kontrolle, Material, Bedrohungen, verfügbare Optionen, Endgrund und Terminal Position Profile getrennt. Einheitliche Zeit-/Aktionsfenster; früh beendete Partien und fehlende Daten markieren. Kein pauschaler Gesamtwert aus Schach, Go und Tokens und keine Behauptung optimaler Problemlösung anhand eines Sieges. Modellbegründung ist keine direkte Messung innerer Denkprozesse. Exakte Engine-Fakten von strategischen Deutungen trennen; natürliche Modellvarianz, Gegnereffekte und Auswahl der Situationen berücksichtigen.

### Einordnung und Weiterentwicklung
Observation Lab beobachtet natürliche Dynamik, Serial Lab wiederholt vergleichbare Duelle, Situation Challenge setzt identische Anfangsbedingungen mitten im Spiel, Punch Lab (§14) verändert gezielt einen laufenden Zustand. Situation Challenge kann eine technische Vorstufe für sichere experimentelle Verzweigung im Punch Lab sein, ist aber methodisch eigenständig: keine eigene frühere Strategie und keine absichtliche nachträgliche Destabilisierung erforderlich.

Gemeinsame Situation Library perspektivisch für Lab, Academy und KI-Coach nutzbar: dieselbe Herausforderung kann ein Mensch in einer Demo selbst **erleben**; Lab erforscht Verläufe, wir erahnen Zusammenhänge. Keine vorgegebene optimale Lösung, solange nur Beobachtungen/Deutungen vorliegen. Verknüpfungen zu LAB-R06, R07, R08 (wo einschlägig), R09 und R10 als mögliche spätere Requirements-Impulse, nicht als Änderung des aktuellen Best-of-Pools.

**Nächster Schritt (Vorschlag):** vollständigen Board-State-Export und sichere Midgame-Initialisierung mit Original-Engine prüfen; einen realen Zustand reproduzieren, Legalität und Phasenübergang prüfen, erst dann einen kleinen wiederholten Pilot mit Farbwechsel und identischem Budget entwerfen. Bestehender Resume-Pilot ist kein Nachweis beliebiger Midgame-Starts. Kein aktueller Implementierungsauftrag, kein API-Start, keine Kostenfreigabe, keine neue bestätigte Hypothese. Der laufende A/B/C-Prozess für das neue Lab bleibt unverändert.


### Ergänzung – Problemlöse-Demo / alternative Handlungsverläufe

Welche Züge führen aus einem Problem heraus, welche verschärfen es möglicherweise? Die Academy-Demo lässt aus identischem S0 selbst gewählte legale Aktionen, unmittelbare regelgeprüfte Folgen und alternative Weiterführungen erleben. Wirkungskategorien als offene Deutungen: Problemlösung, Problemverschiebung, Problemverschärfung, Problemumkehr, Problemübertragung. Rücksprung und Zweigvergleich; tatsächliche KI-Aktionen optional erst nach eigener Entscheidung zeigen. [Interaktionskonzept und Testentwürfe v0.1](../REQUIREMENTS/v0.1/SITUATION_CHALLENGE_DEMO.md). Strategische Langzeitwirkung bleibt Erahnen; keine vorweggenommene optimale Lösung. Kein Implementierungsauftrag.
