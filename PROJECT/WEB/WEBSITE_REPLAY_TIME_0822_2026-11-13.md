# ANDY Arena – WEB-REPLAY-TIME-01 (V0.8.2.2)

**Datum:** 13. November 2026  
**Status:** lokaler Code-Patch erstellt und statisch geprüft; **nicht** live auf Hostinger veröffentlicht oder im Browser abgenommen.  
**Basis:** vollständiges Website-Paket V0.8.2.1 (Mobile-CSS-Cache-Fix).  
**Nächste Version des bereitgestellten Pakets:** **V0.8.2.2**.

## Fachliche Entscheidung

Neben dem **vorhandenen Replay-Slider** und der unveränderten Ereignisanzahl `84 / 249` erscheint direkt daneben ein zweites festbreites Feld für die **seit dem Matchstart tatsächlich vergangene Original-Spielzeit**, z. B. `00:34:02`.

Die Anzeige ist **nicht** die komprimierte Film-/Theaterlaufzeit. Sie wird bei Wiedergabe, Pause, Vor-/Zurückspringen, Slider-Scrubbing, Neustart und Endsprung aus dem aktiven Ereignisstand gespeist. Keine zusätzlichen Bedienelemente und keine zweite Timeline.

## Datenherkunft und Genauigkeit

- Originalquelle: `public_html/theater/original/andy_0c0f7413fdf6.jsonl`, SHA256 `7f955acabc196c592c8b6a623fd9b644d9110e35f482c14fd6704a32682f093e`.
- `match_start.timestamp_utc = 2026-11-10T14:11:43.980128+00:00`.
- Alle **249** protokollierten `decision.timestamp_utc` wurden mit passendem Ereignisindex übernommen.
- `match_end.timestamp_utc = 2026-11-10T16:31:36.825857+00:00`.
- **Enddauer:** `02:19:52` (genauer: `8392.846 s`), während der letzte Decision-Zeitstempel `8392.843 s` nach Matchstart liegt.
- Beispiel: Ereignis **84** bei `2042.545 s` → **00:34:02**.
- Zählung bezieht sich auf 249 protokollierte **Entscheidungsereignisse**, einschließlich fehlerhafter Entscheidungen, nicht ausschließlich auf ausgeführte Brettzüge.

## Konkreter Datei-Diff gegen V0.8.2.1

**Nur verändert:**
- `public_html/theater/START_HIER.html` – festes Zeitfeld `#matchTime` direkt nach `#step`, Theater-CSS-/JS-Cache-Parameter `?v=0822`.
- `public_html/theater/app.js` – `formatMatchTime` und Aktualisierung im zentralen `render()`.
- `public_html/theater/style.css` – feste Zahlenausrichtung und kleine Mobilanpassung.
- `public_html/theater/match-replay.json` – `started_at_utc`, `duration_seconds` und pro Event `timestamp_utc`, `elapsed_seconds`; bisherige Go-/Chess-/Token-Daten unverändert.
- `public_html/theater/replay-data.js` – gleiches Datenobjekt wie JSON, konsistente Browser-Version.

**Neu:**
- `public_html/theater/sync_event_times.py` – wiederholbar, validiert SHA256 des JSONL und Decision-ID-Reihenfolge; verändert ausschließlich Zeitfelder in Replay-JSON/JS.
- `README-V0822.txt` – Deployment- und Testhinweise.

**Unverändert:** Original-JSONL, sämtliche Webseiten-Hauptassets, Homepage, Sprachseiten DE/EN/ZH, Blog, Bilder sowie die eigentliche Chess-/Go-Replay-Logik.

## Lokale Prüfungen

- `node --check` für `theater/app.js` erfolgreich.
- Time-Sync-Skript gegen Original-JSONL erfolgreich; Eventzahl 249, aufsteigende Zeitstempel, passende Event-IDs.
- `replay-data.js` enthält exakt das JSON-Objekt aus `match-replay.json`.
- Prüfsummenvergleich der Release-Archive: exakt fünf vorhandene Dateien verändert und zwei neue ergänzt; keine Dateien gelöscht.

**Paket:** `ANDY_Arena_KOMPLETT_V0822_Replay_Zeitanzeige.zip`, **SHA-256:** `e7b19128c9e7563865beaa9ca3b14e1c0eafea4734c1d1e893520a14596946b4`. Das **vollständige ZIP ist in dieser Sitzung bereitgestellt**, nicht als binäres GitHub-Release archiviert. Dieser Dokumentationscommit ersetzt kein Repository-Quellcode-Commit.

## Offene Freigabechecks

1. Verifikation auf Test-Hostinger: Headerlayout inkl. DE/EN/ZH, Desktop/Tablet/Mobil.
2. Replay-Interaktion: Play, Pause, Zurück, Vor, Scrub, Ende, Neustart; während der kompletten Wiedergabe Zähler und Zeit konsistent.
3. Geladenes `replay-data.js?v=0822` / `app.js?v=0822` / `style.css?v=0822` prüfen; alle Status 200.
4. Der separat dokumentierte Windows-HTTPS/TLS-Fehler aus [Issue #3](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/3) bleibt offen; unabhängig von diesem theaterinternen Patch untersuchen.
5. Erst nach erfolgreicher Live-Abnahme und Deployment die Version als **produktiv** markieren.

**Referenzen:** [Website-Paketkette und Release-Evidence](WEBSITE_RELEASE_EVIDENCE_2026-11-13.md), [Website-Release-Checkliste #2](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/2).
