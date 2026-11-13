# ANDY Lab – Forschungsideen-Sammlung: Symmetrien, Modellkontexte und TKO trotz/wegen Vorsprung

**Stand:** 13.11.2026 · **Status:** Sammlung / **nicht priorisiert**, keine Validierung als empirische Forschungsbefunde  
**Zweck:** Jüngste Beobachtungen und daraus entwickelte Ideen ohne vorzeitige Gewichtung bewahren. Spätere Triage entscheidet über Priorität, Machbarkeit, Kontrollversuche, Code und Working Papers.

**Anschlussdokumente:**
- [ANDY Lab 2.0 Research Architecture](ANDY_LAB_2_0_RESEARCH_ARCHITECTURE_v1.0.md)
- [Series Explorer / Opening & Pattern Atlas](ANDY_SERIES_EXPLORER_OPENING_PATTERN_ATLAS_BLUEPRINT_v1.0.md)
- [Bestehender Rückkampf-Hypothesenpool inkl. SSA und INF](METHODIK/ANDY_REMATCH_HYPOTHESENPOOL_UND_EXPERIMENTDESIGN_v0.1.md)
- [Match-Eligibility-Policy](METHODIK/ANDY_LAB_2_0_MATCH_ELIGIBILITY_AND_COHORT_POLICY_v0.1.md)

## A. Beobachtungen aus den gezeigten Arena-Bildern

**Status sämtlicher Punkte:** subjektive Sichtbeobachtungen anhand einiger Screenshots, **nicht** aus JSONL-Kohorten oder Engine-geprüften Vergleichsdaten abgeleitet.

1. **Frühe Go-Symmetrie:** In verschiedenen Spielen fallen offenbar ähnliche erste Go-Setzungen auf, teils bis ungefähr 16–20 Go-Aktionen. Gezeigt wurden u. a. Gemini-Selbstpartien und weitere Paarungen; die Projektleitung berichtet auch solche Eindrücke bei Claude.
2. **Unterschiedliche Symmetrieformen:** Diagonale Spiegelung, Achsenspiegelung, farbgetauschte 180°-Rotation, lokale geometrische Ähnlichkeit, parallel laufende Randketten und farbkomplementäre Raumaufteilungen werden visuell vermutet. Nicht jede regelmäßige Struktur ist mathematisch eine Spiegelung.
3. **Musterübergänge:** Früh sichtbare globale Symmetrien könnten im weiteren Spiel in lokale Ketten, komplementäre Randbesetzung und andere Strukturen übergehen; ebenso möglich sind frühzeitige Divergenz oder spätere Wiederannäherung.
4. **Frühe Schachstruktur:** Auch Schachfiguren/Materielage/Bauernstruktur können ähnliche Entwicklungsstände zeigen, selbst wenn die konkreten Züge verschieden sind. Gleiche Restfiguren beweisen weder identische Taktik noch gleiches Eröffnungsverhalten.
5. **Go–Chess-Relation:** Go-Steine konzentrieren sich auf einigen Bildern eher in Randregionen, Schachfiguren häufiger innen; ein regelbedingter oder verhaltensbedingter räumlicher Zusammenhang ist offen.
6. **Provider-/API-Kontext:** Die Projektleitung vermutet Spiegelzug-Häufung bei gemeinsamem API-Key, beobachtete später ähnliche Muster auch in anderen Konstellationen. **Dies ist noch kein Gegenbeleg oder Nachweis** eines Key-, Modellfamilien- oder Geometrieeffekts: Es fehlt die systematische Messung und vollständige Zuordnung zu den tatsächlichen Zugangskonfigurationen.

## B. Bereits definierte und neue Hypothesenkandidaten

### B1 – Opening & Symmetry (vor allem im bestehenden Atlas und Pool)

| Themen-ID | Arbeitshypothese / Forschungsfrage | Trennbare Gegenhypothesen |
|---|---|---|
| **PAT-S1** | Die ersten 5/10/16/20 ausgeführten Go-Setzungen zeigen über verschiedene Matches/Serien eine wiederkehrende Symmetriestruktur. | Go-Setup-Regeln und legale Startfelder erzwingen/begünstigen diese Muster; selektive Bildauswahl. |
| **PAT-S2** | **Zeitlich reaktive Spiegelantworten** treten häufiger auf als bei angemessener zustandsbedingter Nullverteilung. | Nur statische Symmetrie, keine zeitliche Spiegelreaktion. |
| **PAT-S3** | Globale Symmetrie geht mit zunehmender Aktionenzahl in lokale/komplementäre Strukturähnlichkeit über. | Keine konsistente Richtung; reine Verdichtung/Phase erklärt den Eindruck. |
| **PAT-S4** | Frühe Chess-Zugfolgen oder Positionsmerkmale bilden wiederkehrende Familien. | Ausgangsstellung und erzwungene/naheliegende Entwicklung verursachen Ähnlichkeit. |
| **PAT-S5** | Go-Setup-Familien und Chess-Opening-Familien treten nicht unabhängig voneinander auf. | Gemeinsame Regeln, Farbe oder anderer Konfigurationsfaktor erklären Zusammenhang. |
| **PAT-S6** | Pattern-Familien sind über mehrere unabhängige Serien/Provider hinweg auffindbar. | Ungleiche/selektive Matchauswahl und Konfigurationen erzeugen Scheinkonstanz. |

**Keine Doppelzählung:** PAT-S1–S6 sind hier **Themenmarker**, keine sechs zusätzlich registrierten unabhängigen Hypothesentests. Die Grundlagen überlappen mit OP-H1–OP-H6 im Series-Explorer-Blueprint sowie INF-H1–INF-H4 im zentralen Hypothesenpool.

### B2 – Anbieter-, Modell- und Zugangskontext

Zentrale bereits registrierte Hypothesen: **INF-H1 (gleicher Key / Mirror Responses), INF-H2 (Projekt vs Key), INF-H3 (Modellfamilien/Heuristiken), INF-H4 (Regeln/Startposition als Nullmodell)**. Die neue Beobachtung „auch bei anderen Anbietern“ ist ein **Hinweis zur künftigen Stratifizierung**, kein Beleg für eine spezifische Ursache.

Zu prüfen: gleiche vs getrennte Keys im selben Projekt; getrennte Projekte; gleiche Modellfamilie vs andere Familie; gleicher vs anderer Provider; Prompt-, Budget- und Ruleset-Gleichheit. Keys niemals in Forschungskorpus speichern, nur pseudonymisierte Gruppenkennungen.

### B3 – „TKO trotz oder wegen Nase vorn?“ (neu gesammelte Kandidaten)

**Ausgangspunkt:** Das offizielle Regelresultat (`KO_CHESS`, `KO_GO`, `TKO_BUDGET`) ist **eine andere Dimension** als der im Moment der Terminierung erreichte Schach- und Go-Zustand. Erreichte Vorteile dürfen den TKO-Sieger nicht überschreiben; sie sind aber wissenschaftlich relevante Beobachtungen.

| Themen-ID | Arbeitshypothese / Forschungsfrage | Konkurrierende Erklärung |
|---|---|---|
| **ADV-H1 – TKO despite advantage** | Ein Akteur kann bei Go-Kontrolle oder Chess-Stellungsmerkmalen im Vorteil sein, aber vor regulärem KO sein Budget überschreiten. Wie häufig? | Hoher Vorteil ist ein momentaner Zwischenstand ohne verifizierte reale Gewinnwahrscheinlichkeit. |
| **ADV-H2 – TKO because of advantage** | Führt ein erkennbarer Vorsprung in bestimmten Situationen zu zusätzlichem Ressourceneinsatz, Sicherungszügen oder anhaltender Strategieinvestition und dadurch zu erhöhtem TKO-Risiko? | Lange Partiedauer/komplexe Stellung verursacht sowohl Vorsprung als auch Ressourcenverbrauch; kein kausaler Vorsprungseffekt. |
| **ADV-H3 – Resource escalation after lead** | Verändert sich der Tokenverbrauch je API-Entscheidung **nach** Erreichen definierter Vorteile stärker als davor? | Phase, spätere Promptlänge, Retrydichte, unvollständige Reasoning-Messung erklären den Anstieg. |
| **ADV-H4 – Advantage conversion** | Wie häufig wird ein dokumentierter Vorteil **vor** Budgetende in einen regulären Sieg umgesetzt? | Position oder Zeitfenster war objektiv noch nicht gewinnentscheidend; keine durch Regeln/Engine belegte Gewinnchance. |
| **ADV-H5 – Budget awareness while ahead** | Erkennt das Modell in protokollierten Aussagen, dass die verbleibenden Tokens für seinen verfolgten Siegweg knapp werden, und reagiert es? | Fehlt der Budgetstand im Prompt, kann ihm fehlendes Bewusstsein nicht als Modellfehler angelastet werden. |
| **ADV-H6 – Defensive endurance / opponent TKO** | Geht systematische Abwehr des regulären KO mit der späteren Budgeterschöpfung eines bereits führenden Gegners einher? | Gegner verliert durch Ressourcenaufwand unabhängig von absichtlicher Abwehrstrategie. |

**Keine vorzeitige Aufnahme als sechs bestätigte oder unabhängige Befunde.** Die Themen überschneiden sich u. a. mit Ressourcen-H9–H12, Adaptivität und SSA-H4/H5; erst nach Operationalisierung und Triage eigenständig registrieren.

## C. Konkrete dokumentierte Fallbeispiele (nur Screenshot-/Gesprächsbasis)

### Fall C1 – Astra (Weiß) vs Gemini 4 Argon (Schwarz), historischer Budget-TKO

In der gezeigten Replay-Endstellung:
- Go-Kontrolle laut UI: **Weiß 66, Schwarz 47**.
- Budget: **Astra 150.584 / 150.000**, **Argon 82.450 / 150.000** Tokens.
- UI-Endgrund: **Budgetüberschreitung Astra**, Schwarz gewinnt per TKO; **160 ausgeführte Züge**, **171 KI-Aufrufe** im Screenshot.
- Das Modell hatte als geplante Aktion u. a. eine Sicherung des Turms und Vorbereitung gegen einen gefährlichen Bauern protokolliert; letzte Aktion offenbar **nicht ausgeführt**.
- **Offene Match-ID-Zuordnung:** Im Screenshot nicht vollständig sichtbar. Keinem vorhandenen Datenbankmatch ohne Abgleich zuordnen.

**Forschungsfrage:** Wie häufig gewinnt ein Akteur Teilspiel-Kontrolle, verliert aber wegen Ressourcenüberschreitung? Ist die Ressourceneskalation durch den Vorteil bedingt oder bloß korreliert?

### Fall C2 – Gemini 4 Argon vs Gemini 3.8 Flash, Rückkampfserie

- Original `andy_1c77f49b3e17`: Serienansicht zeigt Go-KO zugunsten Argon mit Schwelle 72; ursprünglicher Raw-Log-Status ohne terminales `match_end` zuvor offen. **Zugrundeliegende Engine-Rekonstruktion prüfen**.
- Rückkampf `andy_b94759f1b232`: Argon (Weiß) verbraucht **100.275 / 100.000** Tokens; Flash (Schwarz) **78.945**; Go-Kontrolle **48:47**, TKO Argon.
- Weiterer gezeigter Rückkampf: Flash (Weiß) **97.970 / 100.000**, Argon (Schwarz) **100.544 / 100.000**; Go **51:48**, Argon TKO nach **198 ausgeführten Zügen**. **Match-ID noch nicht belegt.**

**Forschungsfrage:** Sind bestimmte Opening-Muster mit späterer Ressourcenerschöpfung und einer ausbleibenden Umwandlung eines Go-Vorsprungs assoziiert? Nicht Ursache aus diesen drei Fällen ableiten.

## D. Was der Offline-Batch-Scanner später messen sollte

### D1 – Frühe Patterns (vor allem Go-Setup)
- Zeitfenster **erste 5/10/16/20 tatsächlich ausgeführte Go-Aktionen**, getrennt vom reinen Go-Setup, von globalen API-Aufrufen und vom Go-Index pro Akteur.
- Occupancy-Matrix (13×13), Farben, Zugreihenfolge; Haupt-/Gegendiagonalspiegelung, vertikale/horizontale Spiegelung und **180°-Rotation**, jeweils **gleiche vs vertauschte Farben**.
- Statische Symmetrie vs unmittelbar/nach 1–3 eigenen Go-Zügen tatsächlich erfolgende Spiegelantwort trennen; nur damals legale Antworten in Nenner.
- Kettenlängen, Nachbarschaft, Randdistanz, lokale Strukturähnlichkeit und Komplementarität.
- Eigene Symmetriescores **mit Nullmodell** aus regelkonformen Vergleichssetzungen; keine 0-Imputation fehlender Stände.

### D2 – Chess / Go–Chess
- Frisch rekonstruierte Chess-Stellungen bei 5/10/20/30 ausgeführten Chess-Aktionen; Schachmaterial, Bauernstruktur, Figurentwicklung, Königszustand.
- Go-Setup-Muster mit späterem Chess-Fingerprint aus derselben Partie verknüpfen; konfundierende Regeln, Farbe, Gegner und Setup-Prompt kontrollieren.
- Verlauf von globaler zu lokaler Symmetrie phasenbezogen; Matching und Divergenz getrennt.

### D3 – Ressourcen und „Nase vorn“
- Zeitreihen: Go-Vorsprung je Akteur, Abstand zur Go-KO-Schwelle, Chess-Material/Stellungsmerkmale **ohne sie automatisch in Siegchance umzudeuten**, kumulierte und pro-Call-Token, Input/Output/Reasoning-Verfügbarkeit, verbleibender Budgetanteil, Retry-/Fehlerphase.
- **Advantage-at-termination** getrennt nach Go und Chess, Terminierungsgrund und Verifikationsstatus.
- **Lead onset → subsequent tokens → KO/TKO** als Ereignisfolge mit Kontrollgruppen und Phasenkorrektur, nicht nur Endwerte.
- **Conversion Rate** mit vordefiniertem Vorteilsschwellwert und Nenner; keine heuristische Chess-„Gewinnwahrscheinlichkeit“ als gesicherte Tatsache.
- Wenn Budgetinformation im Modellprompt fehlt: `budget_visibility=unknown/none`; keine Behauptung über bewusstes Ignorieren.

### D4 – Auswertung/Kohorten
- Match-/Seriencluster und Konfigurationen harmonisieren, Farbtausch korrekt normalisieren.
- Original-JSONL unverändert; Event-/Match-IDs, Sourcehash, Ruleset, Provider-/Adapterversion, Fehl-/Unbekanntwerte, Censoring und Prüfstatus ausweisen.
- Exploration im historischen Korpus von späteren vorregistrierten Bestätigungsserien trennen.
- Auch bei TKO **Teilspielzustand als Forschungsdaten erhalten**; Outcome-Sieg nicht umwerten.

## E. Denkbare Visualisierungen (noch keine Prioritätsentscheidung)

| Ansicht | Zweck |
|---|---|
| Symmetry × Window Heatmap | Wann, bei welchen Serien und unter welcher Transformation erscheinen frühe Patterns? |
| Opening-Fingerprint-Atlas | Go-Setz-/Chess-Stellungsprofile je Match und Serie |
| Cross-Series Similarity Matrix | Welche Opening-Familien wiederholen sich über Paarungen/Provider hinweg? |
| Pattern Transition Timeline | Global symmetrisch → lokal komplementär → divergierend? |
| Go Lead × Token Budget (doppelte Zeitreihe) | Wächst der Ressourceneinsatz nach dokumentiertem Vorteil? |
| Advantage-at-Termination Scatter | Go-Vorsprung gegen Restbudget, Symbolfarbe/Typ für KO/TKO/TECH |
| Advantage Conversion / Censoring | Erreichen regulärer Siegbedingung nach vordefiniertem Vorsprung versus Ressourcenende |
| Material Depletion × Go Progress | Schach-Figurenabbau und Go-Entwicklung, ohne Ursache vorwegzunehmen |

## F. Arbeitsprinzip: sammeln jetzt, später priorisieren

**Jetzt:** Hypothesenkandidaten und negative Fälle sammeln, Quellen sichern, IDs und Querverweise pflegen. Keine Pflicht, sämtliche Vorschläge bereits zu programmieren oder einen Prioritätsrang zu vergeben.

**Später (bewusster Priorisierungsschritt):**
1. Welche Fragen sind mit vorhandenem JSONL und Engine tatsächlich operationalisierbar?
2. Welche Muster haben eine ausreichend große, vergleichbare Match-/Serienstichprobe?
3. Welche Hypothesen sind trennscharf gegenüber Alternativerklärungen?
4. Welche Messungen sind bei geringen Offline-Kosten automatisierbar?
5. Welche Beobachtungen eignen sich für eine prospektive Serie oder Working Paper?

**Leitmotiv:** *Erleben → Erforschen → Erahnen → erneut prüfen.* Das Erahnen produziert ausdrücklich **falsifizierbare Ideen**, keine fertigen Forschungsergebnisse.


## G. Ergänzung 13.11.2026 – Opponent-induced Behavioral Conformity / mögliche sycophancy-artige Imitation

**Beobachtung / Anstoß:** Wiederkehrende, visuell vermutete Spiegelzüge in ANDY führten zu der Frage, ob die Nachahmung gegnerischer Setzungen auf einer aus dialogischen KI-Kontexten übertragenen Anpassungstendenz beruhen könnte: *„Ich mache/imitierte das, was dem Gegenüber zu gefallen scheint“* – obwohl das Gegenüber im Spiel ein Konkurrent ist.

**Begriffsgrenze:** Klassische **Sycophancy** beschreibt übermäßige Anpassung an Erwartungen, Meinungen oder Präferenzen eines Nutzers/Gegenübers. Die räumliche Imitation eines gegnerischen Go-Zuges ist **allein kein Nachweis für Sycophancy**. Als neutrale Forschungskategorie zunächst **behavioral conformity / opponent-induced imitation** verwenden; „sycophancy-artig“ bleibt eine mögliche, gesondert prüfbare Mechanismushypothese.

### Neue, vorläufige Themenhypothesen

| ID | Forschungsfrage / Hypothesenkandidat | Alternativerklärungen |
|---|---|---|
| **SOC-H1 – Opponent-Induced Behavioral Conformity** | Übernehmen GPAI-Modelle in kompetitiven ANDY-Situationen gegnerische Go-Setzmuster über das durch Regeln, Geometrie und Stellung Erklärbare hinaus – auch ohne erkennbaren strategischen Mehrwert? | Strategisch sinnvolle symmetrische Antwort, legale Feldverteilung, räumliche Standardheuristiken, gemeinsame Prompts |
| **SOC-H2 – Maladaptive Mirroring** | Steigt die Spiegelantwort-Häufigkeit auch dann, wenn der gespiegelte Zug regel-/enginegeprüft gegenüber legalen Alternativen objektiv nachteilig ist? | Stellung falsch bewertet, zufällige Fehlentscheidung, fehlende zugängliche Information |
| **SOC-H3 – Social-Alignment Transfer** | Werden Musterübernahmen durch Hinweise auf die Absichten oder Erwartungen des Gegners bzw. durch explizite Anti-Imitations-Anweisungen verändert? | Priming-/Prompt-Effekt ohne sozialen Mechanismus, veränderte Entscheidungsinformation oder Token-Nutzung |

**Status:** Neu gesammelte Hypothesenkandidaten, **nicht priorisiert, nicht validiert**, kein Beleg für Motiv, inneren Denkprozess oder tatsächlich übertragene Sycophancy. Sie ergänzen den Themen-Backlog; **keine automatische Erhöhung der Zahl formell präregistrierter Hypothesen** im zentralen Pool.

### Denkbares Prüfdesign (für spätere Priorisierung)

1. **Deskriptiv zuerst:** Mit dem Offline Pattern Detector tatsächliche zeitliche Spiegelantworten (Haupt-/Gegendiagonale, 180°-Rotation, exakte und lokale Spiegelung) in den ersten definierten Go-Aktionen aus Original-JSONL rekonstruieren. Statische Brettsymmetrie nicht als Reaktion zählen.
2. **Nullmodell:** Verfügbarkeit legaler Spiegelpositionen, ANDY-Setup-/Regelzwänge, Farbe, Zugfolge, Stellung und Gegnerkontext kontrollieren; zufalls-/permutationsbasierte Baselines nur als Forschungsinstrument.
3. **Maladaptive Alternative:** Nur mit vollständiger ANDY-Regel-/Engineprüfung und begründeter Bewertungsmethode feststellen, ob eine spiegelnde Aktion gegenüber Alternativen nachteilig war. Eine einzelne verlorene Partie beweist dies nicht.
4. **Kontrollierte Kontexte:** Möglichst gleichwertige Entscheidungssituationen mit/ohne erkennbares gegnerisches Muster sowie gegebenenfalls mit/ohne kritische Anti-Imitations-Instruktion vergleichen; unterschiedliche Prompts als explizite Intervention behandeln. Nicht zwei tatsächlich verschiedene Brettpositionen als identische Lage ausgeben.
5. **Evidenztrennung:** `observed_mirror`, `evaluated_action_quality`, `documented_model_claim`, `mechanism_hypothesis`; keine aus Modelläußerungen oder Geometrie abgeleiteten sicheren Aussagen über verborgene interne Gründe.
6. **Serienvergleich:** Wiederholungen/Farbtausch, Modell-/Provider-/API-Projekt-Konfiguration und Matchcluster berücksichtigen; Entdeckungsdaten später nicht als unabhängigen Bestätigungstest behandeln.

**Anschluss:** Geometrische OP-/PAT-Hypothesen, **INF-H1–INF-H4** zum API-/Anbieterkontext, **SSA** (Bewertung/Antizipation), **Adaptivität** und der [Opening & Pattern Atlas](ANDY_SERIES_EXPLORER_OPENING_PATTERN_ATLAS_BLUEPRINT_v1.0.md).

**Sammlungsregel bleibt gültig:** Beobachtungen und mögliche Erklärungen aufnehmen – **jetzt nicht priorisieren oder implementieren**. Die spätere Entscheidung über Code, Experimentserien und Working Paper erfolgt separat.


## H. Extern berichteter Pilotbefund: reaktive Go-Spiegelantworten (13.11.2026)

Die **explorative Claude-Auswertung an drei Match-Logs** (u. a. Astra 6/7 im Setup, Argon 8/54 im Hauptspiel und eine viergliedrige gleichartige Spiegelserie #20/#24/#28/#32) einschließlich der methodischen Einschränkungen und weiterer Prüfideen ist im eigenen [Memo zu unmittelbaren Go-Spiegelantworten](METHODIK/ANDY_GO_MIRROR_RESPONSE_EXPLORATORY_CLAUDE_MEMO_2026-11-13.md) dokumentiert. Die berichteten p-Werte sind **nicht von uns reproduziert**; die Stichprobe ist explorativ, kein belastbarer Signifikanznachweis. Noch keine Priorisierung.
