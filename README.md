# FenixPlex — Spec-Übersicht

Musik von einem **Plex Media Server** auf eine **Garmin Fenix 8** synchronisieren und **offline** verfügbar machen.

## Status

Spec-Eingrenzung abgeschlossen (Defaults angewendet). Nächster Arbeitsschritt: SubMusic auf Hardware evaluieren und Antworten ggf. anpassen — siehe [docs/06-naechste-schritte.md](docs/06-naechste-schritte.md).

## MVP (ein Satz)

Eine Plex-Playlist per Wi‑Fi auf die Fenix 8 syncen und offline abspielen.

## Dokumente

| Doc | Inhalt |
| --- | --- |
| [docs/01-plattform-constraints.md](docs/01-plattform-constraints.md) | Garmin/Plex-Constraints, Sync-Varianten A–D |
| [docs/02-komponenten.md](docs/02-komponenten.md) | Bausteine und Produktoptionen |
| [docs/03-techstack.md](docs/03-techstack.md) | Empfohlener Stack |
| [docs/04-fragenkatalog.md](docs/04-fragenkatalog.md) | Priorisierter Fragenkatalog |
| [docs/antworten.md](docs/antworten.md) | Ausfüllbare Antworten (Defaults vorausgefüllt) |
| [docs/05-mvp-entwurf.md](docs/05-mvp-entwurf.md) | Festgeschriebener MVP + Non-Goals |
| [docs/06-naechste-schritte.md](docs/06-naechste-schritte.md) | Eval, Spikes, Phasen |

## Architektur (kurz)

Phone nur für Settings; Download über Watch-Wi‑Fi zu Plex (HTTPS :443); verschlüsselter Offline-Cache; nativer Media Player.

## Wichtige Constraints

- Kein Streaming auf der Uhr
- Große Downloads nur im Wi‑Fi Sync Mode
- Praktisch nur Ports 80/443; TLS mit CA-Zertifikat (kein self-signed)
- Formate: vor allem MP3/M4A
- Prior Art: [SubMusic](https://github.com/memen45/SubMusic) (Plex bereits unterstützt)

## Mitwirken an der Spec

1. [docs/antworten.md](docs/antworten.md) öffnen und Defaults überschreiben, wo nötig.
2. Abweichungen kurz notieren.
3. Danach Phase 0 in [docs/06-naechste-schritte.md](docs/06-naechste-schritte.md).
