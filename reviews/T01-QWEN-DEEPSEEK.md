# ANDY WPS-02 · Gemeinsamer Test T01

**Datum:** 11. November 2026  
**Gegenstand:** HTML-Durchmarsch V1.5, Schwerpunkt Kapitel 03 und 04  
**Status:** Externes Review angefragt · **keine** G1-Freigabe  
**Review-Teilnehmer:** Qwen (Regel-/Engine-Kritik), DeepSeek (Verständlichkeit / Red-Team), Oliver und GPT (Integration)

## Bitte zuerst lesen

- [Interaktive Handbuchseite](https://andy-arena-com.github.io/andy-wps-collaboration/durchmarsch.html?v=1.5#geometry)
- [HTML-Quelltext als Raw-Datei](https://raw.githubusercontent.com/ANDY-Arena-com/andy-wps-collaboration/main/docs/durchmarsch.html)
- [Arbeitscheckliste](https://raw.githubusercontent.com/ANDY-Arena-com/andy-wps-collaboration/main/WPS-02-CHECKLIST.md)

**Zugangshinweis:** Wenn die interaktive GitHub-Pages-Seite nicht bedient werden kann, bitte den HTML-Quelltext lesen und diese Einschränkung deutlich kennzeichnen. Nicht behaupten, die Animation gesehen zu haben, wenn nur der Code gelesen wurde.

## Der gemeinsame Gegenstand

### Kapitel 03: Brett und Koordinaten
- 13×13-Gesamtbrett; nur 8×8-Schachbereich kariert
- Weiß unten; Schach: A–H / 1–8; Go: a–m / 1–13
- Schachfiguren stehen **auf Feldern**; Go-Steine **auf Schnittpunkten**
- Fünf hervorgehobene Go-Leitpunkte
- Separate Schach-/Go-/kombinierte Ansichten

### Kapitel 04: Anfang
- Alle 32 Schachfiguren stehen bereits in der Grundstellung.
- Automatische Demonstration startet per einem Klick.
- Go-Setup setzt **acht schwarze und acht weiße** Steine, abwechselnd.
- **Erst danach** folgen drei Schach-Demozüge und der Demo-Endzustand.
- Go-Steine sollen korrekt auf Schnittpunkten sitzen, nicht in Schachfeldern.
- Die im Go-Setup gesetzten Steine haben eine **Doppelrolle**: Sie gehören zur Go-Ebene und beeinflussen die Schach-Ebene. Der exakte Mechanismus ist im DRAFT noch nicht erklärt.
- Die konkrete Demo-Sequenz ist **keine engineverifizierte ANDY-Partie**.

## Qwen – fachliche Fragen

1. Stimmen 8+8 Go-Setup, Reihenfolge und Übergang zu Schach mit der derzeitigen Regelimplementierung überein? Bitte **Ist-Zustand, Hypothese und Regelvorschlag** unterscheiden.
2. Wo liegen die fünf Go-Leitpunkte in der realen 13×13-Geometrie? Stimmen Diagramm, Koordinaten und Spielfeldorientierung? Falls nicht: exakte Korrektur.
3. Was heißt konkret, dass die Go-Steine „doppelt zählen“? Bitte in **2–4 verständlichen Sätzen** und mit mindestens einer benennbaren Regelwirkung.
4. Gibt es offensichtliche Konflikte in den drei Schach-Demozügen nach dem vorgeschalteten Go-Setup?
5. Welche **drei konkreten Korrekturen** sind am wichtigsten? Belege aus Engine/Match-Log bitte nur dann anführen, wenn du sie tatsächlich lesen konntest.

## DeepSeek – Leser- und Red-Team-Fragen

1. Verstehst du nach Kapitel 03 **ohne Rückfrage**, wo Schachfiguren und Go-Steine stehen und wie beide Koordinatensysteme funktionieren?
2. Wird in Kapitel 04 klar, **warum Go vor Schach beginnt** und was das 8+8-Setup zeigt?
3. Ist die „Doppelrolle“ der Go-Steine ausreichend anschaulich? Was wäre die **eine fehlende Erklärung oder Grafik**, die den größten Erkenntnisgewinn bringt?
4. Welche Textstelle ist unverständlich, zu technisch, zu lang oder behauptet mehr als der derzeit gesicherte Stand?
5. Welche **drei konkreten Korrekturen** sind am wichtigsten? Bitte keine allgemeine Neufassung des gesamten Handbuchs.

## Gewünschtes Antwortformat (für beide)

- **Zugriff:** HTML im Browser bedient / nur HTML-Quelltext gelesen / kein Zugriff
- **Was funktioniert:** maximal drei konkrete Beobachtungen
- **Was nicht funktioniert:** maximal drei konkrete Probleme, mit Kapitel-/Textreferenz
- **Fachlich unbestätigt:** ausdrücklich kennzeichnen
- **Top-3-Korrekturen:** in Prioritätsreihenfolge
- **Gesamteindruck:** Versteht ein interessierter Mensch das Brett und den Beginn einer ANDY-Partie besser als vorher – und wo noch nicht?

**Achtung:** Dies ist zunächst ein **Verständnis- und Review-Test**, keine formale Regelabnahme. Oliver entscheidet, was wir ändern; GPT übernimmt die Aktualisierung des HTML und der Arbeitscheckliste.
