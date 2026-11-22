# ANDY Journal Integrator 0.2A – Read-only Elementor-Feldaudit

**Datum:** 22.11.2026 · **Version:** 0.2.0 (Arbeitsschritt 0.2A) · **Status:** lokal gebaut/getestet, WordPress-Installation und Browserabnahme stehen aus. **Kein Deploy, kein Publishing.**

## Ausgangsdaten
- [Integrator-01-Matrix aus realer WordPress-Inventur](ANDY-JOURNAL-INTEGRATOR-01-MAPPING-20261122.md): 28 RGB-Knoten, 14 Editorial-Demos, 34 native Posts/Pages, 58 Aculia-Widget-Einträge.
- WordPress-Startseite: veröffentlichte Aculia-Seite **ID 14, Home Page 01**, mit 37 Elementor-Widgets.
- Weitere Templates: **26** (Header One), **532** (Header Two) und **455** (Footer One); 21 Widgets.
- Aktiver Content Manager 0.4.6, RGB Pilot 0.6.1, Editorial Sitemap v2 Pilot 0.1.0, Launch Control 0.1.0. Integrator 0.1.0 wird **nur durch sein eigenes Update** 0.2.0 ersetzt.

## Technische Ausführung (noch ausschließlich lokal)
Das ZIP `ANDY-WP-PLUGIN-Integrator-v0.2A.zip` aktualisiert den vorhandenen Plugin-Ordner `andy-journal-integrator` und behält die schon vorhandene WordPress-Adminseite **Werkzeuge → ANDY Integrator**. Die alten 0.1-JSON-/CSV-Exporte bleiben erhalten.

Neue Funktion: **0.2A-Feldaudit** in derselben Adminansicht mit JSON- und CSV-Export:
1. Liest Elementor `_elementor_data` ausschließlich von den real identifizierten Objekten 14/26/532/455.
2. Inventarisiert Settings-Namen, Datentypen und verschachtelte Feldstruktur (beschränkt nach Feldzahl/Tiefe). Erkennt numerische Attachment-IDs in Medienfeldern, ohne Bilddaten/URLs auszugeben.
3. Nur für definierte redaktionelle Feldnamen gekürzte Textvorschauen (URLs/E-Mails redigiert); verdächtige Credentials-Feldnamen und beliebige Volltexte bleiben draußen.
4. Berechnet SHA-256 von Original-Elementor-JSON und Widget-Settings (Fingerprints ohne Originaldaten). Die 0.1-Baseline verfügte noch über *keine* Settings-Hashes.
5. Vergleicht Widget-IDs und Typen mit dem mitgelieferten inventarisierten Baseline-Register (`assets/baseline-01.json`) und markiert hinzugefügte, entfernte und typveränderte Widgets.
6. Exporte ausschließlich im WordPress-Admin mit `manage_options`, festem Host-Gate und Nonce; Download mit `no-store`.

## Sicherheitsgrenzen
**Read-only:** keine Änderungen an Posts, Pages, Elementor-, Theme-, WP-Optionen, Cache oder RGB-Routing; keine öffentlichen Endpunkte; keine aktive Home-Kopie. HTML-Originale, Player, Game-Daten, WordPress-Seite 14, `www.andy-arena.com` und `blog.andy-arena.com` bleiben unangetastet. Ein Feldaudit beweist nicht die Funktion der WpSection-Widgets oder des Replays.

**Vertraulichkeit:** Der JSON-Export kann interne Feldnamen, gekürzte redaktionelle Texte und Media-IDs enthalten. Bitte **nicht ungeprüft** auf GitHub publizieren. Aus dem Export erst eine bereinigte technische Matrix erzeugen, nachdem der Nutzer ihn im Chat bereitgestellt hat.

## Lokale Freigabeprüfungen
- `php -l` auf Plugin-Hauptdatei: **bestanden**
- **38 PHP-Stub-Tests:** Version-0.1-Regressionsfälle, Domain-/Admin-Scope, Settings-Schema und Drift-Detektion, SHA-256, Key-Filter, URL-/E-Mail-Redaktion, Media-ID ohne URL, Admin-/Export-Darstellung: **bestanden**
- ZIP-Struktur und CRC: **bestanden**
- ZIP-SHA256: `29966cce1604a71f9009277bdd5bd7d0557fed710f3742dab17a77a6cf992358`
- Kein realer Hostinger-Pluginupgrade-, Browser- oder Cache-Test durch ChatGPT; Nutzerabnahme steht aus.

## Bedienung auf Hostinger-Testinstanz
1. **Plugins → Plugin hinzufügen → Plugin hochladen** und `ANDY-WP-PLUGIN-Integrator-v0.2A.zip` wählen.
2. Falls WordPress die Versionsersetzung anzeigt, **nur ANDY Journal Integrator 0.1.0 → 0.2.0** ersetzen lassen. Andere Plugins nicht ändern.
3. **Werkzeuge → ANDY Integrator** öffnen. Abschnitt **6. Neues Feldaudit 0.2A** prüfen.
4. **0.2A-Feldaudit als JSON** herunterladen und hier hochladen.
5. Erst danach die tatsächlichen Felder in einem statischen Dry-Run-Diff für **0.2B** analysieren.

## Folgeschritt
**0.2B – reversible private Aculia-Home-Kopie:** Nach Sichtung des realen Settings-JSON und Backup einen nichtöffentlichen Entwurf auf Basis von Home 14 anlegen. Drei demonstrierbare Content-Slices (Fight Night, Perspektive/Research, Academy) mit passenden realen Medien und Originalmodulen. Keine Umstellung der WordPress-Startseite bis zu separater Freigabe.

**Dateien im Chat:** `ANDY-WP-PLUGIN-Integrator-v0.2A.zip` und `ANDY-DOC-Integrator-v0.2A.md`. Die binäre ZIP-Datei ist in dieser Dokumentation referenziert, nicht im GitHub-Repository veröffentlicht.
