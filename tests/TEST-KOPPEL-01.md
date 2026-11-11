# TEST-KOPPEL-01 · Go-/Schach-Wechselwirkung verifizieren

**Stand:** 11.11.2026 · **Status:** Testvorschlag, NICHT enginebestätigt  
**Quelle:** Qwens Hypothesen H1/H2/H3 und DeepSeeks didaktisches Vier-Bilder-Konzept nach T01  
**Ziel:** Das erste fachlich belegte Vorher-/Nachher-Beispiel für WPS-02 finden.

## 0. Vorab: Geometrie richtigstellen

Qwen formulierte als Zuordnungsregel: **Schachfeld A1 wird von Go-Knoten c3, d3, c4, d4 begrenzt**. Daraus folgt rechnerisch für Schachfeld mit Datei-Index `i` (A=0 … H=7) und Reihen-Index `j` (1=0 … 8=7):

- untere linke Ecke = Go-Spalte `c+i`, Go-Reihe `3+j`;
- weitere Ecken sind jeweils eine Go-Spalte/Reihe höher.
- Beispiel `E4`: E ist Index 4, Reihe 4 ist Index 3; E4 hat die Ecken **g6, h6, g7, h7**.
- Daher grenzt Go-Knoten **g7** an die Felder **D4, E4, D5, E5** (nicht E5/F5/E6/F6, wie in Qwens Rückmeldung behauptet).

**Auch die Zuordnungsregel selbst ist noch durch die reale Arena-/Engine-Geometrie zu bestätigen.**

## 1. Hypothese H1 · Go-Stein beeinflusst diagonale Läuferzüge

**Qwens Design-Intention, nicht als Engine-Regel bestätigt.**  
Annahme: Go-Stein an einer kreuzenden Gitterecke verhindert einen diagonalen Schachzug bzw. unterbricht eine Läuferdiagonale.

### TEST-KOPPEL-01A · Basisfall
- Nur in einem Engine-Testzustand mit ansonsten leerer Go-Ebene; Weiß: König A1, Läufer E4; Schwarz: König H8. **Vor Test prüfen, ob diese Minimalstellung als ANDY-State zulässig/erzeugbar ist.**
- Vorher: legale Schachzüge des Läufers E4 dokumentieren.
- Danach: einen schwarzen Go-Stein am tatsächlichen Knoten **g7** setzen.
- Erneut die legalen Schachzüge und gegebenenfalls Bedrohungsfelder prüfen.
- **Entscheidung:** Hat sich die erlaubte Zugmenge geändert? Wenn ja: exakt welche Felder und durch welche geprüfte Regel? *Nicht voraussetzen*, dass F5/G6/H7 vollständig verschwinden.

### TEST-KOPPEL-01B · Kontrolle
- Testzustand zurücksetzen.
- Einen Go-Stein an einem verifizierten Knoten setzen, der **nicht** auf der betroffenen Läuferdiagonale liegt. Qwen schlägt `h7` vor; diese Auswahl vorher anhand der Brettgeometrie bestätigen.
- Dieselben Zugmengen vergleichen.
- **Ergebnis:** Wirkt der Go-Stein punktuell, flächenhaft oder überhaupt nicht? Kontrollversuch mit ebenfalls unverändertem Engine-/Controller-Setup.

### TEST-KOPPEL-01C · Go-Gegenrichtung
- In einem getrennten Test eine Go-Gruppe mit bekannter letzter Freiheit bilden.
- Durch eine gültige Schachaktion eine Schachfigur auf ein angrenzendes Feld bewegen.
- Go-Freiheiten und gegebenenfalls Gruppenstatus *vorher/nachher* aus der Engine auslesen.
- Damit H2 als Regel gilt, muss sich eine echte, protokollierte Go-Zustandsgröße ändern.

## 2. Minimalprotokoll für jede Probe

| Feld | Wert |
| --- | --- |
| Ruleset / Engine-Commit | ausfüllen |
| Matchcontroller / Config | ausfüllen |
| Test-ID | 01A / 01B / 01C |
| Vollständige Ausgangsstellung (Schach + Go) | ausfüllen |
| Aktion und Koordinate | ausfüllen |
| Legale Züge / Freiheitszahl davor | ausfüllen |
| Legale Züge / Freiheitszahl danach | ausfüllen |
| Terminal-/Fehlerstatus | ausfüllen |
| Ergebnis | bestätigt / widerlegt / unklar |
| Reproduzierbarer Log / Replay-ID | verlinken |

**Nicht in das Handbuch als Regel übernehmen**, solange diese Felder unvollständig sind.

## 3. Redaktionelle Umsetzung nach grünem Test

DeepSeeks vierteilige Dramaturgie übernehmen, aber mit **dem tatsächlich bestätigten Figurentyp und Effekt** statt einem vorgegebenen Turm:

1. **Vorher:** Figur und zunächst legale/erreichbare Felder.
2. **Go-Aktion:** Ein Stein erscheint auf dem verifizierten Go-Knoten.
3. **Nachher:** Die *tatsächlich* veränderten Felder/Zugmöglichkeiten hervorheben.
4. **Synthese:** Erläutern, welche Wirkung dieselbe Aktion in Go und in Schach hat.

Die beiden Zustände sollen aus derselben reproduzierbaren Testposition erzeugt werden. Kein erfundener roter Blockadepfeil und keine unbestätigte Aussage über eine Turmlinie.

## 4. Entscheidungen

- **Offen:** Ist H1 überhaupt implementiert?
- **Offen:** Ist H2 implementiert?
- **Offen:** Welche konzeptionelle Doppelwirkung ist in Ruleset v1.1 konkret nachweisbar?
- **Offen:** Was bedeutet die in der Arena sichtbare Figur-/Stein-Kopplung tatsächlich?
- **Fest:** Vor der Veröffentlichung als Regel werden Code-/Replay-Belege verlangt.

**Review:** Qwen = technische Einordnung nach Engine-Zugriff; DeepSeek = didaktische Vier-Bilder-Abnahme; Oliver = fachliche Freigabe; GPT = HTML/Protokoll/Integration.
