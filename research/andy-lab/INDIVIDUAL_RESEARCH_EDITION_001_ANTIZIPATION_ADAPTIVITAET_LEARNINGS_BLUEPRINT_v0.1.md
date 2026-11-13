# ANDY Lab – Individual Research Edition 001: Did They See It Coming?
**Anticipation, Adaptive Response and Learning Signals in an AI Strategy Duel**

**Stand:** 13.11.2026 · **Status:** verbindliche fachliche Priorisierung / Forschungs-Blueprint; keine abgeschlossene Fallvalidierung  
**Referenz:** Astra (Weiß) vs Claude Opus 5.5 (Schwarz), Match `andy_64c8f95436d1`  
**Übergeordnet:** [ANDY Masterplan](../../PROJECT/ANDY_GESAMTKONZEPT_MASTERPLAN_v1.0.md) · [Lab-Memo](ANDY_LAB_MEMO_Intentions_Antizipation_Responsivitaet_v0.1.md)  
**Spätere Vergleichsstudie:** [Comparative Research Edition 001 – 24 Seiten](COMPARATIVE_RESEARCH_EDITION_001_24_SEITEN_BLUEPRINT_v0.1.md)

## Entscheidungsanker

**Priorität 1 = tiefgehende Analyse EINER vollständigen Partie.** Nicht zuerst mehrere Match-Summaries oder Rankings. Kernfokus: (1) korrekte Antizipation, (2) adaptive Reaktion, (3) Lessons / beobachtete Anpassungen. Erst wenn diese Methodik robust ist, wird sie für Matchvergleiche wiederverwendet. Der bestehende **24-seitige Comparative-Blueprint bleibt erhalten**, ist aber der nachgelagerte Schritt.

## Forschungsfragen & Prüfbarkeit

### F1 – Korrekte Antizipation
- Welche spezifischen Aussagen über gegnerische Züge, Reaktionen, Risiken, Folgezustände und Ergebnisse sind in den Modelltexten nachweisbar?
- Welche treten im angegebenen Zeithorizont ein, welche nicht, welche bleiben unbestimmt?
- Unterscheide **richtige Vorhersage** von „erzwungener Fortsetzung“: erzwungen nur nach legaler Alternativenprüfung.
- Claim-Einheit: Textspanne, Match-/Event-ID, Bedingung, Horizont, erwartete Beobachtung, tatsächliche Beobachtung, Prüfstatus.

### F2 – Adaptive Reaktion
- Welche Zustandsänderung/überraschende Gegneraktion war vor einer Modellentscheidung sichtbar?
- Welche früher dokumentierte Absicht/Prognose wurde dadurch bestätigt oder widerlegt?
- Hat das Modell einen bestehenden Plan beibehalten, modifiziert oder aufgegeben? Nur bei ausreichender protokollierter Evidenz als Anpassung codieren.
- War der beobachtete Zug legal, zielgerichtet, auf Gefahr bezogen? Alternativen und taktische Qualität erst mit regel-/enginebasiertem Nachweis beurteilen.
- Kein „nicht adaptiv“ aus dem bloßen späteren Verlust ableiten; ein Zug kann bereits erzwungen sein.

### F3 – Learnings
Drei strikt getrennte Bedeutungen:
1. **Retrospektive Forschungs-Learnings**: Was lernen die Autoren/Analysten über beobachtbares Verhalten und die Untersuchungsmethode?
2. **In-Context-Anpassung**: Ändert ein Modell im Verlauf aufgrund neuer Beobachtungen seine Aussagen oder Handlungen? Nur aus sichtbaren Ereignissen schließen.
3. **Persistentes Modelllernen**: Veränderung von Parametern/Gewichten oder nachhaltiger Fähigkeit **wird durch einzelne API-Matches nicht belegt** und erfordert unabhängiges Training und Follow-up-Evaluation.

## Vollständiges Match statt Schlussphase allein

1. Zunächst sämtliche Eventtypen (API-Entscheidung, legaler Zug, Formatfehler, illegaler Zug, terminal) rekonstruiert und gezählt.
2. Für **jede** relevante Modelläußerung prüfen, ob konkret testbare Claims vorliegen; keine erfundene Intention aus generischen Floskeln ableiten.
3. Zeitachse der Claims, Gegneraktionen, Strategieänderungen, Go-Kontrolle, Chess-Entwicklung und Tokenkosten.
4. Mehrere Fallfenster aus früher, mittlerer, später Partie **nach transparenten Auswahlkriterien**; nicht ausschließlich Bestätigungsfälle.
5. Späte signifikante Episode als Pilot: #139 (Angriffsidee), #141 (Springerzug), #143 (konkrete konditionale Prognose), #145 (Gefahrenerkennung), #146 (Go-Zug), #147 (Matt); Zwangslage/Alternativen zunächst offen.

## Analyseraster pro Episode

| Feld | Inhalt |
|---|---|
| Ausgangslage | Vorzustand, Sichtbarkeit im API-Prompt, Spielsituation |
| Frühere Strategie | belegter früherer Claim, nicht zugeschriebener „Gedanke“ |
| Erwartung | explizit angekündigter Zug/Gegnerreaktion/Ergebnis mit Zeithorizont |
| Neuer Reiz | tatsächlicher Gegnerzug, Fehler, unerwartete Lage |
| Reaktion | ausgegebener Zugversuch, Legalität, Ausführung, neue Modelläußerung |
| Anpassung | Fortsetzung/Revision/Aufgabe/unklar; Kriterien und Evidenz |
| Konsequenz | nachfolgende Ereignisse; lokal und match-global getrennt |
| Validierungsstatus | protokolliert / engine-geprüft / Interpretation / offen |
| Gegenhypothese | z. B. bereits erzwungene Lage, abweichende Priorität, fehlende Information |

## Vorgeschlagene Individual-PDF-Struktur (Ziel 20–24 Seiten)

| Kapitel | Richtwert |
|---|---:|
| Titel, Abstract und Kernaussagen | 2 |
| ANDY-Regeln, Matchkonfiguration, Methode und Datenbasis | 3 |
| Kompletter Spielverlauf: Chess, Go, Ressourcen | 3 |
| Antizipationsanalyse inkl. Claims und Treffer/Nichttreffer | 4 |
| Adaptive Reaktionen auf Überraschungen/Planabweichungen | 4 |
| Ausführliche Ereignisfallstudien mit Brettdiagrammen | 4 |
| Learnings, Gegenhypothesen, Limitationen | 2 |
| Quellen, Reproduzierbarkeit, Datenfelder / Ausblick | 2 |
| **Ziel** | **24** |

Seitenzahlen sind **Redaktionsbudget**, keine Aufforderung zu Leerraum oder Scheinevidenz. Grafiken und Behauptungen nur aus geprüften Daten. Keine psychologischen Aussagen über Modellbewusstsein.

## Datenpipeline zuerst, aber frühes „erlebbares“ PDF

- Original-JSONL mit Hash sichern; Ruleset/Engine-Version, Prompt, Modellversionen, Entscheidungen/Fehler dokumentieren.
- Ereignisse und Claims normalisieren, Claims mit exakten Eventreferenzen belegen; Grenzen/Evidenzstatus im Bericht zeigen.
- Bereits im Pilot eine visuell attraktive Research Edition mit echten Brettern, markierten Episoden, Zeitachsen und Gegenhypothesen erstellen; ungelöste Prüfungen sichtbar markieren.
- Das PDF **und** ein maschinenlesbares Dossier aus derselben Datenbasis speisen.
- Publikations-/WPS-Gates sind getrennt von einer internen Preview.

## Qualitäts-Gates für die erste Edition

- Keine Antizipations-Trefferquote ohne dokumentierte vollständige Stichprobe, Ein-/Ausschlüsse und Prüfmethode.
- Keinen Strategie-Lernzuwachs aus einem Einzelfall behaupten.
- Keine nachträgliche Siegerlogik; auch widersprechende Cases und erkannte Fehlschlüsse zeigen.
- Keine Kausalbehauptung zur Niederlage oder zum „entscheidenden Fehler“ ohne Alternativenprüfung.
- Separate Label: **Datenbefund**, **Regelvalidierung**, **Interpretation**, **offene Frage**.

## Nächster Schritt

**M0:** Original-JSONL `andy_64c8f95436d1` und dazugehörige Engine/Ruleset-Version inventarisieren; dann **Ereignis-/Claim-Extraktion über die gesamte Partie** mit nachvollziehbarer Klassifikation. Die finale Comparative Edition folgt erst nach Validierung dieses Individual-Ansatzes.
