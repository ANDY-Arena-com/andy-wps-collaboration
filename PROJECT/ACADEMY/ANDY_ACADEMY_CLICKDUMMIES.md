# ANDY Academy – Clickdummies / Offline-Prototypen
**Stand:** 14.11.2026 · **Inventar v0.1** · **Aktueller Teststand:** V0.0.2

Ergänzung zum [Academy-Entwicklungsplan](ANDY_ACADEMY_PLAN_v0.1.md). Hier werden ausschließlich tatsächlich bereitgestellte Artefakte und deren Funktionsumfang erfasst. Konzeptskizzen und geplante Demos sind separat gekennzeichnet. HTML/ZIP befinden sich im Entwicklungsdialog ANDY Academy; die Binärdateien wurden nicht in dieses Repository übertragen. Dateinamen und Prüfsummen dienen der eindeutigen Zuordnung.

## 1. Bereitgestellte Clickdummies
| Version | Einzel-HTML | Entwicklungs-ZIP | Stand |
|---|---|---|---|
| V0.0.1 | `ANDY_Interactive_Rulebook_V001.html` | `ANDY_Interactive_Rulebook_V001.zip` | Erster Offline-Pilot, drei Szenarien A–C; positive Rückmeldung, Referenzstand |
| V0.0.2 | `ANDY_Interactive_Rulebook_V002.html` | `ANDY_Interactive_Rulebook_V002.zip` | A–C unverändert, Mini-Quiz ergänzt; positive Rückmeldung, aktueller Teststand |

**Start:** Einzel-HTML direkt im Browser öffnen oder ZIP vollständig entpacken und `ANDY_Rulebook_V001/index.html` bzw. `ANDY_Rulebook_V002/index.html` starten. Kein Server, keine Installation, keine Internetverbindung oder KI-API für die Demo erforderlich. Keine produktive Website-Integration.

## 2. V0.0.1 – Interaktives Grundgerüst
Gemeinsame Oberfläche mit Szenariowechsel A/B/C, hellem 13×13-Brett auf Basis der vorhandenen Theater-Gestaltung, Original-SVG-Figuren, plastischen Go-Steinen, Ansichten Schach/Go/beide, Koordinaten, Phasen- und Fortschrittsanzeige, Kontrollwerten Weiß/Schwarz (Stein- und Gebietspunkte getrennt), Handlungshinweisen und Quellenangabe. Brettinteraktionen und geführte Buttons, Neustart je Szene. Tastaturbedienbare Brettziele; animierte Setzung, Schachbewegung und Steinentfernung.

| Szenario | Umgesetzte Interaktion | Lerninhalt / Datenbasis |
|---|---|---|
| A – Setup & Brettgeometrie | Historische 16 Setzungen Schritt für Schritt, zurückblättern; freies Setup mit abwechselnd acht Setzungen je Farbe; Kontrollflächen umschaltbar im freien Setup | 120 Ringpunkte, fünf doppelt gewertete Hubs, 44 Tabupunkte; Belegung, Selbstmord und Ko geprüft. Match #1–16 bzw. didaktisches Experiment mit JS-Port. Ursprünglicher Grund für exakt acht Setzungen nicht belegt. |
| B – Go-Schlag & Kontrollsprung | Bedrohte Gruppe rot markieren, a1 setzen, sechs schwarze Steine animiert entfernen; Vorher-Ansicht; Kontrollflächen ein/aus | Originalmatch #74: a2–a7 verlieren letzte Freiheit. Weiß 24→25, Schwarz 25→19; bestehende Gebiete bleiben gleich (k11 weiß, k3 schwarz). Keine Gebietsänderung durch diesen Zug. |
| C – Schach & Go | Dieselbe Schachstellung mit/ohne Go-Steine vergleichen; e2–e4 animieren, danach j11 setzen; zurück zur Ausgangsstellung | Originalmatch #17–18; Go-Kontrolle bleibt nach dem Schachzug gleich, dann Go-Aktion derselben Farbe. Kopplung über Phasen und Siegbedingungen, keine räumliche Blockade im zugänglichen Core. Markierte e3/e4 sind didaktische Anschauung, keine vollständige Legalitätsliste. |

## 3. V0.0.2 – Mini-Quiz als optionales Overlay
Der Benutzer liest und experimentiert zuerst, öffnet dann freiwillig „Mini-Quiz“ neben dem Neustart. Nativer Dialog über dem Brett, drei Antwortmöglichkeiten je Frage, direktes Feedback und Erklärung, nächste Frage, Abschluss mit Zahl direkt richtiger Antworten, Wiederholung, Escape/Schließen und Fokus zurück zum Button. Quiz-Zustand getrennt vom Brett; keine Veränderung von Spielstellung, Kontrollwerten oder Szenariofortschritt. Hub-Zählung als kleine Animation (3 weiße / 2 schwarze Hubs = 6 / 4 Steinpunkte unter der Annahme, dass beide zuerst Hubs besetzen).

**Neun implementierte Fragen (je drei):**
- A: möglicher weißer Startvorteil im Hub-Wettlauf; Hubwert gegenüber Ringstein; geometrisch erlaubte Go-Setzpunkte und weitere Zugregeln.
- B: warum sechs Steine bei a1 verschwinden; Bedeutung der leeren Gebietspunkte k11/k3; Ursache des Kontrollverlusts von 25 auf 19.
- C: Go-Steine und Schachlegalität; Zugreihenfolge nach e2–e4; Schachmatt trotz Go-Führung.

Noch kein Level-Test, persistenter Lernfortschritt oder Sternesystem. Die laufende Quiz-Punktzahl ist keine Academy-Zertifizierung.

## 4. Technischer Aufbau / Herkunft
| Datei im ZIP | Aufgabe |
|---|---|
| index.html, style.css | gemeinsame Offline-UI; ab V002 zusätzlich Dialog und Quizgestaltung |
| demo.js | Szenariozustand, SVG-Renderer, Aktionen, Markierungen und Texte |
| go-core.js | lokaler deterministischer Go-Port: Geometrie, Gruppen, Freiheiten, Schlag, Selbstmord, Ko, Kontrolle |
| evidence.js | reduzierte Replay-Projektion mit 249 Zuständen; keine Original-JSONL |
| pieces.js, logo.png | vorhandene Figurenpfade und Logo |
| quiz.js (ab V002) | Fragen, Auswertung, Feedback, Hub-Animation, Dialogsteuerung |
| test.js, README.txt | Replay-/Geometrie-Prüfung, Quellen, Startanleitung, Grenzen |

Website-Designbasis: [V0.8.4.2 Final Polish](../WEB/WEBSITE_RELEASE_V0842_2026-11-14.md), ZIP SHA-256 `2731fce697cb7feddc9959902398413570d8e93e2c699cf5c990bee0c9bd6268`.
Match: `andy_0c0f7413fdf6` (Astra–Argon), protokolliertes Ruleset v1.1, Original-JSONL SHA-256 laut Paket-README `7f955acabc196c592c8b6a623fd9b644d9110e35f482c14fd6704a32682f093e`. [Core](https://github.com/OliverMerx/cair4_andy_game_v3/blob/main/andy/domain/andy_core.py), gelesener Blob `964c6e8331d0eb8618b4ab2666d95ee7aefde3e1`. Originaldaten bleiben unverändert. Keine nachgewiesene historische Engine-Parität.

## 5. Paketidentität und Prüfstand
| Artefakt | Bytes | SHA-256 (am vorliegenden Artefakt erneut berechnet) |
|---|---:|---|
| V001 ZIP | 40303 | `7035c0f01a4524c8baa4ca4df2ebad74ca3b6c2e21e24bbcc6ab35dda950fdd7` |
| V001 HTML | 234064 | `3c69bf72e72fa36edafd03e32862ebe1cdaab817e384c9b96f498b303e70bb88` |
| V002 ZIP | 44972 | `0df206bf2a50613c7e963fb6d47ef488d298b65a36bb1896b7b257d34670f0e0` |
| V002 HTML | 244269 | `c7f6455c13b023a8ed6c4509e578c72b52aa80e773d59a4864b99f3821504434` |

- Erneut geprüft: beide ZIPs fehlerfrei; aus V002 entpackt `node test.js` PASS für 249 Replay-Zustände und Kontrollwertpaare, 124 ausgeführte Go-Züge und Schlagzahlen sowie Geometrie; alle JS-Dateien Syntax OK.
- Laut V002-README früherer Chromium-Test mit eingebettetem Einzel-HTML bestanden: alle neun Fragen, falsche Antworten, Wiederholung, Escape, Fokus-Rückgabe, gleichbleibender Brettzustand/Kontrollwerte/Fortschritt und 375px-Viewport. Nicht in diesem Dokumentationsschritt erneut im Browser ausgeführt.
- Nutzerfeedback im Entwicklungsdialog positiv zu V001 und V002; keine vollständige fachliche oder plattformübergreifende Freigabe daraus ableiten.
- Offen: direkter file://-Aufruf war im Browser-Testcontainer gesperrt; Safari, iPad, Windows und lokale ZIP-Abnahme; vollständige Python-Engine und Schachzuglisten; historischer Engine-Commit; EN/ZH-Übersetzungen; gemeinsame Szenario-Schnittstelle und spätere Website-Einbettung.

## 6. Nur Konzept – noch keine bereitgestellten Clickdummies
- Demo D: Außenrand vs. innere Tabuzone, permanente Freiheiten, geschützte Gruppen und Ankerstrategie; Kontrollgebiete vs. dauerhafte Steinsicherheit.
- Deutlichere Unterscheidung bestehender, gewonnener und verlorener Gebietspunkte (Feedback zu Szene B).
- Academy-Sternesystem, Level 1–6, echte Prüfstellungen und persistenter Fortschritt.
- Live Coach: Observer, Tutor, Advisor, Sparring Partner; schematische UI im Dialog, keine eigenständige HTML-Datei, keine API oder App-Anbindung.
- Replay-Trainingsmodus mit verborgenem Folgezug: menschlicher Kandidat, tatsächlich ausgeführter KI-Zug, enginegeprüfter Vergleich; noch zu konzipieren.
