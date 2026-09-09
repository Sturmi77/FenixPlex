# MVP-Entwurf (Defaults festgeschrieben)

Dieses Dokument nagelt die Spec auf ein **sinnvolles Mindestmaß**, solange [antworten.md](antworten.md) nicht abweicht.

## Ein-Satz-MVP

> Eine Plex-Playlist per Wi‑Fi auf die Fenix 8 syncen und offline abspielen.

## Produktentscheidung

| Thema | Entscheidung |
| --- | --- |
| Produktpfad | **SubMusic evaluieren → bei Bedarf forken**; kein unnötiges Greenfield |
| Sync-Variante | **A** — Phone = Settings; Download Watch ↔ Wi‑Fi ↔ Plex |
| Gerät | Fenix 8 |
| Verteilung | Sideload zuerst |
| PC nötig für Sync? | Nein (nur ggf. für Proxy-/Plex-Setup einmalig) |

## In Scope (MVP)

- Connect IQ Audio Content Provider (bestehend SubMusic oder Fork)
- Plex-Auth per `X-Plex-Token` + Server-URL (HTTPS, Port 443)
- Playlist-Browse und Sync-Auswahl auf der Uhr
- Download im Wi‑Fi Sync Mode
- Plex-Transcode nach MP3 falls nötig
- Offline-Wiedergabe (Playlists, Shuffle)
- Edge: Reverse Proxy oder `*.plex.direct` mit gültigem Zertifikat
- Verständliche Fehlermeldungen bei TLS/Port/Auth

## Non-Goals (MVP)

- Live-Streaming
- On-Demand-Suche der gesamten Plex-Library
- Bulk-Transfer großer Bibliotheken per BLE
- Eigenes Phone-Companion mit Proxy (Variante B)
- Unterwegs-Sync (Hotspot/Remote/VPN)
- Multi-Server / Multi-User
- Podcast-Mode, Listen-Counts, Album Art als Muss
- Connect IQ Store Release
- Desktop/USB Express-Pfad als Primärprodukt

## Architektur (fest)

```text
[Garmin Connect / CIQ Settings] --BLE/Settings--> [Fenix 8 ACP App]
                                                      |
                                              Wi-Fi Sync Mode
                                                      |
                                              HTTPS :443
                                                      v
                                         [Proxy / plex.direct]
                                                      |
                                                      v
                                            [Plex Media Server]
```

## Techstack (fest)

Siehe [03-techstack.md](03-techstack.md): Monkey C / Connect IQ, Plex REST, Caddy/Nginx oder plex.direct, keine eigene Backend-Pflicht.

## Akzeptanzkriterien

1. Setup (Token + URL + Wi‑Fi) in unter 15 Minuten dokumentierbar und nachvollziehbar.
2. Eine Test-Playlist mit ca. 50 Tracks wird ohne manuellen Retry vollständig synchronisiert.
3. Nach Sync: Wiedergabe offline (Phone aus / BT-Kopfhörer).
4. Bei falschem Port/TLS erscheint eine erkennbare Fehlermeldung (kein stilles Scheitern).

## Speicher / Größenordnung

- Soft-Ziel MVP: eine Sync-Auswahl ≤ ~200 Tracks bzw. ~1–2 GB.
- Harte Caps und LRU können nach dem ersten erfolgreichen Sync nachgezogen werden.

## Lizenzhinweis

Bei Fork von SubMusic: Upstream-Lizenz und Attribution prüfen und einhalten.
