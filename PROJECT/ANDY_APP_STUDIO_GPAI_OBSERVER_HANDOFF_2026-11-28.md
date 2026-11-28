# ANDY APP – verbindliche Entwicklungsübergabe
Stand 28.11.2026. Basis: Entscheidungen und Abnahmen im APP/Observer-Thread. Lokaler Quellstand ist nicht mit GitHub gleichzusetzen.

## 1. Betriebsmodell – FROM SYNC TO TRANSFER
8080 (Studio, ~/Documents/GitHub/cair4_andy_game_ui) ist alleinige führende Entwicklungsinstanz. 8082 (cair4_andy_game_signature) wird eingefroren und vollständig archiviert, nicht gelöscht; tatsächliche Archivierung noch nicht bestätigt. Windows Factory bleibt unabhängig. Neue 8082- und Windows-Instanzen erst nach Integration der neuen Modelle UND erstem neuen Observer aus freigegebenem 8080-Stand ableiten. Keine permanente parallele Code-Synchronisation mehr. Code-Deployment und Datentransfer trennen; lokale Keys, Ports, Umgebungen und Datenpfade schützen. Leere Matchbestände für neue Spielinstanzen sind Vorschlag, keine abschließende Freigabe.

Making of: Komplexität nicht durch immer bessere Synchronisation verwalten, sondern deren Notwendigkeit beseitigen. Agile Mona Lisa: erst Gesamtkonzept, dann inkrementelle Vertiefung. Sonderfälle dokumentieren, nicht zum Entwicklungsblocker machen. Systematische Fehler einmal grundsätzlich beheben.

## 2. Transfer – Stand und Abnahme
Empfängerunabhängiger Export aller exportierbaren abgeschlossenen Partien; kein Zielordner, keine Ziel-DB-Abfrage, kein Export-Delta. Empfänger bildet Match-ID-Differenz, überspringt bekannte IDs ohne erneute Evidenzprüfung; dies bedeutet nicht byteidentisch. Neue Partien validieren; Paketintegritätsfehler stoppen, matchbezogene Konflikte protokollieren; keine Originale überschreiben. Vorschau ohne DB-Änderung, Apply separat. Format andy-transfer-pilot-v1. UI Transfer-Tab, Scrollbereich, kurze Zusammenfassung statt 69 bekannten IDs. One Click Import automatisiert Offline-Import und Neustart; bestehende Backup-/Sicherheitsprüfungen erhalten.
Lokale Patchfolge: ANDY_DATAINTEGRATOR02_IMPORT.py ersetzt ANDY_DATAINTEGRATOR01_IMPORT_R01.py; ANDY_FIX_SYNC_SCROLL01.py, ANDY_INSTALL_TRANSFER01.py, ANDY_FIX_SYNC_SCROLL02.py, ANDY_INSTALL_TRANSFER02.py, ANDY_FIX_TRANSFER_UI03.py, ANDY_INSTALL_TRANSFER04.py. Nicht blind erneut installieren; aktuellen 8080-Quellstand prüfen. 8082 hatte nicht zwingend dieselben letzten UI-Patches.
Produktive Vorschau: Bestand 119, ZIP 70, bekannt 69, neu 1, skip 0. Neue Partie andy_5eaa41a0628a (Gemini 3.8 Flash vs GPT-5.2, max_decisions) anschließend im 8080-Replay sichtbar. Vollständiger Neustart-/Wiederholungstest nicht separat belegt. Früher 62/69 JSON-Hash-Konflikte: keine Reparatur; bekannte IDs beim regulären Transfer überspringen. 47 nicht exportierbare Aufzeichnungen nicht weiter auditieren. Keine Aussage über vollständige historische Bestandsidentität.
Offene Partie andy_6f007eda6807 (Kimi K3.1 Pro vs Grok 4.7): regulärer Export schließt mangels match_end aus. Separates ANDY_OPEN_RECORDING_6f007eda6807.zip mit Originalpaar; Importskript scheiterte an Prozessprüfung; bei beendetem 8080 manuell mit unzip -n nur JSON/JSONL nach runs/live entpackt (2462/387266 Bytes laut ZIP). Beide Dateien vorhanden, Partie im 8080-Replay sichtbar. Kein künstliches match_end, keine SQLite-Integration. Vollständige analytische Auswertbarkeit offen. Keine weitere Einzelreparatur.

## 3. Nächster Schritt – GPAI vor Observer
Alle Arbeiten auf 8080. Frisches schlankes ANDY_STUDIO_BASELINE_*.zip vom Nutzer abwarten; alten OBS-ARCH-01-Patch aus 8082 nicht blind installieren. ZIP ohne runs, DB, JSONL, Git, Backups, virtuelle Umgebungen, Keys und Logs; projektspezifische Secrets zusätzlich prüfen. Erst tatsächlichen Quellstand inventarisieren. Keine historischen Migrationen, keine unnötigen Architekturumbauten, keine parallelen Patches. Bestehende Funktionen schützen, kleine getestete Installer mit Backup/Dry Run, tatsächliche Tests von geplanten unterscheiden. Keine behaupteten Downloads ohne erzeugte Datei.
Verbindliche Reihenfolge:
1. GPAI-ARCH-01: Modellidentität, API-Zugang, Inferenzanbieter getrennt erfassen.
2. OPENROUTER-01: gemeinsamer OpenAI-kompatibler Adapter (https://openrouter.ai/api/v1, OPENROUTER_API_KEY), vorhandene Groq-Anbindung prüfen und erhalten.
3. MODEL-EXPANSION-01: Kandidaten und Watchlist anlegen; Modellverfügbarkeit getrennt von Identität.
4. ACTOR-SELECTION-01: pro Spieler Modell und Zugang/Provider unabhängig wählen, auch dasselbe Modell gegen sich selbst über verschiedene Provider.
5. ACTOR-EVIDENCE-01: angeforderte Konfiguration und tatsächlich gemeldete Inferenz-Provenienz je API-Aufruf dokumentieren.
6. ARENA-TEST-01: kurze Funktionsprüfungen/Partien, Providervergleiche; keine kostenpflichtigen Tests ohne Freigabe.
7. OBS-ARCH-01: erster neuer Observer mit globaler Actor-/Zeitsteuerung.
8. OBS-LATENCY-01 und externe Referenzen inkrementell; Deployment nach erstem neuen Observer und neuen Modellen, genaue weitere Tiefe nach Abnahme.
9. DEPLOYMENT-01: 8082 und Windows neu aus 8080 ableiten; keine alte Sync-Architektur reaktivieren.

## 4. Identitäts- und Datenvertrag (Entwurf, nicht implementiert)
Developer (Hersteller), Model Identity/Familie/Version, API Access/Gateway (direkt, Groq, OpenRouter), Inference Provider getrennt. Bestehendes technisches Feld provider kompatibel behalten. Additiv: developer, model_identity, model_id, inference_provider_requested, inference_provider_actual, routing_policy, resolved_model_version. Unbekannt bleibt unbekannt; direkte API ist kein Beweis für physischen Hoster. Actor = Modell + API-Zugang + Inferenzkonfiguration + Reasoning + ANDY-Spielkonfiguration (Budget, Strategie, Awareness etc.). Pro Aufruf tatsächlichen Provider erfassen soweit verfügbar; Routing kann während Match wechseln. Flexible Routing mit Fallback für Arena; Fixed Provider ohne Fallback für Research, unterstützte Parameter und tatsächliche Version prüfen. Historische direkte Anbindungen unverändert lassen. Serien, Replay, Economy, Leaderboard, Lab und Observer müssen später nach Modell bzw. Konfiguration aggregieren können, nicht alles sofort umbauen.
Groq (q) ist nicht Grok (k). Älterer 8082-Baseline laut vorheriger Codeprüfung: GROQ_API_KEY, https://api.groq.com/openai/v1, Meta Muse Spark (Groq), Default meta-models/muse-spark-open, älterer Alias Meta Spark (Groq) ohne passenden Bridge-Zweig. OpenRouter im Factory Budget Planning teilweise vorhanden, eigener Bridge-Adapter damals nicht nachgewiesen. Gegen frischen 8080-Stand verifizieren.

## 5. Modellliste (Kandidaten, keine bestätigten aktiven API-Tests)
13 API-Kandidaten, 3 Watchlist; gegebenenfalls vorhandene Muse-Spark-Identität ergänzen statt duplizieren. Slugs, Preise, Verfügbarkeit und unterstützte Parameter live beim Anbieter prüfen; frühere Katalogangaben sind keine Zugangsgarantie.
| Modell | Vorgeschlagener OpenRouter-Slug / Zugang | Interesse |
|---|---|---|
| Mercury 3 | inception/mercury-3 | Diffusion; Nutzer meldet momentan keinen Early-Stage-Zugang |
| Mercury 2.5 | inception/mercury-2.5 | Diffusion-Alternative |
| Inkling 2 Mini | thinkingmachines/inkling-2-mini | Looped Transformer |
| Inkling 2 Small | thinkingmachines/inkling-2-small | Größenvergleich |
| Nemotron 3 Ultra | NVIDIA-Katalog, exakten Slug prüfen | Mamba-Attention-MoE |
| Nemotron 3 Super | NVIDIA-Katalog, exakten Slug prüfen | Skalierungsvergleich |
| Muse Wonder | meta/muse-wonder | Agentisches Frontier; Meta vs Google Vertex |
| Muse Spark Open | meta/muse-spark-open | Groq vs OpenRouter, Groq-Zugang ggf. Enterprise |
| Muse Ember | meta/muse-ember | Effizienz |
| Command A+ | cohere/command-a-plus | Enterprise |
| Solar Mini 4.5 | upstage/solar-mini-4-5 | kompakter Generalist, Preview |
| MiniMax M3 | minimax/minimax-m3 | agentischer Generalist |
| MiniMax M3.1 Flash | minimax/minimax-m3.1-flash | Effizienz |
| Soofi S Instruct | Watchlist | souveräne deutsche KI |
| ELMOD 2.7B Instruct | Watchlist | Fraunhofer IIS, Edge |
| Kolibri 1.1 | Watchlist | Aleph Alpha, effizientes Reasoning |
Kein öffentlicher nutzbarer API-Zugang für die drei Watchlist-Modelle bestätigt. Status Aktiv erst nach erfolgreichem Test; Kandidat, Watchlist, Historisch getrennt. Direkte Provider-APIs erhalten; weitere direkte Zugänge optional. Modellmetadaten: Architektur, Parameter gesamt/aktiv, Herkunft, Open/Closed Weights, Release, besondere Eigenschaften; nur belegte Werte.

## 6. Observer – Agile Mona Lisa
Zuerst globale Mehrfachauswahl Actors und mehrere frei wählbare Beobachtungsstichtage; gemeinsamer persistenter Kontext über Module hinweg. Configuration, Provider, Evidence architektonisch berücksichtigen. Bestehende Muster & Spiegelung, KI-Einschätzung, Economy (Zeit/Token/USD) erhalten. Alter OBS-ARCH-01-Patch war Architekturpilot ohne echte Filterwirkung; neu auf 8080 prüfen. Snapshot (kumuliert vs Fenster explizit), Evolution, Event; zuerst Snapshot. Perspektiven Actor vs Population, Actor vs Self, Actor over Time. Keine synthetischen Kurven als reale Messwerte. Story-driven Lab Development: Arena -> Observer -> Lab -> Journal; Discovery später. Partial Evidence is Evidence: Lesbarkeit, Vollständigkeit, Auswertbarkeit, Fortsetzbarkeit separat. Offene Matches nicht als Niederlage zählen, fehlende Usage nicht null setzen.

ADAPTIVE-LATENCY-01: individueller Median, P95, Streuung, n je Modell/Provider/Reasoning/Zeitfenster; modellübergreifende Referenz ergänzend. Vorläufige relative Wartezeit-Schwellen bis 100%, 100–200%, 200–300%, 300–500%, >500%; statistische Auffälligkeit kein Fehlernachweis. Offene/abgebrochene Calls getrennt erfassen (Zensierung beachten). Observer liefert Referenzwerte, APP verantwortet Timeout/Watchdog/Stop/Recovery. Unlimited patience must not mean unlimited blocking.
Grok-Referenz: 79 abgeschlossene Versuche, 67 Aktionen, 80 JSONL-Events, attempt 80 Schwarz GO offen seit 27.11. 22:01:10 UTC. 33/33 abgeschlossene Grok-Versuche gültig, längster abgeschlossener Call laut vorheriger Analyse 16:56. Zweiter Freeze Grok vs Grok vom Nutzer berichtet, nicht separat belegt. Ursache nicht nachgewiesen. Checkpoint Grok input 66372, output 1197, Summe 67569; frühere Analyse meldet reasoning 310414 und total 377983 bei Budget 350000; Usage-Semantik und Budgetdefinition prüfen, keine Doppelzählung. Als bekannte Einschränkung dokumentieren, keine Sonderfallreparatur.

## 7. Externe Referenzdaten
Quelle: Nutzer-PDF Muse Wonder - API Pricing & Benchmarks _ OpenRouter.pdf, Snapshot 28.11.2026 11:38, https://openrouter.ai/meta/muse-wonder#benchmarks. Seiten 3–4 Wochenmittel Google Vertex vs Meta: Durchsatz 107 vs 65 tok/s, E2E 5.93 vs 8.30 s, Tool Call Error 1.12 vs 15.59 %, Structured Output Error 5.71 vs 1.86 %, Cache Hit 94.19 vs 88 %. Seite 6 Artificial Analysis Intelligence Index Muse Wonder (Max) 43.7, Rang 17/66. Externe Benchmarks als datierte Quellen-Snapshots mit Methodik, Zeitraum, Version und Provider; keine direkte Gleichsetzung mit ANDY-Aufgaben. Relevante Maße: E2E/TTFT/Durchsatz, Kosten effektiv vs Listenpreis, Reasoning/Cache, Availability, Tool/Structured Output Errors, externe Reasoning-/Intelligence-Benchmarks. ANDY eigene gültige Aktionen, Time-to-Action, Recovery und Kosten pro gültiger Aktion. Keine neue Gesamtkennzahl vor Einzelvergleich. Provider-Effekte nur mit kontrollierten Konfigurationen, Wiederholungen und Seitenwechseln untersuchen.
## 8. Handoff-Regel
GitHub ist Projektgedächtnis, lokaler 8080-ZIP tatsächliche Codebasis. Nach jedem abgenommenen Inkrement betroffene Dateien, Version, Tests, Grenzen und nächsten Schritt dokumentieren. Nächster Thread beginnt bei GPAI-ARCH-01, nicht beim alten Sync. Keine Implementierung der hier geplanten GPAI-/Observer-Funktionen behaupten: Stand heute Konzept und Freigabe der Reihenfolge, frisches ZIP noch ausstehend.
