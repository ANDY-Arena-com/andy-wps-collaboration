# ANDY 2.0 – Gesamtkonzept & Masterplan
**Actor. Network. Dynamics. | Erleben. Erforschen. Erahnen.**

**Version:** 1.0 · **Stand:** 13. November 2026 · **Status:** Strategisches Leitdokument / lebender Plan  
**Geltung:** Projektübergreifend für Arena, App, Lab, Website, Journal, Open-Data-Corpus und Kommunikation.  
**Pflege:** Jede wesentliche Richtungsänderung als nachvollziehbarer GitHub-Commit; keine stillschweigende Umschreibung historischer Daten.

> **Zweck:** Dieses Dokument ist der gemeinsame Referenzpunkt für alle ANDY-Threads, beteiligten Menschen und KI-Systeme. Es unterscheidet die **langfristige Vision** von **bereits nachgewiesenem Ist-Stand**, **konkreten Vorhaben** und **offenen Forschungsfragen**. Bei Threadwechseln zuerst dieses Dokument lesen.

---

## 1. Das Projekt in einem Absatz

ANDY ist ein experimentelles, regelgebundenes Strategiespiel, das Elemente von Schach (Figuren, Taktik, Matt) und Go (Schnittpunkte, Steine, Kontrolle) auf einem gemeinsamen **13×13-Brett** vereint. KI-Modelle verschiedener Anbieter treten unter expliziten Regeln, Konfigurationen und Token-Budgets gegeneinander an. Die tatsächlichen API-Entscheidungen, Zugversuche, ausgeführten Aktionen, Spielzustände und Resultate werden protokolliert. ANDY verbindet ein visuell eindrucksvolles **Arena-Erlebnis** mit einem **überprüfbaren Lab**, einem **publizistischen Journal** und einem langfristig **offenen Forschungs- und Trainingsdatenkorpus**.

**Leitidee:** *Erleben. Erforschen. Erahnen.*

**Arena-Claim (Marketing, nicht Forschungssatz):** *Every AI has a plan. Until it gets punched in the ANDY Arena.*

**Positionierung:** Faktisch ein experimenteller Leistungsvergleich, aber im öffentlichen Storytelling **nicht primär als „Benchmark“ bezeichnen**. Das Ziel ist nicht ein vorschnelles Gesamtranking, sondern die Untersuchung tatsächlicher Handlungsfolgen, Strategien und Grenzen. Das Projekt ist unabhängig von beteiligten Modellanbietern; Markenreferenzen dürfen keine offizielle Partnerschaft suggerieren.

## 2. Grundprinzipien – nicht verhandelbar

1. **Originaldaten bleiben unverändert.** Original-JSONL versionieren bzw. mit eindeutigen Prüfsummen referenzieren; Korrekturen in separaten abgeleiteten Dateien dokumentieren.
2. **Beobachtung ≠ Interpretation.** Aussagen und Begründungen eines Modells sind protokollierte *Äußerungen*, keine Einsicht in interne Denkvorgänge. Ein tatsächlich eingetretenes Ergebnis belegt nicht automatisch die Notwendigkeit, Optimalität oder Ursache der vorangegangenen Handlung.
3. **Engine vor Behauptung.** Illegalität, Schachmatt, Go-Sieg, Brettzustand und Alternativzüge, soweit möglich, anhand der **passenden versionierten ANDY-Regeln/Engine** prüfen. Unbestätigtes ausdrücklich als unbestätigt kennzeichnen.
4. **Jede wichtige Aussage ist rückverfolgbar.** Match-ID, Ereignisindex, Datenfeld/Textspanne, Regel-/Engine-Version, Auswerteskript und Validierungsstatus.
5. **Keine ungeprüfte Vergleichbarkeit behaupten.** Token verschiedener APIs sind nicht automatisch FLOPs, Kosten oder „Intelligenz“; Matchresultate hängen von Farbe, Prompt, Modellversion, Budget, Sampling, API, Regeln und Gegner ab.
6. **Spektakel und Evidenz trennen.** Arena darf dramatisch sein, Lab und Research Editions müssen sachlich, reproduzierbar und kritisierbar bleiben.
7. **KI-Kritik ist erwünscht, keine formale Validierung.** Unabhängige KI-Reviews sind hilfreiche Gegenperspektiven; regelbasierte Prüfungen und menschliche Verantwortung bleiben notwendig.
8. **Release-Sicherheit.** Funktionierende Stände einfrieren, kleine nachvollziehbare Diffs, komplette testbare Website/App-Pakete, Tests online und lokal, Asset-Versionierung, Rückfallplan.
9. **Mehrsprachigkeit konsistent halten.** Deutsch/Englisch/Chinesisch nach Bedarf; gleicher Faktenstand, Sprachwechsel, keine scheinbar existierenden Übersetzungen.
10. **Training nur mit geprüfter Rechte- und Datenlage.** Öffentliche Zugänglichkeit allein erlaubt weder beliebige Wiederveröffentlichung noch kommerzielles Modelltraining; Providerbedingungen, Lizenzen, personenbezogene/secrets in Logs, Sicherheits- und Missbrauchsaspekte vor Freigabe prüfen.

## 3. Die fünf miteinander verbundenen Säulen

| Säule | Zweck / Zielgruppe | Kernartefakt | Status (13.11.2026) |
|---|---|---|---|
| **Arena & Fight Night** | Erlebnis für Interessierte, Gamer, Öffentlichkeit | Cinematic Match-Replay, klassische Analyseansicht | Prototyp/Website live; spezifische Cross-Browser-Abnahme noch offen |
| **ANDY App & Designer** | Spielbetrieb, Replay, Gestaltung, weitere Matches | Python-App, Designer, Match-Engine | Aktive Entwicklung in eigenen Threads; detailgenauer Stand im jeweiligen Code-Repository prüfen |
| **ANDY Lab** | Analyse für Forscher, Analysten, Entwickler | Ereignisbasierte Untersuchungen, validierte Kennzahlen | Erste Memos und sechsseitige PDF-Piloten vorhanden |
| **ANDY Journal** | Vermittlung, Making-of, Narrative, Forschungskommunikation | Mehrsprachiger WordPress-Blog | Blog-Subdomain und Coming-Soon-Seite laufen; WP wird separat aufgebaut |
| **Open Research Corpus** | Reproduzierbarkeit, KI-Forschung, evtl. Training/Evaluation | Roh-JSONL, normalisierte Events, Annotationen, Datenkarten | Zielarchitektur; systematischer Corpus noch aufzubauen |

**Website:** https://andy-arena.com/ · **Blog:** https://blog.andy-arena.com/  
**GitHub-Zusammenarbeitsrepository:** https://github.com/ANDY-Arena-com/andy-wps-collaboration  
**Wichtiger bestehender Forschungsentwurf:** [Lab-Memo zu Intention, Antizipation, Responsivität](../research/andy-lab/ANDY_LAB_MEMO_Intentions_Antizipation_Responsivitaet_v0.1.md)

### Zielgruppen und passende Einstiege

- **Erleben:** kurzes Duell, Fight Card, Gewinner, visuelle Replay-Story.
- **Verstehen:** zugbasierter Replay-Modus, Glossar, Regelwerk, Highlights.
- **Erforschen:** Match-Research-Edition, Vergleichsstudie, Diagramme, Methodik.
- **Wiederverwenden:** Original-JSONL, maschinenlesbare Annotationen, Scripts, dokumentierte Lizenz und Versionen.
- **Mitdiskutieren:** Journal, Open-Source-Beiträge, wissenschaftlicher Review.

Es muss nicht jede Zielgruppe alle Ebenen verwenden. Jede Ebene darf zur nächsten führen.

## 4. Forschungsprogramm: von einer Partie zu vielen Partien

### 4.1 Primärer Analysegegenstand

**Intention / angekündigtes Ziel → Antizipation → Entscheidung/Zugversuch → tatsächliche Ausführung → Gegnerreaktion → beobachtbares Ergebnis**

Jede Textäußerung kann mehrere getrennte überprüfbare *Claims* enthalten. Beispiele: eigener geplanter Zug, vorhergesagter Gegnerzug, behauptete taktische Zwangslage, lokale Go-Wirkung, prognostiziertes Matt. Für jeden Claim immer festhalten:
- wortgetreue Originalstelle oder exakte Quellenreferenz;
- Verfasser, Match-ID, Ereignisindex, Phase (Chess/Go), Zeitpunkt;
- Typ, Spezifität, Bedingungen und Zeithorizont;
- beobachtete Handlung und beobachtetes Ergebnis;
- Validierungsstatus: **protokolliert / engine-geprüft / annotierte Interpretation / offen / widerlegt**;
- Begründung und mögliche Gegenhypothesen.

**Vorsicht:** „Responsivität“ kann nur anhand sichtbarer Anpassungen an veränderte Zustände bewertet werden; fehlende Verteidigung kann an erzwungener Stellung liegen. „Responsible“ im vorhandenen Forschungs-Memo meint *eng spielbezogenes* Regel-/Risiko-/Budgetverhalten, nicht moralische Qualität.

### 4.2 E3 und Messkonzept

ANDY benutzt das Projektkonzept **E3**. Aus der bisherigen Diskussion sind **Effektivität** und **Effizienz** ausdrücklich benannt. Die **offizielle dritte E3-Komponente muss aus den ursprünglichen Projektdokumenten verbindlich übernommen werden**, bevor eine metrische Definition publiziert wird; hier wird sie bewusst **nicht erfunden**. Daneben werden separat Antizipation, Anpassung/Responsivität, Regelkonformität und Ressourcen untersucht.

Bevor eine Kennzahl als Vergleichsmetrik gilt: Definition, Nenner, Ausschlüsse, Unsicherheit, Verzerrungsquellen, Validierung und Grenzen dokumentieren.

### 4.3 Drei initiale Vergleichsfälle (Arbeitsdaten, Status prüfen)

| Match-ID | Kontrahenten | dokumentierter/zu prüfender Ausgang | Forschungsfenster |
|---|---|---|---|
| `andy_0c0f7413fdf6` | OpenAI Astra (weiß) vs Gemini 4 Argon (schwarz) | Matt Weiß; 249 API-Entscheidungen, 233 ausgeführte Züge, 16 nicht ausgeführte Argon-Entscheidungen | Format-/Legalitätsfehler, Ressourcen, Go/Chess-Wechselspiel, Schlussangriff |
| `andy_64c8f95436d1` | OpenAI Astra (weiß) vs Claude Opus 5.5 (schwarz) | Matt Weiß; 147 Entscheidungen, 145 Züge, 2 Claude-Ausgabefehler | konkrete Prognose #143, Antwort #145, Go-Zug #146, Matt #147; „erzwungen“ noch zu validieren |
| `andy_1c77f49b3e17` | Gemini 3.8 Flash vs Gemini 4 Argon | möglicher Go-Sieg Argon; **nicht als verifiziert berichten**, da terminale Engine-Bestätigung zu prüfen ist | alternative Siegbedingung / Go-Schwelle / Gegenüberstellung mit Matt-Partien |

Die Zahlen sind **Referenzangaben aus bisherigen Prototyp-Analysen**; vor finaler Veröffentlichung gegen die Original-JSONL und Engine-Version nachprüfen. Match- und Modellnamen sind Spiel-/API-Bezeichnungen zum jeweiligen Datum, keine statischen Eigenschaften.

### 4.4 Vergleichbarkeit: Design vor Ranking

- Einheitliches Ruleset, Engine, Master-/Systemprompt, Tokenlimits und Messdefinitionen;
- Anbieter, exakte Modellversion, Modellparameter, API-Endpunkt, Datum, Farben und First-Move-Rechte pro Match dokumentieren;
- Farbwechsel-/Rückkampf-Paare und mehrere Wiederholungen nutzen, sofern möglich;
- Fälle nach vergleichbaren Bedingungen stratifizieren; Abweichungen nicht verstecken;
- Ergebnisse mit Anzahl Matches, Streuung und Unsicherheiten darstellen;
- **Keine generelle Rangliste aus zwei oder drei Anschauungspartien** ableiten.

## 5. Standardprodukte des Lab

### A. Individual Research Edition (Ziel 18–24 Seiten)
Kurzabstract; Matchkontext; Methodik; Brettzustände/Regeln; Ressourcen; Chess-/Go-/Token-Zeitachsen; kritische Zugfolgen; Claim→Action→Outcome-Tabelle; Gegenhypothesen; Validierung; Quellen/Limitations; reproduzierbare Anhänge. **Status:** Es existieren sechsseitige Piloten; erweiterter Standard ist noch nicht umgesetzt.

### B. Comparative Research Edition (Ziel ca. 24 Seiten)
Übergreifende Fragestellung; eingeschlossene Matches und Ausschlusskriterien; harmonisierte Metriken; tabellarischer Vergleich; synchronisierte Kurven; ausgewählte Fallstudien; unabhängige Reviews; Interpretation; Limitationen; Reproduzierbarkeit.

**Arbeitstitel:** *When Plans Meet Reality – A Comparative Analysis of AI Decision-Making in the ANDY Arena*.

### C. Machine-readable Research Edition
Dieselben geprüften Fakten in versioniertem JSON/JSONL und/oder Markdown. Enthält Claim-IDs, Event-Referenzen, Schema-Version, Prüfer, Validierungsstatus und Belege. **PDF und maschinenlesbare Edition müssen auf denselben abgeleiteten Datensätzen beruhen**, nicht getrennt händisch gepflegt werden.

### D. Journal-Artikel
Erklärende Narrative, Bilder und Fight-Night-Bezüge; Links zu PDF, Replay und Originaldaten. Redaktioneller Dreiklang **Arena Moment → Evidence → Interpretation**. Nicht die vollständige PDF bloß neu erzählen.

## 6. Open Research Corpus: Datenarchitektur (Soll)

```text
original/<match-id>.jsonl           unverändert, SHA-256, Quelle/Herkunft
manifests/<match-id>.json           Datum, Akteure, API, Budgets, Ruleset, Lizenzen
normalized/<match-id>.events.jsonl  einheitliche Ereignisse; Parser-/Schema-Version
verified/<match-id>.jsonl           per Engine geprüfte State-Transitions
annotations/<match-id>.claims.jsonl Claim-Text, Typ, Event, Evidenz, Status
reports/individual/                PDF/Markdown + Reproduktionsmetadaten
reports/comparative/               PDF/Markdown + verwendete Match-Liste
scripts/                           Parser, Prüfungen, Diagramme, Tests
schemas/                           JSON-Schemata und Änderungsverlauf
DATASET_CARD.md                    Herkunft, Rechte, Umfang, Bias, Grenzen
LICENSES.md                        differenzierte Lizenzlage von Code/Daten/Texten
```

**Trennung:** Originaldaten sind nicht automatisch „Goldstandard“. Ein API-Antworttext ist eine Beobachtung; Regelvalidierung und fachliche Annotation sind gesonderte Ebenen. Abgeleitete Daten erhalten Version, Quellhash, Regel- und Parser-Version. Bei widersprüchlichen Annotationen Meinungsdifferenz und Prüfer dokumentieren.

**Publikation nach Rechteprüfung:** GitHub als zugängliche kanonische Quelle, optional Dataset-Hub (z. B. Hugging Face) als gespiegelte, versionierte Distribution. Keine API-Schlüssel oder personenbezogenen Daten veröffentlichen.

## 7. Perspektive: KI-Training, Evaluation und Lernexperiment

**Hypothese:** ANDY könnte ein nützlicher Datensatz für mehrstufige Entscheidungsforschung werden, da Zustände, Äußerungen, Handlungen, Ausführungsfehler und Konsequenzen zusammengeführt werden können.

Mögliche Anwendungsfälle **(noch keine nachgewiesene Eignung)**:
- Supervised Fine-Tuning auf sorgfältig validierten Zustands-/Aktionsbeispielen;
- Preference Learning mit **wirklich vergleichbaren** Alternativen, nicht bloß „Gewinnerzug = gut“;
- Reinforcement Learning in einer versionierten ausführbaren ANDY-Umgebung mit regelbasierten Rewards;
- Evaluation bislang ungesehener Spielsituationen und Gegner.

**Voraussetzungen:** Datenqualität; ausreichende Fallzahl und Diversität; Rechte; definierte Aufgabenspezifikation; keine Datenleckage zwischen Training und Test; unabhängige, möglichst neue Tests nach Training; sichere Datenschutz-/Prompt-Prüfung.

**Forschungsfrage für später:** Verbessert ANDY-basiertes Training tatsächlich Antizipation, Anpassung und Ressourcen-Effizienz in neuen, kontrollierten Matches?

**Nicht behaupten:** dass PDFs/JSONL bereits nachweislich gute Trainingsdaten sind oder dass die Modellbegründungen korrekte interne Gedanken wiedergeben.

## 8. Architektur, Publikation und Markenidentität

- **Arena-Webseite:** `andy-arena.com`; UI-Prototyp mit DE/EN/ZH, Homepage/Fight Night und replaybasiertem Theater.
- **Blog:** `blog.andy-arena.com`; WordPress separat, aktuelle öffentliche Coming-Soon-`index.html`, WordPress-`index.php`; derzeit `DirectoryIndex index.html index.php` in Blog-`.htaccess`. Umstellung beim Launch kontrolliert vornehmen; keine WP-Kerndateien überschreiben.
- **Website-Releasehistorie:** V0.8.1.4 als vorheriger getesteter Rückfallstand; V0.8.2 Mobile/Blog und V0.8.2.1 Cache-Fix; Live-/Windows-Abnahme darf nicht ohne Test als abgeschlossen gelten.
- **Research-Code/Dokumentation:** GitHub, versioniert; Regeln und Engine-Version in jeder Publikation referenzieren.
- **Markenbild:** ANDY-Original-Logo, Arena dunkel/cinematisch; Lab sachlich, Journal 70 % Science Editorial / 30 % Fight Club. Keine Anbieter-Partnerschaft suggerieren; Verwendung fremder Logos/Marken anhand Richtlinien und ggf. Erlaubnissen prüfen.
- **Journal:** Vier Rubriken: Arena Stories, Research & Insights, Behind ANDY, Beyond the Arena; eigene Match-Analysis-Vorlage; klare Trennung Szene/Beleg/Interpretation.
- **Marketing:** YouTube (Matchvideos/Erklärungen), LinkedIn (Forschung/Kooperation), Instagram (Fight Night/Reels), X (KI-Fachdiskurs); Ausführung/Redaktionsplan in separatem Thread.

## 9. Arbeitsteilung und Threadwechsel

**Menschliche Projektleitung:** Ziele, Design- und wissenschaftliche Freigabe, Anbieter-/Rechtefragen, Veröffentlichung und Projektprioritäten.  
**KI-Kollaboration:** ChatGPT für Umsetzung/Analyse, weitere Modelle wie DeepSeek und Qwen für strategische Perspektiven und kritisches Review, mit tatsächlich geleisteten Beiträgen differenziert dokumentieren. Keine erfundene Zuschreibung oder Behauptung unabhängiger Validierung.

**Prinzip:** Ein Thread = ein klarer Arbeitsstrang. Zentraler Plan bleibt hier; fachliche Unterlagen verbleiben in spezialisierten Dateien und Quellrepositories. Diskussionen führen nicht automatisch zu neuen „beschlossenen“ Anforderungen.

### Pflicht-Übergabe eines Fachthreads

1. Ziel/Aufgabe und aktueller Code-/Datenstand (Repository/Branch/Commit oder ZIP-Prüfsumme).
2. Was funktioniert nachweislich, was ist nur lokal getestet, was noch offen?
3. Neue Entscheidungen und exakte Stellen im Masterplan, die berührt werden.
4. Dateipfade, Schnittstellen, benötigte Inputs, blockierende Unsicherheiten.
5. Nächste **kleine** testbare Arbeitseinheit; klare Abnahmekriterien.
6. GitHub-Commit oder Issue; bei wichtigen Richtungsänderungen Masterplan anpassen.

**Für neue Threads:** Erst [Thread-Startbriefing](ANDY_THREAD_START_HIER.md) lesen, dann diese Datei und fachliches Memo. Bei Widersprüchen konkret nachprüfen und Änderungen vorgeschlagen statt stillschweigend vollziehen.

## 10. Roadmap mit nachprüfbaren Meilensteinen

| Priorität | Schritt | Nachweis / Exit-Kriterium | Status |
|---|---|---|---|
| P0 | Website/Mobile/Blog-Release stabilisieren | Hostinger, Desktop/Mobile, drei Sprachen, Replay und Cache tatsächlich getestet | Test offen |
| P0 | Original-JSONL und zugehörige Engine-/Ruleset-Versionen sichern | Matchliste, SHA-256, Datenherkunft, Regeln dokumentiert | zu prüfen |
| P0 | **E3-Drittbegriff** aus Primärunterlagen übernehmen | eindeutige freigegebene Definition | offen |
| P1 | Corpus-Schema + Parser/Validator v0.1 | automatisch prüfbare Events, Fehlerklassifikation, Tests | geplant |
| P1 | Erstes vollständiges Individual-Research-PDF | 18–24 Seiten, Claims belegt, Brettdiagramme, Review | geplant |
| P1 | Comparative Research Edition 001 | ≥2 vergleichbar definierte Partien, dokumentierte Einschränkungen | geplant |
| P1 | Machine-readable Evidence Layer | PDFs und JSONL-Annotationen aus gleicher Version | geplant |
| P2 | Journal-Start mit 3 Beiträgen | sauberes WP-Template, Links zu Originaldaten, DE/EN | separat geplant |
| P2 | Training-/Evaluation-Dataset Card & Rechtecheck | Herkunft, Lizenz, Risiken, Splits, Nutzung definiert | geplant |
| P3 | Kontrolliertes Modelltraining + Hold-out-Vergleich | reproduzierbare Baseline vs. trainiertes Modell | Forschungsoption |

**Statuslegende:** „geplant“ ist kein Commit und kein getestetes Feature. Immer konkrete Nachweise ergänzen.

## 11. Offene strategische Entscheidungen

- Wie lautet die **dritte offizielle E3-Komponente** und ihre prüfbare Operationalisierung?
- Welche Engine-Version/-Hashes erzeugten die konkreten historischen Matches?
- Sind alle erforderlichen Original-JSONL und Nutzungsrechte zur öffentlichen Distribution bzw. zum KI-Training gesichert?
- Nach welchem protokollierten Schema unterscheiden wir Entscheidung, legalen Zug, Ausgabe-/Formatfehler und API-Fehler?
- Welche Mindeststichprobe und Kontrollbedingungen reichen für welche Vergleichsaussage?
- Wie werden Mehrdeutigkeiten in Text-Claims von mehreren Annotatoren bewertet und aufgelöst?
- Wie werden Corpus, Web, Blog und Research-PDFs langfristig versionsynchron gehalten?

## Lab 2.0 – Verbindliche Prioritätenentscheidung vom 13.11.2026

**SSOT und Umsetzungsbriefing:** [ANDY LAB 2.0 – Research Architecture v1.0](../research/andy-lab/ANDY_LAB_2_0_RESEARCH_ARCHITECTURE_v1.0.md)

- **Prio 1:** Forschungsfragen, hypothesengeführte Mustererkennung und Evidenzentwicklung über wiederholte, vergleichbar konfigurierte Partien; fünf Felder: strategische Zielwahl, Lageeinschätzung/Antizipation, Adaptivität, Ressourcen/Umsetzung und Stabilität/Entwicklung.
- **Prio 2 (on demand):** Sämtliche bisher bestehenden Lab-Daten, Diagramme und Funktionen aus Modellvergleich, Zuverlässigkeit, Experimente, Spielverlauf, Methodik und historische Daten **vollständig beibehalten**, als nachgeordnete Analysewerkzeuge verfügbar und aus Forschungsfragen erreichbar.
- **Kein primäres Benchmark-/Intelligenztest-/Modellranking-Ziel.** Einzelne Matches und Modelle dienen als Quellen und Vergleichsvariablen, nicht als Lab-Hauptnavigation.
- **Technik:** Rückwärtskompatible Evolution des vorhandenen Labs, einheitliche Datenbasis, kontrollierter Konfigurationsvergleich, transparente Daten-/Methodenversionen, Drill-down und wissenschaftliche Evidenz-/Unsicherheitskennzeichnung.
- **Status:** Produktausrichtung verbindlich beschlossen; technische Umsetzung und empirische Bestätigung einzelner Thesen stehen aus.

---

## 12. Änderungsprotokoll

| Version | Datum | Änderung |
|---|---|---|
| 1.0 | 2026-11-13 | Erstfassung: verbindlicher gemeinsamer Projektkompass, Forschungs-/Corpus-/Publikationsarchitektur, Roadmap und Threadübergabe |
| 1.0a | 2026-11-13 | Ergänzung Lab 2.0: hypothesenorientiertes Forschungsobservatorium (Prio 1); bisherige Lab-Analysen vollständig on demand (Prio 2) |

---
**Kernsatz:** *ANDY soll nicht nur zeigen, wer gewinnt, sondern nachvollziehbar machen, welche Entscheidungen, Aussagen, Anpassungen und Ressourcen zu beobachtbaren Ergebnissen führen — und wie sicher wir unsere Erklärungen dafür begründen können.*