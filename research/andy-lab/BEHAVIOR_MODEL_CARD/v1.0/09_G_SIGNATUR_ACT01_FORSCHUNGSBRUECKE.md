# 09 — ANDY g-Signature: ACT 01 → Behavior Model Card → Signature-informed Adaptation

**Datum:** 26.11.2026  
**Status:** Explorative Forschungs-/Designbrücke und Anforderungen für einen möglichen Folgeprototyp. **Keine** empirisch validierte Behavior-Signature, **kein** produktiver Export/Renderer und **kein** belegter Nutzen für Strategiewahl oder Spielausgänge.

## 1. Originalbezug: Das „Logo“ ist der vollständige Netzwerktyp g = K₄

ANDYs graphische Identität entsteht aus vier Knoten und sechs paarweisen Beziehungen. Jeder Knoten ist mit allen drei anderen verbunden; die gezeichnete Innenposition ist graphentheoretisch nicht privilegiert. Die **Topologie bleibt K₄**; Positionen, Knotengrößen, Farben und Kantenstärken können Zustände **repräsentieren**, ohne die zugrunde liegende Vollständigkeit der sechs Kanten zu ändern.

Quelle: **Nutzerseitig eingebrachtes PDF** `ANDY_ACT01_A_Whitepaper_v1.2 (1).pdf`, *Die Sprache der Netzwerke*, Version 1.2 / November 2026, 21 S., Abschnitt „ANDY: ein adaptiver Netzwerktypus“ (S. 3), „Reflex und Reflexion“ (S. 4), „Identität durch Veränderung“ (S. 5). Dieses angehängte PDF ist **nicht durch dieses Dokument als öffentliches GitHub-Artefakt archiviert**; für einen öffentlichen Quellenlink zuerst Ziel und Rechte freigeben.

### Ursprung der vier funktionalen Rollen (ACT 01)

Die im Whitepaper vorgeschlagene konzeptionelle Zuordnung lautet:
- `I1`: erster Input
- `I2`: zweiter Input
- `R`: Vergleich/Reflexion
- `O`: Output

Sechs Relationen in `K₄`: `I1-I2`, `I1-R`, `I2-R`, `I1-O`, `I2-O`, `R-O`. Im Whitepaper sind dies **mögliche funktionale Beziehungen**, noch keine validierten Messkanäle oder nachgewiesenen inneren Verarbeitungskomponenten eines proprietären KI-Modells. Direkte Pfade und Vermittlung werden als Hypothesen über Reflex/Reflexion diskutiert.

**Folge:** Eine Signature mit späteren Rollen wie „Vorgaben / Ankündigung / Execution / Folgen“ wäre eine **neue, versionierte Anwendungssemantik**, nicht die unveränderte ACT-01-Rollendefinition. Nicht heimlich gleichsetzen.

## 2. Was die ACT-01-Versuche bereits tragen

Die vereinbarte **visuelle Lesesprache** (S. 6, 20) definiert vier diskrete Parameter:
- `P` Innenknotenposition 0/1/2,
- `S` Innenknotengröße 0/1/2,
- `C` Innenknotenfarbe 0/1/2,
- `K` eine besonders dick gezeichnete **Außenkante** 0/1/2.

Für ACT-01-Alphabetbilder gilt `N = 9P + 3S + C` (A–Z = 0–25) und `K = (P+S+C) mod 3` als Prüfsymbol. Normale Kantenbreite **2 px**, ausgezeichnete Außenkante **8 px** (S. 20). `K` ist hier **Prüfung**, nicht Verhaltensstärke. Die Prüfrelation entdeckt einzelne Wertänderungen bei unabhängiger Lesung, korrigiert aber nicht beliebige Fehler; sie ist keine Authentifizierung.

**Beobachtungen, keine Generalisierung:**
- **Experiment 001** (S. 7): offene Deutung von fünf Bildern ohne Schlüssel zeigte plausible, aber teilweise nicht gezeigte Dynamik. Mehrdeutigkeit und Suggestion sind relevant.
- **Experiment 002** (S. 8): bei bekannter Grammatik drei Empfänger jeweils **17/17 Zeichen und 68/68 Parameter** in den übermittelten Antworten; die visuelle Erstlesung wurde nicht durchgängig unabhängig gesichert.
- **Experiment 003** (S. 9–10): manipulierte Prüfkante; **KI-A** gab 17/17 richtige Zeichen und 68/68 richtige Parameter und meldete genau einen echten Konflikt. **KI-D** erreichte 17/17 Endtext, aber 61/68 Parameter (falsche Parameter durch Sprachkontext maskierbar). Der Checkpoint-Lauf `KI-C*` ist wegen geändertem Auftrag nicht äquivalent.
- **Praxisexkurs** (S. 13–15): ein Leser erreichte 19/19 Zeichen und 76/76 Parameter bei skaliertem Bild; in Gegenrichtung lag ein korrektes Werkzeugresultat vor, das **nicht** korrekt in die finale Antwort überging. Beide Richtungen sind keine isolierte große Replikationsserie.
- **Grenzen** (S. 11, 21): kleiner explorativer Korpus, nicht kontrollierte Chat-Kontexte/Tools/Bildvorverarbeitung, keine unabhängige End-to-End-Replikation, keine belastbaren Erfolgswahrscheinlichkeiten. Identitäten bewusst anonymisiert.

**Schluss:** KIs können unter bestimmten, bereits getesteten Bedingungen den formalen ACT-01-Code lesen und prüfen. Noch **nicht** gezeigt ist das zuverlässige Lesen kontinuierlich gewichteter sechs Kanten, die Interpretation als objektives Modellverhalten oder ein Nutzen für adaptive Spielstrategien.

## 3. Dicke der Linien: zwei verschiedene Bedeutungen sauber trennen

### Modus A — ACT-01-Nachrichtenalphabet (bereits dokumentiert)

Das hervorgehobene `K` bleibt **genau eine von drei Außenkanten**, mit ursprünglicher Prüf-/Fehlersemantik. Kein neuer Metrikwert wird unbemerkt in dieselbe Kante gelegt. Existierende P/S/C/K-Codierungen müssen für unveränderte Stimuli gleich dekodierbar bleiben.

### Modus B — künftige Behavior Signature (vorerst Hypothese)

**Alle sechs Kanten** des K₄ können erhalten bleiben und je eine **definierte, beobachtbare Relation** durch Dicke darstellen. Vorgeschlagene Status `unavailable`, `observed`, `computed`, `interpreted` getrennt vom numerischen Wert.

- **Linienstärke** = Intensität/Anteil/Wirksamkeit einer präzise definierten *Relation*, **nicht** „Intelligenz“.
- Nur metrisch nachvollziehbare Werte, nachvollziehbar normalisiert, Version/Fenster/Matchauswahl benannt.
- **V1-Prototyp zunächst diskrete Strichstärken** statt stufenloser Veränderung, z. B. 2/5/8 px, **nur illustratives Layout, keine schon validierten Schwellen**. Stufen erst mit definierter Messgröße und Lesetests festschreiben.
- **Fehlender Wert ≠ schwache Beziehung**. Fehlende Daten visuell anders markieren (z. B. neutral gestrichelt und textuell „OFFEN“), nicht 2px als künstliches Nullsignal.
- Farbe, Position, Fläche und Punktgröße bleiben benannte, ggf. zusätzliche Kanäle, nicht durch eine willkürliche numerische Füllung verfälschen.
- Kantenänderungen **ändern die Topologie nicht**, solange alle sechs Relationen im Schema bestehen. Wird eine Kante im Bild komplett entfernt, ist die dargestellte aktive Struktur nicht mehr der vollständige ungewichtete K₄; „inaktiv“ und „nicht vorhanden“ sauber unterscheiden.
- Die g-Signature braucht ein **eigenes eindeutiges Schema mit Versions-ID**, eine Legende und ggf. einen maschinenlesbaren Datenkanal als belastbare Referenz. **Nicht** mit dem `P/S/C/K`-Buchstabencode verwechseln.

## 4. Ein messbares Verhalten ist noch keine K₄-Kantenbeziehung

**Konzeptueller Fortschritt, noch zu operationalisieren:** Die sechs Kanten könnten jeweils eine **begründete Wechselbeziehung** zwischen vier dokumentierten Akteursfunktionen repräsentieren. ACT-01-Rollen `I1/I2/R/O` sind eine Denkhilfe; **interne Modellreflexion R ist nicht direkt beobachtbar**. Extern messbare Stellvertreter (z. B. protokollierte Ankündigung, tatsächliche Ausführung, Ressourcenverbrauch, rekonstruierte Wirkung) benötigen eine **eigene Semantik**.

Kein gewichtetes g-Diagramm **allein aufgrund** von Summen wie Output/Input, Ausführungsquote oder API-Latenz als kausales Netz etikettieren. Zunächst Kennzahlen und Quellen getrennt testen, dann fachlich festlegen: Was misst jede von sechs Kanten? Denominator? Zeitfenster? Fehlermodell? Gegenbelege? Soweit eine Relation nicht identifizierbar ist, als `OFFEN` führen.

Vor der Festlegung der sechs Kanten ist der gezeigte Dreiecks-Entwurf **grafische Exploration**, keine empirisch generierte Behavior Signature.

## 5. Künftiger Anwendungsfall: Signature-informed Adaptation

**Hypothese:** Ein spielendes GPAI-Modell erhält vor dem Zug **eigene historische Signature** und ggf. die **des Gegners** samt **derselben dokumentierten Legende**, um situationsabhängig sein Vorgehen zu wählen. Dies ist ein **neuer experimenteller Interaktions-/Paarungstest**, keine direkte andere-Modell-Rangwertung innerhalb der öffentlichen **Standalone**-Behavior-Card.

### Minimaler kontrollierter Versuchsplan

- **A / Baseline:** identische Spielregeln/-konfiguration, keine Signatures.
- **B / Self:** zusätzlich eigene zuvor eingefrorene Signatur.
- **C / Self + Other:** zusätzlich gegnerische zuvor eingefrorene Signatur; beide durch gleiche Grammatik erklärt.
- **D / Kontrolle:** inhaltlich neutrale oder vertauschte Signaturen mit gleichem Prompt-/Bildumfang, um Effekte von Signaturinhalt vs. zusätzlichem Kontext zu prüfen.

Optional eigene Textfassung der gleichen Daten als Kontrollbedingung: **Ist die visuelle Kodierung hilfreich oder lediglich die zusätzliche Information?**

**Leakage-Schutz:** Alle Profile aus vor dem Teststichtag abgeschlossenen, separat selektierten Spielen; kein Ergebnis/kein Live-Event der gerade untersuchten Testpartie im Profil. Versionen/Match-/Konfigurations-IDs und Zugang zu Gegnerprofilen offenlegen. Keine unbelegten Lernbehauptungen **zwischen** Spielen ohne dokumentierten Wissenstransfer.

### Vier getrennte Prüfungen

1. **Rendern/Quellwahrheit:** Ist der g-Code korrekt aus den definierten Originalmetriken erzeugt? Provenienz und Snapshot.
2. **Visuelle Erstlesung:** Kann ein frischer Empfänger **alle sechs Kanten** und weitere Dimensionen korrekt benennen, **vor** Kontextrekonstruktion? Fehler/Ungewissheit und Skalierung.
3. **Semantik/Auswertung:** Kann er die korrekten **metrischen Bedeutungen** erklären und sich auf echte Matchfenster beziehen? Richtiges Musterwort ≠ richtige Zahl ≠ kausal wahre Deutung.
4. **Handlung/Wirkung:** Ändert die bereitgestellte Signatur beobachtbar Planung und legal ausgeführte Aktionen? Sind eventuelle Wirkungen unter kontrollierten Bedingungen belastbar, nicht nur textliche Strategieankündigungen?

Nur wenn Schritte 1–3 bestehen, adaptive Wirkung anhand einer experimentellen Serie untersuchen. Bei fehlenden Checks keine kausale Erfolgsaussage über „Signatur macht KI stärker“.

## 6. Öffentliche Darstellung / WordPress / Social

- Öffentliche Behavior Cards bleiben **standalone je Modell**, keine Neben-an-Neben-Wertung. Jede gezeigt **aus realen historischen Matches**, mit Zeit-/Kosten-/Bedingungsabdeckung.
- Eine **g-Signature** zeigt *konkret definierte* Beziehungen mit eigener Legende, Version und Snapshot; bei ungeprüfter Lesbarkeit/Meßsemantik als **Konzept** kennzeichnen, nicht als realer Modellzustand.
- Künftige Animationen über Zeit **nicht** als Lernen oder innere neuronale Rekonfiguration bezeichnen; zunächst Änderungen des beobachteten Profils/der Evidenzbasis.
- Gemeinsame GPAI-Herausforderung im [Info-Expander](08_GEMEINSAME_HERAUSFORDERUNG_INFO_EXPANDER.md), konkrete Experimentbedingungen im Evidenz-Tab; Signatur steht unter **beobachtet vs. interpretiert**.
- WordPress importiert **nicht** proprietäre Roh-Prompts/Providerkeys, sondern vorprüfte Snapshotdaten. ACT-01-Buchstabenalphabet ist eine **andere** Darstellungsanwendung und kein Data-Exportformat für die Card.

## 7. Offene Entscheidungen

1. Welche **vier beobachtbaren Rollen** benutzt das spezifische Behavior-Signature-Schema, ohne fälschlich innere Proprietärarchitektur zu behaupten?
2. Welche **sechs empirisch identifizierbaren Kantenrelationen** stehen für diese Rollen? Welcher Beobachtungszeitraum und welche Abdeckung?
3. Diskrete drei Stufen oder ein kontinuierlicher Zahlenwert? Wie robust bleibt die Lesbarkeit bei Thumbnail-/Mobilskalierung?
4. Braucht die Signature einen vom ursprünglichen ACT-01-`K` unabhängigen **Prüfkanal** (z. B. separate Prüfsignatur/Metadaten), wenn die sechs Kanten zugleich Nutzdaten tragen?
5. Wie verhindert die spätere App/CMS-Pipeline, dass eine „Signature“ ohne Schema, Legende, Quellen oder Bedingungen als empirischer Befund erscheint?

## 8. Abnahmetests / vorgeschlagen

- **BMC-T30:** Topologie und sechs Kanten erhalten; semantische Rollen/Schema-Version/Legende dokumentiert.
- **BMC-T31:** ACT-01-P/S/C/K-Kantenkodierung bleibt mit 2/8px vollständig unverändert dekodierbar; Behavior-Schema separat.
- **BMC-T32:** Diskrete Kantenstärken/Knotenattribute korrekt aus realen Metric-Registry-Werten, kein Fantasiewert, `null` bleibt OFFEN; Renderprüfung unter Verkleinerung.
- **BMC-T33:** Unabhängige Erstlesung der sechs Kantengewichte von Semantik- und Handlungstest getrennt; keine nur kontextuell erschlossenen Zeichen als visuell bestätigt zählen.
- **BMC-T34:** Eingefrorene, frühere eigene/gegnerische Snapshots; Baseline/Self/Self+Other/Kontrollarm unter dokumentierten gleichen Regeln; keine aktuellen Matchereignisse in Eingabe.
- **BMC-T35:** Keine automatische Bonoma-/Sweet-Spot-/Overthinking-Diagnose und keine erfolgreiche Adaption aus bloßen Strategieankündigungen.

## Referenzen

- **Primärquelle dieses Nachtrags:** beigefügtes *ANDY ACT 01 / A — Die Sprache der Netzwerke, v1.2*, November 2026, S. 3–10, 11, 13–15, 20–21; **nicht als in GitHub veröffentlicht behauptet**.
- [Nested Competitive Networks](../../CORE/v0.1/03_NESTED_COMPETITIVE_NETWORKS.md)
- [Dynamic Bonoma](../../CORE/v0.1/05_DYNAMIC_BONOMA.md)
- [Sweet Spot?](../../CORE/v0.1/09_SWEET_SPOT.md)
- [Behavior Model Card Product Requirements](01_PRODUCT_REQUIREMENTS.md)
- [Metric Registry](02_METRIC_REGISTRY.md)
- [Evidenzkompass](03_EVIDENZKOMPASS_UND_METHODIK.md)

**Wissenschaftlicher Status:** Die ACT-01-Piloten liefern **dokumentierte positive Lese- und Fehlertests einer vereinbarten Bildgrammatik**. Eine behavior-semantische g-Signature und ihr strategischer Nutzen sind **neue offene Forschungsvorhaben**, keine bereits beobachteten Ergebnisse.
