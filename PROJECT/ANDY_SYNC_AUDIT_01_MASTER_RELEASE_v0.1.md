 # SYNC-AUDIT-01 / Neutraler Master-Release V0.1

15.11.2026 · Prozessänderung durch Projektleitung freigegeben; isoliertes Audit-Werkzeug entwickelt, lokaler Audit und vollständige Release-Implementierung offen.

## Anlass
[BUG #4](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/4): Historische Daten auf Studio 8080 fehlen, Replay funktioniert. Ursache unbekannt, kein nachgewiesener Datenverlust. SYNC-05-Bericht: Studio 252/252, Sandbox 178/252 identisch, 23 abweichend, 51 fehlend zum damaligen Prüfzeitpunkt; 44 bekannte Altfehler. Startfähigkeit ersetzt keine Funktionsabnahme. Quelle: [Betriebsmodell V0.2](ANDY_SYNC05_RELEASE_AND_OPERATING_MODEL_v0.2.md).

## Neuer verbindlicher Prozess
1. Lesender Ist-Audit beider Instanzen: Code/Assets, Abhängigkeiten, deklarierte und tatsächliche Startkonfiguration, Archivauflösung und Berechtigungen; keine laufende Partie unterbrechen.
2. Gezielte Konsolidierung ausschließlich in neutraler Integrationskopie. Kein direktes gegenseitiges Patchen der produktiven Instanzen; keine neue Engine. Unterschiede der Rollen explizit festlegen, nicht wegfiltern.
3. Versionierter Release mit vollständigem Soll-Manifest, gepinnten Abhängigkeiten, Commit/Tag, isoliertem Installations- und Rollbackverfahren. Originaldaten, DBs, Checkpoints, Locks, Queue, API-Secrets und lokale Konfiguration bleiben getrennt. Keine automatische Übernahme von Daten oder Rankings.
4. Offline-Testmatrix: identische historische Fixtures, Replay, Serien/Rematch, Leaderboard, Export, Designer-Rechtegrenzen; STOP-02 (P0), GO-SATURATION-01 v1.2, RESULT-SEMANTICS-02B. Alle fehlgeschlagenen Tests triagieren, keine grüne Gesamtfreigabe bei 44 offenen Altfehlern. Abweichungen und Nachweise dokumentieren.
5. Gestufte Installation aus dem neutralen Kandidaten nach sicherem Matchende, Backup, Vor-/Nach-Hashprüfung, Browser- und Funktionsabnahme 8080 und 8082. Factory ausschließlich aus explizit freigegebenem Release, mit eigener Runtime und Daten. Kein Autoplay ohne Kostenfreigabe.

## Tatsächlich gelieferter erster Baustein
Lokales Paket ANDY_SYNC_AUDIT_01.zip, SHA-256 `61b9224ff7d2454efb6bb90ed980d83eb32e03c3254c2b7f534ee09c5c4dc8b0`, ZIP-CRC geprüft; kein GitHub-Release-Asset. AUDIT_SYNC01.py vergleicht heuristisch ausgewählte Code-/Assetpfade (nicht identisch mit den 252 historischen Manifestpfaden), deklarierte VS-Code-Rollen/Ports und Archiv-Metadaten, ohne Originalinhalte/SQLite zu lesen. Ausgabe außerhalb der App-Verzeichnisse. Keine API-Aufrufe, keine App-Imports, keine Installation. Runtime-Inventar betrifft nur den Auditor-Interpreter; keine Live-Prozessprüfung. Report privat halten. Nicht atomare Momentaufnahme.

RELEASE_GATE.py erzeugt ein Kandidateninventar und eine an Audit- und Manifesthash gebundene Abnahmevorlage. Fehlende Nachweise, Pfaddrift und unbestätigte Archivzuordnung blockieren. 15 manuelle Prüfpunkte; Referenzen werden nicht unabhängig validiert. Selbst bei bestandenem Gate nur READY_FOR_HUMAN_REVIEW, keine automatische Freigabe oder Installation. Vollständiges autoritatives Release-Manifest, echte Funktionsregression und installerbasierter Rollback fehlen noch.

**18/18 synthetische Offline-Tests** bestanden; echte App-Quellen fehlen in diesem Thread. Keine Änderung an 8080/8082 oder Originaldaten. Nächster Schritt: lokalen Auditbericht und aktuelle Quellpakete erhalten, BUG #4 und STOP-02 am tatsächlichen Code untersuchen. [Ruleset v1.2](ANDY_GO_SATURATION_01_RULESET_V1.2.md) und [Ergebnis-Audit](ANDY_RESULT_SEMANTICS_02A_AUDIT_v0.1.md) berücksichtigen. Keine retrospektive Wertungsmutation.
