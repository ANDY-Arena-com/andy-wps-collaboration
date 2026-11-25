# ANDY Journal – HOME-CURATION & GUIDED-TOUR-01

**25.11.2026 · Von der Projektleitung korrigiertes Home-/Coming-Soon-Zielbild**  
**Status: verbindlicher fachlich-technischer Auftrag aus dem UI-Audit; noch kein Plugin-Release, keine öffentliche Freigabe.**  
**Leitmotiv:** **Eine Journal-Home mit einer dramaturgisch kuratierten Startauswahl. Pro Bereich zunächst 1, höchstens 2 tatsächliche Inhalte – ergänzt um WHY, nicht durch Füllkarten.**

Anschluss: [WHY & Progressive Content Release](../content/ANDY-JOURNAL-WHY-PROGRESSIVE-CONTENT-RELEASE-01-2026-11-25.md), [System Map Foundation](../content/ANDY-JOURNAL-SYSTEM-MAP-FOUNDATION-01-2026-11-25.md), [Home Composer 0.1.43 / In-Place Preview](ANDY-JOURNAL-IN-PLACE-PREVIEW-01-HOME-COMPOSER-0.1.43-2026-11-25.md), [Staging/Live-Vertrag](ANDY-JOURNAL-STAGING-LIVE-SINGLE-WORKSPACE-SYNC-CONTRACT-2026-11-25.md).

## 1. Warum die bisherige Steuerung nicht genügt

Die Projektleitung will fünf **aufeinander abgestimmte** redaktionelle Einstiege (Fight Night, Academy, Research, Perspectives, Making of), mit jeweils **einem oder maximal zwei** zum Launch geeigneten, echten Inhalten. Der bisherige Composer gestattet dies nicht auf einheitliche Weise.

Geprüft am vom Nutzer gelieferten Home-Composer-Auszug (ca. 697 Zeilen, Version 0.1.42; Source-Check gegen das anschließend gebaute 0.1.43-ZIP):
- **Highlights:** 6 Inhalte redaktionell ausgewählt, globales Anzeigelimit bereits **2**; Highlight-Auswahl in DE/EN über bestehende Resolver.
- **Fight Night · CMS-Erlebnisbühne:** separates WordPress-/RGB-Quellenmodell, Maximalzahl **2**, Demo-IDs und Feed.
- **Fight Night · Match Stories:** manuelle RGB-ID-Auswahl und Limit **2**; andere Fight-Night-Bühne: **1**.
- **Research-Bühne:** manuelle RGB-ID und Limit **1**; **Research-Scroller** manuelle RGB-IDs und Limit **3**.
- **Making of:** manuelle RGB-IDs und Limit **8**, obwohl native Making-of-Stories existieren.
- **Perspectives:** **8 Themenfelder automatisch** aus Content Composer; keine Home-spezifische Auswahl von 1–2 *Artikeln*; acht Themen bleiben auf der Gabelseite sinnvoll.
- **Academy:** **4 Lernbereiche A–D als festes Raster**, auch ohne veröffentlichte Lektion; keine Home-spezifische Auswahl 1–2 Einstiegsgeschichten.
- **Claim-Teaser, Überblick und Suche** sind strukturelle/erklärende Elemente, **keine eigenständigen Artikel**, und dürfen nicht als zweite/dritte „Contentstücke“ mitgezählt werden.

**Wesentliche Unterscheidung:** `Maximal angezeigte Inhalte` regelt aktuell meist nur die Menge **innerhalb eines einzelnen Moduls**. Der Nutzer braucht dagegen eine **gesamte redaktionelle Auswahl pro Journal-Bereich über mehrere Module hinweg**. `Gleichzeitig sichtbare Teaser` regelt nur die Scroller-Fensterbreite. Die beiden Steuerungen sind nicht austauschbar.

## 2. Verbindliches Nutzungsmodell: fünf Bereiche, je zwei optionale Content-Slots

Im bestehenden **Home Composer** eine kompakte, eigene **„Startauswahl / Redaktionelle Home“**-Ebene vor die komplexe Modulbibliothek einfügen:

```text
STAGING  |  LIVE                  DE | EN
┌──────────────────────────────────────────────────────────────────────┐
│ HOME-REDAKTION · Startauswahl                                      │
│ Bereich        Inhalt 1 (Hauptteaser)  Inhalt 2 (optional)  WHY     │
│ Fight Night    [Story wählen        ] [– kein zweiter –]   ✓       │
│ Research       [Story wählen        ] [– kein zweiter –]   ✓       │
│ Perspectives   [Story wählen        ] [– kein zweiter –]   ✓       │
│ Academy        [Story wählen        ] [– kein zweiter –]   ✓       │
│ Making of      [Story wählen        ] [– kein zweiter –]   ✓       │
│          [Staging-Vorschau]  [Redaktionelle Auswahl speichern]      │
└──────────────────────────────────────────────────────────────────────┘
Darunter: unveränderte fachliche Modul-Editoren / Reihenfolge / Design.
```

- **Zwei ist Obergrenze, keine Pflichtzahl.** Ein Bereich mit einem guten Beitrag benötigt **keinen künstlichen zweiten Platzhalterartikel**. Ein noch leerer Bereich zeigt ausschließlich eine redaktionelle Orientierung/WHY.
- Die Auswahl muss **gezielt vorhandene** native WP-Story-Sprachfassungen bzw. registrierte RGB-Inhalte referenzieren, **keine** neuen Beiträge, Kopien, synthetischen Titel oder erfundenen Verlinkungen erzeugen.
- **DE/EN unabhängig prüfen.** Nur vorhandene und jeweils zur Auslieferung berechtigte Sprachpartner als Artikel-Links anzeigen; kein unbemerkter Sprachfallback für nicht freigegebene Inhalte.
- Pro Bereich wird genau eine **kanonische Startauswahl** hinterlegt; mehrere Home-Module desselben Bereichs (z. B. Fight-Night-Bühne + Fight-Rail + Research-Claim + Research-Rail) dürfen die ausgewählten Inhalte nicht ungewollt mehrfach als zusätzliche Contentplätze zählen. Modul-Positionen, Claim-Design und Layout bleiben weiterhin im Home Composer. Der technische Adapter entscheidet, in welchem bestehenden Modul welcher Slot gerendert wird.
- Die zugehörigen **Gabelseiten** behalten ihren vollständigen Themen- und Contentbestand (Academy A–D / Perspectives acht Themen). **Home-Kuratierung ist keine Löschung oder strukturelle Änderung der Gabelseite.**
- Die bestehende Inhalts-SSOT bleibt: WP-Posts, RGB-Registry, Content Composer Story-/Sprach-IDs, Launch Control WHY und Publication Planning. **Home speichert nur Referenzen, Slots, Anzeigepräferenzen und ggf. Präsentationszuordnung**; kein zweites CMS und keine parallele Text-/WHY-Datenhaltung.
- Die Homepage bleibt mit wachsenden Artikeln **derselbe Renderer und dieselbe Struktur**. Später lässt sich der redaktionelle Home-Umfang bewusst erweitern, ohne erneut eine Coming-Soon-Seite abzulösen. Für die erste Launch-Phase Standard **1 Slot / max. 2**.

## 3. WHY und Guided Tour – beide aus einer Quelle

**Empfehlung: eine *optionale* Guided Tour oben plus kleine „Warum?“-Aktion im Bereich. Keine erzwungene Wahl.** Dieselben von Launch Control bereitgestellten **fünf DE/EN-WHY-Datensätze** treiben beide Darstellungen.

- **Oben im Hero/Header** ein dezenter Button **„Journal entdecken · geführte Tour“** / **„Take a guided tour“**. Nicht auto-starten, keine Navigation blockieren, keinen neuen Hero-Slider oder parallele Webseitenschablone erzeugen.
- Tour mit **fünf Stationen**: Fight Night, Research, Perspectives, Academy, Making of. Pro Station im **vorhandenen Modul** zur Zielposition scrollen, den Bereich optisch hervorheben und seine gespeicherte WHY-Kurzfassung (optional weiterführende Erklärung) zeigen. **Weiter / Zurück / Überspringen / Schließen**, Tastatur- und Mobilbedienung, Fokusmanagement und `prefers-reduced-motion`.
- Pro Bereich **„Warum?“** als diskreter Link/Info-Button für Personen, die **keine vollständige Tour** machen wollen. Er öffnet exakt den gleichen WHY-Inhalt, aber nur für diesen Bereich (Dialog/Popover in vorhandener Design-Shell). **Keine Textduplikate**.
- WHY-Modi **prominent / compact / optional / hidden** bleiben autoritativ in Launch Control. `hidden` darf **in keinem** öffentlichen HTML, Tour-Markup, JSON, REST oder Quelltext sichtbar werden. Leere/unfreigegebene locale-WHYs erzeugen keine öffentliche Tourstation mit Content.
- In der **privaten Administrator-Vorschau** zunächst mit bestehenden WHY-Plänen arbeiten, öffentlich erst nach Prüfung des gemeinsamen **01C2B-Gates**.

## 4. Technik, Phasen und Sicherheit

### CURATION-01A – Redaktionelle Auswahl / Preview auf Staging

- Zunächst **nur Admin-Editier- und Preview-UI** innerhalb **des existierenden Home Composers**, keine neue Plugininstanz; Schema-Versionierung, Nonce/Revisionsprüfung und lokal begrenztes Staging-/Live-Speichern; auf Live noch keine neuen Content-Zugriffsfreigaben.
- Inhalt 1 / optional Inhalt 2 aus existierenden Story-/RGB-Registries; fehlende Sprach-/Freigabe-Referenz eindeutig als `nicht auslieferbar` kennzeichnen statt stillschweigend zu ersetzen.
- Schema nur Referenzen, Bereich, Reihenfolge, Präsentationszuordnung, Revision; keine WHY-Texte, Titel- oder Artikel-HTML-Kopien.
- Originalmodule bleiben erhalten. Privat-Preview kann reale redaktionelle Vorschau-Objekte für autorisierte Admins verwenden, darf keine öffentliche Post-API/REST umgehen.

### CURATION-01B – Modulprojektion / Tour auf geschütztem Staging

- In den bestehenden Modulrenderern die kuratierte 1–2-Auswahl **vor** automatischer Vollbestandsanzeige berücksichtigen; geordnete, sichere Fallbacks bei fehlender Quelle. Academy-/Perspectives-Home-Varianten zeigen 1–2 Einstiegsgeschichten oder passende CTA, nicht automatisch den gesamten Gabelseiten-Katalog, wenn Startauswahl aktiv.
- Bestehende Theme-/Header-/Hero-/Footer-/DE-EN-Konfiguration beibehalten. Tour-/WHY-Schicht als **Progressive Enhancement**, nicht als zweiter Page-Renderer.
- Golden-Screenshots vor/nachher von Staging-Home und privater Vorschau; Navigation und responsive Größen prüfen.

### 01C2B – zwingendes Gate für öffentlichen Launch

- **Keine öffentlich wirksame neue Story-/WHY-Auslieferung allein durch eine Home-Auswahl.** Gleiches Freigabegate wie für native Permalinks, Gabelseiten, RGB, Suche, REST, Feeds, Sitemaps, Medien und Cache; einzelne Sprachen und „editorial withdrawn“ strikt.
- Preview-Auswahl ≠ Veröffentlichungsfreigabe. Keine neuen Post-Status oder implizite Freigabe in bestehenden Modulen.
- Erst nach Browser- und API-Negativtests öffentliches aktivierbares Content-Slot-/WHY-/Tour-Rendering. Ein interner `WP publish`-Status ist ausdrücklich nicht ausreichend.

## 5. Abnahmebeispiele

1. **Research:** Inhalt 1 = eine vorhandene freigegebene, in DE und ggf. EN zugeordnete Research-Story; Inhalt 2 = leer. Im bestehenden Research-Modul genau **eine** Story; daneben `Warum?`, nicht ein erfundener Artikel.
2. **Fight Night:** Zwei explizit ausgewählte Match Stories. Vorhandene Fight-Night-Bühne bleibt Bühne; weitere Fight-Rail zeigt nicht automatisch dieselben Matches als neue, zusätzliche 2–3 Storyplätze.
3. **Academy:** Home zeigt einen Einstieg plus `Warum?`; **A–D bleibt auf der Academy-Gabelseite** vollständig erhalten.
4. **Perspectives:** Home zeigt zwei redaktionell ausgewählte Perspektiven/Stories, nicht automatisch alle acht Themenkacheln; die **acht Themenfelder auf der Perspektiven-Gabelseite** bleiben.
5. **Tour:** Button oben, fünf erlaubte Stationen mit DE/EN-WHY aus Launch Control, überspringbar; Aufruf `Warum?` am einzelnen Modul funktioniert ohne Tour. Fehlender/hidden WHY in jeder Sprache liefert keinen Text.
6. Änderung der Auswahl auf **Staging** verändert **Live nicht**. Rückzug eines Beitrags entfernt ihn nach künftiger Sicherheits-Projektion auch aus Home/Tour/Links; keine Leaks über Markup/Counts/Alt-Texte. Bestehende Staging↔Live-Navigation bleibt funktionsfähig.

## 6. Nicht-Ziele

Keine zweite Coming-Soon-Website. Kein zweiter Content-Store. Kein komplexer Graph, keine automatisch erfundenen Artikel, keine automatische öffentliche Freigabe, keine globalen WordPress-Datenbank-Replacements. Die Guided Tour ist **kein Freigabe-Workaround**. Die fünf WHY-Datensätze bleiben dauerhaft eigenständige redaktionelle Informationen in Launch Control.

**Operative Reihenfolge:** Dieser Auftrag korrigiert den Prioritätenfokus: Die **kuratierten Home-Slots** sind elementar für die gewünschte Launch-Home und müssen vor der nächsten rein gestalterischen Preview-Runde spezifiziert und umgesetzt werden. Tour-/WHY-Präsentation folgt aus denselben Daten, 01C2B bleibt das unverschiebbare Sicherheitsgate vor dem öffentlichen Ausrollen.