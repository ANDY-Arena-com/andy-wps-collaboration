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
