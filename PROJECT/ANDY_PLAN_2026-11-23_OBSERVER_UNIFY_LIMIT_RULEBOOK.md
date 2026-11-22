# ANDY 2.0 — Arbeitsplan Montag, 23.11.2026: Ein Observer, terminale Spielbewertung, Aufruflimit und Spielberater

**Erstellt:** 22.11.2026 (Europe/Berlin), nach Browserbelegen aus Sandbox 8082.  
**Dokumentstatus:** Aufgaben-/Entscheidungsplan, **kein implementiertes Ruleset**, keine Änderung an laufendem Spielcode.  
**Priorität:** zuerst Installations-/Regression-Gate, dann Rulebook-Entscheidung, dann UI/Qualität.  
**Anwendung:** Sandbox `8082` zuerst; Studio `8080` nur nach gesonderter Freigabe; Factory `8083` nicht anfassen.

## 0. Beleg und Ausgangslage vom 22.11.

**Benutzerbestätigt:** Die bisherige Game Intelligence LIVE v0.6 kann per Klick eine LLM-Bewertung im Browser liefern und bei Ereignis X verorten. Das große gesonderte GI-Modal verdeckt aber das Spiel; Pattern/Spiegelung sind separat im bisherigen Observer.

**Neue Screenshots:** Eine Gemini-gegen-Gemini-Partie (Gemini 3.8 Flash vs Gemini 3 Flash Preview) erreicht das Aufruflimit:
- UI: `Beendet: Limit · Aufrufe · kein Spielsieg`, daneben `Archivierung läuft` (zu diesem Screenshot-Zeitpunkt). Finale Archivierungsbestätigung nicht vorliegend.
- `KI-Aufrufe: 100`, `Ausgeführte Züge: 90`, `Fehler/ungeklärt: 10`. **Nicht** behaupten, dass alle zehn dieselbe Fehlerklasse oder eine zusammenhängende Retry-Serie sind.
- Restliche sportliche Tokens laut Screenshot: **Weiß 10.733** bei 39.267/50.000 verbraucht; **Schwarz 8.908** bei 41.092/50.000 verbraucht. Keine Budgeterschöpfung.
- Go-Kontrolle **Weiß 30, Schwarz 25**. Dieser Vorsprung allein ist weder bestätigtes Go-KO (72) noch automatisch eine nachträgliche Gewinnentscheidung.
- In der gleichzeitig gezeigten Game-Intelligence-Bewertung zu **Ereignis X=100** steht ANDY-Gesamt noch **„Noch offen“**, obwohl die Arena die Partie bereits als beendet meldet. Diese fehlende Abbildung der terminalen Fakten ist ein klarer Integrations-/Evaluationsbedarf.
- Vorher beobachtet: wiederholt **0,00** für Schach/Go/Gesamt auch in späten Stellungen. Numerische Qualitätsprüfung steht aus; keine erfundenen Gewinnaussagen.

## P0 — Morgen zuerst

### P0.1 — OBSERVER UNIFY01 sicher anwenden und browserseitig prüfen

**Bestehender, noch nicht auf dem Mac angewendeter Kandidat:** `ANDY_OBSERVER_UNIFY01_8082_ONLY.zip`, `INSTALL_ANDY_OBSERVER_UNIFY01.py`. Gegenstand: **6 MODIFY, 1 ADD**, nur Sandbox 8082. Ziel: EIN bewegliches/skalierbares Observer-Fenster mit oberer Auswahl **Muster & Spiegelung** / **KI-Einschätzung**; für **Live und Replay**; bestehende iframe-Architektur behalten. Keine weiteren Modals, kein zweiter Sidebar-Eintrag. Die vorhandene LLM-Bridge bleibt unverändert.

**Voraussetzungen:** Archivierung der gerade beendeten Partie abgeschlossen; 8082 danach geordnet stoppen. Erst lokalen Dry Run prüfen (`DRY RUN OK`, exakte Hashes), dann nach expliziter Nutzerfreigabe `--apply`; bei Drift oder unklarem Status stoppen. Der Assistent kann die lokale 8082 auf dem Mac **nicht selbst starten/stoppen/installieren**, solange keine entsprechende lokale Computerverbindung besteht. Installer besitzt Stop-Port-Prüfung, Backup, Rollback.

**Abnahme Live:** Observer öffnen, verschieben, verkleinern; Brett sichtbar; Spiegelungs-/Pattern-, Geometry-, Pulse-, Inspector- und Research-Funktionen unverändert; oben auf GI wechseln; `Bewerten` löst genau eine Anfrage für X aus; Activity sichtbar; Ergebnis grafisch und korrekt zu X; zurückwechseln; während Aufruf schließen/wieder öffnen; keine verlorenen/hängenden Aufträge; Observer-Modellwechsel nicht gleich Spielerwechsel; Match-Worker läuft unabhängig.

**Abnahme Replay:** Archiv wählen; Replay-Slider X wählen; bestehende Muster-/Spiegelungsfunktion testen; gleiche GI-Ansicht liefert Evaluation X (rekonstruierte Positionen als **vorläufig** markieren); Wechsel des Sliders zu Y darf das Urteil zu X nicht neu etikettieren. Originaldaten unverändert. Negative Tests: leere/inkonsistente Replayposition, Dialog mehrfach öffnen, zwei Browseraktionen rasch nacheinander, laufender Modellwechsel.

**Status:** Offline- und lokaler Mock-Chromium-Test im Kandidaten als bestanden berichtet; **echte Installation/Live-/Replay-Browserabnahme noch ausstehend**. Kein Sync auf 8080 ohne separate Release-/Regression-Gates.

### P0.2 — Endzustand in Game Intelligence erkennen und anzeigen

Game Intelligence muss **verifizierte terminale Match-Fakten** aus bestehendem State/Ergebnis/Rulebook lesen: `running/finished`, `termination_reason`, `outcome_class`, `winner` oder `no_winner`, bei Bedarf Ressourcenstand sowie Aufruf-/Zug-/Fehlerzähler.

- Abschluss **nicht** als „Noch offen“ ausgeben, wenn die Partie beendet ist. Stattdessen z. B. „Beendet: Aufruflimit · kein Spielsieg“ und **separat** das KI-Positionsurteil („stellungsbezogene Tendenz“, kein offizielles Ergebnis) anzeigen.
- Den Evaluator auf eingefrorenem **X** verankern: Wenn X noch vor Partieende liegt, keine Information aus X+1 ... Endergebnis einschleusen. Bei X=terminal darf der Endgrund offiziell in die Evidenz einfließen. **Keine Future-Data-Leakage**, Live/Replay gleich.
- Status „Archivierung läuft“ vs „Archivierung bestätigt“ bei Quelle kennzeichnen, falls verfügbar, ohne das Archiv zu schreiben.
- Regressionstest: Spiel läuft; terminal durch KO, TKO, Go-Sättigung, Entscheidungslimit, manueller Stop, technischer Abbruch; unbekannte Resultate bleiben unbekannt.

### P0.3 — Offene Rulebook-Entscheidung: KI-Aufruf-/Entscheidungslimit

**Fall:** 100 KI-Aufrufe, 90 ausgeführte Züge, 10 Fehler/ungeklärte Versuche; kein Budget erschöpft; Go 30:25; keine bestätigte KO-Bedingung. Die Anzeige meldet „Limit · Aufrufe · kein Spielsieg“.

**Ausdrücklich zu entscheiden, nicht zu unterstellen:**
1. Ist `max_decisions` bzw. ein maximales **API-Aufrufkontingent** gemeint? Wie zählen fehlgeschlagene Calls, Retries, unbekannte Antworten, erzwungene PASS und „ausgeführte Züge“? Namen/Konfigurationsquelle im realen Code/Evidenz auditieren.
2. Wie wird „Limit erreicht“ sportlich klassifiziert: **DRAW**, **NO CONTEST / kein Spielsieg**, **ABORT/LIMIT**, oder eine **explizite zusätzliche Endpunktwertung**? Die bisherige UI „kein Spielsieg“ ist Ausgangsbefund, keine abschließend freigegebene neue Regel.
3. Falls eine Punktentscheidung gewünscht: **Welche Punkte**? Go-Kontrolle 30:25 allein? Chess-Position, Material, Mischregel? Wann ist eine Differenz signifikant? Ist dieses Ergebnis dann KO/TKO oder **eine eigene Ergebnisart**? Keine stillschweigende Umdeutung. Perspektive der beiden Seiten und Gleichstände festlegen.
4. KO/TKO-Begriffe **regelkonform** trennen: Schachmatt und Go-KO 72, Go-Sättigungs-TKO gemäß freigegebenem `ANDY_GO_SATURATION_01_RULESET_V1.2.md`; Ressourcen-TKO und Fehlerfolge/Retry-Regeln nach tatsächlich aktivem Ruleset; das bloße 100er-Aufruflimit ist aktuell kein nachgewiesener Ressourcen-TKO.
5. Priorität, Terminierung, Winner-Flags und archivierte Evidenz/Schemas/Leaderboard/Replay/Serien/Statistik bei neuer Regel prüfen. **Historische Partien unverändert** lassen, Ruleset-Version erhöhen und Alt-Resultate nicht rückwirkend umwerten.
6. Abnahmetests für identischen Stand bei 100 Calls inklusive Restbudget und unterschiedlichem Go-Vorsprung, Gleichstand, KO kurz vor Limit, TKO und echten Retryfällen.

**Referenz:** [Go-Sättigung Rulebook v1.2](./ANDY_GO_SATURATION_01_RULESET_V1.2.md) entscheidet gesondert TKO bei formaler/funktionaler Sättigung mit höherer Go-Kontrolle. [TKO Refund Research](./ANDY_TKO_REFUND_RESEARCH_v0.1.md) grenzt Budget-TKO von Retry/Abbrüchen ab. Kein Beleg, dass eine bloße Max-Calls-Grenze dasselbe ist.

## P1 — Danach, möglichst morgen

### P1.1 — Kompaktes Arena-Cockpit für KO/TKO-Gefahrenmonitor

- Aktueller **sportlicher** Tokenverbrauch (je Seite), Resttokens, Trend/pro Call und Nähe zur **konfigurierten** Grenze; kein frei erfundener TKO-Schwellenwert.
- Go-KO-Kontrolle vs 72, Chess-Matt/konkrete Drohungen, Go-Sättigungsstatus; **Warnung ≠ bestätigter Sieg**.
- Fehler-/Retry-Folgen **pro Klasse und Seite** statt 10 globale Fehler als „10 Strikes“ zu behandeln.
- API-Calls vs erfolgreiche Aktionen, aktuelles Call-Limit und echte Matchkonfiguration.
- UI: wenige gut lesbare Statuszeilen, Details aufklappbar, kein zusätzlicher breiter Dialog; Brett nicht schrumpfen oder verdecken.

### P1.2 — Qualität und Transparenz der KI-Bewertungen

- Ursache der häufigen **0,00 / 0,00 / 0,00** prüfen: zugelieferte Evidenz/Prompt, JSON-Ausgabeformat, Modellverhalten, Parser-Defaults, Kategorien-Skalierung und Abschlusssituation.
- Schach-, Go-, Gesamt-Tendenz und Unsicherheit differenzieren; bei terminalem Match **offizielles Ergebnis getrennt** vom subjektiven KI-Urteil.
- Begründungen konkret auf Stellung, Patterns, Konfiguration, Risiken beziehen; keine erfundenen Wahrscheinlichkeiten oder vollständigen Historien; Vergleich derselben X-Stellung mit mehreren Modellen möglich.
- GUI muss Aktivitäten zeigen; Ergebnis-/Anfrage-Bindung an Match, X, Modell, Snapshot-Fingerabdruck und Provenienz erhalten.

### P1.3 — Spielmuster & Spiegelung in Live und Replay konsistent

- Gezeigte Brettspiegelung als Research-Hypothese markieren und mit vorhandenen Mirror-/Geometry-/Pattern-Analysetools im selben Observer **live** inspizieren.
- Gegencheck an historischer Replay-Position X; Farben, Brettorientierung, statische versus **zeitlich reaktive** Spiegelungen unterscheiden.
- Keine „KI hat gespiegelt“-Kausalbehauptung allein aus Screenshot.

### P1.4 — Modellwechsel während der Partie: vollständige Strategieübergabe

- Spieler-Modellwechsel darf Kontext **nicht** auf den letzten Zug reduzieren: FEN, Go-Matrix, Spiel-/Ruleset-Konfiguration, Ressourcen, aktuelle Fehlerlage, relevante Verlaufskontexte.
- Die gezeigte `state.log[-4:]`-Kurzchronik im Promptpfad auf fachliche Folgen prüfen. Längerer Verlauf ggf. deterministisch verdichten, ohne neue Modellkosten; Tokenlast beachten.
- Observer-Modellwahl strikt von Spieler-Modellwechsel trennen; kein Neustart/Abbruch der Partie durch UI-Navigation.

### P1.5 — Perspektive Mensch vs. KI: drei Zugvorschläge

- GI-Evaluator als Grundlage für **Spielberater**: manuell anfordern, bis zu drei unterscheidbare begründete Kandidaten für die menschliche Seite aus **Snapshot X**.
- Vor Anzeige regelbasiert mit aktueller ANDY-Engine validieren. Chat-Liste ohne Legalitätsprüfung ist nicht ausreichend.
- **Mensch entscheidet**, Berater führt keinen Zug aus und verändert weder Partie noch Budget-/Fehlerzähler.
- Unterscheide „beste laut Modell“ von objektiv verifizierten Zügen. Auch im Replay als „Was wäre bei X möglich gewesen?“ einsetzbar.

## P2 — Nach Abnahme / kontrollierte Folgearbeiten

- Evidence-/Provenienzformat und Forschungsablage für KI-Bewertungen konzipieren; **keine ungefragten Writes** in Original-JSON/JSONL/SQLite.
- Live-/Replay-/Serien-/Leaderboard-Klassifikation nach **freigegebener** Limit-Regel testen; historisches Material unverändert.
- Gezielt entscheiden, ob/was 8082→8080 übertragen werden darf; Studio-Rollen-/Designer-Gates erhalten, Factory 8083 nicht anfassen.
- Bestehende ausstehende Designer-/Regression-Gates bleiben gesondert offen; keine parallele unkontrollierte Sync-Kampagne.

## Verbindliche Schutz- und Prozessregeln

1. Keine neue Observer-Modal-Architektur: **ein verschiebbarer Observer mit vorhandener iframe-Technik**. Nur auf Nutzerwunsch anders.
2. Keine automatischen Bewertungen/Timer: **nur „Bewerten“**.
3. Jede KI-Antwort gehört unverrückbar zu **Ereignis X**; zeitlich späteres Y darf nicht als X erscheinen.
4. Match-Worker, LLM-Bridge und Spielersteuerung bleiben beim Observer-Einsatz unabhängig; keine verdeckte Modellumschaltung.
5. Bei jeder Codeänderung **Dry Run, Hash-/Diff-Prüfung, Backup, Rollback, konkrete Browser-Ende-zu-Ende-Tests**; reale Testgrenzen markieren.
6. Keine stillschweigende historische Ergebnisumwertung, keine Originaldaten-/DB-/Secret-/Approval-/Symlink-Änderungen.
7. PFLICHT: [Entwicklungs-/Regressionsprozess](./ANDY_DEVELOPMENT_REGRESSION_POLICY_2026-11-21.md) und [Studio-Feature-Gate-Fall](./ANDY_SYNC_FEATURE_GATE_CASE_2026-11-21.md).

## Verweise

- [Game Intelligence LIVE v0.6, Browsermeilenstein und Mensch-KI-Berater](./ANDY_GAME_INTELLIGENCE_LIVE06_STATUS_AND_HUMAN_ADVISOR_2026-11-22.md)
- [Go-Sättigung Ruleset v1.2](./ANDY_GO_SATURATION_01_RULESET_V1.2.md)
- [TKO Refund Research](./ANDY_TKO_REFUND_RESEARCH_v0.1.md)
- [Forschungsideen Symmetrie/TKO/Vorteil](../research/andy-lab/ANDY_LAB_FORSCHUNGSIDEEN_SAMMLUNG_SYMMETRIE_TKO_VORTEIL_v0.1.md)

**Keine Regeln geändert, kein Mac-Code installiert, keine API-Aufrufe ausgeführt.**
