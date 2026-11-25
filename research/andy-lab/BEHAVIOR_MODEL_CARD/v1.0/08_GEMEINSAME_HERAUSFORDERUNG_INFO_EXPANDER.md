# 08 — Gemeinsame Herausforderung: kontextueller Info-Expander auf jeder Model Card

**Produktänderung 25.11.2026. Status:** dokumentierte Anforderung, kein bereits eingebauter HTML-/WordPress-Renderer.  
**Platzierung:** unmittelbar nach Titel/Intro des jeweiligen eigenständigen Modellprofils, **vor den Kennzahlen/Evidenzkompass** (oder in unmittelbarer Nähe, ohne die KPI-Ansicht unnötig zu verdrängen). **Ein universeller, aufklappbarer DE/EN-Einführungstext**, nicht für jedes Modell neu erfunden.

## Warum dieser Expander?

Die Behavior Card zeigt **eine Folge realer Beobachtungen eines Modells**. Neue Leser brauchen zunächst eine übergreifende Antwort:
- Warum lässt ANDY *allgemeine KI-Modelle* (GPAI im breiten Produktverständnis) überhaupt Schach und Go kombiniert spielen?
- Was ist an der gemeinsamen Aufgabe neu/ungewohnt, und worauf mussten sie reagieren?
- Was bedeuten **vergleichbare Vorgaben** – und warum behaupten wir keine identischen effektiven Bedingungen oder gesicherten gleichen Vorwissen?
- Was ist die sachliche Analogie zum Einsatz von allgemeinen KI-Modellen in Unternehmen, ohne Spielleistungen als direkt nachgewiesene Business-Qualität zu verkaufen?
- Wie hängen Model Card, echte Partie, Lab, Spielregeln und AQP zusammen?

**Begriffe präzisieren:** Die im ANDY-Dossier erwähnten „allgemeinen KI-Modelle“ sind nicht automatisch eine formale juristische Einstufung als GPAI nach einer bestimmten Regulierung. In der Arena existieren zudem spezielle Test-/Referenzakteure; nicht jeder beliebige Arena-Akteur ist ein allgemeines KI-Modell. Die Standarderklärung gilt für entsprechende allgemeine Modell-Card-Profile, nicht blind für spezialisierte Engines oder Zufallsreferenzen.

## UX-Spezifikation / BMC-EXP-01 (Must)

**Geschlossener Zustand (Standard):** ein einzelner, gut sichtbarer, nicht dominanter Expander, z. B.
- **DE:** „Warum ANDY? Die gemeinsame Herausforderung für allgemeine KI“
- **EN:** “Why ANDY? A shared challenge for general-purpose AI”
- Optional eine knappe Subline: „Neue Aufgabe · gleiche Grundregeln · dokumentierte Bedingungen“.

**Geöffneter Zustand:** zwei bis vier kurze Absätze und drei bis fünf **verifizierte Dokumentationslinks**, keine wissenschaftliche Langabhandlung. Responsive, keyboard-/screenreader-fähig (native `details/summary` oder semantisch äquivalent, `aria-expanded`, Fokuszustand). Ohne JS verständlich; vor allem kein Akkordeon, das die gesamte Card permanent abdeckt.

**Globaler Inhalt statt Modellkopie:** Inhalt 1× pro Sprachfassung im bestehenden WordPress-Content-/WHY-System verwalten; jede Card referenziert dieselbe versionierte Redaktionskomponente. KEINEN Modellvergleich, keine Rangstatistik und keine automatisch aus API-Daten erzeugten allgemeinen Behauptungen. A/B-Tests oder Lokalisierung verändern nicht historische Match-Snapshot-Kennzahlen. Wenn der Text wesentlich revidiert wird, Fassung/versioniertes Veröffentlichungsdatum berücksichtigen.

**Zusammenspiel mit vorhandenen UI-Elementen:**
1. Universal-Expander **„Warum ANDY?“**: gemeinsame Testidee, Doku, Business-Brücke.
2. Eigene Modellkennzahlen und **Evidenzkompass**: Anzahl Spiele, Stabilitätsaussage nur mit belastbarer Kohorte, Zeit-/Kostenabdeckung.
3. Pro Card/Match eigener Bereich **„Versuchsbedingungen & Originale“**: konkrete Regeln, Quellen, Prompt-/Strategieversion, Budget, API-Route/Version (soweit belegt), Zeit, Rollen, Links. **Nicht** dieselbe Metainfo in den Universalkasten kopieren.

## Vorschlag für den deutschen Standardtext (redaktionell abnehmbar)

**Warum treten hier allgemeine KI-Modelle an?**

ANDY verbindet Schach und Go zu einer eigenständigen, dynamischen Spielaufgabe. Allgemeine KI-Modelle müssen die bereitgestellten Regeln und Spielzustände verstehen, gültige Aktionen erzeugen, ihre Entscheidungen anpassen und mit den vorgegebenen Ressourcen haushalten. Sie nutzen dafür ihre allgemeinen Fähigkeiten sowie die Werkzeuge, die ihnen in der konkreten Spielkonfiguration tatsächlich zur Verfügung stehen.

Die Herausforderung ist **im Regelrahmen gemeinsam**, aber das bedeutet **nicht**, dass Modelle dasselbe Vorwissen, dieselben internen Verfahren oder identische technische Bedingungen haben. Token- und Zeitbudgets, Ausgabegrenzen, Prompt-/Strategieeinstellungen, Modelle/Versionen, Provider-Routen und erlaubte Werkzeuge können variieren. Wir dokumentieren die Voraussetzungen jeder Partie, statt die Ergebnisse als allgemeine Rangfolge zu interpretieren. Dass ein Modell ANDY zuvor nie gesehen oder trainiert hat, lässt sich aus dem Spielprotokoll allein **nicht beweisen**.

Die Parallele zum Unternehmensalltag ist eine **Forschungsfrage**: Auch dort sollen allgemeine KI-Systeme bislang nicht individuell eingeübte Aufgaben anhand neuer Vorgaben bearbeiten, mit ihrem verfügbaren Werkzeugkasten handeln, Unsicherheiten bewältigen und bei veränderten Bedingungen reagieren. **ANDY misst nicht unmittelbar betriebliche Eignung.** Die Model Card zeigt zunächst, was dieses Modell unter den dokumentierten ANDY-Bedingungen tatsächlich getan hat.

**Die Partien, Regeln, Ressourcen und Quellen** lassen sich über die Verweise und Matchdetails der Card nachvollziehen.

### English editorial equivalent (draft)

**Why do general-purpose AI models compete here?**

ANDY combines chess and Go into a distinct, dynamic task. General-purpose AI models must interpret the provided rules and game state, produce executable actions, adapt their decisions and manage limited resources. They rely on their general capabilities and on whichever tools are actually available in a specific match configuration.

The challenge has a **shared rule framework**, but this does **not** imply identical prior knowledge, internal methods or technical conditions. Budgets, output limits, prompts, model versions, provider routes and permitted tools may differ. Each match records its conditions. The logs alone cannot prove that a model has never encountered or been trained on ANDY before.

This suggests a **research analogy** to business: general-purpose AI systems are also asked to solve unfamiliar, not individually rehearsed tasks under specific constraints using the tools available to them. **ANDY results are not direct evidence of business fitness.** This card documents how one model behaved in real ANDY games under stated conditions.

Explore the match details, methodology and documentation below.

## Dokumentations-Links / Vorschlag

Öffentlicher DE-Einstieg (vom Nutzer angegeben, Query-Variante ohne überflüssiges `?`):
1. **[Was ist ANDY? – Einführung](https://andy-arena-com.github.io/andy-wps-collaboration/andy-dokumentation-regeln-lab.html#intro)**
2. **[Regeln: gekoppeltes Schach & Go](https://andy-arena-com.github.io/andy-wps-collaboration/andy-dokumentation-regeln-lab.html#rules)**
3. **[Das ANDY Lab und seine Interpretation](https://andy-arena-com.github.io/andy-wps-collaboration/andy-dokumentation-regeln-lab.html#lab)**
4. **[Komplexität und allgemeine KI-Modelle](https://andy-arena-com.github.io/andy-wps-collaboration/andy-dokumentation-regeln-lab.html#challenge)**
5. **[ANDY-Score & AQP: gleiche Qualifikationsregeln, ungleiche Matchzahl](https://andy-arena-com.github.io/andy-wps-collaboration/andy-dokumentation-regeln-lab.html#score)**

**Quellprüfung:** Die Kapitel und IDs `intro`, `rules`, `lab`, `challenge` und `score` stehen in der Repo-Quelldatei [docs/andy-dokumentation-regeln-lab.html](../../../../docs/andy-dokumentation-regeln-lab.html); die öffentlich publizierte GitHub-Pages-URL wurde im vorliegenden Toolzugriff **nicht erfolgreich geladen**, deshalb externe Navigation/Anker vor WP-Release im Browser E2E prüfen. **Beta Doku V0.9** – Änderungen möglich. Bei DE/EN-Switch ggf. EN-Vorschau [docs/andy-documentation-en.html](../../../../docs/andy-documentation-en.html) verwenden, URL und Kapitelanker getrennt verifizieren. Ungeprüfte Übersetzungs-/Ankerziele nicht frei erfinden.

Links sollen sich optional auf drei Hauptverweise „Einführung · Spielregeln · Mehr zur Forschung“ reduzieren lassen; die weiteren zwei können in einer sekundären „Doku öffnen“-Zeile folgen.

## Evidenzgrenzen und inhaltliche Guardrails

- **Gleiche Herausforderung ≠ exakt gleiche Versuchsbedingungen.** Unterschiedliche Konfigurationen bleiben sichtbar und können Verhaltensunterschiede begründen, ohne kausalen Nachweis.
- **Neue/unbekannte Aufgabe ist eine didaktische Aufgabenbeschreibung, kein belegter Neuheitstest.** Kein behauptetes „definitiv niemals im Training gesehen“ oder „keinerlei Vorwissen“.
- **Allgemeine Fähigkeiten/zugelassene Werkzeuge** ist nicht gleich unbegrenzter Internet- oder Toolzugriff; die konkrete Toolfreigabe pro Match benennen.
- **AQP:** Gleiche Qualifikationsregeln bedeuten nicht, dass alle Modelle die gleiche Zahl Partien absolvieren. Latenz/Kosten/Fehler können Tests begrenzen; ein pausiertes Modell ist nicht automatisch als grundsätzlich schlechter bewertet.
- **Business-Bezug:** Methodische Analogie, nicht direkte Transfer- oder Leistungsbehauptung und nicht statistisch validierte Business-Fitness. Unternehmen bringen andere Risiko-, Fehler-, Governance-, Kompetenz- und Integrationsbedingungen mit.
- **Keine stillen Widersprüche** zum universellen Card-Prinzip: Das Modellprofil bleibt standalone, keine Gegenüberstellung von Modellkennzahlen, keine Rankings, keine pauschalen „KI kann ...“-Sicherheitsversprechen.
- Offenheitsstatus und Dokumentation nach bestehenden Regeln: BEOBACHTET / BERECHNET / INTERPRETIERT / OFFEN; dokumentierte Eigenaussagen sind nicht verborgene Denkprozesse.

## Tests / BMC-T26 bis T29 (ergänzend zum bestehenden Testkatalog)

- **BMC-T26:** Jede veröffentlichte allgemeine KI-Model Card zeigt den universellen DE-/EN-Expander vor/bei den KPIs; initial geschlossen; mobile und tastaturbedienbar; `details`/Focus/SR-Beschriftungen funktionieren.
- **BMC-T27:** Inhalt wird zentral redaktionell gepflegt und in beiden Sprachen konsistent verteilt, ohne Standalone-Modellmetriken, Match-Snapshots oder einzelne Übersetzungsseiten gegenseitig zu überschreiben; Legacy-Cards erhalten ihn nach Upgrade.
- **BMC-T28:** Verifizierte Doku-Links und Hash-Anker führen in den richtigen Bereich; fehlender/veralteter Link wird nicht als funktionsfähig ausgegeben; externe URLs sind sicher escaped; separate Staging-/Live-/EN-Tests.
- **BMC-T29:** Universalkasten enthält keine unbewiesene Aussage „garantiert neu/nie trainiert“, „alle Bedingungen sind identisch“ oder „ANDY beweist betriebliche Eignung“; spezialisierte Referenz- und Zufallsakteure erhalten keinen irreführenden GPAI-Einleitungstext.

## Source of truth und Implementierungsgrenzen

**Redaktionell:** globaler wiederverwendbarer WordPress-Baustein mit DE/EN und Release-Version, im bestehenden Composer/WHY-CMS nach Ist-Audit.

**Faktisch:** APP-JSON-Export enthält weiterhin nur model-/matchspezifische Fakten und Evidenz. **Keine zusätzliche Modell-/Match-Interpretation im universellen Text**, keine Verdoppelung von Daten über jede Card.

**Implementierungsstatus:** derzeit nur dokumentiert, nicht in den HTML-V1-Clickdummy eingebaut und nicht als WordPress-Plugin installiert. Bestehende Staging-/Launch-Control-Freigabegates bleiben gültig.
