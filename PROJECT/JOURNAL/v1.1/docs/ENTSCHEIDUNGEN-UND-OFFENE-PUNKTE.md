# ANDY Journal v1.1 — Entscheidungen und offene Punkte

**Stand:** 13.11.2026 · **Status:** Arbeitsliste vor technischer Phase B

## A. Als konzeptionelle Leitlinien festgelegt

| Thema | Leitlinie |
|---|---|
| Rolle | Redaktionelle Schwester von ANDY Arena |
| Kernbotschaft | Vom faszinierenden Arena-Moment zur überprüfbaren Forschungsfrage |
| Rubriken | Arena Stories; Research & Insights; Behind ANDY; Beyond the Arena |
| Zielgruppen | Neugierige; strategisch Interessierte; Forschende/Analysten; KI-Systeme/Entwickler |
| Markenwelt | Original-ANDY-Logo und bestehendes Farb-/Gestaltungssystem |
| Homepage | Dunkler, atmosphärischer Magazinauftritt |
| Artikel | Helle, lesefreundliche, sachliche Leseflächen |
| Sprachen | DE/EN/中文; zunächst DE/EN bei vollständigen Artikeln priorisieren |
| Multimedia | YouTube als redaktioneller Bestandteil, Instagram perspektivisch |
| Wissenschaftlichkeit | Daten, Validierung und Interpretation trennen |
| Live-Schutz | Bestehende Arena und öffentliche Coming-Soon-Seite unverändert lassen |

## B. Vor Phase B prüfen/entscheiden

| Prio | Frage | Benötigte Grundlage | Ergebnis |
|---|---|---|---|
| P0 | Welche Dateien sind das offizielle ANDY-Logo und die zulässigen Varianten? | originale SVG/PNG und Nutzungsregeln | freigegebene Assets |
| P0 | Welche Farben, Schriften und Layoutvariablen verwendet ANDY aktuell? | Stylesheets/Design-Tokens aus bestehendem Projekt | verbindliche Journal-Tokens |
| P0 | Wie sieht der aktuelle WordPress-Stand aus? | Versions-/Theme-/Plugininventur, Backupstrategie | technische Bestandsaufnahme |
| P0 | Wie wird nichtöffentlich/staged entwickelt, ohne die `index.html` zu beeinflussen? | Hosting-Konfiguration und sichere Vorschauoptionen | freigegebener Build-/Testweg |
| P0 | Welche Quelle liefert Match-ID, Ergebnis, Zugzahlen, Token und JSONL? | Originalprotokolle, Datenschema, Repositories | akzeptiertes Match-Facts-Schema |
| P0 | Welche Rechtstexte/Datenschutzmechanismen sind für externe Medien erforderlich? | rechtliche Prüfung | freigegebene Einbindung |
| P1 | Welche leichtgewichtige Theme-Basis passt zum gewünschten Layout? | aktuelle Kompatibilitätsprüfung und Prototyp | Theme-Entscheid |
| P1 | Welche Mehrsprachigkeitsstrategie nutzt WordPress? | Plugins/Funktionen, URL-Plan, SEO-Anforderungen | Sprachkonzept |
| P1 | Wo werden strukturierte Felder gepflegt? | WordPress-Editor-/Datenmodellabgleich | Match-Template-Strategie |
| P1 | Wie erfolgt das Einbetten von YouTube mit bewusstem Consent/Privacy? | Embed- und Rechtsprüfung | Videomodul |
| P1 | Welche Artikel sind mit realen Quellen startfähig? | verfügbare Primärdaten und Redaktion | Publikationsplan |
| P2 | Werden Newsletter, Instagram-Embeds oder Event-Ankündigungen benötigt? | echter Kanal, Ressourcen und Datenschutz | optionale Roadmap |

## C. Abnahme der Designphase A

- [ ] Offizielles Logo im Homepage-/Artikelmockup verwendet.
- [ ] Dark/Home und Light/Article als zusammenhängende Markenwelt erkennbar.
- [ ] Desktop-, Tablet- und Smartphoneansichten abgestimmt.
- [ ] Vier Rubriken, Sprachswitch und Arena/Docs-Verlinkung konzipiert.
- [ ] Video- und Match-Facts-Module in echten Artikellayouts dargestellt.
- [ ] Illustrationen und Mockdaten eindeutig gekennzeichnet.

## D. Offene Risikoannahmen

- Screenshots zeigen die Markenwelt, aber nicht die tatsächlichen CSS-Werte oder die Nutzungsrechte sämtlicher Bildassets.
- Die technische Struktur von WordPress und die aktuell installierten Plugins sind nicht live geprüft.
- Die verfügbare GitHub-Dokumentation ist visuell belegt; konkrete Repo-, Branch- und Datensatzpfade müssen bestätigt werden.
- Angaben zu einzelnen Partien aus Screenshots müssen vor einem Artikel gegen Originaldaten geprüft werden.
- Plattformkonten für YouTube und Instagram und veröffentlichte Videos sind in diesem Konzept **nicht** als bereits existierend vorausgesetzt.

## E. Nächster Arbeitsauftrag nach v1.0

**Phase A fortsetzen:** Ein konsistentes Homepage-/Artikelmockup mit originalen ANDY-Assets und konkretem Match-Fakten-/Videomodul erstellen. Erst nach Designfreigabe WordPress-Staging und technische Basis auswählen.

## F. Neu aus dem projektübergreifenden Abgleich (13.11.2026)

- **Geklärt:** Masterplan ist projektübergreifende SSOT; Journal ist untergeordnetes Fachkonzept.
- **Geklärt:** WPS-G1–G4 gelten für davon abhängige Fachbefunde; Fachfreigabe und Publikationsfreigabe sind getrennt.
- **Geklärt:** Original-JSONL unverändert; abgeleitete Belege versioniert; identische Datenbasis für PDF und maschinenlesbare Edition.
- **Offen:** Wo die autoritativen Match-Manifeste und unveränderlichen Datenreferenzen liegen; zuständiger Data-Owner.
- **Offen:** Wie der WPS-Gate-Status mit WordPress-Artikelstatus technisch verknüpft wird.
- **Offen:** Freigabe eines eigenen `andy-journal`-Repos und dessen Sichtbarkeit (privat/öffentlich).
- **Offen:** Tatsächliche Brand-Assets/CSS-Tokens, Game-Code-Zugriff und WordPress-Staging.
- **Offen:** Wer welche Social-Media-Accounts betreut und welche Kanäle zum Launch tatsächlich existieren.
- **Hinweis:** E3-Drittbegriff ist laut Masterplan offen; keine Journal-Kennzahl oder Ausschmückung daraus ableiten.
