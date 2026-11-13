# ANDY Lab – Event-to-Evidence Method (A-EEM) v0.1
## Anticipation · Adaptive Response · Actionability · Outcomes · Cross-Match Evidence

**Status:** Methodischer Entwurf / experimentelle Working-Paper-Basis, **nicht validiert oder publiziert**  
**Datum:** 13. November 2026  
**Scope:** Einzelmatch als erste Untersuchungseinheit; wiederholbare Anwendung auf mehrere ANDY-Partien; Vergleich erst nach kontrollierter Harmonisierung.

**Verknüpfungen:**
- [ANDY Masterplan](../../../PROJECT/ANDY_GESAMTKONZEPT_MASTERPLAN_v1.0.md)
- [Individual Research Edition 001](../INDIVIDUAL_RESEARCH_EDITION_001_ANTIZIPATION_ADAPTIVITAET_LEARNINGS_BLUEPRINT_v0.1.md)
- [Vergleichende Research Edition – 24-Seiten-Blueprint](../COMPARATIVE_RESEARCH_EDITION_001_24_SEITEN_BLUEPRINT_v0.1.md)
- [Bestehendes Lab-Memo zu Intentionen und Responsivität](../ANDY_LAB_MEMO_Intentions_Antizipation_Responsivitaet_v0.1.md)
- [Claude-Review als externer Prüfauftrag](../REVIEWS/CLAUDE_SONNET55_REVIEW_ASTRA_OPUS_MATCH_v0.1.md)

> **Kernsatz:** Nicht bloß bewerten, ob eine Prognose später zutraf, sondern **wann** welche Information verfügbar war, welche Gegenreaktionen damals **regelkonform möglich** waren, ob das Modell eine Bedrohung **erkannte**, wie es **handelte**, und was **tatsächlich** folgte. Dieselbe Kodierung zuerst innerhalb eines Matches und dann über verschiedene Matches verwenden.

## 1. Forschungsmethodische Anspruchsgrenzen

ANDY schafft die Möglichkeit eines **integrierten, nachvollziehbaren Forschungsformats** aus (i) gemeinsamem Chess/Go-Spielraum, (ii) API-/Zugversuchs- und Zustandslogs, (iii) öffentlich überprüfbarer regelbasierter Ausführung, (iv) zitierfähigen Modelläußerungen, (v) Ereignis-/Zeit-/Ressourcenverläufen und (vi) menschlicher und maschinenlesbarer Forschungsausgabe. **Ob dieses Format weltweit ohne Vorläufer ist, ist nicht geprüft.** Neuheitsansprüche brauchen systematische Literatur- und Benchmark-Recherche, definierte Abgrenzung und fachliche Begutachtung.

Von Modellen ausgegebene Begründungen sind **Textereignisse**, keine verifizierte interne Kognition. „Learning“ bedeutet hier primär **Forschungs-Learnings** und gegebenenfalls **in-context beobachtbare Anpassung**, nicht nachgewiesenes Training/Parameterupdate.

## 2. Die fünf Analyseebenen

1. **State & Information:** Tatsächlicher Schach-Go-Zustand und welche Informationen im Request für den Akteur verfügbar waren; Input, Regeln, Limits, Verlauf, Zeit.
2. **Claim & Anticipation:** Explizite überprüfbare Prognosen, Zielankündigungen, Risikoaussagen; Bedingungen und Horizont vor Feststellung des tatsächlichen Ausgangs kodieren.
3. **Decision & Feasibility:** Gewählter Zugversuch; legal/illegal/formatfehlerhaft; vorhandene legale ANDY-Alternativen; was im damaligen Regelzustand überhaupt vermeidbar oder erzwungen war.
4. **Response & Adaptation:** Gegnervorgang, neue verfügbare Information, danach gewählter Zug und evtl. dokumentierte Planänderung; Reaktionsangemessenheit nur nach explizitem Kriterium und Alternativencheck.
5. **Outcome & Resources:** Lokale Wirkung, globale Gewinnbedingung, API-/Token-/Zeitverbrauch, Retries; Kausalität nicht aus Chronologie ableiten.

**Analyseketten:** State → Claim → Event → Decision → Feasibility → Response → Outcome. Jeder Pfeil ist eine überprüfbare Relation, keine psychologische Zuschreibung.

## 3. Beobachtungs- und Klassifikationsschema pro Ereignis

| Gruppe | Pflichtfelder / Hinweise |
|---|---|
| Provenienz | match_id, event_id, raw_file_sha256, ruleset, engine_commit, parser_version, analyst/reviewer, timestamp |
| Player context | actor, color, phase (CHESS/GO), model/provider/version, relevant prompt/settings, budget |
| State | pre_state_reference, post_state_reference, beide Boards und Go-Kontrolle soweit geloggt, legality/terminal status |
| Information | belegbar sichtbare Promptteile / Historie / bekannte Grenzen; Unbekanntes als unknown |
| Claim | claim_id, exakte Textspanne, Typ, Kondition, Horizont, Spezifität, Prüfbarkeit, Referenzzeit |
| Decision | rohe Ausgabe, normalisierte Ausgabe, Versuch, gültig/illegal/Formatfehler/API-Fehler, tatsächlich ausgeführter Zug |
| Next opponent | nächste beobachtete Aktion, reale Zustandsänderung, zeitliche Relation, angegebene Vorhersage |
| Feasibility | Anzahl legaler ANDY-Züge; defensive Alternativen; untersuchte Suchtiefe; Solver-/Engine-Version; vollständig vs partiell gesucht |
| Adaptation | explizit dokumentierte Planrevision / planbeibehaltend / nicht feststellbar; Grund nur soweit aus Daten belegbar |
| Outcome | Prognose bestätigt/widerlegt/unklar/nicht testbar; lokale und globale Konsequenz, Ressourceneinsatz |
| Evidence | Direktbeleg, abgeleitet, engine-validiert, annotiert, Gegenhypothese und Unsicherheit |

**Datenstatus streng trennen:** `logged`, `reconstructed`, `engine_verified`, `human_annotated`, `model_reviewed`, `unresolved`, `contradicted`. Mehrere Labels können für verschiedene Teilbehauptungen nötig sein.

## 4. Drei zentrale Forschungsdimensionen

### A. Antizipation
- **Nenner:** explizite, vorab fixierte, hinreichend konkrete Vorhersagen; vage Aussagen getrennt.
- **Zähler:** im angegebenen Zeithorizont eintretende Vorhersagen – einschließlich konditionaler Aussagen nur bei eingetretener Bedingung.
- **Nicht zählen als Erfolg:** nachträgliche Textinterpretation oder allgemeine Überlegenheit, bloß weil ein Matt später eintrat.
- **Ausgaben:** Claim-Timeline, Treffer / Nicht-Treffer / unentscheidbar, Horizont, Konfidenz nur wenn ausdrücklich geäußert.

### B. Adaptive Reaktion
- Vorangegangene Vorhersage/Strategie und unerwartete Gegnersituation **zeitlich verknüpfen**.
- „Adaptiv“ nicht mit „Zug wechselte“ verwechseln: Ein Wechsel kann erzwungen sein, ein Beibehalten kann korrekt sein.
- Klassifikation: `explicit_revision`, `consistent_continuation`, `observed_behavioral_change_without_claim`, `forced_response`, `unclear`.
- Qualitätsbeurteilung nur mit Regeln, legalen Alternativen und transparentem Bewertungsmaßstab. Nicht automatisch aus Sieg/Niederlage ableiten.

### C. Handlungsspielraum / Rechtzeitigkeit
- **Zentrale neue Trennung:** `threat_present` ≠ `threat_visible_to_actor` ≠ `threat_recognized_in_text` ≠ `preventable_under_rules`.
- Ereignisfenster bestimmen: erstmalige *objektiv* belegbare Bedrohung; erste belegte **Äußerung** ihrer Erkennung; **letzte untersuchte Gelegenheit** für legale Abwehr; tatsächliche Reaktion.
- „Letzte Gelegenheit“ nur bei ausreichend vollständiger Alternativensuche unter **vollständigen ANDY-Regeln**, nicht allein nach Schachregeln.
- **Kein** Schluss „nicht adaptiv“ aus erzwungener Mattfolge nach Verlust des Handlungsspielraums.

## 5. Wiederverwendbare Episodenkarte (Mindestprodukt pro Fall)

**Episode ID:** MATCH-ID + Start-/End-Event  
**Forschungsfrage:** Was wurde erwartet, was war sichtbar, was war noch möglich?  
**Vorherzustand:** Chess FEN, Go-Zustand, Spielphase, Informationskontext  
**Claims:** Wortlaut, Event-ID, Kondition/Horizont  
**Gegneraktion:** wirklich ausgeführter Zug und Zustandswirkung  
**Handlungsraum:** legale ANDY-Alternativen, geprüfte taktische Antworten, Search-/Proof-Grenze  
**Reaktion:** Modelltext, versuchte & ausgeführte Aktion, Planrevision  
**Ergebnis:** lokal/global, zeitlich, Ressourcen, Matchende  
**Bewertung:** confirmed / refuted / undecidable / method-limited  
**Gegenhypothesen:** mindestens eine plausible Alternative und notwendiger Test  
**Grafik:** vor/nach-Bretter + markierte Events + Verweise auf JSONL/Code

## 6. Beispiel-Fallfenster: Astra vs Claude Opus 5.5

**Match:** `andy_64c8f95436d1`; Quellen: Original-JSONL und historisches ANDY-Ruleset/Engine nötig. Bereits vorhandene Referenz: Lab-Memo, externer Claude-Review.

- **#139:** dokumentierte frühere Angriffsidee.
- **#141:** Claude `c5d3`; im externen Review als möglich vermeidbarer Fehler bezeichnet.
- **#143:** Astra `c1c8` plus konkrete Prognose `f6e8` / `c8e8` matt.
- **#145:** Claude `f6e8` und Gefahrentext.
- **#146:** Claude GO `a10`, lokale Go-Kontrolländerung.
- **#147:** Astra `c8e8`; protokolliertes Matchende Matt.

**Wichtig:** Externer Review behauptet 20 legale Schachzüge bei #141 und 17 Optionen, die Matt in zwei vermeiden – **nur reine Schachregeln, ohne ANDY-Go-Kopplung** und ohne vorliegenden ausführbaren Suchnachweis. Das ist eine **zu prüfende Hypothese**, kein Befund. Ebenso muss „erzwungene Antwort“ bei #143/#145 getrennt validiert werden.

**Arbeitsfragen:** Wann wäre eine mögliche Schachgefahr im tatsächlichen Prompt sichtbar gewesen? Welche wirklichen ANDY-legalen Abwehrmöglichkeiten gab es vor #141, #143 und #145? War #146 (Go) im Kontext der alternierenden/gekoppelten Regeln freie Wahl oder zeitlich/regeltechnisch bestimmt? Nicht annehmen, dass ein lokal vorteilhafter Go-Zug die globale Schachlage unmittelbar verschlechterte.

## 7. Vergleich mehrerer Partien: Design, bevor man aggregiert

**Reihenfolge:** 1 vollständiges Individual Match → zweites Match mit identischem Schema → Inter-Annotator-/Engine-Prüfung → harmonisierte Fallvergleichsmatrix → erklärende Hypothesen → erst dann mögliche Kennzahlen/übergreifende Working-Paper-Thesen.

Für jede Partie dieselbe **Grundgesamtheit** an Ereignissen und Claims, identische Auswahlregel für Episoden und gleiches Validierungsschema. Kennzahlen nur mit gleichen Definitionen, Voraussetzungen und Konfidenz/Unsicherheit.

**Stratifizierung:** Modell/Version, Provider/API, Gegner, Farbe, Ruleset/Engine, Prompts, Budgets, Reasoning-Setting, Outputlimit, Retrys, First-Move, Chess-/Go-Phase, Matchlänge. Wenige nicht äquivalente Fälle dürfen **Fallkontraste** ergeben, keine generelle Rangfolge.

**Cross-match-Outputs:**
- Muster-Heatmap (Antizipationsart × Phase × Gegner × Modell), nur mit dokumentierten Nennern.
- „Opportunity windows“: Bedrohung sichtbar → Handlungsalternativen offen → Reaktionszeit → Endzustand; zunächst qualitativ.
- Abstimmungsmaß zwischen Annotatoren; Fälle mit Dissens öffentlich ausweisen.
- Fallbasierte Gegenhypothesen und gezielte Experimente für nächste Partien (Farbtausch, Prompt-/Limit-Kontrollen, mehr Wiederholungen).
- In-context-Anpassungen nur als beobachtete Episoden; **kein Nachweis persistenten Lernens**.

## 8. Experimentelle Working-Paper-Thesen (alle vorläufig)

**WP-H1 – Anticipation–Action Gap:** Zutreffende explizite Bedrohungserkennung garantiert nicht, dass eine rechtzeitige legale Gegenmaßnahme gewählt wird. *Prüfung:* diskrete Ereignisketten mit noch offenen Alternativen; Fälle mit erzwungener Reaktion ausschließen.

**WP-H2 – Local vs Global Objective Conflict:** Lokaler Zugewinn auf Go kann zeitlich mit globaler Schach-Niederlage zusammenfallen, ohne sie notwendig zu verursachen. *Prüfung:* kontrollierte Brett-/Regelrekonstruktionen und Alternativen.

**WP-H3 – Execution Reliability as Mediator:** Format-/Legalitätsfehler und Retry-Regeln beeinflussen die realisierte Folge von Entscheidungen unabhängig von ihrer sprachlichen Planqualität. *Prüfung:* rohe Ausgaben, Parser, Retry-/Budgeteffekte, ausgeführte Züge; Gegenmodelle.

**WP-H4 – Resource–Adaptation Relationship:** Unterschiedliche Token-/Zeit-/Outputbudget-Regime können die beobachtete Spezifität von Claims und Reaktionen beeinflussen. *Prüfung:* kontrollierte Settings, Provider-Unterschiede ausweisen.

**WP-H5 – Order–Complexity Feedback (Meta-ANDY):** Mehr parallele Mensch-KI-Workstreams erhöhen Koordinationsanforderungen; neue Governance kann Fehler reduzieren und neue Schnittstellenkosten schaffen. *Prüfung:* separate Prozessdaten, kein Schluss aus Einzelanekdoten.

**Wichtig:** Diese Sätze sind Forschungs-Hypothesen, keine Ergebnisse oder validierte kausale Wirkungen.

## 9. Methodische Risiken / Review-Gates

- Vollständige Spielregeln, echte Prompt-Information und historische Engine-Version rekonstruieren; keine Schach-only-Analyse als volle ANDY-Validierung ausgeben.
- Claim-Extraction nach vorab definiertem Codebuch; Treffer-/Fehlerfälle systematisch, nicht Sieger-zentriert auswählen.
- Textbeschreibungen und Outcome nicht zirkulär gegeneinander validieren.
- Keine Schlussfolgerungen über internes Denken, Bewusstsein, allgemeine Spielstärke oder stabilen Lernfortschritt.
- Alle empirischen Zahlen mit Match-, Event-, Datensatz-/Codeversion und Prüfstatus belegen.
- WPS-Governance und Fach-/Publikationsfreigabe **vor** öffentlichem Working Paper prüfen.
- Neuheit gegenüber bestehender Literatur erst nach Recherche zur Kombination der Methoden beanspruchen.

## 10. Umsetzungsgates und nächste konkrete Lieferung

| Gate | Ergebnis | Kriterium |
|---|---|---|
| **G0** | Rohdaten- und Engine-Inventur | Match-Dateien, Hashes, Promptfelder, Regeln, Versionsbezüge |
| **G1** | Ereignisparser + Codebuch | deterministische Ereignis-/Fehler- und Claim-Kodierung |
| **G2** | Vollständige Individual-Durchsicht | alle Events, alle auswertbaren Claims, keine Erfolgs-Selektion |
| **G3** | Engine-/Alternativen-Validierung | zentrale Episoden, besonders #141–#147, reproduzierbar geprüft |
| **G4** | Individual Research Edition Preview | 20–24-seitiges PDF mit echten Brettzuständen, Evidence-Cards und Limitations |
| **G5** | Zweites Match / Inter-Annotator-Abgleich | gleiche Methodik, Abweichungen dokumentiert |
| **G6** | Comparative Research Edition | 24 Seiten nach bereits fixiertem Blueprint, harmonisierte Daten |
| **G7** | Experimentelle WPS-These | Null-/Alternativhypothese, Studiendesign, Grenzen, fachlicher Review |

**Nächster operativer Schritt:** Die Astra–Claude-JSONL und Version der tatsächlichen ANDY-Engine prüfen, dann über **alle 147 Entscheidungsereignisse** Claims und Reaktionen kodieren. Dazu mindestens drei Episoden aus unterschiedlichen Matchphasen wählen, nicht nur die Mattsequenz. Parallel eine methodisch ehrliche **Individual-PDF-Preview** aus diesen Daten erzeugen.

---

**Leitfrage:** *Did the model see it coming — and could it still do something about it?*
