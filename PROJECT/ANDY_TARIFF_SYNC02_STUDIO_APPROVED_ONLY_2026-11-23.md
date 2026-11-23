# ANDY TARIFF-SYNC02 – Studio 8080 mit freigegebenen Economy-Tarifkarten versorgen

**Stand:** 23.11.2026, nachdem der Nutzer den Read-only-Audit01 auf dem Mac durchgeführt und JSON/MD hochgeladen hat.  
**Status:** Befund bestätigt, isolierter Transferkandidat vorbereitet und offline getestet. **Noch nicht auf dem Mac ausgeführt, keine echte 8080-Browser-Abnahme.**

## Audit-Befund (tatsächlich lokal erhoben)

- **8080:** Tarifdatenbank am erwarteten Pfad fehlt (`DB_NOT_PRESENT`). Der korrekte Studio-Calculator mit SHA `373a735f14dd56a7211fe001477f079c257287ff1c359b13af6930fed0302d87` wurde verifiziert.
- **8082:** 15 Tarifkarten, davon 13 approved und 2 Entwürfe, Audit-Revision 15; Calculator SHA `1f4d31415c75489df36d6fd498f9524d14c0ae905548a0319ef92a6933bc3fe4` verifiziert.
- **Zeitbereich:** Alle 13 freigegebenen Karten gelten ab 31.10.2026 23:00 UTC bis 30.11.2026 23:00 UTC (November 2026 in Berlin).
- **Relevante Anbieter/Modelle:** GPT-6 Astra, GPT-6.1 Sol, GPT-5.2, GPT-4o mini, Claude Opus/Sonnet 5.5, Gemini 4 Argon/3.8 Flash/3.1 Flash Lite/3 Flash Preview, DeepSeek Flash/V4 Pro, Grok 4.7.
- **Aufrufpreis-Test noch nicht möglich:** Der Audit fand die Original-JSONL von `andy_0c0f7413fdf6` im Studio-`runs` nicht; Ergebnis `UNAVAILABLE`, `SKIPPED_NO_MATCH_EVENTS`. Der Screenshot zeigte 118 protokollierte API-Aufrufe, Input-/Output/Reasoning- und Zeitwerte, aber **0/118 mit Kostenwert**. Die fehlende 8080-Tarif-DB erklärt die fehlende tarifbasierte Bepreisung sehr plausibel. **Eventgenaue Modell-/Route-/Intervall-Coverage ist nicht bewiesen.**

## Ursache (bewiesen vs. offen)

**Bewiesen:** Ein sauberer Code-Sync hatte den instanzspezifischen 8080-Tarifpfad hergestellt, jedoch keine freigegebenen Karten dorthin übertragen. Dieses Verhalten war im SYNC02-Dokument sogar als zu erwartende Einschränkung dokumentiert. Die instanzspezifische Trennung ist korrekt; die Funktionsabnahme war trotzdem **unvollständig**.

**Noch offen:** Ob nach dem Transfer alle 118 historischen Entscheidungen einem passenden approved Tarif zugeordnet werden können; fehlende oder anders semantisierte Provider-Reasoning-Tokens werden dadurch nicht nacherzeugt.

## Minimaler Transferkandidat

**Lokal aus dem ANDY-App-Chat bereitgestellt:** `ANDY_TARIFF_SYNC02_APPROVED_ONLY.zip`, enthält `ANDY_TARIFF_SYNC02_APPROVED_ONLY.py` und README. Es enthält **keine persönlichen Tarifdatensätze und keine Datenbank**.

Default **DRY RUN**; `--apply` nur bei gestopptem Studio 8080. Das Skript:

1. Prüft den erwarteten Codehash beider Economy-Calculator-Module, die separate 8082-Tarifdatenbank, SQLite-Integrität, Schema und exakt den Auditscope (15 Karten: 13 approved, 2 drafts; Rev 15).
2. Erstellt eine **neue, eigenständige 8080-Tarifdatenbank**, ausschließlich mit den 13 approved Karten. Bewahrt Modell-ID, API-Route, Zeitraum, Originalkarten-ID, USD/1M-Raten, Herkunftsnachweis und zugehörige Audit-Einträge; ergänzt lokalen Import-Provenienzeintrag je Karte.
3. Veröffentlicht erst nach vollständiger Validierung und ohne Überschreiben existierender 8080-Dateien. **8082 bleibt unverändert**. Bei bereits vorhandener fremder 8080-Tarifdatenbank wird der Transfer blockiert.
4. Schreibt ein Receipt in `~/Downloads`; wiederholter Lauf erkennt unveränderten erfolgreichen Import. `--rollback` verschiebt die **unveränderte** importierte 8080-Tarifdatenbank in ein Downloads-Archiv und löscht keine Benutzerdaten. Drift blockiert.
5. Originalspiele, andere DBs, Code, Git, Designer, Factory 8083, Secrets bleiben unberührt.

## Teststatus

- **PASS (offline):** 5 isolierte Testfälle für Dry Run, 13 approved-only Transfer, Source-DB-Unveränderlichkeit, Audit-Provenienz, erneuten Apply, gültigen Rollback, Blockaden für unerwarteten Studio-DB-Bestand, Quellbestandsänderung, Moduldrift und nachträglich bearbeitete Studio-Tarifdatei.
- **PASS (isolierte Preisberechnung):** Astra mit 791 Input-/376 Output-Tokens ergibt 0,02671 USD als `LEGACY_PROXY` (tarifbasierte Schätzung), gleiche Rechnung auf Test-8082 und Test-8080.
- **NOT RUN:** Mac-Apply, Live-Browser/Replay-Coverage, 118 konkrete Calls, Kosten-UI nach Neustart, Studio-Tarifeditor, Designer-End-to-End-Regression.

## Nächstes Gate

Zuerst **nur Dry Run auf dem Mac** durch den Benutzer. `--apply` erst nach seiner Rückmeldung und bei gestopptem 8080. Danach Audit01 **erneut** ausführen (Ziel: 8080 13 approved, 8082 unverändert 15 Karten) und im selben Replay/Observer-Browser die Kostenwerte nachprüfen. Erst danach SYNC02 als fachlich vollständig abnehmen.

**Prozessfehler vermeiden:** Code-Sync und Betriebsfähigkeit des Features unterscheiden; Daten-/Metadaten-Voraussetzungen pro Instanz im Release-Gate dokumentieren. Siehe [verbindlicher Regressionprozess](ANDY_DEVELOPMENT_REGRESSION_POLICY_2026-11-21.md) und [Feature-Gate-01](ANDY_SYNC_FEATURE_GATE_CASE_2026-11-21.md).
