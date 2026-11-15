# ANDY – START HIER (für neue Threads und beteiligte KI-Systeme)

**Stand:** 15.11.2026 · **Status:** gemeinsames Kurzbriefing; Masterplan hat Vorrang

> **Neue Architekturentscheidung (15.11.2026):** [ANDY Factory – Drei-Instanzen-Architektur V0.1](ANDY_FACTORY_THREE_INSTANCE_ARCHITECTURE_v0.1.md). Ziel: 8080 STUDIO (Arena/Designer), 8082 SANDBOX (technische Experimente), 8083 FACTORY (freigegebener autonomer Forschungsbetrieb). Zuerst **SYNC-05**: vollständiger beidseitiger Funktionsabgleich, gemeinsamer geprüfter Release; danach getrennte 8083-Instanz, kontrollierte Datenmigration, persistente Match Queue und begrenztes Autoplay auf der bestehenden Serial-Engine. SYNC-04 technisch bestätigt (201 Tests, 30/30 Zieldateien), OUTPUT-LIMIT-01 auf 8080 grün gemeldet. 8083 und Autoplay noch nicht implementiert. Dieses Memo aktualisiert die operativen Rollen und den nächsten App-Arbeitsschritt gegenüber den älteren Übergaben.
>
> **Aktuelle App → Lab Übergabe (14.11.2026):** [Serienbetrieb, Evidence Builder und Experiment-Profile](ANDY_APP_LAB_SERIES_HANDOFF_2026-11-14.md). Operativ bestätigter Live-Resume-Referenzfall, logischer Match-Resolver, zwei verifizierte Exportpakete (7 logische Partien / 8 Segmente im Mehrserienexport), Kategorie 2, Serienprofile und kompakter Serien-Manager; historischer Rückkampf erfolgreich bestätigt; SYNC-02 technisch abgeschlossen (8080: 60 Regressionstests im letzten Installer, 32/32 Patch-Dateien bestätigt), Browser-Abnahme offen. 8082 Forschungsbetrieb, 8080 Arena-Entwicklung. Vor neuen App- oder Lab-Aufgaben lesen. Enthält tatsächliches Exportformat, Bedienwege, Analysegrenzen und Abnahme-Gates.
>
> **Historische App-/Serien-Übergabe (13.11.2026):** [8082 RESULT-02 / SERIES-02 Fixstand und SERIES-03-Folgearbeiten](ANDY_APP_8082_SERIES_HANDOFF_2026-11-13.md). Drei Regressionstests auf 8082 bestanden; Live-Abnahme und 8080-Sync noch offen. Diese Übergabe vor App-Arbeiten lesen.

## 1. Zuerst lesen

1. **[ANDY 2.0 – Masterplan v1.0](ANDY_GESAMTKONZEPT_MASTERPLAN_v1.0.md)** – zentrale Vision, verbindliche Prinzipien, Forschungsarchitektur und Roadmap.
2. Je nach Aufgabe: [Lab-Memo zu Intention, Antizipation und Responsivität](../research/andy-lab/ANDY_LAB_MEMO_Intentions_Antizipation_Responsivitaet_v0.1.md).
3. Bei Matcharchiv, Replay, Rückkämpfen, Lab-Import und Ergebnissen: [Match-Evidenzvertrag JSONL + JSON → SQLite v1.0](ANDY_MATCH_EVIDENCE_JSONL_JSON_SQLITE_v1.0.md).
4. Anschließend den tatsächlich vorhandenen Code, Branch, Commit, Original-JSONL und – soweit vorhanden – den originalen Matchbericht JSON oder letzten nachweislich funktionierenden Release untersuchen. **Nicht** auf Basis einer Chat-Zusammenfassung behaupten, dass eine Funktion existiert oder getestet ist.

## 2. ANDY in 30 Sekunden

**ANDY (Actor. Network. Dynamics.)** kombiniert Schach und Go auf einem gemeinsamen 13×13-Brett. KI-Modelle treten unter regelgebundenen Bedingungen und Token-Budgets gegeneinander an. Original-Spielereignisse werden protokolliert.

**Leitmotiv:** *Erleben. Erforschen. Erahnen.*

- Arena: Fight Night / Replay / Erlebnis.
- App & Designer: Engine, Spielbetrieb, UI.
- Lab: reproduzierbare individuelle und vergleichende Matchanalysen.
- Journal: Geschichten, Forschungskommunikation und Making-of.
- Open Research Corpus: originale JSONL, geprüfte Zustände, Claims, Forschungsberichte, mögliche spätere Training-/Evaluations-Releases.

**Öffentliches Marketing:** Nicht primär mit dem Begriff „Benchmark“ auftreten; Datenvergleiche und wissenschaftliche Einschränkungen trotzdem klar benennen.

## 3. Sofort verbindliche Forschungsdisziplin

- **Aussagen eines Modells sind beobachtete Texte, keine inneren Gedanken.**
- Unterschied zwischen Zugversuch, tatsächlich ausgeführtem Zug, Regelfehler, Antwortformatfehler und API-Fehler.
- „Diese Folge geschah“ ist nicht dasselbe wie „diese Folge war erzwungen“.
- Originaldaten unverändert; abgeleitete Daten mit Quelle/Hash/Version.
- PDF für Menschen und JSON/JSONL für Maschinen aus derselben Datenbasis.
- E3: Effektivität und Effizienz bekannt; dritte Komponente **vor Publikation anhand der ursprünglichen Primärdokumente klären**.
- Bei Trainingsdatennutzung: Lizenz-/Providerbedingungen, Datenschutz, Datenqualität, Leakage und unabhängige Evaluation beachten.

## 4. Bekannte Ausgangslage (immer aktualisieren)

- Arena: Website `andy-arena.com` mit DE/EN/ZH und Replay; aktuelle Designreferenz V0.8.4.2 ([Release-Nachweis](WEB/WEBSITE_RELEASE_V0842_2026-11-14.md)), lokal visuell freigegeben, produktiver Stand und vollständige Plattformabnahme offen.
- Blog: `blog.andy-arena.com`, öffentliche Coming-Soon-`index.html`; WordPress dahinter; Blog wird separat entwickelt.
- GitHub: `ANDY-Arena-com/andy-wps-collaboration`.
- Pilot: sechsseitiges PDF zu Astra/Gemini 4 Argon; Forschungsausbau auf 18–24 Seiten und vergleichende Ausgabe vorgesehen.
- Frühe dokumentierte Matches: `andy_0c0f7413fdf6`, `andy_64c8f95436d1`, `andy_1c77f49b3e17` (letzteres Go-Ende noch nicht unabh. geprüft).

## 5. Vorgehen bei jeder neuen Aufgabe

1. Auftrag und Arbeitsbereich benennen; existierende Dateien und Abhängigkeiten prüfen.
2. Bestätigten **Ist-Zustand** von Ideen und Hypothesen trennen.
3. Kleine, testbare Lösung entwerfen; bestehende Funktionen schützen.
4. Bei Veröffentlichungen Quellen/Validierungsstatus angeben.
5. Ergebnis liefern (Code/PDF/Daten/Issue) **im aktuellen Arbeitsdurchgang**, nicht nur ankündigen.
6. Testnachweis und offenen Rest klar dokumentieren.
7. Bei strategisch relevanten Entscheidungen Masterplan als versionierte Folgefassung/Commit fortschreiben.

## 6. Vorlage für eine konkrete Thread-Übergabe

```markdown
# ANDY Fachthread-Übergabe
Arbeitsstrang / Ziel:
Masterplan-Version und Link:
Repository / Branch / Commit oder letzter ZIP-Release:
Verfügbare Originaldaten, Regelschema, Engine-Version:
Bereits implementiert und tatsächlich getestet:
Nur geplant / nicht geprüft:
Jüngste Entscheidungen:
Offene Bugs / Unsicherheiten:
Konkreter nächster Schritt:
Abnahmekriterien und Rückfallversion:
```

**Regel bei Konflikten:** Aktuelle Primärdaten und geprüfter Code schlagen ältere Chat-Erinnerungen. Strategische Abweichungen gegenüber dem Masterplan bewusst dokumentieren, nicht stillschweigend einführen.


## Aktueller Website-Release-Stand (14.11.2026)

**V0.8.4.2 – Final Polish** ist die jüngste vollständige Website-Entwicklungsreferenz, lokal visuell vom Projektleiter freigegeben. [Release-Nachweis, Prüfsumme und ANDY Player Identity Module](WEB/WEBSITE_RELEASE_V0842_2026-11-14.md). V0.8.3.6 bleibt historisch dokumentiert. Hostinger-Deployment, vollständige plattformübergreifende Abnahme und GitHub-Binärarchivierung bleiben offen; Windows-TLS ist separat zu behandeln.


## ANDY Lab – Analysekompass V0.1 (14.11.2026)

[Freigegebene Arbeitsgrundlage für die weitere Datensammlung](../research/andy-lab/ANALYSEKOMPASS/v0.1/README.md): Erleben (Rot), Erforschen (Grün), Erahnen (Blau); drei Stabilitätsstufen, Sweet Spot? (interpretiert/unkalibriert), Antizipation und Reaktion, Spielreihen, Model Behavior Cards und Challenger-Zusammenarbeit. Datensammlung vor Kalibrierung; keine endgültige Modellklassifikation. Ausgangstabelle und sechs SVG-Grafiken liegen im selben Verzeichnis.


## ANDY Lab – Gemeinsamer Erkenntniskern (14.11.2026)

[CORE V0.1](../research/andy-lab/CORE/v0.1/README.md) ist von Projektleitung, ChatGPT, DeepSeek und Qwen im Dialog freigegeben. Erkenntnis als adaptive Stabilisierung ist die verbindende Mitte des Labs; Sweet Spot?, Competitive Mirroring, Dynamic Bonoma und Nested Competitive Networks bleiben konzeptionell. [Konsensmatrix](../research/andy-lab/CORE/v0.1/02_KONSENSMATRIX.md), [Mensch × KI](../research/andy-lab/CORE/v0.1/08_MENSCH_KI.md). Keine Änderung der bestehenden Messverfahren/Hypothesen-IDs; Datensammlung vor Kalibrierung.


## Strategisches Memo – Dezentrale Erkenntnisökonomie (14.11.2026)

[GAME 4 LAB → LAB 4 AI → AI 4 GAME · Memo V0.1](ANDY_MEMO_DECENTRALIZED_RESEARCH_ECONOMY_v0.1.md): freiwillig weltweit gespielte Matches als mögliche Quelle zusätzlicher API-Nachfrage und eines gemeinsamen, kuratierten Open Research Corpus; potenzieller Wert für Evaluation und Trainingsdaten, Anbieterförderung unter Wahrung der wissenschaftlichen Unabhängigkeit. Erfahrungswert 2–5 EUR je Partie, illustrative Skalierung, keine Preis-/Umsatzprognose. Strategische Perspektive, kein Implementierungsauftrag und keine Trainingsfreigabe.


## App → Lab – CACHE-01 / Usage Audit & Cache Control (14.11.2026)

[Technisches Memo V0.1](ANDY_CACHE_01_IMPLEMENTATION_MEMO_v0.1.md) konsolidiert die Briefings von Gemini, Claude, DeepSeek und Qwen mit GPT-Review. **SYNC-03 (8082 → 8080) erfolgreich laut Projektleitung. Nächster Schritt: CACHE-01A, read-only/offline auf 8080.** Danach Usage Normalizer (korrigierter Testvertrag UN-01–17), versionierte Kosten, Cache Control, Prompt-Experimente und Lab-Integration. Historische Budgetlogik und Originaldaten unverändert; kein API-Aufruf ohne Freigabe. Provider-Mappings sind bis zum konkreten Endpoint-Audit vorläufig. [Tarif-Snapshot](../research/andy-lab/REQUIREMENTS/v0.1/API_COSTS_CACHE_2026-11.md).


## Nächster App-Meilenstein – SYNC-05 / ANDY Factory (15.11.2026)

[Architektur- und Entwicklungsauftrag V0.1](ANDY_FACTORY_THREE_INSTANCE_ARCHITECTURE_v0.1.md). Die bisherige Trennung in Arena-Entwicklung und Forschungsbetrieb wird zum Drei-Instanzen-Zielbild erweitert. Code-Sync und Archivmigration strikt trennen. Originaldaten und logische Match-IDs erhalten; keine neue Serial-Engine. Autoplay nur mit freigegebener Queue, Ressourcenlimits und sicherem Stopp. Nächster Schritt: lesender Audit der tatsächlichen lokalen Quellstände, keine kostenpflichtigen API-Aufrufe und keine Unterbrechung laufender Partien.
