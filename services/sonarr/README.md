# Sonarr

Smart PVR for newsgroup and bittorrent users.

## Usage
```bash
docker-compose up -d
```

## Configuration
- **Port**: `8989`
- **URL**: [http://localhost:8989](http://localhost:8989)
- **Config**: `./config` (Local bind mount)
- **Downloads**: `media_downloads` (External volume)

## Network
Uses `network_mode: host`.
