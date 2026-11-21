# ANDY Lab – Cybersecurity-Crossover: Nested Competitive Networks

**Forschungsmemo V0.1 · 21.11.2026 · konzeptionelle Arbeitshypothese, kein empirischer Nachweis und kein Implementierungsauftrag**

**Leitgedanke:** Die relevante Parallele zwischen ANDY Arena und autonomer Cyberabwehr ist **nicht** primär „KI-Angreifer gegen KI-Verteidiger“ oder ein einzelnes Overthinking-Muster. Sie liegt in der **wechselseitigen Konkurrenz verschachtelter, adaptiver Netzwerke** unter sich verändernden Bedingungen, unvollständiger Information und begrenzten Ressourcen.

Dieses Memo formuliert eine mögliche wissenschaftliche Übertragung der ANDY-Forschungsarchitektur. Es belegt weder die Übertragbarkeit konkreter Spielbefunde in die Cybersecurity noch die Eignung eines ANDY-Observers für reale Sicherheitsentscheidungen.

## 1. Ausgangspunkt: Netzwerk gegen Netzwerk statt Modell gegen Modell

ANDY ist kein isoliertes Duell zweier homogener „Intelligenzen“. Die Konkurrenz verläuft zwischen funktional verschachtelten Systemen und ihren Abhängigkeiten:

- **Auf dem Brett:** Schachfiguren mit unterschiedlichen Funktionen, Go-Steine, Nachbarschaften und Gruppen sowie die Kopplung beider Spiele.
- **Auf Akteursseite:** Modellentscheidungen und gegebenenfalls verteilte Funktionen für Planung, Kontrolle, Werkzeuge und Ausführung. Interne proprietäre Architekturen sind nicht vollständig bekannt.
- **Auf Systemebene:** Prompt, Adapter, Engine, Replay/Logging, Infrastruktur und Zugausführung.
- **Auf Ressourcen-/Provider-Ebene:** Budgets, Tokens, Latenz, API-Routing, Cache, Limits, Account und Anbieter.
- **Auf menschlicher Ebene:** Paarung, Spielregeln, Konfiguration, Freigaben und Bewertung.

Diese Ebenen sind eine **funktionale Skizze**, keine wörtliche mathematische Teilmengenhierarchie. Die Ebenen können sich gegenseitig beeinflussen; gemeinsame Infrastruktur ist möglich. Ziele einzelner Ebenen müssen nicht identisch sein.

Der Kern von [Nested Competitive Networks](../CORE/v0.1/03_NESTED_COMPETITIVE_NETWORKS.md) ist: **Lokale Stabilität ist nicht globale Stabilität.** Ein Teilsystem kann erfolgreich funktionieren, während das Gesamtsystem Handlungsmöglichkeiten verliert. Umgekehrt kann der Verzicht auf eine lokale Position die globale Stabilität verbessern.

## 2. Die strukturelle Cybersecurity-Parallele

Auch in einer autonomen Angriff-/Abwehrkonstellation konkurrieren **gekoppelte Netzwerke**, nicht bloß zwei Einzelagenten:

- Ein angreifendes System kann Planung, Zielauswahl, Ausführung, Rückmeldung und Ressourcen koordinieren.
- Ein verteidigendes System kann Beobachtung, Lagebewertung, Schutzmaßnahmen, Verfügbarkeitsziele, menschliche Freigaben und technische Infrastruktur koordinieren.
- Beide beeinflussen über ihre Aktionen eine **gemeinsame, dynamische Umgebung**.
- Die Handlung eines Netzwerks verändert die Gültigkeit, Kosten oder Erfolgsaussichten der Strategie des anderen. Die Gegenreaktion kann den gerade erreichten stabilen Zustand erneut destabilisieren.

Die Analogie betrifft **adaptive Organisation, Kopplung, Konkurrenz, Ressourcen und Reorganisation**. Sie behauptet keine Gleichwertigkeit der Folgen: Ein ANDY-Zug und ein realer Sicherheitsvorfall haben fundamental unterschiedliche Risiken, Informationslagen und Anforderungen.

## 3. Co-Adaption ist die zentrale Analyseeinheit

Zu kurz greift die Frage: „Wie gut passt sich Modell A an?“

Die präzisere Frage lautet:

> **Wie verändern und reorganisieren zwei konkurrierende, verschachtelte Netzwerke wechselseitig ihre Handlungsvoraussetzungen, und unter welchen Bedingungen erhalten, verlieren oder gewinnen sie Handlungsfähigkeit zurück?**

Mögliche Dynamiken:
1. Eine Handlung von Netzwerk A verändert die Bedingungen, unter denen Netzwerk B erfolgreich handeln konnte.
2. Netzwerk B verteilt Analyse-, Umsetzungs- und Kontrollressourcen neu und antwortet.
3. Diese Antwort kann die eben erreichte Anpassung von A wieder entwerten.
4. Lokale Erfolge können globale Kosten erzeugen; eine temporäre Destabilisierung kann Voraussetzung für spätere Restabilisierung sein.
5. Ein vermeintlich „starkes“ Modell kann in einer spezifischen Paarung/Umgebung schlechter abschneiden als ein schwächeres, aber anders organisiertes System.

Deshalb sind **Interaktionsprofile und Serien unter definierten Bedingungen** wichtiger als eine kontextlose Rangliste einzelner Modelle. „Co-Adaption“ meint hier wechselseitige Anpassung *innerhalb* des beobachteten Verlaufs; Lernen *zwischen* Partien darf ohne belegten Informationsübertrag nicht behauptet werden.

## 4. Dynamic Bonoma: Der „Punch“ verändert die Strategiepassung

Die konzeptionelle [Dynamic-Bonoma-Matrix](../CORE/v0.1/05_DYNAMIC_BONOMA.md) trennt **Strategieeignung** und **Ausführungsqualität**:

| | Gute Umsetzung | Schlechte Umsetzung |
| --- | --- | --- |
| Passende Strategie | Success | Trouble |
| Unpassende Strategie | Roulette | Failure |

Die besonders relevante Duell-Dynamik: Der Gegner kann durch seine Aktion eine zuvor geeignete Strategie **unpassend machen, ohne die Ausführungsfähigkeit des betroffenen Netzwerks zu verschlechtern**. Ein mögliches Beispiel ist „Success → Roulette“; andere Übergänge bleiben möglich.

**„The AI has a plan until it gets punched in the arena.“** Der wissenschaftliche Punkt liegt nicht allein im Punch, sondern in der **veränderten Passung von Strategie, Umsetzung, Ressourcen und Umgebung** sowie im möglichen Reorganisationsprozess danach.

Die Quadranten sind **noch keine validierten Messklassen**. Sie dürfen weder allein aus Sieg/Niederlage noch aus legalen Zügen abgeleitet werden.

## 5. Overthinking neu eingeordnet: Netzwerkkoordination statt isolierter Schwäche

Der Unterschied zwischen einem endlos analysierenden Agenten und einem funktionierenden Zyklus aus **Ziel setzen → Handeln → Ergebnis prüfen → anpassen** bleibt wichtig. Aber Overthinking ist nur **eine mögliche Manifestation** eines tieferliegenden Netzwerkproblems:

- Interne Analyse kann Kapazität binden, die an anderer Stelle zur Umsetzung oder Prüfung fehlt.
- Zu frühes Handeln kann ebenso schädlich sein, wenn Risiko oder Unsicherheit unzureichend beurteilt werden.
- Eine gute Ressourcenzuteilung ist **situations- und gegnerabhängig**.
- Die eigentliche Frage ist, ob das Gesamtnetzwerk unter gegnerischem Druck seine **Koordination und Handlungsfähigkeit** bewahrt oder wiederherstellt.

Nicht die Menge des Denkens ist die zentrale Zielgröße, sondern die **zeitlich veränderliche Wirksamkeit der Organisation des Gesamtsystems** unter Konkurrenzbedingungen.

## 6. Competitive Mirroring: funktionale Resonanz statt wörtlicher Kopie

Der bestehende [ANDY-Ansatz Competitive Mirroring](../CORE/v0.1/04_COMPETITIVE_MIRRORING.md) thematisiert mögliche funktionale Selbstähnlichkeiten und Antizipation. Die bisherigen Beobachtungen zu gemeinsamem API-Key-Umfeld und Geschwindigkeit sind **explorativ**, ohne kontrollierte Bestätigung; Caching, Routing, Last und weitere technische Faktoren sind plausible Alternativen. Weder gemeinsames Gedächtnis noch ein Spiegelneuronenmechanismus sind belegt.

Für das Cybersecurity-Crossover wäre relevant, **ob und unter welchen Bedingungen konkurrierende Netzwerke ähnliche Koordinations- oder Reaktionsformen entwickeln**. Dies ist etwas anderes als exakte geometrische Go-Spiegelung und darf nicht mit ihr gleichgesetzt werden.

## 7. Konsequenz für den ANDY Observer: von Modellprofilen zu Interaktionsprofilen

Die bestehende Observer-Idee kann langfristig auf drei Ebenen arbeiten:

| Ebene | Beobachtungsgegenstand | Grenze |
| --- | --- | --- |
| Agent | Protokollierte Aussagen, Aktionen, Fehlversuche, Zeiten, Ressourcen | Keine direkte Kenntnis interner Absichten |
| Interaktion | Aktion A → Zustandsänderung → Handlungsspielraum/Reaktion B → Folge für A | Zeitliche Folge beweist keine Kausalität |
| Verschachteltes Gesamtsystem | Strategiepassung, Ressourcenverschiebung, lokale/globale Stabilisierung, Rekonfiguration, Kollaps/Recovery | Abgeleitete Konstrukte brauchen eigene Operationalisierung und Validierung |

**Forschungsziel:** Die Entwicklung der *Paarung* sichtbar machen, nicht nur jeweils eine Behavior Card für A und B. Denkbar sind **Model Interaction Profiles** mit Setup, Antizipation/Reaktion, Ressourcen, Reorganisation, Kollapsprofil, Gegenfällen und Provenienz.

Die bereits nützliche, deterministische Observer-/Replay-Navigation bleibt Grundlage. KI-Observer wären **austauschbare, separat zu evaluierende Interpretationsmodule**, keine Wahrheitsinstanzen. Ein Observer greift nicht in die spielenden Agenten oder die Engine ein.

## 8. Prüfbare Forschungsfragen für ANDY

1. **Interaktionsabhängigkeit:** Verändert sich die beobachtete Handlungsfähigkeit desselben Modells systematisch mit Gegner, Farbe, Regeln und Ressourcenbedingungen?
2. **Destabilisierung/Restabilisierung:** Lassen sich zeitlich abgegrenzte Zustandswechsel erkennen, bei denen eine zuvor wirksame Vorgehensweise unter gegnerischem Druck unwirksam wird und später angepasst wird?
3. **Lokal vs. global:** Unter welchen Bedingungen begünstigen lokale Gewinne oder lokale Ressourceninvestitionen die Gesamtleistung – oder beeinträchtigen sie?
4. **Organisation vs. Modellstärke:** Können kompakte, versionierte Handlungs-/Feedback-Regeln (z. B. ein Markdown-Skill) die Leistung eines schwächeren Modells unter bestimmten Paarungen verbessern – ohne die Engine zu ändern?
5. **Observer-Mehrwert:** Was erkennen unterschiedliche AI Observer zusätzlich zu deterministischen Ereignis- und Ressourcenanalysen, und mit welcher Fehlerquote?

Diese Fragen sind **Hypothesen**, nicht bereits erhobene Befunde.

## 9. Forschungsdesign und Evidenzgrenzen

- Zunächst **reale ANDY-Originalereignisse** und Replay-Zustände unverändert sichern, mit Match-/Serien-ID, Spielregeln, Engine-, Prompt- und Modellstand, Farbe, Budget und beobachtbaren Zeit-/Ressourcendaten.
- **Einzelereignis, komplette Partie und unabhängige Spielserie** unterscheiden; viele Züge aus derselben Partie sind keine unabhängigen Wiederholungen.
- Kontrollierte **Serien mit Farbtausch**, wiederholten Paarungen und dokumentierten Konfigurationsvarianten bilden.
- Strategie-/Umsetzungs-/Stabilitätsindikatoren **vor einer confirmatorischen Reihe definieren** und Gegenfälle einbeziehen.
- Externe technische Ursachen für Unterschiede, insbesondere Provider-Last, Caching, Routing und Datenformat, prüfen.
- Ohne belegten Informationsfluss keine übergreifende Lernfähigkeit unterstellen.
- **BEOBACHTET / BERECHNET / INTERPRETIERT / OFFEN** konsequent ausweisen. Modellbegründungen sind Texte, kein direkter Einblick in interne Gedanken.
- In einer ersten Phase **keine reale Cyberangriffs- oder Abwehrsimulation** und keine Behauptung operativer Cyber-Tauglichkeit. Die Übertragung bleibt methodisch/konzeptionell; jede spätere Sicherheitsanwendung erfordert domänenspezifische Validierung und Sicherheitsprüfung.

Im Sinne der [adaptiven Erkenntnisannäherung](../CORE/v0.1/06_ADAPTIVE_ERKENNTNISANNAEHERUNG.md) kann neue Evidenz die Interpretation destabilisieren. Eine stabile Erzählung ist kein Ersatz für Gegenproben.

## 10. Möglicher Crossover-Erkenntnisbeitrag

Das Potenzial liegt in einem **kontrollierbaren Modellraum für adaptive, adversariale Netzwerkinteraktion**: ANDY dokumentiert Aktionen und deren Folgen in einer dynamischen Umgebung und macht Ressourcen-/Reaktionsverläufe über Replay und Observer untersuchbar.

Für autonom agierende Cyberabwehrsysteme könnte die *Methodik* relevant werden, wie man die Wechselwirkung von konkurrierenden Netzwerken, ihren Ressourcen, Koordinationsentscheidungen und wechselnder Strategiepassung untersucht. **ANDY validiert keine reale Cyberabwehr** und liefert keine unmittelbar übertragbaren Wirksamkeitswerte.

### Verdichtete Leitthese

> **Nicht „Welche KI denkt oder handelt am besten?“, sondern: Unter welchen Bedingungen erhält die Organisation eines konkurrierenden, verschachtelten Netzwerks ihre Handlungsfähigkeit gegenüber einem anderen – und wie verändert sich dieses Verhältnis im Verlauf ihrer wechselseitigen Anpassung?**

## Projektinterne Quellen und Status

- [ANDY Lab CORE V0.1](../CORE/v0.1/README.md) – freigegebene konzeptionelle Grundlage.
- [Nested Competitive Networks](../CORE/v0.1/03_NESTED_COMPETITIVE_NETWORKS.md).
- [Dynamic Bonoma](../CORE/v0.1/05_DYNAMIC_BONOMA.md).
- [Competitive Mirroring](../CORE/v0.1/04_COMPETITIVE_MIRRORING.md).
- [Adaptive Erkenntnisannäherung](../CORE/v0.1/06_ADAPTIVE_ERKENNTNISANNAEHERUNG.md).
- [Erkenntnishaltung](../CORE/v0.1/01_ERKENNTNISHALTUNG.md).

**Status:** Neue, aus der Diskussion vom 21.11.2026 abgeleitete Crossover-Hypothese. Sie ändert den freigegebenen CORE V0.1, die Spielregeln, die Engine und vorhandene Hypothesen-/Mess-IDs nicht. Kein Implementierungsauftrag und keine empirische Behauptung eines validierten Cybersecurity-Transfers.
