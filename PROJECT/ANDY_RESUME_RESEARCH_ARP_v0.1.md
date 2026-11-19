# ANDY 2.0 – Resume Research & ANDY Referee Protocol (ARP)

**Version:** 0.1 · **Stand:** 19. November 2026  
**Status:** Grundsatzentscheidung der Projektleitung / operativer Implementierungsauftrag; keine Produktionsfreigabe.  
**Herkunft:** Research Handoff „Resume Games & ARP“ des Chief-g-Analyzers nach Konsolidierung mit Qwen und DeepSeek, 19.11.2026, sowie operativer Dialog vom selben Tag.  
**Leitsatz:** Datenerfassung heute. Datendeutung morgen.

Bezug: [Match-Evidenz](ANDY_MATCH_EVIDENCE_JSONL_JSON_SQLITE_v1.0.md), [Serien-Forschungspipeline](ANDY_SERIES_RESEARCH_PIPELINE_SPEC_v0.1.md), [Drei-Instanzen-Architektur](ANDY_FACTORY_THREE_INSTANCE_ARCHITECTURE_v0.1.md), [Cache-Memo](ANDY_CACHE_01_IMPLEMENTATION_MEMO_v0.1.md) (Issue-Links siehe unten).

## 1. Beschluss und Ziel

**Resume Games sind ein eigenständiger Forschungsbereich.** Eine Fortsetzung ist sportlich dieselbe logische Partie, aber experimentell nicht zwangsläufig dieselbe Bedingung wie eine kontinuierlich gespielte Partie. Continuous Games und Resume Games dürfen nicht unbemerkt in gemeinsamen Spielserien, Rankings oder Kennzahlen vermischt werden.

Unmittelbares operatives Ziel: unterbrochene Partien zuverlässig fortsetzen. Ein Briefing soll Hindernisse beseitigen, nicht zu einer neuen Sackgasse werden. Es wird zunächst keine zusätzliche Forschungsanwendung, kein neuer kombinierter Forschungsindex und keine zweite Spiel-Engine gebaut. Rohdaten bewahren, vorhandene Mechanismen wiederverwenden.

Drei Forschungsbereiche:
- **Continuous Play:** reguläre, kontinuierlich ausgetragene Partien.
- **Resumption Research:** unterbrochene und wiederaufgenommene Partien; AI Orientation, Continuity & Recoverability.
- **Recap Benchmark:** eigenständiger späterer Orientierungstest ohne nachfolgendes Spiel; noch nicht implementieren.

**Environmental Punch:** fachlich relevante Umwelt verändert sich. **Continuity Break:** fachlich regelrelevanter Ausgangszustand bleibt unverändert; Unterbrechung verändert eventuell Kontextorganisation, Cache, Modellversion oder sonstige Rahmenbedingungen. Eine Strategieänderung ist weder automatisch schlechter noch ein Beleg für Reorganisation; ein Continuity Break könnte auch Lock-ins auflösen. Diese Aussagen sind Forschungsfragen, keine bestätigten Effekte. Transfer in Healthcare, Agentic Commerce, Compliance etc. bleibt eine spätere Hypothese.

## 2. Beobachtete Ausgangsfälle und offene Diagnose

- Claude Sonnet 5.5 / Grok 4.7: Grok antwortete nach langer Wartezeit und führte einen Zug aus; nachfolgende Claude-Aufrufe endeten wiederholt mit `unknown_token_usage`. Sportliches Restbudget war laut Anzeige vorhanden. Der Code bezeichnet eine unbekannte Abrechnung, nicht die nachgewiesene Ursache. Provider-/Adapter-/Kontextfehler bleiben zu prüfen. Lange lokale API-Wartezeit beweist keine aktive kognitive Verarbeitungszeit. Keine Schlussfolgerung auf erschöpftes Provider-Guthaben, falsche Keys oder Modellversagen allein aus dieser Evidenz.
- Grok 4.7 / Grok 4.7: im beobachteten ARP-Dialog meldete Weiß READY, Schwarz INCONSISTENT mit Rückfrage zum angeblich vorhandenen Ko-Verbot ohne Schnittpunkt. Die Speicherung einer historischen Referenzposition ist nicht gleichbedeutend mit einem konkreten Ko-Verbot. Die bisherige Beschreibung war nach operativer Diagnose mehrdeutig. Konkrete Ko-Legalität anhand der tatsächlichen Engine-Regeln prüfen, nicht allein aufgrund einer Modellaussage. Ein Einzelversuch beweist keinen Zugangsschlüssel- oder Qualitätsunterschied.
- Die gelbe Meldung über offene logische Archiv-/Leaderboard-Synchronisierung ist eine eigene Statusdimension; nicht mit dem API-Abbruch gleichsetzen. Belegsicherung, logischer Kettenzustand, Statistik und sportlicher Status separat prüfen.

## 3. Verbindliche Leitplanken

1. Originale JSONL **und** JSON unverändert; SQLite bleibt abgeleitete Projektion gemäß Match-Evidenz-Vertrag.
2. Jede Fortsetzung mit eindeutigen Segment- und Versuchsreferenzen. Auch gescheiterte, abgebrochene oder blockierte Versuche ohne Wiederanpfiff aufbewahren.
3. ARP getrennt vom sportlichen Wettbewerb: keine Belastung der sportlichen Tokenbudgets, Entscheidungsgrenzen oder Spielzeit durch Recap; tatsächliche API-Ressourcen trotzdem erfassen.
4. Referee vermittelt ausschließlich objektiv verifizierbare Spielgrundlagen, keine strategische Beratung, keine Offenlegung gegnerischer Antworten. READY ist Selbstauskunft, kein Beweis vollständigen Verständnisses.
5. Start erst nach expliziter Operator-Freigabe, gültiger Rekonstruktion und beidseitigem READY; keine Aufweichung bestehender Eignungs-, Ressourcen- oder Terminalitätsprüfungen. Stop respektieren, kein Doppelstart, keine unkontrollierte Retry-Schleife, keine zusätzlichen Paid Calls ohne Freigabe.
6. Unbekannte Werte sind unbekannt, nicht null im Sinne von 0. Keine künstliche Usage, kein künstlicher KO/TKO, keine nachträgliche Erfindung historischer Daten.
7. Kein automatisches Caching-Tuning, Key-Wechsel, Promptwechsel der regulären Spielzüge oder Änderung der Benchmark-Messmethodik im reinen Evidenz-Arbeitspaket.
8. Vollständige Inhalte nur in geschützten lokalen Artefakten bewahren; keinerlei Secrets, Authorization-Header, Zugangsschlüssel oder vertrauliche technische Daten in Forschungslogs oder öffentlichen Downloads. Öffentliche Freigabe getrennt prüfen.

## 4. ARP-Ablauf und Beobachtbarkeit

Nach Startbestätigung bleibt ein sichtbarer Dialog bestehen. Offline-Validierung und Reservierung des Fortsetzungsauftrags; getrennte Briefings für Weiß/Schwarz anhand desselben verifizierten Zustands und jeweiliger Rolle; Auswertung der Antworten. Statuswerte READY, QUESTION, MISSING_DATA, INCONSISTENT, API_ERROR, INVALID. Tatsächliche Modellausgabe von systemseitiger Interpretation oder Fehlerstatus unterscheiden.

Bei Klärungsbedarf verifiziert die Engine ausschließlich regelbezogene Fakten; in ARP-03A zunächst nur Ko und maximal eine zusätzliche Abfrage pro Spieler. Bei neuerlich 2/2 READY und unverändert gültigen Startbedingungen automatisch Wiederanpfiff. Andere oder ungelöste Widersprüche bleiben sichtbar und sperren den Start; Operator kann kontrolliert abbrechen. Keine erzwungene READY-Meldung. Ein allgemeiner freier Dialog ist noch kein zugesagter Implementierungsstand.

**UI:** Inhaltlicher Dialog im Vordergrund, aufklappbares technisches Live-Protokoll, Token/Cache/Zeit je Spieler und Runde, lokaler API-Wartestatus, STOP und Export. Den Übergang zum ersten regulären Spielaufruf sowie technische Fehler und Archivstatus im Protokoll erfassen; erneutes Öffnen bei Abbruch. Weder UI-Status noch READY allein beweist erfolgreiche Spielfortsetzung.

## 5. Minimale Evidenzarchitektur (P0)

Bestehende Match-Dateipaare und ARP-Begleitprotokolle erweitern statt neue Datenbankstruktur zu erfinden. Drei funktionale Ebenen:
- **A. Haupt-JSONL / Match-JSON:** sportliche Ereignisse und kompakte Referenz auf Resume/ARP-Ereignis; Originale bleiben unverändert.
- **B. ARP-/Resume-Begleitprotokoll:** vollständige chronologische Ereignisfolge inklusive erfolgloser Versuche, pro Call/Runde/Spieler; nicht nur ein aggregiertes Objekt. Bestehendes `arp_briefings` als Ausgangspunkt prüfen. Außerhalb normaler Match-Scanner ablegen bzw. eindeutig typisieren.
- **C. Kontext-/Request-Artefakte:** tatsächlich übermittelte System-/User-Nachrichten, relevante Historie, multimodale Bestandteile und Klarstellungen mit sicheren Referenzen und Prüfsummen. Kein bloß nachträglich rekonstruierter Prompt als Ersatz. Geschützte Ablage und separate Exportfreigabe; Prüfsumme ist kein Ersatz für Inhalt.

Konkrete Pfade, Feldnamen und Versionierung am tatsächlichen Quellstand abgleichen; nachstehende Benennung ist ein Zielvertrag, keine Behauptung existierender Felder.

### 5.1 Identifikation
Original Match ID, Resume Segment ID (falls erzeugt), Resume Attempt ID (auch bei Fehlschlag), unmittelbares Parent-Segment, Fortsetzungsnummer, letzter gültiger Zug/Entscheidungspunkt, Unterbrechungszeit und belegter Grund, Start des Versuchs, tatsächlicher Wiederanpfiff (falls erfolgt), Ausführungsstatus. Mehrere Versuche ohne Spielaufnahme nicht als mehrere fortgesetzte Partien zählen. Ketten und spätere experimentelle Branches eindeutig getrennt verknüpfen.

### 5.2 Zustand und Kontext
`resume_baseline_hash` als versionierte SHA-256-Prüfsumme eines deterministisch serialisierten regelrelevanten Zustands. Letzten gültigen Ausgangszustand und rekonstruierten Zustand getrennt ermitteln und prüfen; Schachposition inklusive regelrelevanter Zusatzinformationen, Go-Position, Ko-/historische Referenzzustände, Phase, Zugreihenfolge, Go-Kontrolle, Regelparameter und Zähler. Sportliche Budgets, Strategien und Modellparameter als separate Kontrollgrößen vergleichen. Mismatch blockiert Start. Identischer Zustand ≠ identischer Prompt.
Pro Request tatsächlich an Adapter/Provider übergebenen modellrelevanten Inhalt (am letztmöglichen beobachtbaren Punkt), Prompt-Version, Prompt-Hash, Request-Parameter und Referenzen erfassen. Interne providerseitige Transformationen nicht als bekannt ausgeben. Frühere Kontextdaten, die nie gespeichert wurden, nicht nachträglich als exakte Requests etikettieren.

### 5.3 ARP-Ereignisse
Spieler/Seite, Round/Call ID, Zeitstempel, Request-/Kontextreferenz, tatsächlich empfangene sichtbare Modellantwort vor Normalisierung, interpretierter Status, normalisierte Rückfrage, objektives Prüfergebnis, exakte Referee-Klarstellung, Folgestatus, Fehlerklasse und verfügbare bereinigte Fehlerdetails. Lokale Interpretation von Provider-Antwort trennen. Start, Stop, Blockade, Wiederanpfiff und Ende eindeutig protokollieren.

### 5.4 Ressourcen und Zeit
Pro Call und Spieler Input, Output, Reasoning, Cache Read/Write bzw. gemeldete Cache-Werte, Provider-Gesamtwerte, ursprüngliche Usage-Struktur, Request-Start, Response-Ende, lokales Warten, Retry-Anzahl, erster Antwortbestandteil bei vorhandenen Streaming-Daten, providerseitige Zeiten soweit verfügbar, tatsächliche oder später nachvollziehbar berechenbare Kosten. Fehlende Angaben als unknown/null mit Begründung. Anbieterabhängige Semantik beachten; Cache- und Reasoning-Teilwerte nicht ungeprüft zu Gesamtwerten addieren. Kosten nur mit belegter Preis-/Währungsgrundlage ableiten. Keine zusätzlichen Modellaufrufe zur Messung.

### 5.5 Übergang in den Wettbewerb
Referenz auf letzte verfügbare Modellbegründung und letzten tatsächlich ausgeführten Zug vor Unterbrechung; erster tatsächlicher Request und erste sichtbare Antwort nach Wiederanpfiff soweit verfügbar; angekündigte Handlung, ausgeführte Handlung, Validierung, Folgen, Ressourcen; alle weiteren regulären Entscheidungen aus bestehendem Matchprotokoll. Keine Behauptung über nicht offengelegte interne Gedanken. Auswertungsfenster später 1/3/5/10 Züge und darüber hinaus, ohne zusätzliche Calls.

## 6. P1 – Erweiterte Beobachtbarkeit

Anbieter, angefragte/tatsächlich gemeldete Modellkennung und Version soweit verfügbar, SDK/Adapter/Engine/ARP/Ruleset-Version, Reasoning, Temperature, Seed, weitere Sampling-Parameter, Kontextmodus, anonymisiertes Zugangsprofil und bekannte Account-/Workspace-/Cache-Zuordnung. Keine Speicherung tatsächlicher Keys oder Secret-Fingerprints. Nicht offengelegte Informationen als unbekannt.

Recap Monitor: pro Modell und Zugangsprofil aggregierbare Input-/Output-/Cache-/Reasoning-Werte, Zeit und Klärungsrunden; getrennt je Einzelcall und Gesamtbriefing. Rohdaten behalten; Aggregationen sind Ableitungen. Unterschiedliche Keys sind nicht automatisch unterschiedliche Cache-Grenzen. Gleiche Keys garantieren keine Cache-Treffer. Mehrere Key-Profile sind zunächst Konzept; keine eigenmächtige Änderung der lokalen Konfiguration.

## 7. Klassifikation und gemeinsame Leser

Ziel: Continuous Play, Resume Games und später Recap-only in Arena, Replay, Archiv, Leaderboard, Serien und Lab sichtbar getrennt. Ein blockierter Resume-Versuch ohne Wiederanpfiff ist ein Orientierungs-/Recoverability-Ereignis, nicht automatisch ein erfolgreich fortgesetztes Match. Unklare historische Herkunft als unknown; keine stille Umklassifizierung. Ein logisches Match nicht pro Segment als neues sportliches Ergebnis zählen. Experimentelle Branches ausdrücklich als Branches markieren und nicht mit linearer Fortsetzung verwechseln.

Logische Kettenaggregation über vorhandene Leser und Evidenz-Projektionen lösen. Aktuelle offene Archiv-/Leaderboard-Projektion nicht als erledigt markieren. Factory später ausschließlich getrennte, explizit autorisierte Serien; keine Produktionsfreigabe oder Änderung der bisherigen Watchdog-Priorität durch dieses Memo.

## 8. P2 – Spätere Forschung (nicht Gegenstand der jetzigen Implementierung)

Kontrollierte Gruppen: A kontinuierlich; B unmittelbar wiederaufgenommen mit möglichst identischem Kontext; C zeitversetzt mit vollständiger Historie; D verdichtete Historie; E nur regelrelevanter Zustand ohne alte strategische Begründungen; F gezielt variierte Cache-Bedingungen, soweit kontrollierbar; G ARP-only. Spätere Verzweigungen desselben verifizierten Zustands, unabhängige Wiederholungen, konstant gehaltene Regeln/Budgets/Rollen/Parameter/Versionen soweit möglich; Abweichungen ausdrücklich dokumentieren. Kein Kausalitätsnachweis aus einem Einzelversuch.

Kandidaten: Time to Ready, Tokens to Ready, Clarification Overhead, Critical Awareness, False Readiness, Resume Cost, Resume Quality Delta, Strategy Continuity, Reorganization Cost/Quality, Return on Epistemic Investment (ROEI). Kein automatisches Scoring, keine automatische Feststellung eines Datenresonanzpunkts. Schnelle READY-Meldung, Rückfrage oder hoher Aufwand können jeweils unterschiedliche Ursachen und Qualität haben.

## 9. Operativer Stand und Reihenfolge

| Paket | Berichteter Stand / nächster Schritt |
|---|---|
| ARP-01 | Ready Check und separate Briefing-Ressourcen im Entwicklungsdialog ausgeliefert; tatsächlichen installierten Stand prüfen. |
| ARP-02 | Live-Protokoll; Browser-Screenshot belegt sichtbaren Grok-Ko-Einwand. Export, Fehlerdetails und Ressourcenfelder am tatsächlichen Stand prüfen. |
| ARP-03A | Installer für präzise Ko-Beschreibung, eine begrenzte automatische Klärung, erneute READY-Abfrage, getrennte Ressourcen und Prompt-Hash ausgeliefert; simulierte Tests berichtet, echte Wiederanpfiff-Abnahme offen. |
| ARP-03B | Inhaltliche Dialogoberfläche, nachvollziehbare Referee-Klärung, technischer Expander; noch umzusetzen. |
| ARP-EVIDENCE-01 (P0) | Vor weiteren Forschungsserien Ist-Audit, vollständige tatsächliche Requests/Antworten/Usage, baseline und Referenzen als minimale Erweiterung implementieren. |
| RESUME-CLASS-01 | Separate Kohorten und logische Kettenleser; noch umzusetzen, keine rückwirkende Originalmutation. |
| ARP-RESEARCH (P2) | Spätere Auswertung im Forschungsthread. |

**Reihenfolge:** ARP-03A real abnehmen und tatsächlichen installierten Stand read-only auditieren; ARP-03B und ARP-EVIDENCE-01 eng verzahnt umsetzen, P0-Datenbewahrung bei UI-Arbeit nicht aufschieben; RESUME-CLASS-01 vor regulärer gemeinsamer Statistik-/Serienfreigabe. Zunächst 8082. 8080 und 8083 erst separat geprüfte Übernahme. Kein pauschales Factory-Freeze, kein stilles Umschalten von Keys, keine Finanzierungserweiterung.

**Ist-Abgleich aus Entwicklungsdialog (noch kein aktueller unabhängiger Code-/Lokal-Audit):** separate ARP-JSONL, Tokenabrechnung, erfolglose Briefings, Segmente, Ko-Klärung und Prompt-Hash wurden als vorhanden berichtet. Vollständiger echter Prompt, nicht normalisierte Antwort, baseline_hash, rohe Usage, Zeit-/Konfigurationsmetadaten und Kohortentrennung sind zu prüfen bzw. zu ergänzen. Keine historischen Lücken durch Schätzwerte schließen.

## 10. Abnahmekriterien

- [ ] Gleicher verifizierter Zustand vor/nach Rekonstruktion; absichtlich abweichender Zustand blockiert.
- [ ] 2/2 READY startet exakt einmal; Ko-Fall ohne aktives Verbot und echtes Ko regelkonform geklärt; ungelöste Frage oder Stop startet nicht; keine strategische Info an Gegner.
- [ ] Erfolgreiche und fehlgeschlagene Attempts eindeutig identifizierbar, auch ohne Segment; Originaldateien bytegleich, keine Doppelzählung.
- [ ] Fixture zeigt exakten übermittelten Prompt und sichtbare Antwort vor Interpretation plus Hash, Klarstellung und Übergang zum ersten Spielaufruf; keine Secrets in Logs/Exporten.
- [ ] Cache-/Reasoning-/Usage-Varianten und fehlende Werte korrekt, separate Briefing-Abrechnung je Spieler/Call; sportliche Budgets, Zeit und Grenzen unverändert.
- [ ] Claude/Grok-Fehler oder simulierte gleichartige Fehler liefern interpretierbare Provider-/Adapter-/Engine-Status ohne Spekulation; Archivstatus separat; Live-Protokoll bleibt erreichbar.
- [ ] Klassifikation unterscheidet Continuous, Resume, erfolglose Attempts und unbekannte Historie; Match-Kette zählt sportlich nur einmal; Replay/Lab/Leaderboard/Serien kompatibel.
- [ ] Offline-Regressionstests, idempotente Installation, Backup und Rückrollbarkeit; anschließend explizit autorisierte reale 8082-Abnahme. Kein neuer Paid Call allein durch Audit/Installation.

Bestehende Issues: [#5 TECH-DEATH-01](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/5), [#6 RESUME-02](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/6), [#8 WATCHDOG-02](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/8). Dieses Dokument ergänzt die bisherigen Evidenz-, Recovery- und Factory-Verträge; es schließt keine Issues und ersetzt keine noch ausstehende Abnahme.

**Erleben. Erforschen. Erahnen. Actor. Network. Dynamics.**
