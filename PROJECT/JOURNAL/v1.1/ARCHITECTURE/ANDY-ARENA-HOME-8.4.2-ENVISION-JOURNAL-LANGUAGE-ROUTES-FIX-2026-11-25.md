# ANDY Arena Home 8.4.2 – Envision und sprachrichtige Journal-Links (Korrektur)

25.11.2026 · Korrigierte Auslieferung basierend auf der **originalen Nutzer-ZIP `home_Version_8.4.2..zip`**. Separat von WordPress-Journal / Home Composer.

## Fehler in der ersten Änderung

Die erste Korrektur ersetzte nur zwei englische `Imagine`-Vorkommen; die sichtbare Footer-Zeile `EXPERIENCE · EXPLORE · IMAGINE` blieb stehen. Außerdem verlinkten alle drei Arena-Sprachen auf die Journal-Root statt auf ihre jeweils gewünschte Sprachversion. Der ursprüngliche Upload war zusätzlich in den ZIP-Unterordner `home_Version_8.4.2./` verschachtelt, was beim Entpacken leicht zu falschen Zieldateien führt.

## Korrektur

- `en/index.html`: alle **3** sichtbaren Imagine-Vorkommen inkl. **englischem Footer** durch Envision / ENVISION ersetzt (Mobile-Karte, Lab-Bridge, Footer). Keine weiteren Imagine-Treffer in den hochgeladenen Quelldateien.
- `de/index.html`: exakt **4 Journal-Links** → `https://journal.andy-arena.com/de/`.
- `en/index.html`: exakt **4 Journal-Links** → `https://journal.andy-arena.com/en/`.
- `zh/index.html`: exakt **4 Journal-Links** → `https://journal.andy-arena.com/en/` (**vom Nutzer ausdrücklich bestätigt: ZH-Übersetzung im Journal noch nicht vorhanden, daher EN-Fallback**).
- Außer diesen drei HTML-Dateien keine Quelldatenänderungen. Die Journal-Sprachpfade leiten sich aus der dokumentierten DE/EN-Routenstruktur des Projekts ab; **externes Live-HTTP-Abrufen war hier nicht möglich** – nach Veröffentlichung direkte Routen und Linknavigation prüfen.

## Artefakte im Chat

- **Empfohlen als gezieltes Site-Update:** `ANDY-Arena-Home-8.4.2-NUR-3-HTML-DATEIEN.zip` SHA256 `5f2315febf3c6e3708b8cff5bdd8759c546ddbdee0e49eb7fa25be83a8451b80` – nur `de/index.html`, `en/index.html`, `zh/index.html` direkt am ZIP-Root.
- **Gesamte Home, webroot-kompatibel flach:** `ANDY-Arena-Home-8.4.2-Envision-Journal-DE-EN-ZHtoEN-FIX.zip` SHA256 `081c82cd17a88a0a4849356b5b7e8dd107b8c04e74ee2250bd50f5e9194e1d92`; keine `__MACOSX`-Einträge, keine zusätzliche `home_Version_8.4.2./`-Ebene.

**Prüfung:** ZIP-CRC, 4 Hrefs je Sprache, 3 Imagine-Ersetzungen und bytegleiche übrige 26 Quelldateien geprüft. **Kein Online-Deployment oder Live-Linktest behauptet.** Vorher Webroot-Backup; die drei HTML-Dateien **im aktiven de/en/zh-Ordner** ersetzen, Site/CDN-Cache leeren, EN-Footer sowie 12 Sprachlinks direkt in Browser prüfen.

Die ältere Datei `ANDY-ARENA-HOME-8.4.2-ENVISION-JOURNAL-LINK-2026-11-25.md` ist für die Links und Imagine-Zählung überholt.