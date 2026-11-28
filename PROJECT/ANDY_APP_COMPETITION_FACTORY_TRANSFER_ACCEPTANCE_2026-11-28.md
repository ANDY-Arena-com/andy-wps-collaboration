# ANDY – Competition Factory / Transfer-Abnahme
Stand 28.11.2026. Verbindlicher offener Abnahmepunkt für Threadwechsel.

## Ausgangslage
Der Nutzer hat eine Kopie des aktuellen lokalen Studio-Ordners angelegt und lässt dort längere echte Matches laufen, während die Observer-Entwicklung auf dem führenden Studio 8080 fortgesetzt wird. Die Kopie läuft ohne den neuen Observer-Ausbau (genauer Patchstand, Pfad, Port und Match-IDs noch nicht bestätigt). Sie ist eine temporäre Factory, kein zweiter Entwicklungszweig. Voraussetzung für explizite Competition-Intent-Evidenz: MATCH-AGENDA-02 in der Kopie und entsprechend gestartete Competition Matches. Nicht allein aus der Spieldauer auf Intent schließen.

## Betriebsprinzip
One Master. Multiple Factories. Shared Research. Studio bleibt führender Codebestand. Keine parallelen Codepatches in der Factory, kein Rückkopieren von Code, Registry oder vollständiger DB. Nur neue Match-Evidenz über den vorhandenen Data Transfer übernehmen. Export unabhängig vom Ziel; Import dedupliziert anhand Match-ID. Originale und abgeschlossene Factory-Aufzeichnungen erhalten. Vor Import reguläre Sicherheitsbedingungen (insbesondere keine weiteren aktiven Studio-Runtime-Prozesse und gesicherte DB) einhalten. Keine erneute historische Sync-Reparatur.

## Gezielter Abnahmetest nach Abschluss der Factory-Partien
1. In der Factory eine Stichprobe abgeschlossener Matches mit IDs, tatsächlichem Match Intent (soweit protokolliert), Abschlussgrund, Sieger bzw. Nichtwertung und vorhandenen JSON/JSONL-Belegen dokumentieren. Mindestens ein sportlich gültiges Competition-Ergebnis anstreben; technische Abbrüche separat.
2. Vor Import Studio-Bestand und relevante Actor-Qualifikationsstände dokumentieren. Reguläres Transfer-ZIP erzeugen; Vorschau auf 8080 prüfen (bekannt/neu/skip). Nur neue IDs übernehmen. Keine künstlichen match_end-Ereignisse.
3. Nach Import Original-Evidenz, Match-ID, Intent, Abschlussgrund und vorhandene Provider-/Usage-Daten gegen Quelle prüfen; V1/V2-Projektionen und Replay-Sichtbarkeit bestätigen. Wiederholungsimport darf keine Dubletten erzeugen.
4. Competition-Klassifikation prüfen: explizites match_intent=competition muss erhalten bleiben; sportliche Wertbarkeit ausschließlich nach bestehenden Regeln und belegtem Ergebnis. Research bleibt ohne sportliche Wertung; technische Abbrüche ohne Sieger dürfen keine Siege/Niederlagen erzeugen. Fehlender historischer Intent bleibt unbekannt bzw. nach bestehenden Legacy-Regeln behandelt, nicht erfunden.
5. Model Cards und Leaderboard nach Reload prüfen: neue Actor-Teilnahmen, Ergebnisse und Ressourcenwerte; keine künstlichen Elo-Werte, keine doppelte Zählung. Offene Kosten oder unbekannte Provider getrennt dokumentieren.
6. Match Agenda prüfen: kumulative Qualifikation (API → Functional → Research → Competition) aus tatsächlich erreichter Evidenz. Vollständig qualifizierte Actors verschwinden standardmäßig aus der Agenda; erledigte Stufen deaktiviert. Ein erfolgreiches Competition-Ergebnis soll niedrigere Stufen erfüllen, sofern entsprechende Evidenz vorliegt; fehlgeschlagener Versuch allein reicht nicht.
7. Observer: neue importierte Matches/Actors müssen in der später angeschlossenen Vergleichsprojektion berücksichtigt werden; Stichprobe und Zeitkontext prüfen. OBS-ARCH-01/R01 ist zunächst Kontextsteuerung ohne historische Filterwirkung; keine Abnahme einer noch nicht implementierten Ressourcenprojektion behaupten.

## Status / Übergabe
Offen – Factory-Matches laufen laut Nutzer; noch kein Transfer oder Competition-End-to-End-Test in diesem Schritt ausgeführt. Keine Dateien oder lokalen Daten geändert. Bei Threadwechsel zunächst Abschlussstand und Quellenbelege der Factory erfragen bzw. prüfen und obige Abnahme fortsetzen. Nur systematische Integrationslücken beheben, keine Einzelreparaturen historischer Partien. Observer-Entwicklung kann unabhängig weiterlaufen.

Referenzen: PROJECT/ANDY_APP_STUDIO_GPAI_OBSERVER_HANDOFF_2026-11-28.md; PROJECT/ANDY_APP_MATCH_AGENDA02_IMPLEMENTATION_2026-11-28.md; PROJECT/ANDY_APP_MATCH_AGENDA02_R02_2026-11-28.md; PROJECT/ANDY_APP_OBS_ARCH01_R01_2026-11-28.md.
