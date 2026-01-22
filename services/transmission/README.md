# Transmission

Fast, easy, and free BitTorrent client.

## Usage
```bash
docker-compose up -d
```

## Configuration
- **WebUI Port**: `9091`
- **Torrent Port**: `51413`
- **URL**: [http://localhost:9091](http://localhost:9091)
- **Config**: `./config` (Local bind mount)
- **Downloads**: `media_downloads` (External volume)

## Network
Uses `network_mode: host`.
