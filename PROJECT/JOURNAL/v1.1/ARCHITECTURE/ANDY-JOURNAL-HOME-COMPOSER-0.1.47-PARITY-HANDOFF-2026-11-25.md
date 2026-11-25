# ANDY Journal – Home Composer 0.1.47: Versionsparität und nächster Entwicklungsschritt

**25.11.2026 · Nutzerbestätigung:** Home Composer **0.1.47 ist auf Staging UND Live installiert**. Damit ist der vorherige Home-Composer-Versionsdrift auf Installationsebene beendet. Der zuvor dokumentierte Build-Freeze bezog sich auf die noch ausstehende gemeinsame Installation und muss entsprechend aktualisiert werden. **Ein vollständiger Funktions-Smoke-Test von Claim-Links/Checkboxen, individuellen Farben, Fight-Night-Limit und DE/EN in 0.1.47 ist noch nicht ausdrücklich bestätigt.**

## Unmittelbare nächste Schritte

1. Kurze Funktionsabnahme **beider** Installationen zu Claim-Checkbox/Link, persönlichen Claim-Farben, Fight Night und DE/EN. Abnahme von technischen Versionsständen von Inhaltsständen strikt unterscheiden.
2. **Read-only Inventur aller ANDY-Plugins** auf Staging und Live (Version, aktiv/inaktiv, Dateistand); noch keine belegte Parität von Launch Control oder Content Composer. Keine Änderungen an Datenbanken.
3. Danach genau **ein** nächster Home-Composer-Kandidat für **HOME-CURATION-01A**: zentrale redaktionelle Startauswahl pro Journal-Bereich (Fight Night, Research, Perspectives, Academy, Making of) mit **1 echten Artikel + optional 1 zweitem Artikel**, DE/EN, feste Referenzen auf bestehende WP-/RGB-/Content-Composer-Storys; niemals ein zweites CMS. Manuelle Auswahl bedeutet **kein Auto-Fallback**, sichtbar fehlende IDs, durchgängig wirksame Limits.
4. **HOME-CURATION-01B**: dieselbe Startauswahl in den vorhandenen Journal-Modulen darstellen; bestehender Header, Hero, Claim-Farben, Modul-Layouts und Gabelseiten unverändert. 4 Academy- und 8 Perspectives-Katalogeinträge bleiben auf Gabelseiten.
5. Anschließend **WHY/Guided Tour** aus bereits vorhandenen DE/EN-WHY-Daten in Launch Control: freiwilliger Tour-Button oben und dezenter `Warum?`-Button je Bereich.
6. Für jede neue Version ein Releasezug: **ZIP einfrieren → Staging prüfen → identisches ZIP auf Live → gleiche Version bestätigen**, erst dann weiterentwickeln. Keine weiteren 0.1.48/0.1.49-Ketten vor einem gemeinsamen Abschluss.
7. **PRE-STAGING-01C2B** (native Posts, RGB, Gabelseiten, REST, Suche, Feeds, Sitemap, Medien, Cache, DE/EN) bleibt Voraussetzung für öffentliche Leseproben; ein interner Home-Slot ist **keine** Publikationsfreigabe.

**Bisherige Dokumente:** `PROJECT/JOURNAL/v1.1/STATUS.md`, `PROJECT/JOURNAL/v1.1/ARCHITECTURE/ANDY-JOURNAL-HOME-EDITORIAL-CURATION-GUIDED-TOUR-01-2026-11-25.md`, `PROJECT/JOURNAL/v1.1/ARCHITECTURE/ANDY-JOURNAL-CLAIM-LINK-CHECKBOX-01-0.1.47-2026-11-25.md`.

**Wichtig:** Dieser Handoff ist Planung und Versionsbestätigung, **kein neuer Plugin-Build oder bestätigter Remote-Smoketest**.