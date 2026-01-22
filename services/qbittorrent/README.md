# qBittorrent

BitTorrent client.

## Usage
```bash
docker-compose up -d
```

## Configuration
- **WebUI Port**: `5080`
- **Torrent Port**: `6881`
- **URL**: [http://localhost:5080](http://localhost:5080)
- **Config**: `./config` (Local bind mount)
- **Downloads**: `media_downloads` (External volume)

## Network
Uses `network_mode: host`.
