# Situation Challenge – interaktive Problemlöse-Demo v0.1

14.11.2026 · Ergänzender Konzeptentwurf auf Wunsch der Projektleitung; kein Implementierungsauftrag.
**Erleben. Erforschen. Erahnen.** Die Demo eröffnet einen neuen Erkenntniszyklus, vermittelt keine vermeintlich endgültige strategische Lösung.

## Nutzerfrage
Welche legalen Züge führen aus einem konkreten Problem heraus? Welche verschärfen es möglicherweise oder verlagern es? Ausgangspunkt ist dieselbe versionierte Midgame-Situation aus der Situation Library, mit einer konkret beschriebenen, nachvollziehbaren Bedrohung oder Herausforderung. Der Mensch entscheidet selbst und erlebt die Konsequenzen.

| Mögliche Wirkung | Beschreibung |
|---|---|
| Problemlösung | Bestehende Bedrohung entschärfen oder beseitigen |
| Problemverschiebung | Lokales Problem lösen, dafür z.B. im anderen Teilspiel eine neue Schwierigkeit erzeugen |
| Problemverschärfung | Eigene Verwundbarkeit erhöhen oder Handlungsmöglichkeiten verlieren |
| Problemumkehr | Aus einer Bedrohung eine eigene Chance entwickeln |
| Problemübertragung | Eigene Lage stabilisieren und zugleich Gegner destabilisieren |

Kategorien sind offene Beschreibungen, nicht exklusive Klassen, keine Ampelwertung oder validierten Strategielabels. Kurzfristige und langfristige Folgen können auseinanderfallen; Wirkung hängt von gegnerischen Antworten ab.

## Interaktionsentwurf
1. Originalzustand S0 mit Problemstellung zeigen; Hinweise optional, keine Lösung vorwegnehmen.
2. Legal Action Explorer: eigene Aktion auswählen; vollständige ANDY-Regeln und Aktionsphase beachten.
3. Unmittelbaren regelgeprüften Folgezustand zeigen (Brett, Go-Kontrolle, Material, Bedrohungen, legale Folgeoptionen, soweit verfügbar). Bei mehreren möglichen gegnerischen Antworten Verzweigungen sichtbar machen, nicht nur eine zwangsläufig scheinende Fortsetzung.
4. Optional tatsächliche KI-Entscheidungen aus demselben S0 erst nach eigener Entscheidung offenlegen. Gespielte Verläufe, deterministische unmittelbare Folgen und hypothetische Fortsetzungen deutlich unterscheiden. Keine nicht gespielten Verläufe als historische Daten darstellen.
5. Jederzeit zu S0 zurückkehren, weitere legale Aktionen ausprobieren und Zweige nebeneinander vergleichen. Originale bleiben unverändert. Keine ungeprüfte Behauptung eines optimalen Zuges; strategische Deutungen ausdrücklich als Erahnen kennzeichnen.

## Schnittstellen und Tests (Entwurf)
Anknüpfung an LAB-R06/R07/R09/R10 und Situation Challenge (§15 Forschungsagenda), Dynamic Bonoma, Academy und späteren KI-Coach. Gemeinsame versionierte Zustandshashes, Quellen-Event-IDs, Regel-/Engine-Versionen, Aktions- und Zweig-IDs, Folgefenster, Herkunft und Validierungsstatus. Keine separate widersprüchliche Wissensbasis. Pattern View und Analytical View bleiben verknüpft.
- Start-/Reset-Test: identisches S0 einschließlich regelrelevanter Historie, Phase, Zugrechten und Zählern; keine Veränderung des Originalmatches.
- Legalitäts-/Folgetest: Alternative und unmittelbarer Folgezustand mit tatsächlicher ANDY-Engine prüfen; bei fehlendem vollständigem Zustand blockieren statt erfinden.
- Vergleichstest: mehrere Zweige aus S0 bei gleichen Annahmen, Gegnerantworten und Horizonten nachvollziehbar vergleichen; fehlende oder nicht untersuchte Folgen offen lassen.
- Evidenztest: KI-Originalaktion erst nach eigener Wahl optional anzeigen; beobachtet, regelgeprüft, hypothetisch und strategisch gedeutet trennen.
- Erlebenstest: Nutzer kann selbst wählen, zurücksetzen und Unterschiede nachvollziehen, ohne vorgegebene Siegerstrategie.

Erster Clickdummy darf ausdrücklich gekennzeichnete illustrative Zustände nutzen; fachliche Abnahme erst mit realer, vollständig rekonstruierter Situation. Sichere Midgame-Initialisierung und Legal Action Explorer noch zu prüfen. Keine Änderung der bestehenden Requirements-IDs/Prioritäten, keine neue Hypothese, kein API-Start. Aufnahme in den iterativen A/B/C-Prozess als späterer Prototyping-Kandidat.
