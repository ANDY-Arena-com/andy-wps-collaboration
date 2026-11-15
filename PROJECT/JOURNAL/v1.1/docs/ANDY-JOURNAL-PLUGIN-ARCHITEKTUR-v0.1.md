# ANDY Journal — Plugin-Architektur und Match Library v0.1

**Stand:** 15.11.2026  
**Status:** Architekturentscheidung und dokumentierter erster Praxistest; weitere Umsetzung offen.

## 1. Leitentscheidung

ANDY JOURNAL ist das öffentliche Forschungsmedium. Theme und individuelle ANDY-Funktionen bleiben entkoppelt. Ein gekauftes Premium-Theme ist weiterhin eine Option; die Theme-Entscheidung ist nicht Voraussetzung für die Plugin-Entwicklung.

Standardfunktionen möglichst mit WordPress und etablierten Plugins realisieren. Eigene Entwicklungsarbeit auf Academy, Replay und Forschungsinteraktionen konzentrieren. Keine pauschale Zusicherung der Kompatibilität mit anderen Themes oder Drittanbieter-Plugins.

## 2. Tatsächlicher Entwicklungsstand

| Komponente | Stand | Abnahme |
|---|---|---|
| ANDY Academy v0.1 | Installierbares Plugin, separate datenbasierte Sweet-Spot-Demo v1.0, ZIP-Import, Demo Library, Gutenberg-Block und Shortcode | Projektleitung meldet „funktioniert bestens“ auf aktueller Testsite |
| ANDY Replay v0.1 | Aus Webrelease ANDY_Arena_KOMPLETT_V0842_GitHub_Journal_IndexFix.zip gekapselter Theater-Replay-Player für das vorhandene Referenzmatch | Projektleitung meldet „funzt perfekt“ |
| ANDY Journal Theme v0.3 | Aktuelle Testbasis | Layout-Polish und Plugin-Kompatibilitätsprüfung offen |

Die beiden Plugin-Praxistests sind Nutzerbestätigungen, keine unabhängige vollständige Testmatrix. Ein Test mit einem anderen Theme sowie umfassende Sicherheits-, Browser-, Mobil- und Drittanbieter-Kompatibilitätstests stehen aus. Die ZIP-Dateien werden mit diesem Dokument nicht in GitHub eingestellt.

Bisheriger Replay-Shortcode: `[andy_replay match="andy_0c0f7413fdf6" lang="de"]`. v0.1 ist auf das ursprüngliche Astra–Argon-Replay zugeschnitten; keine allgemeine Match-Importfähigkeit behaupten.

## 3. Zielarchitektur: One Player – Multiple Games – Individual Stories

Ein zentral gepflegter Replay-Player, eine zentrale Match Library und beliebig viele redaktionelle Einbindungen. Keine Player-Kopie je Artikel oder Spiel. Jede Partie wird nur einmal importiert und kann mehrfach genutzt werden.

### A. Zentrales Match Center

Eigenständige WordPress-Gabelseite: Auswahl veröffentlichter Matches, später Filter, Top 10, besondere Partien und Forschungsserien. Der Besucher kann zwischen verfügbaren Partien wechseln; alle nutzen denselben Player.

Vorgeschlagener Shortcode: `[andy_replay_library]`.

### B. Individuelle Match Stories

Ein bestimmtes Match in einem normalen WordPress-Beitrag, einer Seite, auf der Homepage oder in der Academy einbetten. Redaktioneller Titel, Text, Bildwelt und Analyse bleiben individuell.

Vorgeschlagene Schnittstellen:
- `[andy_replay match="andy_89e45631d2f6"]`
- optional Deeplink: `[andy_replay match="andy_89e45631d2f6" start="266"]`
- später Gutenberg-Block mit Matchauswahl.

Die neuen Schnittstellen sind Zielvorschläge, keine bereits implementierten Funktionen. Deeplinks referenzieren stabile Ereignis-IDs bzw. Entscheidungsnummern, nicht ungesicherte Array-Indizes.

## 4. Game Package (vorgeschlagenes Format)

```
andy_<match_id>_v1.0.zip
  manifest.json
  original/
    <match_id>.json
    <match_id>.jsonl
  replay.json
  story.json
  locales/
  media/
```

- manifest: Match-ID, Paket-/Schema-Version, Ruleset, Player-Kompatibilität, Prüfsummen.
- original: byte-identische Originaldaten, Herkunft und unverändertes historisches Ergebnis.
- replay: normalisierte Spielzustände/Ereignisse, aus den Originalen nachvollziehbar abgeleitet.
- story: redaktionelle Dramaturgie, Intro, Highlights, Kommentare, Tempo, Ergebnisinszenierung.
- locales: DE/EN, später 中文.
- media: Cover und optionale freigegebene Medien.

Originaldaten, abgeleitete Daten und Interpretation strikt getrennt. Keine nachträgliche Änderung historischer Resultate. Beispiel: andy_89e45631d2f6 bleibt ABORT/user_stopped unter v1.1; hypothetische Sättigungswertung nach v1.2 ausdrücklich getrennt.

Import nur durch berechtigte Administratoren, validiertes datenbasiertes ZIP-Format, keine ausführbaren PHP-/JS-Dateien aus Matchpaketen. Prüfsummen, sichere Pfadbehandlung, Größenlimits, erlaubte Dateitypen, Konflikt-/Versionsbehandlung und Veröffentlichungskontrolle vor Freigabe spezifizieren und testen. Keine API-Schlüssel oder internen Zugangsdaten publizieren.

## 5. Match Library / Replay Director

Zentral verwaltete Matchdaten, Kontrahenten, Einstellungen, Cover, Sprachen, Intro, Highlights, Ergebniszeremonie und Veröffentlichungsstatus. Mehrere Artikel können dasselbe Match referenzieren. Individuelle Story-Varianten und versionierte Einbindungen als spätere Erweiterung prüfen.

Theater-, Classic- und Analysis-Modus als Ziel; tatsächlich verfügbare Modi beim Player-Audit feststellen. Automatische Highlights für objektive Ereignisse (Schachgebot, Capture, illegaler Zug, Endbedingung) von redaktionellen Kommentaren trennen. Kein erfundener Spielverlauf, keine falsche Ergebniszeremonie.

## 6. Produktionsprozess

Factory erzeugt Originalpartien → Lab analysiert und selektiert → Game Package Exporter erstellt validierte Pakete → Journal-Redaktion importiert und gestaltet → Match Center und einzelne Beiträge nutzen denselben Player.

Top 10 ist zunächst eine kuratierte Auswahl, kein automatisch behauptetes wissenschaftliches Ranking. Veröffentlichungsfreigabe bleibt bei der Redaktion.

Academy analog: einmaliges Plugin, separat versionierte Demo-Pakete aus dem Academy-Thread. Derzeit nur unterstützte datenbasierte Renderer; komplexere Interaktionstypen benötigen gezielte Erweiterung. Gemeinsame technische Formatspezifikation auf GitHub vor unabhängigem Export durch weitere Threads.

## 7. Roadmap

| Version | Umfang |
|---|---|
| Replay v0.1 | Referenzmatch gekapselt; Nutzer-Praxistest bestanden |
| Replay v0.2 | Player von Match-Hardcodings entkoppeln; Paketimport, zentrale Library, Matchauswahl und individuelle Artikeleinbindung |
| Replay v0.3 | Komfortable Library-Verwaltung und Gutenberg-Block |
| Replay v0.4 | Replay Director und redaktionelle Highlights |
| Replay v0.5 | Standardisierter Exporter App/Lab |
| Replay v1.0 | Durchgängiger, abgenommener Produktionsprozess |

v0.2 bewusst ohne vollständigen Director: zunächst story.json nutzen. Drei unterschiedliche reale Referenzpartien als Regressionstest, vorhandenes Originalreplay unverändert funktionsfähig erhalten. Prüfen: richtige Akteure, Farben, Konfiguration, Spielzustände, Captures, Tokens, Endzustände und Zeremonie; falsche Match-ID, fehlerhafte ZIPs, Versionskonflikte, mehrere Einbettungen auf derselben Seite, Theme-Wechsel, responsive Darstellung, keine zusätzlichen KI-Aufrufe. Originaldaten nur bei expliziter Publikationsfreigabe öffentlich zugänglich machen.

## 8. Zuständigkeiten und Grenzen

Journal: Plugin-Integration, Publikation, Story-Dramaturgie. Academy: Lernmodule und kompatible Demo-Pakete. App/Factory/Lab: Originaldaten, Replay-Export und Analyse. Gemeinsame Spezifikationen in GitHub. Keine parallele Spielengine entwickeln.

Keine Änderung an Arena-Website, öffentlicher Coming-Soon-Seite, Theme oder historischen Daten durch dieses Memo. Keine Implementierungs- oder Live-Freigabe für die geplanten Versionen.
