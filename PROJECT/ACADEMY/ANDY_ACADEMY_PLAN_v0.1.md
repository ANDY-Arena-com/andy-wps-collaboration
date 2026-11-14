# ANDY Academy – Road to Victory
**Version:** 0.1 · **Stand:** 14.11.2026 · **Status:** Name und Entwicklungsziel im Projektdialog angenommen; Lernstufen und technische Ausgestaltung Arbeitsplan, noch nicht implementiert.
**Leitmotiv:** Learn the Rules. Master the Game. Challenge the AI.

## 1. Ziel und Einordnung
Die Academy entwickelt das Interactive Rulebook zu einer Lernumgebung, in der Menschen ANDY verstehen, strategische Entscheidungen üben und schließlich gegen KI antreten. Der Projektleiter ist der erste Pilotlerner: erst interaktive Demos, anschließend KI-unterstütztes Spielen, zuletzt eine eigenständig gespielte Herausforderung gegen KI. Ein Sieg ist Ziel, keine Zusage. 
- Arena: KI im Wettkampf erleben.
- Academy: Spiel verstehen und beherrschen lernen.
- Lab: Strategien und KI-Verhalten evidenzbasiert erforschen.
- Journal: Erkenntnisse und Entstehungsgeschichte vermitteln.
Die bestehenden App-, Lab-, Journal- und Corpus-Aufgaben bleiben bestehen. Academy verbindet Website-Lernmodule mit perspektivischem Mensch/KI-Spiel in der App.

## 2. Ausgangsstand und Evidenz

**[Separates Clickdummy-Verzeichnis](ANDY_ACADEMY_CLICKDUMMIES.md):** Liste der tatsächlich bereitgestellten Einzel-HTML- und ZIP-Versionen V0.0.1/V0.0.2 mit detaillierter Funktionsmatrix A–C, neun Quizfragen, Dateistruktur, SHA-256, Testnachweisen und Abgrenzung zu geplanten Modulen. V0.0.2 ist der aktuelle Offline-Teststand; Mini-Quiz ist umgesetzt, Level-Prüfungen, Sterne und Live-Coaching sind noch Konzept.
- Interactive Rulebook V0.0.1: Offline-Pilot A (Setup/Brettgeometrie), B (Go-Schlag/Kontrollsprung), C (Schach–Go-Phasenwechsel). ZIP SHA-256: 7035c0f01a4524c8baa4ca4df2ebad74ca3b6c2e21e24bbcc6ab35dda950fdd7.
- V0.0.2: optionaler Mini-Quiz-Button mit Overlay, drei Fragen je Szenario, unmittelbares Feedback, Hub-Animation; Brettzustand bleibt erhalten. ZIP `ANDY_Interactive_Rulebook_V002.zip`, SHA-256: 0df206bf2a50613c7e963fb6d47ef488d298b65a36bb1896b7b257d34670f0e0. Integrität am 14.11. erneut geprüft. HTML und ZIP im Entwicklungsdialog; keine Binärarchivierung in GitHub nachgewiesen.
- Website-Designreferenz: [V0.8.4.2](../WEB/WEBSITE_RELEASE_V0842_2026-11-14.md); keine Änderung an der produktiven Website.
- README des Piloten dokumentiert 249 Replay-Zustände und 124 ausgeführte Go-Züge erfolgreich gegen den JS-Port abgeglichen; Chromium-Quiz-Test bestanden. Lokales file://, Safari/mobile und vollständige Parität mit historischer Python-Engine nicht bestätigt. Deutsch, spätere EN/ZH-Integration.
- Zugänglicher [ANDY-Core](https://github.com/OliverMerx/cair4_andy_game_v3/blob/main/andy/domain/andy_core.py), gelesener Blob 964c6e8331d0eb8618b4ab2666d95ee7aefde3e1; historischer Engine-Commit des Matchs offen. Kein freies Schachspiel durch den bisherigen JS-Port.
- Originaldaten unverändert lassen; [Match-Evidenz-Methodik](../ANDY_MATCH_EVIDENCE_JSONL_JSON_SQLITE_v1.0.md).

## 3. Lernprinzip
**Lesen → ausprobieren → verstehen → freiwillig testen.**
Jede Demo fokussiert einen Mechanismus. Brett sichtbar halten; Quiz per Button als Overlay öffnen, wieder schließen und ohne Zustandsverlust weiterexperimentieren. Lernmodus mit Erklärung, Übungsmodus mit Vorhersage und Feedback, Testmodus mit zunächst verborgener Lösung. Falsche Antworten konstruktiv erklären; beliebig oft trainieren. Keine Zeitpflicht; Hinweise schrittweise reduzieren. Strategisch offene Fragen als Experimente behandeln, nicht als Multiple-Choice-Wahrheiten.

## 4. Lernpfad und Sternchen (Entwurf)
| Level | Titel | Ziel / vorgeschlagener Nachweis |
|---|---|---|
| 1 ⭐ | Rookie | Brett, Setup, Hubs, Tabuzone, Phasen und Siegbedingungen verstehen; Regeltest bestehen |
| 2 ⭐⭐ | Explorer | Freiheiten, Gruppen, Schläge und sichere Ankerpunkte in neuen Stellungen erkennen und anwenden |
| 3 ⭐⭐⭐ | Tactician | Kontrolländerungen vorhersagen, taktische Aufgaben mit legalen Zügen lösen |
| 4 ⭐⭐⭐⭐ | Strategist | Risiko, Raumgewinn, Verteidigung sowie Schach- und Go-KO-Drohungen abwägen |
| 5 ⭐⭐⭐⭐⭐ | Challenger | Eine vollständige Partie gegen ein dokumentiertes KI-Modell mit KI-Coaching gewinnen; Mensch entscheidet und führt aus |
| 6 ⭐⭐⭐⭐⭐⭐ | Champion | Eine vollständige Partie gegen ein dokumentiertes KI-Modell ohne Coaching gewinnen; anschließende Analyse erlaubt |

Drei Prüfbereiche: Wissen, Antizipation, Entscheidung. Details zu Aufgabenanzahl, Bestehensgrenzen, Hint-Nutzung und Matchkonfiguration sind noch gemeinsam festzulegen. Sterne kumulativ nach bestandenen Kriterien; nicht allein für Klicks oder Teilnahme. Individueller Fortschritt zunächst lokal speichern (Browser-Speicher, Export/Import als Option; file://-Verhalten prüfen), ohne Account oder API. Kein öffentlicher Leistungsnachweis allein aus lokalem Speicher. Letzte Stufen klar nach Gegner, Farbe, Ruleset, Budget und Hilfestufe kennzeichnen; kein allgemeiner Anspruch, alle KI-Modelle zu schlagen.

## 5. Nächster Umsetzungsbaustein: Demo D
Freiheiten, Sicherheit und strategische Ankerpunkte:
- D1 Außenrand: alle verbleibenden Freiheiten eines gegnerischen Steins nehmen; Außenkante besitzt keine zusätzliche Freiheit.
- D2 Innerer Rand: orthogonale Nachbarschaft zu einem nicht bespielbaren Tabupunkt lässt im zugänglichen Core eine permanente Freiheit. Nicht alle inneren Randpunkte sind gleich; die vier Ecken des Schachbrettrandes sind nicht allein durch ihre Ecklage geschützt. Fünf Hubs besitzen ebenfalls permanente Freiheiten.
- D3 Anker: Eine orthogonal verbundene gleichfarbige Gruppe erbt den Schutz eines dauerhaft freien Nachbarn. Verbindung demonstrieren, auch diagonale Nichtverbindung als Gegenbeispiel.
- D4 Kontrolle: Sicherheit und territoriale Wirkung vergleichen. Leerer innerer Randpunkt kann als Gebiet zählen und trotzdem gegnerisch bespielbar sein. Offene Gebiete mit Außenrandkontakt bleiben neutral. Geschützte Steinpunkte nicht mit garantiertem Gebiet gleichsetzen.
- D5 Mini-Quiz im bestehenden Overlay; einfache Aufgaben, später unbekannte Varianten. Visualisierung besetzbarer vs. permanenter Freiheiten, geschützter Gruppen und tatsächlich veränderter Gebietspunkte. Kontrollwerte berechnen, keine Beispielwerte als echte Engine-Ausgabe ausgeben.
Hypothesen: defensive Anker, offensive Raumgewinn-Strategie und hybride Ansätze; Überlegenheit nicht behaupten. Lab kann Häufigkeit und Folgen anhand dokumentierter Matches analysieren.

## 6. KI-Live-Coach – nächstes Brainstorming (offen)
Ziel: Mensch lernt, nicht KI spielt stellvertretend. Keine Umsetzung oder Providerwahl beschlossen.
- Coaching im ersten Schritt an vorbereiteten, unbekannten Replay-Stellungen erproben, danach in einer echten Mensch-gegen-KI-Partie.
- Mögliche Hilfestufen zur Diskussion: nur auf Nachfrage; sokratische Rückfragen; Warnung vor akuter Gefahr; Vergleich legaler Kandidaten; konkrete Zugempfehlung auf ausdrücklichen Wunsch. Hilfen im Verlauf reduzieren.
- Engine liefert Wahrheit über Legalität, Phase, Brettzustand und berechenbare Konsequenzen; Coach liefert verständliche Einordnung, Alternativen und Unsicherheit. Keine erfundene Legalität, kein automatisches Ausführen, keine Einsicht in interne Gegnermodell-Gedanken.
- Entscheidung und Zug bleiben beim Menschen; Coach und Gegner getrennte Rollen. Vor dem Zug eigene Einschätzung erfassen, nach dem Zug Ergebnis vergleichen. Hilfen und Entscheidungen getrennt protokollieren; keine verdeckte Unterstützung im Challenge-Modus.
- Offene Architekturfragen: Live-Datenübergabe aus der App vs. manuelle Pilotübung, Coach-Prompt und strukturierter Zustand, Antwortformat, Häufigkeit/Trigger, API-Budgets, Latenz, Privacy, Zusammenwirken von Schach-/Go-Analyse und Bedienoberfläche.
- Erst Konzept und kleiner Pilot mit dem Projektleiter; **keine unmittelbare Änderung an 8080/8082 oder Website**. Später separat mit App-Thread abstimmen.

## 7. Roadmap / Abnahme
| Schritt | Status | Exit-Kriterium |
|---|---|---|
| A–C V0.0.2 | Offline-Pilot, positives Nutzerfeedback | Visuelle und fachliche Abnahme auf Zielbrowsern |
| D | geplant | Regelgeprüfte Zustände, permanente/entziehbare Freiheiten, Gruppen und Kontrollwechsel nachvollziehbar; Quiz; keine Regression |
| Academy Level 1–4 | Konzept | Versionierte Übungen und Tests mit definierten Kriterien, lokaler Fortschritt, unbekannte Prüfstellungen |
| Coach-Pilot | Brainstorming offen | Mensch entscheidet, enginegeprüfte Hinweise; Coachingmodus klar sichtbar und abschaltbar |
| Mensch/KI-Livepartie | geplant | Reproduzierbarer Pilot, dokumentierte Hilfestufen und Matchbedingungen |
| Unassisted Challenge | Ziel | Vollständige Partie ohne Coach, nachvollziehbarer Nachweis und freiwillige Nachanalyse |

## 8. Forschungs- und Kommunikationsperspektive
Der Projektleiter gab den konzeptionellen Rahmen; nach eigener Darstellung wurden die engeren Go-Regeln von ChatGPT, DeepSeek und Qwen entwickelt und durch weitere KI-Modelle überprüft. KI-Review ist keine formale Engine-Validierung. Die anschließende menschliche Aneignung des Spiels ist ein mögliches Mensch–KI-Lernexperiment: Regeln verstehen, Konsequenzen antizipieren, selbst entscheiden. Einzelne Lernergebnisse und Siege nicht verallgemeinern. Journal/Making-of kann die Entstehung und den Lernweg dokumentieren; Fight Card „HUMAN vs. AI – The ANDY Challenge“ als langfristige Vision, nicht als bereits erreichtes Ergebnis.

## 9. Zusammenarbeit
Zentrale Academy-Planreferenz in diesem Repository; Implementierung zunächst als eigenständige Offline-Pakete auf Basis der bestehenden Website-Assets. Fortlaufende Änderungen mit Release, Quellen, Prüfstatus und offenen Punkten dokumentieren. Der nächste Dialog dient der gemeinsamen Konzeption des KI-Live-Coachings; danach erst technische Entscheidungen.
