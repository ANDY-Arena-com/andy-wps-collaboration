# ANDY Living Lab × Docs – Iteration 01 / First Public Experience
20.11.2026 · Umsetzungsentscheidung nach Delegation durch Projektleitung · basierend auf Produktkonsens 20.11. und Reviews DS/Qwen/Analysis/Docs. Kein technischer Release, keine Anbieterfreigabe.

## Ziel
Eine attraktive, öffentlich verständliche und tatsächlich nutzbare erste Erfahrung statt Feature-Vollständigkeit. Doku weckt Neugier und erklärt; App ermöglicht Untersuchung; Journal vermittelt Ergebnisse und offene Fragen. Arena bleibt eigenständig. Keine konkurrierenden Datenwahrheiten.

## 1. Verbindliches Zielbild und Entscheidungen
- Doku: bestehende Lab-Startseite und sechs Subseiten (Warum ANDY Lab?, Das Spiel als Mikroskop, Was können wir entdecken?, Das Living Lab nutzen, Beyond the Arena, Forschungsgrundlagen) erhalten. DE/EN synchron; übrige Hauptkapitel und Arena-Bedienung bleiben unverändert.
- App: Dashboard → Explorer → einfacher Builder; gespeicherte Profile/Snapshots zunächst in diesen Bereichen, kein eigenes Workspace-Modul als Startvoraussetzung. Macro/Meso/Micro/Event sind Blicktiefen, nicht getrennte Anwendungen. Vier thematische Einstiege Competitive Behavior, Network Configuration, Resource Economy, Competition & Reaction. Alte Ansichten erhalten/integrieren, keine Umbenennung ohne fachliche Prüfung.
- Offline deterministische Analyse, kein zusätzlicher Provideraufruf im Startumfang. Ein optionaler explizit aktivierter KI-Assistent ist später separat zu entscheiden; bestehende Chatfunktion nicht unkontrolliert entfernen. Kein KI-Aufruf beim Öffnen/Filtern/Exportieren.
- Behavior Card als kontextgebundene Profilansicht mit tatsächlichen verfügbaren Werten und offenen Fragen, nicht als Score/Radar mit erfundenen Skalen. Fünf Economics als Perspektiven. Keine automatischen g/DRP/Bonoma/Sweet-Spot/Punch/Overthinking-Urteile.
- Positive statt defizitorientierte Kommunikation: beobachtbare Fragen, Vergleich und Grenzen; kein Marketing einer unbewiesenen Modellüberlegenheit.

## 2. Operatives Gate 0
[#12](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/12) bleibt höchste operative Priorität. Aktuell nur 8082 gemäß [letztem Audit](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/12#issuecomment-7039885066). 8080/8083 nicht ändern oder neu auditieren. Gemeinsamer Facts-Resolver, Resume-Graph-Abdeckung, Lab-Projektion und Browserabnahme offen. S150-Overlap eindeutig, historische Ergebniswertung weiterhin offen. Keine neue DB, keine neue Produktionsprojektion vor Gate; keine Änderung an Regeln, Originalen, Budget/Usage oder lokalen Installationen durch Docs. #11 separat. Doku darf parallel bereits archivierte, klar markierte Referenzfälle nutzen.

## 3. Iteration 01 – ein Case statt neun unabhängiger Werkzeuge
Stabile gemeinsame Case-ID: CASE-CONFIG-01 / Same Models. Different Outcomes. (Astra × Argon).
Referenzen: [S150](../ANALYSES/andy_83f51171e438/v0.1/README.md), [S350](../ANALYSES/andy_cc11a6598bcf/v0.1/README.md).
S150: 3 logische Partien, 4 technische Segmente, 1 belegtes Resolver-TKO Argon, 2 weitere budget_overshoot ohne gesichertes Verdikt. S350: 2 Partien, Farbwechsel, 2 Astra-Matt-Siege laut Runner. 150k/2048/300/Retry 4,5,4 vs 350k/4096/500/Retry 5; A2. Kein isolierter Budgeteffekt, keine neue historische Ergebnisentscheidung. Keine Rohdaten-Neuvalidierung in Docs.

| Schritt | App-Ziel (nach Gate 0) | Doku-Gegenstück | Abnahme |
|---|---|---|---|
| 1 Entdecken | Dashboard-Case mit Ergebnis/Config-Kontrast | Startseite/Entdecken | Frage und Datenstatus sofort verständlich |
| 2 Vergleichen | Explorer S150/S350; Config-Diff; Modellorientierung/Farbwechsel | Spiel als Mikroskop | Profile, n, Unterschiede, fehlende Werte sichtbar |
| 3 Vertiefen | S350 Runde 1: Go-Samples, Ressourcen, Match- und Event-Referenz | Was können wir entdecken? | identische Match-ID/Filter, keine erfundene Vollkurve oder Kausalität |
| 4 Selbst untersuchen | Golden Template: Kohorte, zulässige Metrik, Gruppierung, Grafik | Das Living Lab nutzen | Filterwechsel verändert Grafik nachvollziehbar; offline |
| 5 Bewahren | SVG/CSV + versionierter Snapshot/Live-Definition | Nutzung und Forschungsgrundlagen | Export = Bildschirmwerte, Quellen und Methoden pinnen |
| 6 Verdichten | Minimal-Behavior Card für S350-Kohorte | Entdecken | sportlicher Kontext, Usage und offene Perspektiven; keine universelle Bewertung |

Erste Grafikbibliothek: Vergleich, Verlauf, Relation, Matrix; weitere Muster/Spatial Views nach Prüfung. TKO/Resume-Forensik als nächster Case, nicht neues separates Hauptmodul. Grok/Astra und Fable/Astra erst nach konkreter Original-/Usage-/Resolverprüfung; keine unbestätigten 26k-Behauptungen oder Ko-Kausaldiagnosen.

## 4. Gemeinsamer redaktioneller Vertrag
Jeder Case: Beobachtung → Grafik → offene Frage → eigene Untersuchung → Quellen/Grenzen. Jede Grafik: Case-ID, Metrik/Version, Kohorte/n, Datenstand, Einheit/Nenner, Abdeckung, Quelle. BEOBACHTET/BERECHNET/INTERPRETIERT/OFFEN bezeichnen Evidenzart, nicht Qualitätspunkt. Unbekannt ≠ 0. Doku darf archivierte Daten zeigen, aber App-Ziel ausdrücklich als Entwicklungsziel markieren. Keine toten Buttons oder vorgetäuschte Live-App. Screenshots: UI, Erkenntnis, Use Case, App-Stand. App-Hilfen verlinken stabile Doku-Hashes; Doku verlinkt nur tatsächlich verfügbare App-Views oder ausdrücklich benannte Demos. Keine harte Bindung an localhost in öffentlicher Doku.

## 5. Iteration App ↔ Docs
Ein gemeinsamer Arbeitsstand je Case, keine getrennten Featurelisten:
A) Docs beschreibt Frage und verständliche Grafik; B) App prüft Daten-/Metrikvertrag und verwirklicht schmalen Nutzungspfad; C) gemeinsame Offline-/Browserabnahme; D) Docs ersetzt Entwurf durch verifizierten Screenshot/Export, Journal nutzt denselben Export; E) Beobachtung neuer Lücken zurück in nächsten Zyklus.
Pro Iteration Status: ENTWURF / ARCHIV-REFERENZ / APP-IMPLEMENTIERT / GETESTET / FREIGEGEBEN getrennt von Evidenzmarkern. GitHub-Nachweis, App-Version, Case-ID, DE/EN-Links, Testresultat und offene Abweichungen protokollieren. Kein Release nur aus Dokumentations-Commit ableiten.

## 6. Verantwortungsgrenzen
Docs/Koordination: Navigation, verständliche Research Case, beidseitiger Vertrag, öffentliche archivierte Beispieldaten. Thread 1: tatsächlicher lokaler Code, Datenfundament, minimaler reversibler Einbau auf 8082, Tests/Browser. Analysis: Metrik-/Quellenprüfung und Gegenhypothesen. Projektleitung: externe Freigabe. Keine automatische Kommunikation zwischen Threads; dieses Dokument ist Handoff.

## 7. Startabnahme
Ein neuer Besucher versteht den Fall ohne Methodikstudium, kann nach Gate 0 mindestens ein Filter-/Grafikexperiment ausführen, dessen Export wiedererkennen und die offene Frage benennen. Ergebnis-/Quellenkonsistenz, Sprachparität, Offline/keine zusätzlichen API-Calls, Browser-/Mobiltest. Öffentliche Docs-Preview darf vor App-Abnahme online sein, aber mit ehrlichem Status. Keine festen Wochenfristen oder Vollausbau als Eintrittsbedingung.
