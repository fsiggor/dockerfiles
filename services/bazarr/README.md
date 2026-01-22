# Bazarr

It manages and downloads subtitles based on your requirements.

## Usage
```bash
docker-compose up -d
```

## Configuration
- **Port**: `6767`
- **URL**: [http://localhost:6767](http://localhost:6767)
- **Config**: `./config` (Local bind mount)
- **Downloads**: `media_downloads` (External volume)

## Network
Uses `network_mode: host`.
