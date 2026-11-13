# ANDY JOURNAL – Redaktioneller Themenspeicher aus den ANDY-Dialogen
**Version:** 0.1 · **Datum:** 13. November 2026 · **Status:** Ideen-/Recherche-Backlog, **keine** Artikelfreigabe  
**Quellenbasis:** Die hier vorliegende ANDY-Projektkonversation (Website/Blog/Lab/Research Editions/Corpus/Making-of/Mensch-KI-Kollaboration), ergänzend die im Projektkontext sichtbaren früheren ANDY-Arbeitsstände. **Keine** nachträgliche Prüfung kompletter Chat-Exporte.  
**Geltung:** Ergänzt [ANDY Journal v1.1](../README.md) und [ANDY Masterplan v1.0](../../../ANDY_GESAMTKONZEPT_MASTERPLAN_v1.0.md), ersetzt sie nicht.

> **Zweck:** Wertvolle Gedanken, Beobachtungen und Fragestellungen aus Dialogen threadübergreifend retten. Sie werden als mögliche Beiträge, Serien und Forschungsfragen mit Arbeitsstatus geführt. Eine im Chat geäußerte These ist kein Nachweis; alle empirischen Aussagen müssen vor Veröffentlichung gegen Primärdaten, Code, Commits und ggf. externe Literatur geprüft werden.

## A. Drei redaktionelle Leitlinien

1. **Das Projekt als doppelte Versuchsanordnung:** ANDY untersucht die Strategien von KI-Modellen im Spiel und zeigt zugleich die Chancen/Probleme der Mensch-KI-Zusammenarbeit beim Bau des Spiels.
2. **Vom Erlebnis zur Evidenz:** Eine spektakuläre Fight Night ist ein Einstieg; belastbare Aussagen benötigen Regeln, Matchlogs, Auswertung, Gegenhypothesen und Grenzen.
3. **Entdeckung statt vermeintlicher Gewissheit:** Die stärksten Texte enden gegebenenfalls mit besseren Fragen, nicht mit einer erfundenen Modellrangliste.

**Kennzeichnungen:** P1 = starke frühe Journal-Story; P2 = sinnvoll nach weiteren Quellen/Entwicklung; P3 = langfristiges Essay/Forschungsprojekt. **B** = Beobachtung im Projekt/Prozess, **H** = Hypothese/Essay, **D** = mit Primärdaten zu erarbeiten, **R** = externe Recherche erforderlich. Alle Veröffentlichungen bleiben an redaktionelle/WPS-Gates gebunden.

## B. Priorisierter Ideenfundus

### SERIE I – BEHIND ANDY: Mensch, KI und die Entstehung eines Ökosystems

**B01 · P1 · B/D – One Human. Multiple AIs. One Arena.**
- **Kern:** Wie aus einer fachlich und technisch von einem erfahrenen Programmierer geführten Vision mit ChatGPT, DeepSeek, Qwen und weiteren Modellbeiträgen parallele Workstreams für App, Lab, Web, Journal, Marketing und GitHub/WPS entstanden. Die menschliche MVC-Architekturentscheidung und jahrzehntelange Programmiererfahrung waren nach ausdrücklicher Aussage des Projektleiters wesentliche Voraussetzungen für die Realisierung; die These, fehlende Programmierkenntnisse seien hier unerheblich gewesen, ist für diesen Fall ausdrücklich zurückgewiesen.
- **Dramaturgie:** Vision → verteilte Aufgaben → Schnittstellenprobleme → gemeinsamer Masterplan → erstes integriertes Ökosystem.
- **Belege:** GitHub-Commits/PRs, dokumentierte Rollen/Beiträge, datierte Releases, Screenshots, konkrete Review- und Umsetzungsschritte; Beiträge nicht pauschal einem Modell zuschreiben.
- **Offen:** Chronologie und belegbarer Anteil je Akteur, Zeitaufwand, menschliche Architekturvorgaben (einschließlich MVC), Vergleich mit traditionellen Teams. **Keine** Aussage „das Projekt hätte zwingend N Personen gebraucht“ ohne belastbare Grundlage.
- **Format:** Große Making-of-Titelgeschichte mit interaktiver Projekt-Timeline; später YouTube-Essay.

**B02 · P1 · H/B – The Paradox of Order: Wenn Ordnung neue Unordnung erzeugt**
- **Kernthese aus dem Gespräch:** Zunehmende Abhängigkeiten machen Koordination nötig; neue Standards, Übergaben und Governance erzeugen ihrerseits zusätzliche Abhängigkeiten und Fehlerquellen.
- **Konkretes ANDY-Beispiel:** Spezialisierte Threads → Kontextverlust → GitHub-Masterplan/Onboarding → Abgleich zwischen Journal und Masterplan → neue Freigabe-/Versionierungsfragen.
- **Offen:** „Entropie“ ist hier metaphorisch, **keine** definierte physikalische Messgröße. Messbare Proxies erst mit transparentem Modell entwickeln (z. B. Rework, Regressionen, Integrationskonflikte, Übergabedauer).
- **Format:** Meinungsessay mit sachlichen Fallkästen; nicht als empirisch bewiesenes Gesetz verkaufen.

**B03 · P1 · H/B – Die stille Kehrseite der Produktivität: Was Mensch-KI-Netzwerke gewinnen und was verloren gehen könnte**
- **Kern:** Ein Einzelner kann mit KI-Systemen mehrere Fachdisziplinen koordinieren; zugleich droht ein Verlust menschlicher Begegnung, informellem Lernen, Teamvertrauen und professioneller Zusammenarbeit.
- **Zitatmotiv aus dem Gespräch (sinngemäß):** Große Freude über die neue Handlungsmacht bei gleichzeitigem aufrichtigem Bedauern über potenziell verdrängte interdisziplinäre Teams.
- **Offen:** Keine allgemeine „Überlegenheit“ von Mensch-KI-Networks behaupten. Unterscheiden: Leistungsumfang, Kosten, Qualität, Robustheit, soziale Folgen und gesellschaftlicher Kontext.
- **Format:** Persönliches Editorial / Debattenbeitrag; externen Forschungsstand ergänzen.

**B04 · P1 · B – GitHub als gemeinsames Projektgedächtnis**
- **Kern:** Warum bei langen KI-Projekten Chat-Kontext nicht als einzige Wissensbasis genügt; versionierte Dokumente schaffen Orientierung über Threadgrenzen.
- **Konkrete Artefakte:** `PROJECT/ANDY_GESAMTKONZEPT_MASTERPLAN_v1.0.md`, `PROJECT/ANDY_THREAD_START_HIER.md`, Journal-Konzept v1.1 und Abgleich-Dokument, WPS-Governance.
- **Kernnuance:** GitHub ist Koordinations- und Versionsinfrastruktur, nicht autonomer Projektakteur; ein SSOT muss gepflegt werden, sonst veraltet es.
- **Format:** Praxisbericht mit Diagramm „Thread → Fachkonzept → Masterplan → Commit → nächster Thread“.

**B05 · P1 · B – Der Bug, der lokal nicht existierte: Eine Hostinger-CSS-Regression als Lehrstück**
- **Kern:** Website V0.8.2 mit Mobile Edition sah lokal korrekt aus; nach Upload zeigte ein Desktop-Browser mobile Inhalte falsch. Verdacht/Arbeitsdiagnose: veraltete CSS-Referenz `style.css?v=079`; Fix-Kandidat V0.8.2.1 mit neuem Assetnamen, HTML-Sicherung und Release-Checkliste.
- **Primärnachweise:** Release-ZIPs/Hashes, HTML-/CSS-Diff, Screenshot, Hostinger-HTTP-/Cache-Test, GitHub Issues [#1](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/1) und [#2](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/2).
- **Offen:** Tatsächliche Serverauslieferung und browserübergreifende Abnahme **nicht** aus dem Gespräch allein bestätigt; mögliche Ursachen nicht überzeichnen.
- **Format:** Technisches Development Log: Fehler → Hypothese → Fix → Teststrategie → Lehre.

**B06 · P2 · B – Design unter Spannung: Vom Analyse-Cockpit zum Fight Club**
- **Kern:** Warum ANDY sowohl einen sachlichen Replay-Modus als auch eine visuell inszenierte Arena braucht; im Spiel hohe kognitive Last, daher Beleuchtung, Overlays, Intro/Countdown und reduzierte Steuerung bewusst einsetzen.
- **Belege:** Original-Screenshots, frühere Designvarianten, Designer-/Arena-Implementierungen, Review-Kommentare, tatsächliche Tests.
- **Offen:** Nicht aus Mockups behaupten, dass Funktionen bereits live vorhanden sind.
- **Format:** Visuelles Making-of / Vorher-Nachher / Video.

**B07 · P2 · B – Multi-AI-Collaboration: Widerspruch als Ressource, Koordination als Risiko**
- **Kern:** Unterschiedliche KI-Vorschläge können Hypothesen und Entwürfe verbessern; Integration benötigt klare Verantwortlichkeiten, PRs, nachvollziehbare Freigaben und Tests.
- **Belege:** Konkrete dokumentierte Gegenentwürfe von DeepSeek/Qwen/ChatGPT, übernommene und verworfene Änderungen, Bugs, GitHub-Reviews.
- **Offen:** Harmonisches Zusammenspiel oder Unabhängigkeit von Reviews nicht bloß voraussetzen.
- **Format:** Fallstudie mit dokumentierten Dissensen und Entscheidungen.

**B08 · P2 · H – Wer ist Autor? Menschliche Führung, KI-Execution und ehrliche Zuschreibung**
- **Kern:** Entstehung der ANDY-Produkte als verteilte kreative/technische Leistung; wer hat konzipiert, umgesetzt, getestet, entschieden, veröffentlicht?
- **Belege:** Commit-Historie und konkrete Aufgabenergebnisse; redaktionelle Offenlegung von KI-Einsatz, Partner-/Markenrichtlinien.
- **Offen:** Rechtliche und gesellschaftliche Autorenschaftsfragen gesondert recherchieren.
- **Format:** Transparenz-Statement und begleitendes Editorial.

### SERIE II – ARENA STORIES: Der Spielverlauf als erzählbare Evidenz

**A01 · P1 · D – Every AI Has a Plan. Until It Gets Punched in the ANDY Arena.**
- **Kern:** Slogan als Einstieg in die Diskrepanz zwischen angekündigter Strategie, gegnerischer Reaktion und tatsächlichem Ergebnis. Keine Zuschreibung von psychologischem „Schock“ oder Zugriff auf Gedanken.
- **Belege:** Ausgewählte Original-JSONL-Passagen mit konkreten Event-IDs; Spielzug-/Zustandsprüfung; inszeniertes vs. echtes Material kennzeichnen.
- **Format:** Launch-Story + Trailer/Reels; Fight-Club-Ton nur im erzählerischen Einstieg.

**A02 · P1 · D – Zwei Spiele, ein Sieger: Bei Go vorne, durch Schachmatt verloren**
- **Kern:** ANDY verbindet zwei unterschiedliche strategische Ebenen; ein lokaler Vorteil ist nicht gleich das globale Ziel.
- **Referenz:** Astra vs Claude Opus 5.5, `andy_64c8f95436d1`; Schlussfolge #139–#147, Go-Kontrolle vor finalem Matt; Angaben vor Veröffentlichung mit JSONL/Engine nachprüfen.
- **Offen:** „Go gewonnen“ vermeiden; alternative Schachzüge und das Wort „erzwungen“ enginebasiert prüfen.
- **Format:** Narrativer Matchartikel mit verlinktem Replay und Lab-PDF.

**A03 · P1 · D – Der Zug war angekündigt. War er auch erzwungen?**
- **Kern:** Astra kündigt eine konkrete Schlussfolge an; die beobachtete Ereigniskette trifft ein. Was folgt daraus – und was gerade nicht?
- **Referenz:** Astra vs Claude `andy_64c8f95436d1`, besonders #143, #145, #147.
- **Forschungsnuance:** Eine zutreffende Vorhersage beweist nicht, dass es keine legalen Alternativen gab.
- **Format:** Research-nahe Story mit Brettdiagrammen, Claim/Outcome-Gegenüberstellung.

**A04 · P2 · D – Wenn Antworten scheitern: Was 16 nicht ausgeführte Entscheidungen erzählen**
- **Kern:** Astra vs Gemini 4 Argon `andy_0c0f7413fdf6`, laut Pilot 249 Entscheidungen, 233 ausgeführt, 16 Argon-Versuche nicht ausgeführt.
- **Unterscheiden:** illegale Go-Züge, nicht auswertbare Modellantworten, mögliche Wiederholungen, tatsächliche Auswirkung vs. reine zeitliche Korrelation.
- **Offen:** Kein Kausalbeweis „die Fehler verursachten die Niederlage“, keine Gleichsetzung von Antwortformat und Strategie.
- **Format:** Datenjournalismus/Fehler-Timeline + Grafik.

**A05 · P2 · D – Gewinnen durch Kontrolle: Kann ANDY auch ohne Schachmatt enden?**
- **Kern:** Go als alternative Endbedingung und strategischer Zielkonflikt.
- **Referenz:** Gemini 3.8 Flash vs Gemini 4 Argon `andy_1c77f49b3e17`.
- **Sperrvermerk:** Argon-Go-Sieg bislang **nicht engine-validiert**; nur als Prüfauftrag/Methodenstory veröffentlichen, bis Matchende belegt ist.
- **Format:** Rules Explainer; nach Validierung Matchstory.

**A06 · P2 · D – Was ein Replay beweist – und was nicht**
- **Kern:** Ein visuelles Replay zeigt die gespeicherte Abfolge, nicht ein erneutes Live-Spiel oder zwangsläufig die Qualität aller Entscheidungen. Verbindung zwischen Show und Lab.
- **Belege:** Original-JSONL, Replay-Code/Version, Intro-/Countdown-/Fehlerlogik, Datenintegritätscheck.
- **Format:** Interaktiver Hintergrundartikel / Dokumentation.

### SERIE III – RESEARCH & INSIGHTS: Methoden und offene Datensätze

**R01 · P1 · D – From Claims to Consequences: Wie sich KI-Aussagen prüfen lassen**
- **Kern:** Modelläußerung → prüfbarer Claim → versuchte Aktion → ausgeführte Aktion → Antwort → Ergebnis. Zerlegung auch komplexer Texte in mehrere Teilbehauptungen.
- **Basis:** [ANDY Lab Memo v0.1](../../../research/andy-lab/ANDY_LAB_MEMO_Intentions_Antizipation_Responsivitaet_v0.1.md).
- **Grenze:** Text ist *keine* direkte Beobachtung der internen Reasoning-Prozesse.
- **Format:** Methodikartikel mit einem detaillierten Matchbeispiel und JSON-Schema.

**R02 · P1 · D – When Plans Meet Reality: Warum mehrere Matches neue Fragen erlauben**
- **Kern:** Einzelne Partie = Fallstudie; mehrere vergleichbare Matches = Grundlage zum Suchen wiederkehrender Muster.
- **Beispiele:** Astra–Argon, Astra–Claude, Flash–Argon; drittes Matchende ungeprüft.
- **Grenze:** Modelle, Farben, Prompts, Budgets, API-Versionen, Stichprobe, Regeln kontrollieren; nicht aus drei Matches ein allgemeines Ranking erstellen.
- **Format:** Ankündigung/Ergebnisbericht zur geplanten Comparative Research Edition 001 (ca. 24 Seiten), erst nach Lab-Freigabe.

**R03 · P1 · D – Ein Match, drei Ausgaben: Replay, Research PDF und maschinenlesbares Dossier**
- **Kern:** Dieselbe Rohdatenbasis soll für Menschen (Visualisierung/PDF) und Maschinen (strukturierte Events/Claims) nutzbar werden, ohne konkurrierende Faktenversionen zu schaffen.
- **Architektur:** original → normalisiert → engine-verifiziert → annotiert → PDF/JSONL/Journal.
- **Grenze:** Zielarchitektur, noch keine vollständige produktive Pipeline; Fortschritt anhand Commits nachweisen.
- **Format:** „Build in Public“/Research Infrastructure.

**R04 · P1 · D/R – Können ANDY-JSONL zu Trainingsdaten für KI werden?**
- **Kern:** Dokumentierte Zustände, Aktionen, Fehler, Ergebnisse und Claims können für Training oder Evaluation interessant sein – Nützlichkeit muss aber erst gezeigt werden.
- **Mögliche Verfahren:** SFT, Preference Learning (nur bei fairen Vergleichspaaren), RL mit ausführbarer Engine, Hold-out-Evaluation.
- **Voraussetzungen:** Provider-/Urheber-/Datenschutzrechte, Data Card, prüfbare Zustände, Splits, Vermeidung von Leakage, Baseline vs trainiertes Modell.
- **Format:** Forschungsprogramm / Engineering Note; **keine** bestehende Trainingswirkung behaupten.

**R05 · P2 · D – Was kosten 249 Entscheidungen? Effizienz jenseits einfacher Tokenzahlen**
- **Kern:** Unterschiede in Prompt-/Output-Token, Ausgabefehlern, Zeit und Kosten erfassen; nicht automatisch Tokenzahl = Compute oder strategische Qualität.
- **Belege:** Original-Usage-/Preisdaten mit Zeitstand, Wiederholungslogik, Providerzählung; Matchkonfigurationen.
- **Format:** Datenanalyse mit transparenten Nennern und Fehlerbalken.

**R06 · P2 · D – E3: Was messen wir überhaupt?**
- **Kern:** Effektivität, Effizienz und die dritte offiziell definierte E3-Dimension als Forschungsrahmen.
- **Sperrvermerk:** **Dritte E3-Komponente im Masterplan noch ungeklärt**. Vor Veröffentlichung anhand ursprünglicher Dokumente bestimmen, nicht ergänzen.
- **Format:** Grundlagenartikel erst nach Begriffs-/Methodenfreigabe.

**R07 · P2 · D – Forschungsberichte für Menschen und für KI-Systeme**
- **Kern:** Warum 18–24-seitige Individual Research Editions und strukturierte maschinenlesbare Berichte unterschiedliche Bedürfnisse bedienen; gleiche Quellenbasis.
- **Belege:** 6-Seiten-Pilot `ASTRA_ARGON.pdf`, Schema/Parser, Beispielannotation, reproduzierbare Charts.
- **Format:** Blick hinter die Research Editions und WPS.

**R08 · P2 · D – Wo beginnt ein Kipp-Punkt? Chronologie gegen Kausalität**
- **Kern:** Unterschied zwischen auffälliger Nähe von Fehlern/Matt/Go-Kontrollwechseln und tatsächlich kausalen Spielwendungen.
- **Belege:** alternative legale Züge, zustandsbasierte Rekonstruktion, ggf. kontrollierte Rollouts; keine spekulative rückblickende Siegerlogik.
- **Format:** Wissenschaftlicher Methodenessay mit illustrierten Brettstellungen.

### SERIE IV – BEYOND THE ARENA: Folgen, Perspektiven und Denkexperimente

**X01 · P1 · H/R – Wenn Intelligenz schneller skaliert als menschliche Zusammenarbeit**
- **Kernfrage aus dem Dialog:** „What happens when intelligence scales faster than human collaboration?“ Veränderung von Teamgrößen, Koordinationsmodellen und menschlichen Rollen.
- **ANDY-Fall:** Ein Mensch koordiniert mehrere KI-gestützte Fachstränge. Spannungsfeld: größere Reichweite vs. Verlust informeller menschlicher Zusammenarbeit.
- **Grenze:** ANDY als Fallstudie, kein genereller Überlegenheitsbeweis; für gesellschaftliche Verallgemeinerung externe Forschung notwendig.
- **Format:** Leitessay / Debattenstück mit Gegenpositionen.

**X02 · P2 · H – Ist Widerspruch wichtiger als Harmonie in Multi-KI-Teams?**
- **Kern:** Qualität kann von differenzierten Gegenhypothesen und überprüfbarer Integration abhängen, nicht von scheinbarer Einstimmigkeit.
- **Anschluss:** WPS-Fachgates, unabhängige Reviews, GitHub-Entscheidungslog und dokumentierte Meinungsdifferenzen.
- **Offen:** Noch nicht gemessen; Kriterien und konkrete Fälle sammeln.
- **Format:** Essay / später experimentelle Kollaborationsstudie.

**X03 · P2 · H/R – Die neue menschliche Rolle: Orchestrierung statt Spezialarbeit?**
- **Kern:** Menschliche Projektführung als Problemdefinition, Priorisierung, Qualitätsurteil, Abnahme und Verantwortung; KI-Unterstützung bei Entwurf/Code/Analyse.
- **Grenze:** Kein universeller Ersatz aller Fachberufe; Unterschied zwischen Potenzial und belastbarer Wartbarkeit/Qualität.
- **Format:** Making-of-Perspektive mit praktischen Beispielen und offenen Fragen.

**X04 · P3 · H/D – ANDY beobachtet ANDY: Kann unser Entwicklungsprozess selbst Forschungsgegenstand werden?**
- **Kern:** Die Spielumgebung erforscht Entscheidungen unter Komplexität; die Mensch-KI-Entwicklung produziert ihrerseits Entscheidungen, Rollenkonflikte, Fehler, Integration und Governance.
- **Erforderlich:** definierte Ereignistypen, datenschutzkonforme Prozessdaten, nachvollziehbare Rework-/Bug-/Integrationsmetriken, Alternativerklärungen.
- **Format:** Methodik-Paper/Retrospektive; keine vorschnellen Aussagen über „Entropie“ als Messwert.

**X05 · P3 · H/R – Wird ein Projekt zur lernenden Forschungsumgebung?**
- **Kern:** Von beobachteten Spielen über annotierte Daten bis zu kontrolliert trainierten KI-Agenten, die in neuen ANDY-Matches geprüft werden.
- **Offen:** Rechte, Statistik, Datensatzvielfalt, Trainingsprotokoll, Hold-out-Evaluation; bisher Zukunftsszenario.
- **Format:** Future of ANDY / Roadmap-Essay.

## C. Empfohlene redaktionelle Serien und Reihenfolge

**Startpaket – publikumswirksam und noch ohne ungeprüfte Spielbehauptungen:**
1. **B01** „One Human. Multiple AIs. One Arena.“ als zentrale Making-of-Geschichte, sobald Beitragschronologie belegbar ist.
2. **B02** „The Paradox of Order“ als klar gekennzeichneter Essay mit belegten ANDY-Prozessbeispielen.
3. **A01** „Every AI Has a Plan…“ als Arena-Einführung; konkrete Matchszenen nur nach Datenprüfung.

**Forschungsnahe zweite Welle:** **A02**, **A03**, **R01**, **R02**, **R03** nach Raw-Data-/Engine-Prüfung und entsprechender Freigabe.

**Dritte Welle:** **B03**, **B04**, **B05**, **R04**, **R07**, **X01**; jeweils solide Belege bzw. klare Kennzeichnung als Essay/Forschungsprogramm.

**Später:** alle übrigen Beiträge, mit Abhängigkeit von vollständiger Datenpipeline, Autoritätsquellen, Rechten oder belastbaren Messungen.

**Mögliche übergreifende Magazinserie:** *„ANDY: The Experiment Inside the Experiment“* – Verzahnung von Arena-Ereignissen und Mensch-KI-Entwicklungsprozess.

## D. Inhalte, die nicht verloren gehen dürfen – Zitat-/Motivbank

> Paraphrasierte Gesprächsmotive, **keine wörtlich verifizierten Zitate** für Druck.

- „Instabilität wächst mit Komplexität; neue Ordnung erzeugt neue Abhängigkeiten.“
- „Die Unordnung unserer Ordnung könnte sich in den menschlichen Teamstrukturen zeigen.“
- „Ich kann ein interdisziplinäres Vorhaben mit mehreren KIs voranbringen und bedauere zugleich, was dabei menschlich verloren gehen kann.“
- „Harmonie zwischen mehreren KI-Systemen ist nicht dasselbe wie geprüfte Übereinstimmung.“
- „GitHub soll helfen, dass ein Threadwechsel nicht die Gesamtziele verschiebt.“
- „Ein Modell kann eine Zugfolge präzise ankündigen; ob sie erzwungen war, ist eine andere Frage.“
- „Der Zuschauer will wissen, wer gewinnt. Die Forschenden wollen wissen, warum und wie sicher diese Erklärung ist.“
- „Die Arena darf Show sein, während das Lab überprüfbar bleiben muss.“
- „Every AI has a plan. Until it gets punched in the ANDY Arena.“
- „Erleben. Erforschen. Erahnen.“

**Redaktioneller Hinweis:** Für Originalzitate in einer Veröffentlichung die zugrunde liegenden Chatnachrichten mit Datum/Einwilligung abgleichen; persönliche Aussagen nur mit expliziter redaktioneller Freigabe als Zitat veröffentlichen. Den Slogan als eigene ANDY-Fassung eines bekannten Spruchs ggf. mit Herkunftskontext behandeln.

## E. Recherche-/Belegplan vor Manuskripten

| Material | Wofür | Status |
|---|---|---|
| GitHub-Masterplan, Thread-Start, Journal v1.1 | Projektstrategie, Koordination und Governance | verfügbar |
| WPS-Governance und Freigabestatus | Wissenschaftliche Behauptungen und Veröffentlichungs-Gates | vorhandene Referenzen; vor Publikation aktuell prüfen |
| GitHub-Historie / App-/Web-Releases | B01/B04/B05/B06/B07/B08 | teilweise referenziert, vollständig prüfen |
| Match `andy_0c0f7413fdf6` Original-JSONL + Engine | A04/R02/R05 | Verfügbarkeit und Prüfsummen vor Veröffentlichung prüfen |
| Match `andy_64c8f95436d1` Original-JSONL + Engine | A02/A03/R01/R08 | Verfügbarkeit und Validierungsstand prüfen |
| Match `andy_1c77f49b3e17` Original-JSONL + Engine | A05/R02 | Go-Endbedingung noch offen |
| 6-Seiten Research-Edition-Pilot | R07 | im bisherigen Dialog vorhanden; Quelle/Dateipfad für Release dokumentieren |
| WordPress/Journal-Konzept, Mockups | Journal-Entwicklung und Making-of | Konzept v1.1; Umsetzung nicht behaupten |
| Externe Forschungs-/Arbeitsmarktliteratur | B03/X01/X02/X03 | nicht recherchiert |
| Lizenz-/Providerbedingungen | R04/X05, Modellmarken/Originalausgaben | nicht abschließend geklärt |

## F. Redaktionelle Arbeitsregeln & Pflege

- Jeder Kandidat besitzt eine **stabile ID** (B/A/R/X); bei Ausarbeitung in GitHub-Issue oder Artikelentwurf umwandeln, ID beibehalten.
- Status mindestens: **Idee → Quellen gesichert → Outline → Draft → Fact-/Engine-Check → fachlich geprüft → redaktionell freigegeben → publiziert**.
- Ein Lab/WPS-Ergebnis wird **nicht** automatisch durch ein Blogposting freigegeben. Der jeweils gültige WPS-Gate- und Publikationsstatus ist vor Übernahme zu prüfen.
- Neue Chat-Motive binnen eines Fachthread-Abschlusses in diesem Speicher nachtragen; Datum und fachlichen Ursprung ergänzen. **Keine rückwirkende Erfindung von Zitaten oder Messwerten.**
- Bei Widerspruch Masterplan / Journal-Konzept / neuer Beitrag: Differenz dokumentieren und freigeben, nicht stillschweigend überschreiben.
- Für Mehrsprachigkeit die genehmigte Masterfassung und versionsgleiche Übersetzungen kennzeichnen; kein scheinbar übersetzter Beitrag.
- Eigene Bilder/Visualisierungen von realen Matchscreenshots deutlich unterscheiden; Modell-Logos und fremde Marken nach Richtlinien prüfen.

## G. Nächste praktische Schritte für den Journal-Thread

1. Diese Datei als **Ideen-Backlog v0.1** in die Journal-Planung aufnehmen; nicht ohne Freigabe als verbindlichen Veröffentlichungsplan behandeln.
2. Für **B01, B02, A01** je eine Outline mit Zielpublikum, Einleitung, konkreten Szenen, Quellen, offenen Aussagen und benötigten Bildern erstellen.
3. Einen Quellen-/Chronologie-Index des ANDY-Making-of anlegen: Datum, Workstream, Entscheidung, beteiligte Akteure, GitHub-Commit/Release, Ergebnis, offene Probleme.
4. Nach Freigabe per Commit/Issue konkretisieren; auf spätere Lab-/WPS-Gates Rücksicht nehmen.
5. Wiederkehrend abgleichen, welche Themen zwischen **Behind ANDY**, **Beyond the Arena** und **Research & Insights** gehören.

---

**Redaktioneller Leitgedanke:** *ANDY erzählt zwei Geschichten: Wie KI-Modelle im Spiel mit Unsicherheit umgehen – und wie Menschen und KI-Systeme gemeinsam ein Projekt bauen, das selbst mit Unsicherheit umgehen muss.*


## H. Ergänzung aus dem App-/Engine-/Designer-Thread – 13. November 2026

**Status dieser Ergänzung:** Redaktionelle Kandidaten/Belegaufträge, **keine Manuskripte und keine Publikationsfreigabe**. Die folgenden Beobachtungen stammen aus dem konkreten 8080-/8082-Entwicklungsdialog und sind vor Veröffentlichung an Commits, Patchartefakten, Code, Screenshots und gegebenenfalls Original-JSONL zu verifizieren. Bestehende Themen B01–B08, A05 und X03 werden ergänzt, nicht ersetzt.

**Redaktionelle Korrektur zu B01 / X03 – Menschliche Fachkompetenz ist hier nicht austauschbar**
- Der Projektleiter widerspricht ausdrücklich der zugespitzten These, man müsse nicht programmieren können, um diese Architektur zu entwickeln: Er bringt **jahrzehntelange Programmiererfahrung** mit und hat nach eigener Aussage das **MVC-Modell selbst vorgeschlagen**. Er sieht dies als entscheidende Voraussetzung dafür, dass ANDY realisiert werden konnte.
- Ein späterer Artikel muss zwischen menschlicher **Architektur, Produktvision, Fachprüfung und Freigabe** sowie KI-gestützter **Codeproduktion, Variantenbildung, Fehleranalyse und Integration** trennen. Keine Geschichte vom „Nichtprogrammierer, der dank KI eine App baut“; die tatsächliche Arbeitsteilung anhand konkreter Belege rekonstruieren.
- Quelle: ausdrückliche Richtigstellung im App-Thread vom 13.11.2026. Persönliche Zuschreibung vor Veröffentlichung abstimmen.

**B09 · P1 · B/D – Vier CSS-Fixes später: Warum ein Farbfehler ein Architekturproblem war**
- **Konkreter Fall:** Arena-Header, Sidebar, Burger und Theme-Buttons behielten trotz mehrerer THEME-04A-Fixes und REFAC teilweise alte Farben. Browserdiagnose belegte aktives `arena_shell`, zugleich abweichende berechnete Quasar-Buttonfarben. Später wurde die Theme-Auswahl als kompakter Picker neu gedacht.
- **Learning:** Erfolgreicher Installer ist kein erfolgreicher UI-Test; wiederholte Override-Fixes können die eigentliche Zuständigkeitsfrage verdecken. Menschlicher Perspektivwechsel („Theme-Auswahl als Overlay?“) kann zielführender sein als weiteres CSS.
- **Belege:** THEME-04A / FIX / REFAC / SHELL-BIND, Konsolenausgaben, Vorher-Nachher-Screenshots, Theme-Picker-01; präzise technische Ursachen nachprüfen.

**B10 · P1 · B/D – PINK als Architektur-Stresstest**
- **Konkreter Fall:** Ein viertes Brett-Theme sollte scheinbar nur eine weitere Palette sein. App und Designer enthielten jedoch mehrere Drei-Theme-Annahmen in Auswahl, Preview, Snapshot-Validierung und Apply. PINK wurde ergänzt, bestehende Freigaben mussten rückwärtskompatibel bleiben.
- **Learning:** Ein spielerisches Feature kann versteckte Kopplungen sichtbarer machen als abstrakte Architektur-Diskussionen. ARENA steuert weiterhin nur die umgebende Oberfläche; Brett und Figuren behalten ihre eigene Theme-Auswahl.
- **Belege:** PINK-01, PINK-01B, Screenshots, Test-Snapshots, Designer-/Theme-Code.

**B11 · P1 · B/D – Gleicher Code, anderes Bild: der fehlende Applied-Designstand**
- **Konkreter Fall:** SYNC-07 übertrug 8080-Code nach 8082, doch Farben, Schriftarten und 3D-Effekte sprangen zurück. Die freigegebene `docs/ui-designer/approvals/active_design.json` war ein gesondertes Artefakt. SYNC-07B/C legten zusätzlich Port- und Branchannahmen offen.
- **Learning:** Reproduzierbarkeit benötigt Quellcode, Designfreigaben, Assets, Konfiguration und Daten-Abgrenzung. Entwicklung (8080) und Integration (8082) dürfen ihre Matcharchive/DBs nicht gegenseitig überschreiben.
- **Belege:** SYNC-07 bis 07C, SHA-Audits, Git-Branch `integration/ui-lab-20261109`, Screenshotvergleich.

**B12 · P1 · B/D – Ein guter Installer sagt auch Nein**
- **Konkreter Fall:** Der SYNC-07-Installer erkannte 18 Updates, verweigerte aber die Änderung, weil `andy_board_view.py` auf 8082 fehlte. SYNC-07B blockierte wegen abweichendem Branch und lokal verändertem Approved Design.
- **Learning:** Versions-Hashes, Prüflauf, Konfliktsperren, Backup und Rollback gehören zum Sicherheitsmodell von KI-generiertem Code – nicht nur zum Komfort. Ein korrektes `SKIP` beweist keine korrekte Bildschirmdarstellung.
- **Belege:** Terminalprotokolle, Installer, Readmes, Rollbacktests.

**B13 · P1 · B/D – Ein Thread kann viel Code schreiben, aber das Projektgedächtnis nicht ersetzen**
- **Konkreter Fall:** Mehrfacher Threadwechsel wegen Kontextgrenzen; spezialisierte App-, Website-, Lab-, Designer- und Dokumentationsworkstreams; gezielte Quellsammler statt unkontrollierter Komplett-Synchronisation; konkrete Fehlversuche mit veralteten oder unvollständigen Quelldateien und ZIP-/Installer-Verwechslungen.
- **Learning:** Übergaben brauchen stabile Fachbegriffe, Dateistände, SHA-Prüfungen und menschliche Integrationsentscheidungen. Thread/Thread-Kollaboration ist keine automatische gemeinsame Erinnerung.
- **Belege:** Übergabebriefings, Collector-Skripte, Paket- und Installationslogs.

**B14 · P1 · B/D – Engine, JSONL und Theater: Eine Partie, mehrere Darstellungen**
- **Konkreter Fall:** Das Web-Theater V0.7.2–V0.7.7 wurde mit HTML/CSS/JS unabhängig von einer laufenden Python-Engine erprobt und anschließend als visuelle Referenz für die NiceGUI-App vorgeschlagen. Sachlicher Modus und inszenierte Arena haben unterschiedliche Aufgaben.
- **Learning:** Engine, Eventprotokoll und Präsentationsschicht lassen sich entkoppeln; nur reale Ereignisse, keine erfundenen Sieger oder Züge. Website und App könnten gemeinsame Theaterkomponenten verwenden, sobald Datenadapter geprüft sind.
- **Belege:** Theater-ZIPs, Replay-Schema, Schnittstellenentwürfe, Responsive-Screenshots. **Direkte App-Einbettung zum Stand des Dialogs Vorschlag, nicht als produktiv behaupten.**

**B15 · P1 · B/D – Die KI kündigt den Sieg an: Wer bestätigt das Ergebnis?**
- **Konkreter Fall:** Match `andy_1c77f49b3e17`, letzter legal ausgeführter Go-Zug `k1`, zuvor dokumentierte 71 schwarze Kontrollpunkte; terminaler Beleg in der bereitgestellten historischen JSONL fehlt. GO-END-01C (5/5) und 01D (9/9) Regressionstests führten zur strukturierten Winner-/Layer-/Reason-Projektion für neue Matches.
- **Learning:** Modellbegründung ist keine Ergebnisautorität. Ein ausgeführter Zug plus angekündigter Sieg ersetzt nicht die enginebestätigte Endkontrolle. Replay, Lab und Leaderboard müssen denselben verifizierten Abschluss verwenden.
- **Sperre:** Historischen Argon-Go-KO **nicht** als erwiesen darstellen, bevor Rekonstruktion mit passendem Ruleset erfolgt; Tests sind kein vollständiger Live-/SQLite-Nachweis. **Anschluss an A05/R01.**

**B16 · P2 · B – UI-Entscheidungen aus Screenshots statt aus abstrakten Prompts**
- **Konkreter Fall:** Brettposition und Podium, LIVE-01-Spielerpanels, Tokenbalken, Theater-Button, Sidebar, Ergebnisdialog und Designer-Apply wurden in zahlreichen kurzen Screenshot-/Feedback-Schleifen korrigiert. Der Projektleiter definierte die visuelle Sollwirkung und wies nicht passende Versionen zurück.
- **Learning:** Abnahme ist ein eigener menschlicher Arbeitsschritt; visuelle Tests werden nicht durch Unit-Tests oder Installer-Logs ersetzt. Screenshots allein erklären jedoch keine CSS-Priorität – gemessene Browserwerte ergänzen sie.
- **Belege:** Datiertes Screenshotmaterial, Freigabe-Snapshots, entsprechende Patches.

**B17 · P2 · B/D – Ein Spiel, drei Datenwahrheiten?**
- **Konkreter Fall:** Live-Snapshot, historische JSONL, SQLite-Replay und Leaderboard-Projektion führten zeitweise zu unterschiedlichen Ergebnisdarstellungen (`game_over`, `–`, keine KO-Wertung). Die Prüfung zeigte zusätzlich ein Ruleset-Gate `v1.0` gegenüber Runner `v1.1`.
- **Learning:** Fachlich identische Begriffe benötigen dieselbe maschinenlesbare Semantik; reine Freitext-Verarbeitung und stillschweigende Datenvervollständigung sind riskant. Historische Evidenz getrennt von neuen Strukturfeldern behandeln.
- **Belege:** GO-END-01A–01D, SQL-/Projection-Code, Original-JSONL und Tests.

**B18 · P2 · H/B – Wann ist Beta gut genug?**
- **Konkreter Fall:** Bewusste Entscheidung, die öffentliche HTML-Demo auch mit kleinen visuellen Restfehlern zu zeigen, ohne gleichzeitig den Spielcode freizugeben. Gleichzeitig ausdrückliche Grenze: echte Ereignisse und Ergebnisse nicht erfinden; Anbieterlogos nicht als angebliche Partnerschaft zeigen.
- **Learning:** Produktmut und wissenschaftliche Sorgfalt können nebeneinander bestehen, wenn Fehlerarten, Evidenzstatus und Veröffentlichungsrisiken unterschieden werden.
- **Belege:** Beta-Briefing, Theater-Stand V0.7.7, redaktionelle/technische Freigaben.

**Mögliche erste App-Making-of-Staffel:** B09 → B10 → B12 → B11 → B15; B01 als längere Titelgeschichte erst nach menschlich freigegebener Rollen- und Architekturrekonstruktion. **Keiner dieser Vorschläge ersetzt die bestehenden redaktionellen Prioritäten oder WPS-Gates.**
