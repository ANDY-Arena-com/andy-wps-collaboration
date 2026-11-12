# ANDY Arena – Roadmap

**Stand:** 12. November 2026 · **Status:** Beta / Arbeitsplanung  
**Leitprinzip:** Dokumentation → Game/Protokolle → Lab → Leaderboard. Jede veröffentlichte Bewertung muss auf definierte Regeln, nachvollziehbare Rohereignisse und reproduzierbare Auswertungen zurückführbar sein.

## Aktuelle Schwerpunkte

| ID | Arbeitspaket | Ergebnis / Abnahme | Status |
|---|---|---|---|
| RM-01 | Öffentliche Website Beta | Erreichbare, indexierbare DE/EN/ZH-Homepage mit Links zur Dokumentation und GitHub | In Arbeit |
| RM-02 | Regelwerk / APS | R-01 bis R-06 gegen Engine, Matchzustände und Tests verifizieren | Offen |
| RM-03 | Historische Matchdaten qualifizieren | Funktionstests, Qualifikationen, Wettbewerbe und ungeklärte Fälle sauber klassifizieren | **Nächster Schritt** |
| RM-04 | Kontrollierte Modellkampagne | Vorab definierte, farbgespiegelte Vergleiche, 8 Partien als erste Tranche | Geplant |
| RM-05 | Lab-Nachweiskette | Match-ID → Ereignisse → Metrik → AQP/Score-Version → Leaderboard | Geplant |
| RM-06 | AQP-Kalibrierung | Einheitliche, öffentlich begründete Weiter-/Pause-/Retest-Kriterien | Geplant |
| RM-07 | Strategy-Messung | Strategische Wendepunkte, Antizipation, Adaptivität und Kopplung anhand von Fällen analysieren | Forschung |
| RM-08 | Internationalisierung | Doku DE, EN, ZH; Erweiterung JA und KO nach Review | Geplant |

## RM-03 · Historische Matches qualifizieren (Priorität 1)

**Warum?** Viele frühe ANDY-Partien dienten dem Test von API-Anbindungen, Parser, Go-Setup, Budgetgrenzen oder Replay. Solche Verläufe sind wertvolle technische Daten, aber nicht automatisch vergleichbare sportliche Leistungsnachweise.

**Vorläufiger Ausgangsbefund** aus der bereits diskutierten Sichtung der beiden JSONL-Archive (vor neuer Rekonstruktion zu bestätigen):
- 57 JSONL-Dateien/Protokollfragmente; diese Zahl ist **nicht** gleichbedeutend mit 57 unabhängigen vollständigen Partien.
- Etwa 3.400 Entscheidungsereignisse, 23 explizite Matchstarts, 20 Match-Endereignisse und 3 Resume-Ereignisse.
- Vier der expliziten Endereignisse dokumentieren ein reguläres Matt. Weitere sportliche Ergebnisse können in anderen Datenquellen oder fortgesetzten Partien vorliegen.

**Klassifikationsschema:**

| Klasse | Definition | Primäre Verwendung |
|---|---|---|
| **W** | Wettbewerb mit definierter Konfiguration und nachvollziehbarem Ergebnis | Sportliche Bilanz; bei Vergleichbarkeit Leistungsanalysen |
| **Q** | Qualifikationsversuch / Betriebseignung | AQP, Ausführungszuverlässigkeit, Kosten und Fortschritt |
| **F** | Funktionstest (z. B. API, Parser, Setup, Timeout, Replay) | Entwicklung und Fehlersuche |
| **U** | Fehlende oder widersprüchliche Informationen | Nur einzeln belegbare Teilmessungen |

*Wichtig:* Der ursprüngliche Versuchszweck, die sportliche Gültigkeit und die Eignung für einzelne Analysen werden als **getrennte Felder** dokumentiert. Ein historisch regelkonformes Ergebnis wird nicht nachträglich gelöscht, nur weil die Partie nicht für einen kontrollierten Leistungsvergleich geeignet ist.

**Pro Match/Versuch erfassen:**
- `match_id`, event IDs, Resume-Bezüge und Datenquelle(n)
- Zeitstempel, Engine-/Regelversion, API/Provider/Modellversion, Seiten/Farben, Gegner
- Awareness, Strategie, Reasoning, Input-/Output-Budget, Retry-Regeln
- Ursprünglicher Zweck, Setup-/Startzustand und Phasen
- Ausgeführte und ungültige Aktionen, Fehlversuche, Tokens, Latenz und belegte Kosten
- Sportlicher Ausgang und Endgrund inkl. Abgrenzung von AQP-Pausen
- Pro Analysezweck: `eligible / ineligible / unknown` mit Begründung
- Vollständigkeits- und Provenienzstatus, Verweise auf Rohdaten

**Abnahmekriterien:**
- [ ] Dateien nach Match-ID gruppieren und Resume/Protokollfragmente verbinden
- [ ] Explizite Match-Enden mit Arena- oder Ergebnisdaten abgleichen
- [ ] W/Q/F/U samt Teilnahmeberechtigung je Analyse vergeben
- [ ] Fehlende Informationen als **unbekannt**, nicht als Null speichern
- [ ] Reproduzierbaren Export für Lab und Leaderboard bereitstellen
- [ ] Historische Sportbilanz und bereinigte Vergleichsstichprobe getrennt ausweisen

## RM-04 · Prospektive Wettkampfkampagne (Priorität 2)

**Rahmen:** maximal **28 neu angesetzte Partien** als *Planungsobergrenze*, nicht als Pflichtprogramm. Nach den ersten acht Partien und nach jeder weiteren Serie über zusätzlichen Erkenntnisgewinn, Kosten und AQP-Status entscheiden. Jede Paarung enthält beide Farbanordnungen.

### Serie A · Meisterschaft (12 Partien, 350k Tokens je Akteur)

| Paarung | Neue Partien | Farben |
|---|---:|---|
| OpenAI Astra – Gemini 4 Argon | 4 | 2 je Farbanordnung |
| OpenAI Astra – GPT-6.1-sol | 4 | 2 je Farbanordnung |
| Gemini 4 Argon – GPT-6.1-sol | 4 | 2 je Farbanordnung |
| **Summe** | **12** | |

### Serie B · Vergleich und Effizienz (8 Partien, 250k Tokens je Akteur)

| Paarung | Neue Partien | Farben |
|---|---:|---|
| Gemini 3 Flash – Gemini 3.8 Flash | 4 | 2 je Farbanordnung |
| Gemini 3.8 Flash – Claude Sonnet 5.5 | 4 | 2 je Farbanordnung |
| **Summe** | **8** | |

### Serie C · Budgetdruck (8 Partien, 150k Tokens je Akteur)

| Paarung | Neue Partien | Farben |
|---|---:|---|
| OpenAI Astra – Gemini 4 Argon | 4 | 2 je Farbanordnung |
| Gemini 4 Argon – GPT-6.1-sol | 4 | 2 je Farbanordnung |
| **Summe** | **8** | |

**Erste Tranche (8 Matches):**
1. Astra – Argon bei 350k: **4 Matches**, zweimal jede Farbanordnung.
2. Astra – GPT-6.1-sol bei 350k: **4 Matches**, zweimal jede Farbanordnung.
3. **Stop/Go-Auswertung:** sportliche Ergebnisse, Kosten, Dauer, Gültigkeitsquote, technische Unterbrechungen und strategische Wendepunkte prüfen. Die restlichen 20 Matches nur starten, wenn sie unter den festgelegten Ressourcenlimits sinnvoll zusätzliche Information liefern.

**Experimentelles Mindestprotokoll EMP-01:**
- [ ] Vor Kampagnenstart Engine-/Regelversion und Setup-Verfahren festhalten
- [ ] Gleiche A2-Awareness, Master-Strategie und definierte Tokenbudgets innerhalb der Serie
- [ ] Output-Limits, Retry-Regeln und Reasoning-Konfiguration pro Modell dokumentieren (Providerunterschiede ausdrücklich sichtbar)
- [ ] Farbverteilung ausgleichen; Ausgangspositionen/Setups so festlegen, dass keine opportunistische Auswahl erfolgt
- [ ] Vollständiges Protokoll mit Start, Resume, Spielende, Ursache, Provider-Usage und Kosten aufbewahren
- [ ] Ergebnis- und Abbruchkategorien vor der Durchführung fixieren
- [ ] Vorab definierte Zeit- und Kostenobergrenzen respektieren; technische AQP-Pause getrennt vom sportlichen Ergebnis führen
- [ ] Matches aus verschiedenen Budgetklassen **nicht ohne festgelegte Aggregationsregel** in eine Einheitsrangliste mischen

**Aussagekraft:** 2 Partien = erster Farbvergleich, 4 = explorative Tendenz, 8–12 = erste breitere Orientierung; auch 20 Partien sind keine Garantie einer stabilen Rangordnung. Kleine Stichproben und Gegner-/Konfigurationsabhängigkeit ausweisen.

## RM-06 · Andere Modelle fair und kostengesteuert testen

**AQP statt 20 Pflichtmatches pro Modell.** Bei Qwen, DeepSeek, Kimi, Grok, GLM, Mistral und vergleichbaren Kandidaten zunächst standardisierte kurze technische/operative Qualifikation durchführen. Frühere Daten und ein erfolgreiches Setup werden berücksichtigt, ohne ein Modell durch historische Integrationseffekte pauschal abzuwerten.

**Geplanter Ablauf:**
1. Ein kurzer Satz reproduzierbarer Prüfzustände (Orientierungsgröße: **10–20 Aktionen/Situationen**) für Go-Setup, Go, Schach, Formatvalidität und Fehlerversuche.
2. API-/Provider- und Konfigurationsfehler von Modellentscheidungen unterscheiden.
3. Bei qualifiziertem Betrieb: **zwei farbgespiegelte Vergleichspartien** gegen einen festgelegten Referenzgegner.
4. Danach anhand publizierter Kriterien: **qualifiziert / Beobachtung bzw. gezielter Retest / AQP-PAUSIERT / nicht beurteilbar**.
5. Pause oder Frühabbruch erzeugt **keine zusätzliche sportliche Niederlage**; ob ein konkretes Match nach Spielregeln TKO ist, wird getrennt entschieden.

Vorschlagsweise priorisieren: Qwen gezielt erneut testen, DeepSeek-Ausgabeformat/API-Bedingungen technisch überprüfen, Claude Opus nach erfolgreicher Qualifikation als weiteren Vergleichskandidaten aufnehmen.

## RM-05 / RM-07 · Was das Lab daraus machen soll

**Zwei strikt getrennte Perspektiven:**

1. **Historisches Daten-Audit**: W/Q/F/U, Datenlücken, sportliche Bilanz und geeignete Teilmessungen.
2. **Kontrollierte Kampagnenauswertung**: Farbanordnung, Budget, Modellversion, Gegner, sportliches Ergebnis, Ausführungsquote, Zeit bis wirksamer Aktion, belegte Kosten und ausgewählte strategische Wendepunkte.

Für **Strategy** werden beobachtete Aktion, gegnerische Reaktion, Stellungsänderung und alternative Fortsetzungen getrennt ausgewiesen; Hypothesen sind keine automatisch berechneten Strategie-Messwerte.

**ANDY-Score** bleibt als numerischer Gesamtscore **OFFEN**, bis seine Komponenten nachvollziehbar berechnet und validiert sind. Match-Resultate und messbare Execution-Kennzahlen können bereits separat veröffentlicht werden.

## Entscheidungsprinzip / Definition of Done

Eine Serie gilt als abgeschlossen, wenn:
- Matchdaten und Konfiguration vollständig referenziert sind,
- sportliche Ergebnisse und technische/AQP-Entscheidungen getrennt vorliegen,
- Lab-Kennzahlen aus den Rohereignissen nachgerechnet werden können,
- Farbanordnungen und Budgets korrekt ausgewiesen sind,
- Kosten und Erkenntnisgewinn eine nachvollziehbare Stop/Go-Entscheidung erlauben,
- die Dokumentation mit der tatsächlichen Game-/Lab-Implementierung übereinstimmt.

**Grundsatz:** ANDY garantiert gleiche, vorab definierte Prüfregeln – **nicht** dieselbe Anzahl an Partien.

---

### Verweise
- [ANDY-Dokumentation V0.9 Beta](https://andy-arena-com.github.io/andy-wps-collaboration/andy-dokumentation-regeln-lab.html)
- [Projekt-README](README.md)
- [Dokumentations-Checkliste](WPS-02-CHECKLIST.md)
- [Testfälle](tests/)
