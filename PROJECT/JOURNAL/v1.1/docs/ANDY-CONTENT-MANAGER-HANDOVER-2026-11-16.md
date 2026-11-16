# Übergabe ANDY Journal – Content Manager / DESIGN-01
Stand 16.11.2026. Status: Inventory erfolgreich; schreibender Import NICHT implementiert. Release-Gate BLOCKED.

## Auftrag für den neuen Thread
Direkt auf der bestehenden Aculia-Testinstallation weiterarbeiten, nicht neu konzipieren. Zwei getrennte reale Artefakte erstellen: andy-content-manager-v0.2.zip (Update des vorhandenen Plugins) und ANDY-DESIGN-01.zip (reines Daten-/Medienpaket). Workflow: [Architektur v0.1](ANDY-CONTENT-MANAGER-WORKFLOW-v0.1.md). Erst Dry Run, dann explizite Freigabe, Backup/Rollback und Browser-Abnahme. Keine Änderungen an der öffentlichen Coming-Soon-Seite oder Arena.

## Gesicherter Stand
- Frische Aculia-Demo via integriertem Import nutzerseitig erfolgreich. Hostinger-Backup vom Nutzer bestätigt.
- Zwei echte Inventory-Exporte vom 16.11.2026 (13:23:38 und 13:47:37 UTC); Plugin v0.1 bzw. v0.1.1. In dieser Übergabe beide vollständigen JSON-Dateien tatsächlich maschinell gelesen und verglichen: 211 eindeutige Referenzobjekte laut Export, 196 baseline_match, 15 baseline_changed, 0 fehlende Referenz-IDs laut Export; sämtliche Content-/Elementor-Hash-Paare nach ID zwischen beiden Exporten gleich. Abweichungen zur XML-Baseline: 6 Posts, 5 Pages, 3 CF7-Formulare, 1 MC4WP-Formular. Keine Aussage über Ursache oder sämtliche Metadaten. Cleanup gesperrt.
- Plugin-ZIPs v0.1/v0.1.1 sind vorhanden, ZIP-Integritätsprüfung erfolgreich; baseline.json in beiden byteidentisch (SHA256 0e0eb4f3a64f5cc75c9680950a83ae76e3a8e1406baeb3a7d8acebd8fc35b50c). Vollständige Code-/Sicherheitsprüfung bleibt offen.
- Aculia Child 2.0, Eltern-Theme aculia, WP 7.1.4, PHP 8.3.36, Elementor 4.4.0 (laut Export).
- v0.1.1 erfasst theme_mod:aculia_options-mods, globale Hauptfarbe #f17732. Legacy-Option laut Diagnose nicht vorhanden. Kit 7 aktiv, keine gespeicherten Kit-Einstellungen gemeldet; zunächst nicht anfassen.
- Homepage 14 (home-one), Beitragsseite 733, Menü main_menu 12, custom_logo 136, site_icon 0. Globaler Header 532, Homepage-Override Header 26, globaler Footer 455. Die Footer-Override-Felder des Exports sind nicht als vollständiger Beweis aller Seitenspezifika zu verstehen.

## Konkrete DESIGN-01 Ziele
| Objekt | Widget | Feld / bisherige Medien-ID |
|---|---|---|
| Header 26 | 5b651b3 wpsection_header | image 137, sticky_logo 138 |
| Header 532 | c0cb75f wpsection_header_two | image 135, logo 135, sticky_logo 135 |
| Footer 455 | 770818bd image | image 134 |
| Homepage 14 | ausgewählte Widgets | gezielte Farbfelder, u.a. #FF0000 |

WordPress-Titel ANDY Journal, Untertitel Actor. Network. Dynamics.; Favicon, WordPress-Logo und tatsächlich benötigte Aculia-Fallback-Logos berücksichtigen. Farbentwurf Night #061422, Blue #057DE0 (vor Einsatz als Designentscheidung transparent kennzeichnen; Abgleich mit Original-CD). Keine pauschale String-Ersetzung, keine Änderung der Schriftarten, Layouts, Menüs oder redaktionellen Demo-Inhalte. Kit unangetastet. Alte externe Demo-URLs sind bekannt, separate spätere Content-/Link-Migration. Vorhandene Demo-Medien nicht löschen.

## Private Eingabedateien (nicht im öffentlichen Repo)
Im bisherigen Arbeitscontainer tatsächlich vorhanden:
- andy-content-manager-v0.1.1.zip (enthält andy-content-manager/andy-content-manager.php, baseline.json, readme.txt)
- ANDY-INVENTORY-20261116-134737.json (maßgeblich), optional ANDY-INVENTORY-20261116-132338.json
- ANDY-Journal-Logo-dark.png und ANDY-Journal-Logo-light.png (je 725 x 124 RGBA), ANDY-Journal-Site-Icon.png (512 x 512 RGBA); PNGs technisch lesbar, visuelle Originaltreue und Einsatz auf tatsächlichem Hintergrund vor Freigabe prüfen.
- glad-whitesmoke-octopus-16hostingersitecom.WordPress.2026-11-16.xml (Referenz)
- themeforest-NxHkKeBN-aculia-laboratory-research-wordpress-theme.zip (lizenzierter Quellcode zur Adapterprüfung, nicht publizieren)
Die Verfügbarkeit in einem neuen Thread ist nicht garantiert. Dort reale Dateien öffnen; fehlende Dateien einmal gezielt anfordern. Kein erneuter Inventory-Export ohne konkreten Bedarf. Keine privaten Rohdaten oder lizenzierten Theme-Dateien committen.

## Implementierungs- und Test-Gates
Bestehenden Code lesen und Read-only-Export/Baseline erhalten. Paket-Schema mit fest begrenzten Operationen, Prüfsummen, Zielinstanz/Theme/Versionsprüfung, sichere ZIP- und Bildvalidierung ohne ausführbare Paketdateien. Admin-Capability und Nonce, kein Schreibvorgang bei Aktivierung oder Vorschau. Konfliktprüfung direkt vor Apply gegen erwartete alte Werte, Objekt-ID/Slug/Typ, Widget-ID/Typ und Hashes; Wiederholung muss sicher erkannt werden. Backup vor Änderung, alte Optionen und Metadaten exakt einschließlich fehlender Werte erfassen, neue Medien getrennt protokollieren; Rollback auch bei Teilfehlern und Schutz gegen nachträgliche Änderungen. CSS-/Cache-Regeneration mit realer Elementor-Schnittstelle prüfen. Keine ungetestete Zusage atomarer Transaktionen.
Mindestens PHP-Lint, ZIP-Integrität, Tests für gültige/ungültige Pakete, Konflikte, Wiederholung, Teilfehler, Rollback; reale WP-Laufzeit/Browser-Abnahme als gesondertes Gate. Tatsächlich erstellte Dateipfade prüfen, beide ZIPs erst dann verlinken. Tests und Grenzen ehrlich benennen. Keine Live-Freigabe.

## Abbruchursache
Vorheriger Thread lieferte nach erfolgreichem Inventory wiederholt Statusmeldungen und kündigte v0.2/DESIGN-01 an, ohne diese zu erstellen. Kein technischer Blocker nachgewiesen. In dieser Übergabe sind beide Ziel-ZIPs im Arbeitscontainer nicht vorhanden. Es gab keine Installationsfreigabe und keine bestätigte schreibende Änderung. Nutzer hat Abbruch/Threadwechsel verlangt. Nicht erneut Plan oder Backup abfragen, nicht behaupten, dass Arbeit im Hintergrund läuft. Konkrete Artefakte erzeugen oder präzisen, nachgewiesenen Blocker nennen. Die ursprüngliche Architektur bleibt gültig; Demo Cleanup erst nach Ersatz und Abhängigkeitsprüfung (v0.5).

## Folgearbeiten
Nach Abnahme DESIGN-01: HOME-01, dann Research/Academy/Publications/Stories. Academy/Replay eigenständig; deren Aculia-Kompatibilität separat prüfen. Die spätere Uninstall-Funktion muss Herkunft und Schutzstatus getrennt führen und nur freigegebene, ersetzte Demo-Inhalte reversibel bereinigen.
