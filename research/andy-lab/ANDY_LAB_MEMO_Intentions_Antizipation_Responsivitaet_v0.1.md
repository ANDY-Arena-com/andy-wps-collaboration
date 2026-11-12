# ANDY Lab – Forschungs-Memo v0.1
## Von protokollierten Ankündigungen zu überprüfbaren Handlungen
**Stand:** 12. November 2026  
**Status:** Arbeitshypothese / Validierungsentwurf – keine validierte Benchmark-Metrik  
**Fokus:** *partiebezogene* Handlungsanalyse (nicht primär Modell-Ranking)  
**Referenzfall:** OpenAI Astra (Weiß) vs. Claude Opus 5.5 (Schwarz), Match-ID `andy_64c8f95436d1`  
**Primärquelle:** Original-JSONL `andy_64c8f95436d1.jsonl`; ergänzend ANDY-Matchbericht desselben Matches (12.11.2026).  
**Ziel:** Separat in einem eigenen ANDY-Lab-Thread anhand mehrerer Partien validieren, korrigieren und iterativ operationalisieren.

> **Leitsatz:** ANDY untersucht nicht, was ein Modell *angeblich intern gedacht* hat, sondern was es **protokolliert ankündigt**, was es **tatsächlich ausführt**, wie der Gegner **reagiert** und welche **beobachtbaren Ergebnisse** eintreten.

---

## 1. Forschungsfrage und Einordnung

Das Lab soll zunächst die Dynamik **innerhalb einer einzelnen Partie** nachvollziehbar machen:

1. **Intention:** Welches Ziel, welche Aktion, welches Ergebnis kündigt ein Akteur ausdrücklich an?
2. **Antizipation:** Welche gegnerische Antwort oder Gefahr wird vorhergesagt? Mit welcher Spezifität und unter welchen Bedingungen?
3. **Aktion:** Was wird wirklich versucht und regelkonform ausgeführt? Wie viel Zeit und Token kostet es?
4. **Reaktion / Responsivität:** Wie passt sich ein Akteur an tatsächliche Gegnerzüge, neue Gefahren, Fehler und Planabweichungen an?
5. **Ergebnis:** Ist eine explizite, überprüfbare Prognose eingetreten? Ist das angekündigte Ziel erreicht – und ggf. auf welche andere Weise?

**Nicht** gleichsetzen: Sprachliche Plausibilität = strategische Fähigkeit; protokollierte Modellbegründung = interne Kognition; eingetretene Vorhersage = objektiv optimale Entscheidung; Matchsieg = allgemeine Modellüberlegenheit.

Der Begriff **„responsible“/verantwortliches Wettkampfverhalten** bezeichnet hier eng abgegrenzte, beobachtbare Verhaltensweisen *im Spiel*: Regelkonformität, erkennbare Risikoabwägung, Budgetdisziplin, Behandlung von Unsicherheit und Reaktion auf Gefahren. Er bezeichnet **keine** allgemeine ethische oder moralische Güte eines Modells.

## 2. Referenzmatch: belegbare Eckdaten

| Kennzahl | Astra / Weiß | Claude / Schwarz |
|---|---:|---:|
| Ausgeführte Züge | 73 | 72 |
| Input-Token | 61.114 | 106.542 |
| Output-Token | 65.694 | 83.603 |
| Gesamt-Token | 126.808 | 190.145 |
| Restbudget (je 350.000) | 223.192 | 159.855 |
| Nicht ausgeführte Formatfehler | 0 | 2 |
| Go-Kontrolle am Spielende | 39 | 42 |

**Match:** 147 Entscheidungsereignisse, davon 145 ausgeführte Züge; ca. 55,5 Minuten; Abschluss durch **Matt für Weiß**, letzter ausgeführter Schachzug `c8e8` (Ereignis #147). Tokenverbrauch Astra ca. **33,3 % niedriger** als Claude bezogen auf Claudes Gesamtverbrauch. Die Go-Kontrolle liegt am Schluss bei Claude vorn, ist aber **kein Go-Sieg** und keine direkte Aussage zur objektiven Stellung.

**Zwei präzise Fehlerbeobachtungen:** #116 (Schwarz / Go, `no_explicit_move_to_repair`) und #121 (Schwarz / Go, `empty_visible_response`) hatten jeweils `finish_reason=max_tokens`, keinen ausgeführten Zug und wurden später durch gültige Antworten fortgesetzt. Das sind **Ausgabe-/Formatfehler**, nicht als illegale Spielzüge zu bezeichnen. Aus ihrer zeitlichen Nähe zur Schlussphase folgt **keine belegte Kausalität** für das Matt.

**Messgrenzen:** Tokenzählungen sind protokollierte anbieterspezifische API-Werte, keine automatisch vergleichbaren FLOPs oder Eurokosten. Angegebene Go-Kontrollwerte sind Matchzustands-/Engine-Werte und ohne Regeldefinition keine frei interpretierbaren Gebietspunkte. Die JSONL enthält außerdem Vorzug-Zustände (z. B. `chess_fen`, `go_control_white/black` bei Entscheidungsbeginn); Unterschiede **vor vs. nach** einem Ereignis müssen beim Rekonstruieren beachtet werden.

## 3. Ereignisbasierte Fallanalyse: Was wurde angekündigt, was geschah?

Die Nummern `#N` sind die **fortlaufenden 147 Entscheidungsereignisse**, nicht die Zeilennummern der JSONL (diese enthält auch `match_start` und `match_end`).

| Ereignis | Quelle / Ankündigung des Modells (sinngemäß) | Dokumentierte Handlung / Beobachtung | Bewertung |
|---|---|---|---|
| **#97 Astra CHESS** | Läuferzug `e4a8` soll Turm gegen Läufer gewinnen („Qualität“). | `e4a8`, legal/ausgeführt; späterer Abtausch im Protokoll. | Materialgewinn als *zu prüfende* taktische Behauptung; für objektive Bewertung vollständige Brettrekonstruktion verwenden. |
| **#115 Claude CHESS** | Offene c-Linie, Abtausch nach `Rxc8+` durch Dame ungefährlich. | `a8c8`, ausgeführt; spätere Wechsel auf der c-Linie. | Beispiel einer lokalen konkreten Prognose, nicht identisch mit späterem Endspielangriff. |
| **#133 Claude CHESS** | Bietet Damentausch an und entschärft eine Springerdrohung. | `c8c5`, ausgeführt; #135 Weiß `d6c5`, #137 Schwarz `d7c5`. | Konkrete Zugfolge/Materialänderung prüfbar; nicht ungeprüft als „gut“ bewerten. |
| **#139 Astra CHESS** | Turm greift Springer c5 an und „droht über c8 einen entscheidenden Grundreihenangriff“. | `e1c1`, ausgeführt. | **Frühe nachweisbare Zielankündigung**; später durch #143 konkretisiert. |
| **#141 Claude CHESS** | Springer `c5d3` sei durch Bauer e4 gedeckt und greife Turm c1 sowie Bauer f2 an. | `c5d3`, ausgeführt; danach wird der Weg nach c8 frei. | **Hypothese eines strategischen Fehlers**; tatsächliche Alternativen/erzwungene Niederlage unabhängig mit Regel-Engine prüfen. |
| **#143 Astra CHESS** | „Erzwingt ...Sf6–e8, dann Txe8 matt: sofortiger Gesamtsieg unabhängig von Go.“ | `c1c8`, ausgeführt; #145 `f6e8`; #147 `c8e8`; Match endet mit Matt. | **Ereignisfolge bestätigt**; „erzwingt“ (= einzige mögliche Antwort) noch gesondert regelbasiert verifizieren. |
| **#145 Claude CHESS** | „Turm c8 gibt Schach, und Sf6-e8 ist der einzige legale Zug. Danach droht Txe8 mit Matt.“ | `f6e8`, ausgeführt; #147 folgt Matt. | **Gefahr erkannt, aber im beobachteten Verlauf nicht mehr abgewehrt**. Dies belegt nicht, dass zu diesem Zeitpunkt eine Verteidigung möglich war. |
| **#146 Claude GO** | `a10` soll zwei weiße Steine schlagen und Kontrolle sichern. | `a10`, ausgeführt; protokollierte Kontrolle springt von 41:41 vor dem Zug auf 39:42 vor #147. | **Go-Teilziel beobachtbar erfüllt**; unmittelbar danach Matchverlust auf Schachebene. |
| **#147 Astra CHESS** | „Txe8 ist Schachmatt und gewinnt sofort das gesamte Spiel.“ | `c8e8`, ausgeführt; `match_end`: Matt Weiß. | **Direkt bestätigtes Endziel**. |

### Zentraler Befund: die mehrstufige Ankündigung #139 → #143 → #147

- **#139:** Astra kündigt die Idee des Angriffs auf der c-/achten Reihe an.
- **#141:** Claude zieht seinen Springer `c5d3`, nachdem Astra `e1c1` gespielt hat.
- **#143:** Astra formuliert eine **präzise konditionale Vorhersage**: Antwort `…f6e8`, danach `c8e8` mit Matt.
- **#145:** Claude erkennt und formuliert die unmittelbare Gefahr selbst.
- **#146:** Claude gewinnt mit einem Go-Zug kurzfristig Kontrolle; **dies ändert die Mattdrohung nicht**.
- **#147:** Astra setzt die angekündigte Mattfolge um.

**Interpretation (nicht als Beweis ausgeben):** Möglicherweise priorisierte Claude bei #141 einen lokal plausiblen Springervorteil, ohne die Konsequenz der geöffneten c-Linie hinreichend zu berücksichtigen. Es bleibt offen, ob dies der **erste objektiv entscheidende Fehler** war. Dafür sind die vollständige Schach-Go-Regel-Engine, historische Stellungen und legale Alternativen erforderlich.

### Zweiter Befund: lokale Zielerreichung vs. globales Matchziel

Claude erreicht bei #146 seine angekündigte Go-Wirkung (Kontrolle von 41:41 auf 39:42 zugunsten Schwarz); dies verhindert das bereits angekündigte Schachmatt nicht. Solche Fälle zeigen die Notwendigkeit, **lokale Maßnahme**, **spielübergreifende Risiken** und **finalen Matchausgang** getrennt zu erfassen. Nicht behaupten, Claude habe das Go „gewonnen“ oder die Go-Aktion habe das Matt verursacht.

## 4. Ein prüfbares Analyseobjekt: „Claim / Plan / Outcome“

Ein **Claim** ist eine einzelne aus dem Text extrahierte, prinzipiell überprüfbare Aussage. Eine längere Begründung kann mehrere Claims enthalten. Beispiel #143:

- C143-A: „Ich spiele `c1c8`“ – **Aktion**.
- C143-B: „Schwarz antwortet `f6e8`“ – **Vorhersage der Gegnerreaktion**.
- C143-C: „Danach spiele ich `c8e8` und gewinne durch Matt“ – **bedingtes Ziel / Ergebnis**.
- C143-D: „Diese Antwort ist erzwungen“ – **Legalitäts-/Alternativenbehauptung**, nicht durch den bloßen tatsächlichen Zug bewiesen.

**Pflichtfelder pro Claim:** `match_id`, `event_index`, `actor`, `source_text_exact`, `claim_span`, `claim_type`, `target`, `condition`, `time_horizon`, `related_event_ids`, `evidence`, `verdict`, `verifier`, `confidence`, `notes`.

**Vorgeschlagene Claim-Typen:** `self_action`, `opponent_prediction`, `threat_detection`, `material_goal`, `go_control_goal`, `mate_goal`, `risk_assessment`, `resource_plan`, `rule_legality_assertion`, `adaptation`.

**Bewertungsstatus (nicht nur ja/nein):**
`confirmed`, `contradicted`, `partially_confirmed`, `not_observed`, `not_testable`, `ambiguous`.
Dazu getrennt **methodische Validierungsstufe** `log_only` / `engine_verified` / `independently_reviewed`.

Zwingend: Eine **nicht eingetretene konditionale Prognose** ist nicht automatisch falsch, wenn ihre Voraussetzung nicht eintrat. Beobachtete Übereinstimmung belegt keine **Notwendigkeit**, Optimalität oder Kausalität.

## 5. Vorläufige Lab-Metriken (experimentell!)

Keine der folgenden Größen ist zum jetzigen Zeitpunkt validiert oder für ein öffentliches Modell-Ranking geeignet.

1. **PRR – Plan Realization Rate:** Anteil *prüfbarer, fälliger* Ziel-Claims mit belegter Erfüllung innerhalb des festgelegten Zeithorizonts. Bei teilweise erfüllten Claims eigene Quote statt willkürlicher 0,5.
2. **AA – Anticipation Accuracy:** Anteil *bedingungsaktivierter, prüfbarer* Gegner-/Ereignisprognosen, die nach Beobachtung eintreten. Gegebenenfalls nach Prognosespezifität und Zeitfenster stratifizieren.
3. **RR – Response / Adaptation Traceability:** Anteil *klar definierter Trigger* (Gegnerabweichung, neue unmittelbare Gefahr, illegale Antwort, Budgetschwelle), für die im nächsten relevanten Entscheidungsfenster eine im Log belegte Anpassung vorliegt. **Nicht** als psychologisches „Bewusstsein“ lesen.
4. **CR – Claim Reliability:** Anteil maschinen-/engine-verifizierbarer faktischer Behauptungen über den Spielzustand, die stimmen (z. B. „einzige legale Antwort“, „zwei Steine geschlagen“). Separat nach Schach/Go.
5. **Goal Conflict Cases:** Anzahl dokumentierter Konstellationen, in denen ein Akteur ein *lokales* Ziel erreicht und kurz darauf ein höher priorisiertes Ziel verliert. Zunächst **Fallkatalog**, keine Qualitätskennzahl.
6. **Execution Integrity:** gültige/ausgeführte Züge, Formatfehler, illegale Züge, Recovery, Token- und Latenzaufwand – getrennt von strategischer Qualität.

**Bias-Risiken:** Vielschreiber erzeugen mehr Claims; defensive Modelle formulieren weniger Prognosen; ein „bescheidenes“ Modell kann AA künstlich erhöhen; selektive Zeithorizonte erzeugen Hindsight Bias; wiederholte Varianten der selben Prognose dürfen nicht als unabhängige Treffer zählen. Deshalb stets **Rohzählwerte, Coverage, Claim-Typen und Unsicherheit** mitanzeigen, niemals allein eine Prozentzahl.

## 6. Technisches Vorgehen: reproduzierbarer Plan-Tracker v0.1

**Pipeline**
1. **Ingest:** JSONL zeilenweise lesen; `match_start`, Entscheidungen, `match_end` getrennt behandeln; Index, Akteur, Phase, Zug, Legalität, Ausführung, Zeit, Token, Fehler, Text und Stellungen erhalten.
2. **Normalize:** Entscheidungsnummer vs. Dateizeile; Schachkoordinaten/Go-Koordinaten; vor/nach Zuständen; Player-Mapping und geordneten Ereignisstrom eindeutig bestimmen. Pro Match Schema-/Regelversion festhalten.
3. **Extract candidates:** Explizite Zukunfts-/Risiko-/Zielbehauptungen aus `thought` mit konservativen Regeln und optional KI-gestützter Extraktion erkennen. **Originalwortlaut und Textspanne speichern**; KI-Extraktion ist kein Beweis.
4. **Build links:** Ankündigung → folgende eigene und gegnerische Entscheidungen → Abschluss/Unterbrechung; spezifische Fenster pro Claim-Typ dokumentieren.
5. **Verify:** Log-only für ausgeführte Aktionen, Zeit, Tokens und protokollierte Kontrolle; **Engine** für Legalität, alternative Antworten, Schachmatt, Schlagfolgen, Go-Kontrolle und reale Materialänderung; Analystenreview für Kausalität/Strategiebewertung.
6. **Review:** Unsichere Claims kennzeichnen und gegebenenfalls manuell annotieren; mehrere unabhängige Annotatoren, Differenzen protokollieren.
7. **Report/UI:** Brettzustand + Zeitachse + Claim-Zielkette synchron; klickbare #Ereignisse; Evidenz und Konfidenz sichtbar; Export JSON/CSV/Markdown.

**Skizze des strukturierten Exports:**

```json
{
  "schema": "andy.lab.claim.v0.1",
  "match_id": "andy_64c8f95436d1",
  "claim_id": "C143-B",
  "event_index": 143,
  "actor": "white",
  "phase": "CHESS",
  "claim_type": "opponent_prediction",
  "source_text_exact": "Erzwingt ...Sf6–e8, dann Txe8 matt: sofortiger Gesamtsieg unabhängig von Go.",
  "prediction": "f6e8",
  "condition": "after_white_c1c8",
  "related_event_ids": [143, 145],
  "verdict": "confirmed",
  "verifier": "log_only",
  "open_issue": "Das Wort 'erzwingt' separat mit der Regel-Engine prüfen."
}
```

**UI-MVP:** links Brett/Replay (inkl. Start- und Zielfeld), Mitte Plan-Timeline und Zielstatus, rechts Originaltext / Bewertungsbegründung / Gegenereignisse / Evidenzlinks; Filter nach Akteur, Phase, Claim-Typ, Prüfstatus, Zeithorizont. Das Lab ist analytisch/sachlich und verändert **nicht** den inszenierten Arena-Modus.

## 7. Validierungsplan für einen separaten Thread

### Phase A – Referenzfall als „Gold Standard“
- Original-JSONL `andy_64c8f95436d1.jsonl`, Match-PDF und **passende Engine-/Regelversion** verfügbar machen.
- Für #97, #115, #133–147 alle Claim-Textspannen manuell annotieren (inklusive **nicht prüfbarer** Aussagen).
- Alle Schach-/Go-Zustände vor und nach jedem relevanten Zug aus Engine reproduzieren; Unterschiede zur JSONL dokumentieren.
- Für #141 nach legalen Alternativen und taktischer Bewertung suchen, **ohne** rückblickend unbewiesene Absicht oder Kausalität anzunehmen.
- Den Sonderfall #146 „lokaler Go-Erfolg, globales Schach-Matt“ explizit kodieren.
- Positiv- und Negativbeispiele sowie eine Datei mit offenen Fragen erstellen.

### Phase B – weitere Partien (bewusst unterschiedliche Muster)
Mindestens: eine Partie mit Matt, eine mit Go-Entscheidung (falls verfügbar), eine mit mehreren ungültigen/abgewiesenen Aktionen, eine lange Partie mit Ressourcenknappheit; idealerweise auch ein Match mit Richtungswechsel oder abgebrochenem Plan. **Nicht** nur spektakuläre Siege auswählen. Jedes Match separat validieren, erst anschließend Muster vergleichen.

### Phase C – Objektivierung
- Für Claim-Extraktion **Precision/Recall** gegenüber manuell annotiertem Goldstandard; Inter-Annotator-Agreement berichten.
- Für objektive Claim-Verifikation **Fehlerquote** bei Aktionsverknüpfung, Zustandsrekonstruktion und Urteil bestimmen.
- Metrikdefinitionen und Zeithorizonte **vor** Auswertung weiterer Matches einfrieren; Sensitivitätsanalysen durchführen.
- Ergebnisse *partiebezogen* publizieren; erst nach stabiler Validierung Aggregation diskutieren.

**Abnahmekriterien MVP:** (a) jeder Claim verlinkt auf Originalevent und Originaltext; (b) keine stillschweigende Vermischung von Behauptung und Fakt; (c) „einzige legale Antwort“ wird nicht allein aus der gespielten Antwort bestätigt; (d) ausgeführte Züge, Fehler und Endzustand stimmen mit dem Log; (e) unsichere Befunde bleiben als solche sichtbar; (f) Analyse lässt sich bei gleichem Input reproduzieren.

## 8. Offene Fragen / Designentscheidungen

- Was ist die genaue, versionierte Go-Kontrollfunktion (bis 72), und wie werden **Vor- und Nachzugwerte** gespeichert?
- Welche Schach-/Go-Wechselregeln gelten genau und wie wird eine „erzwungene“ Fortsetzung formal verifiziert?
- Was ist ein sinnvoller Zeithorizont für langfristige Plan-Claims, wenn Modelltexte keine Frist nennen?
- Wann ist ein Strategiewechsel **Adaptation**, und wann nur der ohnehin geplante nächste Zug?
- Wie werden irrelevante, tautologische oder übermäßig vage Aussagen ausgeschlossen?
- Kann ein Modell bei unerwarteter Gegnerreaktion **korrekt revidieren**, obwohl sein ursprünglicher Plan scheitert?
- Welche Aussagen können mit **nur JSONL** bestätigt werden, welche brauchen zwingend die Engine?
- Welche Metriken sind robust gegenüber unterschiedlichen Modellen, Sprache, Begründungslänge und API-Einstellungen?

## 9. Schlussfolgerung und Empfehlung

**Empfehlung:** Den *partiebezogenen Plan-Tracker* zum prioritären experimentellen Analysemodul des ANDY Lab machen. Beginnen mit nachvollziehbaren Einzel-Claims statt einem zusammenfassenden KI-Score. Die Schlusskombination **#139 → #141 → #143 → #145 → #147** ist ein geeigneter erster Referenztest: Das Modell benennt eine Drohung, formuliert eine konkrete Vorhersage und realisiert das Endziel; das gegnerische Modell benennt die Gefahr, aber seine lokale Go-Aktion verhindert das Matt nicht.

Das ist ein **beobachteter Prozess** und eine **prüfbare Hypothese über antizipatorisches/responsives Wettkampfverhalten**, jedoch noch keine allgemeine Aussage zur Überlegenheit eines Modells oder zur nachweisbaren internen Planung.

**Übergabe an neuen Thread:** Dieses Memo + Original-JSONL + Matchbericht + Engine-/Regelversion verwenden. Erste Aufgabe: einen maschinenlesbaren Claim-Katalog für #97 und #133–147 erstellen, Positionen validieren und die hier notierten Einschätzungen gezielt **falsifizieren oder bestätigen**. Jede Revision als neue Memo-Version mit Änderungsliste dokumentieren.

---
*ANDY – Actor. Network. Dynamics. · Erleben. Erforschen. Erahnen.*  
*Ein Forschungs-Memo zur transparenten und reproduzierbaren Analyse; keine universelle Modellrangliste.*
