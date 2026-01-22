# Services Directory

This directory contains the individual configurations for each service in the stack.

## Prerequisite
Ensure you have created the external downloads volume:
```bash
docker volume create media_downloads
```

## Services
- **[Nginx](nginx/README.md)**: Reverse Proxy
- **[Pi-hole](pihole/README.md)**: DNS Ad blocker
- **[Sonarr](sonarr/README.md)**: TV Shows
- **[Radarr](radarr/README.md)**: Movies
- **[Jellyfin](jellyfin/README.md)**: Media Server
- **[Jellyseerr](jellyseerr/README.md)**: Media Requests
- **[Jackett](jackett/README.md)**: Indexer Proxy
- **[Prowlarr](prowlarr/README.md)**: Indexer Manager
- **[Bazarr](bazarr/README.md)**: Subtitles
- **[Transmission](transmission/README.md)**: Torrent Client
- **[qBittorrent](qbittorrent/README.md)**: Torrent Client

## Running a Service
Navigate to the directory and start it:
```bash
cd sonarr
docker-compose up -d
```
