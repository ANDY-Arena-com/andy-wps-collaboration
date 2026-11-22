# ANDY Journal – Integrator 01: vollständige Zuordnungsmatrix

**Stand:** 22.11.2026. **Quelle:** Original-Laufzeitbericht `ANDY-INTEGRATOR-01-20261122.json`, erzeugt 2026-11-22 11:43:21 auf https://glad-whitesmoke-octopus-16.hostingersite.com/. **Status:** Bestandsaufnahme, kein Deployment, keine bestätigte Inhaltsmigration.

Die tabellarische Matrix wurde aus dem Nutzer-JSON des WordPress-Integrators 0.1 generiert und entspricht der in ChatGPT bereitgestellten Excel-Arbeitsmappe. Titelgleiche WP-Beiträge sind *Kandidaten*, keine bestätigte Inhaltsgleichheit. RGB-Routen werden hier nicht auf tatsächliche Erreichbarkeit geprüft. Zugangsdaten, Artikelvolltexte und Roh-Elementor-Daten sind nicht enthalten.

## A. Übersicht

| Kennzahl | Ist |
| --- | --- |
| WordPress-Startseite | page · ID 14 |
| WP-Beitragsseite | ID 733 |
| Native Posts und Pages | 34 |
| RGB-Registerseiten | 28 |
| Sitemap-Demos | 14 |
| Aculia-Objekte | 4 |
| Aculia-Widget-Datensätze | 58 |
| Frontend-Migration | Nicht durchgeführt |

## B. RGB / Sitemap: 28 Seiten

| RGB-Key | Titel | Familie | Typ | Elternknoten | RGB-Route | WP-ID-Kandidat | Bewertung |
| --- | --- | --- | --- | --- | --- | --- | --- |
| home | Home | home | Home | — | / | 14 | Homepage-Kandidat |
| erleben | Erleben | zugang | Zugang | home | ?andy_rgb_asset=erleben.html | — | Kein nativer Titel-Treffer |
| replays | Replay · Match Stories | spiele | Sub-Home | erleben | ?andy_rgb_asset=replays.html | — | Kein nativer Titel-Treffer |
| replay | Sie kennen die Regeln. Aber nicht das Spiel. | spiele | Match-Dokumentation | replays | ?andy_rgb_asset=replay.html | — | Kein nativer Titel-Treffer |
| replay-scene-74 | Sechs Steine mit einem Zug. | spiele | Schlüsselszene | replays | ?andy_rgb_asset=replay-scene-74.html | — | Kein nativer Titel-Treffer |
| replay-scene-case001 | Ein Schach mit überraschender Folge. | spiele | Schlüsselszene | replays | ?andy_rgb_asset=replay-scene-case001.html | — | Kein nativer Titel-Treffer |
| academy | Academy | academy | Sub-Home | erleben | ?andy_rgb_asset=academy.html | — | Kein nativer Titel-Treffer |
| l01 | Wo würdest du deinen ersten Go-Stein setzen? | academy | Lernmodul | academy | ?andy_rgb_asset=l01.html | — | Kein nativer Titel-Treffer |
| l02 | Wie kann ein Stein sechs gegnerische Steine schlagen? | academy | Lernmodul | academy | ?andy_rgb_asset=l02.html | — | Kein nativer Titel-Treffer |
| l03 | Blockieren Go-Steine Schachfiguren? | academy | Lernmodul | academy | ?andy_rgb_asset=l03.html | — | Kein nativer Titel-Treffer |
| erforschen | Erforschen | zugang | Zugang | home | ?andy_rgb_asset=erforschen.html | — | Kein nativer Titel-Treffer |
| research-index | Research | research | Sub-Home | erforschen | ?andy_rgb_asset=research-index.html | — | Kein nativer Titel-Treffer |
| crossover | Crossover-Muster | research | Forschungsgebiet | research-index | ?andy_rgb_asset=crossover.html | — | Kein nativer Titel-Treffer |
| crossover-agentic-ai | Jenseits des Schachbretts: Wie lässt sich die Handlungsfähigkeit agentischer KI erforschen? | research | Crossover-Artikel | crossover | ?andy_rgb_asset=crossover-agentic-ai.html | — | Kein nativer Titel-Treffer |
| continuity | AI Continuity Research | research | Forschungsagenda | research-index | ?andy_rgb_asset=continuity.html | — | Kein nativer Titel-Treffer |
| decision-research | Entscheidungsverhalten | research | Forschungsgebiet | research-index | ?andy_rgb_asset=decision-research.html | — | Kein nativer Titel-Treffer |
| research | Wenn der Zug nicht zur Begründung passt. | research | Fallstudie | decision-research | ?andy_rgb_asset=research.html | — | Kein nativer Titel-Treffer |
| tools | ANDY Tools | tools | Sub-Home | erforschen | ?andy_rgb_asset=tools.html | — | Kein nativer Titel-Treffer |
| documentation | ANDY Dokumentation | projekt | Dokumentation | erforschen | ?andy_rgb_asset=documentation.html | — | Kein nativer Titel-Treffer |
| making-of | Making of | projekt | Sub-Home | erforschen | ?andy_rgb_asset=making-of.html | — | Kein nativer Titel-Treffer |
| making-of-journal | Vom HTML-Dummy zum Journal | projekt | Werkstattbericht | making-of | ?andy_rgb_asset=making-of-journal.html | — | Kein nativer Titel-Treffer |
| erahnen | Erahnen | zugang | Zugang | home | ?andy_rgb_asset=erahnen.html | — | Kein nativer Titel-Treffer |
| perspectives | Perspectives | perspektive | Sub-Home | erahnen | ?andy_rgb_asset=perspectives.html | — | Kein nativer Titel-Treffer |
| andy-demo-chess-meets-go | When Chess Meets Go | perspektive | Essay | perspectives | ?andy_rgb_asset=andy-demo-chess-meets-go.html | 1329 | Titelgleich (prüfen) |
| andy-demo-fragility-of-balance | The Fragility of Balance | perspektive | Essay | perspectives | ?andy_rgb_asset=andy-demo-fragility-of-balance.html | 1331 | Titelgleich (prüfen) |
| andy-demo-when-rules-change | When the Rules Change | perspektive | Essay | perspectives | ?andy_rgb_asset=andy-demo-when-rules-change.html | 1333 | Titelgleich (prüfen) |
| andy-demo-thinking-in-networks | Thinking in Networks | perspektive | Essay | perspectives | ?andy_rgb_asset=andy-demo-thinking-in-networks.html | 1335 | Titelgleich (prüfen) |
| andy-demo-beyond-next-move | Beyond the Next Move | perspektive | Essay | perspectives | ?andy_rgb_asset=andy-demo-beyond-next-move.html | 1337 | Titelgleich (prüfen) |

## C. Aculia / Elementor: 58 Widget-Datensätze

| WP-Objekt | Seite/Template | Widget-ID | Widget-Typ | Widget-Gruppe | Titelhinweis | Tiefe |
| --- | --- | --- | --- | --- | --- | --- |
| 14 | Home Page 01 | 1eef5e6 | wpsection_banner_slider | Slider / Hero | — | 2 |
| 14 | Home Page 01 | 2620f9a | wpsection_service_block | Services / Tabs | Immunology: T-cell tweaks to target tumours | 2 |
| 14 | Home Page 01 | f66143a | wpsection_service_block | Services / Tabs | Molecular biology: RNA editing packs a two punch | 2 |
| 14 | Home Page 01 | fd3a66b | wpsection_service_block | Services / Tabs | Cardiovascular disease: Commonality with cancer | 2 |
| 14 | Home Page 01 | 054176c | wpsection_service_block | Services / Tabs | Immunology: T-cell tweaks to target tumours | 2 |
| 14 | Home Page 01 | 5e4b9b1 | heading | Text / Titel | Our Services | 2 |
| 14 | Home Page 01 | a306f0a | text-editor | Text / Titel | — | 2 |
| 14 | Home Page 01 | ce18fb3 | divider | Sonstiges | — | 2 |
| 14 | Home Page 01 | 844ac79 | divider | Sonstiges | — | 2 |
| 14 | Home Page 01 | 87443e1 | wpsection_service_tab | Services / Tabs | — | 2 |
| 14 | Home Page 01 | 5dd18f6 | icon-box | Informationsbereich | — | 4 |
| 14 | Home Page 01 | 7a15d30 | icon-box | Informationsbereich | — | 4 |
| 14 | Home Page 01 | b525e53 | icon-box | Informationsbereich | — | 4 |
| 14 | Home Page 01 | a9b2f47 | icon-box | Informationsbereich | — | 4 |
| 14 | Home Page 01 | 27b9ad9 | icon-box | Informationsbereich | — | 4 |
| 14 | Home Page 01 | dca9388 | icon-box | Informationsbereich | — | 4 |
| 14 | Home Page 01 | ce2b4fb | heading | Text / Titel | All The Services You Expect  From Aculia | 2 |
| 14 | Home Page 01 | e7344ed | wpsection_button | Sonstiges | — | 2 |
| 14 | Home Page 01 | 02980a7 | heading | Text / Titel | Immunology: T-cell tweaks  to target tumours | 2 |
| 14 | Home Page 01 | 19fdb31 | icon-list | Informationsbereich | — | 4 |
| 14 | Home Page 01 | fc298c6 | icon-list | Informationsbereich | — | 4 |
| 14 | Home Page 01 | 111f4bb | icon-list | Informationsbereich | — | 4 |
| 14 | Home Page 01 | 9d15120 | icon-list | Informationsbereich | — | 4 |
| 14 | Home Page 01 | ca16640 | wpsection_vedio_image_box | Bild-/Text-Feature | — | 2 |
| 14 | Home Page 01 | b44f902 | heading | Text / Titel | Reliable & High  Quality Laboratory | 2 |
| 14 | Home Page 01 | 20f8288 | text-editor | Text / Titel | — | 2 |
| 14 | Home Page 01 | 802cd2e | heading | Text / Titel | Excepteur sint occaecat cupidatat non proident sunt culpa qui officia deserunt mollit anim id est la | 2 |
| 14 | Home Page 01 | 3faef91 | text-editor | Text / Titel | — | 2 |
| 14 | Home Page 01 | d3a356c | divider | Sonstiges | — | 2 |
| 14 | Home Page 01 | 9a1fcab | wpsection_testimonials | Sonstiges | — | 2 |
| 14 | Home Page 01 | db26a23 | heading | Text / Titel | Aculia Journal | 2 |
| 14 | Home Page 01 | 45754a9 | text-editor | Text / Titel | — | 2 |
| 14 | Home Page 01 | 558f043 | divider | Sonstiges | — | 2 |
| 14 | Home Page 01 | 00f3fdb | divider | Sonstiges | — | 2 |
| 14 | Home Page 01 | ffe9286 | wpsection_blog_grid | Artikel / News | — | 2 |
| 14 | Home Page 01 | 92ad9b3 | shortcode | Sonstiges | — | 2 |
| 14 | Home Page 01 | 4cf15ee | wpsection_allslider | Slider / Hero | — | 1 |
| 26 | Header One | 5b651b3 | wpsection_header | Sonstiges | — | 2 |
| 532 | Header Two | c0cb75f | wpsection_header_two | Sonstiges | — | 2 |
| 455 | Footer One | 7fa2c15e | image | Bild-/Text-Feature | — | 2 |
| 455 | Footer One | 770818bd | image | Bild-/Text-Feature | — | 4 |
| 455 | Footer One | 62902975 | text-editor | Text / Titel | — | 4 |
| 455 | Footer One | 591c7e2 | social-icons | Informationsbereich | — | 4 |
| 455 | Footer One | 23925f03 | heading | Text / Titel | Quick Link | 4 |
| 455 | Footer One | 639d7eaf | icon-list | Informationsbereich | — | 4 |
| 455 | Footer One | 086b894 | icon-list | Informationsbereich | — | 4 |
| 455 | Footer One | 3b821c0f | icon-list | Informationsbereich | — | 4 |
| 455 | Footer One | cf9ae60 | icon-list | Informationsbereich | — | 4 |
| 455 | Footer One | 2b3663ea | icon-list | Informationsbereich | — | 4 |
| 455 | Footer One | 9aa915d | heading | Text / Titel | Latest Events | 4 |
| 455 | Footer One | cd70b64 | heading | Text / Titel | Haematopoietic stem cell tation for autoimmune | 4 |
| 455 | Footer One | 6c6d2f6 | icon-list | Informationsbereich | — | 4 |
| 455 | Footer One | 93a051a | heading | Text / Titel | Inventore veritatis et quasi vitae dicta architebeatae | 4 |
| 455 | Footer One | 83280bd | icon-list | Informationsbereich | — | 4 |
| 455 | Footer One | 27148d4a | heading | Text / Titel | Contact Us | 4 |
| 455 | Footer One | 74a01fa2 | text-editor | Text / Titel | — | 4 |
| 455 | Footer One | 2455fb1 | heading | Text / Titel | Aculia | 4 |
| 455 | Footer One | 5bd2d96b | heading | Text / Titel | © 2023 All Right Reserved | 4 |

## D. Home-Komposition (Arbeitszuordnung; Widget-Kompatibilität offen)

| Aculia-Widget-ID / Typ | Vorgeschlagene ANDY-Rolle | Inhalt | Prüfpunkt |
| --- | --- | --- | --- |
| 1eef5e6 / wpsection_banner_slider | Top 3 Story-Slider | D01 Fight Night, D05 Crossover, D07 Research | Slider-Inhalte, Bilder, Links und Mobil-Verhalten im 2A-Feldaudit prüfen |
| 87443e1 / wpsection_service_tab; 2620f9a, f66143a, fd3a66b, 054176c / wpsection_service_block | Fight Night – auswählbare Matches | D01 Hauptmatch; D02/D03 Szenen | Tab-Verhalten/Seiten-Zuordnung/Replay prüfen; Szenen keine vollständigen Spiele |
| ca16640 / wpsection_vedio_image_box | Perspektive / Crossover | D05 Jenseits des Schachbretts | Medienfeld, Link-Ziel und Rechte prüfen |
| 02980a7 / heading | Research-Feature | D07 Wenn der Zug nicht zur Begründung passt | Originaldaten/-grafik und Darstellung prüfen |
| 5dd18f6, 7a15d30, b525e53 / icon-box (weitere ebenfalls vorhanden) | Academy-Einstiege | D09–D11 L01–L03 | Icon-Boxen sind nur Teaser; kein Ersatz für echtes interaktives Brett |
| ffe9286 / wpsection_blog_grid | Journal / native Beiträge | Fünf bereits native ANDY-Essays | Abfragequelle/Filter/Sortierung/Dubletten prüfen |
| 92ad9b3 / shortcode | Tools und echte ANDY-Interfaces | D12 ANDY Tools | Original-Shortcode/Renderer prüfen |
| 455 / Footer One | A–Z, Sitemap, Dokumentation | D13/D14 plus Sitemap | Bestehende Footer-Links und Theme-Templates prüfen |

## E. Editorial-Demos: 14 Einträge

| Demo-ID | Titel | Familie | Typ | RGB-Key | Teaserbild | Medien im Inhalt | Status |
| --- | --- | --- | --- | --- | --- | --- | --- |
| D01 | Sie kennen die Regeln. Aber nicht das Spiel. | spiele | Match-Dokumentation | replay | Matchplakat / Modellidentität | Original-Replay, dokumentierte Partie | Bestandsinhalt |
| D02 | Sechs Steine mit einem Zug. | spiele | Schlüsselszene | replay-scene-74 | Spielstellung / Ausschnitt | Einzelszene, Vorher/Nachher, Replay-Verweis | Bestandsinhalt |
| D03 | Ein Schach mit überraschender Folge. | spiele | Schlüsselszene | replay-scene-case001 | Typografisches Ereignis / Detail | Fall-001-Schlüsselszene | Bestandsinhalt |
| D04 | When Chess Meets Go | perspektive | Essay | andy-demo-chess-meets-go | Fotografisches Editorial | Text und konzeptionelle Illustration | Bestandsinhalt |
| D05 | Jenseits des Schachbretts | perspektive | Crossover | crossover-agentic-ai | Reportage / offene Bildwelt | Argument, Forschungsbezug, Quellen | Bestandsinhalt |
| D06 | AI Continuity Research | research | Forschungsagenda | continuity | Konzeptgrafik / Textteaser | Agenda und offene Forschungsfragen | Bestandsinhalt |
| D07 | Wenn der Zug nicht zur Begründung passt. | research | Fallstudie | research | Originalgrafik / Kennzahl | Datenvisualisierung und Methodenabgrenzung | Bestandsinhalt |
| D08 | Datenresonanzpunkt | research | Interaktives Forschungsmodell | — | Charakteristische Kurve | Geplante interaktive Grafik mit Parametern | Konzept / nicht publiziert |
| D09 | Wo würdest du deinen ersten Go-Stein setzen? | academy | Lernmodul | l01 | Handlung / Schrittfolge | Brettübung und Quiz | Bestandsinhalt |
| D10 | Wie kann ein Stein sechs gegnerische Steine schlagen? | academy | Lernmodul | l02 | Zuganimation / Brettdetail | L02: Demo-Brett, Folge und Quiz | Bestandsinhalt |
| D11 | Blockieren Go-Steine Schachfiguren? | academy | Lernmodul | l03 | Vorher/Nachher | L03: Brettvergleich und Phasenwechsel | Bestandsinhalt |
| D12 | ANDY Tools | tools | Anwendungsübersicht | tools | Echter ANDY-UI-Crop | Observer, Lab und Daten anhand echter Screenshots | Bestandsinhalt |
| D13 | ANDY Dokumentation | projekt | Dokumentation | documentation | Originaloberfläche / Dokument | Originalregeln und Dokumentation referenzieren | Bestandsinhalt |
| D14 | Vom HTML-Dummy zum Journal | projekt | Making of | making-of-journal | Vorher/Nachher / echter Screenshot | Werkstattbericht und Entwicklungsstand | Bestandsinhalt |

## F. Native WordPress-Posts / Pages: 34 Objekte

| WP-ID | Typ | Status | Titel | Slug |
| --- | --- | --- | --- | --- |
| 1 | post | draft | Hello world! | hello-world |
| 2 | page | publish | Sample Page | sample-page |
| 3 | page | draft | Privacy Policy | privacy-policy |
| 10 | page | publish | Checkout | checkout |
| 11 | page | publish | My account | my-account |
| 12 | page | draft | Refund and Returns Policy | refund_returns |
| 14 | page | publish | Home Page 01 | home-one |
| 522 | page | publish | Research Page | research-page |
| 628 | page | publish | Our Books | our-books |
| 663 | page | publish | Journal Articles | journal-articles |
| 681 | page | publish | Our Team | our-team |
| 686 | page | publish | Team Details | team-details-2 |
| 713 | page | publish | Our Events | our-events |
| 724 | page | publish | Event Details | event-details |
| 733 | page | publish | Our Blog | our-blog |
| 739 | post | publish | Molecular biology: Editing packs punch. | molecular-biology-editing-packs-punch |
| 740 | post | publish | Immunology: T-cell tweaks to target tumours. | immunology-t-cell-tweaks-to-target-tumours |
| 741 | post | publish | Lorem ipsum dolor sit amet, consectetur. | lorem-ipsum-dolor-sit-amet-consectetur |
| 742 | post | publish | Excepteur sint occaecat cupidatat. | excepteur-sint-occaecat-cupidatat-2 |
| 743 | post | publish | Haematopoietic stem cell transplant. | haematopoietic-stem-cell-transplant-2 |
| 744 | post | publish | Lacinia eget consecte sed convallis. | lacinia-eget-consecte-sed-convallis-3 |
| 764 | page | publish | Blog Details | blog-details-2 |
| 766 | page | publish | Contact Us | contact-us |
| 850 | page | publish | Home Page 02 | home-page-02 |
| 981 | page | publish | Home Page 03 | home-page-03 |
| 1276 | page | draft | Privacy Policy | privacy-policy |
| 1277 | page | publish | Shop | shop |
| 1278 | page | publish | Cart | cart |
| 1279 | post | publish | Hello world! | hello-world-2 |
| 1329 | post | publish | When Chess Meets Go | andy-demo-chess-meets-go |
| 1331 | post | publish | The Fragility of Balance | andy-demo-fragility-of-balance |
| 1333 | post | publish | When the Rules Change | andy-demo-when-rules-change |
| 1335 | post | publish | Thinking in Networks | andy-demo-thinking-in-networks |
| 1337 | post | publish | Beyond the Next Move | andy-demo-beyond-next-move |

## G. Plugin-Bestand zum Zeitpunkt des Berichts

| Plugin | Version | Aktiv |
| --- | --- | --- |
| ANDY Content Manager | 0.4.6 | Ja |
| ANDY Journal Cockpit | 0.1.0 | Ja |
| ANDY Journal Integrator — Inventur 0.1 | 0.1.0 | Ja |
| ANDY Journal — Editorial Sitemap v2 Pilot | 0.1.0 | Ja |
| ANDY Launch Control | 0.1.0 | Ja |
| ANDY RGB Content Pilot | 0.6.1 | Ja |

## Nächster Schritt

Integrator **0.2A** liest nur die Namen, Typen und Strukturen der tatsächlichen Elementor-Settings und ermittelt Hashes und Medien-ID-Hinweise an der Startseite und den genannten Templates. Das Ergebnis ist ein eigener, lokaler JSON-Export; er ist noch kein Frontend-Dry-Run und darf nicht als Beweis für ein funktionierendes Replay oder ein korrektes Template ausgelegt werden.

**Sicherheitsgrenze:** Dieses Dokument ist eine zuordenbare Planungsgrundlage. Keine Schreiboperation auf WordPress und keine Änderung an RGB-Auslieferung, Aculia-Startseite oder öffentlicher Arena.