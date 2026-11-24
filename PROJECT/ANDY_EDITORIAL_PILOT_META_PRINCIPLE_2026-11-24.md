# ANDY / JOURNAL — Editorial Meta-Prinzip: Der Weg ist das Ziel

**Stand:** 24.11.2026.  
**Anlass:** Erster unabhängiger Pilot mit Editorial Bible v0.1, Originalpaar `andy_a832963b7e60.jsonl` + `.json`, Matchreport, maschinenlesbarer Storyentwurf, Wissens-/Lückenbericht und individuell erzeugtes Naturmotiv. Der Projektleiter stellt fest: Das Bild erinnert trotz anderer Tierarten stark an die bereits vorhandenen Bildreferenzen (zwei gegenübergestellte Wasservögel, Ufer/Wasser, Schach-/Go-Signatur).  
**Status:** Produkt- und Forschungsgedanke, **keine Manual-Freigabe, kein Code-, Plugin-, WordPress- oder Lab-Umbau**.

## Leitsatz

> **Jede Match Story ist zugleich ein Experiment darüber, wie eine KI aus sportlichen Primärdaten eine Erzählung, eine Interpretation und eine Bildmetapher erzeugt.**

**Der Weg ist das Ziel:** Nicht nur das Ergebnis der Partie und der publizierte Text sind interessant, sondern auch die Entstehung des Textes/Bildes, die Möglichkeiten und Begrenzungen der Redaktions-KI, ihre Fehler, Wiederholungsmuster, Quellenabhängigkeiten und redaktionellen Korrekturen.

Das bedeutet **nicht**, dass die redaktionelle Veröffentlichung zum ungesicherten Live-Experiment wird: Die normale Match Story bleibt verständlich und quellenorientiert. Der Entstehungsprozess ist als *separate, versionierte Meta-Evidenz* sichtbar/auswertbar, z. B. in einem Hintergrundkapitel oder Forschungsbericht.

## Zwei unabhängige Prüfpfade

1. **Spiel-Evidenz / Faktentreue:** `<match-id>.jsonl`, `<match-id>.json`, Event-Reihenfolge, Actions vs. Attempts, Rule-/Engine-Version, berichteter vs. unabhängig verifizierter Ausgang, Datenlücken, Herkunft von Kennzahlen und Schlüsselszenen. Jeder überprüfbare Claim benötigt einen Event-/Feldbeleg. Fehlende Belege werden nicht kreativ ergänzt.
2. **Redaktionelle Leistung / kreative Eigenständigkeit:** Verständlichkeit, Spannungsbogen ohne Fiktionalisierung, faire Modellsicht, präzise Auswahl, sprachliche Vielfalt, **neu aus dem Match abgeleitete Bildmetapher** statt bloßer Wiederholung der Visual-Bible-Referenz.

**Nicht vermischen:** Eine spannende Story kann sachlich falsch sein; ein belegter Bericht kann langweilig sein; ein schönes Bild kann generisch oder referenznah sein. Kein einziger pauschaler „Qualitätsscore“ überdeckt diese Dimensionen.

## Konkreter Befund: Bildreferenz als kreativer Anker

**Beobachtet:** Manual Referenz 02 zeigt Kraniche, Wasserlandschaft, Gegenposition und Schach-/Go-Elemente; Pilotvisual zeigt weißen Reiher und Graureiher, Wasserlandschaft, Gegenposition, eine Schachfigur und Go-Steine. Unterschiedliche Arten und Lichtstimmung, aber wiederkehrende grundlegende Komposition/Symbolik.

**Hypothese, noch nicht kausal verifiziert:** Eine detaillierte visuelle Referenz kann als **Kompositionsanker** wirken, obwohl die Anweisung ausdrücklich freie Tierwahl und keine festen Avatare fordert. Alternativer Grund: Konfrontationsmotive und Schwarz-Weiß-Gegensätze gehören zu naheliegenden konvergenten Bildkonventionen; einzelne Probe ist kein Beweis von Referenzkopie.

**Konsequenz:** Eine weitere Iteration sollte prüfen, ob die Pilot-Bildidee **aus einem konkreten Spielmerkmal** stammt (z. B. sich mehrfach neu ordnende Go-Grenzen vs. abruptes Ressourcenende) oder lediglich die generische Polaritätsästhetik wiederholt.

## Minimaler reproduzierbarer Test (kein Featureauftrag)

Gleiche Originalpartie, gleiche Faktenbasis, keine neue kostenpflichtige Partie:

- **Bedingung A (Baseline):** bestehende Editorial Bible inklusive Beispielbilder — Output archivieren.
- **Bedingung B (abstrahierte Art Direction):** identische Stil-/Qualitätsvorgaben, Referenzbilder aber nur als Kriterienliste ohne konkrete Tierarten/Szenen — Output vergleichen.
- **Bedingung C (ereignisgetriebene Bildidee):** vor Generierung in 2–3 Sätzen genau **ein nachgewiesenes Spielmotiv** begründen, dann Komposition bewusst anders als bisherige Referenzen wählen — Output vergleichen.
- Bei Modell-/Prompt-/Laufzeitabweichung den Vergleich als *explorativ*, nicht als kausalen Nachweis kennzeichnen. Keine zwingende dreifache Generierung und kein unkontrollierter API-Kostenlauf.

**Vergleich separat für:** Faktentreue der Story, Quellenlücken, Szenenwahl, Eigenständigkeit des Titels, visuelle Motiv-/Kompositionsdistanz zu bisherigen Bildern, Wiedererkennbarkeit als ANDY, Art-Direction-Treue, Thumbnail-Lesbarkeit. Menschliche Bewertung mit konkreten Gründen und möglichen Gegenargumenten; kein behaupteter objektiver „Neuheitswert“ ohne definierte Messmethode.

## Minimaler Meta-Record je Pilot

**Nur vorhandene Angaben / unknown explizit:**
- `pilot_id`, `match_id`, `source_jsonl_sha`, `source_json_sha`;
- `editorial_bible_version`, `ruleset_reference` und `knowledge_context` (z. B. Thread mit ANDY-Vorwissen vs. frischer Thread);
- `text_model`, `image_model` soweit nachweisbar, Datum, Prompt-/Parameterreferenzen soweit verfügbar;
- Versionen/Hashes der **Outputs**: Report, Story-JSON, Visual, Wissens-/Lückenbericht;
- `claim_checks`: Evidenzstatus je wichtiger Behauptung, nicht bloße Gesamtwertung;
- `visual_checks`: Matchbezug, visuelle Ähnlichkeit zu Referenzen/Vorarbeiten, Bildprovenienz;
- `review`: menschliche Beobachtungen, konkrete Revisionen, freigegeben/noch offen.

**Keine Offenlegung privater interner Reasoning-Inhalte einer KI als Modellwissen behaupten.** Das nachvollziehbare Artefakt ist das *sichtbare Vorgehen* (Inputs, spezifizierte Prompts, erzeugte Zwischenausgaben, Änderungen und Bewertungen).

## Bezug zum ersten Pilot

- **Belegbares Spiel-Narrativ:** `andy_a832963b7e60`, Gemini 3.8 Flash (Weiß) vs. Claude 5.5 (Schwarz), 129 API-Entscheidungen, 122 tatsächlich ausgeführt, am Ende `termination=budget_overshoot` und `game_result=null` im JSON-Bericht.
- **Redaktioneller Erkenntnisgewinn:** präzise, ungewöhnliche Go-Kontrollverschiebungen und Budgetgrenze als erzählbare Episoden, ohne erfundenen Sieger.
- **Meta-Erkenntnis:** gute Quellenorientierung ist **nicht gleich** originelle Bildsprache. Die Ähnlichkeit des Visuals zu den im PDF enthaltenen Naturreferenzen gehört explizit in die Pilot-Nachbetrachtung; nicht stillschweigend als „neues Motiv“ abhaken.
- **Regelgrenze:** Passenden historischen Ruleset-Stand und aktuelle Implementierung separat prüfen; nicht v1.2 auf historische Partien zurückprojizieren.

## Beziehung zu Analyzer, Journal und Lab

- **Arena:** produziert Match-Evidenz, Originale bleiben unverändert.
- **Analyzer:** betrachtet Spielmuster **und** methodische Qualität der erzeugten Interpretationen; keine neue unabhängige Match-Wahrheit.
- **Journal:** wählt, editiert und publiziert nur nach redaktioneller Freigabe. Teaser können Interesse wecken, ohne Forschungsergebnis vorwegzunehmen.
- **Meta-Ebene:** dokumentiert explizit, welche KI und welches Briefing welche Outputs lieferten und was ein Mensch korrigierte. Ggf. als „Wie diese Story entstand“ in späterer Research-/Journal Edition, **nicht als Pflichtkachel im Home-Teaser**.

**Keine Implementierung aus diesem Beschluss ableiten.** Erst den bestehenden Piloten bewerten, die Manual-Versionen kontrolliert variieren und im nächsten unabhängigen Test feststellen, was besser/weniger gut funktioniert.

**Ziel:** **Erleben. Erforschen. Erahnen.** Nicht die Illusion perfekter automatischer Redaktion erzeugen, sondern den Prozess nachvollziehbar, lernfähig und überraschungsoffen gestalten.
