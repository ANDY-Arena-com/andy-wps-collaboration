# ANDY Arena Website – belegte Release-Kette und Statusabgrenzung (13.11.2026)

**Status:** Datei-/Paketprüfung, **kein Nachweis über produktiven Hostinger-Stand**.  
**Kontext:** Website-Fixes am Vormittag 13.11.2026; erst danach bekannt gewordenes Windows-HTTPS/TLS-Problem. Diese Sachverhalte nicht vermischen.

## 1. Quellen und Vertrauensgrenzen

Die folgenden ZIP-Bundles wurden anhand ihrer enthaltenen Dateien, der README-Dateien und der Dateihashes untersucht. Die hier angeführten ZIP-Hashes beziehen sich auf die tatsächlich für die Prüfung vorliegenden Archiv-Bytes. Archiv-Dateinamen sind **nicht** automatisch Git-Tags, Deployment-Nachweise oder Freigaben.

| Reihenfolge | ZIP-Dateiname der geprüften Kopie | SHA-256 des ZIP | Dokumentierte Änderung |
|---|---|---|---|
| 1 | `ANDY_Arena_KOMPLETT_V0812_Play_Closes_Overlays(1).zip` | `669527c6ec8cf572bce75353cd62372e68b200842aa51d865fea6411e9acda86` | V0.8.1.2: Abspielen schließt Replay-Overlays; zuvor Countdownfix in V0.8.1.1 |
| 2 | `ANDY_Arena_KOMPLETT_V0813_Final_Touch(1).zip` | `bad3a6ba5645203d30849890cd6a1337234d15ea9fce8c8b46bbc146b493a074` | V0.8.1.3: Play/Countdown, 0,9-s-Orientierung, SVG-Figuren, Overlay-Detail |
| 3 | `ANDY_Arena_KOMPLETT_V0814_SVG_Schattenfix(1).zip` | `b4c160f4d4bff434aeee03b246c7788d57c041444ab131467a6a75b4facfaae1` | V0.8.1.4: zusätzlicher SVG-Schattenfix (nur `theater/app.js`, `theater/START_HIER.html` gegenüber V0.8.1.3 verändert) |
| 4 | `ANDY_Arena_KOMPLETT_V082_Mobile_Blog(1).zip` | `d1aaef523f45c12108a662022d9d8284467961703013f592bb081f059738e15c` | V0.8.2: Mobile DE/EN/ZH + separate Blog-Coming-Soon-Seite |
| 5 | `ANDY_Arena_KOMPLETT_V0821_Mobile_CSS_Fix.zip` | `20f70ae083a31d4694ed8431c4f871113fa556fd072fbc977e4326e39bd6ce52` | V0.8.2.1: CSS-Dateiname versioniert + absichernde Desktop-Regel |
| 6 | `ANDY_Arena_KOMPLETT_V0822_Replay_Zeitanzeige.zip` | `e7b19128c9e7563865beaa9ca3b14e1c0eafea4734c1d1e893520a14596946b4` | V0.8.2.2: Original-Matchzeit rechts neben vorhandenem Ereigniszähler ([Fixbericht](WEBSITE_REPLAY_TIME_0822_2026-11-13.md)) |

**Herkunft:** Kopien der V0.8.1.2–V0.8.2-Pakete vom Projektleiter in die Analyse eingebracht; V0.8.2.1 als ebenfalls im Arbeitsverzeichnis vorhandenes ZIP separat mitgelesen. Diese Dokumentation archiviert **Metadaten und Diffs, nicht die ZIP-Binärdateien**.

## 2. Tatsächlich anhand der Inhalte geprüfte Diffs

- **V0.8.1.2 → V0.8.1.3:** innerhalb `public_html/` geändert: `theater/app.js`, `theater/style.css`, `theater/START_HIER.html`; übrige Webdateien unverändert.
- **V0.8.1.3 → V0.8.1.4:** geändert: `theater/app.js`, `theater/START_HIER.html`; übrige Webdateien unverändert. **Achtung:** Das V0.8.1.4-ZIP enthält weiterhin die ältere `README-V0813.txt`; seine Version/Schattenänderung ist somit im ZIP-README **nicht separat erklärt**.
- **V0.8.1.4 → V0.8.2:** geändert: `de/index.html`, `en/index.html`, `zh/index.html`, `assets/style.css`. Unverändert: gesamtes `theater/` inklusive Replay-JS, Replay-Daten und Original-JSONL. Zusätzlich existiert außerhalb der Hauptseite `BLOG_SUBDOMAIN_UPLOAD/index.html`, für eine **separate** Subdomain-Document-Root.
- **V0.8.2 → V0.8.2.1:** drei Sprachseiten geändert, `assets/style-v0821.css` hinzugefügt. Inhalt der neuen CSS-Datei ist laut Begleit-README identisch zum V0.8.2-`assets/style.css`; bestehende Theater-Dateien unverändert.
- In **V0.8.2** referenzieren die drei Sprachseiten weiterhin `../assets/style.css?v=079` obwohl die neue Mobile-CSS erst mit diesem Release ausgeliefert wurde. Dies entspricht dem in [Issue #1](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/1) beschriebenen Cache-Risiko.
- In **V0.8.2.1** zeigen die drei Sprachseiten auf `../assets/style-v0821.css` (neuer unverwechselbarer Dateiname).

- **V0.8.2.1 → V0.8.2.2:** ausschließlich theaterbezogene Replay-Dateien für die Original-Matchzeitanzeige und ein wiederholbares Zeitstempel-Synchronisationsskript verändert bzw. ergänzt. DE/EN/ZH-Homepage, ursprüngliche Match-JSONL und Blog unverändert. Siehe [Fixbericht V0.8.2.2](WEBSITE_REPLAY_TIME_0822_2026-11-13.md). Vollständiges ZIP separat bereitgestellt, aber nicht als GitHub-Release-Asset committed.

## 3. Website vs. Browser-/Infrastrukturproblem

**Website-/Cache-Problem (V0.8.2):** Desktop kann neue Mobile-Elemente sichtbar zeigen, falls das aktualisierte CSS nicht ausgeliefert oder zwischengespeichert wird. Gegenmaßnahme V0.8.2.1, siehe [Issue #1](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/1).

**Später entdecktes Windows-Problem:** Chromium/Firefox melden TLS-/Cipher-Handshake-Fehler vor dem Laden von HTML/CSS (`ERR_SSL_VERSION_OR_CIPHER_MISMATCH`, `SSL_ERROR_NO_CYPHER_OVERLAP`). Separat dokumentiert in [Issue #3](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/3) und [Windows-Diagnose](DIAGNOSE_TLS_WINDOWS_IPV6_2026-11-13.md). DNS-/IPv6-/CDN-Zusammenhang ist **zu untersuchen**, nicht bestätigt. Aus dieser zeitlichen Abfolge folgt weder, dass ein Website-Patch die Ursache war, noch dass der Server definitiv korrekt konfiguriert ist.

## 4. Release- und Abnahme-Status (bewusst präzise)

| Frage | Verifizierter Stand |
|---|---|
| Sind die ZIP-Bundles intern differenzierbar und ihre Folge rekonstruierbar? | **Ja**, mit den oben genannten Dateiunterschieden und Hashes. |
| Ist V0.8.1.4 ein klarer Rollback-Kandidat? | **Ja**, dokumentierte letzte getestete Basis laut V0.8.2-README; vor Rollback tatsächliche Hostinger-Kompatibilität nochmals prüfen. |
| War V0.8.2.2 der jüngste technische Website-Patch am 13.11.2026? | **Ja**, seit 13.11.2026 als sechstes Paket. Original-Zeitanzeige ist lokal geprüft, Live-/Browserabnahme offen. |
| Ist V0.8.2.2 nachweislich auf Hostinger produktiv? | **Nicht belegt**. |
| Wurden alle drei Sprachen, Desktop, Mobile, Replay, Windows unter V0.8.2.2 vollständig live abgenommen? | **Nicht belegt**, siehe [Issue #2](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/2). |
| Enthält dieses GitHub-Kollaborationsrepo den wiederherstellbaren exakten Webroot von V0.8.2.2? | **Hier nicht nachgewiesen**. Der Metadateneintrag ersetzt kein Release-Artefakt. |
| Ist der Windows-TLS-Fehler eine nachgewiesene Website-CSS-Regression? | **Nein**; separat untersuchen. |

## 5. Vorgehen bei späterer Release-Freigabe

1. Tatsächlich live ausgelieferte Version und Referenzpaket anhand realer URLs, CSS-Dateiname, Netzwerkanfragen und möglichst Webroot-Prüfsummen zuordnen.
2. Vollständiges unverändertes ZIP in einem geeigneten versionierten Release-Ablageort sichern und dessen Hash mit dieser Tabelle vergleichen (keine Geheimnisse oder privaten Zugangsdaten publizieren).
3. Mac-/Windows-/Mobile-/Tablet-Abnahme und DE/EN/ZH, Replay, Blog-Subdomain, Cache und TLS getrennt protokollieren; [Checkliste #2](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/2).
4. Erst **danach** einen produktiven Status, Release-Tag, Rollback-Version und Deployment-Zeitpunkt verbindlich setzen.

**Leitsatz:** Ein mit Hash belegtes Paket ist nicht dasselbe wie ein nachweislich produktiver oder vollständig getesteter Website-Release.


## Aktueller Website-Release-Stand (14.11.2026)

**V0.8.3.6 – Final Release** ist der jüngste bereitgestellte vollständige Website-Stand und ersetzt V0.8.2.2 als Entwicklungsreferenz. [Konsolidierter Release-Nachweis und SHA-256](WEBSITE_RELEASE_V0836_2026-11-14.md). V0.8.3.5 wurde vom Projektleiter visuell positiv beurteilt; die abschließenden Headerkorrekturen von V0.8.3.6 sind technisch geprüft, die visuelle Endabnahme und das Hostinger-Deployment noch nicht nachgewiesen. Windows-TLS bleibt separat offen.
