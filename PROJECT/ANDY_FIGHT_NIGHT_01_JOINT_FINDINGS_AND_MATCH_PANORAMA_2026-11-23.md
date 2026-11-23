# ANDY FIGHT-NIGHT-01 – Gemeinsame Auswertung von App Development und G-Analyzer

**Datum:** 23.11.2026  
**Beteiligte:** ANDY App Development, G-Analyzer / Living Lab, ANDY Journal / Home Composer  
**Status:** Zusammengeführter **Arbeits- und Anforderungstand**; keine Schema-, Publisher-, Match-Ergebnis- oder WordPress-Implementierungsfreigabe.  
**Auslöser:** Journal-Memo „Vom Spiel zur Geschichte“; die vollständige App-Antwort liegt bereits separat in GitHub, die vollständige Analyzer-Antwort wurde am 23.11.2026 im Journal-Thread bereitgestellt. Diese Datei dokumentiert die **Synthese und Differenzen**, keine erfundenen zusätzlichen Befunde.

## 1. Entscheidungsvorlage: Nicht vom Slider, sondern vom belegten Match zur Geschichte

Gemeinsame Grundlinie beider Fachthreads:

1. **Match Evidence:** unveränderte JSONL + JSON als Primärbelege. Match-IDs, Konfiguration, Akteure, Events, Entscheidungen, Ausführungen, Nutzung, Runner-Endzustand und Quellenqualität. SQLite, Replay, Observer und Screenshots sind **abgeleitete Ansichten**, nicht eine zweite Originalwahrheit.
2. **Analysis / Story Signals:** maschinell nachprüfbare Messwerte; heuristische Auffälligkeiten als *Kandidaten*, mit Event-/Zeitfenster- und Methodenversion, niemals automatisch Kausalbeweise oder Veröffentlichungen.
3. **Editorial Story:** eigenständige **story_id** mit redaktioneller Perspektive, belegten Highlights (0 bis 3, nicht verpflichtend immer 3), Reason Why, Gegenhypothese/offener Frage, Medien, Sprache und Freigabestatus.
4. **Presentation:** Home Composer / Fight Night / Research / Academy / Panorama-Module erhalten **nur referenzierte, freigegebene Story-Daten**; sie schaffen keinen weiteren Match-Faktenstore.

Leitprinzip: **Ein Match → mehrere mögliche Stories → mehrere Darstellungen.** Und: Eine Series Story darf mehrere Matches, eine Research Story mehrere Belegquellen umfassen. Kein Zwang, langwierige oder ereignisarme Partien zur Fight Night zu machen; solche Fälle können wissenschaftlich wertvolle Research-Cases werden.

## 2. Fachlicher Vergleich: Worin stimmen App und Analyzer überein?

| Thema | App Development | G-Analyzer | Gemeinsamer Arbeitskonsens |
|---|---|---|---|
| Ergebnis | Runner-Meldung vs. engineverifiziert | Gleiche Verifikationsgrenze | **result_provenance** verpflichtend, nicht „Matt bewiesen“ ohne Regelcheck |
| Event-Zählung | API/decision, attempt, retry, executed, Game-Turn getrennt | Gleiche Trennung | Nie „249 Spielzüge“ aus 249 Decision-Events ableiten |
| Ressourcen | Input/Output/Reasoning, Cache, Budget, Tarif-/FX-Snapshot | Paradox / Vergleich und Effizienz | Kosten = **Schätzung**, nicht Provider-Rechnung; fehlendes Reasoning ≠ 0 |
| Auffälligkeiten | Regeln, Limits, TKO, Invalids, Retry-Cluster, Positionen | Strategiewende, Says vs. Does, Recovery, Muster, Netzwerke | Robuste Trigger vs. **heuristische Verdachtssignale** getrennt |
| Vergleichbarkeit | Modell-/Providerroute, Budget, Farbe, Ruleset, Segment, Build | Konfigurations- und Serieneffekte | Keine pauschale Modellstärke aus einer Partie |
| Bilder / Replays | geprüfte FEN/Go-Positionen und stabile Assets noch nicht für alle Fälle publiziert | visuelle Belege aus Archiv, teils rekonstruierbar | Herkunft, Frame/Event, Version, Verifikation und Bildrechte dokumentieren |
| Redaktion | Match/Story getrennt, Freigabe erforderlich | Spiel → Kontrast → Forschungsfrage | **Wenige starke Aussagen**, nicht vier Stunden als Erlebnis ausgeben |

**Ergänzung aus Analyzer:** Schwerpunkt auf **Beziehungen** zwischen Akteuren, Ereignissen, Ressourcen und Ergebnissen – insbesondere strategische Wendung, Ressourcenparadox und Netzwerkdynamik. Eine erkenntnisreiche Story kann **erst durch Serienvergleich** entstehen.

**Ergänzung aus App:** Quellenpaar, Hash, Normalisierer-/Metrikversion, logische Match-/Resume-IDs, tatsächlich ausgeführte Aktionen und voraussichtlich belastbare Exportfelder früh absichern. Verifikation nicht durch UI-Darstellung ersetzen.

## 3. Redaktionelle Typen und Routing ins Journal

| Typ | Bezug | Primärer Kanal | Home-Darstellung |
|---|---|---|---|
| **Match Story** | 1 Partie, 1 Schwerpunkt | Fight Night **oder** Research | Große Fight-Night-Bühne / Match Panorama / horizontale Themenreihe |
| **Series Story** | mehrere zusammengehörige Partien / Vergleich | Research / Perspectives, ggf. Fight Night | Vergleichs-Teaser, seitlicher Intro-Scroller |
| **Research Story** | Hypothese, Daten oder methodische Frage aus mehreren Quellen | ANDY Lab / Research | Datenbühne / Research-Scroller / Panorama |
| **Player's Perspective** *(offene spätere Variante)* | Modell-Selbstaussage zum eigenen dokumentierten Verhalten | Research | Redaktioneller Textvergleich mit Quellen; niemals Modellantwort als gesicherte Verhaltensursache |

Jede redaktionelle Story erhält eigene ID und kanonische URL; mehrere Stories dürfen auf dasselbe logische Match zeigen. Ein Modul wählt Story-IDs, nicht kopierte Artikeltexte.

### Die 15-Sekunden-Regel für Teaser

1. **Was geschah?** Ein belegbares, sofort verständliches Ereignis.
2. **Was ist daran ungewöhnlich?** Ein nachvollziehbarer Kontrast, nicht zwingend eine Statistik.
3. **Welche offene Frage folgt?** Reason Why als Einladung zum Lesen, **nicht** als kausale Behauptung.

## 4. Golden Match: Astra (Weiß) gegen Gemini 4 Argon (Schwarz)

**Eindeutige Match-ID:** andy_0c0f7413fdf6. **Serie:** andy_cc11a6598bcf. **Serienanalyse nennt Runde 1 (0-basiert)** am 10.11.2026; ein kurzer Vorschlag aus dem App-Thread nennt „Runde 2“ im umgangssprachlichen Sinn. Für technische Datensätze **Rundenindex 1** verwenden und sichtbare „zweite Partie“ nur bei redaktioneller Klarstellung. **S350**: je 350.000 Tokens, Output-Cap 4.096, maximal 500 Entscheidungen, Ruleset v1.1; weitere Einstellungen und historische Provider-Builds laut Serienanalyse/App-Rückmeldung behandeln.

| Größe | Astra / Weiß | Gemini 4 Argon / Schwarz | Evidenzstatus |
|---|---:|---:|---|
| API-/Decision-Events | 117 | 132 | archivierte S350-Serienanalyse |
| Ausgeführte Aktionen | 117 | 116 | archivierte S350-Serienanalyse |
| Input-Tokens | 102.342 | 134.220 | archivierte S350-Serienanalyse |
| Output-Tokens | 137.594 | 4.834 | archivierte S350-Serienanalyse |
| USD-Schätzkosten | 7,90312 | 0,31678 | November-2026-Tarifkarten / Economy-Observer, **keine Rechnung** |
| Ergebnis | **Astra Matt-Sieger laut Runner** | unterlegen laut Runner | **nicht unabhängig engineverifiziert** |

**Gemeinsame Zählung:** 249 Decisions/API-Aufrufe und 233 ausgeführte Aktionen. Die Differenz **16** betrifft Argon-Aktionen (132 vs. 116), erklärt **ohne Einzel-Eventprüfung noch nicht den Grund**; insbesondere nicht pauschal als „16 illegale Züge“ etikettieren. Astra/Argon-Output-Verhältnis ca. **28,5:1**; Kostenverhältnis **24,95:1** bei den verwendeten Tarifen. Nicht als Effizienz-, Denk- oder Spielstärke-Urteil behandeln.

**Archivierte Schluss-FEN:** 3Q4/3R1k2/8/2K2B2/2P5/8/8/8 b - - 2 55; berichteter letzter Zug d2d7 / Rd7#. **Vor Veröffentlichung** mit passender historischer Engine/Replay-Regelkonfiguration prüfen; eine Illustration aus der FEN ist zunächst eine **rekonstruierte Darstellung**. Die Analyzer-Rückmeldung schlägt tatsächliche Schlussstellung + Economy-Kurven vor, die App-Rückmeldung ebenfalls Schlussstellung und prüfbare Metadaten. Der im Chat gezeigte Arena-Replay-Screenshot ist eine konkrete visuelle Referenz, **kein selbstständiger Nachweis der finalen Stellung**.

**Möglicher Teaser – ausdrücklich Entwurf:**
- **Titel:** „Schachmatt zum 25-fachen Preis?“
- **Ereignis:** „Astra setzt laut Runner Argon matt.“
- **Kontrast:** „7,90 USD vs. 0,32 USD geschätzte tarifbasierte Kosten.“
- **Drittes Signal:** „249 Entscheidungen, aber 233 ausgeführte Aktionen.“
- **Reason Why:** „Zwei grundverschiedene Ressourcenprofile in einer dokumentierten Partie. Welcher Teil des zusätzlichen Aufwands beeinflusste das Ergebnis tatsächlich?“
- **Evidenzhinweis:** Ergebnis nur runnerberichtet; Kosten geschätzt; Zusammenhang **offen**.
- **Publikationsstatus:** noch **nicht freigegeben**. Originaldateien/Hashes, Schluss-FEN und öffentlich verlässliche Story-/Replay-Links vor Freigabe prüfen. Keine erfundenen Links.

**Wichtig zu unterscheiden:** Das Archiv nennt für die 350k-Serie zwei Runner-Matt-Ergebnisse für Astra bei vertauschten Farben. Daraus folgt keine generelle Modellüberlegenheit und keine belastbare Budgetkausalität gegenüber der 150k-Serie.

## 5. Vorschlag für den gemeinsamen Story-Vertrag (noch nicht final)

Kein neues Dateiformat für die Match-Rohquellen. Das geplante **Story-Paket** darf lediglich referenzieren:

- **match_ref:** logical_match_id, originale match_id, series_id, segment_ids, Source-SHA/Dateipaar und Vollständigkeit;
- **actors_and_context:** tatsächliche Modell-/Provider-IDs soweit bekannt, Aliasse, Farbe/Rolle, Ruleset, Budgets, Limits, Versionen;
- **facts:** berichteter Endgrund und result_provenance, definierte Calls/Actions/Errors, Event-/Snapshot-Belege;
- **observations:** metric, value, unit, event_scope, source_ref, method_version, cost_tariff_version, coverage, evidence_status;
- **story_signals:** candidate_type, trigger_id, event_range, comparator_scope, quality, review_status;
- **editorial:** story_id, story_type, title, hook, reason_why, 0–3 highlight_refs, research_questions, counter_hypotheses, tags, language, status/approval;
- **assets:** asset_id, source_match_id, event_x / Replay-Position, image_sha/licence, aspect_ratio, captions, asset_verification;
- **links:** public_story_url, public_replay_url nur wenn tatsächlich gültig, sonst null;
- **relations:** related_matches, related_stories, research_topics, semantic tags.

**Provenienzklassen als Entwurf:** runner-reported fact, unabhängig verified fact, derived metric, detected candidate, analysis hypothesis, editorial selection. In Publikationsansichten Status **nicht weglassen**, wenn dadurch falsche Eindeutigkeit entstünde.

**Keine stille Live-Publikation**, keine zweiten Rohdatenbanken, keine ungeprüften Vorab-Übersetzungen. DE/EN und später ggf. ZH teilen Fakten, haben jedoch eigene redaktionelle Übersetzungen und Freigaben.

## 6. Neuer Composer-Modulvorschlag: MATCH PANORAMA / BREITBANDBILD

**Auslöser:** Im Journal-Thread wurde am 23.11. ein reales Arena-Replay-Bild gezeigt (Brett zentral, Gegner-/Logo-Informationsbereiche links/rechts). Dieses Motiv legt einen weiteren Modultyp nahe:

**„Match Panorama“: ein vollbreites, innerhalb des optionalen Seitenrahmens skalierendes Breitformatbild aus einer belegten Partie; optional völlig ohne Text, vollständig klickbar zum zugeordneten Artikel.**

**Redaktioneller Zweck:** visuelle Ruhe oder großer Erlebniswechsel zwischen Themenreihen, keine weitere erzählpflichtige Teaserkarte. Es kann sowohl auf Home als auch später in Artikeln und Gabelseiten genutzt werden.

**Vorgeschlagene Optionen, noch keine Implementierung:**
- Bildquelle: WordPress-Mediathek oder geprüfte Replay-Asset-Referenz, **kein** erfundenes Titelbild;
- Ziel: vorhandene **story_id / kanonische Artikel-URL**; wenn kein freigegebener Link, nicht öffentlich klickbar;
- **Textanzeige: AUS (Standard) / optional Titel / optional kleine Beschriftung / optional Logo-Overlay**;
- Bildproportionen: Panorama 21:9, 16:9 und Originalformat; responsive Höhe/Crop via focal point; Desktop optional „contain“ zur vollständigen Darstellung;
- Hintergrund/Farbfläche, Overlay, Verlauf, Schattenstärke, abgerundete Ecken und Seitenabstände je Instanz;
- Breite: Modul-Container max-width verwenden oder innerhalb zulässigem Composer-Canvas volle Breite ausnutzen; **Header-/Canvas-Modi** erhalten;
- Interaktion: ganze Bildfläche klickbar, Tastaturfokus und sichtbarer Focus-Ring, sinnvolles Link-Label/Alttext, optional Hover-Zoom; kein Autoplay;
- Provenienz: match_id, event_x/Frame, Quelle, Bildversion, ggf. als **reconstructed** kennzeichnen;
- Optional später: kurze Reihe aus zwei bis mehreren Panoramen, aber **nicht** als Pflicht, zunächst Single-Panorama.
- **Nicht** durch dieses Modul vorwegnehmen: neue Replay-Engine, GIF/Video-Generierung, Video-Abspiellogik oder automatisch erfundene visuelle Matchmomente.

**Abnahme erst später:** verschiedene Bildausschnitte (2048/1440/768/390 px), volle Linkfläche, Bildqualität, semantische Alttexte, kompatibles Canvas und kein Layout-Overflow. Im bestehenden Home Composer erweitern, **keinen neuen Pluginordner**.

## 7. Explizite offene Entscheidungen vor Umsetzung

1. **Golden Match Fact Check:** Verfügbarkeit der ursprünglichen JSONL+JSON, Hashes, FEN-/Endzug-Rekonstruktion und – falls gewünscht – unabhängige Regelnachprüfung.
2. **Match-Identität/Versionierung:** logical_match_id vs. Segment/Resume vs. Story-ID; exakte Event- und API-Zählsemantik verbindlich.
3. **Importer-Vertrag:** Story-Paket-/ZIP-Schema aus vorhandener Evidenz ableiten, zunächst manuell prüfbar, keine direkte App-/WP-Mutation.
4. **Narrative Auswahl:** Fight Night = erlebnisstarke Matches; außergewöhnlich lange oder unergiebige Spiele eher Research, z. B. „AI, explain yourself“ mit ausdrücklich gekennzeichneten Modell-Selbstaussagen.
5. **Bilder:** vorhandene Arena-Grafiken/Screenshots, Logo- und Lizenzrechte sowie echte Replay-Frames inventarisieren; nicht fälschlich neue Fantasiebilder als Matchbelege darstellen.
6. **Editor-/WP-Anbindung:** Nach dem Golden-Match-Prototyp Content-Package, Match-Panorama-Modul und bestehende Fight-Night-Bühne über denselben Story-Resolver versorgen. Bis dahin lediglich dokumentieren.

## 8. Quellen / Abgrenzung

**Primär für diese Synthese:**
- [ANDY App Development: FIGHT-NIGHT-01-Antwort](ANDY_FIGHT_NIGHT_01_APP_RESPONSE_2026-11-23.md) – vollständige A–F-Rückmeldung und JSON-Strukturvorschlag.
- [**G-Analyzer: FIGHT-NIGHT-01 – Originalantwort**](ANDY_FIGHT_NIGHT_01_ANALYZER_RESPONSE_2026-11-23.md) – am 23.11.2026 im Journal-Thread übermittelter Originaltext, unverändert archiviert; diese Datei enthält die Synthese.
- [S350 Serienanalyse v0.1](../research/andy-lab/ANALYSES/andy_cc11a6598bcf/v0.1/README.md) – IDs, Rundenindex, Konfiguration, Runner-Ergebnis, Calls, Actions, FEN und Archivbezug.
- [G-Analyzer-Handoff 23.11.](ANDY_G_ANALYZER_THREAD_HANDOFF_2026-11-23.md) – Economy-Screenshot, Usage-/Kostenstatus und wissenschaftliche Grenzen.
- [Match Evidence v1.0](ANDY_MATCH_EVIDENCE_JSONL_JSON_SQLITE_v1.0.md) – gemeinsames JSONL+JSON- und Provenienzprinzip.
- [Journal-Status / Modulkontext](JOURNAL/v1.1/STATUS.md) – historischer Plugin-/WP-Inventurstand. Spätere Composer-Updates werden dadurch nicht automatisch als auf GitHub geprüft betrachtet.

**Nicht durchgeführt:** neuer Lauf mit Original-JSONL, unabhängige Schach-Engine-Verifikation, neuer WordPress-Pluginbuild, Hostinger-Änderung, Story-Import, Bildrendering, GitHub-Import der Rohdateien.

**Fazit:** **Die Arena dokumentiert das Geschehen. Die Analyzer-Perspektive identifiziert prüfenswerte Kontraste. Das Journal kuratiert die Geschichte.** Die Match-Panorama-Bildwelt kann diese Verbindung besonders wirkungsvoll sichtbar machen, ohne den wissenschaftlichen Evidenzanspruch zu verwischen.
