# ANDY Lab 2.0 – Match Eligibility, Forschungs-Kohorten und Archivstatus v0.1

**Datum:** 13.11.2026 · **Status:** vorgeschlagene Einordnungs- und Filterpolicy, nicht technisch implementiert und nicht anhand aller JSONL-Dateien validiert.
**Kontext:** [Lab 2.0 Research Architecture](../ANDY_LAB_2_0_RESEARCH_ARCHITECTURE_v1.0.md), [Hypothesenpool](ANDY_REMATCH_HYPOTHESENPOOL_UND_EXPERIMENTDESIGN_v0.1.md), [Strategic Situational Awareness](ANDY_STRATEGIC_SITUATIONAL_AWARENESS_SSA_v0.1.md).

## Grundsatz

**Nicht gewonnene und nicht abgeschlossene Partien sind nicht automatisch irrelevant.** Eine Partie mit nur 0–2 ausgeführten Zügen taugt nicht für Langzeit-Adaptivität, kann aber für API-Fehlertypen wertvolle Evidenz liefern. Ein Ressourcen-TKO ist ein relevantes Ergebnis für Ressourcen- und Execution-Forschung, kein pauschaler Ausschlussgrund.

**Zwei getrennte Felder führen:**
1. **Qualität/Status der Quelle:** vollständige/teilweise/unverifizierte Match- und Terminaldaten, Provider-/Tokenusage-Qualität, Regeln-/Konfigurationsstand.
2. **Eignung pro Hypothese:** Einschluss / nur eingeschränkt / Ausschluss mit belegbarem Grund.

Rohdaten archivieren, nicht löschen oder historische `match_end`-Events nachträglich erfinden. Belege und Reclassification-Log versionieren.

## A/B/C-Kennzeichnung für die Übersicht

- **A – Strategisch forschungsrelevant:** hinreichend aussagekräftiger Verlauf und prüfbare Zustands-/Claim-/Konfigurationsdaten für mindestens eine strategische Hypothese. Kein generelles Mindestlängen-Kriterium ohne Hypothesenbezug.
- **B – Eingeschränkt / hypothesenspezifisch:** Auswertung nur für bestimmte Fragestellungen, z. B. Ressourcen-TKO mit zensiertem Siegweg, unbestätigter Terminalstatus, fehlende Reasoning-Tokens, starke Konfigurationsabweichung.
- **C – Archiv/technische Diagnostik:** Starttests, kurze Fehlstarts, unbestätigte APIs, keine aussagekräftige Spielsituation. Nicht für strategische Aggregation; kann für Error-/Adapter-Kohorten in H12 zählen.

**A/B/C sind Sichtbarkeits- und Routinglabels, keine Qualitätspunkte oder unabhängige wissenschaftliche Urteile.** Ein Match kann mit A in H12 und C in H2 geführt werden. Die Statusanzeige muss das differenzieren.

## Hypothesenspezifische Einschlusslogik

| Forschungsfeld | Einschließen, wenn ... | Ausschließen/kennzeichnen, wenn ... |
|---|---|---|
| H1–H4 Strategische Zielwahl | dokumentierte, tatsächlich frei wählbare Chess-/Go-Aktionen, Kontext und Regelinformation | Phasenzwang, kurze Partien ohne Wahlfenster, fehlende relevante Logs |
| SSA-H1–H6 Lageeinschätzung / Prognose | konkrete datierte Aussagen + modell-sichtbare Informationen + validierbare Zustände | fehlender Text, unprüfbare/zu vage Aussagen, unbekannte Sichtbarkeit |
| H5–H8 Adaptivität | mehrere kausal/zeitlich verknüpfbare Gegneraktionen und Reaktionen, prüfbarer Handlungsspielraum | nur Startversuche, fehlende Zustände, erzwungene Folgen nicht als freiwillige Reaktion werten |
| H9–H12 Ressourcen & Ausführung | nachprüfbare API-Aufrufe, Limits und Fehler-/Retrydaten; selbst kurze Fehlstarts relevant | unbekannter Usagewert verhindert Tokeneffizienzvergleich, aber nicht Fehlerzählung |
| H13–H15 Wiederholbarkeit | kompatible Konfigurationsgruppen, unabhängige Matches, Serien-/Farbmetadaten | ungeprüfte Konfigurationsgleichheit, Versionsdrift, singuläre Ausreißer |

**Bedeutung terminaler Labels:** `KO_CHESS`, `KO_GO`, `TKO`, `ABORT`, `TECH`, `UNVERIFIED` getrennt protokollieren. `budget_overshoot`, `illegal_retries_exhausted`, `output_limit_retries_exhausted`, `max_decisions`, `unknown_token_usage`, `model_or_move_error`, `user_stopped` als dokumentierte Ursachen/Untertypen bewahren. Nicht automatisch aus Grundlabel den Gewinner oder die volle strategische Eignung ableiten.

## Vorläufige Beispiele aus Projektleiter-Liste vom 13.11.2026

| Match-ID | Beobachteter Listeneintrag | Vorläufige Route |
|---|---|---|
| `andy_64c8f95436d1` | Astra – Opus, 145 ausgeführte Züge, Schach-KO | A für Episoden/SSA; tiefe Engineprüfung nötig |
| `andy_0c0f7413fdf6` | Astra – Argon, 233 Züge, Schach-KO | A für Strategieverlauf/Ressourcen |
| `andy_cc11a6598bcf` | Argon – Astra, 207 Züge, Schach-KO | A für farbgetauschten Kontrast |
| `andy_1c77f49b3e17` | Flash – Argon, 136 Züge, Ergebnis nicht verifiziert; letztes Ereignis Go `k1` | B (Terminal offen), A-Kandidat nach validierter Engine-Rekonstruktion für Strategieverlauf |
| `andy_b94759f1b232` | Argon – Flash, 165 Züge, `budget_overshoot` | A für Ressourcen/Adaptionsverlauf; zensiert für vollständigen fachlichen KO-Vergleich |
| `andy_7eac20613e74` | Gemini 3 Flash – Gemini 3.8 Flash, 219 Züge, Schach-KO | A für längeren Verlauf (Metadaten prüfen) |
| `andy_a6fcd199c187` | DeepSeek V4 Pro – DeepSeek V4 Pro, 1 Zug, `output_limit_retries_exhausted` | C strategisch; B technisch für Retry-/Fehlertypen |
| `andy_b727095bc245` | Gemini 3.8 Flash – derselbe, 0 Züge, `unknown_token_usage` | C strategisch; Datenqualitätsfall |
| `andy_cf2c9f969541` | Gemini 3 Flash – Gemini 3.8 Flash, 3 Züge, `user_stopped` | C strategisch; Archiv |

**Achtung:** Diese Tabelle basiert auf den **vom Projektleiter kopierten Anzeigewerten**, nicht auf vollständiger Original-JSONL-Verifikation. Insbesondere unterscheiden sich in einzelnen Gesprächen API-Aufrufzahlen und Entscheidungszählung. Version/Parser/Nenner nicht vereinheitlichen ohne echte Quellenprüfung.

## Umsetzung im bestehenden Lab (Prio 2 und neue Prio 1)

**Prio 1 – Forschung:** Standardmäßig nur für die gewählte Hypothese *eligible* Beobachtungen und unabhängige Matchserien aggregieren. Oberhalb jedes Ergebnisses: `n_matches`, `n_series`, `n_episodes`, `n_excluded`, Vergleichbarkeitsklasse, Status geprüfter/ungeprüfter Enden, Datenstand und Methodenversion.

**Prio 2 – bestehende Datenansicht:** Filter `Alle` / `Strategisch relevant` / `Eingeschränkt` / `Archiv/Diagnostik`; vorhandene Matchlisten und Daten bleiben vollständig zugänglich. Bei Klick Einschluss-/Ausschlussgrund je Hypothese zeigen.

**Datenmodell als Vorschlag:**
```json
{
  "match_id": "andy_...",
  "source_status": "verified|partial|unverified",
  "terminal_status": "KO_CHESS|KO_GO|TKO|ABORT|TECH|UNVERIFIED",
  "display_tier": "A|B|C",
  "eligible_hypotheses": ["H12", "SSA-H2"],
  "limited_hypotheses": [{"id": "H1", "reason": "terminal_unverified"}],
  "excluded_hypotheses": [{"id": "H8", "reason": "insufficient_response_episodes"}],
  "coding_version": "eligibility-v0.1",
  "raw_sha256": null,
  "review_status": "provisional",
  "reviewed_at": null
}
```
(Die IDs im Codeblock illustrieren die Struktur; nicht als echte Freigabe einer bestimmten Match-ID ausgeben.)

**Keine blinde Cutoff-Regel:** 10/20/50 Züge sind nicht per se wissenschaftliche Qualitätsgrenzen. Nur an Hypothese, Ereignisnenner und erwarteten Mechanismus gebundene vorab definierte Regeln verwenden.

**Besonderheit Selbstpartien:** Bei gleichem Modell auf beiden Seiten nicht pauschal löschen. Für manche Kohorten/Interaktionshypothesen ausschließen, für Ausführungs- oder Farbkontrollfragen möglicherweise geeignet; als `self_play` markieren.

## Qualitäts- und Reproduzierbarkeitsregeln

- Quelle/Hash, Ruleset, Model-/Provideradapter-Version, Prompt, Budget und Retry-/Outputlimits berücksichtigen.
- Unbekannter Verbrauch ≠ Nullverbrauch. Terminale Siegaussagen des Modells ≠ Engine-geprüfter Sieg.
- Fehler getrennt als Format/Legalität/Provider/API/Limit/Abbruch klassifizieren.
- Ausschlussentscheidungen als Daten versionieren; aus Versionswechseln keine künstlichen Trends erzeugen.
- Hypothesenregistrierung vor neuen experimentellen Serien; explorative Historienanalyse getrennt halten.
- No retroactive modification of original JSONL: Recovery/Annotation in separatem verknüpften Manifest.

## Akzeptanzkriterien für Thread 1

- [ ] Historische Matches und JSONL unverändert erhalten.
- [ ] A/B/C und Evidenz-/Terminalstatus sichtbar machen.
- [ ] Forschungsfilter anhand der ausgewählten Hypothese; nie nur global „Gewinner behalten“.
- [ ] Kurze Fehlmatches bleiben im technischen Forschungskorpus auswertbar.
- [ ] Nicht bestätigte KO_GO nicht automatisch Leaderboard/KO-Statistik zuführen.
- [ ] Bei jeder Aggregation eingeschlossene und ausgeschlossene Matches samt Gründen und Anzahl offenlegen.
- [ ] Rückkampf-/Konfigurationsgruppen und Selbstpartien korrekt markieren.
- [ ] Neues Schema ist rückwärtskompatibel; bestehende Lab-/Replay-Ansichten bleiben auf Abruf erreichbar.

**Leitprinzip:** *Nicht aus den historischen Daten löschen, sondern kontrollieren, welche Daten welche wissenschaftliche Frage tatsächlich beantworten können.*
