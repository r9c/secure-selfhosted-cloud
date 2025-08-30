# Secure Self-Hosted Cloud — Build Log

This document records the progress of building a self-hosted cloud and cybersecurity lab environment using Proxmox, Ubuntu, and Docker.

---

## Base Server Setup
- Built a dedicated server for this project using parts from multiple old pcs:
  - Intel Core i7-8700 CPU  
  - 32GB DDR4 RAM
  - 238GB SSD (system disk)
  - 931GB HDD (data/backups)
    (more upgrades to come)
- Installed **Proxmox VE 9.0** directly on bare metal to act as the hypervisor.  
- Connected the server to the network using a **TP-Link Wi-Fi extender in bridge mode**

## Proxmox Configuration
- Dedicated the 238GB SSD for Proxmox and VM storage.  
- Reserved the 931GB HDD for additional storage and backups.  
- Configured the default bridge `vmbr0` to connect VMs directly to the LAN.  
- Confirmed Proxmox can run fully **headless**

  ## First VM — Ubuntu Cloud Host
- Uploaded **Ubuntu Server 24.04 LTS ISO** into Proxmox.  
- Created VM `cloud-ubuntu` with:
- 4 vCPUs, 8GB RAM, 100GB disk  
- Bridged network via `vmbr0`  
- Installed Ubuntu Server with OpenSSH enabled.  
- Applied initial hardening:
- Updated and patched system with `apt update && apt upgrade`.  
- Installed and configured **UFW firewall**, allowing only ports `22, 80, 443`.  
