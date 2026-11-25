# ANDY Journal · SYSTEM-MAP-FOUNDATION-01 – Technical Release / PRE-STAGING

**25.11.2026 · Implementierter lokaler Release-Candidate: Content Composer 0.1.29 → 0.1.30.**  
**Status: lokal getestet, noch NICHT installiert / WordPress-E2E abgenommen. Kein öffentliches Graph-System und keine neue Veröffentlichung.**

**Fachliche Grundlage:** [SYSTEM-MAP-FOUNDATION-01 des Content-Threads](../content/ANDY-JOURNAL-SYSTEM-MAP-FOUNDATION-01-2026-11-25.md), [WHY & Progressive Content Release](../content/ANDY-JOURNAL-WHY-PROGRESSIVE-CONTENT-RELEASE-01-2026-11-25.md), [PRE-STAGING-Governance](ANDY-JOURNAL-PRE-STAGING-ADMIN-UND-LAUNCH-GOVERNANCE-2026-11-25.md).

## 1. Architekturentscheidung und Eigentümer

Keine neue Plugininstallation. **Content Composer** bleibt Owner der Story-/Sprach-/Themenreferenzen und erhält **einen kleinen, ausschließlich internen Relation-Store** als passives Register. **Launch Control** bleibt Owner von WHY, Coming-Soon-/Bereichsplanungen und der späteren öffentlichen Freigabeentscheidung. **WordPress-Posts** bleiben die einzige Content-Quelle. Home Composer, Gabelseiten und RGB Pilot bleiben unverändert. Es gibt keine neue zweite Contentverwaltung und keine duplizierte Artikel- oder WHY-Datenhaltung.

| Datenobjekt | Autoritative Quelle |
|---|---|
| Native Beiträge, Status, Titel, Permalinks | WordPress |
| Story-ID, DE/EN-Sprachpartner | Bestehende Option `andy_xm_registry_v01` des Content Composer |
| Academy- und Perspectives-Themenkeys | Bestehende Content-Composer-Funktionen |
| WHY DE/EN und vier Darstellungsmodi | `andy_why_home_v01` in Launch Control 0.2.1, falls installiert |
| Publikations-/Leseproben-Planung | Launch Control 0.2.0/0.2.1; 01C2B fehlt |
| **Neu: gerichtete, typisierte Beziehungen** | **`andy_system_map_edges_v01`**, revisionsgeführt und mit `autoload=false` |

**Wichtig zur Identität:** stabile `area:*` IDs für Arena, Fight Night, Academy, Research, Perspectives, Making of, Data und Lab; `topic:perspectives:<key>` und `topic:academy:a|b|c|d` direkt aus den vorhandenen Themen-Katalogen; `story:<existing-story-key>` nur bei gültiger registrierter Story mit tatsächlichem WP-Post. Historische Schlüssel `andy.native.<WP-ID>` bleiben **ausgeschlossen**, da die numerische Post-ID nicht umgebungsübergreifend portabel ist. **Keine automatische Neuanlage, kein alternativer ID-Layer.** Spätere Identitätsmigration in der bestehenden Registry ist ein eigener, geprüft durchzuführender Auftrag.

## 2. Tatsächlich implementiert

**Content Composer 0.1.30 – SYSTEM-MAP-FOUNDATION-01** mit neuem internem Menü **Beiträge → ANDY System Map**:
- Ein Relationdatensatz hat eigene stabile ID, Quell-/Ziel-ID, gerichtetes Prädikat aus kleiner erlaubter Liste, getrennte Aussageart (Funktion, Beobachtung, Befund, Hypothese, Analogie, offene Frage, Widerspruch), DE-/EN-Erklärung und unabhängige DE-/EN-Status `draft|approved|withdrawn`, Geltungsbereich, bis zu 8 Belegreferenzen, Herkunft, Editor, Zeit und komplette frühere Revisionen.
- Empirische Beobachtung, Befund und Widerspruch benötigen bei `approved` mindestens eine **Referenz**. Die Redaktion muss deren Glaubwürdigkeit separat prüfen: `approved` macht eine Behauptung **nicht wahr** und macht sie insbesondere **nicht öffentlich**.
- Der Store hat anfängliche Sicherheitslimits 80 Kanten und 30 vorherige Revisionen je Kante; bei Erreichen bewusstes **Stop-Gate**, kein unbemerktes Abschneiden.
- Administrator- und Nonce-Schutz, explizite Speichereinwilligung, Validierung von Endpunkten/Prädikaten/Belegen/Sprachen und Schutz gegen veraltete Formularstände (Revisionshash). Ein Revisionshash ist **keine transaktionale Sperre** für gleichzeitige Serveranfragen; separates Konfliktaudit bleibt möglich.
- Read-only-Funktion `andy_sm_internal_projection('de'|'en')` verweigert Ausgabe an nicht-administrative Aufrufer. **Kein öffentliches Rendering**, keine neuen Frontend-/REST-/Feed-/XML-Sitemap-/Markdown-/JSON-Endpunkte, keine automatischen Beziehungsvorschläge, kein WP-Post-Write.

**Byte-Diff:** gegenüber dem 0.1.29-Quell-ZIP nur 3 neue/geänderte Quelldateien: `andy-journal-content-composer.php` (Versions-/Ladeeintrag), `includes/system-map-foundation.php`, `README-SYSTEM-MAP-FOUNDATION-01.md`; **85 weitere bestehende Dateien unverändert**. Keine neue Theme-/Elementor-/RGB-Funktion, kein neuer Homepage-Renderer.

## 3. Lokale QA und Downloads

- **74/74 isolierte PHP-Funktions-/Negativtests** bestanden; unter anderem ID-Gates, Entwurf/Freigabe je Sprache, Knotenreferenzen, Nachweis-Pflicht für empirische Aussagen, Nicht-Admin-Blockade, Verlauf/Revision und fehlende öffentliche Hooks.
- **24/24 PHP-Dateien** syntaktisch geprüft. Keine zwingende `mbstring`-Abhängigkeit.
- ZIP-CRC und Plugin-Header verifiziert; **Rollback bytegleich** mit dem aus WordPress exportierten 0.1.29-Quellstand.
- **Keine** echte Hostinger-Installation, PHP-7.4-Runtime-, mehrbenutzer-transaktionale, Browser- oder Performance-Abnahme. System Map öffnet keine öffentlichen Daten.

| Chat-Artefakt (Binärarchive nicht in GitHub) | SHA-256 |
|---|---|
| `INSTALL-IN-WORDPRESS-ANDY-Content-Composer-0.1.30-SYSTEM-MAP-FOUNDATION-01.zip` | `38cbe7b0151312124962eab90a508862f65a167bd44492ad99ada22627fc5b36` |
| `ROLLBACK-ANDY-Content-Composer-0.1.29.zip` | `51a3b379864d3c3aa20f0b6bf6c553c709953e4d2c7c03e8827605eb88adf970` |

Weitere Details: `ANDY-SYSTEM-MAP-FOUNDATION-01-CONTENT-COMPOSER-0.1.30-RELEASE-2026-11-25.md` (Chat-Artefakt).

## 4. Integrationstest und Stop-Gate vor der Staging-Kopie

1. Vollständiges Hostinger-Backup (WP-Dateien, Plugins, DB, Uploads, insbesondere `andy_xm_registry_v01`). Tatsächlich installierten Content Composer 0.1.29 verifizieren; **inaktive alte 0.1.4 nicht aktivieren**.
2. Einzel-ZIP 0.1.30 installieren, 0.1.29 ersetzen. Unter **Beiträge → ANDY System Map** die vorhandenen Knoten anzeigen, zunächst keine Beziehung freigeben.
3. Optional `rel.arena.research` zwischen `area:arena` und `area:research` mit `provides_events_for`, DE/EN-Erklärung und Provenienz als **interne Entwurfskante** anlegen, neu laden, editieren und die Revision prüfen.
4. Bestehende Content-/Home-/Academy-/Perspectives-/Making-of- und RGB-Funktionen, DE/EN, Sitemap/A–Z unverändert prüfen. Bei Abweichung 0.1.29 als Einzel-Rollback verwenden; die neue Relation-Option bleibt nach Datei-Rollback inert, DB-Recovery gesondert.
5. **Keine öffentliche Map oder Preview-/WHY-Schaltung.** Auf künftiger geschützter Staging-Kopie getrennt testen, dass Live- und Staging-Storystatus/-IDs bei Importen synchronisiert werden, ohne Post-ID als globale Identität zu übernehmen.

## 5. Verbindlicher Next-Step-Vertrag

**PRE-STAGING-01C2B zuerst:** eine durchgängige, getestete Freigabe-/Sperrentscheidung über Home, Gabelseiten, native Posts, Sprachpartner, Suche, REST, Feeds, XML-Sitemaps, alte RGB-Assets und Cache/Media. Neue Map-/Exporte dürfen **nicht** vor diesem Gate öffentlich werden.

Danach:
- **SYSTEM-MAP-MVP-01:** kleine visuelle Macro-Knotenansicht plus zugängliche Text-/Listenansicht; alle Endpunkte/Beziehungen/Locales vor Anzeige durch dieselbe Freigabeentscheidung filtern.
- **SYSTEM-MAP-EXPORT-01:** passive sprachbezogene HTML-/Markdown-/JSON-Projektionen aus **derselben gefilterten** Datenbasis, kein zweites Autorensystem. Hidden WHY und gesperrte Knoten dürfen auch in Quelltext/Metadaten/Counts nicht leaken.
- **SYSTEM-MAP-GROWTH-01 und LAB-Adapter:** erst später; Evidenzprovenienz, Revisionshistorie, mögliche Widersprüche, kein autonomes Veröffentlichen.

**Redaktioneller Parallelauftrag:** Der Content-Thread liefert erste DE/EN-WHY-Texte, mögliche Kanten mit explizitem Aussage-/Evidenzstatus, Geltungsbereich und vorhandenen stabilen Referenzen; **keine** neuen WordPress-Beiträge/Pluginänderungen ohne eigene Freigabe. Ein Contentstück muss nicht zwangsläufig eine Kante liefern.

**Status dieses Commits: dokumentiertes lokales Softwareartefakt, kein WP-Release oder Publikationsnachweis.**