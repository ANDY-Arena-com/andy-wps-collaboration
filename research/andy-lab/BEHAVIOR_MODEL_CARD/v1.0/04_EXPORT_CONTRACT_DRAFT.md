# 04 — ANDY Behavior Export Contract 1.0-draft

**Geltung:** künftiger **read-only APP-Exporter** → manuelle JSON-Datei → **validierter WordPress-Staging-Import**. Der Vertrag ist ausdrücklich ein **DRAFT**, noch kein vorhandener Importer, DB-Schema oder freigegebener CMS-Contract.

## 1. Grundarchitektur

```text
Original Match JSONL + Match JSON (unverändert)
              │
     vorhandene Identity/Evidence/Result-Resolver
              │
     Metric Registry + Regeln + Coverage
              │
       BEHAVIOR EXPORTER (read-only, determ.)
              │
    andy.behavior-card / 1.0-draft JSON-Snapshot
              │
       Schema-/Semantik-/Hash-Prüfung
              │
       WordPress STAGING (Review-Entwurf)
              │
        Journal Launch Control / Freigabe
              │
         Behavior Card / Journal / Social
```

**Nicht:** JSONL zu WordPress kopieren und dort willkürlich neu auswerten; neue SQL-„Wahrheit“ bauen; APP mit WordPress-Datenbank verbinden; öffentliche Card automatisch mit dem Export überschreiben.

## 2. Top-Level-Datenstruktur

| Feld | Typ / Pflicht | Semantik |
|---|---|---|
| `schema`, `schema_version` | string, Muss | maschinenlesbarer Contract; Schemaänderungen versionieren |
| `subject` | object, Muss | historisch belegte Modellbezeichnung, Provider, tatsächlich geloggte Modell-ID oder null |
| `snapshot` | object, Muss | eindeutige `snapshot_id`, Erzeugungszeit, Datenstand, Autor/Exporter, Parser-/Metricversion, Scope-Hash |
| `scope` | object, Muss | Filter, Ein-/Ausschlussregeln, `match_count`, `model_appearances`, Kohorten, Zeitfenster |
| `metrics` | object, Muss | Kennzahlen als Wert+Einheit+Zähler/Nenner+Coverage+Berechnung+Evidenzstatus, niemals nackte Zahl ohne Definition |
| `matches` | array, Muss | detaillierte *logische* Matchbezüge; Rollen, Bedingungen, Resultatstatus, Quellreferenzen |
| `conditions` | array, Muss | Ruleset/Engine/Provider/Strategie/Awareness/Budgets/Output-Cap/Retry/Datum je Match oder Gruppe |
| `interpretations` | array, Muss (leer erlaubt) | Bonoma/Sweet-Spot/SSA/Aftermatch ausschließlich eventreferenziert, versioniert, unabhängig reviewed |
| `provenance` | object, Muss | Primärhashes wo verfügbar, historische Sekundärbelege, Datenabdeckung und Ausschlussprotokoll |
| `publication` | object, Muss | `draft`, Editor-/Review-Status, DE/EN-Redaktion getrennt, öffentliche Linkfähigkeit, Freigabe |
| `links` | object, Muss | bestätigte Match-/Replay-/Journal-/Lab-URLs oder `null`, keine generierten ungetesteten Links |

**Wertobjekt** (kanonischer Entwurf): `{value,unit,numerator,denominator,coverage:{...},status,source_ids,metric_version}`. Unbekannt `value:null`, nicht 0; zusätzlich `missing_reason` bei Bedarf. Prozentwerte als Prozent 0–100 (nicht still 0–1). Zeiten intern Millisekunden oder Sekunden mit verpflichtender Einheit; keine Unit-Implizitheit.

## 3. Identity / Match-/Segmentvertrag

- `model_subject_id`: stabile interne Modellidentität, von tatsächlicher API-Version getrennt; historische Anzeigenamen dürfen nicht still zu konkreten Checkpoints umgedeutet werden.
- `match_id`, `root_match_id`, `segment_id`, `series_id`, `branch_type` (original/resume/refund/experimental), `parent_id`, `role` (white/black) pro beobachteter Modellrolle.
- **Self-play**: dasselbe Modell auf Weiß/Schwarz, zwei Rollen/Beobachtungsströme, aber genau **eine logische Partie**. Deduplizierung nach belegten Matchketten.
- **Resume** technische Segmente zu einer logischen Originalpartie zusammenführen; keine doppelte Usage. **Refund** als getrennte Experiment-/Fortsetzungsbranche kennzeichnen, für reguläre Card-Zählung nicht still hinzufügen.
- `match_start` und `match_end` ggf. historisch fehlend; Config aus passender JSON und Events mit Quellenstatus ergänzen, aber nie Defaults als dokumentierte historische Tatsachen ausgeben.
- `reasoning_tokens` / `cached_tokens` mit Kenntnis der konkreten Providersemantik; unbekannt/null ist nicht 0.
- `game_result` / `termination` aus Runner-JSON nicht als unabhängig engine-geprüft labeln.
- `rule_version` der ursprünglichen Partie maßgeblich; neue GO-SATURATION-v1.2-Entscheidung nicht rückwirkend an historische v1.1-Partien anlegen.

## 4. Exportvalidierung

Vor Export:
1. Modell-/Matcherkennung samt IDs und Rollen, eindeutiger Scope, Source-Hashes und Konflikte/Exklusionen.
2. Alle logischen Spiele deduplizieren; Konsistenz Decision/Executed/Token-Usage gegen Originalbericht und ggf. Resolver.
3. Fehlende Latenzen/Usage/Stammdaten **pro Modellrolle/Match** markieren, statt repräsentative Werte zu vervollständigen.
4. Metric Registry versionieren und passende Zeit-/Nennersemantik bei jeder berechneten Zahl speichern.
5. Keine Rohprompts, personenbezogenen Daten, Keys, Accounts, geheime Providerkonfiguration, proprietäre Antwortinhalte oder unbeabsichtigt geschützte Matchlogs in öffentlichem Export.
6. Snapshot/Manifest-Hash für Identifikation; unveränderliche archivierte Snapshotversion nach redaktioneller Freigabe.

Bei Import:
1. Schema-/Content-/Größenprüfung, JSON strict, erlaubte IDs/Feldtypen und numerische Plausibilität.
2. `snapshot_id`+Quellhash idempotent. **Gleiche ID + anderer Inhalt = Konflikt**, keine stillen Überschreibungen.
3. Redaktionsfelder getrennt von Datenfeldern. Vorher/Nachher-Diff, Revisionslog, Rollback und Veröffentlichungsgate.
4. Nicht auflösbare Event-/Storylinks bleiben leer/deaktiviert; kein falsches „Replay ansehen“.
5. Staging-only bis Review; Live nur über Journal-Freigabe und bestehendes Stage→Live-Verfahren.

## 5. Beispiel

[Maschinenlesbares Beispiel für Argon](examples/behavior_card_argon_v1_draft.json).

**Wichtig:** Die Beispielwerte stammen aus den **historischen S150-/S350-Analysezusammenfassungen**, nicht aus einem neu ausgeführten APP-Exporter oder einem erneuten Original-JSONL-Audit. Es ist **kein produktionsreifer Austauschdatensatz**. `source_kind=derived_historical_analysis`, fehlende Primärhashes und Teilabdeckung machen diese Grenze sichtbar.

## 6. API- und CMS-Entscheidungen, die noch offen sind

- Exaktes Feld-/Typ-Schema erst nach Reader-Audit des aktuellen Data-/Evidence-Resolvers finalisieren; keine alte UI-DB als neue Autorität installieren.
- Ob der WP-Importer eigenständiges Plugin, Modul des bestehenden Content Composer oder Bridge wird, erst nach Plugin-Ist-Audit klären. **Bestehende Pluginarchitektur vor neuen Plugins.**
- Welche Links `/match/<id>/event/<x>` tatsächlich unterstützen, erst am aktuellen Replay- und Journal-Routing verifizieren.
- Größe und öffentliche Freigabe der Quellbelege separat entscheiden (Hash+Meta ohne öffentliche RAW ist möglich).
- Bei echten Zusatzkosten durch Tarif- und Usage-Versionen Preisrevision separat, nicht unbemerkt als historisches Invoice-Faktum.

## 7. Änderungsprinzip

`schema_version` nur für veränderten Datenvertrag, `metrics_version` für definitorische Rechenänderungen, `snapshot_id` für eingefrorene konkrete Auswahl. Ein laufendes Profil zeigt *latest reviewed*; historischer Social-Beleg verweist immer auf einen eingefrorenen Snapshot.
