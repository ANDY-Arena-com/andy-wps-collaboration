# ANDY Series Explorer & Opening/Pattern Atlas – Gesamtkonzept v1.0

**Stand:** 13. November 2026  
**Status:** Konzeption und priorisiertes Umsetzungsbriefing; **noch keine realisierte oder mit Original-JSONL validierte Pattern-Analyse**  
**Adressaten:** Thread 1 (ANDY_APP), ANDY_LAB, Research/Working Papers, Designer  
**Prinzip:** Offline zuerst, deterministische und überprüfbare Grafiken zuerst, Semantik/Interpretation später.  
**Zentraler Bezug:** [ANDY Lab 2.0 – Research Architecture](ANDY_LAB_2_0_RESEARCH_ARCHITECTURE_v1.0.md) · [Event-to-Evidence Method](METHODIK/ANDY_EVENT_TO_EVIDENCE_METHOD_v0.1.md) · [Hypothesenpool](METHODIK/ANDY_REMATCH_HYPOTHESENPOOL_UND_EXPERIMENTDESIGN_v0.1.md) · [SSA](METHODIK/ANDY_STRATEGIC_SITUATIONAL_AWARENESS_SSA_v0.1.md) · [Match Eligibility](METHODIK/ANDY_LAB_2_0_MATCH_ELIGIBILITY_AND_COHORT_POLICY_v0.1.md)

---

## 1. Zielsetzung und Produktentscheidung

**ANDY Series Explorer** ist ein lokal/offline nutzbares Forschungswerkzeug zur grafischen Analyse und zum Vergleich **mehrerer Matches innerhalb einer experimentellen Rückkampfserie und zwischen verschiedenen Serien**. Dabei steht nicht das einzelne Game, das einzelne Modell, ein Benchmark oder eine Rangliste im Zentrum, sondern die **Wiederkehr, Stabilität, Abweichung und Entwicklung empirischer Muster**.

Der **ANDY Opening & Pattern Atlas** ist die methodisch priorisierte Komponente des Series Explorer: Vergleich der **ersten relevanten Go-Setzentscheidungen**, der **frühen Schachentwicklung** sowie der **Relation zwischen Go-Setup und Schachauftakt**. Bewusst **nicht** zwangsläufig die ganze Partie analysieren: Spätere Züge können stark divergieren, während Eröffnungen eine vergleichbarere Ausgangsbasis bieten.

**Leitfrage:** *Welche strukturellen und zeitlichen Muster wiederholen sich in den ersten relevanten Entscheidungen einer Partie – innerhalb und über verschiedene Rückkampfserien hinweg? Wie verändern sich diese Muster bei Farbtausch und Konfigurationsvariation?*

Das Werkzeug ist eine **sekundäre Analyseinfrastruktur** von ANDY Lab 2.0. Seine Erkenntnisse speisen später die primären Forschungsfragen, nicht umgekehrt.

### Abgrenzung
- Kein weiteres Replay-Frontend und keine KI-Spielstärke-Rangliste.
- Keine Abhängigkeit von Live-APIs oder zusätzlichem KI-Tokenverbrauch im grafischen MVP.
- Keine automatische Gleichsetzung von geometrischer Ähnlichkeit und strategischer Intention.
- Keine nachträgliche Änderung der Original-JSONL oder historischer Ergebnisse.
- Semantische Aussagen und Working-Paper-Thesen entstehen **erst** nach expliziter, prüfbarer Evidenzkodierung.

---

## 2. Ausgangslage / neue Serienstruktur

Die Arena/Replays verwalten jetzt Ursprungsmatches mit nachfolgenden Rückkämpfen unter einer gemeinsamen Serienzuordnung; eine Ansicht „Serien / Kandidaten / Alle Matches“ ist vorhanden. Die neue Serienstruktur soll direkt als Dateneingang für den Explorer dienen.

Beispiel aus aktueller Serienansicht (vom Projektleiter angezeigt):

| Serie | Match | Weiß | Schwarz | Status in Ansicht |
|---|---|---|---|---|
| `andy_1c77f49b3e17` | Original `andy_1c77f49b3e17` | Gemini 3.8 Flash | Gemini 4 Argon | Anzeige: Schwarz gewinnt durch Go-Kontrolle 72 ≥ 72; ursprüngliches JSONL ohne `match_end`, Validierung/Quelle der Serienanzeige prüfen |
| `andy_1c77f49b3e17` | Runde 1 `andy_b94759f1b232` | Gemini 4 Argon | Gemini 3.8 Flash | `budget_overshoot`; TKO-Verursacherprüfung laut Serienansicht noch offen |
| `andy_64c8f95436d1` | Original `andy_64c8f95436d1` | OpenAI Astra | Claude Opus 5.5 | Schachmatt Weiß |
| `andy_64c8f95436d1` | Runde 1 `andy_740a81fdbcc9` | Claude Opus 5.5 | OpenAI Astra | `user_stopped` |

**Wissenschaftliche Konsequenz:** UI-/Leaderboard-Terminalanzeigen, tatsächlicher Raw-Log-Status und rekonstruierte Engine-Ergebnisse getrennt führen. Abgebrochene oder TKO-Partien können trotz fehlenden regulären KO-Verlaufs für bestimmte Musteranalysen geeignet sein, sind aber **zensiert** für andere.

---

## 3. Kernkonzept: Zwei Vergleichsebenen, ein gemeinsames Datenmodell

### Ebene A – Intra-Series
- Alle Matches einer `rematch_group_id` oder rekonstruierbaren Ursprungs-/Folgekette gegenüberstellen.
- Gleiche Modellpaarung, Farbtausch, Wiederholungen und gezielte Konfigurationsvariation kenntlich machen.
- Wiederkehrende Opening Fingerprints, Varianten, Abweichungen und den Zeitpunkt der Auseinanderentwicklung bestimmen.
- Für ein Matchpaar „Warum ähnlich/anders?“ zunächst **deskriptiv** anhand der tatsächlich gemessenen Merkmale erklären.

### Ebene B – Cross-Series
- Serien-Fingerprints und ihre Streuung miteinander vergleichen.
- Wiederkehrende Go-Setup-Familien, Schacheröffnungsfamilien und **Go–Chess-Relationsfamilien** in unterschiedlichen Gegner-/Modell-/Budgetkonstellationen finden.
- Konfigurationen und Datenqualitätsklassen vor jedem Vergleich filtern. Muster über Serien hinweg nicht mit unabhängigen Experimenten verwechseln, wenn Serien sich überschneiden oder dieselben Matches enthalten.

**Ein Match-Fingerprint** beschreibt ein einzelnes frühes Spielsegment. **Ein Serien-Fingerprint** beschreibt Verteilung, häufige Varianten und Streuung der Match-Fingerprints in derselben Serie. Cross-Series-Musterfamilien entstehen erst aus verglichenen Serien-Fingerprints oder aus kontrollierten matchübergreifenden Analysen.

---

## 4. Priorität im Analysefenster: Die ersten relevanten Entscheidungen

**Fenster flexibel definieren; Zahlen sind Forschungsparameter, nicht stillschweigend angenommene Fakten.**

### Go Setup
- Erste **5 / 10 / 15 / 20** ausgeführte Go-Setzentscheidungen als einstellbare Fenster.
- Ergänzend exakt die regeltechnisch definierte **Go-Setup-Phase** separat auswerten, damit „20 Go-Aktionen“ nicht mit „20 globalen API-Entscheidungen“ oder „20 Zügen pro Akteur“ verwechselt wird.
- Beide Perspektiven: **set-order** (Reihenfolge), **set-position** (geometrische Anordnung), **post-window board** (Zustand nach definiertem Fenster).
- Immer festhalten: globale Event-ID, Go-Aktion-Index, Akteur, Farbe, Phase, fehlgeschlagener vs ausgeführter Zug. Fehlversuche dürfen das geometrische Fenster nicht unbemerkt verschieben.

### Frühe Schachentwicklung
- Erste **5 / 10 / 20 / 30** tatsächlich ausgeführte Schachaktionen als definierbares Fenster; nach Bedarf zusätzlich Halbzüge/volle Züge unterscheiden.
- Identische Zugfolgen und ähnliche Stellungsmerkmale **getrennt** untersuchen.
- Aus den wirklichen ANDY-Brettzuständen: Zentrumskontrolle, Bauernstruktur, Figurenentwicklung, Königssicherheit, Schachbedrohungen, Bewegungsräume – nur soweit mit dem gültigen Regelsystem nachprüfbar.
- Nicht unbesehen klassische Schach-Eröffnungsnamen als korrekte strategische Interpretation eines gekoppelten 13×13-ANDY-Spiels ausgeben.

### Go–Schach-Relationen (ANDY-spezifische Kernfrage)
- Go-Setup-Fingerprint **mit** nachfolgendem Chess-Opening-Fingerprint pro Match verknüpfen.
- Prüfen: Welche frühen Go-Knoten/Regionen gehen häufig mit welchen frühen Schachentwicklungen und Einschränkungen einher?
- Getrennt untersuchen: räumliche Nähe/Überlappung, regelmechanische Abhängigkeit, zeitliche Abfolge, Kontroll-/Bedrohungsänderungen, geometrische Kopplung.
- Keine Ursache aus einer Korrelation ableiten: gemeinsame Anfangsbedingungen, Farbe, Regeln, Modell-/Prompt und Gegner können beide Teilmuster beeinflussen.

### Divergenz untersuchen statt voraussetzen
- Die Vermutung lautet: Frühe Entscheidungen sind ähnlicher, danach nimmt die Streuung zu.
- **Messfrage:** Wie verändert sich Musterähnlichkeit bei Fenstern 5,10,15,20,30 ...? Zeitpunkt/Phase signifikanter Divergenz **erst nach gewählter Definition und Messung** markieren.
- Die tatsächliche Streuung kann je Phase und Konfiguration auch stabil bleiben oder zwischenzeitlich wieder konvergieren.
- Darum Eröffnungsorientierung als **Priorität**, nicht als Dogma „späte Züge immer wertlos“.

---

## 5. Grafische Ansichten – vom ersten Vorschlag bis zum Pattern Atlas

| Ansicht | Inhalt | Zweck | Umsetzung |
|---|---|---|---|
| **A – Overlaid Match Curves** | Go-Kontrolle, Tokenverbrauch, Fehlerverlauf, ggf. Schach-Merkmale mehrerer Matches | Gemeinsamkeiten/Unterschiede im Verlauf | MVP |
| **B – Match Fingerprint Grid** | Small Multiples: Go, Tokens, Chess-Entwicklung, Fehler, Terminierung pro Match | Viele Partien mit einheitlichem Maßstab scannen | MVP+ |
| **C – Series Heatmap** | Zeilen=Matches, Spalten=Phasen oder Fenster; Farbwert=Go-Differenz, Ressourcen, Fehler oder definierter Merkmalwert | Serienmuster und Ausreißer | MVP+ |
| **D – Resources × Progress** | Scatter: Tokens oder Calls gegen Go-Kontrolle/Schachereignisse; KO/TKO/Abort als Symbole | Engpässe und zensierte Enden sichtbar machen | später |
| **E – Event Timeline** | API-/Chess-/Go-/Retry-/KO-Ereignisse in Zeitordnung | Nachvollziehbare Phasenübergänge, Drill-down | MVP+ |
| **F – Opening Atlas / Go Setup Map** | 13×13-Overlay der frühen Go-Setzungen, Belegungsfrequenz, Zugordnungs-Varianten | räumliche Selbstähnlichkeit | **MVP-Kern** |
| **G – Chess Opening Atlas** | Frühe Figuren-/Bauernstruktur, Positionsmerkmale und Eröffnungsvarianten | strukturelle Chess-Selbstähnlichkeit | **MVP-Kern** |
| **H – Go–Chess Relation View** | Gemeinsame Merkmale und Übergänge von Setup zur Schacheröffnung | gekoppelten Spieleffekt sichtbar machen | MVP+ |
| **I – Match Similarity Matrix** | NxN paarweise Ähnlichkeit, auswählbar Go/Chess/Relation/Event/Resource; Klick auf Paar | Ähnliche Paarungen entdecken | **MVP-Kern** |
| **J – Similarity / Divergence vs Window** | Ähnlichkeit im frühen Spiel bei Fenstern 5,10,15,20,30... und nach Phasen | Zeitpunkt der Konvergenz/Divergenz messen | **MVP-Kern** |
| **K – Cluster / Pattern Families** | Gruppen ähnlicher Match- und Serien-Fingerprints; Ausreißer sichtbar | Musterfamilien in großen Kohorten | später |
| **L – Cross-Series Pattern Atlas** | Matrix/Atlas von Serien-Fingerprints und Musterfamilien | generalisierbare Muster über Serien prüfen | nach Intra-Series-MVP |

**Design-Prinzip:** Nicht alle zwölf Ansichten gleichzeitig auf der Startseite. Eingang: Serie wählen → Fenster/Phase wählen → Opening Atlas + Similarity + Divergence; weitere Diagramme bei Bedarf öffnen. Gruppierung nach Forschungsfrage statt Benchmark-Dashboard.

### Wichtig: grafischer MVP
1. **Serienselector + Vergleichbarkeitsindikator**
2. **Go-Setup-Overlay** und **Schach-Opening-Merkmale** für frühe, konfigurierbare Fenster
3. **Paarweise Similarity Matrix** (mindestens ein transparent definiertes Go-Maß und ein Chess-Maß)
4. **Similarity-vs-Window-Kurve** (Divergenz)
5. **Überlagerte Go- und Token-Zeitreihen** als sekundäre Kontextvisualisierung
6. **Drill-down** Match → Event/Position/Originalquelle
7. **Export** PNG/SVG/CSV/JSON mit Metrik-/Regelversion, Settings und Datenstand

---

## 6. Definition von Ähnlichkeit: Nicht ein magischer Prozentwert

Eine Ähnlichkeitszahl ist **nur** sinnvoll mit benannten Eingabemerkmalen, definierten Normalisierungen, tolerierten Transformationen und Grenzen. Kein ungeprüfter Gesamtscore, der „strategische Intelligenz“ suggeriert.

### A – Go-Setup-Ähnlichkeit
1. **Exakte Übereinstimmung** der Go-Zugfolge innerhalb eines Fensters (und längster gemeinsamer Präfix).
2. **Occupancy/Intersection-over-Union (Jaccard)** für besetzte Go-Knoten pro Seite, aus definierter Akteursperspektive; Reihenfolge bewusst nicht berücksichtigt.
3. **Spatial overlap / distance**: frequente Regionen, Steinabstände, Rand-/Zentrumskonzentration, Symmetrie, Cluster, frühe Nachbarschaft.
4. **Zeitpunkt der Setzung**: gleiches Muster an anderer Stelle im Zugfenster getrennt kennzeichnen.
5. **Transformationen** (Spiegelung/Rotation/Farbtausch): jeweils explizite Vergleichsvariante, nicht unbemerkt mischen; Regeln/Chess-Überlagerung können symmetrische Go-Transformationen verbieten oder ihre Interpretation ändern.

### B – Schach-Opening-Ähnlichkeit
1. **Exakte Folge** der Schachaktionen oder längster gemeinsamer Präfix.
2. **Positionsmerkmale** nach festen Fenstern: Schachfiguren/Bauernverteilung, Zentrum, König, Entwicklung, kontrollierte Felder.
3. **Strukturabstand** zwischen Merkmalvektoren (mit benannter Gewichtung); exakte Chess-FEN-Zustände nur wenn sinnvoll und historisch tatsächlich rekonstruierbar.
4. **Transpositionen**: gleiche/ähnliche Position trotz anderer Zugreihenfolge erkennen, ohne aufgrund klassischer 8×8-Eröffnungsdatenbanken falsche Ableitungen zu machen.

### C – Relationsmuster
1. Kombinierte Go- und Chess-Merkmale innerhalb derselben Match-Phase bzw. ausdrücklich definiertem zeitlichen Übergang.
2. **Conditional pattern counts**: Wie häufig tritt Chess-Muster B bei Go-Muster A auf – verglichen mit geeigneten Kontrollgruppen?
3. Räumliche Überlappung und potenziell regelmechanische Interaktion getrennt ausweisen.
4. Keine automatische kausale Behauptung, solange alternative Erklärungen nicht geprüft sind.

### D – Zeit-/Ereignis-Muster
1. Sequenzabstand für Go/Chess/Retry/Bedrohungs-Ereignistypen.
2. **Dynamic Time Warping (DTW)** für vergleichbare kontinuierliche Verläufe (Go-Kontrolle, Ressourcen) unterschiedlicher Dauer; nicht blind über regeltechnische Phasengrenzen warpen.
3. Im MVP zuerst Merkmale einzeln/nebeneinander; später gewichteter Composite **nur** nach expliziter Forschungsentscheidung.

### E – Clustering und serienspezifische Fingerprints
- Clustering erst, wenn mehrere unabhängige, ausreichend vergleichbare Matches vorliegen; kleine Serien visuell paarweise betrachten.
- Clusterrobustheit prüfen (andere Fenster, Merkmalsgewichte, Match-Ausschluss, Farb-Transformationen).
- **Serien-Fingerprint** = typische Go-/Chess-/Relationsmuster **plus Streuung**, n Matches, n unabhängige Wiederholungen, Gegenbeispiele, Konfigurationsklasse; nicht nur Mittelwert.
- Serienübergreifend über Gruppen vergleichen; kein globales „Model X hat 94 % Ähnlichkeit“ ohne definierte Methode.

---

## 7. Wissenschaftlich korrekte Ausrichtung und Normalisierung

**Drei verschiedene X-Achsen nicht verwechseln:**
1. globale API-Entscheidungsnummer (inkl. fehlgeschlagener Aufrufe);
2. ausgeführte Aktion eines Typs (Go-Setzung, Schachaktion; mit Akteurzuordnung);
3. normierter Matchfortschritt in % (nur ergänzend; kann frühe KOs mit langen TKOs täuschend ähnlich machen).

**Model-oriented statt color-oriented:** Nach Farbtausch Argon-Sicht als Argon-Sicht vergleichen, aber Rohfarbe zusätzlich speichern. Separat „Weiß-/Schwarz-orientiert“ anbieten. Rotationen/Spiegelungen müssen mit gekoppelten Chess/Go-Regeln vereinbar und als solche ausgewiesen sein.

**Konfigurationen:** Identisch / kontrollierte Variation / ähnlich / nicht direkt vergleichbar. Check: modellspezifische Konfiguration beim Farbtausch, Prompt-/Reasoning-/Output-/Retrylimits, Budget, Ruleset/Engine, Provider/Modellversion und Startzustand.

**Fehlendes vs null:** Nicht dokumentierte Go-Kontrolle ist `unknown`, niemals Null. Nicht bestätigter KO_GO bleibt offen; UI-/Engine-Rekonstruktion mit Nachweis in getrennter abgeleiteter Tabelle. Keine erfundenen Thinking-Tokens.

**Selektionsregeln:** Für eine 20-Go-Aktionen-Analyse nur Matches mit hinreichend vielen beobachteten ausgeführten Go-Setzungen; kürzere Matches als zensiert/getrennte Kohorte statt stillschweigend aus Nenner entfernen. Abort/TKO für Eröffnungsstruktur oft **trotzdem brauchbar**, wenn das frühe Fenster vollständig beobachtet wurde. Historische Testmatches gemäß Eligibility-Policy filtern.

**Abhängigkeiten:** 100 API-Entscheidungen derselben Partie sind nicht 100 unabhängige Experimente. Farbgetauschte Rückkämpfe paaren; Matchserie als Cluster; bei Cross-Series echte Unabhängigkeit prüfen.

---

## 8. Datenfluss und vorgeschlagenes Exportformat

```text
Original-JSONL / lokale ANDY DB / bestehende Serien-IDs
   ↓ Read-only Import + Hash/Version + Match-Endstatus
Match- & Config-Registry + parent_match_id / rematch_group_id
   ↓ Ereignisnormalisierung inkl. GO_SETUP, CHESS, GO, errors/retries
Opening Windows (executed go 5/10/15/20; chess 5/10/20/30)
   ↓ rekonstruierte Boardstates + Fingerprint-Extraktion
Go-Fingerprints / Chess-Fingerprints / Relation-Fingerprints
   ↓ metrikspezifische Similarity-Matrix und Divergenz pro Fenster
Series Fingerprints / Cross-Series Pattern Families
   ↓ UI & Forschungsdatenexport
PNG · SVG · CSV · JSON + manifest + method/engine hashes
```

**Vorgeschlagene minimale Entitäten:** `series`, `match`, `config_snapshot`, `event`, `board_state`, `opening_window`, `fingerprint`, `similarity_edge`, `pattern_cluster`, `evidence_note`.

**Fingerprint-Beispiel (Schema-Entwurf, keine echten Daten):**
```json
{
  "match_id": "andy_example",
  "series_id": "andy_series_example",
  "ruleset_version": null,
  "actor_id": "model_id",
  "actor_color": "white",
  "window": {"phase": "GO_SETUP", "unit": "executed_go_actions", "end": 20},
  "features": {
    "go_set_positions": [],
    "go_occupancy_by_actor": {},
    "chess_opening_features": {},
    "go_chess_relations": {}
  },
  "completeness": "unknown",
  "fingerprint_version": "v0.1",
  "source_sha256": null
}
```

**No fictional data in real UI:** Frühere illustrative Similarity-Prozentwerte und Diagramme sind lediglich Entwürfe, keine berechneten ANDY-Ergebnisse.

---

## 9. Spätere semantische Ebene (ausdrücklich Phase 2)

Erst wenn die datengestützte geometrische/zeitliche Musterbasis stabil ist, den **Event-to-Evidence-** und **SSA-Claim-Analyzer** integrieren:
- Wann nennt ein Modell erstmals einen Go-/Chess-Siegweg?
- Welche eigenen/generischen Gegnergefahren werden zu welchem Zeitpunkt erkannt?
- Wird eine konkrete Antwort vorhergesagt und tritt sie tatsächlich ein?
- Ändert ein Modell seinen Plan und waren legale Alternativen vorhanden?
- Sind objektiv ähnliche Openings auch ähnlich begründet oder adaptiv behandelt?

**Semantisches Clustering nicht als unüberprüfte Tatsache anzeigen.** Claims vor Outcome kodieren; Textzitate mit Event-ID, Match-ID und Konfigurationssnapshot, gegen Engine geprüfte Zustände und Gegenhypothesen. Modelltext = protokollierte Äußerung, nicht innere Kognition.

**Langfristiger Forschungsanschluss:** H1–H4 strategische Zielwahl, H13 Wiederholbarkeit, SSA/Lageeinschätzung, H2 Adaptivität, H9 Budgetvariation und weitere Hypothesen aus dem [Pool](METHODIK/ANDY_REMATCH_HYPOTHESENPOOL_UND_EXPERIMENTDESIGN_v0.1.md).

---

## 10. Konkrete experimentelle Fragen aus dem Opening Atlas

**OP-H1 – Go Opening Recurrence:** Bei vergleichbaren Start-/Regel-/Budgetbedingungen treten bestimmte räumliche Go-Setup-Fingerprints innerhalb und über Serien wiederkehrend auf.

**OP-H2 – Chess Opening Recurrence:** Frühe Schachentwicklung bildet wiederkehrende Positions-/Zugfamilien, auch bei unterschiedlicher exakter Zugfolge.

**OP-H3 – Go–Chess Coupling:** Bestimmte Go-Setup-Strukturen sind mit bestimmten frühen Schachentwicklungen assoziiert, stärker als aufgrund der gemeinsam festgelegten Anfangsbedingungen zu erwarten.

**OP-H4 – Opening Divergence:** Ähnlichkeit früher Spielabschnitte nimmt ab einem datenabhängigen Fenster/Phasenwechsel ab; dies ist zu prüfen und nicht vorauszusetzen.

**OP-H5 – Color vs Actor Perspective:** Wie stark ändern sich Muster unter Farbtausch, nachdem Rollen- und Modellsicht korrekt harmonisiert wurden?

**OP-H6 – Cross-Series Generality:** Musterfamilien erscheinen auch über mehrere vergleichbare, voneinander unabhängige Serien hinweg und nicht nur in einem konkreten Matchpaar.

**Status:** Forschungsfragen/Hypothesen zur Registrierung, nicht validierte Beobachtungen. Vor neuen Serien Messgrößen, Transformationszulässigkeit, Fenster und Ausschlüsse fixieren; bestehende Serienexploration separat kennzeichnen.

---

## 11. Umsetzungspaket für Thread 1 (ANDY_APP)

### Phase 0 – Inventur und minimaler Datenvertrag (P0)
- Serienstruktur, gespeicherte `parent_match_id`/`rematch_group_id` und Matchindex im aktuellen Code prüfen.
- Vorhandene JSONL-Felder für Go-Setup, Chess-Aktionen, Positionen, Go-Kontrolle, Tokens, Fehler, Terminierung und Modelltexte inventarisieren.
- Ruleset und tatsächlich erlaubte Symmetrien/Transformationen nachsehen; Definition „erste Go-/Chess-Aktionen“ vor Implementierung fixieren.
- Fehlende/endstatusoffene Daten sauber markieren; keine historischen Logs manipulieren.
- Ein kleines maschinenlesbares `fingerprint_schema_v0.1` und Metrik-Codebuch erstellen.

### Phase 1 – Offline Opening-Pattern-MVP (P1, jetzt)
- Lokale Serienauswahl mit Match-/Konfigurationstabelle, Match-Eligibility und Farbzuordnung.
- Einstellbare Fenster 5/10/15/20 (Go) und 5/10/20/30 (Chess) plus komplette Go-Setup-Phase.
- 13×13-Setup-Overlay mit eigener/gegnerischer Besetzung und Häufigkeitsheatmap.
- Frühe Schachzüge/Positionsstrukturen, auch bei transponierten Zugfolgen.
- Paarweise Similarity-Matrix **Go und Chess separat**, mit echter berechneter Metrik, Nenner und Konfigurationsstatus.
- Similarity-/Divergence-by-Window-Kurve samt Zeit-/Phasenbezug.
- Klick auf Matchpaar: zwei frühe Brettzustände, Gemeinsamkeiten, Unterschiede, Event-/Match-IDs.
- Bestehende Go-/Tokenkurven als sekundäre, auswählbare Vergleichsansicht.
- Read-only, keine zusätzlichen LLM-API-Kosten, reproduzierbarer Export.

### Phase 2 – Relationen & erweiterte Grafiken (P2)
- Go–Chess-Relationen mit konkretem Kopplungsbezug; bedingte Häufigkeiten vs Vergleichs-/Nullgruppen.
- Match-Fingerprint-Grid, Serien-Heatmap, Ereignis-Timeline, Resource-vs-Progress.
- Serien-Fingerprints (Verteilungen/Streuung), erste Cross-Series-Vergleiche nach Konfigurationsklassen.
- Bei genügend Daten Clustering mit Sensitivitätsprüfungen.

### Phase 3 – Semantik und Forschungsreporting (P3, später)
- Event-to-Evidence + SSA-Claim-Annotation in denselben Visualisierungen.
- Erkenntnisstände/Working-Paper-Verknüpfung, Konfidenz/Unsicherheiten, Gegenhypothesen.
- Keine automatische Validierung aus LLM-Interpretationen; Engineprüfung und Provenienz notwendig.

### Abnahmekriterien
- [ ] Serien- und Folge-Matches werden korrekt zusammengeführt; Originale bleiben unverändert.
- [ ] Go-Setup-Phase vs erste N Go-Aktionen und frühe Chess-Aktionen sind sauber unterscheidbar.
- [ ] Gleiche Model-ID wird nach Farbtausch korrekt verfolgt; Farbe bleibt explizite Variable.
- [ ] Keine irrelevanten fehlgeschlagenen API-Versuche als ausgeführte Setzungen zählen.
- [ ] Go-/Chess-/Relationsähnlichkeit sind **separat definierte und anzeigbare** Maße.
- [ ] Opening-Fenster frei auswählbar; Phase/Einheit/Nenner sichtbar.
- [ ] Ähnlichkeitsmatrix und Divergenzkurve zeigen ausschließlich aus Logs errechnete Werte, keine Demo-Zahlen.
- [ ] Fehlende Daten/zu kurze Matches/eingeschränkte Vergleichbarkeit sind sichtbar; keine Null-Imputation.
- [ ] Visualisierungen haben Drill-down auf Match/Ereignisse und Export.
- [ ] Mehrere Serien mit gleichen Methoden cross-series vergleichbar; Unterschiede/Unsicherheiten dokumentiert.
- [ ] Keine Einschränkung der vorhandenen Lab-1.0-Analysefunktionen und Replays.

---

## 12. Kompakte Übergabe an Thread 1

> **ANDY Series Explorer & Opening/Pattern Atlas:** Baue ein lokal/offline laufendes, read-only Tool für die Analyse von Rückkampfserien. Kern ist **nicht** die komplette Matchdauer, sondern die ersten relevanten Go-Setzungen (etwa Fenster 5/10/15/20, Setup-Phase getrennt) und die frühen Schachaktionen (5/10/20/30). Vergleiche (1) Go-Raum-/Reihenfolgemuster, (2) Chess-Zugfolgen und Stellungsmerkmale, (3) Go–Chess-Relationsmuster. Zeige pro Serie Opening Fingerprints, echte paarweise Similarity-Matrix, Divergenz nach Fenstergröße und ergänzend überlagerte Go-/Tokenkurven. Danach vergleiche Pattern-Familien **zwischen** Serien unter harmonisierten Konfigurationen. Farbtausch modellspezifisch normalisieren, Rohdaten niemals ändern, unvollständige Enden markieren, alle Scores mit Metrik/Version/Quelle erklären. Erst später semantische Claims und KI-Interpretation hinzufügen. Bestehendes Lab und Replay bleiben erhalten.

**Leitsatz:** *Nicht nur wer gewinnt oder wie die Partie endet, sondern welche frühen Muster sich wiederholen, wo sie auseinanderlaufen und ob diese Muster über unterschiedliche Experimente hinweg Bestand haben.*


## Anhang – Fortlaufender, noch nicht priorisierter Themenspeicher (13.11.2026)

**Neue Beobachtungen und Hypothesenkandidaten zu frühen Go-/Schach-Symmetrien, Infrastrukturkontrollen und dem Verhältnis von strategischem Vorteil zu Ressourcen-TKO:** [ANDY Lab Forschungsideen-Sammlung – Symmetrie & „TKO trotz/wegen Nase vorn“](ANDY_LAB_FORSCHUNGSIDEEN_SAMMLUNG_SYMMETRIE_TKO_VORTEIL_v0.1.md).

Dieses Zusatzdokument ist ausdrücklich ein **Backlog ohne Priorisierung**. Es erweitert die Ideensammlung, nicht den Nachweisstand der bisherigen Hypothesen. Implementierung erst nach einer späteren fachlichen Triage.
