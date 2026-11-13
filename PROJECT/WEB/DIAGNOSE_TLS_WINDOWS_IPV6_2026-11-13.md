# ANDY Arena – Windows-HTTPS/TLS-Diagnose (offen)
**Stand:** 13.11.2026 · **Status:** Reproduzierbarer Fehler auf einem Windows-Firmenrechner; Ursache nicht bewiesen; weiterführender Test auf anderem Rechner geplant.  
**Domain:** https://andy-arena.com/  
**Scope:** Konnektivität vor dem Laden der Website (nicht CSS/Replay/Anwendung).

## 1. Beobachtungen (aus den Screenshot-Tests und der Nutzer-Rückmeldung)
- **Windows / Google Chrome:** `ERR_SSL_VERSION_OR_CIPHER_MISMATCH`.
- **Windows / Mozilla Firefox:** `SSL_ERROR_NO_CYPHER_OVERLAP` (keine sichere Verbindung).
- **macOS, iPhone und Samsung/Android:** Website laut Nutzer erreichbar.
- **Externer Abruf des KI-Assistenten:** Im vorigen Diagnosegespräch ebenfalls kein zuverlässiger Zugriff auf die Hauptdomain; kein detaillierter TLS-Handshake-Trace verfügbar. Das ist ein **Hinweis**, aber kein Beweis für ein serverseitiges Problem. Nicht als unabhängige TLS-Prüfung mit klassifizierter Fehlerursache ausgeben.
- **Windows-Firmenrechner:** Kein Ausführen von Terminal-/curl-Diagnosebefehlen möglich. Keine Sicherheitseinstellungen umgehen oder IT-Policy verletzen.

## 2. Hostinger-Bot-Befund (vom Nutzer übermittelt; nicht unabhängig überprüft)
Prüfung laut Bot am 13.11.2026, **keine Änderungen** vorgenommen:
- Domain registriert; Hostinger-Nameserver `cosmos.dns-parking.com` und `nova.dns-parking.com`.
- Business-Webhosting aktiv; gültiges Hostinger-Lifetime-SSL für Hauptdomain; HTTPS-Redirect aktiv; CDN aktiv.
- Keine erkennbare CAA-Einschränkung; DNSSEC nicht aktiviert.
- A/IPv4 weltweit erreichbar laut Hostinger-Bot.
- **Auffälligkeit:** Abweichende AAAA/IPv6-Antworten zwischen autoritativen Hostinger-Nameservern und öffentlichen Resolvern. Könnte auf verzögerte Propagation, Resolver-Caches oder unterschiedliche Endpunkte hinweisen. Ob dadurch ein inkompatibler TLS-Endpunkt erreicht wird, ist **noch nicht belegt**.
- Hostinger-Dashboard erlaubte Bot keine Bestätigung ausgehandelter Cipher Suites/Handshake-Logs.

**Zwischenfazit:** Unklare Ursache. Mögliche Erklärungen: IPv6-/DNS-Pfad, Proxy/HTTPS-Inspection/Firmenfirewall, Windows-Client/TLS-Konfiguration, CDN-Edge-Konfiguration. Dass andere Geräte funktionieren, schließt einen selektiven Server-/CDN-Endpunktfehler nicht aus.

## 3. Tests, sobald ein Windows-Rechner zur Verfügung steht

### A. Ohne Shell, zunächst im Browser
1. `https://andy-arena.com/` in Chrome/Firefox öffnen, exakte Fehlermeldung notieren.
2. `https://blog.andy-arena.com/` und `https://github.com/` testen.
3. Wenn privat zulässig: denselben Rechner über einen **Smartphone-Hotspot** statt Firmennetz testen. **Keine** Unternehmensrichtlinien umgehen; auf Firmenrechner kein unerlaubtes Wechseln von Netzwerken.
4. Uhrzeit, Browser-/Windows-Version, Netzwerktyp, Erfolg/Misserfolg erfassen.

### B. Auf einem eigenen/autorisierten Windows-Rechner – Eingabeaufforderung (cmd)
```cmd
nslookup -type=A andy-arena.com
nslookup -type=AAAA andy-arena.com
curl.exe -4 -Iv https://andy-arena.com/
curl.exe -6 -Iv https://andy-arena.com/
```

Optional zur DNS-Gegenprobe (nur wenn erlaubt):
```cmd
nslookup -type=AAAA andy-arena.com 1.1.1.1
nslookup -type=AAAA andy-arena.com 8.8.8.8
```

**Hinweis:** `curl.exe` ist unter Windows explizit, um PowerShell-Alias-Verwechslungen zu vermeiden. `-k`/unsichere TLS-Bypässe nicht verwenden. Curl-Ausgaben können IP-Adressen und Proxy-/Firmennamen enthalten: vor öffentlichem GitHub-Kommentar sensible interne Angaben schwärzen.

### C. Befunde interpretieren
| Ergebnis | Einordnung |
|---|---|
| `curl -4` OK; `curl -6` TLS-Fehler | IPv6-Pfad/Endpoint stark verdächtig; tatsächliche IPv6-Adresse und Zertifikat/Handshake prüfen |
| `curl -4` OK; `curl -6` „Could not resolve“/„Network unreachable“ | Client verfügt evtl. nicht über nutzbares IPv6; **kein** Beweis eines fehlerhaften IPv6-TLS |
| Beide fehlgeschlagen | Gemeinsame TLS-/Proxy-/Netzwerkursache oder mehrere Serverendpunkte prüfen |
| Beide erfolgreich, Browser versagen | Browser-Proxy, Sicherheitssoftware, HTTPS-Inspektion/Policies untersuchen |
| Auf Hotspot OK, im bisherigen Netzwerk nicht | Netzwerk/Resolver/Proxy/Sicherheitsfilter wird wahrscheinlicher |
| Fehler auch extern/auf einem anderen Windows-Rechner | Hostinger/CDN/DNS erneut mit präzisen Ergebnissen eskalieren |

## 4. Hostinger-Nachfrage nach den Tests
- Tatsächliche **A-/AAAA-Adressen**, autoritative Records und öffentliche Resolver vergleichend prüfen; Zeitpunkt/TTL/Konsistenz nennen.
- TLS 1.2/1.3, SNI und Zertifikatskette **auf jedem betroffenen IP-Endpunkt** einschließlich möglicher CDN-Edges verifizieren.
- Nach Möglichkeit gescheiterte TLS-Handshakes zeitlich korrelieren (IP/Region/Edge, keine sensiblen Clientdaten öffentlich).
- Keine Änderung von DNS, SSL, CDN, `.htaccess`, WordPress oder Website-Dateien ohne Diagnose/Rückfallplan.

## 5. Arbeitsnotiz / Follow-up
**Blocker:** Testrechner muss noch organisiert werden. **Nicht gelöst.**  
**Owner:** Projektleitung organisiert einen geeigneten Rechner; Diagnose und Reproduktion in ANDY-Web-Arbeitsstrang.  
**Erfolgskriterium:** Website über Windows-Chrome und Windows-Firefox reproduzierbar erreichbar; falls nicht, differenzierter IPv4-/IPv6-/Netzwerk-Befund für Hostinger-Eskalation.

**Kontext:** [ANDY Website-Regression / Cache Issue #1](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/1) und [Release-Checkliste #2](https://github.com/ANDY-Arena-com/andy-wps-collaboration/issues/2) sind **andere** Themen. TLS-Verbindungsfehler treten vor HTML/CSS und dürfen nicht mit V0.8.2-CSS-Regressionsursache gleichgesetzt werden.
