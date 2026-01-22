# Pi-hole

Network-wide Ad Blocking.

## Prerequisites
Before starting, copy the example environment file and set your password:
```bash
cp .env.example .env
# Edit .env to set WEBPASSWORD
```

## Usage
Start the service:
```bash
docker-compose up -d
```

## Configuration
| Setting | Value | Notes |
| :--- | :--- | :--- |
| **DNS Port** | `53` (TCP/UDP) | Standard DNS port. |
| **Web Port** | `8053` | **Changed from 80** to avoid conflict with Nginx. |
| **URL** | [http://localhost:8053/admin](http://localhost:8053/admin) | Access the admin dashboard here. |
| **Data/Config** | `./etc-pihole` | Local bind mount. **Note:** This directory is ignored by git. |
| **Password** | `WEBPASSWORD` | Defined in `.env`. |

## Network
Uses `network_mode: host`.
- The container shares the host's networking stack.
- It will bind directly to port 53 on the host.
