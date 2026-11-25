# ANDY Journal – WHY & Progressive Content Release 01

> **Technischer Umsetzungshinweis – WHY-01A / PRE-STAGING-01C2A (25.11.2026):** [Launch Control 0.2.1 als lokaler Release-Candidate](../ARCHITECTURE/ANDY-JOURNAL-PRE-STAGING-01C2A-WHY-01A-RELEASE-2026-11-25.md). Der **dauerhafte WHY-Editor für fünf Home-Bereiche** (DE/EN, vier Modi, getrennte Daten) und eine **diagnostische** Einzelfreigabe-Kandidatenliste wurden implementiert und isoliert getestet. **Der öffentliche WHY-Renderer wird noch nicht aufgerufen; die Freigabeentscheidung schützt noch keine URLs.** WHO/WHY-01 in Gabel-/Contentseiten und PREVIEW-CONTENT mit echter öffentlicher Wirkung folgen erst nach 01C2B-Sicherheitsgate und Staging-Abnahme. Dieses Dokument bleibt fachliche Quelle; keine rückwirkende Behauptung einer vollständigen Feature-Freigabe.

**25.11.2026 · Fachlicher Input aus dem parallelen Content-/Konzept-Thread, durch die Projektleitung zur technischen Kenntnis gegeben.**  
**Status:** Zukunftsanforderung für redaktionelle und technische Abstimmung, **noch keine Plugin-Implementierung, öffentliche Freigabe oder Staging-Abnahme**. Die zehn Kapitel unten halten das übermittelte Konzept in seiner Gliederung fest; ergänzende technische Integrationsregeln folgen in §11.

**Zentraler Leitsatz: Am Anfang dominiert das Warum, später das Was.**

## 1. Zielsetzung

Die erste öffentliche Version des ANDY Journals soll bereits das **Gesamtkonzept verständlich vermitteln** und zugleich **einzelne echte, vollständig lesbare Inhalte** anbieten. Während der Coming-Soon-Phase steht die Funktion der Bereiche und ihres Zusammenspiels im Vordergrund. Mit wachsendem Contentbestand tritt die erklärende Ebene zurück, bleibt aber dauerhaft verfügbar.

## 2. Bestehende Architektur erhalten

- Vorhandene Plugins, Home-Module, Gabelseiten und Content-Templates weiterverwenden.
- Bestehendes Launch Control als zentrale Veröffentlichungssteuerung nutzen.
- Live und Staging nutzen dieselbe technische Architektur mit getrennten Daten/Freigaben.
- **Content bestimmt Gabelseite; Gabelseite bestimmt Home.**
- Keine separate Coming-Soon-Site, keine redundante Inhaltsverwaltung.

## 3. Neue Funktion: WHY

**WHY ist eine dauerhafte redaktionelle Orientierungsebene, nicht lediglich temporärer Coming-Soon-Text.**

| Ebene | Redaktionelle Frage |
|---|---|
| **Home-Modul** | Warum existiert dieser Bereich innerhalb von ANDY? |
| **Gabelseite** | Welche Funktion haben Themen und Contenttypen dieses Bereichs? |
| **Contentseite** | Warum ist der konkrete Inhalt relevant, und wie hängt er mit anderen Inhalten zusammen? |

DE und EN müssen separat redaktionell bearbeitbar sein.

## 4. Individuell steuerbare Darstellung

Die WHY-Sichtbarkeit ist **unabhängig** von Veröffentlichungsstatus oder öffentlicher Erreichbarkeit steuerbar:

| WHY-Modus | Darstellung |
|---|---|
| **Prominent** | Erklärung direkt und vollständig sichtbar |
| **Kompakt** | Kurzer Text, optional erweiterbar |
| **Optional** | WHY-Button öffnet den Erklärungstext |
| **Ausgeblendet** | Kein öffentliches WHY-Element |

Die Modi sollen perspektivisch pro Modul, Gabelseite und Contentseite konfigurierbar sein, bei gemeinsamem Design und ohne redundante Renderer. Coming Soon nutzt vorzugsweise „Prominent“; später ist ein Wechsel ohne Neuerstellung des WHY-Textes möglich.

**Präzisierung für die Implementierung:** Der Modus steuert nur **die Darstellung**. Er gewährt weder selbst Zugriff auf eine gesperrte Seite, noch macht er geschützte WHY-Texte über API, JSON oder Quelltext öffentlich.

## 5. Coming Soon mit echten Leseproben

Ein Coming-Soon-Bereich darf kombinieren:
- WHY-Erklärung;
- Einführung und Ausblick auf geplante Inhalte/Funktionen;
- **mindestens einen ausdrücklich freigegebenen, vollständig lesbaren Beispielartikel in DE/EN, sofern redaktionell verfügbar**.

Dafür werden **native WordPress-Beiträge**, keine Kopien oder neuen parallelen Contentobjekte verwendet. Die gezielte Freigabe eines Beispielartikels **öffnet niemals automatisch alle Inhalte** seines Coming-Soon-Bereichs.

Direktaufrufe, Sprachpartner, WordPress-Suche, REST, Feeds, Sitemap und Cache müssen in die Sicherheitsprüfung einbezogen werden. Vorschau/Teaser dürfen nicht behaupten, dass ungeprüfte Funktionen oder Artikel bereits verfügbar seien.

## 6. Inhaltliche Vernetzung

Perspektivisch erklärt WHY die Verbindungen der Bereiche:

- **Research** untersucht Arena-Daten und stellt Evidenzfragen.
- **Perspectives** erkundet mögliche Bedeutung außerhalb des Spiels.
- **Academy** vermittelt Wissen für selbstständiges Verstehen/Nutzen.
- **Making of** reflektiert die gemeinsame Entwicklung.

In der ersten Stufe reichen editierbare Erklärungstexte. Strukturierte Beziehungen, Querverweise und semantische Navigation sind spätere Erweiterungen. **Jetzt kein komplexes Netzwerk-/Graph-System implementieren.**

## 7. Kommunikative Grundlage: GAME 4 LAB / ANDY Flywheel

**Erlebnis → Motivation → Nutzung → Daten → Erkenntnisse → Kommunikation → neues Erlebnis.**

Dieser Kreislauf ist die konzeptionelle Grundlage der WHY-Erklärungen. Die Bereiche besitzen sowohl eine Funktion innerhalb des Flywheels als auch eigenständigen Nutzen. **Es handelt sich um ein Zielmodell, nicht um einen empirisch nachgewiesenen Motivationseffekt.**

## 8. Vom Content-Thread vorgeschlagene Entwicklungsinkremente

- **WHY-01 – Technische Basis:** DE/EN-Datenmodell, editierbare WHY-Texte, gemeinsame Darstellung, vier Modi, Home-Ebene.
- **WHY-02 – Vertiefung:** Gabelseiten, optional Contentseiten, gemeinsame Gestaltung.
- **PREVIEW-CONTENT-01 – Leseproben:** explizite Einzelfreigaben bei `coming_soon`, bestehendes Launch Control, Prüfung sämtlicher öffentlicher Zugriffspfade.
- **WHY-03 – Vernetzung (später):** strukturierte Beziehungen, Content Contract, Editorial Bible, semantische Navigation.

Technische Reihenfolge mit PRE-STAGING-Arbeitspaketen abstimmen. **Sichere Publikations- und Zugriffskontrolle hat Vorrang vor der ersten öffentlichen Aktivierung.**

## 9. Arbeitsteilung

**Technik-Thread:** Datenmodell, Editoren, Renderer, Launch Control, Freigabeschicht, Live/Staging-Kompatibilität, Regressionstests.

**Content-/Konzept-Thread:** Gesamtstory, DE/EN-WHY-Erklärungen, Gabelseiten-Einführungen, freizugebende Beispielartikel, Bildkonzepte, inhaltliche Beziehungen.

Währenddessen **keine Plugins durch den Content-Thread ändern**.

## 10. Abnahmekriterien des übermittelten Konzepts

- Bestehende Home und Contentfunktionen bleiben erhalten.
- WHY-Text ist in DE/EN editierbar und der Sichtbarkeitsmodus unabhängig vom Bereichsstatus wählbar.
- Eine freigegebene Leseprobe ist in Coming Soon tatsächlich vollständig lesbar; andere interne Inhalte bleiben geschützt.
- Beim Wechsel zu Live bleiben WHY-Inhalte erhalten.
- Keine redundante Content-/Plugin-Architektur, kein Überschreiben vorhandener redaktioneller Daten oder Einstellungen.
- Aktuelle installierte Pluginstände vor neuer Entwicklung prüfen; keine alten Entwicklungspakete als neue Basis verwenden.

## 11. Technische Einordnung für PRE-STAGING-01C2 / WHY / PREVIEW-CONTENT

Dieser Abschnitt ist **eine technische Integrations-Empfehlung zu den gelieferten Anforderungen**; nicht Teil des wörtlichen redaktionellen Konzepts und **noch keine Abnahme**.

### 11.1 Drei getrennte Dimensionen

1. **WordPress-Status / Redaktion:** `post_status`, sprachbezogene redaktionelle Prüfung, Rückzugsmarker und Veröffentlichungshistorie.
2. **Bereichsfreigabe:** `internal` / `coming_soon` / `live`; bei `coming_soon` zusätzliche **explizite Post-Allowlist** für Leseproben, keine Vererbung von Freigaben an andere Posts.
3. **WHY-Darstellung:** `prominent` / `compact` / `optional` / `hidden`; beeinflusst nur die Präsentation **bereits autorisierter** Seiten/Elemente.

Eine hohe WHY-Prominenz darf keine Bereichssperre übersteuern. Der durch Content definierte Gabel-/Home-Aufbau bleibt die einzige Quelle für redaktionelle Daten. **Keine nachträgliche automatische `publish`-Mutation** bei Bereichswechsel.

### 11.2 Empfohlene Autorisierungsregel (Zielvertrag, nicht implementiert)

Für einen **öffentlichen einzelnen Standard-Artikel** muss mindestens gelten:

```text
post.status == "publish"
AND editorial_review_for_current_locale == approved
AND NOT editorial_withdrawn
AND (
     area.mode == "live"
     OR (area.mode == "coming_soon" AND post_id_is_explicitly_approved_preview)
)
```

`area.mode == "internal"` sperrt den öffentlichen Zugriff auf Bereich und Beiträge grundsätzlich; Ausnahmen gelten nur für berechtigte WP-Preview-/Redaktionssitzungen. Unbekannte Bereichszuordnung, widersprüchliche Mehrfachzuordnung und nicht geklärte Altveröffentlichungen bedürfen einer **bewussten, sicheren Default-Regel** (nicht automatisch freigeben). Eine DE-Leseprobe impliziert **keine automatische EN-Freigabe** und umgekehrt. Ob die bisherige Editorial-Workflow-Prüfung ein verbindliches `approved`-Flag bereitstellt, muss der Code-Audit zeigen; dieses Feld ist **kein bestätigter vorhandener Datenbankschlüssel**.

**Wichtig:** Eine Datei in der öffentlichen WordPress-Mediathek kann unabhängig von der Sichtbarkeit eines Posts direkt erreichbar bleiben. Für unveröffentlichte/vertrauliche Assets darf daher kein WP-Uploads-Schutz allein durch die Artikel-Allowlist behauptet werden.

### 11.3 Reihenfolge gegen PRE-STAGING

| Schritt | Umsetzung und Gate | Öffentliche Wirkung |
|---|---|---|
| **01C1 – vorhanden** | Launch Control 0.2.0 mit DE/EN-Kurz-Teasern und geplanter Bereichsfreigabe; in Nutzer-Screenshot im WP-Admin sichtbar | **Keine wirksamen Routen-/Zugriffssperren** |
| **01C2 – zuerst** | Gemeinsamer Autorisierungs-/Routing-Vertrag für Area- und Post-Status; Inventur der tatsächlichen Composer-, Making-of-, RGB-, WP-Suche-/REST-/Feed-/Sitemap-/Cache-Pfade | Erst nach vollständiger Regression/Berechtigungsprüfung und expliziter Freigabe |
| **WHY-01 – technisch parallel vorbereitbar** | Gemeinsame DE/EN-Daten und WHY-Modi, redaktioneller Editor, nichtöffentliche Anzeige-Tests auf vorhandenen Modulen | Zunächst **keine** ungeprüfte öffentliche Anzeige |
| **PREVIEW-CONTENT-01 – nach 01C2-Gate** | Explizite, pro Post/Sprache freigegebene Leseproben innerhalb `coming_soon` | Nur freigegebene Posts, danach Negativtests sämtlicher sonstiger Zugriffe |
| **WHY-02** | WHY auf Gabelseite und Content; UI/Accessibility, Mobile, Sprachwechsel | Nur auf bereits freigegebenen Seiten |
| **WHY-03 – später** | Semantische Beziehungen/Flywheel-Navigation | Getrennte redaktionelle/technische Freigabe |

**Kein neues WHY-Plugin per Voreinstellung:** Datenhaltung/Editor als kleiner Erweiterungsvertrag im vorhandenen Content-/Launch-System, gemeinsamer Renderer/Adapter in bestehenden Composern. Die genaue Ownership erst nach Quellprüfung der **tatsächlich installierten** Stände entscheiden.

### 11.4 Kritische Regressionstests vor wirksamer Freigabe

- DE- und EN-Home, fünf Gabelseiten, native Posts, Browser-Direktlinks, Legacy-RGB-Assets, Academy/Perspectives/Making-of-Pfade.
- Bei Coming Soon: **ein freigegebener Post erlaubt**, zweiter publizierter Post derselben Kategorie **gesperrt**; Entwurf gesperrt; zurückgezogen gesperrt; fremde Sprache gesperrt; `internal` sperrt alles.
- WP-Suche, RSS/Feeds, REST, XML-Sitemaps und Vorschaukarten zeigen nur autorisierte Inhalte; Sprachwechsel nur auf erlaubte Partner.
- LiteSpeed/WordPress/CDN-Cache nach Umschaltung invalidieren, angemeldete Redaktionsvorschau von anonymen Nutzern trennen; `noindex` nicht als Zugriffsschutz behandeln.
- Keine Änderung der bestehenden Home-Designdaten, Elementor-Header/Slider, des globalen Footers und der WordPress-Beitragsstatus; Rollback und Datenmigration separat prüfen.

## 12. Links / Synchronisation

- [Content-Handoff Coming Soon DE/EN](ANDY-COMING-SOON-CONTENTKONZEPT-HANDOFF-2026-11-25.md)
- [Launch Control 0.2.0 / PRE-STAGING-01C1](../ARCHITECTURE/ANDY-JOURNAL-PRE-STAGING-01C1-PUBLICATION-PLANNING-RELEASE-2026-11-25.md)
- [PRE-STAGING Governance](../ARCHITECTURE/ANDY-JOURNAL-PRE-STAGING-ADMIN-UND-LAUNCH-GOVERNANCE-2026-11-25.md)
- [Making-of-Katalog / MO12](ANDY-MAKING-OF-STORY-KATALOG-v0.1-2026-11-25.md)

**Dokumentation und technische Einordnung sind kein WordPress-Release, keine Beitragsfreigabe und kein Beleg, dass Content-/WHY-Entwürfe bereits öffentlich sind.**

## 13. Weiterführender fachlicher Handoff: System Map (25.11.2026)

[ANDY JOURNAL – SYSTEM-MAP-FOUNDATION-01](ANDY-JOURNAL-SYSTEM-MAP-FOUNDATION-01-2026-11-25.md) ergänzt die bisherige WHY-03-Perspektive um einen **frühen schlanken semantischen Datenvertrag**, eine gemeinsame öffentliche Projektion für visuelle System Map und maschinenlesbare Exporte sowie den späteren Lab-Anschluss. Die Graph-Basis soll bereits bei den ersten vernetzten Leseproben berücksichtigt werden; kein komplexes Graph-System als Launch-Pflicht. Die bestehenden WHY-Modi und 01C2-Sicherheitsgates bleiben unverändert. Technische Detailentscheidung und Abnahme beim Technik-Thread.
