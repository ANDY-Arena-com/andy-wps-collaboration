# ANDY – START HIER (für neue Threads und beteiligte KI-Systeme)

**Stand:** 13.11.2026 · **Status:** gemeinsames Kurzbriefing; Masterplan hat Vorrang

> **Aktuelle App-/Serien-Übergabe (13.11.2026):** [8082 RESULT-02 / SERIES-02 Fixstand und SERIES-03-Folgearbeiten](ANDY_APP_8082_SERIES_HANDOFF_2026-11-13.md). Drei Regressionstests auf 8082 bestanden; Live-Abnahme und 8080-Sync noch offen. Diese Übergabe vor App-Arbeiten lesen.

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
