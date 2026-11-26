# ANDY Signature — FOUNDATION 1.0 RC1

Stand: 26.11.2026 | Instanz 8082 | Status: Release Candidate, lokal bestätigter Foundation Gate01; kein finaler Release.

## Ausgangspunkt und bestätigter Datenbestand
Nach CLEAN-FINAL01–07A: 107 Partien, 214 Spielerzuordnungen, 7.951 Events, 107 legacy_match_details, 7.951 legacy_event_details und 7.951 replay_payloads. SQLite kompaktiert (41.562.112 → 34.988.032 Bytes); 11 direkte Laufzeitabhängigkeiten plus pytest separat. Historische Dateien extern archiviert, Teststruktur teilweise konsolidiert. Forschungsdaten und Designer bei den finalen Testpatches unverändert.

## Abnahme FOUNDATION GATE01
Der Nutzer bestätigte auf seinem Mac 7/7 Prüfgruppen:
- Local core integrity and unchanged bytes
- Role, port and Factory designer policy
- Foreign archive overrides and Studio write denial
- Run directory and lifecycle alias denial
- Core symlink and hardlink denial
- Read-only SQL and atomic rollback of projections
- Resume chain eligibility and explicit limit extension

Prüflauf ANDY_FOUNDATION_GATE01.py, ohne --apply. Keine kostenpflichtigen API-Aufrufe. Der Befund bezieht sich auf den lokalen Signature-Stand, nicht auf einen bereits veröffentlichten oder verifizierten Software-Commit.

## Restschuld und Freigabegrenzen
Letzter vollständiger Regressionstest vor FINAL07A: 568 bestanden, 15 fehlgeschlagen, 44 Subtests bestanden. FINAL07A lokal installiert, danach kein vollständiger Testbefund. Historische Designer-Verträge und JS-Mocks bleiben sichtbar; keine pauschale Deaktivierung. Architektur-Inventar meldet u.a. Application-Adapter mit Presentation-Imports (andy_recovery_index → andy_match_picker und andy_model_display) sowie Domain- und Infrastructure-Abhängigkeiten; differenziert prüfen, nicht pauschal als Architekturverletzung klassifizieren. Gate01 deckt weder tatsächlichen UI-Dispatch noch Live Resume/Refund, vollständige Regression, portable Neuinstallation oder tatsächliche 8083-Laufzeit ab. Sicherheitsrelevante offene Serien-/Instanzprüfungen vor produktiver Factory-Freigabe klären. RC1 bedeutet keine vollständige Produktfreigabe.

## Operative Entscheidung
Historische Sonderfälle und Testkosmetik dürfen den Forschungsfortschritt nicht dauerhaft blockieren. Evidenz bewahren, Unsicherheit sichtbar halten, keine künstlich grünen Tests. Kritische Schutzfunktionen bleiben verbindliche Freigabekriterien.

## Zielarchitektur
Siehe [Three Instance Architecture](ANDY_FACTORY_THREE_INSTANCE_ARCHITECTURE_v0.1.md).
- 8080 Studio: Design/UI; unabhängig, vorerst unverändert.
- 8082 Signature: Konsolidierung, Forschung und Analyse.
- 8083 Factory: Produktion von Partien und Evidenz; vorerst unverändert.
- Gemeinsamer versionierter Softwarekern, getrennte lokale Runtime-Datenbanken, keine gemeinsam beschreibbare SQLite-Datei und keine blinde Synchronisation.

## Priorisierte Roadmap
1. FOUNDATION RC1: lokalen Quellstand und Release-Manifest sichern; tatsächlicher Git-Tag/Quellcommit noch nicht erstellt bzw. verifiziert.
2. SYNC-06A: zunächst nur 8082; versionierter Transfervertrag, Export/Import, Integritätsprüfung, Identitätsprüfung, Dublettenschutz, atomare Übernahme und Wiederholbarkeit. Testspiele ausschließen; Originale und Provenienz erhalten. Keine API-Kosten.
3. SYNC-06B: tatsächliche 8083-Installation inspizieren, isolierte Factory-Anbindung validieren, erst dann kontrollierten Transfer freigeben.
4. g-Signature Engine: K4, vier Knoten/sechs Kanten, versionierte Kennzahlen und nachvollziehbare Kohorten; unbekannt ist nicht null.
5. Behavior Model Cards; danach perspektivisch Adaptive Pre-Match Signature.

Modellidentität: Provider + exakte API-Modell-ID, angeforderte und gemeldete IDs separat, siehe [Issue #16](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/16). Keine kostenpflichtigen API-Tests ohne explizite Nutzeraktion.

## Status
CLEAN-Phase operativ abgeschlossen, Restschuld offen. Gate01 lokal bestätigt. SYNC-06 und g-Signature noch nicht implementiert. Dieses Dokument protokolliert den Stand und die Entwicklungsentscheidung; es ersetzt weder einen Software-Release noch einen vollständigen Abnahmebericht.
