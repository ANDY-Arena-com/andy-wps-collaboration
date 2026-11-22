# ANDY 2.0 — Game Intelligence LIVE v0.6: Browser-Meilenstein und Spielberater-Perspektive (22.11.2026)

**Stand:** 22.11.2026, ca. 23:26 Uhr (Europe/Berlin)  
**Instanz:** Sandbox `sandbox:8082`  
**Status:** technischer Live-Bewertungspfad **im Browser bestätigt**; fachliche Qualität, Modal-Integration, Replay-Parität und Gesamtre­gression **offen**.  
**Art dieses Eintrags:** Dokumentation des beobachteten Entwicklungsstands und eines vom Nutzer vorgeschlagenen Folgekonzepts. **Kein Code-Release, keine Synchronisation nach 8080, keine Freigabe für 8083.**

## 1. Nutzerbeobachtung und nachgewiesener Meilenstein

Am 22.11.2026 bestätigte der Nutzer: „aber das Grundprinzip funktioniert.“ Sein Screenshot von `127.0.0.1:8082` zeigt die **KI-SPIELEINSCHÄTZUNG** mit einer eingetroffenen Bewertung für **Ereignis X = 66**. Sichtbar sind:

- Modell: **OpenAI GPT-4o-mini**; manuell ausgelöster Button **„Bewerten“**.
- Anzeige: **„Bewertung X = 66 eingetroffen“** und „KI-Antwort für X = 66 eingetroffen“.
- Bewerteter und aktueller Stand im gezeigten Moment: **X = 66**; Differenz **0**.
- Angezeigte KI-Rechenzeit: **2,8 Sekunden**.
- Drei grafische Sichten: **Schach**, **Go**, **ANDY Gesamt**, jeweils mit Verlaufsgrafik, Tendenz und Begründungsbereich.
- Im gezeigten Ergebnis: **0,00** für alle drei Sichten, Schach und Go „Ausgeglichen“, ANDY Gesamt „Noch offen“.
- UI-Kennzeichnung: **„RESEARCH · NICHT REGELVERIFIZIERT“**; Modellurteil ist nicht identisch mit regelbasierter Tatsache.

**Bewiesen:** Der Benutzer konnte aus der laufenden Sandbox-Arena heraus mindestens eine reale Bewertung für den benannten Spielpunkt auslösen; eine Modellantwort und die zugehörige grafische Darstellung kamen an. Der manuelle Pfad über den bestehenden Game-Intelligence-Evaluator und die ANDY-LLM-Bridge ist damit grundsätzlich im Browser funktionsfähig.

**Nicht allein durch den Screenshot bewiesen:** In allen Fällen korrekte fachliche Bewertung; langfristige Verlässlichkeit oder Kalibrierung der drei numerischen Tendenzen; vollständige Modellwechsel-/Close-Reopen-Regression; Replay-Integration; Unveränderlichkeit jeder Snapshot-Payload unter allen Lastfällen. Drei identische 0,00-Werte sind Anlass für Qualitätsprüfung, nicht automatisch ein Fehlerbeweis. Der Nutzerbildschirm ist ein punktueller Browserbeleg, kein vollständiger Testbericht.

## 2. Aktuelle Umsetzung / bewusste Architekturgrenzen

- **Live v0.6** baut auf der zuvor funktionierenden **v0.5** auf; v0.6 adressiert die Aktivitätsanzeige und das Wiederöffnen des Panels.
- **Bestehende iframe-/HTML-Architektur bleibt erhalten**. Kein Ersatz durch native NiceGUI-Widgets ohne vorherige Nutzerentscheidung.
- **Vorhandene ANDY-LLM-Bridge:** KI-Bewertung über `evaluate_live_evidence()` und `andy_llm_bridge.call_llm()`; keine separate Provider-Infrastruktur für Game Intelligence.
- **Einziger Auslöser:** ausdrücklicher Knopfdruck auf **„Bewerten“**. Kein Timer, kein Polling zur automatischen Bewertung, keine Auto-Beobachtung und keine KI-Anfrage pro Spielzug.
- **Snapshot-Vertrag:** Beim Klick wird der Zustand zu Ereignis **X** fixiert. Die Antwort wird explizit zu **X** ausgewiesen; eine inzwischen weitergelaufene Partie darf die Zuordnung nicht stillschweigend auf X+1 usw. verschieben. Match, Ereignis, Modell und Snapshot-Fingerabdruck dienen der Zuordnung (Implementierungs-/Offline-Teststand aus v0.5/v0.6; nicht als vollständige Browser-Abnahme sämtlicher Randfälle missverstehen).
- Der Observer darf den **Match-Worker / KI-Spieler nicht anhalten oder verändern**. Modellwahl des Observers ist von den Modellen der Spieler zu trennen.
- Die Bewertung ist derzeit eine **Research-Einschätzung** auf der subjektiven Skala −2 bis +2, weder Centipawn-Auswertung noch Gewinnwahrscheinlichkeit; keine stillschweigend interpolierten KI-Messwerte.
- Technischer v0.6-Fokus: auffälliger **„Bewerten“**-Button, sichtbare **„KI arbeitet an Ereignis X“**-Aktivität und Wiederanbindung nach Schließen/Wiederöffnen. Für diese Fälle wurden vorab Offline-Tests berichtet; vollständige browserbasierte Regression bleibt zu prüfen.

### Verwandte Implementierungsstellen (Sandbox; zur Orientierung)

- `andy/presentation/shared/components/andy_game_intelligence_live02.html` — bestehender iframe und Grafik-UI.
- `andy/presentation/shared/components/andy_game_intelligence_live02_panel.py` — Panel-/Python-Anbindung, Request-/Response-Zuordnung.
- `andy/presentation/shared/components/andy_game_intelligence_eval02.py` — strukturierte LLM-Bewertung.
- `andy/presentation/shared/shell/andy_v1_shell.py` und `andy/features/arena/views/andy_arena_ui.py` — bestehende Arena-Anbindung des Evaluators.

Dateinamen sind die zuletzt dokumentierten Pilot-Pfade; ein erneuter Live-Datei-/Hash-Abgleich oder Code-Commit wird mit diesem Journal-Eintrag **nicht** behauptet.

## 3. Offene UX- und Funktionsfragen, ausdrücklich NICHT abgeschlossen

1. **Observer-Zusammenführung:** Die KI-Einschätzung ist derzeit noch ein **separates großes Modal**, das das Brett weitgehend verdeckt. Ziel: Einbindung als **wählbarer Analysemodus in das bereits vorhandene, verschiebbare und skalierbare Observer-iframe**, statt eines zweiten Fensters. Bestehende Pattern-/Replay-Funktionen beibehalten.
2. **Live UND Replay:** Gleiche Auswertungsverfahren für beide Datenquellen. Live bezieht Snapshot X aus der laufenden Partie; Replay aus dem gespeicherten Ereignis X. Muster-/Verlaufsanalysen bekommen bei Bedarf zusätzlich den Verlauf bis X. Keine pauschale Einschränkung auf nur einen Modus.
3. **Close/Reopen und Modellwechsel:** Laufende Bewertung soll außerhalb der Fensterlebensdauer zu Ende laufen; beim Wiederöffnen Aktivität/Ergebnis wieder sichtbar sein. Observer-Modellwechsel darf laufenden Auftrag nicht umetikettieren und **nie** das Spielermodell wechseln. Vollständige Realbrowser-Abnahme der kritischen Wege noch offen.
4. **Ergebnisqualität:** Schach-, Go- und Gesamturteil unabhängig und nachvollziehbar prüfen; Begründung, Unsicherheit, Modell, Provenienz und Ereignis X anzeigen. Keine Behauptung von objektiven Gewinnwahrscheinlichkeiten.
5. **KO/TKO-/Konfigurationsrisiken im Cockpit:** Echte Match-Konfiguration und Regelprüfungen sind maßgeblich; Budgetverbrauch, verbleibende Tokens, Fehlerfolgen und Entscheidungsgrenzen kompakt anzeigen. Grenzannäherung von einem regelbasiert bestätigten KO/TKO unterscheiden. Kleines Cockpit, keine übergroßen zusätzlichen Karten.
6. **Strategischer Kontext beim KI-Spielerwechsel:** Der aktuelle Zustand (FEN, Go, Ressourcen und Matchkonfiguration) muss vollständig bleiben; frühere strategische Ereignisse dürfen nicht auf die letzte Zuggruppe reduziert werden. Vorliegender Codebefund: `unified_state()` zeigt nur `state.log[-4:]` in der Kurzchronik. Zuerst Auswirkungen und vollständigen Promptpfad verifizieren, dann eventuell eine deterministische Spielübergabe konzipieren. Nicht Bestandteil der Live-v0.6-Abnahme.

## 4. Folgekonzept: Spielberater für Mensch gegen KI

**Nutzeridee (22.11.2026):** Der funktionierende Live-Bewerter ist eine **Vorstufe für einen Spielberater in Mensch-vs.-KI-Partien**. Eine separate KI soll den aktuellen Stand auswerten und beispielsweise die **drei besten nächsten Züge für den Menschen vorschlagen**. **Die Entscheidung über den tatsächlichen Zug trifft ausschließlich der Mensch.**

### Fachlicher Zielvertrag (Vorschlag; noch nicht implementiert)

1. Mensch fordert die Beratung ausdrücklich an: **„Zugvorschläge“** im gemeinsamen Observer-Analysemodus. Keine permanente Beratung, kein Timer, kein automatischer Modellaufruf.
2. Der Berater erhält denselben vollständig fixierten **Match-/Ereignis-X-Kontext** wie die Spieleinschätzung, ergänzt um die **menschliche Seite am Zug**, die tatsächlich aktive Konfiguration, relevante Regeln und den bisherigen Verlauf, soweit für die Auswahl erforderlich.
3. Ergebnis: bis zu **drei unterscheidbare, priorisierte Zugkandidaten** für den Menschen mit kurzer Begründung, erwarteter taktischer Wirkung in **Schach, Go und ANDY Gesamt**, Risiken/Unsicherheit und eindeutiger Kennzeichnung **„Vorschlag für Ereignis X“**.
4. **Regelprüfung vor Darstellung als spielbarer Vorschlag:** Kandidaten müssen gegen die bestehende ANDY-Zug-/Legalitätsprüfung validiert werden, einschließlich kombinierter Schach-/Go-Regeln und aktiver Ressourcen-/Matchkonfiguration. Nicht prüfbare oder ungültige Modellvorschläge als solche markieren, nicht als zulässigen Top-Zug ausgeben. Eine LLM-Rangliste ist kein objektiver Beweis für „beste“ Züge.
5. **Keine Zugausführung durch den Berater.** Keine Mutation des laufenden Spielstands, keine Änderung der Spieler-/Observer-Modelle, keine Budget-/Fehlerzähleränderung durch reine Beratung, soweit solche Effekte nicht ausdrücklich konzipiert und freigegeben sind. Nur die vorhandene menschliche Zugsteuerung führt nach Nutzerentscheidung einen Zug aus.
6. Die Partie darf während der Beratung weiterlaufen. Ist sie inzwischen bei Y statt X, muss die Anzeige **„Vorschläge für X – aktueller Stand Y“** lauten; keine Umdeutung zu Y. Gegebenenfalls Neuanfrage per Knopfdruck, nicht automatisch.
7. **Replay-Übertragbarkeit:** Dieselbe beratende Analyse kann retrospektiv „Was wären hier drei sinnvolle nächste Züge gewesen?“ beantworten, ohne die Replay-Daten zu verändern.
8. **Vor Umsetzung klären:** Wie eine kombinierte ANDY-Aktion fachlich repräsentiert und von der bestehenden Regelprüfung beurteilt wird; erst danach Vorschlagsformat und UI verbindlich festlegen. Das Feature bleibt **Konzept**, kein bereits gebauter Berater.

## 5. Abnahmestand / nächster Schritt

| Prüfung | Status | Evidenz / Grenze |
|---|---|---|
| Einzelne manuelle Live-KI-Bewertung auf 8082 | **PASS (Browserbeleg)** | Ereignis X=66; GPT-4o-mini; Antwort und Grafiken; angezeigte 2,8 s |
| Drei numerische Bewertungen fachlich plausibel/kalibriert | **NOT RUN** | 0,00 / 0,00 / 0,00 nur beobachtet |
| Antwort bei Fortgang X→Y korrekt zu X gebunden | **PASS (berichtet: Offline-Test)** / Browser-Negativtest **NOT RUN** | Kein vollständiger Laufzeitbeleg |
| Schließen/Wiederöffnen während laufender Anfrage | **PASS (berichtet: Offline-Test)** / Browser-Regressionsserie **NOT RUN** | Kein universeller Freeze-Fix belegt |
| Keine Beeinflussung der Spielermodelle | **NOT RUN** | Beobachtung bei Modellwechsel/Schließen gesondert prüfen |
| Integration in gemeinsames Live-/Replay-Observer-Modal | **NOT RUN** | Noch separates großes Modal |
| Spielberater Mensch-vs.-KI mit drei Vorschlägen | **NOT IMPLEMENTED** | Nutzerkonzept, keine Codeänderung |
| Studio 8080 / Factory 8083 | **NOT RUN / UNVERÄNDERT DURCH DIESEN DOC-EINTRAG** | Keine Synchronisation oder Codefreigabe |

**Nächste sinnvolle Etappe:** Erst die v0.6-Browserregression von KI-Aktivität, Schließen/Wiederöffnen und Observer-vs.-Spieler-Modellwahl abschließen. Danach die gemeinsame Observer-Oberfläche als explizit abgestimmten 8082-Kandidaten planen. Für den Mensch-KI-Berater zunächst die bestehenden ANDY-Regeln zur Legalität von Zugvorschlägen prüfen. Kein ungefragter Architekturwechsel.

## 6. Instanz-, Datenschutz- und Release-Schutz

- **Nur Dokumentation in diesem GitHub-Projektrepository**, keine Änderung des ANDY-Spielcodes, keine API-Anfrage, kein Start/Stop einer Partie.
- **8080 Studio und 8083 Factory nicht anfassen.** Kein ungeregelter 8082→8080-Sync, insbesondere nicht der Shell-/Rollen-Gates.
- Keine Originalpartien, Archivdateien, JSON/JSONL, SQLite, API-Secrets, lokale Backups oder UI-Designer-Freigaben in dieses Journal übertragen.
- Vor einem späteren Installer oder Sync gelten ausdrücklich [Entwicklungs-, Regression- und Release-Prozess](./ANDY_DEVELOPMENT_REGRESSION_POLICY_2026-11-21.md) und [SYNC-FEATURE-GATE-01](./ANDY_SYNC_FEATURE_GATE_CASE_2026-11-21.md).

**Provenienz:** Nutzerbeobachtungen und Browser-Screenshot aus dem ANDY-App-Dialog am 22.11.2026; Pilot-v0.5/v0.6-Implementierungs- und Offline-Testberichte aus demselben Arbeitsverlauf. Dieser Dokumentationseintrag ersetzt keinen Zugriff auf die aktuellen lokalen Source-Dateien, kein tatsächliches Git-Release und keinen vollständigen Regressionsbericht.
