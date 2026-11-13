# ANDY Lab — Comparative Research Edition 001
## *When Plans Meet Reality*
### A Comparative Analysis of AI Decision-Making in the ANDY Arena

**Status:** Verbindlicher redaktioneller **Ziel-Blueprint** (24 Seiten); **kein** fertiger oder wissenschaftlich freigegebener Bericht  
**Version:** v0.1 · **Datum:** 13. November 2026  
**Zuordnung:** [ANDY-Gesamtkonzept](../../PROJECT/ANDY_GESAMTKONZEPT_MASTERPLAN_v1.0.md) · [Lab-Memo: Intentionen, Antizipation, Responsivität](ANDY_LAB_MEMO_Intentions_Antizipation_Responsivitaet_v0.1.md)  
**Anlass:** Im Projektgespräch explizit festgehaltene 24-Seiten-Gliederung; nicht durch eine vorzeitige PDF-Gestaltung oder eine unvollständige Datensammlung ersetzen.

> **Leitentscheidung:** Zunächst eine gemeinsame, überprüfbare Analyse- und Datenpipeline aufbauen; **dieses 24-Seiten-Konzept bleibt die Zielarchitektur** der ersten Comparative Edition. Aus denselben validierten Fakten entstehen die menschlich lesbare PDF-Ausgabe und eine maschinenlesbare Edition. Fehlende Daten/Tests werden sichtbar markiert, nicht erfunden.

## 1. Originale 24-Seiten-Gliederung (aus dem ANDY-Dialog gesichert)

| Nr. | Kapitel | Seiten | Geplante PDF-Seiten |
|---|---|---:|---|
| 01 | Titel, Abstract, Executive Summary | **2** | 1–2 |
| 02 | Forschungsdesign, Regeln, Datenbasis | **3** | 3–5 |
| 03 | Matchprofile und Ausgangssituationen | **2** | 6–7 |
| 04 | Vergleich von Ressourcen und Spielverläufen | **3** | 8–10 |
| 05 | Antizipation, Ankündigungen und tatsächliche Handlungen | **4** | 11–14 |
| 06 | Fallstudien ausgewählter Wendepunkte | **4** | 15–18 |
| 07 | Vergleichende Befunde und Gegenhypothesen | **3** | 19–21 |
| 08 | Limitationen, Reproduzierbarkeit, Quellen | **3** | 22–24 |
| | **Gesamt** | **24** | |

**Seitenbudget:** Zielvorgabe für den ersten Entwurf, nicht Grund, wissenschaftliche Belege wegzulassen oder Lücken künstlich zu füllen. Umfangsänderungen nur als dokumentierte redaktionelle Entscheidung. Zusätzliche umfangreiche Daten/Quellen ggf. über GitHub-Anhänge statt im PDF.

## 2. Was auf die Seiten kommt (redaktionelle Feinstruktur)

### S. 1–2 — Titel / Abstract / Executive Summary
- Cover: Titel, Edition-ID, Datum, Version, Autoren-/Redaktionshinweis, drei beteiligte Match-Kontexte.
- Präziser Abstract: Forschungsfragen, Studiendesign, Quellen, gesicherte Beobachtungen, wichtige Limitierungen.
- Executive Summary als nachprüfbare Kernaussagen, **keine Sieger-Rangliste** oder Rückschlüsse auf allgemeine Intelligenz.

### S. 3–5 — Forschungsdesign / Regeln / Datenbasis
- ANDY: gemeinsames 13×13-Brett; Schach/Go; regelrelevante Endbedingungen.
- Herkunft der Partien; Einschluss-/Ausschlusskriterien; Modell-/API-/Prompt-/Budget-/Engine-Versionen; Spielseiten und Color-Swap-Kontext.
- Wie Entscheidung, ausgeführter Zug, fehlerhafte Antwort, illegaler Zug und terminales Event jeweils gezählt werden.
- Fehlerquellen, Vergleichbarkeit, Regelvalidierung, Status der Engine-Rekonstruktion.

### S. 6–7 — Matchprofile / Ausgangslagen
- Je Match: Match-ID, Akteure/Seiten, Datum, Ausgangslage, Budgets, Dauer, Anzahl API-Entscheidungen / ausgeführter Züge, terminales Ergebnis mit Prüfstatus.
- Gegenüberstellung der Startstellungen, Matchkonfigurationen und möglichen Unterschieden.

### S. 8–10 — Ressourcen und Spielverläufe
- Grafiken: kumulierte Input-/Output-/Gesamt-Token pro Akteur, Entscheidungen, Fehlversuche, Zeit.
- Chess- und Go-Ereignisse auf kompatibler Ereignisachse; Go-Kontroll-Verlauf und Endwerte als **Kontrolle**, nicht voreilig als eigenständiger Sieg.
- Verhältniszahlen/Normalisierung inkl. Nenner und Provider-Usage-Limitationen.
- Diagramme als Code reproduzierbar; Quelle, Zählweise und Achsenbeschriftungen angeben.

### S. 11–14 — Antizipation / Ankündigung / Handlung
- Claim-Taxonomie: Absicht, eigener Zug, Prognose gegnerischer Antwort, Ziel, behauptete Zwangslage, Kontext-/Risikoaussage.
- Pro Aussage: Originalspanne, Ereignis-ID, angekündigter Horizont, ausgeführte Aktion, Reaktion, Ergebnis, Prüfstatus.
- Ausgewählte dokumentierte Treffer, Nicht-Treffer, mehrdeutige Fälle; **kein** Mental-State-Reading.
- Unter geeigneten Datenbedingungen: Claim/Outcome-Kennzahlen mit transparenten Ein-/Ausschlüssen und Unsicherheit.

### S. 15–18 — Fallstudien konkreter Wendepunkte
- 2–4 Fallstudien mit Diagrammen der Brettzustände (Vorher/Nachher), Chronologie und konkurrierenden Lesarten.
- Kandidat: Astra–Claude Schlussfolge #139/#141/#143/#145/#146/#147 (Vorhersage trifft beobachtet ein; „erzwungen“ separat prüfen).
- Kandidat: Astra–Argon Bauernumwandlung/Schlussmatt und Argon-Fehlversuche.
- Kandidat: Flash–Argon Go-Endbedingung **nur bei Engine-verifiziertem terminalem Ereignis** als bestätigter Sieg.
- Keine reine Chronologie als bewiesene kausale Wendung deklarieren.

### S. 19–21 — Vergleichende Befunde / Gegenhypothesen
- Muster nur über dokumentierte, möglichst vergleichbare Fälle hinweg diskutieren.
- Alternativerklärungen: Farbe, Startrechte, Gegner, API/Version/Prompt, Budget, Re-try-Logik, Regeldetails, Stichprobenselektion.
- Explizite Tabelle: Beobachtung → mögliche Interpretation → Gegenhypothese → erforderliche Prüfung.
- Kein allgemeines Modell-Ranking aus kleiner, heterogener Fallauswahl.

### S. 22–24 — Limitationen / Reproduzierbarkeit / Quellen
- Begrenzung der Stichprobe, Versions-/Provider-/Zuglogik; Grenzen der Modelltexte.
- Manifest der verwendeten JSONL-Dateien mit SHA-256, Ruleset/Engine-/Parser-/Schema-Version und Auswerteskripten.
- Status je Befund (protokolliert / engine-geprüft / Hypothese / offen / widerlegt), Review- und Publikations-Gates.
- GitHub-Links, ggf. QR-Codes; Quellen, Glossar, Versionierung und nächster Forschungsbedarf.

## 3. Initialer Pilot-Korpus und Status

| Match-ID | Referenz | Vorläufiges Prüf-/Forschungsziel |
|---|---|---|
| `andy_0c0f7413fdf6` | Astra (weiß) vs Gemini 4 Argon (schwarz) | protokolliertes Matt Weiß; Format-/Legalitätsversuche, Tokens, späte Claims |
| `andy_64c8f95436d1` | Astra (weiß) vs Claude Opus 5.5 (schwarz) | protokolliertes Matt Weiß; #143 Prognose, #145 Antwort, #146 Go, #147 Matt |
| `andy_1c77f49b3e17` | Gemini 3.8 Flash vs Gemini 4 Argon | möglicher Go-Sieg Schwarz; **terminales Ereignis/Engine noch zu prüfen** |

**Wichtig:** Diese Matchreferenzen und die frühere sechsseitige Research Edition sind Ausgangspunkte, **keine** vollständige Validierung aller Daten. Nur geprüfte Zahlen und zugelassene Primärquellen in finale Tabellen/Abbildungen übernehmen.

## 4. Technisches Arbeitsprodukt vor dem Layout

Geplante gemeinsame Pipeline:

```text
Original-JSONL + Manifest + Ruleset/Engine
   ├─ sha256 / Quelle / unveränderte Archivierung
   ↓
Parser und normalisierte, schema-validierte Ereignisse
   ↓
regel-/engine-geprüfte Brettzustände und Resultate
   ↓
Claim-Extraktion + unabhängige Annotation/Review
   ↓
vergleichbare Kennzahlen + reproduzierbare Grafiken
   ↓
Research Dossier (versioniertes JSON/JSONL + Markdown)
   ├─ Comparative Research Edition PDF (24 Seiten)
   └─ Datenpaket für KI-lesbare Analysen / Journal-Quelllinks
```

**Mindestfelder pro Match:** Match-ID; Originaldatei/Prüfsumme; Zeitpunkt; Akteursnamen/Modelle/API-Versionen; Farb-/Startzuweisung; Prompts/Token-Budget und -Usage; Ruleset/Engine-Version; Ereignis-ID; Typ; vor/nach Zuständen; Zugversuch; Legalitäts-/Formatstatus; tatsächlicher Zug; terminales Ereignis; Quelle und Validierungsstatus.

**Mindestfelder pro Claim:** Claim-ID; Match-/Ereignis-ID; unveränderte Quelltextspanne/Position; Typ; Bedingung/Horizont; Gegenüberstellung Handlung/Ereignis; Bewertung, Prüfmethode und Unsicherheitsgrund.

**Qualitätskontrollen:**
- Summe Entscheidungen = ausgeführte Züge + nicht ausgeführte Entscheidungen (mit ausdifferenzierten Ursachen).
- Pre- vs Post-State nicht verwechseln; Zug- und Original-JSONL-Zeilennummern unterscheiden.
- Tokens/Zeiten nur soweit vorhanden; keine fiktiven Nullwerte für fehlende Daten.
- Matchende über Engine/terminales Log prüfen; Go-Kontrolle ≠ automatischer Sieg.
- Grafiken/Tabellen mit identischen Quellen und Versionen wie das maschinenlesbare Dossier.
- Veröffentlichen erst nach passender Lab-/WPS-Freigabe.

## 5. Konkrete Meilensteine

| Gate | Ergebnis | Abnahmebedingung |
|---|---|---|
| **M0 — Dateninventur** | Liste aller Original-JSONL/Engine/Regeln inkl. Herkunft | Vorhanden/nicht vorhanden/zu prüfen explizit dokumentiert |
| **M1 — Parser & Schema v0.1** | Ereignisse und Fehlerklassen | maschinelle Tests gegen reale Matchlogs |
| **M2 — Verifikation** | Regeln/Endbedingungen/Brettzustände | reproduzierbare Prüfprotokolle; offene Fälle markiert |
| **M3 — Claims & Diagramme** | Forschungsdossier mit Belegreferenzen | nachprüfbar, kein erfundenes „Denken“ |
| **M4 — Erstes Individual PDF** | 18–24 Seiten, z. B. Astra–Argon | fachliches Review und Formatabnahme |
| **M5 — Comparative PDF 001** | **24 Seiten nach Kapitelraster oben** | 2+ datenkompatible Fälle, Vergleichseinschränkungen, Quellen und Freigabegates |
| **M6 — Maschinenlesbare Edition** | abgeglichene strukturierte Auswertungen | gleicher Daten-/Script-Stand wie PDF |

**Reihenfolge:** M0 → M1 → M2 → M3. M4/M5/M6 verwenden dieselbe überprüfte Datenbasis; M4 und M5 sind unterschiedliche redaktionelle Produkte.

## 6. Was bei einem Threadwechsel erhalten bleiben muss

1. Den [Masterplan](../../PROJECT/ANDY_GESAMTKONZEPT_MASTERPLAN_v1.0.md) und **dieses 24-Seiten-Blueprint** lesen.
2. Nachvollziehbar zwischen bereits geprüft, angenommen, geplant und offen unterscheiden.
3. Für jede Änderung des Seitenbudgets/Studienumfangs eine dokumentierte Entscheidung treffen.
4. Neue Daten-/Engine-/Schema-Funde mit Pfad, Commit, Hash und Versionsstand ergänzen.
5. Nie einen fertigen Report behaupten, wenn nur ein Konzept oder Pilot existiert.

## 7. Offene Fragen (bewusst nicht erfunden)
- Welche vollständigen Original-JSONL und historischen Engine-Versionen sind verfügbar?
- Wie wird die dritte E3-Dimension offiziell bezeichnet?
- Welche Rechte erlauben eine öffentliche Wiederveröffentlichung bzw. spätere Trainingsverwendung der Modelltexte?
- Welche Fälle lassen sich fair vergleichen? Welche Matchs brauchen Ausschluss-/Sensitivitätsanalysen?

---
**Redaktionelle Leitformel:** *Die 24 Seiten sind die erzählerische Struktur. Das versionierte Dossier ist der wissenschaftliche Unterbau.*
