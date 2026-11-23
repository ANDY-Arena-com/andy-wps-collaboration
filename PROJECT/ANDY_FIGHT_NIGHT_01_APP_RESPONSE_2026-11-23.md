# ANDY FIGHT-NIGHT-01 — Antwort aus App Development

**Datum:** 23. November 2026  
**Adressaten:** ANDY Journal / Fight Night, G-Analyzer und ANDY App Development  
**Auftrag:** Antwort auf das Memo „Vom Spiel zur Geschichte: Datenstandard für Match Stories und Fight-Night-Teaser“, 23.11.2026 (vom Projektleiter im ANDY-App-Chat als Text bereitgestellt).  
**Status:** **Anforderungsanalyse / Vorschlag, keine Implementierung, kein neues Schema freigegeben.**

## Grundentscheidung

**Match/Game** = unabhängig von der Redaktion dokumentierte Ereignisse, Konfiguration und Ergebnis samt Provenienz.  
**Match Story** = kuratierte, quellengestützte **Interpretation einer** Frage, Perspektive oder Überraschung; mehrere Stories pro Match möglich.  
**Fight-Night-Teaser** = redaktionell ausgewählter, kurzformatiger **Einstieg in eine Story** mit bis zu drei Highlights, „Reason Why“, Bild/Replay-Link. Der Teaser ist **kein** neuer Match-Faktenstore. Eine ungewöhnliche Statistik allein sollte keine Story automatisch publizieren.

**Pipeline (Vorschlag):** Original-JSONL + JSON → bereits bestehende Evidence-/Replay-Projektion → deterministische Beobachtungen mit Quellen und Methoden → G-Analyzer / kuratierte Match-Story-Annotation → Journal-Teaser. Keine zweite Partiewahrheit, keine automatische Originalmutation.

## A. Zehn interessanteste Datenpunkte / Beobachtungstypen (App-Perspektive)

| # | Beobachtungstyp | Aus Nutzersicht interessant, weil … | Beleg-/Automationsstatus |
|---|---|---|---|
| 1 | **Sportliches Ergebnis + tatsächlicher Endgrund** (Matt, Go-Kontrolle, KO/TKO, Abbruch, Limit) | es die Fallhöhe und das Ende erklärt | `match_end`/JSON oft dokumentiert; `runner_reported` von unabhängiger Regel-/Engine-Verifikation trennen |
| 2 | **Zwei Akteure, Farben und stabile Modell-/Provider-IDs** | der Vergleich überhaupt erst verständlich wird | in Konfiguration/Events meist verfügbar; Aliasse, Routing, Versionen teilweise lückenhaft |
| 3 | **Konfigurationsprofil und kontrollierter Farbwechsel** | ein überraschendes Resultat durch veränderte Bedingungen erklärbar sein *könnte* | dokumentierte Budgets, Limits, Awareness, Ruleset und Farbzuordnung; historische Runtime-/Modellversion teils unbekannt |
| 4 | **Schlüsselpositionen und regelgeprüfte Terminal-FEN/Go-Werte** | ein konkret sichtbarer Moment die Geschichte trägt | FEN/Go-Kontrolle im Archiv vorhanden; Endposition teils nur rekonstruiert oder im Runner dokumentiert; Verifikation gesondert |
| 5 | **API-Versuche vs. tatsächlich ausgeführte Aktionen** (Retries, Invalid, Deadlock) | Mühe und erfolgreiche Wirkung nicht dasselbe sind | JSONL-Entscheidungen mit `executed`; sachliche Ereignismarker möglich |
| 6 | **Budgetverlauf, Erschöpfung und Recovery/Refund-Bezug** | die Handlungsmöglichkeit nach einem Rückschlag fraglich wird | Match-/Segment- und Budgetfelder; Resume-/Refund-Ketten auf logische Partien normalisieren |
| 7 | **Input, Output, Reasoning/Thinking und Cache** | Denk-/Kommunikationsstile stark differieren | protokolliert, aber Providersemantik und Feldabdeckung unterschiedlich; fehlend ≠ null; keine Doppelsummen |
| 8 | **API-/Spielzeit und Setupphase** (z. B. 16 Go-Steine) | Verzögerungen, Konzentration des Aufwands und Tempo sichtbar werden | bei Eventzeiten/Phasen rekonstruierbar, Latenz ≠ gesamte Spielzeit |
| 9 | **Tarifbasierte Kosten, Kostenkurven und Kostendifferenz** | der Preis eines Ergebnisses überraschend sein kann | Economy-Observer mit modell-, zeit-, routeabhängigen approved Karten; Schätzung, nicht Rechnung; Wechselkurs getrennt |
| 10 | **Verlaufsmuster, Spiegelungen, Go-Kontrolle und Führungs-/Ereigniswechsel** | es visuelle Erzählbögen schafft | beobachtete Verläufe und Pattern-HEURISTIK verfügbar; „Führungswechsel“ nur mit **festgelegter, versionierter Messmethode** – nicht automatisch als tatsächlicher Vorteil |

**Journal-/Analyzer-Ergänzung:** Einen **Anomalie- oder Vergleichbarkeitsbeleg** neben jedem Highlight mitführen: Quelle, Ereignis-X, Bezugsspiel/Serie, Metrik, Methode, Zeitfenster und Qualitätsstatus. Insbesondere „erstmals“, „Rekord“, „größter“ nur mit definierter Grundgesamtheit.

## B. Mindeststandard: Was ist pro Match verpflichtend?

### B1. Technischer Datensatz („Match Fact Sheet“, klein)

**Pflicht bei jedem importierten Match, auch Kurztest/Abbruch:**
- `logical_match_id`; bekannte `segment_ids`/Parent-Bezüge mit Kennzeichnung von Lücken; Original-`match_id`.
- Quelleninventar: Vorhandensein und **Hash** von `<match_id>.jsonl` und `<match_id>.json` (oder explizit `missing`), Herkunft/Snapshot-Zeitpunkt; **kein raten**, wenn Quelle fehlt.
- Zwei Akteure: Originalanzeigenamen, normalisierte Modell-/Provideridentität **soweit belegbar**, Originalfarbe, ggf. `unknown`.
- Start-/Endstatus: Zeitstempel, ob final/abgebrochen/laufend, berichtetes Ergebnis oder explizit `unknown`; `result_provenance = runner_reported | engine_independently_verified | unverified | conflicting`.
- Konfigurationsstatus: vorhandene Ruleset-/Budget-/Cap-/Limit-/Profilfelder **mit Quelle und unbekannt-Markierung**.
- Abdeckung/Zählweise: Anzahl protokollierter Decisions/API-Aufrufe, ausgeführte Aktionen, Retries/Fehler soweit vorhanden, und fehlende Daten.
- Version des Normalisierers/Resolvers und die für die Ableitungen verwendete Event-Definition.

**Pflicht erst für eine veröffentlichte Match Story / Fight-Night-Teaser:**
- stabile `story_id` + `match_id`, verknüpfter Primärbeleg, redaktioneller Titel, **Reason Why**, bis zu drei evidenzverknüpfte Highlights, freigegebene Sprachversion(en) und Publikationsstatus.
- pro Highlight **Beweis + Evidenzqualität**; mindestens ein geprüfter visueller Bezug/Replay-Zeitpunkt oder eine explizite alternative bildliche Darstellung.
- **Redaktionelle Freigabe** (kein automatisches Publishing) und überprüfter Link zum tatsächlichen öffentlichen Ziel; ohne veröffentlichten Replay-Endpunkt keinen Link erfinden.

**Optional:** Good moment/longform narrative, exakte Provider-Rechnung, GI-Samples, historische Ratings, Agent-Thoughts, Geometrie-/Mirror-Indikatoren, Gegenfaktisches/Alternativzüge, Logos/Titelbilder, DE/EN/ZH. Die fehlenden optionalen Angaben verhindern keine Basiserfassung.

### B2. Trennung der Informationsarten (Pflicht für alle Consumer)

1. `reported_fact` – vom Runner/Originalbericht gemeldet, jedoch ggf. noch nicht unabhängig validiert.
2. `verified_fact` – durch passende technische Regeln und Quellen unabhängig geprüft.
3. `derived_metric` – deterministisch abgeleitet mit konkreter `method_version`, Zeit-/Tarif-/FX-Snapshot.
4. `detected_candidate` – algorithmischer Marker, ohne validierte redaktionelle Bedeutung (z. B. Spiegelung).
5. `analysis_hypothesis` – überprüfbare Einschätzung/Frage; **kein** Spiel-Fakt.
6. `editorial_selection` – Titel, drei Highlights, Reason Why und Freigabe; gehört zur Story, **nicht** in Match-Originale.

Dies sind **vorgeschlagene semantische Klassen**, keine Behauptung über vorhandene Datenbankspalten.

## C. Verfügbarkeit und Zuverlässigkeit

| Quelle/Funktion | Stand | Zu beachten |
|---|---|---|
| Original `jsonl + json` | Primärquelle; dokumentierter Import-/Archivvertrag | Historische Dateien teils fehlen `match_start/end`; logische Resume-IDs nicht addieren |
| SQLite-/Replay-Projektion | bereits vorhanden | abgeleitet; Fehlen in UI kann Projektionsverlust statt Datenlücke sein; nicht selbst als Quelle „beweisen“ |
| Konfigurationen (Budget/Cap/Strategie/A2) | bei S350 vollständig dokumentiert | bei älteren Spielen einzelne Felder/Engine-Version unbekannt |
| End-FEN/Go-Kontrolle | in S150/S350 archiviert | ggf. letzter Decision vs `match_end`; nicht als unabhängige Stellungsevaluation verwechseln |
| Decision/Executed/Fehler | in den archivierten S150/S350-Analysen belegt | Eventzählung ≠ ausgeführter Spielzug; Rechtsgültigkeit gesondert |
| Legacy Input/Output/Reasoning | häufig vorhanden; neuer Observer sichtbar | Argon-Reasoning nicht ausgewiesen ≠ 0; Providersemantik unbekannt |
| Economy USD/EUR/Usage | UI am 23.11. sichtbar, 249/249 Calls mit Kostenwert in S350 R1 | historische approved Nov-Tarifkarten; Schätzung, keine echte Anbieterrechnung; EUR umgerechneter UI-Faktor |
| Pattern/Mirroring | Live/Replay-Observer sichtbar | heuristisch; mögliche Geschichten, **keine nachgewiesene KI-Intention** |
| GI-Bewertungen | manuelle X-bezogene Stichproben | LLM-Meinungen; nicht mit offiziellen Resultaten gleichsetzen; Lücken bleiben Lücken |
| Visuelle Assets / Replay-Permalinks | Ausgangsdaten für FEN/Go/Observer vorhanden | **Automatischer Asset-Export, stabile öffentliche Replay-/Story-Deep-Links und CDN-Rechte noch nicht abgenommen** |

**Offene Code-/Runtime-Prüfung:** Das ist ein dokumentierter Bestandsabgleich, **kein aktueller Read-only-Scan des gesamten Mac-Codes**. Exakte Feldnamen, System-Endpunkte, Assets und Publisher-Rechte dürfen erst nach App-Code-/Browserprüfung als implementiert ausgegeben werden.

## D. Welche Highlights kann das System automatisch erkennen?

**Unmittelbar robuste **Kandidaten** aus dokumentierten Daten** (kein automatisches Story-Urteil):
- **Endevent**: Matt/Go-Regelabschluss/TKO/Limit/Abbruch als `highlight_candidate`, mit Runner-/Verifikationsstatus.
- **API-Fehl-/Retry-Cluster**: hoher Anteil `executed=false`, Serien zusammenhängender invalid/failed Attempts, sofern Event-Gründe dokumentiert.
- **Budget-Schwelle**: dokumentierter Restbudget-Wechsel/Erschöpfung, `budget_overshoot`, Refund-/Resume-Ereignis; Segment-/Regelkontext angeben.
- **Zeitspitze**: extrem lange API-Antwort oder Go-Setupphase relativ zu einer sauber definierten Vergleichsgruppe.
- **Kosten-/Usage-Ausreißer**: große modell-/zeitabhängig tarifierte Differenz oder hohe Output-Menge; Schätzungs-/Coverage-Badge und Vergleichsnenner, keine globale Wertung.
- **Endpositionsprofil**: aus belegter End-FEN/Go-Kontrolle statt unbegründetem Siegvorhersagescore.

**Nur nach zusätzlichem fachlichem Vertrag / nicht als belastbarer Auto-Trigger freigeben:**
- „Wendepunkt“/„Führungswechsel“, solange keine vergleichbare Positions-/Bewertungsfunktion existiert.
- „Strategiewechsel“, „Täuschung“, „psychologische Dominanz“, „bewusstes Spiegeln“ oder „Recovery“, falls lediglich aus Mustern/Text oder KI-Selbstauskünften geschlossen.
- „Rekord“, „erstmals“, „signifikant“, wenn Grundgesamtheit/Versionsstatus/Fehlerbehandlung fehlen.
- Rückwirkende GI-Bewertung ohne Nutzerauftrag oder als unverifizierte Zeitreihe.

**Pragmatischer Rule-Vertrag, vorgeschlagen:** `trigger_id`, `candidate_type`, `match_id`, `event_from/to`, `source_id+sha`, `metric_version`, `observed_value`, `comparator_scope`, `coverage`, `quality`, `review_status`. Kein neues Persistenzmodell festgelegt.

## E. Konkretes Beispiel für Fight-Night-Teaser + Story

**Match:** `andy_0c0f7413fdf6` — Serie `andy_cc11a6598bcf`, Runde 1 am 10.11.2026.  
**Akteure:** Astra (Weiß) vs. Gemini 4 Argon (Schwarz); 350k Tokenbudget **je Modell**, Output-Cap 4096, max. 500 Decisions, Retry 5, A2/master, `x_go_moves=1`, `reasoning_effort=default`, Ruleset v1.1. Modellbezeichnungen historisch aus Serienarchiv; exakt eingesetzter Provider-Build unbekannt.

### Redaktionelle Vorschau (VORSCHLAG, nicht veröffentlicht)

- **Titel:** „Schachmatt zum 25-fachen Preis?“
- **Motiv / Titelbild:** *aus originaler Schluss-FEN gerenderte Endposition*; FEN `3Q4/3R1k2/8/2K2B2/2P5/8/8/8 b - - 2 55`. Geprüfte Wiedergabe erforderlich, bevor das Bild veröffentlicht wird. Die Chess-Notation des letzten Zugs aus dem Archiv: `d2d7 / Rd7#`.
- **Highlight 1 (Runnerbericht):** Astra gewinnt als **Weiß durch Schachmatt**; bei gemeldeten Endwerten besitzt Argon nur den König, Astra Materialwert 18 (P1,N3,B3,R5,Q9 ohne König) und Go-Kontrolle 65 gegenüber 50. **Kein unabhängiger Engine-Check** protokolliert.
- **Highlight 2 (Ereignis-Aggregat):** **249 protokollierte Decisions/API-Aufrufe, 233 ausgeführte Aktionen**; Astra **117/117**, Argon **116/132** ausgeführt. Keine bewiesene Ursache der 16 nicht ausgeführten Argon-Aktionen ohne Einzel-Events.
- **Highlight 3 (tarifbasierte Economy-Schätzung):** Astra **7,90312 USD** vs. Argon **0,31678 USD**, Verhältnis **24,95 : 1** bei November-2026-Tarifkarten und im Observer **249/249** Call-Kostenwerten; Input/Output Astra **102.342/137.594**, Argon **134.220/4.834**. Keine Provider-Rechnungsfreigabe.
- **Reason Why (redaktionell):** „Zwei grundverschiedene Ressourcenprofile in einem dokumentierten Schachmatt. Was erklärt den höheren Output-Aufwand – und welche Teile davon halfen tatsächlich?“ *Eine Frage, keine Kausalantwort.*
- **Direkter Zugang:** Geprüfte öffentliche Journal-Story-/Replay-Links **noch nicht vorhanden**; im Konzept `match_id` + optional `event_x=249` bzw. Schlussposition als interner Zielanker. **Nicht als produktiven Permalink behaupten.**
- **Forschungsfragen:** (i) Output/Thinking relativ zu ausgeführten Aktionen und Phasen; (ii) Ursache der fehlgeschlagenen Aufrufe bei Argon; (iii) Unterschiede über Farbwechsel und 150k/350k-Versuche, ohne Budget-Kausalität zu suggerieren.

### Warum dieser Fall als MVP taugt

Er liefert **belegtes Ergebnis aus dem archivierten Runnerbericht, Original-FEN, Event-Zähler, visuell reproduzierbare Stellung und aktuellen Economy-Screenshot**. Die Schwesterpartie der 350k-Serie `andy_cc11a6598bcf` endete ebenfalls laut Runner mit Astra-Matt bei umgekehrten Farben (Astra Schwarz, Argon Weiß). Das erlaubt zusätzlich **eine zweite, serienspezifische Story**, darf aber nicht ohne Konfigurations-/Gegner-/Zeit- und Anbieterprüfung zu einer allgemeinen Modellwertung werden.

**Beweisquellen (jeweils getrennt):**
- [S350 Serienanalyse v0.1](../research/andy-lab/ANALYSES/andy_cc11a6598bcf/v0.1/README.md) — Ergebnis laut Runner, Konfiguration, Eventzahlen, FEN, Go, Material, Input/Output, archivierte Quellenhashes.
- [G-Analyzer Handoff 23.11.](ANDY_G_ANALYZER_THREAD_HANDOFF_2026-11-23.md) — aktueller 8080/8082-Observer-Screenshot mit USD/EUR, Calls, Zeitraum; Screenshot ist eine UI-Beobachtung und **keine unabhängige Revalidierung der Original-JSONL**.
- [Match-Evidence-Vertrag](ANDY_MATCH_EVIDENCE_JSONL_JSON_SQLITE_v1.0.md) — Status- und Quellenregeln.

## F. Minimaler versionierter maschinenlesbarer Vertrag — Diskussionsentwurf

**Vorschlag**, keine behauptete aktuelle Python-/DB-Schnittstelle:

```json
{
  "schema": "andy.match_story.v0.1-draft",
  "story_id": "story-andy_0c0f7413fdf6-economy-01",
  "match": {
    "logical_match_id": "andy_0c0f7413fdf6",
    "series_id": "andy_cc11a6598bcf",
    "segment_ids": [],
    "source_refs": [
      {"kind": "jsonl", "status": "archived_in_series_snapshot", "sha256": null},
      {"kind": "json", "status": "archived_in_series_snapshot", "sha256": null}
    ]
  },
  "facts": {
    "actors": [
      {"side": "white", "display_name": "Astra"},
      {"side": "black", "display_name": "Gemini 4 Argon"}
    ],
    "result": {
      "value": "Astra checkmate",
      "status": "runner_reported",
      "source_ref": "S350-2026-11-14-v0.1"
    },
    "config_ref": "S350-2026-11-14-v0.1"
  },
  "observations": [
    {
      "id": "calls-executed-r1",
      "event_scope": "full_match",
      "metric": "decision_calls_executed",
      "value": {"calls": 249, "executed": 233},
      "method_ref": "S350-2026-11-14-v0.1",
      "quality": "archived_derived_metric"
    },
    {
      "id": "cost-ratio-nov26",
      "event_scope": "full_match",
      "metric": "usd_estimate_ratio_white_black",
      "value": 24.95,
      "tariff_period": "2026-11",
      "rate_source": "observer_approved_tariff_cards",
      "fx_rate_eur_per_usd": 0.91,
      "quality": "tariff_estimate_not_invoice"
    }
  ],
  "editorial": {
    "status": "draft",
    "languages": {"de": {"title": "Schachmatt zum 25-fachen Preis?", "reason_why": "Was kostet Denkaufwand – und was davon wirkte im Spiel?"}},
    "highlight_refs": ["runner-result", "calls-executed-r1", "cost-ratio-nov26"],
    "hero_visual": {"type": "final_chess_fen", "fen": "3Q4/3R1k2/8/2K2B2/2P5/8/8/8 b - - 2 55", "render_status": "not_yet_verified"},
    "public_story_url": null,
    "public_replay_url": null,
    "approval": "pending"
  }
}
```

**Spezifikationshinweis:** Der Demo-JSON-Datensatz enthält bewusst **keine erfundenen Rohquellen-SHA**, öffentlichen Links, vollständige Provider-Modellversion, Replay-Pfad oder Schema-/API-Namen. Das ist eine logische Struktur, keine Importdatei für den aktuellen Code. Ein tatsächlicher Publisher sollte API/Model-/Ruleset-/Methoden-/Tarifversionen sowie `snapshot_as_of` und ggf. `supersedes` als echte referenzierbare Datensätze mitführen.

**Eindeutigkeit:** `match_id` identifiziert das Spiel, **`story_id` identifiziert die Perspektive**, `teaser_id` optional die Platzierung im Journal. X/Segment/Attempt als getrennte Provenienz. Verschiedene Storys dürfen denselben Fakt referenzieren; redaktionelle Sprachversionen ändern historische Fakten nicht.

## 15-Sekunden-Antwort aus App-Sicht

In genau diesem Fall würde ich zeigen:

1. **„Astra setzt Argon matt“** — verständliches sportliches Ereignis, korrekt als **Runnerbericht** gekennzeichnet.
2. **„7,90 $ vs. 0,32 $“** — die überraschende, belegte **tarifbasierte Kostenschere**.
3. **„249 Entscheidungen, 233 ausgeführte Aktionen“** — erklärt, dass der Weg zum Ergebnis nicht mit einer glatten Zügesequenz gleichzusetzen ist.

**Warum diese drei?** Ergebnis = Handlung; Kosten = überraschender Kontrast; Entscheidungs-/Ausführungsdifferenz = Forschungsfrage. Das finale Brett als echtes visuelles Motiv macht die Geschichte in einem Blick greifbar, aber **erst nach render-/regelbezogener Prüfung**.

## Umsetzungsreihenfolge (nur Plan)

1. **Kein neuer Code jetzt.** Ein gemeinsames redaktionelles Feldinventar und Provenienz-Klassen für Journal/Analyzer/App aus diesem Memo konsolidieren.
2. **Ein Golden Match** (S350 R1) in einem rein redaktionellen Prototyp durchdeklinieren, Quellen und finale Figurposition nachprüfen, keine Primärdaten umschreiben.
3. Danach eine zweite Story **aus derselben Partie** als Test für `story_id` versus `match_id` und Sprachversionierung.
4. Erst später einen read-only Export / Publisher-Vertrag freigeben; niemals automatische Veröffentlichungen aus heuristischen Observer-Marken.

**Leitmotiv:** Erleben → Erforschen → Erahnen. Die belastbare Geschichte entsteht nicht durch mehr Text, sondern durch **wenige starke Fakten und die richtige, ergebnisoffene Frage**.
