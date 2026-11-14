# LAB-R11 – Resource & Game Records
14.11.2026 · Best-of-Kandidat für das iterative Lab-Prototyping · Entwurf

**Ziel:** Auffällige Extremwerte über verfügbare Partien, Serien und Modelle identifizieren und näher erforschen. Rekorde sind keine Leistungsbewertungen, sondern interessante Extremfälle für Lab, Situation Challenge und Academy (Erleben).

## Auswertungsmöglichkeiten
- Höchster Gesamtverbrauch eines einzelnen Akteurs pro logischer Partie.
- Höchster Input-, Output- und ausgewiesener Reasoning-Tokenverbrauch (Providersemantik und Überschneidungen beachten).
- Höchster Tokenverbrauch einer einzelnen Entscheidung bzw. eines API-Aufrufs; diese Einheiten bei mehreren Versuchen separat ausweisen.
- Ressourcenrekorde je Spielphase (Setup, Chess, Go).
- Längste/kürzeste Partie (Dauerdefinition, externe Abbrüche und Resume beachten).
- Höchste Anzahl ausgeführter Aktionen.
- Höchste Anzahl geschlagener Schachfiguren und Go-Steine.
- Größter absoluter Ressourcenunterschied zwischen Kontrahenten derselben Partie.
- Größtes verbleibendes Budget bei einem Sieg; getrennt von Budgetüberschreitung.

## Interaktion
Sortierbare Top-10-Übersichten, Minimum, Maximum, Median, Filter nach Modell, Gegner, Serie, Budget, Outputlimit und Spielphase. Direkter Drill-down zur Originalpartie bzw. Entscheidung. Anzeige von Datenstand, Nenner, Einheit, Konfiguration, Endgrund, Gleichständen, Abdeckung und Quellenreferenz. Unterschiedliche Profile nicht als gleichwertige Leistungsbedingungen interpretieren.

## Referenzfall
Gesprächsimpuls 14.11.2026: Opus gegen Astra, Segment andy_b46041d24049, gemeldeter kumulativer Verbrauch Opus 351618 Tokens bei 350000 Budget; siehe PROJECT/ANDY_APP_LAB_SERIES_HANDOFF_2026-11-14.md. Kandidat für Abnahmetest, nicht als neu verifizierter globaler Rekord festgeschrieben. Rekordposition beim jeweiligen Datenimport neu berechnen. Originalprotokolle vor fachlicher Abnahme prüfen.

## Datenqualität und Tests (Entwurf)
- Logische Partien und technische Resume-Segmente unterscheiden; kumulative Verbrauchswerte nicht addieren. Überlappende Exporte deduplizieren.
- Fehlende Usage-Werte nicht als null behandeln; gemeldete Reasoning-Tokens nicht doppelt zählen. Unvollständige Summen kennzeichnen; bei unklarer Vergleichbarkeit separate Ansicht.
- Filterwechsel muss Ranking, Extremwerte, Median, Nenner und Quellen konsistent aktualisieren. Bei weniger als zehn geeigneten Einträgen nur vorhandene anzeigen.
- Test auf Gleichstände, fehlende Daten, Budgetüberschreitung, Resume und unterschiedliche Profile; Drill-down auf korrekte Match-/Event-ID. Keine behauptete Abnahme ohne Test.
- Versionierte Analyse-/Methodenreferenz und Datenstand verwenden; Anbindung LAB-R01/R02/R03/R06/R07/R10 und Pattern Observatory.

Status: neuer Requirements-Kandidat im A/B/C-Zyklus; Priorisierung offen, kein Implementierungsauftrag, keine neue Forschungshypothese oder strategische Bewertung.
