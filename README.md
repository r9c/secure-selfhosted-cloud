# Secure Self-Hosted Cloud

This is documentation for the design and deployment of a private cloud environment on **Proxmox VE** using an Ubuntu VM with **Docker + Docker Compose**.  

## Plans
- Self-host secure and privacy-focused services
- Learn Linux administration and virtualization
- Demonstrate infrastructure as code and documentation practices

## Services
- **Vaultwarden** – self-hosted password manager  
- **Nextcloud** – private cloud file storage  
- **Uptime-Kuma** – service monitoring  
- **Nginx Proxy Manager** – reverse proxy & SSL termination  

## Documentation
- [Build Log](docs/LOG.md) – step-by-step progress notes  
- [Architecture](docs/ARCHITECTURE.md) – diagrams and system design  

## Stack
- Proxmox VE 9.0 (hypervisor)  
- Ubuntu Server 24.04 (VM)  
- Docker + Docker Compose  
- Reverse Proxy, TLS, isolated service containers  
