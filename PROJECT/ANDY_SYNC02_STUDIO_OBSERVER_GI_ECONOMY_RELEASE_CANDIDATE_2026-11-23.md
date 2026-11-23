# ANDY SYNC02 — Studio 8080 Observer/GI/Economy: gezielter Release-Kandidat

**Datum:** 23.11.2026. **Status:** Source-Vergleich und lokaler Offline-Sync-Kandidat abgeschlossen; **kein Mac-Apply, kein Git-Code-Commit, keine echte Studio-8080-Browser-Abnahme**. Studio 8080/Integration 8082/Factory 8083 auf den Macs werden durch dieses Dokument nicht geändert.

## Auswertung des vom Nutzer exportierten `ANDY_SYNC_SCOPE01_CODE_ONLY.zip`

- **43/43** Dateien aus `MANIFEST_SOURCE_ONLY.json` stimmen mit ihren SHA-256- und Größenangaben überein.
- Der Quellvergleich ergibt **9** abweichende gemeinsame Python-Dateien, **9** Sandbox-only-Pfade und **4** Studio-only-Dateien im breiten Audit. Der gezielte Code-Export enthält 43 Dateien einschließlich relevanter Kontrollpfade.
- Die Abweichungen im eigentlichen Source-Merge sind klein: Arena (~9 neue/geänderte Zeilen), Replay (~13), LLM Bridge (~27), Broadcast (3), Observer-Pulse erweitert um GI/Economy-Modi, Shell alter GI-Modal-Einstieg vs. gemeinsamer Observer.
- **Unverändert lassen**: Studio `andy_ui_release.py` und die Studio-Versionen von `andy_lab_v02_preview.py`, `andy_stats_original.py`. Die Sandbox hat hier absichtlich andere Rollen-/Designer-Gates.
- **Unverändert lassen:** Studio-Launcher-Gate `(sandbox:8082 OR studio:8080)` in `andy_v1_shell.py`, bereits browserseitig als gezielter Studio-Fix bestätigt.
- **Nicht löschen:** v01-GI-Pilotdateien, Studio-only ZYKLIOPEN-Tests/Reports und Sandbox-only `andy_app_subq.py`/`semantic_pilot.py`; separate Tech-Debt-Kandidaten, kein Bestandteil des Funktionssyncs.
- **Quellcode-Integrationsumfang:** 6 `MODIFY` + 7 `ADD`, ausschließlich im Studio-Codebaum; 8082-Quellen und Factory 8083 unberührt.
- **Wichtige neu erkannte Instanzabhängigkeit:** Die 8082-Tarif-DB im Provider-Tarifmodul ist fest auf `~/Library/Application Support/ANDY/8082/economy_tariffs.sqlite3` konfiguriert. Der **Studio-Kandidat verwendet stattdessen /ANDY/8080/economy_tariffs.sqlite3**; keine DB-Kopie und kein gemeinsamer Writer. Studio-Kostenwerte können zunächst offen sein, solange seine eigenen November-Tarifkarten nicht separat übertragen wurden.

## Reversible Installation auf dem Mac

Chat-Anhang `ANDY_SYNC02_STUDIO_OBSERVER_GI_ECONOMY.zip`; Paket enthält 13 Code-Dateien im Payload, `MANIFEST.json`, `INSTALL_ANDY_SYNC02_STUDIO.py`, `README_ANDY_SYNC02_STUDIO.md`.

- **Default Dry Run:** genaues Branch-/Rollen-/File-Hash-/Asset-/geschützte Studio-Code-Vertrag und Python-AST. Bei Drift `BLOCKED` ohne Schreiben.
- **Apply nur gestopptes 8080:** Port-8080-Check, atomare Dateioperationen, vorheriges Source-Backup nur in Downloads und exakter Rollback-Pfad; keine Git-Aktionen, keine anderen Instanzen, keine Originalspiel-/DB-/Designer-Approval-Mutation.
- **Rollback:** nur wenn keine neueren Änderungen in den verwalteten Dateien entstanden sind.

### Offline-Abnahme

- Python AST und Payload-SHA-Prüfung aller 13 Zieldateien.
- Dry Run; Hash-Drift stoppt; geschützter Studio-Designer-Stand stoppt; isolierter Apply; Idempotenz; Rollback-Drift-Gate; vollständiger Rollback — **PASS**.
- Dynamisch generiertes Observer-JavaScript und beide iframe-Skripte per Node-Syntax — **PASS**.
- Isolierter Chromium-Smoke mit dem generierten Observer-Host: ein Observer, drei iframe-Ansichten, Pattern/GI/Economy-Wechsel und keine JS-Laufzeitfehler — **PASS**.
- **Nicht abgenommen:** echter 8080-Live-Match/Replay/Designer-Apply am Mac, verschiedene Provider, Studio-Tarifstand, Studio-Git-Code-Commit und Gesamtregression.

## Browser-Abnahmeliste vor Git-Codefreigabe

1. Aktivitäts-Launcher im **Studio 8080** funktioniert weiterhin; keine alte V01-GI-Header-/Sidebar-Doppelbedienung.
2. Arena + Replay nutzen den **einen** verschiebbaren Observer mit drei Modi; GI auf explizites `Bewerten` bei X; unabhängige Player-/Observer-Modelle.
3. Economy ohne eigenen LLM-Call, Input/Output/Reasoning/Cache/USD/EUR, lokale Studio-Tarifkarten getrennt von 8082.
4. Designer Test → Preview → Apply → Reload/Persistenz; Studio-Role-Gate für Living Lab/Daten erhalten.
5. Browser- und Code-Gates für 8080/8082 getrennt; Archive/Refund/Resume/KO/TKO und Factory nicht verändern.

**Folgearbeit:** Nach erfolgreicher Studio-Abnahme gesondert Tariffkarten-Replizierung prüfen, Release-Stand per explizit freigegebenen Codepfaden in Git sichern. **Cleanup erst danach** laut [Tech-Debt Issue #14](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/14).

Bezüge: [TECH-DEBT-AUDIT01](ANDY_TECH_DEBT_AUDIT01_FINDINGS_SYNC_GATE_2026-11-23.md) · [SYNC-FEATURE-GATE-01](ANDY_SYNC_FEATURE_GATE_CASE_2026-11-21.md) · [Regressionsvertrag](ANDY_DEVELOPMENT_REGRESSION_POLICY_2026-11-21.md).
