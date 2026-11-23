# ANDY Live Observer → Data / Living Lab — DeepSeek Review 1

**Eingang:** 23.11.2026, vom Projektleiter im ANDY-App-Thread weitergegeben.  
**Quelle:** als DeepSeek-Review zugeordnete externe Rückmeldung aus dem Chat. **Redaktionell strukturierte Übertragung**, nicht als neue direkte Modellbefragung oder wortgetreues Transkript aus einer externen API ausgeben.  
**Status:** fachlicher Vorschlag, keine bereits installierte Data-Architektur, keine Codeänderung.

## 1. Kernurteil

Der funktionierende gemeinsame iframe-Observer mit Pattern/Mirroring, manuellem GI und Economy für Live/Replay ist eine brauchbare Grundlage. Für die Forschung muss **ein idempotenter Datenfluss** verhindern, dass der Observer neben der Data & Evidence Engine eine konkurrierende Datenquelle etabliert. Ein **kanonischer Observation-Vertrag** soll Ereignisse aus Live, Replay und Legacy mit Identität, Herkunft, Methode, Qualität und Granularität verbindlich verbinden. Die Forschungsintegration ist wesentlich ein Datenarchitekturproblem, nicht ein neues Chart-Problem.

## 2. Vorgeschlagenes kanonisches Event-/Observation-Schema

- **Identität**: `match_id` (logische Partie), `segment_id` (Resume/Refund), `event_x` (historische Ereignisposition).
- **Attempt vs. Action**: `api_attempt_id` und `executed_action_id` getrennt, um fehlgeschlagene Calls und Retries nicht als Züge zu zählen.
- **Provenienz**: `source_hash` von Original-JSONL/Matchbericht, `ingestion_timestamp`, `observer_version`, `method_version`, bei Kosten/LLM zusätzlich `tariff_version`, `fx_rate_version` und tatsächliche Modell-ID.
- **Qualität**: `quality_flag` mit unterschiedlichen Kategorien für verifiziert, rekonstruiert, heuristisch, LLM-annotiert, Tarifschätzung.
- **Granularität**: `observation_granularity` pro Zug / API-Aufruf / Intervall.
- **Observation-Typen**: `pattern_snapshot`, `gi_score`, `economy_metric` sowie erweiterbare typspezifische Payloads.

Kritisches Risiko: Drei voneinander getrennte vollständige Schemata für Pattern/GI/Economy erzeugen konkurrierende Rechen- und Forschungsdefinitionen.

## 3. Wiederverwendung: drei Ebenen

1. **Originaldaten**: JSONL + JSON immutable/read-only; Observer liest und erzeugt Ableitungen, schreibt nicht in die Primärquelle.
2. **Normalisierte Events und Beobachtungen**: Data & Evidence Engine soll dieselben Verträge für Replay, Observer und Lab bereitstellen. Vorgeschlagen ist ein einheitlicher Ingestion-Pfad und keine unabhängige Observer-Matchdatenbank.
3. **Lab/Research**: Lab-Explorer/Builder fragt normalisierte, versionierte Events/Observations ab und verknüpft sie über Modelle, Zeiträume, Konfigurationen und Partien.

Getrennte Tarif-SQLite als Metadatenquelle ist aus DS-Sicht nur reproduzierbar, wenn die tatsächlich angewendete Tarif-/FX-Version im Kostenbeleg referenziert und historisch auflösbar bleibt.

## 4. Provenienz je Ableitung

- `derived_from` — Originalevent / Source-Hash.
- `transformation` — z. B. Pattern-Extraction, GI-Score, Economy-Berechnung mit Version.
- `input_parameters` — z. B. FX-Faktor, Tarifkarte, Prompt-/Snapshot-Fingerprint.
- `uncertainty` — Unsicherheits- oder heuristische Einschränkung, soweit sinnvoll.
- Vorläufig rekonstruierte Replay-Brettzustände dürfen nicht als unabhängig engineverifiziert ausgegeben werden.

## 5. Drei Schnittstellen (als Vorschlag, Bestand nicht verifiziert)

1. **Ingestion Observer → Data**: normalisierte Observation-Events über *bestehende Schnittstelle, falls vorhanden*, statt direkter unabhängiger Datenbank-Writer.
2. **Query Data → Lab**: Filter nach Match, Typ, Qualität, Modell, Version und Zeit.
3. **Annotation Lab → Data**: hypothesespezifische Erkenntnisse als neue, auf Basisbeobachtungen zurückverweisende Annotationen.

Ein physischer Event-Bus oder genau eine vorhandene Ingestion-API wurde **durch diesen Review nicht im lokalen Code nachgewiesen**.

## 6. Drei vorgeschlagene Inkremente

### I. Schema und read-only Export während Sync
Ein kanonisches Observation-Schema spezifizieren; bereits sichtbare Daten nach Live/Replay/Legacy in ein **read-only Testexportformat** übersetzen. Prüfen: lückenlose Provenienz und Trennung API-Aufruf/ausgeführter Zug. Noch kein Produktiv-DB-Write.

### II. Idempotente Normalisierung und Provenienz nach Sync
Observation-Ableitungen kontrolliert in die bestehende Evidence Engine übernehmen. Mehrfachimport derselben Quellen darf kein zweites Sample erzeugen; Qualitätserhöhungen nachvollziehbar versionieren.

DS schlägt für Upsert anfänglich einen Schlüssel aus `source_hash + event_x + observation_type` vor. **Kritische Präzisierung durch die Integrationskoordination nötig:** Das reicht allein nicht für mehrere KI-Urteile zum selben X, getrennte Spieler/Versuche, Modell-/Methodenversionen oder mehrere unabhängige Aufträge. Vor Umsetzung Schlüssel und Append-only/Korrektursemantik vereinheitlichen.

### III. Lab-Explorer-Anbindung
Read-only Views im bestehenden Lab-Explorer, Join auf Match-/Konfigurationsdaten; reproduzierbare erste Hypothese mit klaren Quality-Flags und keinerlei Originalmutation. Test: Replay-/Live-Duplikat und rekonstruierte Positionen nicht als unabhängige verifizierte Evidenz zählen.

## 7. Wichtigste Risiken / Gegenargumente

- Eine neue Observer-Dateninsel würde künftige Migration und Konflikte erzwingen.
- Unbekannte Werte, Rekonstruktionen und Methodenversionen dürfen in Summen nicht verschwinden.
- Alle fachlichen Datenarten und Zeitachsen brauchen eine eindeutige Verknüpfung.
- Eine bestehende normalisierte Pipeline ist als **Ziel**, nicht als bereits bewiesene konkrete API zu verstehen.

## 8. Redaktioneller Integrationsvermerk

Dieser Review liefert einen wertvollen gemeinsamen **Datenvertrag**. Nicht alle berechenbaren Kennzahlen müssen deshalb als eigenständige immutable Records gespeichert werden. Der Qwen-Review argumentiert ergänzend für **ein gemeinsames deterministisches Metric-Engine-Read-Model** und eine **sparsame persistente Annotationsebene**. Die beiden Alternativen werden im separaten Konsens-/Dissensdokument verglichen.

**Keine neue technische Freigabe; keine Veröffentlichung von Originalspielen/Secrets oder tatsächlichen Kostenabrechnungen.**
