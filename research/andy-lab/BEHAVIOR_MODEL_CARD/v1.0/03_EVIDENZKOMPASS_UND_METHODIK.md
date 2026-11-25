# 03 — ANDY Evidenzkompass / Methodik / Theory Overlay

**Kernaussage:** Viele Spiele können robustere Aussagen über *wiederkehrendes Verhalten unter vergleichbaren Bedingungen* ermöglichen. **Mehr Spiele garantieren weder monoton konvergierende Werte noch Generalisierbarkeit**, insbesondere bei abweichenden Rulesets, Tokenbudgets, Engineversionen, Providern oder Selektionsregeln.

## A. Drei getrennte Achsen statt Evidenz-Ampel

### A1 – Beobachtungsumfang
- **N logische reale Partien**, Zeitraum und Datenstand, individuelle Rollen/Teilnahmen bei Self-play separat.
- Welche Partien haben vollständigen JSONL+JSON-Rahmen? Welche sind historisch nur teilweise dokumentiert?
- Anteil mit belegter Ruleset-Version, Modell-ID, API-Latenz, Token-Usage, Endgrund.
- Aus welchen *Konfigurationsgruppen* stammen Beobachtungen (z. B. 150k / 350k), ohne sie als Sieger-/Leistungsgruppen gegeneinander auszuspielen?
- Auswahlbias: Welche Spiele wurden überhaupt durchgeführt, archiviert, qualitätsgeprüft, ausgeschlossen? Fehlgeschlagene Setups und Abbrüche nicht verschweigen.

### A2 – Empirische Stabilität
- Erst bei hinreichend vergleichbaren wiederholten Spielen für **eine konkrete Metrik** beurteilen; z. B. historische Ausführungsquote, p50-API-Zeit, Output/Input.
- Visuelles Grundprinzip: X = Zahl eingeschlossener *logischer Partien*, Y = kumulative eigene Kennzahl; optional Unsicherheits-/Streuungsband **nur mit definierter Methode und realen Daten**.
- Konfiguration/Engine/Modellstand pinnen; Abhängigkeit von Serien und identischen Prompts berücksichtigen, ggf. Blocks statt naive Unabhängigkeit.
- Erst ab ausreichend vielen geeigneten Partien eine Stabilitätsaussage; vorab nur „bisherige Beobachtung“ und die Rohstreuung.
- Eine flachere Kurve beweist **kein** internes Lernen; viele Züge derselben Partie sind keine unabhängigen Studienfälle.
- Keine künstlichen Kennzahlen `confidence=73%`, Sterne, einheitliche Stufen „geringe Qualität“ oder erfundene Konfidenzintervalle.

### A3 – Erhebungsaufwand
- Tatsächliche **eigene aktive API-Zeit**, belegte Matchlaufzeit als separater Kontext, Kosten **nur mit dokumentierten Tarifen** und Source-/Preis-Coverage.
- Eine geringe Spielzahl kann Folge echter **Langsamkeit, hoher Kosten, API-Limits oder fehlender Verfügbarkeit** sein; ohne Ursachenbeleg nur als mögliche Erklärung nennen.
- Anzeige z. B. „5 reale Partien; davon 1/5 mit vollständiger eigener API-Zeit; Kosten historisch nicht für alle Fälle belegbar.“
- **Keine Benachteiligung seltener/teurer/langsamer Modelle**; niedrige Erhebungsabdeckung ist keine negative Verhaltensnote.

## B. Visuelle Umsetzung

**Kompakt oberhalb der Analysen:**
`5 dokumentierte Partien · 2 Budgetgruppen · Latenzabdeckung 1/5`
Darunter zwei absichtlich unterschiedliche Darstellungen:
1. **Scope-/Coverage-Balken** mit Anzahl echter Partien, Segment-/Ruleset-Abdeckung und separaten Nullzuständen.
2. **Aufwandskarte**: dokumentierte API-Stunden / optional geschätzte Kosten mit Zeitpunkt und Tarifstatus.

Ein drittes Diagramm **„Beobachtung wächst“** darf zuerst ein didaktisches, klar als Konzept markiertes Schema sein, nicht eine vorgetäuschte echte Stabilitätskurve. Für veröffentlichte Cards nur reale, definierte Metrikreihen mit ausreichender Datenbasis oder explizites „noch nicht auswertbar“.

## C. Nested Competitive Networks als Kontext, nicht Punktzahl

Die Card beschreibt ein Modell, doch das beobachtete Handeln entsteht in einem verschachtelten Wirkungssystem:

- **Spielwelt:** gekoppelte Schach-/Go-Regeln, Positionen, Anfangszustand, Gegnerinteraktion.
- **Akteur/Funktionen:** ausgegebene Entscheidungen/Behauptungen; interne Architektur proprietärer Modelle nicht bekannt.
- **System:** Prompt, Adapter, Engine, Berechtigungen, Logger, Interpreter, Werkzeuge.
- **Provider/Ressourcen:** Routing, API-Limits, Cache, Tokens, Latenz, Budget, Tarife.
- **Mensch:** Konfiguration, Spielauswahl, Stopps, Freigaben, Auswahl der untersuchten Kohorte.

**Lokale Stabilität ≠ globale Stabilität:** Gute lokale Aktion kann mit Ressourcenverlust des Gesamtsystems einhergehen; eine Fehlfunktion kann beim Adapter/Provider statt beim Modell entstehen. Aus einer einzelnen Serie folgt kein allgemeiner kausaler Business-Befund.

## D. Dynamic Bonoma

Matrix der **Strategieeignung** × **Umsetzungsqualität**: Success, Roulette, Trouble, Failure. Der „Punch“ kann eine Strategie ungeeignet machen, obwohl Ausführung unverändert funktioniert. Ein Übergang und eine anschließende Reorganisation müssen **situativ mit Eventfenster, Alternativen und Entscheidungskriterien** belegt werden. Keine Quadrantenzuordnung aus Sieg/Niederlage, Kontrollpunkten allein oder Legalität.

## E. Sweet Spot? / Overthinking

Die Konzeption Underthinking ↔ Sweet Spot? ↔ Overthinking ist **unkalibriert, hypothesenhaft**. Eine mögliche Passung zwischen situativem Analysebedarf, Ressourcenallokation, realisierter Handlung und verbleibender Wettkampffähigkeit. **Budget-TKO ist kein Overthinking-Beweis; Output-Tokens sind nicht Reasoning-Tokens.** Ein Modell kann innerhalb *derselben Partie* unterschiedliche Konstellationen zeigen. Interpretation getrennt von deskriptiver I/O-Ratio, Zeit, Phasen und Ergebnissen.

## F. Stabilität A/B/C und Reflexion

A Grundstabilität: Setup, Regelbefolgung, initiale Umsetzung.  
B Wettkampfstabilität: Durchhaltevermögen, regelkonforme Ausführung, Ressourcen und Fehlerverlauf.  
C adaptive Wettbewerbsfähigkeit: Antizipation, Initiative, Reaktion, Zielwahl und Umsetzung unter Bedingungen; nicht aus einem Sieg automatisch ableitbar.

Aftermatch/Selbstkommentar einer später neu angerufenen KI ist eine **neue sekundäre Modelläußerung**, nicht Erinnerung an die damalige interne Denkspur. Sie erhält eigenes Datum, Prompt/Modellkontext und Evidenzstatus und darf den Primärbericht nicht überschreiben.

## G. Vier Nachweisstatus

**BEOBACHTET:** direkt geloggter Originalwert; Datenherkunft dokumentiert.  
**BERECHNET:** reproduzierbare Formel aus geloggten Daten; Metrikversion/Nenner dokumentiert.  
**INTERPRETIERT:** theoriegestützte Deutung mit Eventanker, Alternativerklärungen und Reviewer.  
**OFFEN:** nicht genügend Daten, keine verlässliche Klassifikation, Widerspruch oder fehlende Engine-/Provider-Semantik.

Zusätzlich Ergebnisevidenz `runner_reported` / `engine_independently_verified` / `unverified` / `conflict` gesondert führen. Eine UI-Auszeichnung „Quellen geprüft“ darf keine Verifikation innerer Gedanken oder kausaler Strategie behaupten.

**Grundsatz:** Die Card ist ein Living-Lab-Snapshot, nicht die Bewertung eines Modells als Mensch, Arbeitnehmer, Geschäftswerkzeug oder allgemeine Intelligenz.

## Quellen

[CORE – Nested Competitive Networks](../../CORE/v0.1/03_NESTED_COMPETITIVE_NETWORKS.md) · [Dynamic Bonoma](../../CORE/v0.1/05_DYNAMIC_BONOMA.md) · [Sweet Spot](../../CORE/v0.1/09_SWEET_SPOT.md) · [Analysekompass](../../ANALYSEKOMPASS/v0.1/README.md) · [Cybersecurity-Crossover (Hypothese)](../../CROSSOVER/CYBERSEC_NESTED_COMPETITIVE_NETWORKS_v0.1.md).
