# ANDY – SEO, Homepage-Verknüpfung und Internationalisierung

Stand: 12. November 2026 · Arbeitspaket für Homepage- und Dokumentations-Launch.

## 1. Quellen und bereits vorhandener Stand

Homepage-Clickdummy V3: `ANDY_Coming_Soon/de/index.html`, `en/index.html`, `zh/index.html`, sprachneutrale Weiterleitung über `index.html`.
Die drei Sprachen verlinken bereits mehrfach auf:
`https://andy-arena-com.github.io/andy-wps-collaboration/andy-dokumentation-regeln-lab.html`.

Dokumentation DE (führende Beta-Arbeitsfassung):
`https://andy-arena-com.github.io/andy-wps-collaboration/andy-dokumentation-regeln-lab.html`.

Die tatsächliche öffentliche Homepage-URL war zum Zeitpunkt dieses Arbeitspakets nicht bestätigt. **Keine Domain erraten und keine toten Rücklinks veröffentlichen.**

## 2. SEO-Grundlagen der deutschen Dokumentation

Bereits im HTML der DE-Dokumentation eingerichtet:
- `<html lang="de">`, aussagekräftiger `<title>`, `meta description`
- `rel=canonical` auf die stabile GitHub-Pages-URL **ohne** `?v=...`
- `robots=index,follow` und OpenGraph-Basismetadaten
- Acht echte `<a href="#...">`-Kapitel-Links mit sprechenden Linktexten, bei bestehender JavaScript-Kapitelnavigation
- Kein `hreflang` für unpublizierte Sprachseiten

Wichtig: Fragmentnavigation einer Einzelseite verbessert die Auffindbarkeit der Abschnitts-Links, erzeugt aber **keine acht separat indexierbaren Dokumente**. Für dauerhaftes Kapitel-SEO eigene URLs mit echten HTML-Inhalten vorsehen.

## 3. Verbindliches Link-Konzept beim Homepage-Launch

Sobald die Live-Homepage-URL bestätigt und erreichbar ist:
1. Dokumentations-Header: Logo und ANDY Arena-Schriftzug als **ein** semantischer Link `<a href="LIVE_HOME">...`.
2. Kapitel 01: inhaltlicher Link `ANDY Arena erleben` → `LIVE_HOME/de/` (sofern diese URL tatsächlich existiert).
3. Dokumentations-Footer: `ANDY Arena – offizielle Website` → bestätigte Homepage-URL.
4. Kapitel 03 und 06: nur wenn passende Anker oder Seiten live sind, themenbezogene Links zu Fight Night/Lab/Score.
5. Homepage → Dokumentation: Links **nach Sprache** und **Thema**. Vorerst DE-Doku bei EN/ZH ausdrücklich als deutsch kennzeichnen, statt eine Übersetzung vorzutäuschen.

**Nicht:** viele identische Links oder künstliche „Backlinks“ zur Rankingspekulation. Von der Homepage zur Doku und zurück ist hauptsächlich sinnvolle Navigation und thematische interne/verbundene Verlinkung.

## 4. Sprach-Roadmap

| Priorität | Sprache | Sprachcode | Motivation |
|---|---|---|---|
| 1 | Deutsch | `de` | redaktionelle Ausgangsfassung |
| 1 | Englisch | `en` | internationale Go-, Schach- und KI-Community |
| 1 | Vereinfachtes Chinesisch | `zh-Hans` / ggf. `zh-CN` | chinesischsprachige Go-Community; Homepage hat schon `zh/` |
| 2 | Japanisch | `ja` | Go-Tradition, KI-/Game-Community |
| 2 | Koreanisch | `ko` | zentrale Go-Community; für Zielgruppe wichtiger als viele andere Lokalisierungen |
| 3 | Traditionelles Chinesisch | `zh-Hant` / ggf. `zh-TW` | Taiwan und Nutzer traditioneller Schriftzeichen |

Es gibt drei **Schriftsprachen** in der ersten Homepage-Version: DE, EN und vereinfachtes ZH. `ch` ist **kein** Sprachcode für Chinesisch; korrekt ist `zh`, spezifischer `zh-Hans` oder `zh-Hant`.

Empfohlene eigenständige Dokumentationspfade nach Abstimmung mit dem Homepage-Hosting:
- `/docs/de/`
- `/docs/en/`
- `/docs/zh/`
- `/docs/ja/`
- `/docs/ko/`
- `/docs/zh-hant/` (später)

Bis der endgültige Dokumentations-Host feststeht, diese Pfade **nur als Zielstruktur** verstehen, nicht als tatsächlich live vorhandene URLs. Auf GitHub Pages zunächst lokalisierte Dateien je Sprache mit eigener URL verwenden; später mit Redirect/Canonical sauber auf den endgültigen Host umziehen.

## 5. Übersetzungs- und Nachweiskonzept

- Eine inhaltliche Quellversion (DE) mit festen Kapitel-IDs `intro, arena, lab, rules, challenge, score, development, collaboration` und Regel-IDs `R-01...`.
- Pro Sprache eine **vollständige** eigenständige HTML-Seite oder Kapitel-Seite mit `<html lang="...">`, lokalisierter Navigation, Titel, Description und interner Linkstruktur.
- Schema, Protokoll-IDs und maschinenlesbare Bewertungsformeln nicht übersetzen; nur Beschreibungstexte und Beispiele sprachlich übertragen.
- Fester Glossarstatus für: ANDY-Score, AKS, AQP, KO/TKO, Strategic Turning Point, Go-Setup, Strategy, Execution.
- Fachliche und muttersprachliche Prüfung insbesondere für Go-Terminologie, Schachterminologie und chinesische Zeichenvarianten.
- Freigegebene Sprachseiten wechselseitig mit **vollständigen reziproken** `hreflang`-Links verknüpfen, einschließlich Selbstreferenz. Nicht vorhandene oder unvollständig übersetzte Seiten ausschließen.
- Jede Sprachseite **selbst-kanonisch**; keine EN/ZH/JA/KO-Seite kanonisch auf die deutsche Seite setzen.
- `x-default` nur für eine wirkliche sprachneutrale Auswahl- oder Weiterleitungsseite.
- Sprachumschalter ausschließlich zu erreichbaren Seiten; niemals eine deutsche Seite als scheinbar japanische Variante ausweisen.

## 6. Homepage-Release-Check

Clickdummy V3 enthält `meta name="robots" content="noindex,nofollow"` in DE/EN/ZH und im Root-Redirect. Vor Launch gemeinsam prüfen:
- `noindex,nofollow` der öffentlichen Homepage-Landingpages entfernen; einen noch unfertigen rechtlichen Stand nicht unbemerkt veröffentlichen.
- Für jede echte Homepage-Sprache Self-Canonical und gültige reziproke `hreflang`-Links auf öffentliche URLs.
- Logo, Interaktions-/FAQ-Links, Impressum, Datenschutz und mobile Darstellung.
- Docs-Rücklinks mit echtem Homepage-Ziel, nicht mit relativen GitHub-Pages-URLs.
- Sitemap für **publizierte** Sprachversionen, ohne Platzhalter.
- Nach Launch: URL-Inspektion, Rendering und Linkprüfung in der Search Console.

## 7. Nächste Integrationsstufe

Regelwerk → Engine → Lab → Leaderboard: Jede öffentliche Wertung verweist auf Methodik, Daten und Feature. In der Doku sollten Score, AQP und R-01 bis R-06 später eigene indexierbare Inhaltsseiten bekommen, ohne die bestehende Gesamtdokumentation als Leseroberfläche aufzugeben.

Quellen zur allgemeinen SEO-Implementierung:
- https://developers.google.com/search/docs/crawling-indexing/links-crawlable
- https://developers.google.com/search/docs/specialty/international/managing-multi-regional-sites
