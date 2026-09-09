# Plattform-Constraints (Garmin Fenix 8 + Plex)

## Kurzfazit

Auf einer Fenix 8 ist Musik **nur offline** nutzbar (kein Live-Streaming). Der offizielle Weg für Drittanbieter ist eine **Connect IQ Audio Content Provider App**: Auswahl auf der Uhr, Download über **Wi‑Fi Sync Mode**, Ablage in verschlüsseltem Cache, Wiedergabe über den nativen Media Player. Das Handy dient typischerweise als **Auth-/Settings-Brücke** (Garmin Connect / Connect IQ Mobile), nicht als Bulk-Transferkanal für ganze Bibliotheken.

Referenz-Prior-Art: [SubMusic](https://github.com/memen45/SubMusic) (Connect IQ Store) mit Plex-Support inkl. Transcoding.

## Datenfluss (Standardpfad)

```text
Phone (Garmin Connect / Settings)
        |  OAuth, Token, kurze API-Calls (BLE)
        v
Fenix 8 CIQ Audio Content Provider
        |  Wi-Fi Sync Mode + makeWebRequest
        v
Plex Media Server (HTTPS :443)
        |  Audio (MP3 / M4A)
        v
Encrypted Media Cache  -->  Native Media Player
```

## Constraint-Tabelle

| Constraint | Bedeutung für FenixPlex |
| --- | --- |
| Kein Streaming | Tracks müssen vorab heruntergeladen werden |
| Wi‑Fi Sync Mode | Große Downloads nur in Sync-UI; Wi‑Fi ist nicht dauerhaft an |
| BLE über Phone | Normale `makeWebRequest` laufen oft über Garmin Connect (Phone); für Musik-Bulk ungeeignet |
| Formate | CIQ: MP3, M4A, WAV, ADTS; Express/Personal Music: vor allem MP3/M4A |
| Ports | Garmin-URLs praktisch nur **80/443** — Plex `:32400` braucht Reverse Proxy oder `*.plex.direct` / Remote Access |
| TLS | Watch-Wi‑Fi oft nur TLS 1.2; keine self-signed Certs |
| Storage | Fenix 8 ca. **32 GB** (geteilt mit System/Apps) |
| Sandbox | Provider-Content ist verschlüsselt; kein freier USB-Zugriff auf CIQ-Cache |

## Alternativpfad: Personal Music (kein CIQ Provider)

**Garmin Express / USB „My Music“** — Dateien vom PC auf die Uhr. Das ist ein anderes Produkt (Desktop-Exporter), kein Spotify-ähnliches Sync-Erlebnis. Nützlich als Proof-of-Concept oder Fallback, nicht als Primär-UX.

## Sync über Mobiltelefon — realistische Varianten

| Variante | Beschreibung | Bewertung |
| --- | --- | --- |
| **A (Standard)** | Phone = Login/Settings; Download = Watch ↔ Wi‑Fi ↔ Plex | Empfohlen; wie Spotify/Deezer auf Garmin |
| **B (Phone-Proxy)** | Companion lädt von Plex und stellt HTTP bereit; Watch lädt im Sync Mode vom Phone | Fragil (Netzwerk-Erreichbarkeit Phone↔Watch) |
| **C (BLE-Metadaten)** | Phone steuert Playlist-Auswahl; Bytes weiter über Wi‑Fi | Sinnvolle Ergänzung zu A |
| **D (kein CIQ)** | Phone/PC exportiert Dateien; Transfer per USB/Express | Schneller MVP, schlechtere UX |

Große Bibliotheken per BLE zu pushen ist **kein** valider Primärpfad.

## Quellen / Referenzen

- [Creating Music Apps in Connect IQ 3](https://www.garmin.com/en-US/blog/developer/creating-music-apps-3x/)
- [How do I create an Audio Content Provider?](https://developer.garmin.com/connect-iq/connect-iq-faq/how-do-i-create-an-audio-content-provider/)
- [Toybox.Media](https://developer.garmin.com/connect-iq/api-docs/Toybox/Media.html)
- [Garmin MonkeyMusic sample](https://github.com/garmin/connectiq-apps/tree/master/audio-provider)
- [SubMusic](https://github.com/memen45/SubMusic)
- [Plex Media Server API](https://developer.plex.tv/pms/)
