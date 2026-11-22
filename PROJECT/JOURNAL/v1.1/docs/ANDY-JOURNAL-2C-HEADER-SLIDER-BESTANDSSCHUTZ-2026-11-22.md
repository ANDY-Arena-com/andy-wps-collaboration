# ANDY Journal – 2C: Header-/Slider-Bestandsschutz statt neuer Header-Entwicklung

**Stand:** 22.11.2026. **Status:** Diagnose-/Integrationsvorgabe; keine Änderung an WordPress, keine neue Pluginversion.

## Anlass
Nutzer-Screenshots vom 22.11.2026 zeigen im Admin unter `Werkzeuge → ANDY Journal · Module v0.4.2` die bestehenden nativen Elementor-Module:
- HOME · Hero und Content: WP-Seite **14**
- HOME · Header: **26** („Header One“)
- GLOBAL · Header: **532** („Header Two“)
- GLOBAL · Footer: **455** („Footer One“)
- Bestehende Workflows `Publishing · CONTENT-01 / HOME-02`, `DESIGN-01: applied`, `HOME-01 · Slider-Test`, `Journal: applied`. Das sind **historische Nutzer-/UI-Bestätigungen**, keine neue Live-Apply-Prüfung.
- Das Cockpit listet Content Manager, Publishing, Journal Module/Home, Design Import und RGB Pilot. Integrator und Editorial v2 sind zusätzliche Admin-Labore und sollen diese alten Funktionen nicht duplizieren.

## Frühere technische Implementierung (aus Archiv)
[WP-Baseline vom 17.11.](ANDY-JOURNAL-WP-BASELINE-2026-11-17.md) dokumentiert:
- **DESIGN-01:** Logo-Varianten, Sticky-/Home-Header-Design, Farben und Site-Identität;
- **HOME-01:** 3-reihiger nativer `wpsection_banner_slider` **1eef5e6** auf Seite 14, u. a. nativer Fade-/Overlay-/Responsive-Ansatz und selektive, freigegebene Importlogik;
- **CONTENT-01 / HOME-02:** 5 bereits native Essays und dynamische Publishing-Slots mit einem **Renderzeit-Hook**, der ursprünglich auf die native Zielinstanz wirkt (nicht gespeicherte Slider-Settings umschreibt);
- Gültiger Rollback-/Import-Weg im Content Manager; kein neuer konkurrenzierender Importer.

[Historisches Artefaktregister](ANDY-JOURNAL-ARTEFAKTE-2026-11-17.md) nennt die einzelnen Pakete sowie Prüfsummen. Diese Archive sind **nicht** automatisch auf dem laufenden Server oder in GitHub verfügbar, also niemals einen alten ZIP-Stand ungeprüft installieren. Aktuell meldete die 0.1-WordPress-Inventur Content Manager **0.4.6**, die native Adminansicht zeigt die **interne Modulrevision 0.4.2**; die Revisionsnummern nicht als vermeintlichen Widerspruch behandeln.

## Bestätigte 2A-Hard-Facts
Nutzerbericht `ANDY-INTEGRATOR-02A-20261122(1).json`:
- Seite **14**, Elementor-Widget-Count 37, 0 Widget-ID-Drift seit 0.1 (nicht seit 17.11.).
- Header **26**, Widget `5b651b3`, Typ `wpsection_header`, Feldnamen `image`, `sticky_logo`; ausgewiesene Medien-IDs **1310/1309**.
- Global-Header **532**, Widget `c0cb75f`, Typ `wpsection_header_two`, Felder `image`, `logo`, `sticky_logo`, `text`, `text1`, `btnlink`; ausgewiesene Medien-ID **1309**.
- Footer **455** existiert, 19 Widgets, globales Template nicht durch 2B editiert.
Die ursprüngliche Nov.-16-Baseline nennt andere Bild-IDs (Header 26: 137/138; Header 532: 135); Vergleich erst nach Untersuchung der tatsächlichen Medien und früheren Importfreigaben. **Keine automatische Rückstellung auf frühere IDs.**

## Technisch geprüfte Lücke des 2B-Entwurfs
Aus dem tatsächlich bereitgestellten `ANDY-WP-PLUGIN-Integrator-v0.2B.zip`:
- Der Generator erstellt eine zusätzliche WP-`page` mit `post_status=draft`; er kopiert `_elementor_data`, einige Standard-Elementor-Metafelder (`_elementor_edit_mode`, `_elementor_template_type`, `_elementor_version`, `_elementor_pro_version`, `_elementor_page_settings`, `_wp_page_template`) und ggf. `_thumbnail_id`.
- Eine tatsächliche **seitenbezogene Header-Override-Zuweisung** ist in dieser Kopier-Whitelist nicht ausdrücklich enthalten. Ob sie von Theme-Metafeldern oder Optionen gesteuert wird, ist **noch nicht geprüft**. Die Entwurfsseite ist zudem eine **andere WP-ID** als 14. Deshalb können Homepage-spezifische Header-/Slider-Hooks oder Template-Bedingungen im Entwurf anders wirken.
- 2B ändert ausdrücklich **nicht** die bestehenden Header-Elementor-Objekte 26/532, den Footer 455, die WordPress-Startseitenoption oder den Publishing-Hook.
- Der Slider im 2B-Entwurf übernimmt die zu Zeitpunkt der Kopie **gespeicherten** Slides und ersetzt Text/Links. Der früher dokumentierte **dynamische** CONTENT-01/HOME-02-Renderzeit-Hook muss separat auf Entwurfskompatibilität geprüft werden. Nicht behaupten, dass er auf der neuen Entwurfs-ID automatisch greift.
- Aktuell sichtbare Unterschiede der Header und Slider sind deshalb **plausibel** durch Header-Override-/Template-Bedingungen und/oder Slider-Laufzeithooks erklärbar, aber nicht endgültig auf diese zurückgeführt.

## Verbindliche Regeln für 2C
1. **Keine neuen Header neu erfinden oder Pakete reimportieren.** Bestehende Header **26/532** und Footer **455** als SSOT behandeln.
2. Vor Änderungen **Ist-Stand der Theme-Optionen, Header-Override-Metafelder und Publishing-/Slider-Renderhooks lesend auditieren**. Einstellungen nicht erraten.
3. **Nur private Entwurfskopie** so erweitern, dass sie das gewünschte Header-Verhalten und den zuvor bewährten nativen HOME-01-Hero **bewusst** erbt/abbildet. Kein Überschreiben von Seite 14 und kein Hook-Global-Patch ohne verifizierten Scope.
4. Für die nachfolgenden Content-/Bildarbeiten: 3 individuell bebilderte Slides, sehr unterschiedliche Editorial-Motive, originales ANDY-Logo und real vorhandene Inhalte. Aculia-Stockbilder erst nach Medienrechts- und Funktionsprüfung austauschen.
5. Aufruf `/` und `/?utm_source=chatgpt.com` deterministisch machen; Abweichung zwischen Aculia und RGB separat mit aktivem RGB-Standardmodus, Cache und Router untersuchen.
6. Laufzeit-/Browser-Abnahme von Draft und Root, mobil/desktop, sowohl bei eingeloggten als auch nicht eingeloggten Nutzern. Kein Frontend-Publish bis expliziter Freigabe.

**Erkenntnis:** Die Konvergenz ist nicht „Aculia neu gestalten“, sondern **frühere native DESIGN-01/HOME-01/CONTENT-01-Veränderungen** mit neuem RGB-Content und dem Editorial-v2-Mapping zu kombinieren. 2B war ein guter isolierter Content-Dry-Run, noch keine vorlagentreue Master-Home.
