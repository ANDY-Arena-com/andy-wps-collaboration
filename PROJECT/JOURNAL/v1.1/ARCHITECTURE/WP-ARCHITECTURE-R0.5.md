# ANDY JOURNAL · WP-ARCH R0.5
**24.11.2026 · Tagesabschluss · Journal v1.1 · Entwicklungscheckpoint**
Fortschreibung von [R0.4](WP-ARCHITECTURE-R0.4.md), Git-Checkpoint 726af08a803667c4e980e9a43d143c1afb8dbd28. Historische Dokumente bleiben erhalten.

## 1. Arbeitsstand und Evidenz
- Home Composer (HC) **0.1.37 HIGHLIGHTS-FIT-TAGS-01**: letzter im Entwicklungsgespräch positiv bestätigter Home-Arbeitsstand.
- Content Composer (CC) **0.1.26 ACADEMY-VIDEO-IMPORT-FIX-01**: Nutzer bestätigt erfolgreichen Import und ausdrücklich die Übernahme redaktioneller Änderungen in die Overview.
- CC **0.1.27 PERSPECTIVES-CONTENT-01** und **0.1.28 PERSPECTIVES-OVERVIEW-01**: ausgeliefert, Nutzer reagiert auf 0.1.28 positiv („Top!!! Für heute sehr gute Ergebnisse.“); kein detaillierter Hostinger-Abnahmebericht zu Import, beiden Sprachen, Filter, Bildern und Routen. Jüngster bereitgestellter Arbeitsstand ist 0.1.28, nicht pauschal vollständig abgenommen.
- Alle 22 seit R0.4 bereitgestellten ZIPs im Arbeitsverzeichnis erneut geöffnet, Plugin-Header-Version mit Dateiname abgeglichen, ZIP-CRC/Integrität geprüft, SHA-256 neu berechnet (Abschnitt 9). Release-READMEs ausgewählter Inkremente, Beispiel-JSONs und Filter-/Overview-Code aus 0.1.28 eingesehen. Keine erneute vollständige PHP-/Browser-/WordPress-Prüfung in diesem Dokument; frühere Testzahlen sind Berichte aus den jeweiligen Releases. Keine Live-Datenbankabfrage. Dieser Commit dokumentiert, archiviert keine Binärdateien und verändert weder Website noch WordPress-Daten.
- HC und CC sind verschiedene Plugins mit unabhängigem Versionsstand. In-place-Update des jeweils gleichen Slugs, keine parallelen Installationen oder Downgrades. [Release-/Import-Gate](../docs/ANDY-WORDPRESS-RELEASE-UND-IMPORT-GATE-v0.1-2026-11-23.md) bleibt bindend.

## 2. Chronologie seit R0.4
| Release | Inkrement / Ergebnis |
|---|---|
| HC 0.1.31 | HIGHLIGHTS-CURATION-01: kuratierbare Highlights |
| HC 0.1.32 | HIGHLIGHTS-POLISH-02: visuelle Überarbeitung |
| HC 0.1.33 | TYPOGRAPHY-01: lokale Webfont-Option, flexible Texthöhen; weitere Typografiearbeit zurückgestellt |
| CC 0.1.14 | ACADEMY-STRUCTURE-01: vier Lernbereiche, eigene DE/EN-Routen, opt-in, explizite Legacy-Demo-Links, Seitenentwürfe als Anker |
| CC 0.1.15 | ACADEMY-DIDACTICS-01: Bereichstabs, Introduction, Niveaus, Lernziel, Dauer, Bild, Sprachwechsel |
| CC 0.1.16 | ACADEMY-LIGHT-01: helle statt dunkler Lernumgebung |
| CC 0.1.17 | ACADEMY-VISUAL-01: vier Bereichs- und drei Lektionsbilder, Mediathek-Overrides |
| HC 0.1.34 | ACADEMY-HOME-01: erste Home-Anbindung |
| HC 0.1.35 | ACADEMY-HOME-02: vier feste Bereichskarten statt wechselnder Lektionen, auch leere Bereiche, gemeinsame Bereichsdaten |
| HC 0.1.36 / CC 0.1.19 | ACADEMY-IMAGE-COVER-01: flächig proportionale Bilder (Home 16:10, Übersicht Tabs 2:1, Introduction/Lektion 16:9) |
| CC 0.1.18 | ACADEMY-LESSON-LAYOUT-01: kompakte native Lektionsdetailseite, kein großes Hero standardmäßig |
| CC 0.1.20 | ACADEMY-LEGACY-LAYOUT-01: separates Banner auf den drei Original-Demorouten entfernt, Player beibehalten |
| CC 0.1.21 | ACADEMY-LESSON-SOURCE-01: gemeinsamer Lektionsdatensatz, Lernziel/Titel/Intro/Dauer/Niveau, vorher/nächste und zurück; editierbare Legacy-Metadaten |
| HC 0.1.37 | HIGHLIGHTS-FIT-TAGS-01: echte Themen-Tag-Links und Cover/Contain-Bildmodus |
| CC 0.1.22 | ACADEMY-RULE-SAMPLES-01: fünf weitere redaktionelle A-Lektionen, DE/EN-Entwurfspaare; Nutzer bestätigt Anlage |
| CC 0.1.23 | ACADEMY-ADMIN-FILTERS-01: native Beitragsliste nach ANDY-Inhaltsbereich A–D, Template und Lernniveau filtern; keine redundante Kategorisierung |
| CC 0.1.24 | ACADEMY-VIDEO-SAMPLES-01: zehn B/C/D-Lektionen, Video-Slot, lokale Sprachfelder, Niveau-Filter nur A |
| CC 0.1.25 | ACADEMY-VIDEO-TEST-01: externe Testvideo-IDs, Ergänzungsbutton; Nutzer meldet, dass Buttons keine neuen Inhalte anlegen |
| CC 0.1.26 | ACADEMY-VIDEO-IMPORT-FIX-01: gemeinsamer Importbutton, fehlende Sprachpartner, separater Lock, persistenter Bericht mit WP-Fehlern und ID-Tabelle; Nutzer bestätigt Erfolg und Content→Overview |
| CC 0.1.27 | PERSPECTIVES-CONTENT-01: sechs quellengestützte DE/EN-Paare, editierbares Thema, Key Visual unmittelbar unter Header, freie Erzählform |
| CC 0.1.28 | PERSPECTIVES-OVERVIEW-01: DE/EN-Overview, dynamische Themenfilter, Rücklinks, editierbare Introduction, Topic-ID/Label-Fix |
Versionsreihen sind getrennt; die Tabelle gruppiert funktionale Zusammenhänge, keine exakte minutengenaue Reihenfolge.

## 3. Architekturentscheidung: Content bestimmt Overview bestimmt Home
Von hinten nach vorne: native WordPress-Beiträge sind redaktionelle Quelle von Titel, Introduction, Lernziel bzw. Thema, Bild, Tags und lokalisiertem Inhalt. Die Overview liest veröffentlichte passende Beiträge; Home nutzt gemeinsame Bereichsdaten oder ausdrücklich kuratierte Inhalte. Keine zweite redaktionelle Pflege der Karten. Sprache und Freigabe getrennt, Shared Design und gemeinsame Bildreferenzen aus R0.4 gelten weiter. Admin-Filter lesen die tatsächlichen ANDY-Metadaten statt WP-Kategorien zu duplizieren (auch Beiträge unter Uncategorized auffindbar). Redaktionelle Beispiele dürfen nach Prüfung veröffentlicht werden, wenn klar als solche erkennbar; keine automatische Publikation oder Freigabe von Originaldaten.

## 4. Academy (MS-05): Lernumgebung in der Breite
Neutralgraue Identität, helle redaktionelle Oberfläche; vier eigene Bereichsbilder, die der Nutzer in WP ersetzen kann. Keine starren identischen Lehrformate.
| Bereich | Bestand/Vorlagen | Didaktik |
|---|---:|---|
| A · ANDY-Spiel verstehen | 8 | Regeln, interaktive Demos, Anfänger/Fortgeschrittene/Experten, Mini-Quiz |
| B · Werkzeuge bedienen | 4 | Video-Tutorials, Screenshots, Übungen; thematisch für Fortgeschrittene |
| C · Auswerten und erforschen | 3 | Videos, Charts und Beispieldaten; Experten |
| D · Installieren und entwickeln | 3 | Videos, Anleitungen, Code; Experten |
18 Lektionen als geplanter/verfügbarer Beispielbestand, nicht 18 bestätigte öffentliche Posts; drei DE-Original-Demos plus 15 native DE/EN-Vorlagen (= bis zu 30 Entwürfe). B/C/D benötigen keine individuellen Anfänger-/Experten-Filter; spätere Filter nach Werkzeug, Analyseaufgabe, Plattform. A–D sind keine zwingende Lernreihenfolge: D kann Voraussetzung für praktische Nutzung von B/C sein; B-Videos können vor Installation Orientierung geben. Querverweise statt künstlicher Voraussetzungskette.
- A03 Setup/Hubs, A05 Go-Schlag, A07 Schach-Go-Kopplung sind vorhandene Originalmodule. Legacy nur DE und nur bei aktivem RGB-Register/Contentmodus und expliziter Freigabe; Original-Interaktion bleibt unverändert. Keine native Migration behaupten.
- Neue redaktionelle A-Lektionen A04 Freiheiten, A06 Gebietskontrolle, A08 unsterblicher Anker, A09 Kontrollsprung, A11 strategische Zugentscheidung. Keine neue Regelengine, noch keine validierten interaktiven Szenarien.
- B01 Designer, B02 Replay, B03 Observer, B04 Lab/Data; C01 Kontrollkurve, C02 Modelle/Konfigurationen, C03 Token/Kosten; D01 GitHub, D02 lokale Installation, D03 Konfiguration/Start. Texte und Lernzeiten sind beispielhaft; Video-Slots verwenden vorläufig externe Testvideos, ausdrücklich keine tatsächlichen ANDY-Anleitungen. Eigene YouTube-Videos je Sprache später eintragen; bewusstes Laden per Klick. Eigene Texte/Videos und bewusst entfernte Videos schützen.
- Details: kein großes Headerbild für Regel-Lektionen; Lernmetadaten oben, Interaktion schnell erreichbar; Vor/Zurück nach Bereich und Lektionscode, Rücklink zum Bereich. Native Metadaten _andy_ac_lesson (gemeinsam), _andy_ac_goal (lokalisiert), _andy_cc_intro (Excerpt-Fallback), Featured Image. Legacy-Option andy_ac_legacy_lessons_v01 plus Bildoption; Bereichsbilder andy_ac_area_images_v01. Routen /de/academy/ und /en/academy/, ac_area/ac_level, bestehendes E2E und Kollisionsschutz.
- Import: Beiträge → ANDY Academy; native WordPress-Entwürfe, keine Überschreibung. 0.1.26 behebt beobachteten Ausfall praktisch; genaue Hostinger-Ursache nicht nachgewiesen. Isolierte Tests (32 im Release berichtet), persistenter Bericht pro Nutzer, getrennte Locks, fehlende Partner reparieren, keine stillschweigende Fehlerunterdrückung.
- Zusammenarbeit mit Rulebook-Thread: dieser erstellt/validiert Szenarien, Regeln, Quiz und Engine; Journal-Thread integriert, verwaltet, verlinkt, gestaltet und ermöglicht Lernfortschritt. Vorschlag elf weitere Demos, vier fachliche Prioritäten Freiheiten, Gebietskontrolle, geschützter Anker und Kontrollsprung ohne Schlag. Detaillierte Rule-IDs und versionierte Regelreferenz, stable R-01…R-06 HTML-Anker, Ruleset/Match/Ereignis/Engine-Referenz, evidenzbasierter Szenariotyp getrennt vom Vorschaubild sind **offen**, nicht implementiert. Historische Regeln v1.1 und beschlossene v1.2 unterscheiden, kein rückwirkendes Umschreiben. Ein Player/viele Szenarien; allgemeiner Content-Paketimport noch offen. Drei Schwierigkeitsniveaus ≠ sechs nachgewiesene Kompetenzstufen; Sterne nur für bestandene Leistungen, nicht Seitenaufrufe. Siehe [Academy-Plan](../../../ACADEMY/ANDY_ACADEMY_PLAN_v0.1.md) (Pfad vom Architekturordner: ../../../ACADEMY).

## 5. Perspectives (MS-07): Problem-driven statt Solution-driven
**Nicht die Lösung sucht das Problem.** Nutzerentscheidung: Perspectives hat Vorrang vor Research im engeren Sinne. Ausgangspunkt sind reale Probleme und existierende publizierte Forschungsfragen; ANDY entwickelt nachvollziehbare Antwortangebote, keine erfundenen Forschungsfragen und keine künstliche Anwendungssuche. Ergebnis kann auch sein, dass ANDY noch keinen tragfähigen Beitrag leisten kann. Transfer und Analogie ≠ empirischer Nachweis. Erkenntnislogik: reales Problem → externe Forschung → belegbare ANDY-Beobachtung/Methode → möglicher Transfer/Antwort → Grenzen. Keine starre Artikelgliederung. Blau = Erahnen/Transfer, Grün = Erforschen/Prüfen, Rot = Erleben/Beobachtung. Dimensionsfarben und Anwendungsfelder nicht gleichsetzen; blaue Artikel können grüne/rote Bausteine enthalten. Externe Fragestellungen geben Research Impulse, die Arena liefert beobachtbare Fälle.
- Eigene thematische Editorial-Bildwelten (Health, Token Economy, Agentic Commerce, Co-Creation, Adaptive Systems). Großes Beitragsbild **direkt unter dem gemeinsamen Header**, blaue Abschlusslinie, freie WP-Artikelgestaltung. Anders als Academy. Bilder aus vorhandenen RGB/Academy-Assets sind nur Übergangsmotive, keine wissenschaftlichen Abbildungen. Individuelle Bildproduktion und Auswahl offen.
- Sechs DE/EN-Entwurfspaare (12 Beiträge) über Beiträge → ANDY Perspectives. Explizite Themenzuordnung _andy_pc_topic, _andy_cc_template=perspectives, _andy_cc_intro/Excerpt, Beitragsbild, Quellen im editierbaren Body, gemeinsame Bildreferenz. Keine automatische Publikation/Überschreibung, EN separat prüfen.
| ID/Thema | Titel | Externe Quelle (im Entwurf referenziert) | Form / ANDY-Transfer |
|---|---|---|---|
| P01 Health | Nicht nur die richtige Antwort zählt | [How to benchmark medical AI agents](https://doi.org/10.1371/journal.pmed.1005170) | Entscheidungsketten: Angemessenheit, Prozesssicherheit, Ressourcenverantwortung; vergleichende Tabelle, keine klinische Validierung |
| P02 Token Economy | Was kostet ein Gedanke? | [Scaling LLM Test-Time Compute Optimally](https://arxiv.org/abs/2408.03314) | Essay: situativer Ressourcenaufwand |
| P03 Token Economy | Ist die beste KI auch die wirtschaftlichste? | [AI Agents That Matter](https://arxiv.org/abs/2407.01502) | Kosten und Leistung getrennt vergleichen |
| P04 Agentic Commerce | Wenn KI zum Wettbewerber wird | [Agentic Markets](https://doi.org/10.1007/s12525-026-00906-y) | Gedankenexperiment über autonome Akteure |
| P05 Co-Creation | Wer entwickelt hier eigentlich wen? | [When combinations of humans and AI are useful](https://doi.org/10.1038/s41562-024-02024-1) | Perspektivwechsel, illustrativer Dialog |
| P06 Adaptive Systems | Wenn Handlungsfähigkeit an ihre Grenze stößt | [Measuring AI Ability to Complete Long Tasks](https://arxiv.org/abs/2503.14499) | Ressourcenerschöpfung und experimentelle Wiedergewinnung |
Quellen und Titel aus bereitgestelltem Entwurf/Entwicklungsgespräch; keine erneute externe Literaturprüfung in diesem Git-Abgleich. Vor Veröffentlichung Primärquellen, konkrete Forschungsfrage, ANDY-Evidenz und Transfergrenzen redaktionell/fachlich prüfen. [Economy Observer 23.11.](../../../ANDY_LIVE_OBSERVER_ECONOMY_STATUS_2026-11-23.md) dokumentiert beobachteten Sandboxstand; [TKO Refund](../../../ANDY_TKO_REFUND_RESEARCH_v0.1.md) ist Forschungs-/Implementierungsziel, kein genereller Recoverability-Nachweis.
- 0.1.28: /de/perspectives/ und /en/perspectives/, Aktivierung in Beiträge → ANDY Perspectives, opt-in und Language E2E, Pfadkollision blockiert beide neuen Routen ohne WP-Seiten zu überschreiben. Editierbare DE/EN Introduction (andy_pc_intros_v01). Filter pc_topic, Themen/Weitere Perspektiven, dynamische Counts; keine Entwürfe, internen/gesperrten oder sprachlich nicht zugeordneten Inhalte. Rücklink/Breadcrumb zur gewählten Themenübersicht, Sprachwechsel mit Filter. 23 PHP-Syntaxprüfungen und 27 isolierte Prüfungen laut Release; kein erneuter WP-Livetest.
- Home bleibt durch 0.1.28 unverändert. Bestehendes Home-Modul kann per konfigurierbarem Link auf die neuen Routen zeigen; automatische Home-Integration und dynamische Themenbilder noch offen.

## 6. Making-of / Erkenntnisse
- Zunächst große Academy-Heros, dann Erkenntnis: Lernen braucht unmittelbaren Zugang zur Übung, nicht viel dekorative Fläche. Für Perspectives hingegen ausdrücklich großformatiges Bild. Keine universelle Gestaltung erzwingen.
- Home zuerst mit individuellen Academy-Lektionen, dann vier gemeinsame Bereichskarten; gleiche Inhalte aus zentraler Quelle statt Doppelpflege.
- Native WP-Kategorie allein reicht für fachliche Filter nicht; Metadaten als gemeinsame Grundlage, getrennt von Schlagwörtern und Sprache.
- Video-Import 0.1.24/25 nicht erfolgreich im Nutzer-Livetest; 0.1.26 macht Fehler sichtbar, verhindert Dubletten und wird erfolgreich getestet. Keine unbewiesene Root Cause als Fakt festschreiben.
- Agile Mona Lisa: zuerst Breite mit transparentem Testmaterial, dann fachliche Vertiefung. Keine externen Testvideos als ANDY-Produktion, keine generierten Messwerte.
- Problem-driven Crossover: nicht nachträglich passende Anwendungen zu einer vorhandenen Lösung erfinden. Die externe Frage legitimiert den ANDY-Einsatz.
- Making ANDY bleibt selbst ein Co-Creation-Untersuchungsgegenstand; Umwege, Nutzerkorrekturen und Abnahmelücken dokumentieren.

## 7. Fortschreibung Modulstatus und Priorität
MS-00/01 Shared Shell/Home: fortgeschrittener Arbeitsstand, HC 0.1.37; MS-02 Gabelseiten: Fight Night, Academy und Perspectives als Piloten, Research noch auszubauen; MS-03/09/10/12 Core, Content Manager, Bridge und Language: nativer DE/EN-Workflow mit dynamischer Academy-Overview praktisch bestätigt, Perspectives-Pilot bereitgestellt; MS-05 Academy: Breite 18 Lektionen/Vorlagen, Original-Player separat, Lernpfade/Prüfungen und echte B/C/D-Videos offen; MS-06 Research: Zahlenreihen-MVP, vollständige Gabelseite und reale Analysen offen; MS-07 Perspectives: sechs quellengestützte Entwurfspaare plus Overview, eigene Bildwelten und Home-Crossover als nächste Aufgabe; MS-08 Social: Konzept; MS-11/13/14 Asset/Evidence/Editorial Studio: kein vollständiger versionierter Paketvertrag oder Freigabe echter Match-Evidenz. R0.4 bleibt für übrige Module maßgeblich.
Nächste Reihenfolge (aus Projektentscheidung und daraus abgeleitetem Arbeitsvorschlag):
1. Perspectives komplettieren: reale Themenbilder, Content-Review mit Primärquelle, dynamischer Home-Crossover, DE/EN-Live-Abnahme.
2. Academy parallel: eigene Videos durch Nutzer, Rulebook-Thread liefert geprüfte Szenarien. Regelreferenzen und gemeinsame Content-Pakete statt neuer Plugin-Version pro Lektion.
3. Research-Gabelseite, echte APP-Evidenz und erste vollständige rot/grün/blau vernetzte Story (interne Reiher-Story bleibt gesperrt bis ausdrückliche Freigabe).
4. Übergreifende semantische Vernetzung: Tags/A–Z/Sitemap plus Beziehungen nach Regeln, Match, Quellen und verwandten Beiträgen; keine automatisch behaupteten Kausalzusammenhänge.
5. Lernpfade, Kompetenzprüfungen und Sterne; KI-Coach und Replay-Challenges erst bei validierter Engine und klarer Aufgabenstellung.
Kein neuer Plugin-Code, keine Deinstallation, keine Publikationsfreigabe durch dieses Dokument.

## 8. Abnahmepunkte
- Academy-Import und Content→Overview: durch Nutzer bestätigt (0.1.26). Vollständige Abnahme von Video-Wiedergabe, DE/EN, Filtersuche, Originalplayer-Parität, Mobilansicht und Datenschutz nicht belegt.
- Perspectives: Nutzer positiv, konkrete Checkliste noch auszuführen: sechs Paare/keine Dubletten, veröffentlichte passende Beiträge/keine gesperrten, Themenwechsel, Detailbild unter Header, Rücknavigation, DE/EN und Home-Verlinkung, Bild-/Quellenreview.
- Research und echte Evidenz: keine neuen validierten Ergebnisse aus Demo-Texten ableiten.
- Release-Gate: vor nächstem Update installierte Version und tatsächliches Ausgangs-ZIP prüfen, Backup, keine Publikation ohne Freigabe.

## 9. Artefaktregister seit R0.4
Alle Dateinamen beginnen mit `ANDY-WP-PLUGIN-`; die folgenden Suffixe sind exakte restliche Namen. ZIP-CRC und jeweiliger Plugin-Header wurden im Tagesabschluss erneut geprüft. Hashes identifizieren die lokal vorhandenen Pakete; keine Git-Binärarchivierung und kein Nachweis installierter Bytes.
| Dateinamensuffix | SHA-256 |
|---|---|
| Home-Composer-v0.1.31-HIGHLIGHTS-CURATION-01.zip | 41fa9a4ccebea3ef93e43ebb36fe0302778a1b0bf61b873ac817281e349d7f88 |
| Home-Composer-v0.1.32-HIGHLIGHTS-POLISH-02.zip | 73e2e56044d1f9c665bfde9349c9240a5929f7f9b23b3ec0f601d3035265e673 |
| Home-Composer-v0.1.33-TYPOGRAPHY-01.zip | cd8b145cc1cc7482781ff5ff3dbce66d368c4f8f13df78610af47855d5ae3c30 |
| Home-Composer-v0.1.34-ACADEMY-HOME-01.zip | 5414d583f19ba63183fcefdc434a3465309c7b2449b60029bd5fb9218cdb8bdb |
| Home-Composer-v0.1.35-ACADEMY-HOME-02.zip | 439db2239057bdaa2716c6aaa223a1e221d0673bed7323432d997fd1a2d9d966 |
| Home-Composer-v0.1.36-ACADEMY-IMAGE-COVER-01.zip | 2070b560ef4da874124487d63e8b05e9ae24a633a05e88e34c67f7e269551d77 |
| Home-Composer-v0.1.37-HIGHLIGHTS-FIT-TAGS-01.zip | 5b772b90c87bdd20807bb127417576e6ef8dcb2f4c3b7347cd69bf650732dbf9 |
| Journal-Content-Composer-v0.1.14-ACADEMY-STRUCTURE-01.zip | 49bcd972c0ba06e154b113c1f1e270ae1f16e0d2a93e5088ae65a22e519a2bf5 |
| Journal-Content-Composer-v0.1.15-ACADEMY-DIDACTICS-01.zip | 54676e3035e9844fb547509f96ab9345161b7a8dd05ca5946ad63959b93c24ad |
| Journal-Content-Composer-v0.1.16-ACADEMY-LIGHT-01.zip | 89024d8fc86609d86758d223997082bf63d5bf77ede556b34d360d8c2c8be6af |
| Journal-Content-Composer-v0.1.17-ACADEMY-VISUAL-01.zip | 71ffeb1ea7d8bec50e8f9c9f9afeb7188db08be81f0dea7f184a000cfd27fd83 |
| Journal-Content-Composer-v0.1.18-ACADEMY-LESSON-LAYOUT-01.zip | 87a89da076b0b84761c1ba4fb3464c543a4cb6bc158f8c62b45beb0d337165a9 |
| Journal-Content-Composer-v0.1.19-ACADEMY-IMAGE-COVER-01.zip | 8250a86742b2359197d8ed796f276c5e84bb66c5b9c5ead717dcdf143bf75028 |
| Journal-Content-Composer-v0.1.20-ACADEMY-LEGACY-LAYOUT-01.zip | 87229fecea2eff4ec46a6ec6e6010c6c4c99429abda2f89d7285df6d931491c5 |
| Journal-Content-Composer-v0.1.21-ACADEMY-LESSON-SOURCE-01.zip | cb99a57e7fc3e9c2ef699d9585592aca473c90fb28838f2708f88837b5cc91d9 |
| Journal-Content-Composer-v0.1.22-ACADEMY-RULE-SAMPLES-01.zip | 57332ce3b04d831cd0cf31e5bc9e71879b5e6b2a1e8d2b166aa61352bfbeec7d |
| Journal-Content-Composer-v0.1.23-ACADEMY-ADMIN-FILTERS-01.zip | 36531cd8dc74678fcca18820219582aac19b60afb5a57aff8c9a5bc7d4ed5e26 |
| Journal-Content-Composer-v0.1.24-ACADEMY-VIDEO-SAMPLES-01.zip | 6013b06c2362a9e2b19559ea9613c4d9ca4fdf6e813c8992c571e875b8493a0a |
| Journal-Content-Composer-v0.1.25-ACADEMY-VIDEO-TEST-01.zip | cb94221e89bb0f05309ec42b76839fcf73408460f3a9a241d6cb2a79985a923f |
| Journal-Content-Composer-v0.1.26-ACADEMY-VIDEO-IMPORT-FIX-01.zip | f09eb8a0583505a0e7207b10f405bca9394dcef162208bfa5c464c9e06f1d88f |
| Journal-Content-Composer-v0.1.27-PERSPECTIVES-CONTENT-01.zip | 262811c945dac8bf9698625de960659984f7cb147556d9a1c64f833243be0ccf |
| Journal-Content-Composer-v0.1.28-PERSPECTIVES-OVERVIEW-01.zip | 4acccf7845b3632682559896dc34471d23f921c9f44f140a58e5b82d9a4092e4 |

**Erleben. Erforschen. Erahnen. – Reale Probleme. Bestehende Forschungsfragen. Eigenständige Antworten.**

## 10. Format-Backlog: visuelle Übersichten und Whitepaper (Nachtrag 24.11.2026)
Nutzerimpuls zum Tagesabschluss, ausdrücklich nur als Backup/Ideenspeicher; keine Implementierung oder Prioritätsänderung.
- **Visuelle Übersichten / Visual Briefs**: eigenständiges, kompaktes redaktionelles Format, z. B. für Pinterest, LinkedIn und andere Social-Kanäle. Zwei Screenshot-Referenzen aus dem Dialog: „How to Explain AI to Decision Makers“ (fünf anschaulich geschichtete AI-Ebenen) und „Qwen3.8 vs Inkling-2-Mini“ (mehrspaltige Benchmark-Scorecard mit hervorgehobenen Vergleichswerten). Die Referenzen inspirieren die Darstellungsform; ihre Taxonomie und Messwerte werden nicht als ANDY-Ergebnisse übernommen oder als geprüft bezeichnet. Drittanbieterbilder bleiben im Dialog; keine öffentliche Bildkopie im Repo.
- Mögliche ANDY-Formate: visuelle Begriffslandkarten, Modell-/Konfigurationsvergleiche, Token-Economy-Scorecards, kompakte Ablauf- und Erkenntnisgrafiken. Vertikale, eigenständig verständliche Darstellung als Vorschlag; verlinkt auf den vollständigen Journal-Content. RGB-Zuordnung nach Erkenntnisart, nicht nach Ausgabekanal. Quellen, Bedingungen, Einheiten, Stichprobe und Evidenzstatus bei Vergleichen transparent halten; keine pauschalen Sieger aus einzelnen Kennzahlen ableiten.
- **Whitepaper**: eigener Bereich innerhalb von Research (grün), nicht unter Perspectives. Ausführliche, versionierte Dokumentation von Fragestellung, Methodik, Datenbasis, Befunden, Grenzen, Quellen und Reproduzierbarkeit. Mögliche HTML-/PDF-Ausgabe und eigene Übersicht sind spätere Gestaltungsentscheidungen, keine bereits implementierten Funktionen.
- Content → Overview → Home bleibt maßgeblich; Social-Grafiken und Whitepaper können aus gemeinsamen redaktionellen Fakten und Evidenz hervorgehen. Kein zusätzliches Plugin und keine Publikation durch diesen Nachtrag.

## 11. Perspectives – drei weitere Crossover-Themen (24.11.2026)
Vom Projektleiter ergänzt: Cybersecurity, Compliance/XAI und Datenresonanzpunkt (im Dialog „Datensresonanzpunkt“). Zusammen mit Health, Token Economy, Agentic Commerce, Co-Creation und Adaptive Systems ergeben sich acht Themenwelten im redaktionellen Backlog. Keine neuen Beiträge, Filter oder Plugins durch diesen Nachtrag. Problem-driven: externe bestehende Fragestellungen und Primärquellen vor Ausarbeitung jedes Artikels identifizieren; projektinterne Hypothesen nicht als externe Forschung oder validierte Antworten darstellen.

| Thema | Projektinterner Anknüpfungspunkt | Evidenzgrenze / nächster Schritt |
|---|---|---|
| Cybersecurity | [Cybersecurity-Crossover: Nested Competitive Networks](../../../../research/andy-lab/CROSSOVER/CYBERSEC_NESTED_COMPETITIVE_NETWORKS_v0.1.md), Memo 21.11.2026. Wechselseitige Co-Adaption verschachtelter konkurrierender Netzwerke, lokale vs. globale Stabilität, Reorganisation und Ressourcen unter adversarialen Bedingungen. Dynamic Bonoma, Competitive Mirroring und Model Interaction Profiles. | Konzeptionelle Analogie, keine validierte operative Cyberabwehr; externe Forschungsfrage/Primärquelle suchen und Transfergrenzen ausweisen. |
| Compliance / XAI | [Event-to-Evidence Method](../../../../research/andy-lab/METHODIK/ANDY_EVENT_TO_EVIDENCE_METHOD_v0.1.md) und [Match-Evidenzvertrag](../../../ANDY_MATCH_EVIDENCE_JSONL_JSON_SQLITE_v1.0.md): nachvollziehbare Kette von verfügbarer Information, protokollierter Aussage, Entscheidung, Legalität, Reaktion und Ergebnis; Originalquellen, Provenienz, Unsicherheit, unabhängige Validierung. | Vorläufige redaktionelle Zuordnung zu Auditierbarkeit und überprüfbarer Erklärung, keine Behauptung rechtlicher Compliance oder mechanistischer Explainability. Modelläußerung ist kein Nachweis interner Kognition. Spezifisches Crossover-Dokument und externe Forschungsfrage noch identifizieren. |
| Datenresonanzpunkt | Vom Projektleiter benannter eigenständiger Themenpunkt; genaue Definition und GitHub-Referenz noch zuzuordnen. | Im geprüften Main-Repository kein eindeutiger Begriffstreffer; keine Definition ergänzen oder mit Competitive Mirroring gleichsetzen. Bis zur Quellenzuordnung als offener Themenanker führen. |

Alle drei Themen sind für Perspectives (blau, Transfer) vorgemerkt. Spätere empirische Untersuchungen gehören in Research (grün). Kein Wechsel der bisherigen Prioritäten.

## 12. Making of – Entwicklungscheckpoint 25.11.2026
[Story-Katalog und Entwicklungsstand](../content/ANDY-MAKING-OF-STORY-KATALOG-v0.1-2026-11-25.md). Eigenständige neutralgraue Meta-Ebene mit RGB-Akzenten. 10 DE/EN-Story-Paare im Add-on 0.1.0/0.1.1; MO11 „Der Mensch als Orchestrator“ als neuer Entwurf. Home-Bridge auf vorhandener Rail, Content→Overview→Home, keine Änderungen an den parallel bearbeiteten Composern. Staging-Aufbau, Rollen von ChatGPT, DeepSeek, Qwen und Hostinger-KI, GitHub als Wissensbasis und Rolling-Handoff-Test dokumentiert. Genaue Live-Abnahme der Bridge und Ausgang des Handoff-Tests offen. Keine Binärarchivierung oder Publikationsfreigabe.
