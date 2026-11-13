# ANDY Lab – Memo: unmittelbare Go-Spiegelantworten in drei Partien

**Datum:** 13.11.2026  
**Status:** Exploratives Forschungsmemo / **nicht unabhängig repliziert oder validiert** / **keine Priorisierung**  
**Quelle:** Vom Projektleiter übermittelte Auswertung eines Claude-Tests an drei verfügbaren Match-Logs (ca. 280 Go-Züge), einschließlich berichteter Zählungen und Permutationstests. Die ursprünglichen JSONL wurden **für dieses Memo nicht erneut eingelesen oder der Testcode geprüft**. Die Zahlen sind daher *berichtete Ergebnisse*, nicht eine eigene Reproduktion des ANDY Lab.

## 1. Motivation

Über mehrere vergleichbare ANDY-Partien wurden wiederholt visuell auffällige Go-Setzmuster beobachtet: zeitlich reaktive spiegelbildliche Antworten des zweiten Akteurs, teilweise nach horizontaler oder vertikaler Achse, beiden Diagonalen oder 180°-Drehung. Statische Brettsymmetrie ist dabei **nicht** automatisch zeitlich reaktive Spiegelung.

**Arbeitsfrage:** Treten unmittelbare Spiegelantworten häufiger oder in längeren Serien auf, als unter den tatsächlich legalen und vergleichbaren Spielsituationen zu erwarten wäre? Sind sie modell-, gegner-, farb-/rollen-, phasen- oder konfigurationsabhängig?

## 2. Berichtete Methode

Für jeden Go-Zug wurde geprüft, ob er einer der fünf geometrischen Abbildungen des **unmittelbar vorherigen gegnerischen Go-Zuges** entspricht: Horizontalachse (H), Vertikalachse (V), Hauptdiagonale (D), Gegendiagonale (D′), Rotation um 180° (R180). Die Namensgebung der Achsen ist konventionsabhängig und in implementiertem Code zu fixieren. Ein Treffer durch *irgendeine* Transformation zählt in der Sammelmetrik als Mirror Response. Setup und Haupt-Go-Phase werden getrennt.

Auswertung gegen eine Zufallsbasis aus **gemischten Antwortzügen**; diese Baseline bildet Setup-Regelzwänge nur teilweise ab und gilt **nicht** als bereits legalitätskonditionierte Nullverteilung.

## 3. Berichtete Ergebnisse aus nur drei Partien

| Partie | Go-Setup-Phase | Haupt-Go-Phase | Bemerkung |
|---|---|---|---|
| Astra – Opus | Opus **4/8**, Astra **5/7** | Opus **0/32**, Astra **4/31** | Setup auffällig, Hauptphase begrenzt |
| Astra – Argon | Argon **3/8**, Astra **6/7** | Argon **8/54**, Astra **1/53** | stärkste gemeldete Serien |
| Flash – Argon | **nicht auffällig** (Zahlen im übermittelten Auszug nicht spezifiziert) | **nicht auffällig** | negativer Vergleichsfall |

Auffälligste gemeldete Treffer gegenüber der verwendeten gemischten Antwort-Baseline:
- **Astra im Setup der Astra–Argon-Partie: 6/7**, berichtet **p≈0,002**.
- **Argon in der Haupt-Go-Phase gegen Astra: 8/54**, berichtet **p≈0,002**.

**Keine belastbare allgemeine Signifikanzbehauptung:** drei selektierte Partien, mögliche Mehrfachtests (Spieler × Phasen × fünf Transformationen × Fenster), innerhalb der Partie abhängige Züge, nicht vollständig regelkonditionierte Nullverteilung und fehlende Original-Testimplementierung. P-Werte nur als explorative Hinweise behandeln, nicht als endgültige Evidenz oder Effektgröße.

## 4. Konkreter Kandidat: vier gleichartige Spiegelantworten

Für **Argon gegen Astra** wird eine Folge von vier unmittelbaren Antworten mit derselben Spiegelung um die Zeilen-Mittellinie (bei Koordinaten a–m, 1–13) genannt:

| Ereignis | Gegnerzug → Argon-Antwort |
|---|---|
| #20 | `j11 → j3` |
| #24 | `l11 → l3` |
| #28 | `k10 → k4` |
| #32 | `k12 → k2` |
| #52 | `a8 → a6` (spätere weitere gleichartige Antwort) |

Die Bezeichnung **„vertikal“** aus dem ursprünglichen Bericht ist zu kontrollieren: Die Beispiele halten die Spalte konstant und spiegeln die Zeilennummer `r → 14-r`; im Koordinatensystem ist dies typischerweise eine **Spiegelung an der horizontalen Mittelachse**. Im späteren Code Transformationen durch Formeln statt ungesicherte Namen kennzeichnen.

**Zusätzliche Beobachtung:** Astra beantwortete laut Auswertung im Setup eine Serie von sechs gegnerischen Go-Zügen mit passenden, aber gemischten Transformationen (H/V/Diagonale).

Für einen Test der Serienlänge sollten auch rein zufällige/geometrisch oder legalitätsbedingt erwartbare Streaks bestimmt werden; selbstsymmetrische Felder und Achsenpunkte dürfen Treffer nicht unkritisch vervielfachen.

## 5. Modell-Thoughts und beobachtete Aktionen

Berichtet:
- Argon erwähnte in der Astra-Partie in **0 von 62 Go-Thoughts** ausdrücklich Spiegelung/Symmetrie.
- In der Flash-Partie benutzte Argon dreimal Begriffe wie „analog“/„symmetrisch“, davon einmal bei einem berichteten Spiegelzug (Event **#32**, „analog zu Weiß' Zug m7“).

**Interpretationsgrenze:** Weder Nicht-Erwähnung noch Erwähnung belegen oder widerlegen ein internes Motiv. Selbstbeschreibungen sind nicht gleich verifizierte strategische Intentionen.

## 6. Wichtige Konfundierungen und Alternativerklärungen

1. **Setup-Hubs und Brettgeometrie:** Symmetrische gute freie Startpunkte (z. B. e5/e9/i5/i9) können Spiegelungen schon ohne Gegnerimitation begünstigen. Vor allem die Haupt-Go-Phase separat analysieren.
2. **Rollen-/Zugfolgeeffekt:** In den betrachteten Logs beginnt Weiß. Unmittelbare Antwortspiegelung kann deshalb wesentlich die Rolle des zweiten Spielers abbilden statt eine feste Modelleigenschaft. **Farbtausch-Rematches sind entscheidend.**
3. **Transformationen und Multiples:** Treffer unter beliebiger der fünf Abbildungen ist leichter als die Vorabfestlegung *einer* Transformation. Separat Anzahl / Art, längste identische Streak und Korrektur für Suche über viele Kandidaten berichten.
4. **Legale Feldwahl:** Zustand, belegte Felder, Hub-Regeln, Go-Phase, Zentrum und gültige Alternativen verändern den erwarteten Trefferanteil. Nullmodelle müssen sich an diesen Bedingungen orientieren.
5. **Frühe Selektion:** Die drei initial gesichteten Partien gehören zum Entdeckungssatz; verbleibende Partien sind nur dann unabhängiger Bestätigungssatz, wenn sie nicht nach denselben Auffälligkeiten ausgewählt oder für die Hypothese bereits ausgewertet wurden.
6. **Modell-/Provider-/API-Kontext:** Provider, Modellfamilie, gemeinsamer API-Key/Projekt, Konfiguration und Promptbedingungen getrennt erfassen; keine Infrastruktur-Ursache aus Bildmustern ableiten.
7. **Keine Gleichsetzung mit Sycophancy:** Spiegeln könnte spielerisch sinnvoll, eine gelernte Musterheuristik oder unangemessene Verhaltensangleichung sein. Nur mit Stellung, legalen Alternativen und kontrolliertem Verhaltenstest unterscheidbar.

## 7. Datenschema für künftigen Pattern-Atlas

Vorgeschlagene **abgeleitete** Felder pro Go-Aktion (Original-JSONL unverändert):
- `go_action_index`, `event_id`, `match_id`, `actor`, `color`, `phase`, `source_timestamp`;
- `previous_opponent_go_event_id`, `previous_opponent_coordinate`, `response_coordinate`;
- `mirror_of_last_opp` als Array der passenden Transformationscodes `H,V,D,Dprime,R180` (mögliche Mehrfachtreffer auf Achsen erfassen);
- `mirror_streak`, `mirror_same_transform_streak`, `distance_to_symmetry_axis`;
- `mirror_reply_eligible`, `mirror_reply_legal`, dokumentierter Grund bei fehlender Vergleichbarkeit;
- Go-Kontrolländerung sowie pro Aktion und kumuliert verwendete Tokens, fehlgeschlagene Entscheidungen/Retry, soweit verlässlich verfügbar;
- Versions- und Ruleset-Felder für Reproduzierbarkeit, pseudonyme API-Key-/Projektgruppen (keine Secrets).

Definiere bei „unmittelbar“ ausdrücklich, ob der letzte **Go-Zug des Gegners** oder das letzte ausgeführte Gesamtereignis gemeint ist und wie dazwischenliegende Schachzüge behandelt werden.

## 8. Weitere zu prüfende Forschungsfragen

- **MIR-H1 – Reaktive Spiegelung:** In der Haupt-Go-Phase sind Spiegelantworten gegenüber zustands-/regelkonformen Nullmodellen überrepräsentiert.
- **MIR-H2 – Persistente Transformation:** Mehrere unmittelbare Antworten hintereinander unter *derselben* vorher definierten Transformation treten häufiger auf als erwartet.
- **MIR-H3 – Rollen- oder Modelleffekt:** Farbtausch und Serienvergleich unterscheiden Zweitspieler-/Farben- von Modell-/Paarungseffekten.
- **MIR-H4 – Strategischer Wert:** Spiegel-Streaks hängen mit Go-Kontrolländerung, späterer Siegwegwahl oder Ressourcenverbrauch zusammen; beobachtete Korrelation ist keine Kausalität.
- **MIR-H5 – Zentrum als Bruchpunkt:** Spiegelserien enden häufiger, wenn der Gegner zentrale oder auf Symmetrieachsen liegende Felder besetzt.
- **MIR-H6 – Behavioral Conformity:** Spiegeln geschieht möglicherweise selbst dann, wenn regelkonforme Alternativen objektiv besser wären; prüft erst dann eine mögliche sycophancy-artige Überanpassung.

**Status aller MIR-Hypothesen:** **Ideen für spätere Triage, keine neue formelle Präregistrierung und keine abgeschlossene Signifikanzanalyse**. Überlappung mit bestehenden OP-H1–OP-H6, INF-H1–INF-H4 und SOC-H1–SOC-H3 beachten; nicht doppelt zählen.

## 9. Empfohlenes späteres Vorgehen (nicht jetzt priorisiert)

- Originaldaten aller geeigneten Match-JSONL offline und deterministisch normalisieren, einschließlich historischer Fälle ohne `match_end`; Rohdaten unverändert lassen.
- Vor der vollständigen Kohortenanalyse Transformationen, Fenster, Nenner, Nullmodell, Hauptmetrik, Streakdefinition und Mehrfachtest-Korrektur festschreiben.
- Die konkret genannte Sequenz mit #20/#24/#28/#32 sowie #52 anhand der tatsächlichen Zugfolge zuerst auf Spiel-/Event-Ebene verifizieren.
- Ergebnisse pro Partie, Spieler, Paarung, Phase und Farbtauschserie aggregieren; Match-Cluster statt naiv unabhängiger Züge als Einheiten berücksichtigen.
- Separat markierte Keypoint-/Story-Szenen können die Sequenzen später auf der Website nachvollziehbar zeigen, müssen aber zwischen **belegter Spiegelantwort** und **Interpretation** unterscheiden.

## 10. Verweise

- [Series Explorer & Opening Pattern Atlas – Blueprint](../ANDY_SERIES_EXPLORER_OPENING_PATTERN_ATLAS_BLUEPRINT_v1.0.md)
- [Gesammelte Symmetrie-/Sycophancy-/TKO-Hypothesen](../ANDY_LAB_FORSCHUNGSIDEEN_SAMMLUNG_SYMMETRIE_TKO_VORTEIL_v0.1.md)
- [Bestehender zentraler Hypothesenpool](ANDY_REMATCH_HYPOTHESENPOOL_UND_EXPERIMENTDESIGN_v0.1.md)

**Leitlinie:** Erst systematisch zählen, dann Alternativerklärungen und regelkonforme Vergleichsoptionen prüfen; **nicht** aus geometrischer Wiederholung auf Absicht oder aus einem günstigen Ergebnis auf strategische Überlegenheit schließen.


## Ergänzung – Musterähnlichkeit statt Musteridentität

**Präzisierung der Forschungsfrage:** Wiederkehrende Muster müssen **nicht identisch** sein. Die exakte Mirror-Response-Metrik ist nur ein enger, gut prüfbarer Spezialfall. Der Pattern Atlas soll vor allem **Ähnlichkeitsfamilien** erkennen und untersuchen, auch wenn Koordinaten, Reihenfolge und Formen variieren.

Drei getrennt auszuweisende Ebenen:
1. **Exakte geometrische Spiegelantwort:** definierte Transformation des letzten gegnerischen Go-Zuges (bisherige Pilotmetrik).
2. **Ungefähre räumliche Ähnlichkeit:** verwandte Strukturen nach Transformation, mit begrenzten Abweichungen in Positionen, Abständen, lokalen Ketten oder Randverteilung.
3. **Funktionale/zeitliche Ähnlichkeit:** ähnliche territoriale Funktionen oder Entwicklungsverläufe (z. B. Randbesetzung, Barrieren, Gebietssicherung), auch ohne geometrisch passende Einzelzüge. Funktionale Gleichwertigkeit braucht eine explizite regel- und zustandsbasierte Operationalisierung.

**Auswertungsprinzip:** Exakte Spiegelung, statische Stellungsähnlichkeit, zeitliche Antwortähnlichkeit und funktionale Ähnlichkeit **nicht zu einem ungeprüften Einzelscore vermischen**. Im Offline-Scanner sowohl vorab definierte Tests als auch explorative Musterentdeckung vorsehen; abgeleitete Musterfamilien in unabhängigen Partien bestätigen. Ähnlichkeit allein belegt weder Nachahmung noch strategische Absicht oder Sycophancy.
