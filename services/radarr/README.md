# Radarr

A fork of Sonarr to work with movies à la CouchPotato.

## Usage
```bash
docker-compose up -d
```

## Configuration
- **Port**: `7878`
- **URL**: [http://localhost:7878](http://localhost:7878)
- **Config**: `./config` (Local bind mount)
- **Downloads**: `media_downloads` (External volume)

## Network
Uses `network_mode: host`.
