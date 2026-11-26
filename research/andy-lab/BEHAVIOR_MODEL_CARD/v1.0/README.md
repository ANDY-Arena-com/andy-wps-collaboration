# ANDY Behavior Model Card — Produktstand V1.0

**Stand:** 25.11.2026 · **Status:** konsolidierter Produkt-/Requirements- und Schnittstellenentwurf, **keine freigegebene technische Implementierung**.
**Adressaten:** ANDY App/Analyzer/Lab, ANDY Journal/WordPress, Editorial, Data/Evidence und Social.
**Grundentscheidung:** **Standalone-Verhaltensprofil genau eines Modells**, aus nachweislich realen ANDY-Partien. **Keine direkten Modellvergleiche, keine Konkurrenzbalken, keine Rankings, kein Intelligenzscore.** Gegner sind ausschließlich Matchkontext und ggf. Quelle eines Ereignisses, niemals die Referenzachse der Card.


**Zentrales Umsetzungsticket:** [GitHub Issue #15 – APP-Exporter → Journal/WordPress](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/15) (Planung, keine technische Abnahme).

## Produktidee

Eine Behavior Model Card erzählt *nicht*, welches Modell besser ist, sondern **was dieses Modell unter welchen Bedingungen tatsächlich getan hat**, mit welcher Geschwindigkeit, mit welchen Ressourcen und über wie viele logisch unabhängige Partien. Sie wächst mit neuen dokumentierten Spielen, ohne historische Beobachtungen zu überschreiben.

Die Card ist **kein amtliches Anbieterprofil**. Angaben zu Modellen, APIs, Tokenverbrauch und Latenzen werden aus historischen Spielprotokollen entnommen und mit ihrem Nachweisstatus gekennzeichnet. Aussagen über proprietäre innere Denkprozesse sind ausgeschlossen.

**Gemeinsamer Kontext:** Auf jeder allgemeinen KI-Card erklärt ein zentraler, aufklappbarer DE/EN-Baustein die besondere Schach-Go-Aufgabe und die Rolle allgemeiner KI-Werkzeuge. Gleicher Regelrahmen, aber keine behauptete identische effektive Konfiguration und kein verifizierter „unbekanntes Vortraining“-Nachweis; Link zur öffentlichen ANDY-Dokumentation.

**Primärsicht:** Anzahl Spiele → ausgeführte Aktionen und API-Entscheidungen → tatsächliches eigenes Spieltempo → Input/Output/Reasoning-Ressourcen → Spielverlauf und Regelereignisse → Versuchsbedingungen, Quellen und offene Datenlücken.

**Sekundärsicht:** Bonoma-Dynamik, Sweet Spot/Overthinking, Stabilität A/B/C, Antizipation, Recovery/Kollaps und Aftermatch-Reflexion. Immer als eigenständige, vorläufige, ereignisgebundene Interpretationen, nie aus der Tokenmenge oder Siegquote automatisch als Modellcharakteristik etikettieren.

## Anforderungen und Artefakte

| Dokument | Inhalt |
| --- | --- |
| [01_PRODUCT_REQUIREMENTS.md](01_PRODUCT_REQUIREMENTS.md) | verbindliche Produktleitplanken, Funktionsumfang, P0/P1, Akzeptanz |
| [02_METRIC_REGISTRY.md](02_METRIC_REGISTRY.md) | konkrete Zähler, Nenner, Definitionen, Coverage, Tempomessung, Tokenrelation |
| [03_EVIDENZKOMPASS_UND_METHODIK.md](03_EVIDENZKOMPASS_UND_METHODIK.md) | Beobachtungsumfang vs. Verhaltensstabilität vs. Erhebungsaufwand; Bonoma/Sweet Spot, Nested Networks |
| [04_EXPORT_CONTRACT_DRAFT.md](04_EXPORT_CONTRACT_DRAFT.md) | versionierter APP-JSON-Exporter, Snapshot, Provenienz, Beispiel und Importgrenzen |
| [05_UI_WP_JOURNAL_SOCIAL.md](05_UI_WP_JOURNAL_SOCIAL.md) | HTML-V1-Layout, Journal-/Fight-Night-Verknüpfung, WordPress und Social-Teaser |
| [06_ENGINEERING_ROADMAP_TESTS.md](06_ENGINEERING_ROADMAP_TESTS.md) | Implementierungsreihenfolge, Security/Release/Regression und Tests |
| [07_PILOTDATEN_QUELLEN_STATUS.md](07_PILOTDATEN_QUELLEN_STATUS.md) | belegter Gemini-4-Argon-Pilot mit fünf logischen Partien und nachweisbaren Grenzen |
| [examples/behavior_card_argon_v1_draft.json](examples/behavior_card_argon_v1_draft.json) | **Illustration des Vertrags**, keine produktive exporterzeugte Datei |
| [schema/behavior_card_v1_draft.schema.json](schema/behavior_card_v1_draft.schema.json) | maschinenlesbarer JSON-Schema-Draft, noch kein freigegebener Importvertrag |
| [08_GEMEINSAME_HERAUSFORDERUNG_INFO_EXPANDER.md](08_GEMEINSAME_HERAUSFORDERUNG_INFO_EXPANDER.md) | verbindlicher globaler DE/EN-Info-Expander „Warum ANDY?“, Grundlagen und Business-Analogie |
| [09_G_SIGNATUR_ACT01_FORSCHUNGSBRUECKE.md](09_G_SIGNATUR_ACT01_FORSCHUNGSBRUECKE.md) | ACT-01-Whitepaper, nachgewiesene visuelle Lesetests, Linienstärke und künftige gewichtete K₄-Behavior-Signature |

**Referenz-Demo:** `ANDY_BEHAVIOR_MODEL_CARD_V1.html` (offlinefähiger HTML-Clickdummy vom 25.11.2026, derzeit im ursprünglichen Chat-/Handoff-Paket; **nicht als in GitHub eingecheckt behaupten**). Der Entwurf zeigt Überblick, Spieltempo, Ressourcen, Verhalten und Evidenz; Filter 5 Spiele / S150 / S350. Die Spezifikation hier ist die Grundlage für spätere Reimplementierung, kein behaupteter Plugin-Release.

## Wissenschaftliches Fundament – vorhandenen Kern erhalten

- [Analysekompass v0.1 – inklusive bestehender Card-Grafik](../../ANALYSEKOMPASS/v0.1/README.md) (historische Baseline, nicht überschreiben).
- [Dynamic Bonoma](../../CORE/v0.1/05_DYNAMIC_BONOMA.md) und [Sweet Spot?](../../CORE/v0.1/09_SWEET_SPOT.md).
- [Nested Competitive Networks](../../CORE/v0.1/03_NESTED_COMPETITIVE_NETWORKS.md): lokale Stabilität ist nicht globale Stabilität; Modelloutput entsteht in einem verschachtelten technischen, ökonomischen und menschlichen Wirkungssystem.
- [Adaptive Erkenntnisannäherung](../../CORE/v0.1/06_ADAPTIVE_ERKENNTNISANNAEHERUNG.md).
- [Lab-V1.0-Produktkonsens](../../REQUIREMENTS/ANDY_LAB_V1_0_PRODUCT_CONSENSUS_2026-11-20.md): Living Lab, Story-driven Development, gemeinsame unveränderte Originaldaten.
- [Match Evidence](../../../../PROJECT/ANDY_MATCH_EVIDENCE_JSONL_JSON_SQLITE_v1.0.md): JSONL + Match-JSON sind Primärbelege; SQLite abgeleitet.

## Einordnung ins ANDY-Flywheel

**Arena (echte Partien) → Evidence/Metric Engine (faktische Projektion) → Behavior Card (modellbezogenes Eigenprofil) → Journal / Fight Night / Social (redaktioneller Einstieg) → Replay (Originalereignis) → Lab (offene Forschung) → neue Partien.**

Card-Export und WordPress-Anbindung sind *geplante Verträge*, keine bereits installierten Funktionen. Journal-Content bestimmt Übersicht und Home; bestehendes Launch Control, Staging-first und DE/EN-System bleiben die Publikationsinstanzen.

## Nicht verhandelbare Grenzen

1. **Keine andere Modell-ID als Bezugsgröße** im sichtbaren Card-Profil; kein „besser/schneller als“, keine Anbieter-Rangfolge.
2. **Unbekannt ist nicht null.** Fehlende Zeit-/Reasoning-/Preiswerte bleiben fehlend.
3. **Viele Züge sind nicht viele unabhängige Partien.** Spielzahl und Konfigurationsmix immer nennen.
4. **Viel Datenmaterial ist nicht automatisch hohe Aussagekraft.** Mehr Wiederholungen unter *vergleichbaren Bedingungen* können stabilere Schätzungen ermöglichen; Konfigurationsmix, Auswahlbias, Versionen und Korrelationen sind gesondert sichtbar.
5. **Schnelligkeit:** eigene aktive API-Zeit des porträtierten Modells statt gesamte Matchdauer; Laufzeitvergleich mit Gegnern entfällt.
6. **Kein Overthinking-Beweis durch Budget-TKO/Tokenmenge**; kein Bonoma-Quadrant aus einem Sieg.
7. **Keine Writes in Original-JSONL/JSON/Engine**, keine neuen Paid Calls nur für den Export; keine WordPress-Live-Änderung aus diesem Dokument.
8. **Veröffentlichung nur nach Review und vorhandenem Journal-Launch-Gate**, nicht automatisch nach Import.

**Status:** Produkt-/Datenvertrag in Entwurfsfassung. Es gibt noch keinen produktiven App-Exporter und kein freigegebenes WordPress-Behavior-Plugin. Keine Rückdatierung der dokumentierten Konzepte als implementierte Features.
