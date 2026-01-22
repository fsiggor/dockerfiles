# Nginx Reverse Proxy

Serves as the gateway to all other services.

## Usage
```bash
docker-compose up -d
```

## Configuration
- **HTTP Port**: `80`
- **HTTPS Port**: `443`
- **Config**: `./nginx.conf` (Mapped to `/etc/nginx/conf.d/default.conf`)
- **SSL**: `./config/letsencrypt`

## Proxy Mappings
Proxies requests to `127.0.0.1` (localhost) for:
- `/sonarr` -> Port 8989
- `/radarr` -> Port 7878
- `/jackett` -> Port 9117
- `/transmission` -> Port 9091
- `/jellyfin` -> Port 8096
- `/pihole` -> Port 8053

## Network
Uses `network_mode: host`.
