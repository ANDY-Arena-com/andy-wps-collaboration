# ANDY Arena Website – V0.8.4.2 Final Polish

**Aktualisierung 15.11.2026:** GitHub-Projektlink und Journal-Umbenennung; Journal-Aufruf bei Hostinger laut Projektleiter erfolgreich. Siehe [Nachtrag vom 15.11.2026](#nachtrag-vom-15112026--github-projektlink-und-journal). Die Versionsnummer bleibt V0.8.4.2.

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


## Nachtrag vom 15.11.2026 – GitHub-Projektlink und Journal

**Status:** Website-Paket V0.8.4.2 mit redaktionellen und Navigationskorrekturen. Der Projektleiter meldete am 15.11.2026, dass die Journal-Seite bei Hostinger jetzt funktioniert. Dieser Einzeltest ist keine vollständige technische Abnahme; ein unabhängiger Live-Dateiabgleich war nicht möglich.

### Änderungen
- Abschnitt 06 (Beta-Veröffentlichung): separaten Entwicklungsbutton entfernt; Link zum [GitHub-Projektbereich](https://github.com/ANDY-Arena-com/andy-wps-collaboration/tree/main/PROJECT) im Fließtext integriert. Weitere GitHub-Entwicklungslinks in mobiler Navigation und Footer auf denselben Projektbereich aktualisiert.
- Beta-Code-Download weiterhin als noch nicht verfügbar gekennzeichnet; keine Veröffentlichung eines Beta-Spielcodes.
- Blog → Journal in Desktop-Kopfzeile, mobiler Navigation, Footer und Coming-Soon-Landingpage; Deutsch, Englisch und Chinesisch berücksichtigt. Subdomain bleibt `blog.andy-arena.com`.
- Gegen das ursprüngliche V0.8.4.2-Paket exakt vier Dateien geändert: `public_html/de/index.html`, `public_html/en/index.html`, `public_html/zh/index.html`, `BLOG_SUBDOMAIN_UPLOAD/index.html`. Die übrigen 51 Dateien sind byteidentisch. Replay, CSS, JavaScript, Matchdaten und SVGs bleiben unverändert.
- Die Coming-Soon-Seite separat als `index.html` ins Webverzeichnis der Blog-Subdomain hochladen; die einzeln im Chat bereitgestellte Datei `ANDY_Journal_index.html` ist byteidentisch mit der Landingpage aus beiden Journal-Paketen.

### Referenzartefakte (lokal verifiziert)
| Paket | Größe | SHA-256 |
|---|---:|---|
| `ANDY_Arena_KOMPLETT_V0842_GitHub_Journal.zip` | 747848 Bytes | `12c2665fd1777e8d31e55c64bb4a5e74b97e4b2acc95fa6e39c376a6306e1ee6` |
| `ANDY_Arena_KOMPLETT_V0842_GitHub_Journal_IndexFix.zip` | 747864 Bytes | `c68ff463ecadc8cb0fc46e04416179d89636667104a53edf0db1a139e703a580` |

Beide ZIPs enthalten je 55 Dateien; Integritätsprüfung ohne Fehler. Die Journal-Variante verlinkt in allen drei Sprachen auf `https://blog.andy-arena.com/` (12 Links). Die IndexFix-Variante unterscheidet sich davon ausschließlich in diesen drei Sprach-HTML-Dateien und verlinkt ausdrücklich auf `https://blog.andy-arena.com/index.html`.

Beim vorangegangenen Test erschienen zeitweise die WordPress-Standardseite und für den direkten HTML-Aufruf eine 404-Seite. Anschließend bestätigte der Projektleiter die Funktion auf Hostinger. Die genaue Serverursache und die tatsächlich hochgeladene Linkvariante sind nicht unabhängig verifiziert. Die reguläre Journal-Variante mit Subdomain-Root bleibt der empfohlene Referenzstand, sofern dieser Aufruf weiterhin funktioniert; IndexFix ist eine dokumentierte Alternativvariante. Keine Änderungen an WordPress oder Hostinger durch diesen GitHub-Dokumentationsschritt.

**Noch offen:** Dauerhafte Binärarchivierung der ZIPs im Repository, unabhängiger Abgleich des produktiven Deployments inklusive exakter Linkvariante und vollständige Browser-/Mobil-/Sprachregression.
