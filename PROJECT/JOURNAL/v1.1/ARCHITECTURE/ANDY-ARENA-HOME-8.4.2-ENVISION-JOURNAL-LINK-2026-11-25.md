# ANDY Arena Home 8.4.2 – EN Envision & Journal-Link

**25.11.2026 · Benutzerauftrag umgesetzt, lokal geprüft, nicht automatisch veröffentlicht.**

**Basis:** Vom Nutzer hochgeladene `home_Version_8.4.2..zip` (Arena-Home, getrennt von WordPress-Journal und dessen Home Composer).

Minimaländerungen:
- `en/index.html`: **zwei** sichtbare „Imagine“ durch **„Envision“** ersetzt: mobile dritte Karte sowie „Experience. Explore. Envision.“ in der Lab-Bridge.
- `de/index.html`, `en/index.html`, `zh/index.html`: jeweils **vier** bestehende Links auf `https://blog.andy-arena.com/` durch `https://journal.andy-arena.com/` ersetzt. Bezeichnungen unverändert.
- Alle anderen Archivmitglieder **bytegleich** zum Original. Kein CSS/JS, kein Hero, kein Footer, kein WordPress-Plugin oder Sprachwechsler geändert.

**Lokales Update-ZIP im Chat:** `ANDY-Arena-Home-8.4.2-Envision-Journal-Link.zip` – SHA-256 `5740091340db0f934bb6500dd68c2ee18791c3e9aac2e3b5a2c0febb86566035`.

**QA:** ZIP-Test bestanden; exakt drei geänderte HTML-Dateien, zwölf Linkersetzungen, zwei Textänderungen, 73 unveränderte Archiveinträge; alle 3 Locales mit vier neuen Journal-Links und ohne alte Blog-URL. **Kein Live-Deploy und kein Browser-E2E behauptet.**

**Installation:** Archivstruktur wurde beibehalten: `home_Version_8.4.2./de/index.html`, `en/index.html`, `zh/index.html`. Beim Deploy tatsächlich die drei lokalen HTML-Dateien in die korrespondierenden Home-Sprachordner übertragen; nicht versehentlich nur einen neuen Unterordner neben dem aktiven Webroot entpacken. Vorher Live-Backup, danach DE/EN/ZH Journal-Navigation und EN-Mobile/EN-Desktop testen.
