# ANDY TKO Refund – Resource Extension Research
Stand 19.11.2026 · Beschluss / Implementierungsziel, keine Produktionsfreigabe.
Ergänzt [Resume Research & ARP](ANDY_RESUME_RESEARCH_ARP_v0.1.md) und Issue #9.

## Ziel
Ein bereits sportlich abgeschlossenes Ressourcen-TKO bleibt unverändert gültig. Ein explizit genehmigtes Zusatzbudget ermöglicht einen eigenständigen experimentellen Folgepfad vom letzten verifizierten Spielzustand. Refund ist eine ANDY-interne Ressourcenzuteilung, keine Rückerstattung von Providerkosten und keine Löschung verbrauchter Tokens. Ausgangsfall Fable 5.2/Astra: laut Operator TKO für Astra und inhaltlicher Vorteil Fable; Originalbericht/Tokenabrechnung noch zu prüfen, keine unabhängige Qualitätsbewertung.

## Vertrag
- Reguläre Resume-Sperre für geschlossene Partien bleibt bestehen. Separater TKO-Refund-Modus; zunächst ausschließlich belegtes Tokenbudget-TKO, keine KO/DRAW, Retry-TKO, unklare Usage, technische Abbrüche oder Regeländerung. Regelzustand muss nichtterminal und eindeutig rekonstruierbar sein. Kein stilles Erhöhen sonstiger Limits.
- Zusätzliche Token pro Seite explizit festlegen, bisherigen Verbrauch inklusive Overshoot vollständig beibehalten; erweitertes Budget = bisheriges Budget + genehmigte Zusatzmenge. Rest = max(0, erweitertes Budget minus kumulativer Verbrauch). Kein Reset von Zug-/Aufrufzählern, Modell, Strategie oder Spielregeln.
- Neue eindeutige Experiment-ID, Root/Parent/Branch, Refund-Index, Ausgangsergebnis samt Grund, Originaldatei-Hashes, verifizierter Baseline-Zustand/Hash, ursprüngliche und erweiterte Konten pro Seite, Freigabezeit, ARP-Attempt-ID, Status auch bei blockiertem Start, Folge-Usage und Folgeergebnis getrennt. Unbekannt bleibt unbekannt.
- ARP und tatsächliche Spielaufrufe nur nach aktiver Freigabe; Briefing-Ressourcen separat. Kein strategischer Vorteil durch Referee. Originaldateien bytegleich, keine Writes in normale DB/Archiv/Serien/Leaderboard; eigener Forschungsordner außerhalb normaler Scanner, keine automatische Publikation. Wiederholung/weitere Refunds später explizit, nicht automatisch; keine Doppelstarts.
- All Games perspektivisch als kategorieübergreifende Sicht (Continuous, Resume, TKO Refund; Recap separat), nicht als naive Summe von Siegen: Original und davon abhängige Folgepfade unterscheidbar, offizielle und experimentelle Resultate getrennt, Nenner/Abhängigkeiten offenlegen. Bewertungsformel vertagt. Performance, Efficiency, Recoverability und Resource Elasticity sind Forschungsfragen, keine automatischen Scores.

## Arbeitspakete
1. TKO-REFUND-01: read-only Quellprüfung, Budgetrechnung, eindeutige separate Freigabe-/Evidenzakte, sicherer Pilot mit bestehender Engine und ARP.
2. TKO-REFUND-02: Arena-Bedienung, Live-Tracking, Replay/Export gesondert; nach realer Sandbox-Abnahme synchronisieren.
3. ALL-GAMES-01: abgeleitete Gesamtübersicht mit sichtbaren Kohorten und Branchbeziehungen, spätere Wertungsregeln.
Abnahme: echte Quellpaare validieren, unbekannte Usage und falsche Endgründe blockieren; Originale/DB bytegleich, alte normale Resume-Sperre bleibt; explizite Freigabe, kein Paid Call bei Installation/Audit; getrennte Ergebnisse, Stop/Fehler und Wiederholungen sauber protokolliert. 8082 zuerst; 8080/8083 unverändert bis geprüfter Übernahme.
