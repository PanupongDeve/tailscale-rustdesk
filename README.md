## 🚀 Setup Tailscale and Rustdesk with Docker Compose

This project provides a simple way to run Tailscale and Rustdesk server components using Docker Compose.

### 🛠️ Prerequisites
- [Docker](https://www.docker.com/get-started) and [Docker Compose](https://docs.docker.com/compose/) installed
- A `.env` file with your Tailscale authentication details (see Tailscale docs)

### 📦 Services
- **tailscale**: Provides secure networking for your containers and devices.
- **rustdesk-hbbs**: Rustdesk relay server (for NAT traversal and relaying connections).
- **rustdesk-hbbr**: Rustdesk rendezvous server (for peer discovery and connection setup).

### ▶️ Usage
1. Clone this repository and navigate to the project directory.
2. Create a `.env` file with your Tailscale environment variables (see [Tailscale docs](https://tailscale.com/kb/1085/docker/)).
3. Start all services:
   ```powershell
   docker compose up -d
   ```
4. (Optional) Check logs for each service:
   ```powershell
   docker compose logs tailscale
   docker compose logs rustdesk-hbbs
   docker compose logs rustdesk-hbbr
   ```

### 🔌 Ports
- Rustdesk HBBS: 21115, 21116, 21118
- Rustdesk HBBR: 21117

### ℹ️ Notes
- Tailscale runs in host network mode and requires elevated privileges (NET_ADMIN, SYS_MODULE).
- Data for Tailscale is persisted in the `./tailscale` directory. If you want to keep the directory tracked by git but ignore its contents, a `.gitkeep` file is included and `.gitignore` is configured accordingly.

---
For more information, see the official documentation:
- [Tailscale Docker Guide](https://tailscale.com/kb/1085/docker/)
- [Rustdesk Server Setup](https://rustdesk.com/docs/en/self-host/)
