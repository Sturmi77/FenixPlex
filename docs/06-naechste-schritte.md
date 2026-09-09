# Nächste Schritte und Spike-Liste

Voraussetzung: [antworten.md](antworten.md) und [05-mvp-entwurf.md](05-mvp-entwurf.md) sind akzeptiert (oder bewusst überschrieben).

## Phase 0 — Entscheidung bestätigen

1. SubMusic auf der Fenix 8 installieren und mit dem eigenen Plex testen.
2. Ergebnis festhalten:
   - **Passt** → Projekt = Doku + Setup-Guide; wenig/kein Code.
   - **Fast** → Fork; Issues priorisieren (Plex-UX, Ports, TLS, Fehlertexte).
   - **Ungeeignet** → Eigenbau auf Basis MonkeyMusic-Sample begründen.
3. Sync-Variante **A** und Non-Goals nicht ohne neuen Spec-Eintrag aufweichen.

## Phase 1 — Infrastruktur-Spikes (Hardware)

| Spike | Ziel | Pass-Kriterium |
| --- | --- | --- |
| S1 HTTPS:443 | Plex über 443 erreichbar (Proxy oder plex.direct) | `curl` von LAN lädt Track-Part |
| S2 TLS 1.2 | Cipher/Protokoll Watch-kompatibel | Watch-Sync startet ohne TLS-Fehler 0 / -300 |
| S3 Auth | Token in Settings; Library/Playlists lesbar | Playlist-Liste auf Uhr sichtbar |
| S4 Audio-Download | Eine Datei via SyncDelegate/`makeWebRequest` | Track offline abspielbar |
| S5 Transcode | FLAC/ALAC-Quelle → MP3 über Plex | Abspielbar; Größe plausibel |

Reihenfolge: S1 → S2 → S3 → S4 → S5.

## Phase 2 — Produkt-MVP

Nur nach bestandenen Spikes:

1. Setup-Anleitung (Wi‑Fi 2.4 GHz, Proxy, Token) in `docs/setup.md` (neu).
2. Sync-Flow: Playlist wählen → Sync → Progress → Offline-Playback.
3. Fehlerpfade: Auth, Netz, Speicher voll, unsupported format.
4. README mit Link auf Spec und bekannte Limits (Ports, TLS, kein Streaming).

## Phase 3 — Optional danach

- Album Art, Listen-Counts
- Hardcaps / Speicherverwaltung
- Connect IQ Store
- Phone Companion (nur Settings-UX, weiterhin Variante A)
- Unterwegs via VPN (explizite Spec-Erweiterung)

## Explizit später / nicht ohne Spec-Change

- Variante B (Phone-Proxy)
- Desktop Express Exporter als Hauptprodukt
- Multi-Server

## Definition of Done (Spec-Phase)

Diese Spec-Phase ist erledigt, wenn:

- [x] Constraints, Komponenten, Techstack dokumentiert
- [x] Fragenkatalog + Antwortvorlage mit Defaults
- [x] MVP + Non-Goals festgeschrieben
- [x] Nächste Schritte / Spikes dokumentiert
- [ ] Nutzer hat Defaults bestätigt oder Antworten überschrieben
- [ ] Phase-0 SubMusic-Eval auf echter Hardware gelaufen
