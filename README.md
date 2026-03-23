# spoke-plex

Spoke module for [Plex](https://www.plex.tv/) media server with [Tautulli](https://tautulli.com/) monitoring.

## Services

| Service  | Description            | Port  | Network |
|----------|------------------------|-------|---------|
| plex     | Plex media server      | 32400 | troxy   |
| tautulli | Plex statistics/monitoring | 8181 | troxy |

## Prerequisites

- Spoke hub deployed with `troxy` network
- Traefik available as a hub service
- GPU passthrough (`/dev/dri/`) for hardware transcoding

## Quick Start

```bash
cp .env.example .env
# Edit .env — set media paths for your system
docker compose up -d
```

## Module Environment Variables

| Variable        | Default                              | Description                 |
|-----------------|--------------------------------------|-----------------------------|
| `PLEX_IMAGE`    | `lscr.io/linuxserver/plex:1.43.0`    | Plex container image        |
| `TAUTULLI_IMAGE`| `ghcr.io/tautulli/tautulli:v2.16.1`  | Tautulli container image    |
| `PLEX_IP`       | `192.168.35.83`                      | Plex static IP              |
| `PLEX_PORT`     | `32400`                              | Plex server port            |
| `PLEX_URL`      | `https://plex.${DOMAIN}`             | Plex advertise URL          |
| `TAUTULLI_IP`   | `192.168.35.87`                      | Tautulli static IP          |
| `TAUTULLI_PORT` | `8941`                               | Tautulli web port           |
| `MEDIA_DIR`     | `/mnt/media`                         | Base media directory        |
| `MOVIES_DIR`    | `${MEDIA_DIR}/movies`                | Movies library path         |
| `TV_DIR`        | `${MEDIA_DIR}/tv`                    | TV shows library path       |
| `MUSIC_DIR`     | `${MEDIA_DIR}/music`                 | Music library path          |

## References

- [Plex Docker (LinuxServer)](https://docs.linuxserver.io/images/docker-plex)
- [Tautulli](https://tautulli.com/)
