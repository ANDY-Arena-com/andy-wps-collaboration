# WPS-02 · Kapitel 1 – Ziele und Siegbedingungen

> **Redaktionsstand:** DRAFT / zur fachlichen Prüfung durch Qwen  
> **Stand:** 11. November 2026 · **G1:** NICHT FREIGEGEBEN  
> **Verbindlichkeit:** Dieses Dokument beschreibt zunächst den Konsens und die Prüfaufträge aus den Rückmeldungen von Qwen und DeepSeek. **Es ist keine bestätigte Wiedergabe des aktuellen Engine-Verhaltens.**
>
> **Prüfgrundlage:** Aktuell tatsächlich eingesetzte Version von `andy_core.py` **und** Matchcontroller / Arena-Auswertung; bitte Commit, Konfiguration und Pfade dokumentieren.

## 1.1 Worum geht es in ANDY?

ANDY verbindet Schach und Go auf einem gemeinsamen Brett zu **einer Partie**. Die beiden Regelwelten werden nicht als zwei getrennte Spiele mit zwei unabhängig zu addierenden Siegen geführt.

Der Spieler muss deshalb beide Ebenen im Blick behalten: Ein Erfolg in einer Ebene kann entscheidend sein, ohne dass auf der anderen Ebene ebenfalls ein Sieg erreicht wurde.

**Status:** Redaktioneller Konsens von Qwen und DeepSeek; konkrete Auslöser und Interdependenzen sind unten zu verifizieren.

## 1.2 Wie kann eine Partie gewonnen werden?

**Vorgesehene Erklärung für Leser, erst nach Engine-Prüfung verbindlich:**

1. **Schachmatt:** Wenn eine regelkonforme ANDY-Schachstellung den gegnerischen König mattsetzt, könnte dies die Partie unmittelbar beenden. **Prüfen:** Die exakte Mattbedingung im Hybridkontext und der entsprechende Endcode.
2. **Go-Siegbedingung:** Qwen und DeepSeek nennen eine mögliche **Go-Kontrollschwelle** als weiteren Gewinnweg. Der genannte Wert **72 ist ausdrücklich nur ein Beispiel und KEIN bestätigter Schwellenwert**. **Prüfen:** Ob eine solche Schwelle existiert, welche Zählweise gilt, wann ausgewertet wird und ob dies sofort gewinnt.
3. **Aufgabe:** Qwen nennt freiwillige Aufgabe als möglichen Endgrund. **Prüfen:** Ob ein Resign-Befehl tatsächlich vorgesehen und implementiert ist.

**Nicht voraussetzen:** Dass jeder genannte Siegweg implementiert ist oder dass es genau diese drei regulären Enden gibt.

## 1.3 Wie endet ein KI-Wettkampf durch Ressourcenverbrauch?

In den ANDY-Arena-Duellen spielen die Modelle unter begrenzten Ressourcen (insbesondere Token-Budget, möglicherweise Zeit- oder Versuchsgrenzen).

Eine Ressourcenerschöpfung ist **nicht mit einem Sieg auf dem Brett identisch**. Qwen und DeepSeek schlagen vor, solche Enden unter **TKO** zu führen. Für das Regelheft muss jedoch geklärt sein:

- Welche Ressource wird **konkret** begrenzt: Eingabe-, Ausgabe-, Reasoning-, Gesamt-Token, Zeit oder anderes?
- Ist das Limit vor der nächsten Aktion, nach einer Antwort oder bei Überschreitung ausschlaggebend?
- Ist die Niederlage per Wettkampfreglement tatsächlich implementiert, und welcher Controller-Endcode steht im Matchlog?
- Wie werden Budgetfehler von Provider- oder Adapterfehlern unterschieden?

**Status:** Wettbewerbsrahmen und vorgeschlagene Begrifflichkeit; konkrete Semantik UNBESTÄTIGT.

## 1.4 Begriffe für das Ergebnisprotokoll

| Anzeige-Begriff (Vorschlag) | Vorläufige Bedeutung | Was zu verifizieren ist |
| --- | --- | --- |
| **KO** | Am Brett erreichter Spielgewinn, etwa durch Matt oder eine bestätigte Go-Siegbedingung | Tatsächliche Board-Endcodes, Zuordnung im Lab und Leaderboard |
| **TKO** | Niederlage aufgrund einer definierten Ressourcen- oder Wettkampfgrenze | Endcodes, Trigger, Auswertung und zulässige Ursachen |
| **TECH / No Contest** | Neutraler technischer Abbruch, z. B. ein Infrastrukturfehler | Ob und wie ein neutraler Status existiert und von Elo/Leaderboard ausgeschlossen wird |

**Wichtige Trennung:** (1) Spielzustand der Engine, (2) Abbruch-/Endursache des Matchcontrollers, (3) öffentliche Ergebnisbezeichnung, (4) Ranglistenwertung. Diese vier Dinge müssen nicht identisch sein.

## 1.5 Besonders offene Regel- und Wertungsfragen

### A. Gleichzeitige Gewinnbedingungen
Kann eine einzelne ANDY-Aktion mehrere Endbedingungen auslösen, etwa Matt und eine Go-Kontrollschwelle? Wenn ja, **welcher Status wird tatsächlich vergeben**? Qwens Empfehlung „Matt vor Go“ ist **noch kein belegter Ist-Zustand und keine getroffene Entscheidung**.

### B. Patt, Remis und Wiederholung
Welche Regeln gelten für Patt, Stellungswiederholung, Zähl-/Zuglimits oder andere Remis-Situationen? **Keine Annahme**, dass Remis unmöglich sei.

### C. `illegal_retries_exhausted`
Qwen erwägt **TKO**, DeepSeek ordnet wiederholte illegale Aktionen eher **TECH** zu. **Nicht entschieden.** Zu klären sind Ursachen, aktueller Controller-Endcode und Wettbewerbswertung; insbesondere eine illegale Modellaktion ist nicht automatisch ein Infrastrukturfehler.

### D. Parser-, API- und Providerfehler
Welche Fälle führen zur Wiederholung, zu einem Modellverlust oder zu einem neutralen Abbruch? Ein API-/Netzwerkausfall sollte nicht ungeprüft als Niederlage gewertet werden. DeepSeeks pauschale Zuordnung eines `invalid_response` zu neutralem TECH ist ebenfalls erst am tatsächlichen Controller zu prüfen.

### E. Budgetüberschreitung und Zeitzwang
Welcher konkreter Code trennt fehlendes Budget, einen Providerfehler, ein Timeout und das Ausbleiben eines gültigen Zugs? Werden Anfragen bereits bei Erreichen des Limits verhindert oder erst nachträglich bewertet?

### F. Aufgabe
Existiert eine explizite Aufgabe-Aktion? Welchem Ergebnistyp ist sie zugeordnet?

## 1.6 Arbeitsmatrix für den technischen Review

Qwen, bitte ergänze in deiner Antwort für jede Zeile **Codepfad/Funktion**, **Konfigurationsvariable oder Zahlenwert**, **Engine-/Controller-Commit**, **tatsächlichen Endcode** und wenn möglich **reproduzierbare Mini-Teststellung oder Matchlog**.

| Fall | Aktuell implementiert? | Code / Config / Endcode | Ergebnis / Wertung |
| --- | --- | --- | --- |
| Schachmatt | **offen** | — | — |
| Go-Gewinn / Schwelle | **offen** | — | — |
| Gleichzeitige Endbedingungen | **offen** | — | — |
| Patt / Remis / Wiederholung | **offen** | — | — |
| Aufgabe | **offen** | — | — |
| Tokenbudget erreicht / überschritten | **offen** | — | — |
| Zeitlimit | **offen** | — | — |
| Wiederholt illegale Aktionen | **offen** | — | — |
| Parser- / Antwortfehler | **offen** | — | — |
| Provider-/API-Ausfall | **offen** | — | — |
| Engine-/Controllerfehler | **offen** | — | — |
| Leaderboard-/Elo-Berücksichtigung | **offen** | — | — |

## 1.7 Didaktische Fassung nach Freigabe

Erst **nach der Bestätigung** der Endbedingungen wird aus diesem Prüftext eine knappe, anschauliche PDF-Seite:

- **Worum spielen wir?** Ein gemeinsamer Partieverlauf, keine getrennte Schach- und Go-Wertung.
- **Wie kann man auf dem Brett gewinnen?** Nur die tatsächlich implementierten ANDY-Siegwege.
- **Wie kann ein KI-Duell außerhalb des Bretts enden?** Ressourcen-/Wettkampfgrenzen getrennt von neutralen technischen Abbrüchen.
- **Was bedeutet das Ergebnis?** Eindeutige Ergebnislegende KO / TKO / TECH, falls vom System gedeckt.

**Keine Brettzugbeispiele in diesem Kapitel.** Die vollständige Startaufstellung, Felder, Schnittpunkte und Koordinaten kommen im nächsten Kapitel; erst danach folgen regelgeprüfte Anfangs-, Mittel- und Endspielbeispiele.

---

### An Qwen: Bitte jetzt prüfen

1. Lies **diese Version** und zitiere die relevanten Codepfade samt Engine- und Controller-Version.
2. Korrigiere jede falsche oder unbewiesene Behauptung ausdrücklich.
3. Beantworte die Fälle **A–F** und fülle die Arbeitsmatrix so weit wie möglich.
4. Kennzeichne fehlende Implementierungen und eigene Regelvorschläge getrennt.
5. **Keine Freigabe G1 beantragen**, solange die Endbedingungen nicht technisch und redaktionell abgestimmt sind.

**Redaktion:** GPT / Oliver · **Fachreview:** Qwen · **Freigabe:** ausschließlich Oliver.
