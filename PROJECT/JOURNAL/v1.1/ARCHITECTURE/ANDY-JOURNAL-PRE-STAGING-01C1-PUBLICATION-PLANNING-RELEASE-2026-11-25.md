# ANDY Journal · PRE-STAGING-01C1 – Publication & Coming Soon (sichere Vorbereitungsphase)

**Stand:** 25.11.2026 · **Status:** WordPress-Plugin-Update lokal erstellt und geprüft; **nicht installiert, nicht live abgenommen, kein öffentlicher Launch**.

**Basis:** Tatsächlich aus Hostinger exportierter Plugin-Code **ANDY Launch Control 0.1.0**; [PRE-STAGING Governance](ANDY-JOURNAL-PRE-STAGING-ADMIN-UND-LAUNCH-GOVERNANCE-2026-11-25.md) und [Menü-/Hook-Audit](ANDY-JOURNAL-PRE-STAGING-01A-PLUGIN-MENUE-HOOK-AUDIT-2026-11-25.md). Ziel: zentrale Planung statt zweites CMS oder zweites Home-Plugin. Stand des übrigen Systems laut Nutzer: Cockpit 0.2.3, RGB Pilot 0.6.4, Home Composer 0.1.39, Content Composer 0.1.29.

## Umgesetztes lokales Inkrement

**`andy-launch-control` 0.1.0 → 0.2.0**. Neuer Tab **Publication & Coming Soon** neben den unveränderten vier Pilot-Sitemap-/Content-/Profil-/QA-Tabs; **kein zusätzlicher Pluginordner**. Die alte Option `andy_launch_control_v010`, `plan.json`, `crossover-source.html` und bestehende Admin-Callbacks wurden beibehalten.

- Fünf Bereiche: Fight Night, Academy, Research, Perspectives, Making of. Geplante Modi `internal` / `coming_soon` / `live`, **Voreinstellung `internal`**. Redaktionelle DE/EN-Titel und Teaser mit vorbereiteten Vorschlagstexten; optionale validierte WP-Bild-ID.
- Sichere Speicherung über bestehende `alc_guard()`-Administratorberechtigung, Nonce, explizite Checkbox, Vollvalidierung aller fünf Bereiche, Gegenprüfung der Bild-ID und Schutz gegen paralleles Überschreiben (`revision`-Hash).
- Option `andy_publication_planning_v01`: redaktionelle Planung **ohne Laufzeitwirkung**. Die in WordPress gespeicherten Zustände verändern ausdrücklich **kein** Home-Modul, keine Gabelseite, keine öffentlich abrufbare Beitrags-/RGB-URL.
- Unabhängiger, **standardmäßig abgeschalteter** Historien-Tracker `andy_publication_history_optin_v01` über `transition_post_status`; er zeichnet erst nach expliziter Aktivierung echte Wechsel eines Standard-WP-Posts auf. Gespeichert werden `_andy_pub_first_observed_publish_gmt`, `_andy_pub_last_observed_publish_gmt`, `_andy_pub_last_observed_unpublish_gmt`, `_andy_pub_known_ever_published`. **Beobachtungsbeginn ≠ historisch erste Veröffentlichung.** Alte Entwürfe ohne Belege bleiben „unbekannt“, nicht „nie publiziert“.
- Zusätzliche redaktionelle Post-Metabox mit explizitem Rückzugsmarker `_andy_pub_editorial_withdrawn_v01`, Nonce, `edit_post` und Revisions-/Autosave-Ausschluss. Pausierung eines Bereichs wird **niemals** automatisch als redaktioneller Rückzug klassifiziert. Der Marker ändert aktuell **weder den WP-`post_status` noch öffentliche Sichtbarkeit**.
- **Keine** `wp_insert_post`-/`wp_update_post`-Aufrufe und **keine** Frontend-Routing-/Query-Hooks durch den neuen Code. Kein automatisches Publizieren, Deaktivieren, Löschen oder Umgestalten.

## Artefakte und QA

| ZIP, jeweils ein WordPress-Pluginroot | SHA-256 |
|---|---|
| `INSTALL-IN-WORDPRESS-ANDY-Launch-Control-0.2.0-PRE-STAGING-01C1.zip` | `3dd11e17e74e2dfc7f74187b34c99611e2f158e7ea924a3e3fba55bea1aec0ad` |
| `ROLLBACK-ANDY-Launch-Control-0.1.0.zip` | `0b665bcc0ce179aa0e61d587b1c2a5f897ac9096928dc78cddcb2e70806aaac7` |

**42/42 isolierte PHP-Stubprüfungen bestanden**: Defaultstatus und Textfelder, DE/EN, invalides Schema, fehlende Teaser, falsche Bilder, Wechsel-/Rückzugssemantik, Geschichtserfassung nur opt-in, keine Frontend-Hooks/Statusänderungen. PHP-Lint, ZIP-CRC und Plugin-Header auf beiden ZIPs bestanden. Original `plan.json` und `crossover-source.html` sind bytegleich. **Keine echte WP-/Hostinger-/Browserabnahme**, keine Performance-/Cache-/REST-Regression.

Die fertigen ZIPs sind **im Chat** ausgeliefert, **keine GitHub-Binärdateien**. Das vollständige Release-/Installationsprotokoll liegt als `ANDY-PRE-STAGING-01C1-LAUNCH-CONTROL-RELEASE-2026-11-25.md` im Chat.

## Abnahme- und Stop-Gate

Vor Installation vollständiges Hostinger-Backup mit DB, Uploads und aktiver Pluginliste. **Nur das einzelne 0.2.0-ZIP** installieren und vorhandenen Launch Control 0.1.0 ersetzen. Im Cockpit/Launch Control die vier unveränderten Pilot-Tabs und den neuen Tab prüfen; DE/EN-Teaser nur als **Plan** speichern. **Die öffentliche Home und die Gabelseiten müssen vor/nach der Installation gleich bleiben.** Historienbeobachtung zunächst abgeschaltet lassen. Bei Fehler mit 0.1.0-Rollback auf denselben Pluginordner zurückgehen; neue Options/Meta bleiben bis zu ausdrücklicher Bereinigung in der DB.

**PRE-STAGING-01C2 bleibt zwingend offen:** sichere End-to-End-Integration der zentralen Bereichszustände in **Home Composer**, **Content Composer** (virtuelle Gabelseiten und WordPress-Permalinks), **Making of**, **RGB Legacy-Assets**, **Suche, REST, Feeds, Sitemaps, DE/EN-Sprachpartner und Cache**. Die hier gespeicherten Zustände dürfen nicht vor dieser **vollständig getesteten** Freigabeschicht als wirksame Veröffentlichungssperren ausgegeben werden. Noindex ist kein Zugriffsschutz. Production-Home unverändert schützen; künftiges Staging benötigt eigenen echten Host-/Passwortschutz.