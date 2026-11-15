# ANDY FACTORY – Budget Preflight & Funding Control V0.1

**15.11.2026 · Fachlicher Entwicklungsauftrag · geplant, noch nicht implementiert**

Projektleitung wünscht eine Live-Abfrage vorhandener Anbieterbudgets vor dem Forschungsbetrieb. Auto-Funding wird bei einigen ihrer Provider bereits genutzt; die konkrete Konfiguration, insbesondere Schwellenrichtung, Betrag, Währung und Monatsgrenze, wird je Anbieter lokal ermittelt. Keine Annahme, dass eine erwähnte 5-EUR-Schwelle bei allen Anbietern gleich wirkt. Keine Veröffentlichung individueller Guthaben, Zahlungsdaten oder Zugangsdaten.

Referenzen: [Betriebsmodell V0.2](ANDY_SYNC05_RELEASE_AND_OPERATING_MODEL_v0.2.md), [Factory Architektur V0.1](ANDY_FACTORY_THREE_INSTANCE_ARCHITECTURE_v0.1.md), [CACHE-01](ANDY_CACHE_01_IMPLEMENTATION_MEMO_v0.1.md).

## 1. Drei unabhängige Ressourcenebenen

| Ebene | Bedeutung | Wirkung |
|---|---|---|
| Provider Funding | Aktuell verfügbares Guthaben, Kosten-/Nutzungslimits, Abrechnungsart (Prepaid/Postpaid), Auto-Funding sofern nachweisbar | Zahlungsfähigkeit und externe Limits; keine automatische Startfreigabe |
| ANDY Factory Budget | Explizit freigegebenes Geldlimit je Queue/Lauf/Instanz, mit optionalen Teilkontingenten je Provider | Verbindliche lokale Freigabegrenze; keine Erhöhung durch Provider-Aufladung |
| Match-Ressourcen | Tokenbudget je Akteur, Output-Cap, Aufruf- und Retry-Limits | Sportliche Regeln und technisches Versuchslimit; kein Ersatz für Geldlimit |

Bei mehreren Modellen desselben Abrechnungskontos Guthaben nicht pro Modell addieren; bei mehreren Factories/Instanzen desselben Kontos gemeinsame externe Nutzung berücksichtigen. Getrennt bewilligte lokale Kontingente; keine globale Echtzeit-Koordinierung behaupten, solange nicht implementiert. Externe Aufladungen oder andere Prozesse können den Kontostand zwischen Abfragen ändern.

## 2. Live-Abfrage: zuerst tatsächlich verfügbare Provider-Schnittstellen auditieren

FACTORY-BUDGET-01A (read-only): pro tatsächlich konfiguriertem Provider/Endpoint prüfen, ob eine offiziell dokumentierte, autorisierte Abfrage für Guthaben, harte/ weiche Ausgabenlimits, Nutzung, Abrechnungsart und Auto-Funding existiert. Zugriffsumfang, Account-/Projektbezug, Währung, Aktualität und eventuelle Kosten dokumentieren. Vorhandene API-Keys können andere Berechtigungen als Billing-Keys haben; nicht ungeprüft privilegierte Schlüssel verlangen. Keine privaten Admin-Endpunkte erraten, keinen Dashboard-Scrape als verlässliche Datenquelle voraussetzen.

Adapter mit Capability-Profil je konkreter Route. Nicht jeder Anbieter stellt alle Felder bereit:
- Live bestätigt inkl. Zeitstempel und Scope
- manuell bestätigt inkl. Zeitstempel, Gültigkeit und Herkunft; ausdrücklich kein Live-Wert
- nicht unterstützt / nicht berechtigt / Fehler / veraltet / unbekannt

Fehlend ist nicht null. Kein Guthaben aus Nutzungskosten oder einem Kreditlimit erfinden. Postpaid-Konten haben nicht zwingend ein Guthaben im Prepaid-Sinn. Bei unbekanntem Funding oder fehlender Tarif-/Kosten-Evidenz automatischen Start blockieren; sofern technisch sinnvoll, ein separat und eng begrenzt freigegebener manueller Pilot mit dokumentiertem lokalem Kostenlimit und belastbarer Kostenabschätzung. Ein manueller Funding-Nachweis ersetzt keine fehlende belastbare Kostenabschätzung.

Abfrage ausschließlich lesend, mit Timeout, Rate-Limit-Backoff und ohne Provider-Modellaufruf. Keine automatische Zahlung, Aufladung, Änderung von Auto-Funding oder Anbieterlimits durch ANDY. Eventuelle kostenpflichtige Abfrage oder notwendige zusätzliche Berechtigung vor Ausführung transparent machen und freigeben lassen.

## 3. Preflight / Start-Gate

```text
    Nutzer: Queue + freigegebener EUR-Rahmen
                      |
             Provider-Routen ermitteln
                      |
             Read-only Funding-Check
                      |
        Tarif + Kostenreserve + lokale Limits
                      |
           +----------+----------+
           |                     |
         READY                BLOCKED
           |               Diagnose / manuelle
       explizites             Entscheidung
       Autoplay                  |
           |                     |
       vor jedem Match <---------+
           |
       Match -> Archiv -> Budget-Abgleich
           |
       naechster Preflight
```

- Vor Autoplay-Aktivierung alle benötigten Provider prüfen und pro Auftrag konservative Kostenreserve inklusive erwartbarer Retries, Output/Thinking/Input, Cache-Read/Write nach nachgewiesener Semantik und tatsächlichem Abrechnungsweg berechnen. Unbekannte Tarife nicht mit 0 bewerten. FX-Quelle/Datum und Reserve bei Nicht-EUR-Preisen dokumentieren.
- Vor jedem Match Funding-Aktualität erneut prüfen (Live-Refresh oder nach definierter Gültigkeit), lokale Restfreigabe und reservierte Kosten atomar abgleichen. Optional Refresh auf Nutzeraktion und bei Fehlern/Schwellenereignissen, keine unnötigen Polling-Lasten.
- Vor jedem Modellaufruf erwartbare maximale Mehrkosten gegen verbleibende lokale Freigabe prüfen; Reservierung über alle gleichzeitig zugelassenen Requests. Keine nachträgliche Freigabe durch Auto-Funding; kein nächster Call wenn Limit erreicht, Kostenbasis unbekannt oder Billing-Scope widersprüchlich. Provider-Abrechnung kann verzögert oder höher als Schätzung sein; ohne belastbare Obergrenze keine Garantie eines exakten Rechnungs-Hardcaps. Fehlende Abschluss-Usage darf keine Reserve automatisch freigeben.
- Bei Funding-/Kosten-/Provider-Fehler sicher blockieren/pausieren; kein sportlicher TKO allein wegen eines Factory-Funding-Problems. Technischen Stopp mit eigener Ursache protokollieren; laufende API-Antwort nicht als ungeschehen behandeln.
- Buchung: freigegeben, reserviert, geschätzt verbraucht, soweit vorhanden bestätigt abgerechnet, ungeklärt, verfügbar. Schätzung und Rechnung niemals doppelt summieren. Bestehende sportliche Tokenbudget-Semantik unangetastet.
- STOP nach aktueller Partie und sofortiger Schutzstopp bei Kosten-/Sicherheitsgrenze unterscheiden. Nach Crash offene Reservierung und unklaren Call nicht verdoppeln oder stillschweigend freigeben.

## 4. Auto-Funding

Auto-Funding ist optionales externes Provider-Verhalten, nicht die Factory-Freigabe. Wenn offiziell und autorisiert abfragbar: Status, Trigger (Richtung und Schwelle), Aufladebetrag/Zielguthaben, Zeit-/Monatslimit, Währung und Zeitpunkt der Beobachtung separat anzeigen. Sonst unbekannt bzw. manuelle Angabe. Jede Aufladung als separaten Funding-Vorgang behandeln, nicht als Modellverbrauch. Keine Änderung des Provider-Funding durch Factory. Bei Bedarf empfiehlt die UI eine manuelle Prüfung der Provider-Einstellungen; keine Zahlungslinks zu ungeprüften Zielen.

Beispiel (fiktiv): Factory-Freigabe 50 EUR, aktuell geschätzter Verbrauch 40 EUR, 6 EUR für unvollständige Calls reserviert. Verbleibende unreservierte Freigabe 4 EUR. Auto-Funding von 20 EUR beim Provider erhöht diese 4 EUR nicht. Ein 5-EUR-Auftrag wird blockiert, ohne weitere explizite Freigabe.

## 5. Produktionsmonitor / Budget-Tabelle

| Provider / Scope | Funding-Art | Guthaben / Ausgabenlimit | Auto-Funding | Datenstand | ANDY Restfreigabe je Kontingent | Gate |
|---|---|---|---|---|---|---|
| Beispiel A | Prepaid | Live-Wert | an/aus/unbekannt | Abfragezeit | lokal berechnet | READY/BLOCKED |
| Beispiel B | Postpaid | Limit, falls belegbar | nicht anwendbar / unbekannt | Abfragezeit | lokal berechnet | READY/BLOCKED |
| Beispiel C | unbekannt | nicht unterstützt | unbekannt | letzter Versuch | lokal berechnet | BLOCKED |

Illustrative Zeilen, keine echte Provider-Capability-Behauptung. Separate Account-Zeile, falls mehrere Modelle dieselbe Abrechnung teilen. Globale Factory-Restfreigabe prominent, keine Summierung mehrfach referenzierter Kontingente. Anzeige der Gründe je blockiertem Auftrag. Kosten- und Tokenfortschritt getrennt. Private Billing-Daten nur lokal; Export der Forschungsdaten enthält keine privaten Guthaben, Account-IDs oder Funding-Details.

## 6. Implementierungsreihenfolge und Abnahmekriterien

| Paket | Auftrag | Abnahme |
|---|---|---|
| FACTORY-BUDGET-01A | Provider-Capability-Audit, lesende Adapter und simulierte Daten | dokumentierte offizielle Route; Status/Scope/Währung/Frische; Fehlerfälle ohne Calls an Modelle |
| FACTORY-BUDGET-01B | lokales Budget-Ledger und Preflight-Service | persistente Freigaben/Reservierungen, Tests für mehrere Modelle pro Account, stale/unknown, parallele Nutzung, FX, begrenzte Retry-Kosten |
| FACTORY-BUDGET-01C | Budget-Tabelle und UI-Gates | manuelles Refresh, Funding/Auto-Funding getrennt, keine private Information im Forschungs-Export, verständliche Blockadegründe |
| FACTORY-03 | Integration in Autoplay | explizites Opt-in, pre-match/per-call Prüfung, Restart/Fehlerfälle; Auto-Funding kann Freigabe nicht erhöhen |

Beginne mit RESULT-SEMANTICS-02, FACTORY-01 (isolierte Grundinstallation) und parallel planbarem Budget-Audit; Budget-Gate ist zwingende Voraussetzung für freigegebenen automatischen kostenpflichtigen Betrieb. Bisherige CACHE-01-Normalisierung und Tarife wiederverwenden, keine zweite Kostenwahrheit. Keine Provider-Live-Abfragen in diesem Doku-Schritt ausgeführt; kein gebuchter Betrag, kein Funding-Zugriff, keine neue Programmlogik behauptet.


## 7. Provider-Vollabdeckung – Bridge-Inventar und erster Capability-Audit (15.11.2026)

**Ziel der Projektleitung: alle Provider der Bridge unterstützen**, auch wenn einzelne kein öffentlich dokumentiertes Live-Guthaben anbieten. Audit des Kandidaten ANDY_SYNC05_RESULT_DISPLAY.zip, Pfad `andy/infrastructure/providers/andy_llm_bridge.py`: elf Provider-IDs. Installierter Live-Code noch separat hashprüfen. Anbieter-/Routen-Zuordnung grundsätzlich aus gemeinsamer Registry ableiten; neue Bridge-Provider müssen einen expliziten Funding-Capability-Eintrag oder unknown-Fallback erhalten. Meta als Modellhersteller nicht zusätzlich zum tatsächlichen Abrechnungsanbieter Groq/OpenRouter zählen. Regionale Konten (z.B. Kimi) nie vermischen.

| Bridge-ID | Offiziell belegter oder zu prüfender Abfragepfad | Geplante Umsetzung / Grenze |
|---|---|---|
| deepseek | [GET /user/balance](https://api-docs.deepseek.com/api/get-user-balance/) | Standard-Inference-Key, Währung, verfügbares Guthaben und Teilbeträge. Offiziell dokumentierter Startkandidat; nur direkter bestätigter Host. |
| openrouter | [GET /api/v1/credits](https://openrouter.ai/docs/api/api-reference/credits/get-credits) | Management-Key, Gesamtcredits und Verbrauch; Scope prüfen. |
| xai | [Billing Management](https://docs.x.ai/developers/rest-api-reference/management/billing) | Separater Management-Key + Team-ID; Prepaid-Balance und Postpaid-Limits. Einheit/Vorzeichen anhand dokumentierter Beispiele und Live-Beleg validieren. [Auto-top-up in Console](https://docs.x.ai/console/billing) dokumentiert; maschinenlesbare Einstellungen noch nicht bestätigt. |
| qwen | [Alibaba Cloud QueryAccountBalance](https://www.alibabacloud.com/help/en/user-center/developer-reference/api-bssopenapi-2017-12-14-queryaccountbalance) | Separater RAM-Lesezugriff; Cash, Kredit und Währung unterscheiden. Gleiches Billing-Konto/Region zur DashScope-Route belegen; kein DashScope-Key an Billing-Endpunkt ungeprüft weiterreichen. |
| openai | [Admin APIs](https://developers.openai.com/api/docs/guides/admin-apis), [Organization costs](https://developers.openai.com/api/reference/python/resources/admin/subresources/organization) | Admin-Schnittstelle für Kosten und Limits; kein öffentlich belegter Live-Prepaid-Saldo im bisherigen Audit. Keine privaten Dashboard-Endpunkte. |
| anthropic | [Usage/Cost API und Analytics-Nachfolger](https://platform.claude.com/docs/en/manage-claude/usage-cost-api) | Kosten-/Nutzungsabfrage mit geeigneter Admin-/Analytics-Berechtigung; abhängig von Kontotyp. Kein bestätigter Prepaid-Saldo-Endpunkt. |
| gemini | [Gemini Billing](https://ai.google.dev/gemini-api/docs/billing/) | Prepay/Postpay und Auto-Reload dokumentiert; Cloud-Billing-Konto zu API-Projekt zuordnen. Live-Prepay-Saldo/Auto-Reload-API für konkrete Route noch nicht bestätigt. |
| mistral | [Billing](https://docs.mistral.ai/admin/billing-usage/billing), [Admin Usage](https://docs.mistral.ai/admin/admin-api/usage-metrics) | Guthaben und Auto-Recharge in Console; Enterprise-Admin-API für Usage. Kein bestätigter Live-Saldo-Endpunkt für Standardkonto. |
| groq | [Billing FAQ](https://console.groq.com/docs/billing-faqs), [Spend Limits](https://console.groq.com/docs/spend-limits) | Postpaid, Organisationslimits und verzögerte Usage in Console; geeigneten öffentlichen Billing-Leseendpunkt noch nicht bestätigt. |
| kimi | GET /v1/users/me/balance als Kandidat aus [Drittquellen-Dokumentation](https://github.com/bcharleson/codexbar/blob/main/docs/moonshot.md) | Offizielle Spezifikation, Währung, Region und Kontozuordnung noch zu verifizieren; bis dahin kein automatischer Probe-Request. |
| zai | Z.ai / Zhipu, konkrete Plattform und Billing-Route prüfen | Noch kein offiziell belegter Guthaben-Leseendpunkt ermittelt; manueller Nachweis / unknown. |

**Bewertung:** Dokumentationsaudit, keine Live-Verifikation von Konten. Nicht belegte Schnittstelle bedeutet nicht, dass sie definitiv nicht existiert. Auto-Funding-Abfrage ist ein separates Capability-Feld, nicht aus Guthaben ableiten. Bestehende Provider-Konfiguration nur auf Nutzerrechner und nur lesend prüfen; keine Secrets in Chat, Testreports, Browser oder GitHub. Admin-/Billing-Credentials optional, getrennt von Inference-Keys, geringstmöglicher Zugriff; keine zusätzliche Berechtigung automatisch verlangen. Ausschließlich feste, verifizierte HTTPS-Hosts/erlaubte Leseoperationen, keine Redirects mit Credentials, kein Top-up-/Limit-Write. Keine API-Calls beim Import des Moduls.

### Umsetzung in Wellen

1. Gemeinsames FundingSnapshot-/Capability-Schema für alle elf IDs; Status pro Feld, Scope, Originalwährung, Zeitstempel, Fehlerkategorie; unbekannte Provider fail-closed. Keine Beträge aus fehlenden Werten ableiten.
2. DeepSeek als erster offizieller Live-Balance-Pilot; Offline-Transport-Fixtures vor explizit freigegebenem lokalen Read-only-Check. Kimi erst nach offizieller Quellenklärung.
3. OpenRouter, xAI und Alibaba Cloud: optionale Billing-Zugriffe und sichere Kontozuordnung getrennt testen. OpenAI, Anthropic, Gemini, Mistral, Groq und Z.ai: jeweils dokumentierte Felder integrieren; manuelle Bestätigung für nicht abrufbare Funding-Felder. Ein reiner Kostenreport ist kein Saldo.
4. Gemeinsame UI/Preflight für alle Routen; automatische Produktionsfreigabe nur nach den in Abschnitt 3 definierten Kosten-, Funding- und Frische-Gates. Regression: jede Bridge-ID abgedeckt, Shared Accounts nicht doppelt zählen, Region/Gateway nicht stillschweigend wechseln, keinerlei Zahlungs-/Konfigurationsmutation.

Die elf Provider sind der aktuelle Zielumfang, keine Zusage von elf Live-Guthaben-APIs. Dieser Doku-Schritt ändert keine Bridge, kein Konto und keine laufende Partie.
