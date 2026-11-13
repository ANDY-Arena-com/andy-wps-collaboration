# ANDY Journal – Abgleich mit ANDY 2.0 Masterplan und WPS-Governance

**Datum:** 13.11.2026 · **Ergebnis:** Journal-Fachkonzept v1.1 (zur Prüfung / Weitergabe; nicht freigegeben)

## Quellen direkt geprüft

1. [ANDY 2.0 Masterplan v1.0](https://github.com/ANDY-Arena-com/andy-wps-collaboration/blob/main/PROJECT/ANDY_GESAMTKONZEPT_MASTERPLAN_v1.0.md) – projektübergreifende Vorgaben.
2. [Thread-Startbriefing](https://github.com/ANDY-Arena-com/andy-wps-collaboration/blob/main/PROJECT/ANDY_THREAD_START_HIER.md) – verpflichtendes Lesen, Übergaben, Realitätstest.
3. [WPS Governance](https://github.com/ANDY-Arena-com/andy-working-papers/blob/main/GOVERNANCE.md), [Editorial Guide](https://github.com/ANDY-Arena-com/andy-working-papers/blob/main/EDITORIAL_GUIDE.md), [Publication Status](https://github.com/ANDY-Arena-com/andy-working-papers/blob/main/PUBLICATION_STATUS.md), [Publishing](https://github.com/ANDY-Arena-com/andy-working-papers/blob/main/PUBLISHING.md) – Freigaben, fachliche Gates und Arbeitsstände. WPS-Repository ist privat.
4. Lokales Journal-Konzept v1.0 einschließlich Entscheidungen- und Matchcheckliste als Vergleichsbasis.

## Bereits konsistent

| Thema | Befund | Beleg |
|---|---|---|
| Rolle Journal | Ergänzt Arena/Lab, statt deren Funktion zu kopieren | Masterplan §3, §5D, §8 |
| Markenbild | 70 % Science Editorial / 30 % Fight Club; Original-Logo | Masterplan §8 |
| Redaktion | Vier Rubriken und Arena Moment → Evidence → Interpretation | Masterplan §5D, §8 |
| Zielgruppen | Erlebnis → Replay → Forschung → maschinenlesbare Quellen | Masterplan §3 |
| Sprachen | DE/EN/ZH, keine vorgetäuschten Übersetzungen | Masterplan §2, §8 |
| Sicherheit | Unveränderte Coming-Soon-Seite; getrennte WordPress-Umsetzung | Masterplan §8 |
| Multimedia | YouTube, Instagram als Teil projektübergreifender Kommunikation | Masterplan §8 |

## In v1.1 präzisiert / ergänzt

| Punkt | Änderung | Grund |
|---|---|---|
| SSOT | Klare Hierarchie Masterplan → Fachunterlagen → Umsetzung/Belege; neue Threads lesen Quellen direkt | Masterplan §9 und Thread-Startbriefing |
| Forschung | Claim-Taxonomie und Evidenzstatus; JSONL nicht automatisch validiert | Masterplan §2, §4, §6 |
| Match Facts | Quellhash, Engine-/Parser-/Schema-Version und Eventreferenzen als Soll-Metadaten | Masterplan §2, §4, §6 |
| Research Editions | Keine zweite wissenschaftliche Fassung in WordPress; PDF und maschinenlesbar aus derselben Datenbasis | Masterplan §5, §6; WPS Publishing |
| Publikationsprozess | Fachgates G1–G4, Fachfreigabe und getrennte Publikationsfreigabe verankert | WPS Governance, Publication Status |
| Launch | Ziel drei Startbeiträge statt lediglich mindestens eines Beispielartikels; Abweichung nur nach Freigabe | Masterplan §10 |
| Änderungen | GitHub-Branchen/PRs, Thread-Übergabe und Statusgrenzen konkretisiert | Masterplan §2, §9 |
| Wissenschaft | Ungeklärte dritte E3-Komponente ausdrücklich nicht definieren | Masterplan §4.2, §11 |

## Keine stillschweigende Angleichung / offene Punkte

- **WPS-Freigabestatus:** Laut `PUBLICATION_STATUS.md` (Stand 11.11.2026) waren keine Inhalte fachlich freigegeben. Vor einer Veröffentlichung aktualisieren; keine Freigabe aus v1.1 ableiten.
- **Journal vs. WPS:** Ein populärer Journal-Artikel ist nicht automatisch ein WPS-Paper. Sobald er jedoch abhängige Forschungsbehauptungen aufgreift, gelten deren fachliche Gates; allgemeine Einführungs-/Making-of-Texte benötigen eigene Fakten- und Publikationsfreigabe.
- **Launch mit drei Artikeln** ist eine Projektplanung, keine Zusage, dass drei geprüfte Texte vorliegen.
- **Corpus** ist weitgehend Zielarchitektur. Der Ort und Publikationsstatus von Original-JSONL, Manifests, geprüften Annotationen und Datenrechten sind noch zu verifizieren.
- **Matchangaben** im Mockup bzw. Masterplan sind nicht unabhängig anhand von Original-JSONL und Engine geprüft. Keine unbelegte Generalisierung.
- **WordPress/Theme/Multimedia/SEO** sind nicht technisch getestet. Bestehende Coming-Soon-/Arena-Systeme bleiben unverändert.
- **Offizielle E3-Definition** ist unvollständig; keine Ergänzung durch Vermutung.
- **WPS-Sichtbarkeit:** Internes Repository nicht ohne Freigabe in einen öffentlichen Journal-Bereich übertragen.

## Empfehlung zur Weitergabe an Parallel-Threads

1. Masterplan v1.0 bleibt übergeordnet und unverändert.
2. Journal-Gesamtkonzept v1.1 als fachlichen Entwurf verwenden; erst nach Review/Freigabe in die SSOT übernehmen.
3. Den Zuständigen für WPS/Lab die Schnittstelle Gate-Status → Journal-Artikelstatus zur Prüfung vorlegen.
4. Neue Entscheidungen, Testnachweise und Freigaben als GitHub-Commit/Issue dokumentieren.

**Nicht ausgeführt:** keine GitHub-Schreiboperation, keine WordPress-/Arena-Änderung, kein Audit des Originalcodes oder der Matchlogs.