# ANDY Lab 2.0 – Research Architecture & Umsetzungsbriefing

**Version:** 1.0 · **Beschluss-/Konzeptstand:** 13.11.2026 · **Status:** gemeinsam abgestimmte Produktausrichtung; technische Realisierung ausstehend  
**Adressaten:** ANDY_APP (Thread 1), ANDY Lab, Web/Journal, Forschung und Working-Paper-Koordination  
**Geltung:** Prioritäten, Informationsarchitektur, wissenschaftliche Einordnung und technische Integrationsprinzipien für Lab 2.0.  
**Masterplan:** [ANDY Gesamtkonzept](../../PROJECT/ANDY_GESAMTKONZEPT_MASTERPLAN_v1.0.md)  
**Forschungsgrundlagen:** [Event-to-Evidence Method](METHODIK/ANDY_EVENT_TO_EVIDENCE_METHOD_v0.1.md) · [Rückkampf-Hypothesenpool](METHODIK/ANDY_REMATCH_HYPOTHESENPOOL_UND_EXPERIMENTDESIGN_v0.1.md) · [Strategic Situational Awareness](METHODIK/ANDY_STRATEGIC_SITUATIONAL_AWARENESS_SSA_v0.1.md)

---

## 1. Verbindliche Leitentscheidung

> **ANDY Lab 2.0 ist primär ein kontinuierlich wachsendes, hypothesengeführtes Forschungsobservatorium für empirische Muster strategischen Verhaltens von GPAI-Systemen im adaptiven Wettbewerb.**
>
> **Priorität 1:** Forschungsfragen, Forschungs-/Gegenhypothesen, übergreifende empirische Muster, Veränderungen über wiederholte Experimente, Evidenzstand und Unsicherheit.  
> **Priorität 2:** Der komplette Funktions- und Datenumfang des bisherigen Labs – Modellvergleich, Zuverlässigkeit, Experimente, Spielverlauf, Methodik und historische Daten – bleibt erhalten und ist **on demand** als Forschungsinstrumentarium erreichbar.

**Nicht primäre Lab-Ziele:** KI-Intelligenztest, allgemeine „Bestes Modell“-Rangliste, Benchmark-Cockpit, individuelle Match-Story, isolierte Performance-KPIs oder Sieger-Inszenierung. Solche Angaben können als beobachtete Variablen, Kontext oder Arena-Story vorkommen, steuern aber **nicht** die Lab-Informationsarchitektur.

**Klarer Perspektivwechsel:** Nicht „Welches Modell ist intelligenter?“ und auch nicht „Welches Match war besonders?“, sondern **„Welche Verhaltensmuster beobachten wir unter welchen experimentellen Bedingungen – wie stabil sind sie, welche Hypothesen stützen oder widerlegen sie und wie verändert sich der Evidenzstand mit neuen Partien?“**

Das einzelne Match bleibt unverzichtbare **Quellen- und Beobachtungseinheit**, aber nicht primärer Einstiegspunkt. Das einzelne Modell bleibt eine **Einfluss-/Kontrollvariable**, aber nicht Mittelpunkt. Einzelspiel-Fallstudien/Individual Research Editions bleiben als nachvollziehbare Belege und methodische Tiefenprüfungen möglich; ihre Relevanz für eine konkrete Forschungsfrage bestimmt, wann sie geöffnet werden.

## 2. Ausgangslage: das bisherige Lab erhalten, nicht abwerten

Bisheriger Forschungsrundgang:

1. **Modellvergleich** – Vergleichskennzahlen, Paarungen, Farben, ausgewertete Modelle.
2. **Zuverlässigkeit** – Ausführungsquoten, Format-/Legalitäts- und Retryfehler.
3. **Experimente** – Konfigurationen und Vergleichsbedingungen.
4. **Spielverlauf** – chronologische Entscheidungen, Kontroll- und Ressourcenverläufe, Replay-/Ereignisbezug.
5. **Methodik** – Definitionen, Grenzen, Datenqualität, Validierung.
6. **Historische Daten** – Herkunft, Archiv und zeitliche Verfügbarkeit.

**Alle sechs bleiben technisch/funktional erhalten:** vorhandene Diagramme (u. a. Geschwindigkeit × Zuverlässigkeit, Ausführungsquoten, Fehler-Heatmaps, Weiß-/Schwarz-Matrix, Go-Kontrollkurven, historische Aktivität), Filter, Daten- und Exportmöglichkeiten, vorhandene Quellenbezüge und der Forschungsassistent. Kein Big-Bang-Rewrite, keine parallele oder divergierende Datenhaltung.

**Neue Rolle:** Im Lab als sekundärer Bereich **„Analysewerkzeuge & Daten“** auffindbar und **kontextuell aus einer Forschungsfrage heraus** verlinkt. Priorität 2 bedeutet *niedrigere Sichtbarkeit*, nicht geringeren fachlichen Wert oder Löschung.

## 3. Primäre Navigation: fünf Forschungsfelder

Die Startseite präsentiert zuerst Fragen, nicht Charts, Match-IDs oder Modellnamen. Der Hypothesenpool wird **fachlich in fünf Felder** gruppiert; die IDs bleiben unverändert.

| Forschungsfeld | Leitfrage | Bestehende Hypothesenbezüge | Primäre Evidenzquellen |
|---|---|---|---|
| **01 Strategische Zielwahl** | Unter welchen Bedingungen wählen Modelle Schach oder Go als Siegweg; bleiben Präferenzen stabil? | H1–H4, H13 | Claims/Zieläußerungen, freie Chess-/Go-Aktionen, Kontrollentwicklung, KO-Typen |
| **02 Lageeinschätzung & Antizipation** | Wie zutreffend bewerten sie eigene und gegnerische Chancen/Gefahren und prognostizieren Entwicklungen? | SSA-H1–H3, SSA-H5, H15 | zitierfähige Modelläußerungen, verifizierte Zustände, Threat-/Forecast-Episoden |
| **03 Adaptivität im Wettbewerb** | Wann und wie ändern sich Pläne und Handlungen nach neuen/unerwarteten Gegneraktionen? | H5–H8, SSA-H4, SSA-H6 | Eventsequenzen, Vorhersage–Gegneraktion–Reaktion, Alternativen/Opportunity Windows |
| **04 Ressourcen & Umsetzung** | Wie beeinflussen Budget, Thinking-/Outputlimits, Retries und Fehler die realisierte Handlung? | H9–H12 | Token-/Zeit-/API-Nutzung, Roh-/Normalformat, Legalität, Ausführungs- und TKO-Ereignisse |
| **05 Stabilität & Entwicklung** | Welche Muster bleiben über Farben, Gegner, Konfigurationen, Modell-/API-Versionen und Zeit erhalten? | H3, H6, H13–H15 | verknüpfte Rückkampfserien, Konfigurationsgruppen, Kohorten-/Zeitvergleich |

**Querbezüge ausdrücklich zulassen:** Eine Beobachtung kann mehrere Hypothesen betreffen, ist dadurch aber **nicht mehrfach unabhängige Evidenz**. Die bestehende Literatur-/Neuheitsfrage bleibt offen; ANDY beansprucht hier keine universelle Intelligenzmessung.

## 4. Standardaufbau einer Forschungsfeld-Seite

1. **Leitfrage und Relevanz:** kurzes, verständliches Forschungsproblem – keine Modellwertung.
2. **Hypothesenregister:** IDs, explizite Arbeitshypothesen und Gegenhypothesen, Operationalisierung, vorab/explorativ, Version.
3. **Empirische Abdeckung:** Anzahl relevanter *Matches*, unabhängiger Serien, Konfigurationsgruppen und auswertbarer Ereignisse; fehlende Daten und Verzerrungen sichtbar.
4. **Muster und Verläufe:** aggregierte Kennzahlen, beobachtete Unterschiede, zeitliche Entwicklung, Reproduktions-/Unsicherheitsintervalle soweit sinnvoll.
5. **Evidenzlage:** gestützt / widersprochen / gemischt / offen / mangels Daten nicht prüfbar; Belege und Ableitungsgrenzen.
6. **Kontrollierte Vergleichsansicht:** Filter nach Ruleset, Budget, Reasoning- und Retrysetting, Modell-/Adapterversion, Gegner, Farbe, Zeitraum; nur zulässige Vergleichsgruppen.
7. **Gegenbeispiele und Alternativerklärungen:** sichtbare negative Fälle, Selektions- und Confounderrisiken.
8. **Drill-down auf Prio-2-Werkzeuge:** passender Plot, Match, Ereignis, Original-JSONL, Code/Engine-Prüfung, Forschungsassistent.
9. **Nächste Experimente:** welche neue Serie kann konkurrierende Erklärungen unterscheiden?
10. **Publikations-/Update-Referenz:** zugehörige Research Edition oder Working Paper und Datenstand, ohne vorzeitige wissenschaftliche Freigabe.

**Datensparsame Oberfläche:** Beginne mit Leitfrage, relevantem Muster/Evidenzstatus und gut lesbarer Grafik; Details, komplexe Metriken und historische Analysen aufklappbar oder kontextuell erreichbar. Keine Übersicht mit 21 gleichgewichtigen Hypothesenkacheln.

## 5. Das Lab wächst mit der Datenbasis

- **Einzelne Partie:** Beobachtung oder Prüfbeispiel; keine generalisierte Aussage.
- **Vergleichbare Farbtauschpaare:** erste Kontrolle des Farbeffekts.
- **Wiederholungen gleicher Konfiguration:** Variation, Häufigkeit, Gegenfälle und vorläufige Muster.
- **Gezielte kontrollierte Variation:** Budget/Reasoning/Retry/Regeln/Gegner verändern, *einen Faktor möglichst gezielt*, andere dokumentieren.
- **Historische/Längsschnittvergleiche:** Entwicklung über Zeit; Modell-/Adapter-/Regelupdates als potenzielle Störfaktoren explizit kontrollieren.

**Kein automatischer Wahrheitsgewinn allein durch „mehr Spiele“.** Es kommt auf Unabhängigkeit, Vergleichbarkeit, Datenqualität, Abdeckung und Konfundierung an. 1.000 Entscheidungen aus wenigen Partien sind keine 1.000 unabhängigen Match-Beobachtungen. Match/Serie sind Cluster; Unsicherheit entsprechend berechnen.

Forschung bleibt zweigleisig:
- **Explorativ:** aus vorhandenen Logs Muster entdecken und Hypothesen formulieren.
- **Konfirmatorisch:** Hypothesen, Nenner, Metriken, Einschlussregeln und Entscheidungsmaß **vor neuen Partien** versioniert festlegen; neue, bisher unbenutzte Spiele zur Prüfung verwenden. Nicht dieselbe Entdeckungsserie als unabhängige Bestätigung zählen.

Bei laufend ergänzten Daten **Datenstand/as-of, Korpusversion, Methodik-/Parser-/Engineversion, Stichprobenumfang und Änderungsprotokoll** mitführen. Historische Ergebnisse nicht stillschweigend überschreiben. Forschung darf früheren Annahmen widersprechen.

## 6. Configuration Comparator: fachlich entscheidendes Werkzeug

| Vergleichsstufe | Definition | UI-/Analysevorgabe |
|---|---|---|
| **Identische Konfiguration** | Gleiche Ruleset-/Engineversion, Modellversionen, Prompts/Strategiemodus, Awareness, Tokenbudget, Reasoning-/Output-/Retry-/Entscheidungslimits, Ausgangsbedingungen und kontrollierte Rollen/Farben | als vergleichbare Wiederholung gruppieren |
| **Kontrollierte Variation** | Explizit dokumentierter gezielter Faktor (z. B. Farbe **oder** Budget) bei sonst möglichst konstanten Bedingungen | Unterschied/Intervention kennzeichnen |
| **Ähnliche Konfiguration** | Relevante Bedingungen vergleichbar, einzelne Störfaktoren dokumentiert | nur vorsichtige explorative Auswertung |
| **Nicht direkt vergleichbar** | Schlüsselparameter fehlen oder sind relevant verschieden | keine unkommentierten Vergleichs- oder Rankingzahlen |

**Kritisch:** Bei Farbtausch wandern modellspezifische Konfigurationen **mit dem Modell**, nicht mit Weiß/Schwarz. `parent_match_id`, `rematch_group_id`, `config_snapshot`, Terminierungsgrund, tatsächliche Modell-/Adapterversion und Regelstand möglichst dokumentieren. Wenn alte Daten Felder nicht enthalten, als unbekannt kennzeichnen, keine Konfiguration erfinden.

**Ebenen trennen:** Änderungen **innerhalb des Matches** (Adaptivität), **zwischen Wiederholungen** (Varianz/Präferenz) und **über längere Zeiträume** (Drift/Updates) haben unterschiedliche Aussagekraft.

## 7. Daten- und Methodenarchitektur (Anforderungen, kein Behaupten über Ist-Code)

```text
Original-JSONL + Matchmanifest + Regeln/Engine + Adapter-/Provider-Metadaten
     ↓ validieren, versionieren, hashen
Normalisierte Matches / Spieler / Konfigurationen / Entscheidungen / Zustände
     ↓ Claim-/Episodenkodierung + Engine-/Alternativenprüfung
Hypothesenbezogene Evidenzdatensätze
     ↓ kontrollierte Match- und Serienaggregation + Unsicherheiten
Forschungsfragen / Befundstand / vergleichende Entwicklung
     ↕ selektiver Drill-down
Altes Lab: sechs bestehende Analysebereiche + JSONL + Replay
```

**Evidenzstatus explizit:** `logged` (protokolliert), `derived` (berechnet), `engine_verified` (regelgeprüft), `annotated`, `hypothesis`, `unresolved`/`contradicted`. Modelläußerungen sind **protokollierte Texte**, kein direkter Beleg interner Denkprozesse. Entsprechendes gilt für Antworten des KI-Forschungsassistenten.

**Minimaler Forschungsnachweis:** hypothesis_id/version, dataset_snapshot/hash/as_of, eligibility_filter, config_comparability, n_matches/n_groups/n_episodes, metric/version, result, uncertainty, caveats, supporting event IDs, contrary cases, source/output links, update timestamp.

### Forschungsassistent
Wandelt sich von einem allgemeinen Dashboard-Kommentator zu einem **kontextgebundenen Evidenz- und Hypothesenassistenten**:
- „Welche Beobachtungen stützen oder widersprechen H2?“
- „Welche Ausnahmen treten bei Farbtausch auf?“
- „Welcher Konfigurationsunterschied erklärt den Trend alternativ?“
- „Welche Folgeexperimente würden zwischen H1 und H2 unterscheiden?“

Antworten müssen Quelle, Konfiguration, Datenstand und Unsicherheit benennen und Hypothese vs. Beleg trennen. **Keine automatische Forschungsfreigabe durch den Assistenten.**

## 8. Navigation / UX: Evolution statt zweites Lab

**Primär (Start):** „Forschungsfragen“ mit fünf Themen; pro Thema laufend aktualisierte Evidenzstände. Optional kompakter „Was hat sich seit dem letzten Datenstand verändert?“-Abschnitt, aber **keine** Leaderboard-Topkarte.

**Sekundär (on demand):** „Analysewerkzeuge & Daten“ mit unverändertem Bestand:
1. Modellvergleich
2. Zuverlässigkeit
3. Experimente
4. Spielverlauf
5. Methodik
6. Historische Daten

**Querverbindungen:** Hypothese → passende Vergleichsgruppe/Visualisierung → einzelne Ereignisse/Original-Logs; Rücklink zum Hypothesenkontext. Auswahl/Filter nach Möglichkeit durchreichen.

**Prio-2 heißt nicht verborgen:** über sichtbaren, jedoch nachgeordneten Link/Expander erreichbar, bestehende Deep-Links möglichst stabil. Keine bisherige Funktion entfernen. Aktuelle labtechnische Architektur und UI-Tests vor Eingriff inventarisieren.

### Gewünschter neuer Einstiegstext

> **ANDY Lab – Muster erkennen. Hypothesen prüfen. Entwicklungen verstehen.**
>
> ANDY Lab untersucht anhand einer wachsenden Zahl dokumentierter Experimente, wie allgemeine KI-Modelle unter neuartigen Regeln, konkurrierenden Siegwegen und begrenzten Ressourcen handeln. Im Mittelpunkt stehen Forschungsfragen zu strategischer Zielwahl, Lageeinschätzung, Antizipation, Adaptivität, Ressourcennutzung und der Wiederholbarkeit beobachteter Muster.
>
> Jede Forschungsfrage wird mit überprüfbaren Hypothesen, vergleichbaren Versuchskonfigurationen und nachvollziehbaren Daten verbunden. Neue Partien erweitern oder korrigieren den dokumentierten Evidenzstand.
>
> **ANDY Lab misst keine allgemeine Intelligenz und erstellt keine universelle KI-Rangliste.** Die bekannten Analysewerkzeuge und Einzeldaten bleiben für vertiefende Untersuchungen vollständig verfügbar.

**Nicht als bereits live ausgerollten Website-Text verstehen:** ist ein vorgeschlagener, durch die Produktentscheidung fachlich gedeckter UI-Text.

## 9. Priorisierte Umsetzung für Thread 1 (ANDY_APP)

### P0 – Schutz des vorhandenen Labs
- Bestehende UI-Funktionen, Datentabellen, Diagramme, Filter, Forschungsassistent und Links inventarisieren.
- Vorhandene URLs/Panel-/Modal-Schnittstellen und Zustandsübergänge dokumentieren; Regressionstests vor Neustrukturierung.
- Ausgangs-Lab jederzeit erreichbar lassen. Keine Umbenennung/Entfernung ohne Kompatibilitätsplan.

### P1 – Neue Forschungs-Startansicht (kleiner MVP)
- Fünf Forschungsfragen als Einstieg.
- Pro Frage: Kurzthese, zugeordnete Hypothesen, **echter** Daten-/Evidenzstatus, Anzahl auswertbarer Matches, Grenzen, ein passender Plot falls vorhanden.
- Wo Kennzahlen noch nicht existieren: **„Noch keine validierte Evidenz“**, niemals Demo-Zahlen als echte Daten.
- Prominenter, aber sekundärer Zugang „Analysewerkzeuge & Daten“ zum bisherigen Lab.
- Kein eigenes zweites Backend für dieselben Matches.

### P2 – Verknüpfung / Hypothesenregister
- Bestehende H1–H15 und SSA-H1–H6 aus GitHub als referenzierbare Registry übernehmen.
- Forschungsfrage ↔ Hypothese ↔ definierte Kennzahl ↔ Dataset/Configs ↔ Source Event/Match.
- Drill-down auf bestehende Charts, Logs und Replay; Konfiguration/Filter möglichst beibehalten.
- Scope und Nenner vor Vergleichen anzeigen.

### P3 – Serienanalyse und Evidenzentwicklung
- Rückkampf-Metadaten/-Gruppen, Color-Swap-Serien, Configuration Comparator.
- Aggregationen nach Zeit/Dataset-Stand, Match-/Serienzahl und Version; Gegenbeispiele, Unsicherheiten und Trends.
- Explorativ/konfirmatorisch getrennte Evidenzstände; versionsgebundene Research-Edition-/Working-Paper-Verknüpfungen.

**Reihenfolge bewusst pragmatisch:** P1 darf mit vorhandenen Daten und ausdrücklich offenen Hypothesen anfangen. Eine vollautomatische SSA-Claim-Analyse ist keine Voraussetzung für die neue Informationsarchitektur.

## 10. Akzeptanzkriterien

- [ ] Lab startet mit **Forschungsfragen**, nicht Leaderboard, Modell- oder Einzelmatch-KPI.
- [ ] Fünf Forschungsfelder werden konsistent auf Hypothesen-IDs abgebildet.
- [ ] Alle sechs früheren Lab-Bereiche samt Datendiagrammen/Filtern bleiben **on demand** erreichbar.
- [ ] Bei fehlender Evidenz werden keine Forschungsbefunde vorgetäuscht.
- [ ] Vergleiche zeigen Regel-/Modell-/API-/Budget-/Retry-/Farbkonfiguration und Vergleichbarkeitsklasse.
- [ ] Rückkampfserie und Ursprungspartie sind verknüpfbar; unterschiedliche Einstellungen nicht stillschweigend zusammengeworfen.
- [ ] Aggregationen benennen **n Matches / n Serien** und Daten-/Methodenversion, nicht nur Zugzahlen.
- [ ] Zeitverläufe trennen In-Match-Adaptivität, Cross-Match-Wiederholbarkeit und historische Änderungen.
- [ ] Jede relevante Aussage kann bei Bedarf auf Daten, Events oder Validierungsartefakte zurückgeführt werden.
- [ ] KI-Assistent unterscheidet Daten/Fakten, berechnete Kennzahlen, Hypothesen und offene Fragen.
- [ ] Bestandstests und Replay des alten Labs bleiben funktionsfähig.
- [ ] Öffentliches Framing vermeidet Intelligenztest-, Universal-Benchmark- oder allgemeine Siegerranglisten-Versprechen.

## 11. Wissenschaftliche Outputs und Zuständigkeiten

**Lab 2.0:** zeigt hypothesengeführte, wachsende Evidenzübersichten und Entwicklung unter kontrollierten Bedingungen.  
**Individual Research Editions:** beleuchten einzelne Matches/Episoden als nachvollziehbare Evidenzbeispiele und methodische Tiefenprüfungen, nicht als primäre Homepage-Inhalte.  
**Comparative Research Editions:** harmonisierte, mehrteilige Vergleiche über Matches/Serien.  
**Working Papers:** experimentelle Thesen mit Methoden-, Evidenz-, Gegenhypothesen- und Limitationsabschnitten; Freigabe nach bestehender WPS-Governance.

**Keine Neuheit oder bestätigte empirische Wirksamkeit vorab behaupten.** Eine neuartige Produkt-/Methodenkombination bleibt überprüfbare wissenschaftliche Positionierung.

## 12. Klare Nicht-Ziele für die erste UI-Stufe

- Kein Löschen des bisherigen Labs.
- Kein Neuentwurf aller Diagramme.
- Keine automatische generische Modell-Rangliste.
- Keine vorgetäuschte kausale Erklärung aus Korrelationen.
- Keine 21 Hypothesen als gleichgewichtige Menüeinträge.
- Kein eigenständiger zweiter Forschungsdatenbestand.
- Keine erzwungene Neuanalyse sämtlicher historischer JSONL vor einer nutzbaren neuen Startseite.

## 13. Weitergabe an andere Threads

**Kurzer Übergabesatz für Thread 1:**

> Das bestehende ANDY Lab bleibt vollständig erhalten, aber seine sechs Analysebereiche sind ab Lab 2.0 **Prio 2: Analysewerkzeuge & Daten, on demand**. **Prio 1** ist ein hypothesengeführtes Forschungsobservatorium mit fünf Fragenfeldern: Strategische Zielwahl, Lageeinschätzung/Antizipation, Adaptivität, Ressourcen/Umsetzung, Stabilität/Entwicklung. Primäre Inhalte sind aggregierte, versionierte Befunde aus wiederholten vergleichbaren Partien, Gegenhypothesen und Evidenzstände – keine Benchmarks, Modellranglisten oder Einzelmatch-Prominenz. Baue schrittweise, rückwärtskompatibel, mit Drill-down auf die bestehenden Funktionen. Dieses Dokument ist die Referenz für Zielbild und Abnahme.

---

**Leitsatz:** *Arena zeigt die Kämpfe. Replay rekonstruiert die Partien. ANDY Lab 2.0 untersucht, welche Muster über viele Partien hinweg entstehen – und welche Forschungsthesen die Daten tatsächlich tragen.*


## Ergänzung 14.11.2026 – freigegebener Erkenntniskern V0.1

[Gemeinsamer Erkenntniskern](CORE/v0.1/README.md) als übergreifende inhaltliche Mitte: Erkenntnis als adaptive Stabilisierung, Erleben (rot), Erforschen (grün), Erahnen (blau). Vier konzeptionelle Denkmodelle: Sweet Spot?, Competitive Mirroring, Dynamic Bonoma, Nested Competitive Networks; adaptive Erkenntnisannäherung als Klammer. Keine neue feste Messkategorie oder Änderung der fünf Forschungsfelder, Hypothesen-IDs, sechs Werkzeuge, Score-/AQP-Regeln oder Vergleichbarkeitsbedingungen. [Konsensmatrix](CORE/v0.1/02_KONSENSMATRIX.md). Die Umsetzung der Lab-App bleibt separat.


## Ergänzung 14.11.2026 – Punch Lab (eigenständiges zukünftiges Forschungsfeld)

Neben Observation Lab und Serial Lab tritt perspektivisch **Punch Lab – Controlled Destabilization & Adaptive Recovery**: Chaos gezielt verursachen, Lageanalyse, Neuorientierung, Ressourcenaufwand und relative Restabilisierung untersuchen. Siehe [Forschungsagenda, Abschnitt 14 – PL](METHODIK/ANDY_REMATCH_HYPOTHESENPOOL_UND_EXPERIMENTDESIGN_v0.1.md#14-forschungsagenda--punch-lab--controlled-destabilization--adaptive-recovery-pl). Die fünf bisherigen Felder bleiben bestehen; PL ist ein zusätzliches experimentelles Querschnittsfeld. Zunächst ungestörte Serien, später isolierte Interventionen mit Kontrollfortsetzungen; experimentelle Ergebnisse separat vom Arena-Leaderboard. Kein sofortiger App-Entwicklungsauftrag.
