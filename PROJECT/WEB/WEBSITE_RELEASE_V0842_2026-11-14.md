# ANDY Arena Website – V0.8.4.2 Final Polish

**Stand:** 14.11.2026. **Status:** lokale visuelle Designfreigabe durch Projektleiter („hammer!!!“) nach V0.8.4.2. Kein nachgewiesenes produktives Hostinger-Deployment und keine vollständige plattformübergreifende Regression.

## Release-Artefakt
- `ANDY_Arena_KOMPLETT_V0842_Final_Polish.zip`
- SHA-256: `2731fce697cb7feddc9959902398413570d8e93e2c699cf5c990bee0c9bd6268`
- 747773 Bytes, 55 Dateien; ZIP-Integrität erneut erfolgreich geprüft.
- Gegen V0.8.4.1 geändert: DE/EN/ZH index.html, theater/START_HIER.html, theater/style.css; README-V0842-FINAL-POLISH.txt ergänzt.
- ZIP im Chat bereitgestellt; GitHub-Binärarchivierung noch offen.

## Entwicklungsfolge
| Version | Änderung | SHA-256 des vorliegenden ZIP |
|---|---|---|
| V0.8.3.7 | Doppelter Close-Button: äußerer Notausstieg nach Replay-Initialisierung ausgeblendet | b051604fa516c73bac6be705f746c0027e44340e1509fb0ed7e8cfdca10b613a |
| V0.8.3.8 | Header-Höhen harmonisiert, Statistik-Icon statt Fußlink, Hybrid-Spielericons | 5073fec6b4b7562e34faaf1a3060056b0c9a108b08b1433e4bed6079ad832967 |
| V0.8.3.9 | Black Corner gespiegelt, Logo-Rahmen, Hybrid-Icons statt Handschuhe | 04a70660a950d7f0fb887dd3edaf22210736991eefc6357cf704caa07168f4a1 |
| V0.8.4.0 | Player Identity Module, Intro mit VS. zwischen Spielerflächen, König-Innenleben | 9eddc511d4725296b809f475e908ba9437dc52439f1eaf4a6ef6b30dad5cf896 |
| V0.8.4.1 | Könige deckend weiß/dunkel gefüllt, Außenhintergrund transparent | 4b5f3fb133f63df99eab5975d43edc78b81006acaef3e64340b059ef3d4baef3 |
| V0.8.4.2 | Arena-Corner-Titel zur Brettmitte ausgerichtet: Weiß rechtsbündig, Schwarz linksbündig | 2731fce697cb7feddc9959902398413570d8e93e2c699cf5c990bee0c9bd6268 |

## Designreferenz: ANDY Player Identity Module
- Spiegelbildliche Anordnung: Modellidentität außen, Hybrid-Icon innen; VS. im Intro ausschließlich zwischen den Spielerflächen.
- König und runder plastischer Go-Stein derselben Spielfarbe; König mit Innenlinien und deckender Füllung, transparenter Außenhintergrund.
- Master-SVGs im Paket: public_html/theater/assets/hybrid-white.svg und hybrid-black.svg. Für App, Archiv, Siegerehrung und Lab als wiederverwendbare Designreferenz vorgesehen; dort noch nicht implementiert.
- Modellname prominent, Anbietername und Original-Anbieterlogo zusammen; weiße quadratische Logo-Kacheln, Seitenverhältnis erhalten.
- Einheitliche Header-Controls; Statistik/Originaldaten über Balkendiagramm-Icon. Kein Fußlink unter Bühne.
- Bestehende Replay-Dramaturgie und wissenschaftliche Abgrenzungen aus [V0.8.3.6](WEBSITE_RELEASE_V0836_2026-11-14.md) bleiben maßgeblich.

## Offen
Vollständiges ZIP dauerhaft archivieren; Hostinger-Backup und Deployment separat bestätigen; DE/EN/ZH, Mobile, Browser und vollständige Funktionstests dokumentieren. Windows-TLS bleibt separates Issue #3. Visuelle Designfreigabe ist kein Nachweis für vollständige technische Abnahme. Kein produktiver Eingriff in diesem Dokumentationsschritt.
