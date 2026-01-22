# Jackett

API Support for your favorite torrent trackers.

## Usage
```bash
docker-compose up -d
```

## Configuration
- **Port**: `9117`
- **URL**: [http://localhost:9117](http://localhost:9117)
- **Config**: `./config` (Local bind mount)
- **Downloads**: `media_downloads` (External volume)

## Network
Uses `network_mode: host`.
