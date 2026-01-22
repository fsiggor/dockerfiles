# Agentic Coding Guidelines

This repository hosts a Docker-based media stack configuration, deploying services like Jellyfin, Radarr, Sonarr, and others via Docker Compose, with Nginx as a reverse proxy.

## 1. Build, Lint, and Test Commands

Since this is an infrastructure-as-code repository, "building" implies validating configurations and deploying containers.

### Validation & Linting
- **Validate Docker Compose:** Ensure the YAML is valid and configurations are correct.
  ```bash
  docker-compose config
  ```
- **Validate Nginx Config:** (Requires running container)
  ```bash
  docker exec -t nginx nginx -t
  ```

### Deployment (Build/Run)
- **Stack 1 (Basic Media):** Jellyfin, Radarr, Sonarr, Jackett, Transmission.
  ```bash
  docker-compose --profile stack-1 up -d
  ```
- **Stack 2 (Advanced + VPN):** Jellyfin, Radarr, Sonarr, Prowlarr, qBitTorrent, VPN.
  ```bash
  # Requires environment variables for VPN credentials
  VPN_SERVICE_PROVIDER=nordvpn \
  OPENVPN_USER=user \
  OPENVPN_PASSWORD=pass \
  docker-compose --profile stack-2 up -d
  ```
- **Nginx Proxy:**
  ```bash
  docker-compose -f docker-compose-nginx.yml up -d
  ```

### Testing & Verification
There are no automated unit tests. Verification is manual or operational:
- **Check Status:**
  ```bash
  docker ps
  ```
- **Service Health:** Verify specific services are reachable via curl (e.g., `curl -I localhost:8096`).
- **Logs:** Check logs for errors.
  ```bash
  docker-compose logs -f [service_name]
  ```

## 2. Code Style & Conventions

### Docker Compose (`docker-compose.yml`)
- **Indentation:** Use **2 spaces** for indentation.
- **Naming:** Service names must be lowercase and match the application name (e.g., `radarr`, `sonarr`).
- **Quotes:** Use double quotes `"` for string values in keys like `restart: "unless-stopped"`.
- **Environment:**
  - Common variables like `PUID`, `PGID`, and `TZ` are currently hardcoded (e.g., `1000`, `UTC`).
  - When adding new services, preserve this pattern unless refactoring to use a `.env` file.
- **Volumes:** Map configuration to named volumes (e.g., `radarr:/config`) and data to host paths (e.g., `downloads:/downloads`).
- **Network:** All services must join the external `mynetwork`.

### Nginx Configuration (`nginx.config`)
- **Indentation:** Use **4 spaces** for indentation within blocks.
- **Structure:**
  - Use comment banners to demarcate proxy sections: `###SERVICE-PROXY###`.
  - Place `location` blocks inside the main `server` block.
- **Proxy Headers:** consistently set standard headers (`Host`, `X-Real-IP`, `X-Forwarded-For`, `Upgrade`, `Connection`).
- **Paths:** Be mindful of trailing slashes in `proxy_pass`.

### General Guidelines
- **Paths:** Always use absolute paths in documentation or scripts if referring to host directories.
- **Refactoring:**
  - If modifying `docker-compose.yml`, run `docker-compose config` to ensure validity before committing.
  - If refactoring to use `.env` files, document the required variables clearly in `README.md`.
- **Safety:**
  - Do not commit real credentials (VPN passwords, API keys) to the repo. Use placeholders or environment variables.
  - When editing `nginx.config`, ensure syntax is valid to prevent the reverse proxy from failing on reload.

## 3. Error Handling
- **Container Restarts:** Use `restart: "unless-stopped"` for all services to handle crash recovery.
- **Nginx Fallbacks:** Ensure `50x.html` is configured for server errors.
