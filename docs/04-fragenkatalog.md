# Fragenkatalog — Spec eingrenzen

Fragen priorisiert beantworten. **Blocker (A) zuerst.**  
Antworten in [antworten.md](antworten.md) eintragen (Vorlage mit Defaults vorausgefüllt).

Legende: `[ ]` offen · `[x]` beantwortet · Default = Annahme aus [05-mvp-entwurf.md](05-mvp-entwurf.md)

---

## A. Ziel und Abgrenzung (Blocker)

| # | Frage | Default |
| --- | --- | --- |
| A1 | Primärziel: **eigene CIQ-App**, **SubMusic nutzen/forken**, oder **Desktop/USB-Exporter**? | SubMusic evaluieren, bei Lücken **Fork** (nicht Greenfield) |
| A2 | Muss Sync **ohne PC** funktionieren (nur Uhr + Phone + Heimnetz)? | Ja |
| A3 | App **nur für dich (sideload)** oder **Connect IQ Store / andere Nutzer**? | Sideload zuerst |
| A4 | Welche Geräte außer Fenix 8? | Nur Fenix 8 |

## B. Sync-Modell

| # | Frage | Default |
| --- | --- | --- |
| B5 | „Über Mobiltelefon“ = nur Setup (**A**), Phone-Proxy (**B**), oder Dateitransfer vom Phone? | **A** (Phone = Setup) |
| B6 | Ist **Heim-Wi‑Fi an der Uhr** vorausgesetzt und akzeptabel (wie Spotify/Deezer)? | Ja |
| B7 | Sync auch unterwegs (Hotspot, Remote Plex, VPN)? | Nein im MVP |
| B8 | Manueller Sync-Start vs. periodisch/automatisch beim Docken/Laden? | Manuell |

## C. Plex und Bibliothek

| # | Frage | Default |
| --- | --- | --- |
| C9 | Plex lokal, Remote Access, oder hinter VPN/Tailscale? | Lokal + HTTPS-Proxy / `plex.direct` |
| C10 | Auth: manuelles Token, plex.tv Login, oder beides? | Manuelles `X-Plex-Token` |
| C11 | Sync-Einheit: **Playlists**, Alben, Artists, Smart Playlists, Podcasts? | **Playlists** |
| C12 | Bibliotheksgröße (Tracks / GB) und Hardcap auf der Uhr? | Hardcap später; MVP: eine Playlist ≤ ~200 Tracks / ~1–2 GB |
| C13 | Quellformate? Transcoding über Plex? Zielbitrate? | Plex-Transcode → **MP3** (~160–192 kbps) |
| C14 | Mehrere Plex-Server / Nutzer / Shared Libraries? | Ein Server, ein Nutzer |

## D. UX auf der Uhr

| # | Frage | Default |
| --- | --- | --- |
| D15 | Browse online vs. nur vorkonfigurierte Sync-Liste? | Online-Browse der Playlists zur Sync-Auswahl |
| D16 | Offline: Playlists, Shuffle, Queue, Podcast-Mode? | Playlists + Shuffle; Queue/Podcast später |
| D17 | Album Art, Listen-Counts zurück zu Plex? | Nice-to-have; nicht MVP-kritisch |
| D18 | Speicherverwaltung: manuell löschen, LRU, „Playlist ersetzen“? | Manuell + Sync ersetzt Auswahl |

## E. Edge, Sicherheit, Betrieb

| # | Frage | Default |
| --- | --- | --- |
| E19 | Darf ein **Reverse Proxy auf 443** betrieben werden? | Ja |
| E20 | Öffentliches Internet vs. nur LAN/VPN? | Nur LAN im MVP |
| E21 | Token-Speicherung nur auf der Uhr oder auch Phone/Cloud? | Uhr (+ Connect IQ Settings), kein Cloud |
| E22 | Logging/Diagnose bei Sync-Fehlern (TLS, -300, Port)? | Ja — klare Fehlertexte |

## F. Nicht-Ziele und Qualität

| # | Frage | Default |
| --- | --- | --- |
| F23 | Explizit **kein** Streaming, keine On-Demand-Suche der gesamten Library? | Ja, beides Non-Goal |
| F24 | Offline-Wiedergabe während Aktivität / BT-Kopfhörer / Lautsprecher? | BT-Kopfhörer; Lautsprecher egal |
| F25 | Wartungsaufwand: Einmal-MVP vs. langfristig gepflegte App? | MVP zuerst, Wartung offen |
| F26 | Lizenz/Open Source? | Offen (wie SubMusic-kompatibel prüfen) |

## G. Erfolgskriterien (MVP-Definition)

| # | Frage | Default |
| --- | --- | --- |
| G27 | MVP in einem Satz? | „Eine Plex-Playlist per Wi‑Fi auf die Fenix 8 syncen und offline abspielen.“ |
| G28 | Akzeptanzkriterien (Dauer, Fehlerrate, Größe, Setup)? | Setup &lt; 15 Min; Sync einer 50-Track-Playlist ohne manuellen Retry; Wiedergabe offline |

---

## Nutzung

1. Defaults in [antworten.md](antworten.md) prüfen und abweichen wo nötig.  
2. Jede Abweichung kurz begründen.  
3. Danach [06-naechste-schritte.md](06-naechste-schritte.md) abarbeiten (Entscheidung bestätigen → Spikes).
