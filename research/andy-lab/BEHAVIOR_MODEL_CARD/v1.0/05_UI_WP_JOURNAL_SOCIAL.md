# 05 — UI, WordPress, Journal und Social / V1

**Ausgangspunkt:** vorhandener **offlinefähiger HTML-Clickdummy V1** (25.11.2026, Gemini 4 Argon, 5 logische Spiele). Kein Live-Website-Feature. Journal besitzt bereits Match-Story-/Fight-Night-Templates, DE/EN, Content Composer, Launch Control und Staging-first-Verfahren. Zuerst vorhandene Komponenten auditieren und wiederverwenden.

## A. Card-IA / visueller Aufbau

**Top / Hero:** Modellname und Anbieter (Identitätstatus), eigene Kennzahlen (Partien, ausgeführte Aktionen, API-Entscheidungen, Datenstand), kurze belegte Beobachtung. **Keine gegnerischen Resultatbalken und kein Rang.**

**Universeller Intro-Expander unter dem Hero (BMC-R16):** „Warum ANDY? Die gemeinsame Herausforderung für allgemeine KI“. Initial zugeklappt, barrierefrei DE/EN; erklärt gekoppeltes Schach-Go als neu gestellte Aufgabe für allgemeine KI-Modelle, verfügbaren Werkzeugkasten, gemeinsamen Regelrahmen und individuell dokumentierte Voraussetzungen. Verweist auf die öffentliche ANDY-Dokumentation [Einführung](https://andy-arena-com.github.io/andy-wps-collaboration/andy-dokumentation-regeln-lab.html#intro), [Regeln](https://andy-arena-com.github.io/andy-wps-collaboration/andy-dokumentation-regeln-lab.html#rules), [Lab](https://andy-arena-com.github.io/andy-wps-collaboration/andy-dokumentation-regeln-lab.html#lab), [Komplexität](https://andy-arena-com.github.io/andy-wps-collaboration/andy-dokumentation-regeln-lab.html#challenge) und [AQP](https://andy-arena-com.github.io/andy-wps-collaboration/andy-dokumentation-regeln-lab.html#score). **Nicht behaupten**, dass Vorwissen und effektive Konfiguration identisch seien oder konkrete ANDY-Ergebnisse direkt Business-Fitness belegen. **Ein zentraler redaktioneller Baustein**, kein eigener APP-Messwert und keine wiederholte modellindividuelle Kopie. [Freigabevorlage, EN-Text und Linkprüfung](08_GEMEINSAME_HERAUSFORDERUNG_INFO_EXPANDER.md).

**Unter dem Hero bzw. direkt nach dem Expander: Evidenzkompass.** Drei visuell getrennte Felder: ① Umfang (z. B. 5 Partien, 2 dokumentierte Budgetgruppen), ② Stabilitätsbeobachtung (bei zu wenig vergleichbaren Partien: „noch nicht berechenbar“), ③ Erhebungsaufwand (z. B. API-Zeit 1/5 Spiele; geschätzte Kosten nur mit gültigen Tarifen). Kein Score/Schulnoten-Feeling.

**Tabs/Sections (Clickdummy-Parität):**
1. `Überblick`: eindeutige Spielhistorie, Zeitfenster, ausgeführte Aktionen, Spielumfang und Kennzahlen mit Coverage.
2. `Spieltempo`: eigene API-Zeit, Calls/Zeitraum, Aktionen pro aktiver API-Stunde; p50/p95 nur mit echten per Call-Werten; Gesamtmatchdauer ausdrücklich separate Größe.
3. `Ressourcen`: Input-, Output-, Reasoning-/Cache-Felder sofern vorhanden, `Output/Input`, Phasenprofil, eigener zeitlicher Verbrauch.
4. `Verhalten`: Ereignisbasierte, als **INTERPRETIERT** gekennzeichnete Bonoma-/Sweet-Spot-/Stabilitätsbefunde; bei fehlender Grundlage „noch nicht untersucht“.
5. `Evidenz`: Matchliste, Bedingungen, Prüfniveau, Quellen/Methoden, fehlende Werte, historische Version und Datenschutz.

**Grafikvorschläge:** eigener I/O-Zeitverlauf; eigene API-Latenz-Histogramme oder Zeitlinie; Aktionen pro Partie als einzelne Bars; Verteilung nach eigenen Spielphasen; Coverage- und Konfigurationsdiagramm; bei ausreichender homogener Stichprobe Stabilisierung einer *einzelnen* Kennzahl mit echten Wiederholungen. **Keine fremden Modellserien, kein Effizienzvergleich, keine fiktive Konfidenzkurve.**

**Interaktionen:** Tabnavigation, Filter nach dokumentierter Konfiguration, Zeit und Partie; auf Balken/Zeile klicken öffnet Matchdetails; bestätigte Match-Story/Replay-Landingpages; Quellen-Tooltip und inhaltlich passende Glossarbegriffe. Filter aktualisieren alle KPIs, Nenner, Coverage, Titel und Export; kein geheimer Vergleich. Mobile/Keyboard/Screenreader und druckbare Methodenansicht.

## B. Vom Social-Teaser bis zur Primärevidenz

```text
Instagram / LinkedIn (eine überprüfbare Beobachtung)
        ↓  Snapshot-ID + kanonische URL
Behavior Model Card (Standalone-Profil)
        ↔  Journal Match Story / Fight Night
        ↔  Original Replay, ggf. Event X
        ↔  ANDY Lab (Methodik, Bonoma, Sweet Spot)
```

**Teaser-Regeln:** eine echte, gut lesbare Zahl oder eine offene, konkrete Frage; Bezugsmenge (z. B. „aus 5 Partien“), Bedingungen bei relevantem Einfluss, Datenstand und Link auf vollständige Card. Instagram eher visuelle Kachel/Carousel, LinkedIn eher methodischer Kontext; **keine algorithmischen Anbieterurteile, keine „schneller als“-Claims**. Statische Social-Assets dürfen von derselben geprüften Snapshot-JSON erzeugt werden, müssen aber vor Versand redaktionell genehmigt sein.

**Einstiegsbeispiele (keine endgültigen Posts):**
- „Was verraten 5 dokumentierte ANDY-Partien über das Tempo von Gemini 4 Argon?“ (Tempoabdeckung **nur 1/5**, daher diese Grenze im Beitrag sichtbar).
- „Ein Modell, viele Aktionen: Wie verändern sich Input und Output über echte Spiele?“
- „Wie belastbar ist ein Verhaltensprofil, wenn viele weitere Partien sehr zeitaufwendig sind?“
Keine fiktionalen Einzelspiele oder erfundenen Budget-/Preiswerte als reale Schlagzeile.

## C. WordPress-Verantwortlichkeiten

**APP/Metric Engine:** Identifikation, Deduplikation, Verifizierung, Berechnung der Daten und des Evidenzstatus.  
**WordPress/Journal:** validierter Import/Referenz auf Snapshot, Darstellung, redaktionelle DE-/EN-Texte, Bilder, interne Links, Freigabe, SEO/Social-Vorschau. WordPress darf keine eigenen alternativen Spielregeln oder Ergebnisresolver erraten.  
**Lab:** methodische Interpretation und fallbezogene Research-Versionen, **keine automatische Label-Erzwingung**.

**Content-Pipeline:** *Content bestimmt Bereich/Gabelseite, Bereich bestimmt Home.* Behavior Card ist ein eigener Contenttyp oder vorhandene Composer-Vorlage **nach Ist-Audit**; keine parallele redundante Artikelverwaltung. Modellidentität, Match-Story-Bezüge und Sprachen stabil referenzieren. Gemeinsame Datenwerte für DE/EN, separat editierbare Texte; keine zwei divergierenden Zahlenbestände.

**Staging first:** `staging.journal.andy-arena.com` als Entwicklung; Live als separater öffentlicher Publikationsstand. Bestehendes **Launch Control / Veröffentlichungsgate**, Rollback und selektiver Stage→Live-Code-/Content-Prozess respektieren. **Kein Remote-DB-Write, keine Secrets im Export, kein ungefragter vollständiger Plugin-Deploy.** Staging-URLs vor Veröffentlichung nicht indexieren; WordPress-REST/Archiv/Feeds/Cache/Bild-Crops mitprüfen.

**Details-Akkordeon wie auf Fight Night:** `Versuchsbedingungen & Originale` für Ruleset, Engine, Modell, Route, Budget, Awareness, Limits, Match-IDs, Rohdatenzugang/Linkstatus, Code-Revision. „Anbieter-Dokumentation“ ist Orientierung und **kein Beweis** eines konkreten API-Endpoints.

## D. Canonical Navigation / Links

- Card → Match Story mittels ausdrücklich geprüfter `match_id`-Relation, bei fehlender Story nicht anzeigen.
- Match Story → Card bei Modellnamen (nur wenn Profil vorhanden und freigegeben), unabhängig von gegnerischer Profilverfügbarkeit.
- Szenen → Replay Event X nur bei realem unterstütztem Deep-Link; sonst zur belegten Replay-Landingpage mit Kontexttext.
- Card → ANDY Lab mit passender Forschungsfrage/Methodik, nicht mit halluzinierter Live-Auswertung.
- Stabile `slug`, `language`, `canonical_snapshot_id` und Revisionsstatus statt hart kodierter Hostingpfade. DE/EN-Routing und Homepage-Reihenfolge separat verifizieren.

## E. Social-/Journal-Ausgabe aus demselben Datensatz

Geplanter Social-Baustein ist **ein Export-Preset**, kein automatischer Posting-Bot:
`{snapshot_id, subject, fact:{value,unit,denominator,period,conditions,status}, source_url, review_status, locale, suggested_caption, image_alt, asset_ref}`.
Keine neue Quelle; Image-Layout darf visuell variieren, Zahlen bleiben identisch. LinkedIn-/Instagram-Text kann redaktionell zugespitzt werden, **ohne** eine hypothetische Bonoma-/Overthinking-Deutung als bestätigte Modelleigenschaft auszugeben.

## F. Perspektive: g-Signature und ACT-01-Bildsprache (Research, noch kein V1-Must)

Das Zeichen ist das vollständige **g-Netzwerk K₄** mit vier Knoten und sechs möglichen Relationen, kein beliebig deformiertes Marketinglogo. ACT-01 hat eine explizite visuelle Grammatik `P/S/C/K` und Leseversuche dokumentiert: **Kantenstärke 2px/8px** als eines von vier Codeattributen, in Experiment 002 drei Mal 17/17 Zeichen und 68/68 Parameter bei bekannter Grammatik; zugleich dokumentierte Wahrnehmungs-/Kontextfehler. **Das bestehende `K` ist ein Prüftrit, kein Verhaltenswert.** Eine spätere gewichtete sechs-Kanten-Behavior-Signature benötigt ein **eigenes versioniertes Schema**, real beobachtbare Relationen, eigene Null-/Coverage-Darstellung und unabhängige visuelle Decoder-Tests. **Nicht** als vorhandene validierte Spiel-/Strategie-Kennzahl darstellen. [Forschungsbrücke ACT 01 → Signature](09_G_SIGNATUR_ACT01_FORSCHUNGSBRUECKE.md).

## G. Journal-Thread-Schutz

Die aktuelle Fight-Night-Demo `andy-fn-demo-claude-grok-2` ist **fiktiv**, ihre Beispielkennzahlen und Illustration sind **kein reales Spiel**. Nicht als Datenquelle des App-Exporters verwenden. Bestehendes Editorial/WHY/Content-Composer/Freigabesystem erhalten; Behavior-Importer erst bei definiertem Auswertungs-/Sicherheitsgate.

**Relevante Bestandsdokumente:** [Journal-System und Status](../../../../PROJECT/JOURNAL/v1.1/STATUS.md) · [Journal-Match-Stories](../../../../PROJECT/JOURNAL/v1.1/docs/ANDY-JOURNAL-MATCH-STORIES-v0.4.md) · [Journal-WP-Plugin-Architektur](../../../../PROJECT/JOURNAL/v1.1/docs/ANDY-JOURNAL-PLUGIN-ARCHITEKTUR-v0.1.md) · [APP-Match-Evidenz](../../../../PROJECT/ANDY_MATCH_EVIDENCE_JSONL_JSON_SQLITE_v1.0.md).
