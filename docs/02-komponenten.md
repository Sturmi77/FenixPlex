# Komponenten

Bausteine einer sinnvollen FenixPlex-Lösung. Pflicht vs. optional hängt vom gewählten Produktpfad ab (siehe [05-mvp-entwurf.md](05-mvp-entwurf.md)).

## 1. Watch App (Connect IQ Audio Content Provider)

- **Sprache:** Monkey C  
- **Rolle:** Sync-Konfiguration, `SyncDelegate`, `ContentDelegate`, Offline-Playback, Cache-Verwaltung  
- **Referenzen:** [MonkeyMusic](https://github.com/garmin/connectiq-apps/tree/master/audio-provider), [SubMusic](https://github.com/memen45/SubMusic)  
- **Status im Default-MVP:** Pflicht

## 2. Plex-Anbindung

- Auth (`X-Plex-Token` / plex.tv)
- Libraries, Playlists, Tracks
- Part-Download oder Transcode-URL
- Optional: Server-Discovery  
- **Status im Default-MVP:** Pflicht (Token + feste Server-URL)

## 3. Erreichbarkeit / Edge

- HTTPS auf Port **443**, gültiges CA-Zertifikat
- ggf. Nginx/Caddy-Proxy vor Plex (`:32400`)
- optional Tailscale/VPN statt Public Remote Access  
- **Status im Default-MVP:** Pflicht (Proxy oder `*.plex.direct` auf 443)

## 4. Phone Companion (optional)

- Settings / OAuth, Server-URL / Token speichern
- Sync-Trigger, Statusanzeige
- Connect IQ Mobile SDK (Android/iOS) **oder** nur Connect IQ App Settings  
- **Status im Default-MVP:** Minimal — Connect IQ App Settings, kein eigenes Companion

## 5. Transcode-/Proxy-Service (optional)

- Normalisierung auf z. B. 128–192 kbps MP3
- Wenn die Uhr Plex nicht zuverlässig erreicht  
- **Status im Default-MVP:** Weglassen; Plex-Transcoding nutzen

## 6. Desktop-Pfad (optional / Alternative)

- Tool lädt von Plex → Playlist-Struktur für Garmin Express → USB-Sync
- MVP ohne CIQ möglich, UX schlechter  
- **Status im Default-MVP:** Nicht im Scope (nur als Fallback-Idee dokumentiert)

## Produktoptionen vor dem Bau

| Option | Wann wählen | Aufwand |
| --- | --- | --- |
| **SubMusic nutzen** | Features reichen aus | Minimal |
| **SubMusic forken / beitragen** | Plex-UX / Discovery / Fehlerbehandlung verbessern | Mittel |
| **Eigenes FenixPlex** | Volle Kontrolle, eigene Marke/Store | Hoch |
| **Hybrid Desktop** | Schneller PoC ohne Store-App | Niedrig–mittel |

Default-Entscheidung: siehe [05-mvp-entwurf.md](05-mvp-entwurf.md) (CIQ-first, SubMusic als Referenz/Fork-Kandidat).
