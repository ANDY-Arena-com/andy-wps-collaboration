# ANDY 2.0 – SYNC-05 / gemeinsamer Code und Drei-Instanzen-Betrieb

**V0.2 · 15.11.2026 · Betriebsprotokoll und Architekturfortschreibung**

**Status:** SYNC-05 lokal ausgerollt gemeldet; STUDIO und SANDBOX starten laut Projektleitung. FACTORY bleibt Zielarchitektur. Regressionsvergleich ohne neue beobachtete Fehler; absolute Testfreigabe nicht grün. Kein formaler gemeinsamer Git-Code-Release nachgewiesen.

Dieses Dokument ergänzt und aktualisiert den Ist-Stand von [Architektur V0.1](ANDY_FACTORY_THREE_INSTANCE_ARCHITECTURE_v0.1.md); die dort definierten Schutzprinzipien und der [Masterplan](ANDY_GESAMTKONZEPT_MASTERPLAN_v1.0.md) bleiben maßgeblich.

## 1. Architektur auf einen Blick

```text
               ANDY 2.0 / GEMEINSAMER CODE
               SYNC-05 · 252 manifestierte Dateien
                            |
          +-----------------+-----------------+
          |                 |                 |
    +-----v------+    +-----v------+    +-----v------+
    | 8080       |    | 8082       |    | 8083       |
    | STUDIO     |    | SANDBOX    |    | FACTORY    |
    | Gestaltung |    | Experiment |    | Produktion |
    | LAEUFT     |    | LAEUFT     |    | GEPLANT    |
    +-----+------+    +-----+------+    +-----+------+
          |                 |                 :
     lokale Tests      Forschungsruns      eigene Queue
     Designer          eigenes Archiv      eigenes Archiv
          |                 |                 :
          +--- nur lesen -->+                 :
                            |                 :
                            +.. Import .......+
                                geplant      :
                                              :
                  gepruefte Evidence-Exporte  :
                            |                 :
                            v                 v
                       ANDY LAB / RESEARCH CORPUS
                         Analyse, nicht Runner
```

Durchgezogene Linien: aktuelles Betriebsmodell bzw. bestätigte Startfähigkeit; gepunktete Linien: geplante Erweiterungen. Der gemeinsame Codebestand bezeichnet den auditierten Dateiumfang, nicht die Gleichheit aller lokalen Dateien, Git-Branches oder Daten. Exporte waren bereits vor SYNC-05 verfügbar; ihr vollständiger Betrieb nach dem Rollout wurde noch nicht separat bestätigt.

| Rolle | STUDIO | SANDBOX | FACTORY |
|---|---|---|---|
| Standard-Port | 8080 | 8082 | 8083 |
| Zweck | Arena, Designer, Academy, UI | API-/Runner-Experimente, Serien, Forschungsruns | stabile, reproduzierbare Forschungsproduktion |
| Code | gemeinsamer Kandidat | gemeinsamer Kandidat | später eingefrorener Release |
| Datenspeicher | lokale Test-Runs; Fremdarchiv nur lesen | eigene Runs, bisherige DB-Verknüpfungen | eigene Runs, DBs, Queue, Locks |
| Designer | Schreiben nur im explizit freigegebenen Branch | derzeit keine Schreibfreigabe | keine Designer-/Git-Schreibaktionen |
| Status | Start über VS Code bestätigt | Start gemeldet | noch nicht eingerichtet |

**Leitsatz:** 8080 gestaltet. 8082 experimentiert. 8083 produziert. ANDY Lab forscht.

## 2. Gemeinsamer Code ≠ gemeinsame Laufzeitdaten

- Ein gemeinsamer fachlicher Codepfad für Engine, Runner, Arena, Replay, Serien, Evidenzadapter und Ergebnisdarstellung. Kein neuer Engine-Fork und keine zweite Serien-Engine.
- Instanzrolle, stabile Instanz-ID und Port explizit setzen; Port und Ordnername allein verleihen keine Schreibrechte.
- Aktuell getrennte Arbeitsverzeichnisse und lokale Prozesse. Studio darf Forschungs-Runs und Replay-Archiv von Sandbox lesen; lokale Studio-Tests nicht automatisch in das Forschungsarchiv werten.
- Original-JSON/JSONL bleiben unverändert. SQLite V1/V2 sind abgeleitete Archivdaten. Keine Datenbank-, Run-, Secrets- oder Git-Branch-Synchronisierung durch Code-Rollout.
- Sandbox behält seine bestehenden DB-Verknüpfungen; Factory benötigt eigene physische Datenspeicher. Keine gemeinsame schreibbare SQLite-Datei über Hosts.
- Designer-Freigaben sind rollen- und branchgebunden. Studio: feature/ui-designer-1.0; Sandbox: integration/ui-lab-20261109 ohne freigegebenen Designer-Schreibbranch. Kein automatischer Branch-Wechsel.
- Derzeit lokaler Betrieb. Portable Versions-/Abhängigkeitsdefinition, Runtime-Root, Instanz-/Release-Provenienz und Multi-Host-Schutz sind weitere Aufgaben.

## 3. Entwicklungs- und Abnahmeprotokoll vom 15.11.

| Schritt | Befund / Entscheidung |
|---|---|
| SYNC-05A Audit V2 | 242 Pfade Studio, 201 Sandbox; 179 identisch, 17 abweichend, 46 nur Studio, 5 nur Sandbox. Beide Exporte enthielten je eine per Geheimnisheuristik ausgelassene Testdatei; aus früherem Paket hashidentisch rekonstruiert. |
| SYNC-05B Merge | gemeinsame Codebasis in isolierter Kopie; Arena/Broadcast/Designer aus Studio und Serien-/Live-/Archivfunktionen aus Sandbox gezielt konsolidiert |
| Designer-Schutz | explizite Entwicklungsrolle und freigegebener Branch; Factory darf nicht persistieren; 18 neue Schutztests bestanden |
| NO-RANDOM | Zufall als aktiv wählbares Modell bzw. impliziter Startdefault entfernt; historische Zufallsevidenz erhalten; 12 neue Tests bestanden |
| Smoke V3/V4 | Testinstanzen 8180/8182; zunächst fehlten historische Replay-Einträge, da DB nur Schema enthielt. Historische SQLite-Snapshots korrigierten die Testumgebung; Replay-Historie vom Nutzer sichtbar bestätigt. Keine produktive Datenmigration. |
| RESULT-DISPLAY-01 | KO/TKO und lesbare Endtypen statt technischer Rohcodes; 14 neue Tests bestanden; Darstellung von Projektleitung akzeptiert |
| Preflight | 252/252 Kandidatendateien hashgeprüft; 242/242 bzw. 201/201 auditierten Basisdateien bestätigt; bestehende Sandbox-Datenbankverknüpfungen erkannt |
| SYNC-05E.1 | Studio-Installation und erster Start gemeldet; erneuter Apply korrekt durch Basis-Hashprüfung abgewiesen. VS-Code-Start zunächst wegen fehlender Variablen gescheitert; explizite Rollen-Konfiguration ergänzt, Start danach bestätigt. |
| SYNC-05E.2 | Sandbox-Installer und separate Debug-Konfiguration bereitgestellt; Projektleitung meldet beide Instanzen laufend. |

### Letzter vollständiger Offline-Test am Mac

Quelle: lokal erzeugter Bericht SYNC05B_REPORT.json (im Dialog als SYNC05B_REPORT(4).json geteilt), Schema sync05b-local-test-v1, mode full; Preflight-Terminalausgabe. Bericht und private lokale Pfade werden nicht ins öffentliche Repo übernommen.

| Stand | Bestanden | Fehlgeschlagen | Übersprungen |
|---|---:|---:|---:|
| Studio (Basis) | 473 | 44 | 1 |
| Sandbox (Basis) | 283 | 0 | 1 |
| Gemeinsamer Kandidat | 546 | 44 | 1 |

- 0 Kandidatenfehler bei vorher bestandenen Tests; 44 mit identischem Basisstatus; 0 ohne passenden Vergleich.
- Zwei frühere Test-IDs durch erweiterte Rollen-Tests ersetzt. Der Bericht weist die alten IDs als fehlend aus; neue Rollenprüfungen bestehen.
- Alle 14 RESULT-DISPLAY-Tests, 18 Designer-Guard-Tests und 12 NO-RANDOM-Tests bestanden.
- `candidate_test_gate=false`, `release_approved=false`. Keine Umdeutung der 44 Fehler zu Erfolg. Betroffen u. a. Architekturprüfungen, Designer-/UI-Verträge, Node-Smoke und Runtime-Mocks. Einzelursachen noch nicht vollständig triagiert.
- Offline-Tests in temporären Kopien mit ausgewählten historischen Fixtures; Python-Socket-Guards, kein OS-Sandbox-Nachweis.
- Gestufter Rollout mit explizitem Schalter zur Annahme der bekannten 44 Testabweichungen vorgesehen. Backup/Rollback laut Entwicklungsprotokoll an isolierten Kopien geprüft. Vollständige lokale Installations-/Rollback-Logs wurden nicht übermittelt.

### Manifestierter Installationsumfang

| Maßnahme | Studio | Sandbox |
|---|---:|---:|
| Ersetzen | 24 | 23 |
| Hinzufügen | 10 | 51 |
| Unverändert | 218 | 178 |
| Löschen | 0 | 0 |

Kandidat: ANDY_SYNC05_RESULT_DISPLAY.zip. Lokale Hilfsmittel: PREPARE_SYNC05_RELEASE.py, INSTALL_SYNC05_STUDIO.py, INSTALL_SYNC05_SANDBOX.py. Diese Namen sind Referenzen auf bereitgestellte lokale Pakete, keine in diesem Doku-Repo nachgewiesenen Release-Assets. Kein automatischer Commit oder Push des Programmcodes. Abschließender gemeinsamer Post-Install-Hashreport der beiden Live-Arbeitsverzeichnisse und formale Release-ID/Tag fehlen noch. Die Nutzermeldung „beide laufen“ bestätigt Startfähigkeit, keine vollständige Browser-/API-/Archivabnahme.

## 4. Startvertrag und Betrieb

```text
STUDIO:  ANDY_ROLE=studio   ANDY_PORT=8080  ANDY_INSTANCE_ID=studio-8080
SANDBOX: ANDY_ROLE=sandbox  ANDY_PORT=8082  ANDY_INSTANCE_ID=sandbox-8082
FACTORY: ANDY_ROLE=factory  ANDY_PORT=8083  ANDY_INSTANCE_ID=<eindeutig>
```

Studio zusätzlich: ANDY_SERIES_ARCHIVE_READONLY (Sandbox-Runs), ANDY_ARCHIVE_DB_READONLY (Sandbox-Archivverzeichnis), ANDY_RESEARCH_ORIGIN (Sandbox-URL), ANDY_DESIGNER_BRANCH (freigegebener Designer-Branch). Pfade bewusst lokal konfiguriert. Sandbox verwendet das eigene Archiv. Factory-Konfiguration im nächsten Paket separat abnehmen.

VS Code: ANDY_app.py starten, cwd auf Instanzverzeichnis und die Variablen in der jeweiligen launch.json unter env setzen. Keine API-Keys in launch.json oder im Doku-Repo veröffentlichen. Starter mit expliziten Variablen verwenden; fehlende Rolle/ID führt absichtlich zum Startabbruch. Kein Neu-Apply des bereits installierten Pakets: bei Hashabweichungen zuerst Soll-/Ist-Vergleich, keine erzwungene Überschreibung.

Code-Änderung: Audit → gezielter Merge → Offline-Tests → Browser-Abnahme → sicherer Spielstopp → Backup → gestufte Installation → Post-Install-Hashprüfung → Start-/Funktionsprüfung → versionierter Release. Keine laufenden Matches für Update beenden. Keine unbeabsichtigten Provider-Aufrufe; keine automatische Aktualisierung der Factory.

## 5. Ergebnissemantik und offene Abnahme

KO (Schachmatt / Go-Kontrolle) und TKO sind sportliche Siege, sofern Verursacher und Gegner belegbar sind. Projektleitung hat ausdrücklich daran erinnert; ein nicht zuordenbarer historischer TKO bleibt ein Evidenzproblem, keine neue Spielregel. Die vorherige 8082-Übergabe führte Output-Limit/Illegal-Retry-Wertung noch als fachlich offen; diese Fälle systemweit unter dem nun vereinbarten Prinzip konsolidieren. Externe API-/Adapterfehler, Nutzerabbruch, allgemeines Aufruflimit oder fehlende Evidenz nicht pauschal als Sieg werten. RESULT-DISPLAY-01 hat **nur die Darstellung** vereinheitlicht, nicht das Ranking neu berechnet. RESULT-SEMANTICS-02 muss Runner, logische Resume-Ketten, Serien, Replay, Leaderboard und Lab aus einem gemeinsamen Ergebnisvertrag versorgen. Historische Daten nicht überschreiben, neue Wertungsprojektion mit Provenienz und Dublettenprüfung.

Restabnahme: 44 Altfehler einzeln untersuchen; produktive Hashgleichheit und Release-Manifest sichern; Offline-Testpartie samt Archivierung/Replay, Designer-Persistenz, Live/Reconnect, Serien-/Rematch-/Exportpfade abschließend prüfen. Kein bezahlter Live-Test ohne ausdrückliche Freigabe.

## 6. Nächste Arbeitspakete

| Reihenfolge | Paket | Abnahmeziel |
|---|---|---|
| 1 | RESULT-SEMANTICS-02 | zentrale KO/TKO-Zuordnung, keine Doppelwertung, historischer Dry-run |
| 2 | FACTORY-01 | 8083 unabhängig installiert, eigene Runtime, Daten und ID, manuelle Offline-Partie; kein Autoplay beim Start |
| 3 | ARCHIVE-IMPORT-01 | kontrollierter Import aus Studio/Sandbox; Originale unverändert, Hashes/Provenienz, idempotente Projektion |
| 4 | FACTORY-02 | persistente Match Queue; ein Worker, reservierte Job-/Match-ID; keine Doppelstarts |
| 5 | FACTORY-03 | explizites Autoplay, Stop nach aktueller Partie, Ressourcen-/Kostenlimits und Blockierregeln |
| 6 | FACTORY-04 | sicherer Wiederanlauf, Crash-/Reconnect-/Backup-Tests |
| 7 | DOMAIN / REASONING / CORRECTION / CACHE | kontrollierte Experimente, getrennte Profile, keine ungeprüften Factory-Updates |

Stabilisierung und offene Release-Gates begleiten diese Reihenfolge; FACTORY bleibt bis zur Freigabe ein isolierter Pilot. Export- und Importvertrag gemäß [Match-Evidenz](ANDY_MATCH_EVIDENCE_JSONL_JSON_SQLITE_v1.0.md) und [Research Pipeline](ANDY_SERIES_RESEARCH_PIPELINE_SPEC_v0.1.md). Lab bleibt Auswertungsebene, Website bleibt Präsentationsebene.

## 7. Protokollregel für künftige Änderungen

Je Paket dokumentieren: Datum, Ziel, betroffene Rolle/Instanz, Basis-/Ziel-Release und Hashes, geänderte Funktionen/Dateien, Tests inkl. Fehlschläge, echte Nutzerabnahme, Daten-/Kostenwirkungen, offene Risiken und Rückfallversion. Unterscheidung: geplant / implementiert / isoliert getestet / lokal installiert / im Betrieb bestätigt / vollständig freigegeben. Keine private Konfiguration oder unveröffentlichte Forschungs-Rohdaten in diesem öffentlichen Repository.

**Dieser Commit dokumentiert den Stand; er verändert keine laufende App, keinen Programmcode, keine Datenbank und keine Spielwertung.**
