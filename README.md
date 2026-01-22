# Docker Media Stack

A modular, Docker-based media stack using **Host Networking**.

## Structure
The repository is organized into individual services in the `services/` directory.

- **[services/](services/)**: Contains all service configurations.
- **[services/backups/](services/backups/)**: Legacy configuration files.

## Prerequisites
1.  **Docker & Docker Compose** installed.
2.  **External Volume**: You must create the shared downloads volume before starting any service.
    ```bash
    docker volume create media_downloads
    ```

## Getting Started
1.  Navigate to a service directory (e.g., `services/sonarr`).
2.  Copy `.env.example` to `.env` (if applicable).
3.  Run the service:
    ```bash
    docker-compose up -d
    ```

For detailed instructions, see **[services/README.md](services/README.md)**.

## Networking
All services run in `network_mode: "host"`.
- **On Linux**: Services share the host IP.
- **On macOS/Windows**: Services share the Docker VM IP but are accessible via `localhost`.
- **Internal Communication**: Services talk to each other via `127.0.0.1` (localhost).

## Services Overview
| Service | Port | URL | Description |
| :--- | :--- | :--- | :--- |
| **Nginx** | 80/443 | http://localhost | Reverse Proxy |
| **Pi-hole** | 53/8053 | http://localhost:8053/admin | DNS Ad Blocker (Web Port moved to 8053) |
| **Sonarr** | 8989 | http://localhost:8989 | TV Shows |
| **Radarr** | 7878 | http://localhost:7878 | Movies |
| **Jellyfin** | 8096 | http://localhost:8096 | Media Server |
| **Transmission** | 9091 | http://localhost:9091 | Torrent Client |
| **qBittorrent** | 5080 | http://localhost:5080 | Torrent Client |
| **Jackett** | 9117 | http://localhost:9117 | Indexer Proxy |
| **Prowlarr** | 9696 | http://localhost:9696 | Indexer Manager |
| **Bazarr** | 6767 | http://localhost:6767 | Subtitles |
| **Jellyseerr** | 5055 | http://localhost:5055 | Media Requests |

## Migration Notes
- **Profiles Removed**: Services are no longer grouped by profiles (`stack-1`, `stack-2`). You can run any combination of services.
- **Network Removed**: The external `mynetwork` bridge is replaced by Host Networking.
- **Volumes**: `downloads` is now an external volume `media_downloads` to allow sharing across separate compose files.
