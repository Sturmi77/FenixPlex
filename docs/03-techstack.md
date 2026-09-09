# Techstack

## Empfohlene Richtung (Default-MVP)

Connect-IQ-first wie SubMusic: die Uhr sync’t per Wi‑Fi direkt (oder über einen kleinen lokalen HTTPS-Proxy) gegen Plex; das Phone dient nur dem Setup.

| Schicht | Stack | Bemerkung |
| --- | --- | --- |
| Watch | Connect IQ SDK, Monkey C, `AudioContentProviderApp`, `Media.SyncDelegate` | Kernprodukt |
| Phone | Connect IQ App Settings (oder später Mobile SDK Kotlin/Swift) | Auth/Settings |
| Plex | PMS REST + `X-Plex-Token`; Transcode-Query-Params bei Bedarf | Bibliothek + Download |
| Edge | Caddy/Nginx auf 443 → Plex; Let’s Encrypt | Port-/TLS-Constraints |
| Optional Backend | Node / Go / Python nur bei Proxy/Transcode/Queue | Nicht im Default-MVP |
| Dev/Test | CIQ Simulator + echte Fenix 8 + lokaler PMS | Hardware-Spike Pflicht |
| Alternative MVP | Python/Go Desktop-CLI → Dateien + M3U → Garmin Express | Nur wenn CIQ vertagt wird |

## Sync-Variante (Default)

**Variante A:** Phone = Login/Settings; Download = Watch ↔ Wi‑Fi ↔ Plex.

## Dev-Tooling (bei Eigenbau / Fork)

- [Connect IQ SDK](https://developer.garmin.com/connect-iq/) (aktuell installieren)
- Visual Studio Code + Monkey C Extension (oder Garmin-empfohlenes Setup)
- Garmin Express / USB für Sideload und Logs
- Plex Media Server (lokal) mit kleiner Test-Musikbibliothek
- Optional: `curl`/Skript für Plex-Playlist- und Part-URL-Checks vor dem Watch-Spike

## Nicht empfohlen als Primärstack

- Reines BLE-File-Transfer vom Phone zur Uhr für ganze Bibliotheken
- Self-signed HTTPS gegen Watch-Wi‑Fi
- Direkte Plex-URLs mit Port `:32400` ohne Proxy/`plex.direct`
- Live-Streaming-Architektur (von der Plattform nicht unterstützt)
