# 01 — Product Requirements / ANDY Behavior Model Card V1.0

**Status:** abgestimmte Produktleitlinien + auszuarbeitende technische Anforderungen, keine App-/WordPress-Implementierung. Must = fachliche Abnahmebedingung einer späteren V1.

## 1. Problem und Nutzerwert

Reale ANDY-Partien liefern eine ungewöhnlich dichte Abfolge aus API-Entscheidungen, ausgeführten Schach-/Go-Aktionen, Zeit, Ressourcen, Fehlern und Kontext. Ohne einen **standalone, kumulativen Modellblick** bleiben diese Daten über Einzelmatch, Replay, Lab und Journal verstreut. Die Card führt sie zu einem lesbaren empirischen Profil zusammen, verlinkt die Quellen und macht Grenzen der Erhebung sichtbar.

**Zielgruppen:** interessierte Öffentlichkeit, Unternehmen mit KI-Anwendungsinteresse, Forschende, Journal-Leser und die menschliche Projektleitung. Eine Card allein erbringt **keine** validierte Business-Eignungsprüfung eines Modells.

## 2. Kernentscheidungen

**BMC-R01 – Ein Subjekt pro Card (Must).** Eine Version/Modellidentität pro Card, je nach Evidenz ausdrücklich als historischer Modellname ohne nachgewiesene Endpoint-/Checkpoint-Identität. Kein direkter Vergleich mit anderen Modellen und keine „Top X“- oder übergreifenden Score-Karten. Gegner nur ausklappbar unter Matchkontext.

**BMC-R02 – Nur echte dokumentierte Spiele (Must).** Keine synthetischen Matchzahlen, erfundenen Geschwindigkeiten oder Demo-Fakten in als real gekennzeichneten Cards. Konzept-/Demo-Modi permanent unmissverständlich markiert.

**BMC-R03 – Kumulative Spielhistorie (Must).** Anzahl eindeutiger *logischer Partien*, Zeitraum, Kohorten-/Ruleset-/Konfigurationsmix, Anzahl Entscheidungen und ausgeführter Aktionen; Historie nach Datum und Konfiguration filterbar. Self-play zählt als **eine Partie** und ggf. zwei Rollen/Teilnahme-Spuren, nicht als zwei Partien.

**BMC-R04 – Geschwindigkeit (Must).** Eigene aufsummierte API-Latenz der Modellereignisse, Aktionen je Stunde *eigener aktiver API-Zeit*, API-Aufruf-Zeit p50/p95 und ggf. Spielwandzeit separat. Erhebungsabdeckung in Partien und Entscheidungen sichtbar. Keine naive Division aller Aktionen durch die gesamte Spieldauer.

**BMC-R05 – Ressourcen und Input/Output (Must).** Input-Tokens, Output-Tokens, Output/Input als Verhältnis, Input-/Output-Werte pro API-Entscheidung bzw. ausgeführter Aktion mit Nenner; wahlweise im Spielverlauf und nach Phasen (Setup/Schach/Go), wenn eindeutig protokolliert. Reasoning/Cache getrennt, providerspezifisch, keine Doppelzählung. Kein Rückschluss „kurzer Output = wenig Thinking“.

**BMC-R06 – Regelkonformität und Handlungsfähigkeit (Must).** API-Entscheidung ≠ ausgeführte Aktion ≠ Fehlversuch. Nichtausführung aus dem Grundprotokoll klassifizieren (z. B. illegal, JSON/Format, Cutoff/Outputlimit, Budget, Adapter, Core-Rejection, unbekannt), andernfalls „ungeklärt“ statt automatisch „illegal“. Setup-Ausführung, Schach-/Go-Aktionsverteilung und Ergebnisse nur nach Evidenzstatus. Retry-Vorgänge erhalten.

**BMC-R07 – Evidenzkompass (Must).** Drei *separate* Elemente: (a) Beobachtungsumfang und Konfigurationsabdeckung, (b) empirische Stabilität ausgewählter Kennzahlen innerhalb sinnvoller, ausreichend großer Kohorten, (c) Zeit-/Kostenaufwand der Datenerhebung. **Kein eigener Evidenz-Gesamtscore, keine Sterne, kein degradierendes Qualitätslabel für wenige Partien.** Dokumentieren, dass bestimmte Modelle wegen langer API-Zeiten/hoher Kosten seltener gespielt werden können; dies ist Erhebungsbedingungen, nicht Modellschelte.

**BMC-R08 – Versuchsbedingungen (Must).** Pro Match: Datum, Match-/Serien-/Segment-ID, Spielpartner als Kontext, Farbe/Rolle, Rule-/Engine-Version oder unbekannt, Modell-ID/Route sofern belegbar, Strategie, Tokenbudget, Output-Cap, Reasoning-Effort, Awareness, Retry-Limit, max Decisions, Setup/Go-Zuggruppe und zusätzliche relevante Faktoren. API-/Providerlinks belegen nicht den konkreten Endpunkt. Das System kann unterschiedliche Bedingungen anzeigen, aber keine naive gemeinsame Kausalinterpretation vorgeben.

**BMC-R09 – Herkunft und Prüfung (Must).** Jede Kennzahl hat Messdefinition, Einheit, Grundgesamtheit, zugrunde liegende Matches, Coverage, Quellenhashes bzw. gekennzeichnete historische Sekundärbelege, Parser-/Metric-/Rulesetversion und Status: BEOBACHTET, BERECHNET, INTERPRETIERT, OFFEN. Runner-Resultat und unabhängig engineverifiziertes Resultat getrennt.

**BMC-R10 – Theoretische Felder getrennt (Must).** Die vorhandenen Konzepte Dynamic Bonoma (Passung Strategie/Execution und Punch/Reorganisation), Sweet Spot? (situative Ressourcenpassung, Under-/Overthinking), Stabilität A/B/C, SSA/Antizipation, Recovery/Kollaps und Nested Networks bleiben **revidierbare Forschungsfragen**. Automatische Einstufung erst bei definiertem Verfahren, Gegenbeispielen und separater Freigabe; standardmäßig „noch nicht untersucht“.

**BMC-R11 – Quellen-Drill-down (Must).** Vom aggregierten Fakt zur einzelnen logischen Partie, vom Match zur Match Story und bei belegter Funktion zu Replay Event X; keine erfundenen Deep-Links. Quellenzugang kann privat bleiben; dann nachweisbare Metadaten statt öffentliche JSONL anbieten.

**BMC-R12 – Historische Snapshots (Must).** Neue Partien ändern abgeleitete Live-Projektion, aber nicht ältere, freigegebene Story/Social-Snapshots. Schema-, Metrik- und Quellversion speichern; Korrekturen als neue Revision, nicht als unbemerkte Veränderung.

**BMC-R13 – Public Content (Must).** Für Journal DE/EN getrennte redaktionelle Textfelder, gemeinsame Faktengrundlage und Bildreferenzen. Teaser/Social: eine belastbare Beobachtung, die zur Card und von dort zur Partie führt; keine Rankings, keine nicht belegten Übertreibungen.

**BMC-R14 – Sicherer Datenfluss (Must).** App: read-only Export aus bereits existierender Evidence-/Metric-Engine. WordPress: validierter manueller JSON-Import in Staging, idempotent, Rollback, Review/Launch Control vor Veröffentlichung; keine zweite unabhängige Spielwahrheit.

**BMC-R15 – Nutzbare V1-Oberfläche (Must).** Übersicht, Spieltempo, Ressourcen, Verhalten, Evidenz; interaktive Filter, erklärende Tooltipps, Mobile/Keyboard/Accessibility, Nullzustände, Provenienz und Quellen. Keine analytischen Diagramme mit Fantasiewerten.

**BMC-R16 – Universeller Info-Expander „Warum ANDY? Die gemeinsame Herausforderung“ (Must).** Jede veröffentlichte Behavior Card für allgemeine KI-Modelle enthält vor oder unmittelbar bei den Hauptkennzahlen einen standardmäßig geschlossenen, barrierefreien, responsiven **DE/EN-Expander** mit gemeinsamer Aufgabenidee (kombiniertes Schach+Go, Regeln und Zustand, Handlungen, Ressourcen, zugelassene Tools), verifizierten Dokumentationslinks und ausdrücklich begrenzter Business-Analogie. **Gleicher Regelrahmen ≠ identische effektive Bedingungen; eine tatsächlich völlig unbekannte Vortrainingserfahrung ist nicht beweisbar.** Allgemeine redaktionelle Inhalte zentral/versioniert im bestehenden WP-Content-/WHY-System verwalten, **nicht in jede modellbezogene APP-JSON kopieren**. Für Spezial-/Zufallsreferenzen andere Darstellung oder keine GPAI-Einführung. Volltext, Links und Tests [in der Expander-Spezifikation](08_GEMEINSAME_HERAUSFORDERUNG_INFO_EXPANDER.md).

## 3. Explizite Nicht-Ziele

- Kein Modellvergleich, Anbieter-Ranking, universeller Intelligenz- oder Leistungsscore.
- Keine automatische Diagnostik interner „Denkqualität“, kein vermuteter Anbieter-Reasoning-Anteil aus fehlenden Daten.
- Kein produktiver WP-Plugin-Neubau, keine Live-Änderung, kein App-/DB-Umbau als Folge dieses Dokuments.
- Keine Realzeit-Synchronisation in V1, keine automatische Veröffentlichung oder Social-Posting.
- Keine Übertragung von ANDY-Kennzahlen als objektive Business-Produktivitäts-, Security- oder Compliance-Eignung.
- Kein Zugriff auf geheime Providerkonfiguration, keine API-Keys, keine Roh-Prompts/privaten Gedanken/Personendaten im Public Export.
- Keine erneute Aufwertung historischer KO/TKO/ABORT-Ergebnisse durch neuere Rulesets.

## 4. P0/P1 nach vorhandener Architektur

**P0 – V1 manueller Pilot:** Schemaentwurf finalisieren, Exporter read-only, ein echtes Modellprofil über mindestens 2–5 eindeutige Partien, fehlende Zeiten offenlegen, Offline-Renderer/Journal-Staging, QA + Redaktion. Bereits existierende Data-/Evidence-Projektion wiederverwenden; keine Blockade durch unrettbare Altfälle.

**P1 – evidenzbasiertes Wachstum:** Zeitverteilungen über mehr Spiele, phasen-/situationsbezogene Zeit- und Tokenverläufe, Event-Drill-down, stabilitätsbezogene Zeitreihen nur bei definierter Kohorte, manuell geprüfte Bonoma-/Sweet-Spot-Fälle, Aftermatch-Kommentare als neue Sekundärdaten, Social-Visual-Export mit Snapshotbindung.

**P2 – optionaler Sync:** kontrollierte inkrementelle App→WP-Übernahme mit Revision/Preview/Approval; kein unkontrollierter automatischer Live-Publish.

## 5. Definition of Done für V1

1. Dieselbe Match-Auswahl ergibt deterministisch dieselben Zahlen und Quellen-IDs; validierte Rechenformeln sind dokumentiert.
2. Drei Grenzen explizit erkennbar: *eigene aktive API-Zeit vs. Matchdauer*, *Modelloutput vs. Reasoning*, *Zahl Partien vs. Robustheit/Aufwand*.
3. Kein Vergleichsranking und keine automatische Bonoma-/Overthinking-Kategorisierung.
4. Mindestens ein dokumentierter Problemfall zeigt korrekt `null` und Abdeckung statt 0/geschätzter Zahl.
5. Self-play, Resume-Segmente, Refund, historische Version, Fehlerklassen, partielle Quellen und Replay-Link-Fehlen bestehen Regression.
6. WP-Staging-Import ändert keine anderen Plugins, Posts, Sprachpartner, Originaldateien oder Live-Daten.
7. Redaktion/Projektleitung hat konkrete öffentliche Zahlen, Metaphern, Quellen und Datenschutz freigegeben.
8. Jede allgemeine KI-Card hat den redaktionell freigegebenen DE-/EN-Info-Expander, überprüfte Kapitel-Links und klare Kennzeichnung der Business-Analogie.
