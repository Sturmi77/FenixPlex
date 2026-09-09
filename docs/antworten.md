# Antworten auf den Fragenkatalog

Status: **Defaults übernommen** — bitte abweichen und datieren, wo die Annahme nicht passt.

Ausgefüllt am: 2026-09-09  
Quelle der Defaults: Plan „FenixPlex: Spezifikation eingrenzen“

---

## A. Ziel und Abgrenzung

| # | Antwort | Abweichung / Notiz |
| --- | --- | --- |
| A1 | SubMusic zuerst evaluieren; bei Bedarf **forken**, kein Greenfield ohne Grund | |
| A2 | Ja — Sync ohne PC (Uhr + Phone + Heimnetz) | |
| A3 | Sideload / persönlich zuerst; Store später optional | |
| A4 | Nur Fenix 8 | |

## B. Sync-Modell

| # | Antwort | Abweichung / Notiz |
| --- | --- | --- |
| B5 | Variante **A** — Phone nur Setup/Settings | |
| B6 | Heim-Wi‑Fi an der Uhr ist vorausgesetzt | |
| B7 | Unterwegs-Sync **nicht** im MVP | |
| B8 | Manueller Sync-Start | |

## C. Plex und Bibliothek

| # | Antwort | Abweichung / Notiz |
| --- | --- | --- |
| C9 | Lokal + HTTPS auf 443 (Proxy oder plex.direct) | |
| C10 | Manuelles `X-Plex-Token` | |
| C11 | Sync-Einheit: **Playlists** | |
| C12 | MVP-Zielgröße: ca. ≤ 200 Tracks / 1–2 GB pro Sync-Set | |
| C13 | Transcode über Plex nach **MP3** | |
| C14 | Ein Plex-Server, ein Nutzer | |

## D. UX auf der Uhr

| # | Antwort | Abweichung / Notiz |
| --- | --- | --- |
| D15 | Playlists online browsen und zur Sync-Liste wählen | |
| D16 | Offline: Playlists + Shuffle | |
| D17 | Album Art / Listen-Counts: später | |
| D18 | Manuelles Löschen; Sync aktualisiert gewählte Playlists | |

## E. Edge, Sicherheit, Betrieb

| # | Antwort | Abweichung / Notiz |
| --- | --- | --- |
| E19 | Reverse Proxy auf 443 erlaubt | |
| E20 | Nur LAN im MVP | |
| E21 | Token auf Uhr / Connect IQ Settings, kein Cloud | |
| E22 | Verständliche Sync-Fehlerdiagnose | |

## F. Nicht-Ziele und Qualität

| # | Antwort | Abweichung / Notiz |
| --- | --- | --- |
| F23 | Kein Streaming; keine Full-Library On-Demand-Suche | |
| F24 | BT-Kopfhörer während Aktivität | |
| F25 | MVP zuerst | |
| F26 | Lizenz offen halten; bei Fork SubMusic-Lizenz beachten | |

## G. Erfolgskriterien

| # | Antwort | Abweichung / Notiz |
| --- | --- | --- |
| G27 | Eine Plex-Playlist per Wi‑Fi auf die Fenix 8 syncen und offline abspielen | |
| G28 | Setup &lt; 15 Min; ~50 Tracks zuverlässig syncbar; Offline-Playback | |

---

## Offene Blocker

Keine — Defaults gelten, bis hier bewusst überschrieben wird.
