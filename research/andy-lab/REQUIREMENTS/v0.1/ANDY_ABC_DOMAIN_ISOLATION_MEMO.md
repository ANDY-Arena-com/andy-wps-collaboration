# ANDY-ABC – Domain Isolation & Coupling
Stand 15.11.2026 · Lab Research Memo v0.1 · Konzeptimpuls aus Thread 1, kein Implementierungsauftrag.

## Ziel
Die Kopplung der beiden ANDY-Spieldomänen selbst zum Forschungsgegenstand machen. Lokale Kompetenz und globale Wirksamkeit unterscheiden: Gute Leistungen in isolierten Aufgaben garantieren keine gute Koordination im gekoppelten System. Umgekehrt könnten Wechselwirkungen zusätzliche Handlungsmöglichkeiten eröffnen. Erleben – Erforschen – Erahnen.

## Drei experimentelle Bedingungen
| Bedingung | Domäne | Kopplung |
|---|---|---|
| A – Chess only | isoliertes Schach | ohne Go-Kopplung |
| B – Go only | isoliertes Go | ohne Schach-Kopplung |
| C – Hybrid | ANDY Schach + Go | bestehende Wechselwirkungen |

Ordinary Go/Chess und isolierte ANDY-Domänen mit ihrer spezifischen Topologie, Regeln und Initialisierung klar unterscheiden. Die konkrete Regeldefinition für isolierte Modi ist offen. Keine stillschweigende Änderung der Hybrid-Engine. Die drei Modi sind Vergleichsbedingungen, nicht automatisch kausal isolierte Experimente.

## Mögliche Muster (hypothetisch, keine Befunde)
| Chess | Go | Hybrid | Mögliche Lesart |
|---|---|---|---|
| gut | schwach | schwach | domänenspezifische Schwierigkeit |
| gut | gut | schwach | mögliches Koordinations-/Integrationsproblem |
| gut | schwach | gut | möglicher positiver Kopplungseffekt |
| gut | gut | gut | stabile domänenübergreifende Ausführung/Wirksamkeit |
| schwach | schwach | schwach | möglicherweise übergreifendes Ausführungs- oder Kompetenzproblem |

Auch andere Kombinationen sind möglich. Gut/schwach sind hier lediglich Platzhalter; keine einheitliche validierte Skala oder Diagnose. Strategische Qualität, Regelkonformität, technische Ausführung und Ressourcenerschöpfung getrennt erfassen. Eine fehlende Ausgabe beweist kein mangelndes Spielverständnis.

## Lab-Erweiterung: Domain Behavior Profile
Als zusätzliche Vergleichsdimension der Model Behavior Cards sowie Pattern View und Analytical View:
- Strategische Wirksamkeit: domänengerechte Ergebnisse, Brettentwicklung, nachvollziehbare Situationen; keine unbegründete aggregierte Note.
- Ausführungsstabilität: legale Aktionen, Fehlversuche, Retries, Abbrüche und Endgründe.
- Ressourcen: logische Tokens, Reasoning soweit berichtet, API-Latenz, Dauer, geschätzte bzw. belegte Kosten, Cache-Status und Abdeckung gemäß CACHE-01.
- Vergleichbare Serien und Profile nebeneinander, gemeinsame Filter und Drill-down zu Original-Match/Event. Domänenabhängige Metriken getrennt halten; nicht anwendbare Felder als solche markieren.

Unterschiede im Aufgaben-/Spielumfang, Zugreihenfolge, Budget, Prompt, Outputlimit, Modellversion, Gegner, Farbe, Regeln und Topologie dokumentieren. Replikate und Farbwechsel; gleiche Vergleichseinheiten vorab definieren. Gleiche Tokenbudgets allein gewährleisten keine Vergleichbarkeit. Ein möglicher zusätzlicher Ressourcenbedarf im Hybrid ist zu untersuchen, nicht vorauszusetzen. Kein einfacher Abzug A+B von C ohne begründete gemeinsame Messbasis.

## Serienarchitektur und App-Anschluss
Game Mode als eindeutiges Merkmal der vorhandenen Serienprofile, analog zur Cache-Konfiguration. In Übersicht, Profilvergleich, Fingerprint, Rematch und JSON/JSONL-/Serienexport mitführen. Bei Mode-Wechsel neues Profil, keine Vermischung der Ergebnisse oder regulären Leaderboards. Historische Modi nur bei belegter Zuordnung kennzeichnen. Keine zusätzliche Serienverwaltung oder Experiment Builder.

Thread 1 schlägt DOMAIN-01 (Offline-Domänentest mit vergleichbaren Stellungen) vor DOMAIN-02 (vollständige isolierte Spielmodi) vor. Zugreihenfolge, Spielende, Wertung, Prompt, Replay und Engine müssen konsistent sein. Technische Umsetzung und Regelentscheidungen verbleiben bei Thread 1 und Projektleitung. Kein API-Start oder bezahlter Pilot durch dieses Memo.

## Anschluss an Forschungsfelder
- Nested Competitive Networks: Wechselwirkungen gekoppelter Netzwerke.
- Dynamic Bonoma: Passung von Strategie und Ausführung bei zunehmender Koordinationsanforderung.
- Sweet Spot?: mögliche Balance von Kopplung, Ressourcenbelastung und Wirksamkeit.
- Economic Competition: Kosten der Koordination mehrerer Problemdomänen.
- Situation Challenge: lokale gegenüber domänenübergreifender Problemlösung.

Unternehmensbezug: Lokale Aufgabenkompetenz ist nicht gleich globale Wirksamkeit. Gekoppelte Aufgaben, Ziele und Ressourcen können zusätzliche Koordinationsanforderungen oder Chancen erzeugen. ANDY bietet dafür ein experimentelles Anschauungsfeld, keinen direkten Nachweis von Unternehmensleistung. Später möglicher Journal-Themenkandidat, keine Publikationsfreigabe.

## Status / Referenzen
Erweiterungsimpuls zum bestehenden Requirements-Pool, insbesondere R02/R03/R04/R05/R06/R07/R10/R11; keine neuen verbindlichen Requirement-IDs, Hypothesen, Scores oder Prioritäten. Grundlage: Thread-1-Briefing und anschließende Lab-Einordnung vom 15.11.2026. Keine Datenanalyse, Engine-Validierung oder Tests vorgenommen.
- [Lab Requirements](README.md)
- [Economic Competition](SUBQUADRATIC_ECONOMIC_COMPETITION.md)
- [Situation Challenge](SITUATION_CHALLENGE_DEMO.md)
- [CACHE-01](../../../../PROJECT/ANDY_CACHE_01_IMPLEMENTATION_MEMO_v0.1.md)
