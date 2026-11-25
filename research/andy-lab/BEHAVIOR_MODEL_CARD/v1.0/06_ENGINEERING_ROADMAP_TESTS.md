# 06 — Implementation Plan, Regression und Abnahme

**Status 25.11.2026:** Requirements/Datenvertrag dokumentiert. Ein älterer HTML-Clickdummy ist lokal/Chat verfügbar und wurde visuell getestet; **kein neuer APP-Exporter, kein WordPress-Behavior-Plugin, keine neue DB, keine öffentlichen Inhalte oder Produktivschaltungen** in diesem Arbeitsstrang.

## Phase 0 – Ist-Audit & Verträge vor Code

- Read-only Reader-/Resolver-/Metric-/Archiv-Audit der aktiven 8080/8082-Stände und vorhandenen JSONL+JSON-Feldtypen; Studio/Factory-Rollen beachten.
- Tatsächlichen Ablauf `decision`→Ausführung, Latenz `latency_ms` und Provider-Usage semantisch gegen Beispieloriginale prüfen. Original `chess_fen` im Decision-Event kann den Zustand **vor** der Aktion repräsentieren.
- Match-Identity-/Resume-/Refund-/Self-play-Regeln mit bestehenden Lab-/Leaderboard-Projektionen und Exklusionsliste abstimmen; keine Altfall-100%-Pflicht, Problemfälle offen ausschließen.
- Festlegen, wie `reasoning_tokens`, `output_tokens`, Cache, Preise und API-Laufzeit bei verschiedenen Providern tatsächlich geloggt sind. Null != 0.
- Aktuelle WP-Composer-/Editor-/Sprach-/Content-ID-/Launch-/Staging-Verträge lesen; minimalen Integrationspunkt bestimmen, nicht reflexhaft neuen Plugin-Baum aufbauen.
- `04_EXPORT_CONTRACT_DRAFT.md` anhand echter verfügbarer Feldnamen reviewen; Exportformat erst dann als `1.0` einfrieren.

## Phase 1 – V1 Exporter (manuell)

- Read-only Kommando/APP-Aktion „Behavior Card exportieren“, Modell/Matchselektion, Filter, JSON erzeugen und lokal speichern; **keine Provider-/Engine-Aufrufe**.
- Reuse bestehender Evidence-/Metric-Leseschicht, keine neue divergierende Source-of-Truth-Datenbank.
- Modellname/ID/Rolle, logische Partien, Zähler, Token, Latenzen, Coverage, Bedingungen, Quell-/Metrikversionen in deterministischer Reihenfolge.
- Getrennter Public-Subset-Export ohne unsichere Rohtexte; Originalhashes/Quellen bei fehlendem Freigaberecht ggf. nur als privates Manifest.
- Validationsreport mit PASS/WARN/STOP, ausgeschlossenen Fällen, Konflikten, missing data, total covered games/calls.
- Minimaler Testkorpus: 1 reguläres vollständiges Match, 1 partial-framed, 1 Self-play, 1 Resume-Kette, 1 Refund-Research-Branch, 1 fehlende Timing-/Reasoning-Usage.
- Ein freigegebener exportierter Snapshot einfrieren; Originalquellen bytegleich.

## Phase 2 – Reader/UI/WP-Staging

- Bestehende offline HTML-V1 als UI-Referenz, nicht als Importer oder visuelle Livegarantie.
- Validierter *manueller* WP-JSON-Import unter Adminrechten, Schema-/Versionscheck und Quell-/Snapshot-Identitätsprüfung.
- Import Preview mit Ersetzungen, Datenabdeckung und Linkstatus; keine WP-Post-Massenänderung; Änderungen granular.
- Gemeinsame Fakten für DE/EN, getrennte redaktionelle Texte, stabile Modell-/Match-Relations, Quellenakkordeon.
- Navigation Card↔Match Story↔Replay nur nach URL-Funktionsprüfung; Social OG/Preview nur aus freigegebenem Snapshot.
- Import idempotent, Revisionsprotokoll/Rollback; Staging-Freigabe vor Live, Launch Control bestehend.
- Visuelle Abnahme: Desktop, Mobile 320/375/390/430/720/1024, Keyboard, nicht verfügbare Diagramme, fehlende Links, DE/EN.

## Phase 3 – Ausbau, erst nach V1-Abnahme

- Optionale Phasen-/Zeitverlauf-Views, quantilbasierte Response-Speed; keine geschätzten Zeiten aus wall time.
- Evidenzbasierte Stabilitätsansicht **nur** mit definierter vergleichbarer Kohorte und Messmethode.
- Manuelle interpretative Bonoma/Sweet-Spot/SSA-Overlays, Review-Dissens, Gegenbelege; keine Auto-Label-Pflicht.
- Optionales Aftermatch (neue, separat nachgewiesene Modelläußerungen) und Social-Assets aus Snapshot.
- Kontrollierter Snapshot-Update/Sync nur bei explizitem Folgeentscheid, kein laufender API-/WordPress-Live-Kanal als Default.

## Test- und Abnahmematrix

| Test-ID | Fall | Erwartung |
| --- | --- | --- |
| BMC-T01 | 5 Argon-Piloten aus S150/S350 | 5 logische Matches, 486 Entscheidungen, 458 Ausführungen aus den **dokumentierten Sekundärquellen** reproduzierbar; Roh-Audit separat |
| BMC-T02 | Self-play gleicher Modellname in Weiß/Schwarz | 1 logische Partie, 2 Rollen, Call-/Action-Summe aller Rollen ohne doppelte Matchzählung |
| BMC-T03 | S150 R0 / überlappendes Segment | dedupliziert, historische Warnung sichtbar |
| BMC-T04 | reguläre Resume-Kette | eine logische Partie, Segmentusage ohne Doppelzählung |
| BMC-T05 | Refund nach Ressourcen-TKO | Forschungsbranch getrennt von ursprünglicher sportlicher Partie |
| BMC-T06 | Fehlende JSONL-Start-/Endevents, ergänzender Matchbericht | partielle Rahmenstatus, keine geratenen Engine-/Rulesetfelder |
| BMC-T07 | `decision` mit `executed=false` | nicht pauschal „illegal“; Endgrund/Klasse korrekt |
| BMC-T08 | Own-API-Latency nur in 1/5 Spielen | einzig dieser zeitabgedeckte Teil mit Aktionen/h; keine 5-Spiel-Tempozahl |
| BMC-T09 | fehlende, negative, 0, NaN Timingfelder | Warn/Exclude, nicht als Nullzeit/Übergeschwindigkeit |
| BMC-T10 | Input=0 oder fehlende Usage | Output/Input `null` oder nicht berechenbar, nie Infinity |
| BMC-T11 | `reasoning_tokens=null` | als nicht gemeldet, nicht als 0 Thinking |
| BMC-T12 | Reasoning in Output enthalten | keine Summation als doppelte Tokens |
| BMC-T13 | unterschiedliche Rulesets | Originalstand bleibt, keine rückwirkende v1.2-TKO-Neuwertung |
| BMC-T14 | Runner-Outcome vs. Engine-Verifikation | verschiedene Evidenzfelder, Konflikt sichtbar |
| BMC-T15 | importierter Snapshot identisch | idempotent; kein doppelter WP-Beitrag |
| BMC-T16 | Snapshot-ID gleich, Payload verändert | STOP-Konflikt mit Revision nötig |
| BMC-T17 | Feld/Schlüssel mit URL/HTML/Script / fremden Links | Sanitizer, erlaubte Domains, kein XSS oder ungetesteter Deep-Link |
| BMC-T18 | fehlender Match-/Event-Link | kein funktionsloser Button oder erfundener URL |
| BMC-T19 | öffentliche Ausgabe / privater Rohdatensatz | Source-Metadaten ohne Keys, rohe privaten Inhalte nicht leaken |
| BMC-T20 | alte/neue DE-/EN-Sprachpartner | gemeinsame Kennzahlen, unabhängiger Text, kein kaputter Sprachwechsel |
| BMC-T21 | alter WP-Live-Stand + neues Staging | keine automatische Code-/DB-/Content-Übertragung |
| BMC-T22 | Social-Preset | Fakt, Nenner, Datum, Quellen-Snapshot identisch; Redaktionsfreigabe nötig |
| BMC-T23 | Modellvergleich/„#1“-Konfiguration im UI | abgelehnt: kein Vergleich, keine Rankings |
| BMC-T24 | Bonoma/Sweet-Spot ohne Eventbeleg | nicht veröffentlicht als verifiziert; `not_evaluated` oder Interpretationshinweis |
| BMC-T25 | sehr wenige Spiele / hohe Zeit-/Kostenlast | transparent als Coverage/Aufwand statt negatives Modellurteil |

## Sicherheit, Regression, Arbeitsteilung

**APP:** Codesync/Port-Rollen getrennt, 8082 zunächst ohne Eingriff in laufende Arena, 8080 erst eigener freigegebener Regression-Gate, 8083 protected. Kein Schreibzugriff auf Original-JSONL/JSON oder produktive Resultate, Backup/Dry-run/Rollback bei späterem Code-Release.

**WP:** echte Staging-Instanz, separates Launch-Gate, kein Hostinger „Gesamt-Publish“, keine ungeprüfte neue Plugin-Abhängigkeit, keine Duplikatdatenbank, vorhandene Journey Home/Gabelseite/Content und DE/EN erhalten.

**Editorial:** Story-/Social-Fakten erst durch Checker, dann Review; Demo-Inhalte als DEMO markiert; keine Aussagen über Modelleigenschaften jenseits der dokumentierten Spielbedingungen.

**Research:** interpretative Verfahren, Versionen und Gegenbelege; keine Kausalität aus zeitlicher Folge, keine Gleichsetzung von Modellurteil und Engine-Validierung.

## Definition: Was ist heute erledigt?

**Erledigt:** Konsolidierung der Anforderungen und Konzeption, existierender HTML-Clickdummy V1 aus früherem Chat, zwei archivierte Analysequellen und Pilotberechnung.  
**Offen:** APP-Ist-Audit, ein echter exportierter JSON-Datensatz, GitHub-Ablage des vollständigen Clickdummy-HTML, WP-Importprototyp, öffentliche Seite, Live-/Browser-QA, verbindlicher Schema-/Metric-Freeze.
