# ANDY Journal – MODULE-SOURCE-PARITY-01 · Home Composer 0.1.44

**25.11.2026 · Lokaler, installierbarer Staging-Release-Candidate. Kein bestätigter WordPress-/Browser-/Cache-E2E-Test; Live bleibt unverändert.**

## Nutzerbefund / Fehler

Staging und Live machen wiederholt sichtbar, dass **Editor-Konfiguration nicht zuverlässig der OnSite-Projektion entspricht**. Screenshot: Fight-Night-CMS-Bühne mit den gespeicherten IDs `1419,1423,1427`, angeboten im aktuellen WordPress-CMS jedoch u.a. `1469,1466,1471,1473,1475`, Maximalzahl `2`, gewähltes Farbpreset `Nature of Competition · Schwarz / Rot` und sechs gleichzeitig sichtbare, aber nicht wirksame individuelle Farb-Eingabefelder.

Im Quellcode war `src.contentBridge ? cmsFightStories : ...` ein **nachweisbarer Override** für manuelle IDs und die konfigurierte Maximalzahl. Außerdem nutzen Content-Composer-Stories Kennungen `wpstory-<PostID>`, ältere Home-Demos `wpfn-<PostID>`; alte Auswahl konnte diese nicht einheitlich auflösen. Die individuellen Farbfelder werden nur bei `fight_theme=custom` im Renderer wirksam, während die sechs Felder im Admin unabhängig davon bearbeitbar wirkten.

**Ohne direkten WP-DB-Zugriff bleibt die tatsächliche Verfügbarkeit der historischen Post-IDs offen.** Kein blindes Reparieren, Neu-Anlegen oder Ersetzen von Stories.

## Erstes Reparaturinkrement: 0.1.44

**Änderung ausschließlich im bestehenden Plugin `andy-home-composer`, Basis 0.1.43.** Neue explizite Wahl **`Automatisch` / `Manuell · ausschließlich diese Post-IDs`** in der WP-Fight-Night-Bühne, als neues Feld `fight_selection_mode` in der **bestehenden Modulkonfiguration**. Bestehende Module ohne das Feld bleiben zunächst im bisherigen **Automatikmodus**, damit das Update nicht ungefragt die Home leerräumt.

Eine gemeinsame CMS-Selektionsfunktion verwendet für **Admin-Vorschau und öffentlichen Renderer dieselbe eingetragene Reihenfolge und Maximalzahl (1–12)**, auch bei aktiver Content Bridge. Sie versteht **beide** bestehenden WP-ID-Darstellungen (`wpstory-` und `wpfn-`) und listet im Editor die wirksame Auswahl sowie fehlende IDs. **Manueller Modus füllt nie stillschweigend aus dem Gesamtbestand auf**. Eingetragene, zeitweise ungültige numerische Referenzen bleiben für die Fehlerdiagnose sichtbar, werden aber nicht als Beiträge gerendert.

Die vorhandenen Farbfelder sind nun bei festem Theme sichtbar und technisch deaktiviert; erst bei `Individuelle Farben` werden sie bearbeitbar. **Die bestehenden Nature-CSS-Styles selbst werden nicht global verändert.** Nach Änderung von Quelle/Modus/IDs/Theme/Limit aktualisiert sich die Editorauflösung.

**Unverändert:** Home-/Hero-/Header-/Footer-Struktur, Reihenfolge aller Module, WHY und Launch Control, Content Composer, RGB Registry, Staging-/Live-Navigation, WordPress-Post-/Meta-Status und sämtliche Inhalte. Keine neuen Publikations-/REST-/Sitemap-Adapter, keine Datenbankmigration. Das Paket enthält die vorherige 0.1.43-Private-Preview-Korrektur auch für Staging-Sites, die noch 0.1.42 zeigen.

## QA und Release

- **19/19 JS-Runtime-Auswahltests** (inklusive Bridge/Max-2, manuelle Reihenfolge, fehlerhafte/duplizierte IDs, leere Slots, alte/neue ID-Formate, Nature-Modus) plus **5 Strukturtests** bestanden.
- **6/6 PHP-Dateien** Lint OK, JS-Syntax OK, ZIP-CRC/Pluginroot OK.
- Byte-Diff zu 0.1.43: **4 Quelldateien geändert, 1 README ergänzt, keine entfernt**.
- **Keine reale WordPress-/Hostinger-/Browser-/visuelle Farb-/Cache-Abnahme.** Vor Installieren auf Live gesonderte Freigabe.

**Staging-Update (Chat-Artefakt):** `INSTALL-IN-WORDPRESS-ANDY-Home-Composer-0.1.44-MODULE-SOURCE-PARITY-01.zip` · SHA-256 `db9ca604e69886661a73bc2d1cd1dca4280fa097f688f9fdd3b0c3abb092bfd1`.  
**Rollback (Original-Baseline):** `INSTALL-IN-WORDPRESS-ANDY-Home-Composer-0.1.43-JOURNAL-IN-PLACE-PREVIEW-01.zip` · SHA-256 `219eaa1625cf581d4c372bd7410ee7234e9d1ab9f40e9baf4409ff9aa8ac6e53`.  
**Detailbericht im Chat:** `ANDY-MODULE-SOURCE-PARITY-01-HOME-COMPOSER-0.1.44-RELEASE-2026-11-25.md`.

## Prüfverfahren

1. **Nur auf geschütztem Staging**, nach Backup, Home Composer 0.1.44 installieren. Bisherige Staging-Version in WP-Pluginliste prüfen. Live unverändert lassen.
2. Fight-Night-WordPress-Modul öffnen: **Automatisch**, max. 2, speichern; Staging-Home prüfen: max. 2 aus dem tatsächlich geeigneten CMS-Datensatz.
3. **Manuell**, zwei im Editor **angebotene** Beitragsnummern eintragen; prüfen: genau diese zwei und ihre Reihenfolge. Eingabe einer nicht verfügbaren Referenz muss **Warnung/Leerstelle** statt Ersatzstory liefern.
4. Festes Theme Nature = sechs Farbfelder **inaktiv** und Nature-Preset auf Site. Theme **Individuelle Farben** = Felder aktiv, gespeicherte Farben nach Cache-Kontrolle auf derselben Staging-Home sichtbar.
5. Staging↔Live-Navigation, DE/EN, alte Module und private Preview vergleichen; anonymes Veröffentlichungs-/Sicherheitsgate weiterhin nicht abgenommen. Bei Fehler 0.1.43-Rollback.

## Verbindlicher gesamtmodularer Zielvertrag

**Nicht mit Fight-Night-Fix allein erledigt.** Das weitere [HOME-CURATION & GUIDED-TOUR-01](ANDY-JOURNAL-HOME-EDITORIAL-CURATION-GUIDED-TOUR-01-2026-11-25.md) benötigt einen einheitlichen Modul-Adapter:

| Eigenschaft | Zwingende Regel |
|---|---|
| Owner/Quellsystem | Klare Quelle: WP/Content Composer oder RGB, keine HTML-/Textkopie |
| Auswahl | Explizit **Manuell** oder **Auto**; kein unbemerkter Fallback |
| Referenzen | Nur tatsächliche Story-/Content-IDs, mit Locale/Gültigkeitsdiagnose |
| Limit | **Maximum gerenderter Inhalte**, nicht Fensterbreite des Sliders |
| Farbraum | Nur aktive Theme-/Farbdefinitionen editierbar; OnSite-Darstellung entspricht Editor |
| Audit | „konfiguriert → aufgelöst → renderbar“ inkl. Warnung bei Differenzen; kein erfundener Ersatzcontent |
| Sicherheitsstatus | `publish` nicht gleich öffentliche ANDY-Freigabe; 01C2B-Gate bleibt Pflicht |
| Komposition | Max. 1–2 zusammenhängende **Contentstücke pro Bereich über mehrere Module**; 8 Perspectives-Themen und Academy A–D bleiben auf ihren Gabelseiten |

**Weitere Umsetzung in Reihenfolge:** (a) modulübergreifende Source-/Limit-/Design-Diagnose im bestehenden Home Composer, (b) zentrale fünf-Bereiche-Home-Kuratierung mit 1–2 Story-Slots pro Bereich, (c) optionaler WHY-Button/Guided Tour aus der Launch-Control-WHY-Quelle, (d) öffentliche Freigabe erst nach 01C2B-Negativabnahme. **Kein neues Plugin und kein pauschaler Staging→Live-DB-Transfer.**