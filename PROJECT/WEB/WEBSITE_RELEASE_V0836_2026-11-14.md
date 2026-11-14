# ANDY Arena Website – V0.8.3.6 Final Release

**Stand:** 14.11.2026. **Status:** vom Projektleiter als abschließende Website-Version beauftragt; vollständiges Release-Paket erstellt, technische Paketprüfungen bestanden. Positive visuelle Rückmeldung zu V0.8.3.5; die beiden letzten Layoutkorrekturen in V0.8.3.6 sind noch visuell abzunehmen. Kein nachgewiesenes Hostinger-Deployment.

## Release-Artefakt
- Datei: `ANDY_Arena_KOMPLETT_V0836_Final_Release.zip`
- SHA-256: `3945857d20b9de3b9a2c71be841cb6006cd5232f5c9ea2a80a928074bc269a12`
- Größe: 742667 Bytes.
- Basis: V0.8.3.5 Final Polish.
- ZIP in der Unterhaltung bereitgestellt; **nicht als GitHub-Binärasset archiviert**.
- Gegen V0.8.3.5 nur `public_html/theater/START_HIER.html` und `public_html/theater/style.css` verändert; `README-V0836-FINAL-RELEASE.txt` ergänzt. Keine Änderungen an JS, Originaldaten, Homepage oder Sprachseiten.
- Alert mittig im reservierten Headerbereich; Close und vier Transportbuttons einheitlich 28 × 28 CSS-Pixel; CSS-Cache-Parameter `0836-final-release`, Theater-HTML-Titel V0.8.3.6.

## Konsolidierter Funktionsstand
Entwicklungsfolge aus den Offline-Paketen und den begleitenden Testgesprächen (keine erneute vollständige Browser-Abnahme aller Zwischenversionen):

| Version | Entwicklung |
|---|---|
| 0.8.2.2 | Original-Matchzeit neben Ereigniszähler |
| 0.8.2.3–0.8.2.4 | Keypoint-Experimente: Slider-Marker, dann nummerierte Karten unter dem Brett und Szenenerklärung |
| 0.8.2.5–0.8.2.6 | Acht semantische Keypoints mit Originalzitaten, Einzelschritten und grafischer Hervorhebung; verschiebbares Fenster über der gesamten Bühne |
| 0.8.2.7–0.8.2.8 | Einklappbare Schlüsselmomente, standardmäßig geschlossen; größeres Brett; Erklärungslayer darüber |
| 0.8.2.9–0.8.3.0 | Mattinszenierung, sichtbare Endstellung, Siegerehrung ausschließlich auf Buttonklick |
| 0.8.3.1–0.8.3.4 | Guided Tour konsolidiert: Brett zuerst, Steuerung, Weiß, Schwarz, Schlüsselmomente; zentriertes Tourfenster. Schachbewegungen mit Startmarkierung, Figurbewegung und Zielmarkierung über Go-Ebene |
| 0.8.3.5 | Farbrollen deutlich, redundanter Titel entfernt, Alerts im Header, Abstand zur Keypoint-Leiste, kompakter Tonbutton |
| 0.8.3.6 | Abschließende Zentrierung des Alerts und einheitliche Transport-/Close-Buttons |

## Inhaltliche Leitlinie
Astra–Gemini 4 Argon, Match `andy_0c0f7413fdf6`. Die im Replay enthaltenen Szenen verbinden protokollierte Modellbegründungen, ausgeführte Aktionen und Spielzustände. Semantische Aussagen sind keine unabhängigen Belege für interne Absichten oder optimale Strategie. Forschungsinterpretationen, insbesondere Spiegelmuster und Mattprognosen, sind gesondert regelkonform zu validieren. Keine Aussagen aus Flash–Argon auf diese Partie übertragen.

## Technische Prüfung und offene Freigabepunkte
ZIP-Integritätsprüfung und Node.js-Syntaxprüfung erfolgreich; Diff gegen V0.8.3.5 wie oben. Keine neue visuelle Browserprüfung dieser letzten Korrekturen. Vor Deployment Backup, Offline-Abnahme, Hostinger-Abgleich, DE/EN/ZH, Replay/Animation/Keypoints/Tour/Finale und Cache prüfen. Windows-TLS/IPv6 bleibt separates offenes Infrastrukturthema (Issue #3). Blog-Subdomain separat behandeln. Die vollständige Binärarchivierung des Pakets in GitHub bleibt offen.

**Referenzen:** [Paketkette bis V0.8.2.2](WEBSITE_RELEASE_EVIDENCE_2026-11-13.md), [Replay-Zeitanzeige](WEBSITE_REPLAY_TIME_0822_2026-11-13.md), [Masterplan](../ANDY_GESAMTKONZEPT_MASTERPLAN_v1.0.md), [Release-Checkliste](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/2).
