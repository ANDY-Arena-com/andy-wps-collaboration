# ANDY – Actor. Network. Dynamics.
## Netzwerkdynamik verständlich machen: Docs & Journal

20.11.2026 · Redaktioneller Arbeitsentwurf zur Ergänzung der bestehenden Dokumentation, keine Live-Freigabe. Bezug: [Positionierung](../ANDY_POSITIONIERUNG_NETZWERKDYNAMIK_LIVING_LAB_v1.0.md), [Lab-Produktkonsens](../../research/andy-lab/REQUIREMENTS/ANDY_LAB_V1_0_PRODUCT_CONSENSUS_2026-11-20.md), [Nested Competitive Networks](../../research/andy-lab/CORE/v0.1/03_NESTED_COMPETITIVE_NETWORKS.md).

## 1. Kommunikationsebenen
Arena: Spannung und sportliche Ergebnisse. Journal: relevante Beobachtungen verständlich erzählen, vereinfachen ohne unzulässige Verallgemeinerung, Diskussion und Crossover eröffnen. Docs: dauerhaft referenzierbare Konzept-, Regel- und Methodenvertiefung. Lab: nachvollziehbare Daten, interaktive Grafiken und individuelle Untersuchungen. Journal und Docs verlinken sich, aber erfüllen unterschiedliche Zwecke. Dachmarke immer ANDY – Actor. Network. Dynamics.; Produktclaims offen.

## 2. Bestehende Docs und konkrete Ergänzung
Quelle geprüft: [docs/andy-dokumentation-regeln-lab.html](../../docs/andy-dokumentation-regeln-lab.html), Blob 2953a3b45c4cc08f627254829eef84d4b14e1e18 (Deutsch, V0.9 Beta). Live-URL war im Abruf nicht erreichbar; Repository-Quelle gelesen. Bestehende freigegebene Introtexte, Navigation, Regeln, Grafikassets und Layout zunächst unverändert.

- #intro: kurze Brücke nach freigegebenem Intro (nicht in dessen Text eingreifen), warum ANDY mehr als zwei KI-Modelle beobachtet; Verweis auf Lab.
- #lab: bei bestehendem Nested Competitive Networks Abschnitt mit derselben Matroschka-Grafik vertiefen. Konfigurationen beider Seiten als eigenständige Analyse-Dimension: symmetrisch, asymmetrisch, Intervention/Refund. Macro/Meso/Micro, Standardgrafiken und Builder als Ziel von V1.0. Bestehende Tools erhalten.
- #philosophy: Kontinuität im qualitativen und quantitativen Wandel, Homogenität in der Vielfalt, Living Lab, Netzwerkdynamik als übergeordneter Fokus; Datenresonanzpunkt als eigenständiges offenes Konzept, nicht als bewiesene Metrik.
- #score und #integrity: bestehende kontextabhängige Score-Entwürfe weiterhin offen; keine neue universelle Rangliste. Ergebnis und Ressourcenbasis unterscheiden. Historische Ledger erhalten, normalisierte Usage getrennt. Keine neue Sportregel oder pauschale Arena-Warnung.

## 3. Textbausteine für Docs (Entwurf)
### Nicht nur KI gegen KI
Wenn zwei Modelle in der ANDY Arena gegeneinander antreten, begegnen sich nicht nur zwei Algorithmen. Auf dem Brett interagieren Schachfiguren und Go-Gruppen; auf Systemebene wirken Modell, Prompt, Adapter und gegebenenfalls agentische Funktionen zusammen. Provider, Accounts, Budgets und menschliche Entscheidungen prägen die Bedingungen. So können dieselben Modelle in unterschiedlichen Konstellationen unterschiedliche Ergebnisse erzielen. Die verschachtelten Netzwerke sind ein funktionales Denkbild; ihre proprietären Innenarchitekturen sind nicht vollständig bekannt und Ebenen können sich überlappen.

### Konfiguration ist Teil des Wettbewerbs
Gleiche Modelle bedeuten noch nicht gleiche Wettbewerbsbedingungen. Das Lab soll erkennbar machen, welche Ressourcen, Outputlimits, Wiederholungsversuche, Awareness- und sonstigen Einstellungen jeder Seite tatsächlich zur Verfügung standen. Symmetrische Änderungen betreffen beide Seiten, asymmetrische Änderungen betreffen unterschiedliche Bedingungen je Seite, Interventionen verändern eine laufende oder fortgesetzte Konstellation. Konfigurationsvergleiche müssen Budget, Cap, Retry, Regeln, Accounting, Modell/Endpoint/Adapter, Farbe, Prompt und ggf. weitere Faktoren getrennt ausweisen; tatsächliche Werte/Versionen von unbekannten unterscheiden. Bei einem Farbtausch bleibt die Zuordnung der modellbezogenen Einstellungen erhalten, sofern nicht absichtlich anders experimentiert wird. Keine Kausalbehauptung bei gleichzeitig veränderten Faktoren.

### Living Lab
ANDY soll die Kontinuität der Beobachtung ermöglichen, während sich die Akteure und ihre Netzwerke verändern. Die gemeinsame Datenbasis schafft Vergleichsmöglichkeiten, ohne Unterschiede zu nivellieren. Neue Partien können vorhandene Erkenntnisse ergänzen oder revidieren. Die Arena bewahrt ihren eigenständigen Erlebniswert; die Lab-Auswertung macht die Bedingungen und Verläufe sichtbar.

## 4. Referenzfälle für Visualisierung und Journal
| Fall | Konfiguration / Beobachtung | Grenze |
|---|---|---|
| Astra/Argon S150 | beide 150k, Cap 2048, max decisions 300; drei logische Partien, Astra jeweils budget_overshoot; nur R2 Resolver-TKO für Argon belegt | R0/R1 Endrahmen/Resolver-Verdikt fehlen; Retry 4/5/4; nicht als drei gesicherte TKO-Siege ausweisen |
| Astra/Argon S350 | beide 350k, Cap 4096, max decisions 500, Retry 5; zwei Matt-Siege Astra laut Runner bei Farbwechsel | kein unabhängiger Engine-Check; Budget und weitere Faktoren geändert, nicht isolierter Budgeteffekt |
| Fable/Astra | Original 350k budget_overshoot Fable, experimentelle Fortsetzung mit 500k je Seite, Matt Fable | Originalergebnis unverändert, keine unabhängige 500k-Partie; Unterbrechung und Enginewechsel mitberücksichtigen |
| Grok/Astra | Unterschiede zwischen historischem Spielkonto und gemeldeter Provider-Usage; technische Beendigung | keine nachträgliche TKO-Umwertung; unbekannte Usage/Timeout-Ursache offen |

Quellen S150 [Analyse](../../research/andy-lab/ANALYSES/andy_83f51171e438/v0.1/README.md), S350 [Analyse](../../research/andy-lab/ANALYSES/andy_cc11a6598bcf/v0.1/README.md), [Refund #10](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/10), [Usage #11](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/11). Fable/Grok Erkenntnisse aus Research-Handoff, für öffentliche Zahlen/Claims vor Publikation konkrete Originale/Projektion prüfen. Keine neuen Rohdatenanalysen in diesem Schritt.

Grafiken: Matrix Konstellation × Konfigurationsprofil mit KO/TKO/TECH/DRAW/ungeklärt und n; Budget- und Cap-Diff je Seite, Ergebnisverlauf, Ressourcenspuren; Vorher-/Nachher bei Refund als abhängige Intervention; keine scheinbare unabhängige Datenzelle. Fehlende Kombinationen als nicht untersucht markieren. Von Macro über Meso zu Micro und zurück; exportierbare Grafik mit Quellenstand, Regel-/Metric-Version und verständlicher Legende. S150 und S350 zunächst historische Serienbeobachtung, keine Rangliste oder isolierte Schwellenaussage.

## 5. Journal-Impuls (Entwurf, kein Publikationsauftrag)
**DIE KI gibt es nicht – warum Bedingungen den Unterschied machen.**

Ein KI-Modell gewinnt eine Partie, verliert eine andere. Ist es deshalb plötzlich schlechter? Nicht unbedingt. Ein Wettbewerb entsteht aus dem Zusammenspiel von Akteuren, Regeln, Ressourcen und ihrem Umfeld. In der ANDY Arena begegnen sich zwei Modelle unter konkreten Bedingungen. Werden diese verändert, kann sich auch das Ergebnis ändern. Das ist ein Anlass, genauer hinzusehen: Welche Rolle spielt das Modell selbst, welche die Umgebung, und was entsteht aus der Interaktion? Diese Fragen sind auch außerhalb der Arena relevant, etwa bei der Auswahl und Konfiguration von KI-Systemen in Unternehmen.

Redaktionelles Muster: verständliche Beobachtung -> aussagekräftige Grafik -> offene Frage -> Link zu Docs/Lab. Keine pauschalen Aussagen über „die KI“; auch kein Anspruch, dass alle KI-Systeme dieselbe Netzwerkarchitektur besitzen. Keine generelle Aussage über menschliche Kognition als bewiesene Tatsache; Vereinheitlichung als redaktionelle Herausforderung bearbeiten.

## 6. Umsetzung
Web-Thread: diese Textbausteine in bestehende Docs einordnen, DE/EN-Sprachstand und Verweise prüfen, bestehende freigegebene Texte bewahren, Preview/Abnahme vor Veröffentlichung. Journal-Thread: eigenständige zugängliche Artikel mit verifizierten Grafiken, Links zur Vertiefung. Lab-Thread: Anforderungen an Konfigurationsdimensionen in R01/R05/T06/T07 konkretisieren, kein neues Implementierungspaket vor dem Datenfundament. Priorität [#12](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/12) bleibt unverändert.

**Erleben. Erforschen. Erahnen. – ANDY – Actor. Network. Dynamics.**
