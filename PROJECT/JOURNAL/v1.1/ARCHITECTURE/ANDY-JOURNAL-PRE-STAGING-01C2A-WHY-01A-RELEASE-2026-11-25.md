# ANDY Journal – PRE-STAGING-01C2A & WHY-01A · Release- und Übergabevertrag

**25.11.2026 · Lokaler WordPress-Release-Candidate, 116/116 isolierte Checks bestanden.**  
**Weder in WordPress installiert noch öffentlich abgenommen.** **Keine öffentlichen Freigaben oder Zugriffssperren implementiert.**

Quellen: [WHY & Progressive Content Release 01](../content/ANDY-JOURNAL-WHY-PROGRESSIVE-CONTENT-RELEASE-01-2026-11-25.md), [Launch Control 0.2.0, PRE-STAGING-01C1](ANDY-JOURNAL-PRE-STAGING-01C1-PUBLICATION-PLANNING-RELEASE-2026-11-25.md), [PRE-STAGING Governance](ANDY-JOURNAL-PRE-STAGING-ADMIN-UND-LAUNCH-GOVERNANCE-2026-11-25.md).

## Ausgangsbasis und Abgrenzung

Der letzte Nutzerscreenshot bestätigt **ANDY Launch Control 0.2.0** auf \`journal.andy-arena.com\` mit erreichbarem Reiter **Publication & Coming Soon**, nicht aber dessen gesamte Formularpersistenz oder Browser-/Routensicherheit. Laut vorausgehender Nutzerabnahme ist **Cockpit 0.2.3** installiert, **RGB Pilot 0.6.4** und **Home Composer 0.1.39** wurden positiv geprüft, **Content Composer 0.1.29** war die aktive Quellbasis. Diese fachlichen Plugins werden **nicht** durch dieses Inkrement verändert.

**In-place-Plugin-Update \`andy-launch-control\` 0.2.0 → 0.2.1.** Gleicher Pluginordner, kein neues System; die bisherigen vier Pilot-Tabs, die Veröffentlichungsvorbereitung 01C1, der opt-in Historientracker, die Notizen und der redaktionelle Rückzugsmarker bleiben erhalten. \`plan.json\` und \`crossover-source.html\` sind **bytegleich**.

## A. WHY-01A: dauerhafte Home-Orientierungsdaten

- Für **Fight Night, Academy, Research, Perspectives und Making of** je DE/EN eine selbst editierbare WHY-Überschrift, Kurzfassung (330 Zeichen) und Langfassung (2500 Zeichen).
- WHY-Modus pro Home-Bereich, unabhängig von \`internal\`/\`coming_soon\`/\`live\`: **prominent**, **compact**, **optional**, **hidden**.
- Additive Option \`andy_why_home_v01\` mit strengem Array-Schema, Administrator-/Nonce-/Bestätigungsprüfung, Revisions-Hash gegen paralleles Überschreiben, bereinigten und bei Ausgabe escapten Texten.
- Read-only-API \`alc_why_home_data(area, lang)\`; eigener HTML-Renderer \`alc_why_home_render(area, lang)\` mit nativen \`details/summary\` für einklappbare Modi. **Dieser Renderer ist noch in keiner öffentlichen Home eingebunden.** Die tatsächliche Home und sämtliche Composer bleiben unverändert.
- WHY auf Gabel- und Contentseiten (**WHY-02**) folgt erst nach getrenntem Adapter-/Sicherheitscheck. Keine zweite Contentdatenbank, kein zweites Home-Plugin.

## B. PRE-STAGING-01C2A: Policy-Kern und Leseproben-Kandidaten

**Reine interne/diagnostische Freigabeentscheidung**, nicht die öffentliche Durchsetzung:

- \`alc_policy_decide(context)\` ist ein deterministischer, **fail-closed** Autorisierungsvertrag. Für einen öffentlichen WP-Post: \`post_status=publish\`, ohne Passwort, nicht als intern markiert, nicht \`_andy_ew_translation_pending\`, nicht redaktionell zurückgezogen, mit gültiger ANDY-Bereichszuordnung und eindeutiger DE/EN-Sprachzuordnung.
- Bereichsstatus: **internal** verweigert immer; **live** erlaubt nur bereits gültige Post-/Sprachkontexte; **coming_soon** erfordert zusätzlich einen explizit vorgemerkten, zur **Post-ID + Bereich + Sprache** passenden Leseproben-Kandidaten. Eine DE-Freigabe öffnet keinen EN-Partner.
- \`alc_policy_evaluate_post(id, lang)\` liest bestehendes \`_andy_cc_template\`, \`_andy_mo_story\`, \`andy_lr_lang\` und den vorhandenen 01C1-Bereichsplan. Nicht eindeutig klassifizierte Beiträge oder Standardseiten haben keine implizite Erlaubnis. **Keine unbewiesene Zuordnung über Kategorien oder Slugs.**
- Im vorhandenen Tab neuer **PREVIEW-CONTENT**-Adminbereich für Vormerken/Entfernen von höchstens 40 **tatsächlich veröffentlichten, eindeutig zugeordneten** Post-IDs. Option \`andy_pub_preview_candidates_v01\`, reine Planung, keine Veröffentlichungs- oder Routewirkung. Admin-POST, Nonce, explizite Bestätigung, Revisionsschutz; Entwürfe, fremde Sprachfassungen, redaktionelle Rückzüge und interne Posts werden abgelehnt.
- **Keine neuen öffentlichen WordPress-Hooks** (\`parse_request\`, \`template_redirect\`, \`pre_get_posts\`, REST, Suche, Feeds, Sitemap). **Keine Statusmutation, keine neue URL oder Freigabe.** Die geplante Entscheidung darf gegenüber Nutzern nicht als bereits wirksamer Schutz dargestellt werden.

## Quellcode- und Paketnachweis

| Artefakt | SHA-256 |
|---|---|
| \`INSTALL-IN-WORDPRESS-ANDY-Launch-Control-0.2.1-PRE-STAGING-01C2A-WHY-01A.zip\` | \`9b64dc1ded203472dc87ea012eb1e61092ea7409b2c8b118f528e1786789394c\` |
| \`ROLLBACK-ANDY-Launch-Control-0.2.0.zip\` | \`1999dc0a0999cd25fa720a48ce7f50af67ef9bab4edf09bd9a094e93800374fd\` |

Beide Archive sind **WordPress-Einzelplugin-ZIPs** mit genau einem Ordner \`andy-launch-control/\`, **9 neue Release-Dateien**, **6 Original-Rollback-Dateien**. Sämtliche Rollback-Dateien mit der aus dem Nutzer-Handoff bekannten installierten 0.2.0-Baseline bytegleich verifiziert. CRC erfolgreich, PHP-Lint **4/4 PHP-Dateien**, **116/116 isolierte PHP-WordPress-Facade-Assertions** bestanden (Validierung, Speichern, Revisionsabgleich, Sprachzuordnung, Policy-Ausnahmen und Negativfälle; kein Live-WP).

Die installierbaren Binärpakete und der ausführliche Releasebericht \`ANDY-PRE-STAGING-01C2A-WHY-01A-RELEASE-2026-11-25.md\` wurden **nur im Chat** ausgegeben. Kein Binär-Commit ins Repository.

## Installations- und Stop-Gate

1. **Vollständiges Production-Backup** inklusive DB, Uploads, RGB-Optionen und bestehender Pluginversionen. Aktuell installiert: Launch Control **0.2.0** (per Nutzer-Screenshot).
2. **0.2.1-Einzel-ZIP** installieren; bei vorhandenen Plugins Update desselben Ordners bestätigen.
3. Unter **ANDY Journal → Launch Control → Publication & Coming Soon** alte Planungsfelder/Status prüfen; neue Bereiche **WHY** und **PREVIEW-CONTENT** müssen erscheinen. Für Research einen DE/EN-WHY-Text speichern, neu laden und Persistenz prüfen. Weder die Home noch Gabelseiten oder WordPress-Post-Status dürfen sich dadurch verändern.
4. Eine bereits publizierte und gültig zugeordnete Post-ID testweise als Leseprobe **vormerken**, Diagnose prüfen, wieder **entfernen**. Das ist keine Publikation. Nicht publizierte oder ungeprüfte Posts müssen abgewiesen werden.
5. DE/EN-Home, Header/Slider, Academy, Perspectives, Making of, RGB-Sitemap und A–Z sowie die früheren Launch-QA-Funktionen vergleichen. Bei Abweichung Original **0.2.0**-Rollback benutzen; neue, additive Optionen werden beim Rollback nicht gelöscht.

## Danach zwingend: PRE-STAGING-01C2B (noch nicht umgesetzt)

Öffentliche **Durchsetzung** derselben gemeinsamen Policy muss mit den tatsächlichen Quellpfaden von **Home Composer**, **Content Composer** (native Permalinks, Gabelseiten, Archive, Sprache), **Making of**, **RGB Pilot** (Legacy-Assets), WordPress-Suche, REST, Feed, XML-Sitemap und **LiteSpeed-/Hostinger-/CDN-Cache** integriert und **auf geschützter Staging-Kopie mit eigener Datenbank** samt positivem/negativem Browser- und API-Test abgenommen werden. Media-Uploads sind als separater direkter Dateizugriff zu berücksichtigen. Ein \`noindex\` ist **keine** Zugangssperre.

**Sicherheitsprinzip:** Vor voller 01C2B-Abnahme und ausdrücklicher Freigabe keine öffentlich wirksamen Bereichs- oder Leseproben-Schalter – einschließlich auf Production. Die bloße Installation von Launch Control 0.2.1 ändert daran nichts.

**Making-of-Thema:** Wiederverwendbare Funktionen, Quellen des tatsächlichen Codes, getrennte Geltungszustände und reversibles Vorgehen. Ein lesbarer, roter „NOCH NICHT ÖFFENTLICH WIRKSAM“-Hinweis ist Teil des Produkts, kein bloßes Testlabel.