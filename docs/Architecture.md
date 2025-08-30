# Secure Self-Hosted Cloud — Architecture

This document shows the current and planned architecture of the self hosted cloud environment.

---

## Current Setup
- **Hardware:** Custom built server (Intel i7-8700, 32GB DDR4, 238GB SSD, 931GB HDD) *Initial build — further upgrades planned.*
- **Hypervisor:** Proxmox VE 9.0 on bare metal.
- **Networking:** Ethernet via TP-Link Wi-Fi extender in bridge mode (once again, temporary). *Initial setup — will migrate to complete wired connection when possible.*
- **VMs (so far):**
  - `cloud-ubuntu` (Ubuntu Server 24.04) with UFW firewall enabled.

---

## Planned Architecture
### Core Cloud Services (Docker on `cloud-ubuntu`)
- **Reverse Proxy:** Nginx Proxy Manager (entry point for all services).
- **Vaultwarden:** Self-hosted password manager (Bitwarden-compatible).
- **Nextcloud:** Private file storage and sync platform.
- **Uptime-Kuma:** Monitoring and status dashboard.

### System Features
- **Backups:** Scheduled Proxmox backups to the 931GB HDD.
- **TLS/HTTPS:** Certificates managed by Nginx Proxy Manager (LAN certs first, Cloudflare Tunnel later).
- **Monitoring:** Service uptime tracking via Uptime-Kuma.
- **Scalability:** Designed so additional services (media server, wiki, automation tools) can be added easily.

---

## Diagram (Planned)
```mermaid
graph TD
    subgraph Proxmox Node [Proxmox Server (i7-8700, 32GB RAM)]
        subgraph CloudHost [Ubuntu VM: cloud-ubuntu]
            NPM[Nginx Proxy Manager]
            Vault[Vaultwarden]
            Next[Nextcloud]
            Kuma[Uptime-Kuma]
        end
    end

    NPM --> Vault
    NPM --> Next
    NPM --> Kuma
