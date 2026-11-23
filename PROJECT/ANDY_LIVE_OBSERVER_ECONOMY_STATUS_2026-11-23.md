# ANDY 2.0 — Zwischenstand: Ein Live-/Replay-Observer, Game Intelligence und Economy (23.11.2026)

**Zeitbezug:** 23. November 2026 (Europe/Berlin), nach den heute vom Projektleiter im Browser gezeigten 8082-Tests.  
**Funktionaler Status:** Auf **Sandbox 8082 lokal im Browser beobachtet**; **kein durch diesen Eintrag erstellter Code-Commit**, kein vollständiger 8080-Release, keine vollständige fachliche oder plattformübergreifende Abnahme.  
**Ziel dieses Eintrags:** aktuellen, nach dem 21./22. November fortgeschriebenen Stand für die 8080/8082-Synchronisierung und für unabhängige Reviews von DeepSeek (DS) und Qwen (Q) festhalten.  
**Leitmotiv:** **Erleben. Erforschen. Erahnen.**

## 1. Was sichtbar funktioniert — 8082

### Ein Observer statt getrennter KI- und Pattern-Fenster

- **Ein verschiebbares und skalierbares Observer-Fenster** mit vorhandener **iframe-/HTML-Architektur**. Nicht durch reaktive NiceGUI-Cards ersetzen.
- Ein Auswahlfeld oben schaltet innerhalb dieses Fensters zwischen **„Muster & Spiegelung“**, **„KI-Einschätzung“** und **„Economy · Zeit / Token / USD“** um.
- **Live und Replay** nutzen die Observer-Funktionen unter derselben Oberflächenlogik. Replay springt an gewählte historische Ereignisse; Live folgt bereits protokollierten Ereignissen.
- Musteransicht: Formationen, geometrische/diagonale Verläufe, Spiegelungen, Mini-Go-Brett, Pulse/Textwechsel und Inspector-Bezug. Im Browser sind sich während einer laufenden Partie weiterentwickelnde Formations-/Spiegelungskurven zu sehen. **Ein „Spiegelungsverdacht“ ist eine Heuristik, kein Nachweis einer KI-Intention**.
- Der alte separate KI-Einschätzungs-Einstieg im Arena-Header wurde im beobachteten UX-Stand entfernt. Der **Observer** bleibt der gemeinsame Einstieg; frühere doppelte Aufrufpfade und vertikal zentrierte Arena-Bühne wurden gezielt korrigiert.
- Die Bühnen-/Broadcast-Ausrichtung wurde zur besseren gleichzeitigen Sichtbarkeit von Spiel und Observer oben angeordnet.

### Game Intelligence / KI-Einschätzung

- **Manueller Button „Bewerten“**, keine automatische KI-Abfrage pro Zug; vorhandene ANDY-LLM-Bridge.
- Für jeden Auftrag wird der **Matchzustand zum Ereignis X** referenziert. Das Ergebnis bleibt **X** und dem ausgewählten Bewertungsmodell zugeordnet, auch wenn die Partie inzwischen bei Y ist.
- Drei sichtbare KI-Tendenzen: **Schach, Go, ANDY Gesamt**, je subjektive Skala −2 bis +2, Begründung/Unsicherheit, Verlauf bisher tatsächlich angeforderter Messpunkte.
- **Modellwechsel** des Bewertungsmodells lässt vorher gemessene Punkte **derselben Partie** in der gemeinsamen Kurve sichtbar; jedes Sample behält seinen Urheber. **Nicht bewertete Zwischenstände werden nicht erfunden**.
- Browserbelege: Bewertungsreihen mit 7→8→10 Punkten über verschiedene Modelle; positive und negative, nicht nur neutrale Tendenzen; Aktivitätsanzeige und aktuelle X-Zuordnung. In Replay können historische Positionen **rekonstruiert/vorläufig** sein. Kein universeller Nachweis der fachlichen Qualität oder aller Modell-/Providerkombinationen.
- **Noch offen:** offizielle finale KO/TKO-/Limit-Ergebnisse im GI-Panel klar sichtbar machen, getrennt vom subjektiven KI-Urteil; bei X vor Spielende keine späteren Endfakten einfließen lassen; optionale rückwirkende Verlaufsbewertung 1..X bzw. in Intervallen (GI-HISTORY-01, TBD); Mensch-vs.-KI-Spielberater mit drei *regelgeprüften*, rein beratenden Zugoptionen erst als Konzept.

### Economy Observer (aktueller UI-Meilenstein)

- **Dritter Modus im selben Observer**, nutzbar für bereits protokollierte Live-Ereignisse und Replay.
- Kombinierte Zeitreihe nach **Matchzeit oder Ereignis X**, Spielerfilter Weiß/Schwarz/Beide, Kurven für API-Zeit, sportliche UND soweit verfügbar Provider-Token, Kosten und Einzelkategorien.
- Pro Spieler sichtbar: **API-Zeit, Input-Tokens, Output-Tokens, separat gemeldete Reasoning-Tokens, Cache-Felder sofern vorhanden; berechnete Gesamtkosten in USD und EUR sowie Input-/Output-/Cache-Kosten**.
- **Kein zweiter KI-Aufruf für die Economy-Ansicht**: Sie verarbeitet protokollierte Spiel- und API-Ereignisse. Der laufende Observer-Refresh stellt vorhandene neue Werte dar; keine neue zusätzliche Timer-/Provider-Infrastruktur.
- Eingebauter **Tarifkarten-Editor**: Provider, API-Modell-ID, zeitliche Gültigkeit (von/bis), getrennte USD/1M-Preise, Quellen-/Notizfeld; gesonderte SQLite-Datenbank für Tarife außerhalb des App-Git. Vorbefüllung der bekannten Novembertarife **01.–30.11.2026** als praktische Rechenbasis; individuell abänderbar. USD→EUR-Faktor im Observer zunächst **0,91 EUR je USD**, editierbar.
- Bei älteren Logs ohne modernes Provider-Usage-Objekt: **Legacy-Rechnung** aus tatsächlich protokollierten Input-/Output-Zählern × zeitbezogenem Tarif. Keine Behauptung exakter Rechnungskosten; das UI soll trotzdem direkt die **rechnerischen Kosten** zeigen statt sperrender Warn-/Freigabedialoge.
- Grundsatz: **ANDY-Spielkonto, gemeldete Provider-Usage, Reasoning/Thinking, Tarifschätzung und tatsächliche Rechnungsbelege nicht doppelt zählen oder stillschweigend vermischen**. Nicht gemeldete Reasoning-Tokens sind **unbekannt**, nicht 0; Provider unterscheiden sich bei der Inklusion in den Output-Tokens.
- Browserbeleg vom 23.11., 12:58: **32/32 Aufrufe** in der angezeigten Economy-Stichprobe mit Messwert; Weiß **0,03062 USD / 0,02787 EUR**, Schwarz **0,31063 USD / 0,28267 EUR**; Input/Output getrennt, bei Schwarz **3.276 gemeldete Reasoning-Tokens**. Diese Werte gelten **nur für den Screenshot/ausgewählten Spielabschnitt und die hinterlegten Tarifkarten**; keine globale Modellbewertung.
- Weiterer Browserbeleg: 23 historische Aufrufe anhand der November-Tarifkarten mit berechnetem kumulierten USD-Verlauf; früheres Problem „USD offen“ bei Legacy-Daten behoben. Kosteneditor und spätere Versionen sind auf 8082 browserseitig sichtbar. Versionen der tatsächlich lokal installierten Einzeldateien wurden für diesen Statusbericht nicht unabhängig neu gehasht.

## 2. Warum das über ein Match hinaus wichtig wird

**Story-driven Lab Development:** Eine überraschende Beobachtung → Frage → untersuchbare Darstellung → wiederholbare Analyseregel → Lab-Evidenz → Journal/Learning → nächste Versuchsanordnung.

Beobachtungen, aus denen heute wiederverwendbare Fragen entstanden:

1. **Grok/Astra und abweichende Provider-Usage:** Im [USAGE-AUDIT-Issue #11](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/11) ist für `andy_e1dee05964fb` der Forschungs-Handoff mit **133.355 ANDY- vs. 743.126 Provider-Tokens** (Grok) dokumentiert. **Diese konkrete Matchzahl war im Issue noch nicht unabhängig am Original-JSONL verifiziert**. Derselbe grundsätzlich relevante Accounting-Unterschied wurde an anderen Grok-JSONL unabhängig reproduziert. Reasoning-Token-Inklusion ist providerabhängig. **Sportliche Regeln/Altresultate nicht automatisch korrigieren**.
2. **Go-Setup als wiederkehrende Aufgabe:** 16 erfolgreiche Steinsetzungen ermöglichen Vergleiche von **API-Zeit, Calls, Fehlern, Tokens, Kosten** und deren Schwankungen nach Zeitpunkt/Modell/Konfiguration. Beobachtet wurde ein einzelnes Setup >10 Minuten; andere archivierte Setups waren wesentlich kürzer. Alle zeitlichen/technischen Einflussfaktoren noch nicht kontrolliert; keine bewiesene Provider-Warteschlangenursache.
3. **Kurze Tests sind wertvolle Evidenz:** Auch unvollständige oder absichtlich abgebrochene Spiele können Setup-Performance zeigen; **im Archiv erhalten, per Replay-Filter ausblendbar**, ohne Sport-/Forschungswert zu verwechseln.
4. **Spiegelung und Muster** bereits während des Live-Spiels sichtbar; die entscheidende Forschung ist, ob die beobachteten Muster über Serien, Rollen/Farben, Gegner und Konfigurationen stabil auftreten.
5. **Modellübergreifende GI-Zeitreihe** macht Stellungs-/Modellbewertungsänderungen sichtbar, ist aber **noch kein konsistentes Ein-Modell-Urteil für jeden Zwischenzustand**. Backfill/Replay-Analyse wäre ein gesonderter kontrollierter Modus.

## 3. Technische/operative Grenzen

- **Instanzgrenzen:** 8082 = Integration/Sandbox/aktuelle Browserpilotierung; 8080 = Studio mit bewusst abweichenden Rollen-/Designer-/Launcher-Gates; 8083 Factory nicht anfassen.
- **Git-Status:** Der Unterschied zwischen lokalen Arbeitsdateien und GitHub-Branch wurde per Read-only-Audit offengelegt. Es gibt umfangreiche lokal uncommittete Codeänderungen; der gezeigte 8082-Browserstand ist **nicht gleichbedeutend mit einem vollständigen, gepushten Integration-Commit**. **Vor Sync** vollständige Inventur, sichere Quellcodekopie, minimale Diff-Auswahl, Code-/Role-Gate-/Browser-Regression; keine blinde Dateikopie.
- **Daten:** Original-`<match>.jsonl` + `<match>.json` bleiben Primärquellen. SQLite-/Lab-Ansichten sind abgeleitete Projektionen, niemals neue historische Wahrheiten. Resume-Segmente/doppelte Logs nicht doppelt zählen. Event/Aufruf/ausgeführter Zug/Fehlversuch unterscheiden.
- **Observer-Anmerkungen** (LLM-Einschätzungen, heuristische Spiegelmarker, berechnete Kosten) sind **abgeleitete Evidenz**, nicht Ergebnis-/Regel-Fakten. Verweis auf Match-ID, Ereignis X, Bewertungsmodell, Datenstand, Algorithmus/Policy-Version und Herkunft nötig.
- **Live vs Replay:** vorläufig rekonstruierte historische Brettstellungen explizit als solche halten; Bewertung zu X hat keinen Wissenszugriff auf spätere Endereignisse.
- **Forschungsarbeit** darf parallel zum 8080/8082-Sync laufen, aber **keine neuen Spielcode- oder Datenbankschreibzugriffe** durch externe Reviewer auslösen.

## 4. Anschluss Living Lab / Data (offene Integrationsaufgabe, nicht bereits fertig)

Bestehender Produktkonsens: Die Arena ist ein eigenes Produkt, der **Observer** untersucht eine Partie bzw. einen gewählten Zeitpunkt, das **Living Lab** untersucht hypothesengeleitet **viele Partien**, und die **Data/Evidence Engine** verbindet Originale, Regeln, Ableitungen, Queries und Reproduzierbarkeit. Keine neue parallele Lab-Datenquelle.

Zu bewertende Themen für unabhängigen DS-/Q-Review:

- Einheitliches **Ereignis-/Snapshot-/Anmerkungsformat**: `logical_match_id`, `segment_id`, `event_id`, `api_call_id`, `attempt/executed`, `state_hash`, `ruleset`, `source_sha`, `observer_metric_version`, `model_id`, `tariff_version`, `as_of`, `quality/provenance`.
- **Provider-Economy** auf derselben Event-Achse: sportliche Tokens, Usage-Total, Cache, Thinking/Reasoning, USD/EUR und Antwortzeiten; fehlende Daten/Methodenunterschiede differenzieren. Tarifkarte ist Metadatum, nicht Teil der Originalpartie.
- **Live-Event-Import → deduplizierte Read-Model/Metric Registry → Replay/Lab/Explorer**; Snapshot/Verlauf ohne Multi-Writer-Risiko. Views sollen auf **denselben berechneten Kennzahlen** beruhen.
- **Hypothesen/Panel-Evidenz** für Muster (Spiegelungen, Verzögerungen, Fehler, Kosten, Kosten je *erfolgreicher* Entscheidung, Risiko/Erholung) und übergreifende Kohorten nach Modell-ID, Version, Anbieter, Konfiguration, Zeitraum, Gegner, Farbe, Regeln und Setup-Profil.
- **Independent Review** für riskante Fehlinterpretationen und die 2–3 sinnvollsten, kostengünstigen nächsten Versuche.

## 5. Offene Punkte / Priorität

| Thema | Stand 23.11.2026 | Nächster Schritt |
|---|---|---|
| Gemeinsamer Live-/Replay-Observer | **Browserbelege auf 8082 vorhanden** | Browserregression beim 8080/8082-Sync, Studio-Gates schützen |
| Muster/Geometry/Spiegelung live | **sichtbar funktional** | Heuristische Marker und Trends in Lab-Evidenzmodell verknüpfen |
| GI manuelles X-Bewerten und Modellwechsel-Verlauf | **sichtbar funktional** | Qualität / Endzustand KO/TKO/Limit / Backfill als eigenes TBD |
| Economy Zeit/Token/USD+EUR / Input/Output/Reasoning | **sichtbar funktional** | model-/zeitabhängige Tarife und Rechnungsspiegel kontinuierlich pflegen |
| Tarifeditor und Novemberkarten | **auf 8082 sichtbar und nutzbar** | Konten-/Belegabgleich optional; keine Centgenauigkeit als UI-Voraussetzung |
| Ökonomik über viele Spiele | **noch kein Lab-Produktnachweis** | Reviewer-Lösungsvorschläge in bestehenden Data-/Metric-/Lab-Vertrag integrieren |
| Setup Benchmark, Kurztest-Filter | **Forschungsidee/Replay-UX-Issue** | [Replay UX #13](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/13) |
| Sportliches Accounting / Usage-Gleichheit | **offener Fairness-Audit** | [USAGE-AUDIT #11](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/11), keine stillen Regeländerungen |
| Lab-/Leaderboard-Datenkonsistenz | **bestehende P1-Priorität** | [DATA-SYNC #12](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/12) |
| Lokale Codefreigabe 8080/8082 | **ausstehend** | Inventar, Audit, selektiver Git-Commit/Sync und Regression |

## 6. Verbindliche Bezüge

- [Observer Research Handoff 21.11.](ANDY_OBSERVER_STATUS_HANDOFF_2026-11-21.md) — damaliger Ausgangsstand, **durch diese jüngeren Browserbelege fortgeschrieben**, nicht rückwirkend geändert.
- [Game Intelligence LIVE v0.6 22.11.](ANDY_GAME_INTELLIGENCE_LIVE06_STATUS_AND_HUMAN_ADVISOR_2026-11-22.md) — historischer Zwischenstand vor vollständiger Observer-Zusammenführung.
- [ANDY Lab V1 Produktkonsens 20.11.](../research/andy-lab/REQUIREMENTS/ANDY_LAB_V1_0_PRODUCT_CONSENSUS_2026-11-20.md)
- [Lab Research Architecture](../research/andy-lab/ANDY_LAB_2_0_RESEARCH_ARCHITECTURE_v1.0.md)
- [Event-to-Evidence Method](../research/andy-lab/METHODIK/ANDY_EVENT_TO_EVIDENCE_METHOD_v0.1.md)
- [JSONL+JSON→SQLite Evidenzvertrag](ANDY_MATCH_EVIDENCE_JSONL_JSON_SQLITE_v1.0.md)
- [API-Kosten und Caching November](../research/andy-lab/REQUIREMENTS/v0.1/API_COSTS_CACHE_2026-11.md)
- [Resource & Game Records LAB-R11](../research/andy-lab/REQUIREMENTS/v0.1/RESOURCE_GAME_RECORDS.md)
- [USAGE Audit #11](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/11) · [Lab/Leaderboard Sync #12](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/12) · [Replay UX #13](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/13)
- [Entwicklungs-/Regressionsprozess](ANDY_DEVELOPMENT_REGRESSION_POLICY_2026-11-21.md) · [SYNC Feature-Gate](ANDY_SYNC_FEATURE_GATE_CASE_2026-11-21.md)

**Dokumentations-Commit allein:** keine Änderung an Python/HTML/iframe/Bridge/Tarif-DB/Original-JSONL; keine API-Anfragen oder Instanz-Neustarts durch diesen Eintrag.
