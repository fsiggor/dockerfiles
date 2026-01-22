# Jellyfin

The Free Software Media System.

## Usage
```bash
docker-compose up -d
```

## Configuration
- **Port**: `8096`
- **URL**: [http://localhost:8096](http://localhost:8096)
- **Config**: `./config` (Local bind mount)
- **Media**: `media_downloads` mapped to `/data`

## Network
Uses `network_mode: host`.
