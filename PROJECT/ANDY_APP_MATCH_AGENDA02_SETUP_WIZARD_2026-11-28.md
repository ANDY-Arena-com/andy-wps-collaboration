# ANDY APP – MATCH-AGENDA-02 und Setup Guided Tour
Stand 28.11.2026. Verbindliche nächste Entwicklungsbasis, noch keine Implementierung dieses Inkrements.

## 1. Priorität und Abschluss der Grundlagenphase
MATCH-AGENDA-02 – Minimum Required Evidence jetzt umsetzen und produktiv abnehmen. Danach ist eine gemeinsame Basis für weitere APP- und Observer-Entwicklung geschaffen; keine zusätzliche Detailoptimierung als Voraussetzung. Master bleibt Studio 8080, mehrere lokale Ports mit gemeinsamem Code und Datenbestand. Deployment auf weitere Rechner erst nach erstem neuen Observer und Modellintegration.

MATCH-AGENDA-01: Nutzer-Screenshots bestätigen Agenda mit 33 Actors, 25 offenen Pflichtspielen, 132 Matchbelegen und 4 Lesehinweisen sowie vorausgefüllte Spielkonfiguration. Diese Zahlen sind ein UI-Snapshot, keine abschließend validierte Datenabdeckung. Muse Ember vs Gemini 3.8 Flash wurde bewusst als Testspiel ohne reguläre Archivierung gestartet; Anzeige am Ende: 46.045 vs 1.915 Tokens, davon Output 41.865 vs 128, je 50k Budget, API-Zeit insgesamt 151s. Keine Aussage über strategische Qualität oder genaue Reasoning-Quote ohne Beleg. Motivation: zielorientiertes Testende, keine modellspezifischen Sonderpatches.

## 2. MATCH-AGENDA-02 – verbindlicher Funktionsumfang
- Match Intent separat von Evidenz und Ressourcenlimits: Functional, Research, Competition. Historische Matches ohne Intent weiterhin auswerten, keine rückwirkende Änderung.
- Functional: erste gültige Aktion des zu qualifizierenden Actors als Ziel. Ende unmittelbar nach bestätigter und protokollierter Aktion, vor nächstem API-Aufruf; eigener Abschlussgrund qualification_goal_reached. Budget, Output-Cap, Retry- und Fehlergrenzen bleiben wirksam. Vorgeschlagene Defaults 50k je Actor, Output-Cap 8192 soweit unterstützt, Reasoning default, Kandidat Weiß, editierbar. Keine künstliche Siegwertung oder Nutzerabbruch.
- Research: regulär archivierte Versuchsaufzeichnung mit definiertem Ziel, zunächst z.B. max_decisions 10; keine sportliche Wertung. Competition: reguläres Spielziel und bestehende sportliche Wertungsregeln. Intent allein erzeugt keine Qualifikation.
- Kumulative Qualifikation API → Functional → Research → Competition. Höherwertige tatsächlich erreichte Evidenz erfüllt darunterliegende Anforderungen, nicht umgekehrt. Technisch abgebrochener Competition-Versuch kann Functional erfüllen; kein automatischer Research-/Competition-Erfolg. Research-Grundqualifikation nach bisheriger Agenda: archivierter definierter Abschluss mit gültigen Aktionen beider Actors; genaue Kriterien im gemeinsamen Projektionscode festlegen. Competition nur nach gültigem sportlichem Ergebnis.
- Kompakter persistenter Qualification Record auch bei Funktionstest ohne vollständige Matchaufzeichnung. Bestehende gemeinsame DB verwenden, additive Struktur, keine zweite DB. Route/Actor-Identität, Zeit, Testziel, Ergebnis, gültige Aktionen, Aufrufanzahl, Usage soweit bekannt, gemeldeter Inferenzanbieter, optional Match-ID und Belegreferenz. Keine Schlüssel speichern. Fehlende Werte unbekannt; idempotente Speicherung, gemeinsame Schreibsicherheit.
- Gemeinsame Qualifikationsprojektion für Agenda, Cards, Leaderboard und später Observer; historische vorhandene Evidenz anrechnen, keine Wiederholung nur wegen neuem Schema. Exakte belegte Identitäten verwenden, keine Alias- oder Provider-Inferenz ohne Beleg.
- Agenda zeigt fehlende Evidenz und erlaubt direkte Auswahl jeder höheren Spielabsicht; vorhandenen Setup-Dialog mit Defaults öffnen, bei belegtem Port vorhandene Parallelübergabe nutzen. Keine automatische kostenpflichtige Partie. Replay historische Aktivität.
- Neue Actors im Leaderboard auch ungewertet sichtbar, Cards zeigen Qualifikation. Keine künstlichen Elo-Werte. Funktionstest ohne reguläre Aufzeichnung nicht in Matchstatistik mischen.
- Abnahme: erfolgreiche erste Aktion beendet Test ohne weiteren Call; Fehlschlag bleibt offen; kompakter Nachweis nach Neustart und auf anderem Port sichtbar; Research/Competition rechnen niedrigere Stufen an; bestehende reguläre Spielsteuerung unverändert; Agenda/Cards/Leaderboard konsistent. Offline-Tests und produktive Tests unterscheiden.

## 3. Zukunft: Setup-Guided-Tour-Wizard (Einsteiger / Academy)
Nutzerwunsch ausdrücklich vorgemerkt: später geführte Ersteinrichtung für neue ANDY-Nutzer. Umsetzung deutlich später; Hook bereits jetzt bei MATCH-AGENDA-02 architektonisch berücksichtigen.
Ziel: neue Installation ohne Kenntnis von Modellnamen, Providern oder internen Menüs bis zum ersten erfolgreichen Spiel führen.
Geplanter Ablauf:
1. Setup-Status ermitteln: existiert ein nutzbarer Modellkatalog, welche Modelle/Routen sind registriert und auswählbar?
2. API-Key-Verfügbarkeit je relevanter Route prüfen (nur Vorhandensein, keine Werte ausgeben oder speichern). Vorhandensein ist nicht gültige Authentifizierung.
3. Fehlende Zugänge erklären, zu bestehender Konfiguration/Recruitment führen; tatsächlichen API-Test nur bewusst auslösen, Kostenhinweis.
4. Geeigneten verfügbaren Actor und Referenzgegner vorschlagen, vorhandene Qualification Evidence anrechnen.
5. Über denselben Match-Agenda-/Setup-Pfad ersten kurzen Funktionstest vorbereiten und nach explizitem Start ausführen.
6. Ergebnis erklären, nächste Schritte zu Research Match, Replay, Cards, Leaderboard und Observer anbieten.
Hook jetzt: wiederverwendbare, UI-unabhängige Readiness-/Qualification-Projektion mit getrennten Statuswerten für Modellregistrierung, Key vorhanden/unbekannt, API-Qualifikation, Functional, Research, Competition; vorhandene Setup-/Agenda-Einstiegspunkte wiederverwendbar halten. Keine neue parallele Datenhaltung, keine Duplikation der API- oder Spielsteuerung. Konkrete Schnittstellennamen nach Inspektion des aktuellen Codes wählen. Kein erzwungener Wizard, kein automatischer API-Aufruf oder Key-Export. Später optional erneut aufrufbar; Fortschritt aus tatsächlicher Evidenz ableiten.
Wizard-UI, Onboarding-Texte und umfassende Plattformtests ausdrücklich nachgelagert; Hook noch nicht implementiert.

## 4. Weiterarbeit
Aktuelle nächste Aufgabe: MATCH-AGENDA-02 implementieren, einschließlich minimalem Setup-Hook, anschließend lokale Abnahme. Danach wieder Observer/Usage/Economy/Actor Selection/Evidence und weitere Forschungsfunktionen gemäß Hauptübergabe priorisieren. Keine historische Sync-Reparatur.
Referenzen: PROJECT/ANDY_APP_STUDIO_GPAI_OBSERVER_HANDOFF_2026-11-28.md und PROJECT/ANDY_APP_MATCH_AGENDA01_2026-11-28.md. Vor Umsetzung tatsächlichen lokalen Stand bzw. Baseline und Patchkette verifizieren. Dieses Dokument ist eine Entscheidung und Abnahmespezifikation, kein Nachweis fertigen Codes.
