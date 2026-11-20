# ANDY Arena – Hybrid Start UI v0.1

20.11.2026 · Beschluss der Projektleitung: Hybridlösung als erster Umsetzungsschritt; nur bereits aktivierte Cases. Konzept freigegeben, technische Umsetzung und Abnahme offen. DATA CONSISTENCY (#12) bleibt Priorität 1; keine Vermischung mit Accounting (#11).

## Ausgangslage und Abwägung
8082-Screenshot: Sidebar mit KI vs. KI, Partien nachspielen, Leaderboard; Lab/Research mit Serien und ANDY Lab. Header-Controls wechseln je Modus. Mensch vs. KI ist vorgesehen, noch nicht Teil des initialen Umfangs.
- Direkte Sidebar-Modi: schnell und sichtbar, aber wachsender Platzbedarf und Vermischung von Produktnavigation und Aktivität.
- Rein zentraler Start: ein Einstieg, gut erweiterbar, aber zusätzlicher Klick und geringere Sichtbarkeit häufiger Funktionen.
- Beschlossene Hybridlösung: zentraler Start plus sichtbarer aktueller Modus und kontextbezogene Schnell-/Direkteinstiege. Mehr Zustandslogik und potenziell redundante Einstiegspunkte; deshalb gemeinsame Actions statt mehrfacher Implementierung.

## UI-Prinzip
Sidebar = WO bin ich? Start = WAS möchte ich tun? Toolbar = WIE steuere ich es?
- Sidebar: Arena als gemeinsamer Spielbereich, Leaderboard, Serien und ANDY Lab weiterhin erreichbar; Design und Sprache erhalten.
- Header: zentraler Start-Button, aktueller Modus sichtbar, bestehende modusspezifische Controls. Schnellzugriff auf neue KI-Partie und Replay; konkrete Platzierung und Beschriftung im Clickdummy/Browser prüfen.
- Startmodal: Auswahl KI vs. KI oder Replay, danach bestehende Konfiguration bzw. Partienauswahl öffnen. Keine doppelte Implementierung bestehender Dialoge. Abbruch verändert nichts. Direkteinstieg aus Profil/Lab/Serien in Replay umgeht die Modusauswahl.
- Serienübersicht bleibt eigenständig; vorhandene Serienstarts bleiben erreichbar, zunächst kein neuer eigenständiger Startmodus ohne Ist-Prüfung.
- Mensch vs. KI, Mensch vs. Mensch, Academy, Turniere und Experimentmodus sind Erweiterungsoptionen, nicht Teil dieses Releases. Keine neuen inaktiven Platzhalter erforderlich.
- Lab Dashboard/Explorer/Builder bleiben Produktziel, nicht Teil dieses UI-Pakets.

## Technischer Vertrag / Prüfbedarf
Aktiver Spielprozess, sichtbare Ansicht und ausgewählter Modus getrennt verwalten. Navigation und Öffnen/Abbrechen des Modals dürfen keine Partie stoppen, zurücksetzen, überschreiben oder einen neuen Provider-Call auslösen. Bei laufendem Spiel keine stillschweigende Ersetzung; bestehende sichere Stop-/Bestätigungsmechanismen erhalten. Rückkehr zur laufenden Partie muss möglich bleiben. Toolbar folgt dem tatsächlich dargestellten Aktivitätskontext, ohne einen aktiven Hintergrundprozess zu verschleiern. Bestehende Reader, Replays, Serien, Themes, Sprachwechsel und Rollenprofile erhalten. Routing/State-Management und reale Controls zuerst anhand des installierten Codes prüfen. Kein Full-Sync und keine Änderung an Ruleset, Budget, Awareness, Originaldaten oder Fight Nights.

## Abnahme
- Beide aktivierten Modi über Start erreichbar; richtige bestehende Konfiguration/Replay-Auswahl und Toolbar.
- Schnellzugriffe und direkte Replay-Einstiege funktionieren ohne redundantes Modal.
- Abbrechen des Startdialogs lässt Zustand unverändert.
- Während laufender KI-Partie Ansichtswechsel und Rückkehr ohne Abbruch oder zusätzliche Calls durch Navigation.
- Kein unbeabsichtigter Neustart oder Überschreiben beim Moduswechsel; explizite Bestätigung bei Konflikt.
- Bestehende Serien-, Leaderboard-, Lab-, Theme- und Sprachfunktionen ohne Regression.
- Offline-Tests, Backup/Rollback vor Eingriff, lokale Browser-Abnahme auf betroffener Instanz; keine kostenpflichtigen Testaufrufe ohne Freigabe.

Status: Konzeptentscheidung dokumentiert; konkrete UI-Details und technische Machbarkeit TBD. Kein Code geändert. Umsetzung separat von #12 nach abgestimmter Reihenfolge.
