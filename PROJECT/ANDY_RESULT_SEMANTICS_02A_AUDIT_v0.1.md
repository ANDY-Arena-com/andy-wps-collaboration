# RESULT-SEMANTICS-02A — TKO-Evidenz-Audit V0.1

**15.11.2026 · isolierter Audit-Kandidat, nicht installiert**

Vor FACTORY-01 wird die gemeinsame Ergebniswertung konsolidiert. KO und belegbarer TKO sind sportliche Siege. Endtyp und Gewinnerzuordnung unterscheiden; historische Unsicherheit sichtbar halten. Bezug: [Betriebsmodell](ANDY_SYNC05_RELEASE_AND_OPERATING_MODEL_v0.2.md), [Factory Budget Preflight](ANDY_FACTORY_BUDGET_PREFLIGHT_v0.1.md).

## Tatsächlicher Entwicklungsstand

Im SYNC-05-Kandidaten ist der bisherige TKO-Resolver auf Budgetüberschreitung spezialisiert; Retry-TKO wird in verschiedenen Ansichten und historischen Leaderboard-Pfaden unterschiedlich behandelt. RESULT-DISPLAY-01 bleibt optisch unverändert. 02A ist ein eigenständiger read-only Auditor, noch keine Änderung der App-Wertung.

- TKO-Kandidaten: budget_overshoot, output_limit_retries_exhausted, illegal_retries_exhausted.
- Strikter Nachweis anhand originalem JSON/JSONL-Paar, konsistenter Match-ID, Start-/Endrahmen, Akteurszuordnung, Entscheidungszahl, kumulativen Konten und terminaler Retry-Folge. Kein unabhängiger Engine-Nachweis.
- Unbekannte oder widersprüchliche Belege bleiben offen. Resume-Segmente nicht separat werten; logischen Resolver in Folgepaket integrieren. Doppelte IDs über Archive hinweg ausweisen, nicht als unabhängige Siege summieren.
- Format-/other-Retry-Erschöpfung, exakte Budgeterschöpfung und technische Abbrüche außerhalb dieses Auditumfangs; bei Bedarf fachlich separat klären.
- Keine Datenbanköffnung, API-Anfrage, Installation, Rankingänderung oder Originaldatenmutation.

## Nachweis

42 synthetische Offline-Tests bestanden. Vier vorhandene DeepSeek-Originalpaare lieferten nach dem strikten Kandidaten zwei Budget-TKO und zwei Output-Limit-TKO, jeweils mit belegbarer Gewinnerseite. Hashes der Originale nach dem Audit erneut geprüft. Doppelte IDs im simulierten Zwei-Archiv-Audit erkannt. Kein realer Illegal-Retry-Referenzfall in dieser Stichprobe. Keine Pauschalaussage über Modellqualität aus vier Selfplay-Partien.

Lokales Paket: ANDY_RESULT_SEMANTICS_02A.zip, SHA-256 b1bcae4c7714b28582ed1f95e91b886af81da312ea11f1370de7fc5f7988b44c. ZIP-CRC und enthaltene Bytes geprüft. Nicht als GitHub-Release-Asset veröffentlicht.

## Nächste Abnahme

Projektleitung führt AUDIT_RESULT02A.py lokal aus; beide Apps dürfen weiterlaufen. Ergebnisbericht auf Vollständigkeit, Dubletten, Konflikte und historische Sonderfälle prüfen. Die gesamte Archivabfrage am Mac steht noch aus; keine atomare Momentaufnahme beider Archive, nur Einzeldateikonsistenz. Anschließend 02B: Resolver-Konsolidierung mit bestehenden logischen Resume-Ketten, Arena/Replay/Review/Serien/Leaderboard/Lab-Export, Offline-Regression und expliziter Dry-run einer späteren Wertungsprojektion. Keine rückwirkende Mutation ohne Freigabe. FACTORY-01 folgt der Ergebnisintegration; Funding-Audit kann parallel vorbereitet werden. Budget-Preflight bleibt Voraussetzung für autonomes kostenpflichtiges Autoplay.
