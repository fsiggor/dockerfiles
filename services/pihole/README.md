# Pi-hole

Network-wide Ad Blocking.

## Usage
```bash
docker-compose up -d
```

## Configuration
- **DNS Port**: `53` (TCP/UDP)
- **Web Interface Port**: `8053` (Moved from 80 to avoid conflict with Nginx)
- **URL**: [http://localhost:8053/admin](http://localhost:8053/admin)
- **Config**: `./etc-pihole` (Local bind mount)
- **Password**: Set via `.env` or environment variable `WEBPASSWORD` (default: see compose file)

## Network
Uses `network_mode: host`.
