# ANDY Lab – Externer KI-Review: Astra × Claude Opus 5.5
**Stand:** 13.11.2026 · **Status:** überlieferter KI-Review, **nicht unabhängig validiert**  
**Match-ID:** `andy_64c8f95436d1`  
**Quelle:** Vom Projektleiter in den ANDY-Lab-Thread kopierter Text eines separaten Claude-Chats; darin bezeichnet sich das prüfende Modell als „Sonnet 5.5“. Original-Chat/Tool- und Rechenartefakte noch nicht im Repository vorliegend.  
**Verwendung:** Validierungs-Backlog für [Individual Research Edition 001](../INDIVIDUAL_RESEARCH_EDITION_001_ANTIZIPATION_ADAPTIVITAET_LEARNINGS_BLUEPRINT_v0.1.md), kein freigegebener Forschungsbefund.

> **Grundsatz:** Ein Claude-Review über ein Claude-Opus-Match ist eine interessante zweite Perspektive, aber keine regelbasierte oder statistisch unabhängige Prüfung. Keine pauschale Gleichsetzung von Modellidentität, Reasoning-Parametern, „Brute-Force“-Behauptung und vollständig reproduzierbaren Prüfungen.

## 1. Zugriffsbeobachtung (separat von Matchanalyse)

Claude berichtet, die aktuelle deutsche Website `andy-arena.com` gelesen zu haben und konkret aktuelle Inhalte (Demo-Konfiguration, 249 API-Entscheidungen und 233 ausgeführte Züge, 16 Fehlversuche, fehlender Claude-Demoeintrag) erkennen zu können. Gemini dagegen berichtete, nur einen älteren Suchindex-Stand („ANDY — Das geteilte Brett“) gelesen zu haben; der vorliegende Assistent konnte die Domain in früheren externen Abrufen nicht zuverlässig erreichen. **Dies beweist keine universelle Erreichbarkeit oder Nichterreichbarkeit**; die Zugriffs- und Toolkontexte können sich unterscheiden. Für Windows-TLS-Diagnose vgl. [Windows-SSL/TLS-Issue #3](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/3).

Claude lobt die Unterscheidung Daten/Interpretation, offene Superlativformulierung, Token-/Reasoning-/Retry-Konfigurationsdemo und Trennung API-Entscheidungen/ausgeführte Züge. Bemerkungen: kein Claude-Demoeintrag; Ergebnis erst nach Replay; Testfassung/nicht indexiert, Datenschutztexte im Ausbau. Diese Aussagen sind **Review-Beobachtungen**, keine technische Funktionsprüfung oder Veröffentlichungsgenehmigung.

## 2. Vom Nutzer übermittelte Matchanalyse (Aussagen des Reviews)

### Matchdaten (gegen Original-JSONL überprüfen)
- Astra Weiß gewinnt laut Reviewer in Runde 33 durch Schachmatt, Partie 55m29s.
- Beide Spielseiten: `master`, A2, 350.000 Token-Budget.
- 147 Entscheidungen; 145 ausgeführte Züge laut bisherigem Lab-Memo.
- End-Go-Kontrolle: 39 (Astra) : 42 (Claude).
- API-/Tokenwerte laut Reviewer:

| Kennzahl | Astra | Claude Opus 5.5 |
|---|---:|---:|
| Token gesamt | 126.808 | 190.145 |
| Output | 65.694 | 83.603 |
| API-Zeit (Sek.) | 2.356 | 973 |
| Fehlversuche | 0 | 2 |
| Ausgabeformat | 73/73 „strikt“ | 56/74 mit Markdown-Fences laut Reviewer |

**Achtung:** „56 von 74 mit Fences“ und „0 Fehlversuche“ betreffen unterschiedliche Definitions-/Normalisierungsebenen; beide Angaben inklusive Nenner/Code durch Parser prüfen. „API-Zeit“ ist nicht automatisch Gesamtspielzeit, und die Modell-/Provider-spezifische Token-Semantik bleibt zu prüfen.

### Taktische Kernhypothese
Claude bezeichnet den schwarzen Zug `c5d3` (im bisherigen Memo Ereignis #141) als Fehler und behauptet:
- Vor diesem Zug seien **20 legale Schachzüge** möglich gewesen;
- **17 von 20** hätten ein Matt in zwei Zügen vermieden (als Beispiele nennt der Review `h6`, `g6` und Königszüge);
- die Prüfung sei „per Brute-Force“, aber **nur unter reinen Schachregeln ohne Go-Kopplung** durchgeführt worden;
- daher „flacher taktischer Fehler, kein strategischer“.

**Wichtige Einschränkung:** Kein FEN, Suchcode, genaue Perspektive/Zugfolgen oder Ausgabe des Brute-Force-Checks wurde mitüberliefert. Diese Zahlen und der Schluss „kein strategischer Fehler“ sind **offene, zu replizierende Claims**. Die Situation vor #141 und die nachfolgende Folge #143, #145, #147 getrennt prüfen. Insbesondere darf „17 vermeidende Züge“ nicht als ANDY-legale oder global optimale Optionen ausgegeben werden, solange Engine und Zugbedingungen nicht rekonstruiert sind.

### Fairness-/Konfigurationshypothese
Claude behauptet, bei Opus enthielten die API-Requests nur `model` und `max_tokens`, und `reasoning_tokens` sei `None`; Astra nutze je Zug ~850 nicht sichtbare Reasoning-Tokens, während Claude-Ausgabe sichtbar gewesen sei.
- **Test:** reale Request-Felder und Antwort-Usage/finish_reason je Provider, API-Version, Max-Output, Reasoning-Modi und effektive Promptinhalte aus Original-JSONL/Code prüfen.
- **Grenze:** Aus einem fehlenden Feld in einem gegebenen Log folgt nicht zwingend der genaue serverseitige Reasoning-Modus. Tokenzahlen über Provider hinweg nicht unreflektiert vergleichen.

### Format-/Logging-Hypothesen
- Zwei Claude-Fehlversuche im Go-Bereich mit `finish_reason=max_tokens`, einem abgeschnittenen JSON und einer leeren sichtbaren Antwort; nach Retry jeweils gültige Antwort.
- In diesen Fällen laut Reviewer `cap_hit:false` trotz `finish_reason=max_tokens` → **möglicher Feldsemantik-/Logging-Konflikt**, nicht automatisch Bug ohne Definition von `cap_hit`.
- Laut Review wird bei Opus Markdown-Fencing großzügig normalisiert. Unterscheiden: Rohantwort → normalisiert → parser-konform → legaler Spielzug → ausgeführt.
- Vorschlag: Fehlerklassifizierung und vollständige Audit-Timeline statt pauschaler „Formatgenauigkeit“.

## 3. Prüfpaket mit Prioritäten

| Prio | Frage | Benötigter Beleg | Status |
|---|---|---|---|
| **P0** | Stimmt Stellung vor #141, Zahl 20 legaler Züge und „17 vermeiden M2“? | Original-FEN, Ruleset/Engine, ausführbarer Suchcode, Alternativzüge | offen |
| **P0** | Können Astras vorausgesagter und Claudes gewählter Zug als *erzwungen* gelten? | FEN und legale Alternativen zu #143/#145, tatsächlicher Schach-/Go-Kontext | offen |
| **P0** | Wie sind `cap_hit` und `finish_reason=max_tokens` definiert? | Logger/Parser-Code, zwei konkrete Ereignisse, Request-/Responsefelder | offen |
| **P1** | Welche Reasoning-Einstellungen waren tatsächlich wirksam? | API-Request/Provider-Modellversion/Usage, Code | offen |
| **P1** | Wie viele Opus-Antworten hatten Markdown-Fences und wie wurden sie normalisiert? | Rohtext + Parser-Logs + Nennerdefinition | offen |
| **P1** | Erklärt beobachtete lokale Go-Zielerreichung die globale Entscheidung? | Board-Replay, Agentenprompts, Alternativen, Zielkonfliktanalyse | offen |
| **P2** | Welche Zugfolgen antizipierten beide Systeme über **alle** Spielphasen korrekt? | vollständiges Claim-Schema und Matchdurchlauf | geplant |

## 4. Relevanz für die Individual Research Edition

Die von Claude aufgeworfene **Taktik-vs-Strategie-Frage** macht den Individual-Fokus besonders ergiebig: Ein Modell kann Risiken erkennen, eine Antwort korrekt vorhersagen und dennoch in einem früheren Zug vermeidbar in eine schlechte Stellung geraten sein. Daraus darf nicht automatisch ein Schluss über Adaptivität/Reasoning-Fähigkeit gezogen werden. Untersuchen:
1. Was war zum jeweiligen Entscheidungszeitpunkt im Prompt sichtbar?
2. Welche konkrete Gefahr wurde im Text erkannt/übersehen?
3. Welche Handlungen waren im tatsächlichen ANDY-Regelraum legal?
4. Gab es realistische Alternativen, die den Endzustand verändert hätten?
5. Wie wurde die Reaktion danach sprachlich und faktisch fortgesetzt?

**Konsequenz:** Kein Sieger-Bias, keine Anthropic-/OpenAI-Hersteller-Voreingenommenheit, keine „Schwestermodell“-Sonderannahme. Der Review ist ein prüfbarer Fragenkatalog.

## 5. Veröffentlichung und Follow-up

- Nicht als unabhängig validierte Engine-Analyse zitieren.
- Vor einer PDF-/Journal-Veröffentlichung Originalzitate/Reviewer-Zuschreibung und Quellrechte prüfen.
- Quellenartefakte (Claude-Review, Original-JSONL, Auswertungsskript, FEN-Snapshots) jeweils mit Version, Hash und Freigabestatus versehen.
- Sobald verifiziert: einzelne Claims als **bestätigt / widerlegt / nicht entscheidbar** und mit exakten Belegen nachführen.

**Kurzfazit:** Der größte Wert dieses Reviews liegt nicht in einem vermeintlichen Urteil „taktisch statt strategisch“, sondern in den **konkreten reproduzierbaren Prüfaufträgen**, die daraus entstehen.
