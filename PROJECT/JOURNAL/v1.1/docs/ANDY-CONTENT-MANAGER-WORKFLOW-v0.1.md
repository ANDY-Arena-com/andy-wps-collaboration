# ANDY Content Manager – Architektur und Publishing Workflow v0.1

Stand: 16.11.2026 | Status: abgestimmtes Vorgehen, Implementierung offen.

## 1. Ausgangslage und Ziel

ANDY Journal ist eine eigenständige vollständige Website; die ANDY Arena bleibt separat und verlinkt darauf. Aculia dient als professionelle Layout-Infrastruktur, Elementor/WpSection als bestehende Bearbeitungsbasis. Demo-Strukturen möglichst erhalten, Inhalte und Corporate Design gezielt transformieren. Keine unnötige Eigenentwicklung von Standardfunktionen, kein Fork des Themes.

Der erste Demo-Import mit alten King-Composer-Inhalten scheiterte teilweise. Auf einer frischen WordPress-Testinstanz funktionierte der integrierte Import nach Nutzerbestätigung wie erwartet. Der neue WXR-Export vom 16.11.2026 ist Ausgangspunkt der Bestandsaufnahme, kein vollständiges Backup. Theme-Optionen, aktives Elementor-Kit, tatsächliche Medien und dynamische Abhängigkeiten sind gesondert zu prüfen. Kein Roh-Export mit personenbezogenen Daten oder Zugangsdaten ins öffentliche Repository.

## 2. Modularer Aufbau

Content Manager als dauerhaft installiertes separates WordPress-Plugin; Academy und Replay bleiben eigenständige Laufzeitplugins, Research Library perspektivisch ebenfalls als modularer Baustein. Content Manager verwaltet redaktionelle Inhalte und Designkonfiguration, nicht Match-Engine oder Lernlogik. Interaktive Inhalte über kompatible Schnittstellen/Shortcodes einbinden; Originaldaten und bestehende Pakete unangetastet lassen.

Paketlinien:
- DESIGN-01: Website-Identität, Originalsignet, Haupt-/Sekundär-/Footerlogo, Favicon, globale ANDY-Farben. Typografie, Abstände und Layout zunächst unverändert.
- HOME-01: Hero/Slider, vier Einstiege, Research Tabs, Discover ANDY, Featured Replay, Academy-Demo, Philosophy, Perspectives, Latest Stories, Newsletter/Footer.
- RESEARCH-01, PUBLICATIONS-01, ACADEMY-01: Gabelseiten und ausgewählte Inhalte; Token Economy als eigener Inhaltsbereich.
- STORIES-01 und Folgepakete: redaktionelle Beiträge, Medien und Zuordnungen.

Vier redaktionelle Produktionslinien: reale Match-Stories mit Replay, vergleichende Forschung, Token Economy (inkl. tatsächlicher Kosten nur bei belegter Abrechnung, sonst gekennzeichnete Schätzung), Academy mit realen Spielsituationen. Produktionslinien sind nicht automatisch neue Rubriken.

## 3. Publishing Workflow

1. Funktionierenden Original-Demostand extern vollständig sichern (DB und Dateien).
2. Inventory/Export des installierten Zustands: Seiten, Post Types, Templates, Widget-IDs, Menübeziehungen, Medien, relevante Theme-/Elementor-Einstellungen und aktive Zuordnungen.
3. Baseline und Content Registry aufbauen; IDs nur instanzbezogen, stabile logische Identitäten und Fingerprints für Pakete.
4. Inhaltspaket offline auf Basis des tatsächlichen Bestands erstellen; Layouts und responsive Einstellungen erhalten.
5. Paket hochladen, Schema/Version/Kompatibilität/Referenzen prüfen, Dry Run mit Vorher-Nachher-Vorschau, Konflikten und betroffenen Objekten.
6. Administrator wählt Bereiche und bestätigt explizit. Vor Änderung betroffene Werte sichern; keine unbemerkte Überschreibung redaktioneller Änderungen; keine Duplikate durch Wiederholung.
7. Über WordPress-/Elementor-kompatible Schnittstellen selektiv aktualisieren; Cache/CSS-Regeneration soweit erforderlich. Ergebnis und Paketversion protokollieren.
8. Browser-Abnahme (Desktop/Mobil, Navigation, Bilder, Slider, Links, Editor, interaktive Plugins). Unveränderte Bereiche auf Regression prüfen.
9. Bei Fehlern Rollback; bei Erfolg Registry aktualisieren; ersetzte Demo-Inhalte erst nach gesonderter Freigabe bereinigen.

## 4. Content Registry und Herkunft

Status | Bedeutung
---|---
Original | unveränderter, eindeutig identifizierter Demo-Inhalt
Transformed | bestehendes Objekt zu ANDY-Inhalt umgearbeitet
Native | neu erstellter ANDY-Inhalt
Obsolete | nachweislich durch freigegebenen Ersatz entbehrlich
Protected | weiterhin benötigte Struktur oder Ressource
Archived | reversibel entfernt bzw. gesichert

Vorgeschlagene technische Präzisierung: Herkunft und Schutzstatus getrennt speichern, da z.B. ein Original-Template zugleich geschützt sein kann. Registry erfasst Objektart, lokale ID, logische ID, Baseline-/aktuellen Fingerprint, Paket-ID/Version, Abhängigkeiten, Ersatzobjekt, Änderungsstatus und Freigaben. Unbekannte Herkunft oder Referenz bedeutet nicht löschbar. Manuell geänderte Inhalte nicht allein anhand Titel oder Slug als Demo klassifizieren.

## 5. Demo Content Cleanup / Uninstall

Ziel: entbehrliche Demo-Inhalte entfernen, nicht Aculia oder dessen benötigte Plugins deinstallieren. Herkunftserfassung beginnt in v0.1, automatische Bereinigung bleibt bis zur Abhängigkeitsprüfung gesperrt.

Kandidaten: alternative Homepages, nicht transformierte medizinische Beispielbeiträge, Demo-Teamprofile/Testimonials, ungenutzte Medien, verwaiste Kategorien/Tags, nicht benötigte Templates. Keine pauschale Löschung nach Post Type, Upload-Datum oder Dateiname.

Replacement Gate: benötigter Ersatz existiert, ist abgenommen und aktive Navigation/Referenzen zeigen korrekt darauf. Abhängigkeiten prüfen: aktive Start-/Beitragsseite, Menüobjekte, Header/Footer, Elementor-Kit, geschachtelte Templates, Widget-Daten, dynamische Queries, Shortcodes, Beitrags- und Hintergrundbilder, Theme-Optionen, Taxonomien und Plugin-Beziehungen. Unvollständig analysierbare dynamische Referenzen sind Blocker. Transformed/Native und referenzierte Ressourcen schützen.

Dry Run zeigt Kandidaten, Gründe, Abhängigkeiten und blockierte Objekte. Selektive Freigabe; zunächst Papierkorb oder separat gesicherte reversible Archivierung (Medien/Taxonomien nicht blind wie normale Posts behandeln). Wiederherstellung inklusive Beziehungen und Dateien testen. Erst nach erneuter Browser-Abnahme und separater Zustimmung endgültig löschen. Kein automatisches Cleanup bei Plugin-Deaktivierung oder WordPress-Uninstall.

## 6. Paket- und Sicherheitskonzept (Entwurf)

Versioniertes Daten-ZIP mit manifest.json, Paket-ID, Schema-/Content-Version, Zieladapter/Kompatibilität, erwarteten Baseline-Fingerprints, erlaubten Operationen, Medien und Prüfsummen. Keine ausführbaren PHP-/JS-Dateien aus Content-Paketen. Keine beliebigen Options-/SQL-Schreibzugriffe; explizite Allowlist, Administratorrechte, Nonce, ZIP-Pfad-/Größenprüfung und sichere Medienvalidierung. Kein Import bei Konflikt oder unbekannter Zielstruktur. Keine privaten Exporte öffentlich speichern. Design- und Content-Pakete separat auslieferbar.

Rollback muss tatsächliche alte Werte, Zuordnungen und gegebenenfalls Dateien wiederherstellen; keine Zusage transaktionaler Vollständigkeit ohne Tests. Externes Backup bleibt Voraussetzung.

## 7. Roadmap

| Version | Umfang / Gate |
|---|---|
| v0.1 | Read-only Inventory/Export und Registry-Baseline; keine Content-/Design-Schreiboperationen oder Löschungen |
| v0.2 | Selektive Design-/Content-Transformation, DESIGN-01 zuerst; Vorschau, Sicherung und Rückweg vor erster Schreiboperation |
| v0.3 | Modularer Daten-ZIP-Import, Versionsprüfung und Wiederholbarkeit |
| v0.4 | Komfortabler Versionsvergleich, Änderungsverlauf und Rollback-Verwaltung |
| v0.5 | Demo Cleanup mit Replacement Gate und Abhängigkeitsprüfung, reversible Archivierung zuerst |
| v1.0 | Abgenommener Publishing Lifecycle: installieren, aktualisieren, ersetzen, deinstallieren, wiederherstellen |

## 8. Abnahme und offene Punkte

Nächster Schritt: v0.1 implementieren und auf der neuen Aculia-Testinstanz testen. WXR-Inventar mit Live-Bestand abgleichen; tatsächliche Theme-Options- und Elementor-Kit-Schnittstellen, Widget-Schemata und Medienreferenzen ermitteln. Adapter und Paketformat konkretisieren. Academy/Replay-Kompatibilität auf Aculia separat testen. Keine Live-Freigabe; bestehende Arena, frühere Journal-Testinstanz und öffentliche Coming-Soon-Seite bleiben unverändert.

Dieses Dokument beschreibt das vereinbarte Vorgehen und ergänzende technische Sicherheitsvorschläge, keine bereits implementierten Funktionen. Zahlen zum Demo-Bestand werden erst nach verifizierter Inventarisierung festgeschrieben.
