# 📦 Plex + Pi-hole Ansible Deployment

This is a fully automated Ansible project to set up a self-hosted media and DNS filtering server. It installs **Docker**, then deploys **Plex Media Server** and **Pi-hole** as Docker containers. Ideal for home lab enthusiasts looking to manage media and network filtering with ease and repeatability.

---

## 🧰 Features

- ✅ Automated Docker installation via Ansible
- 🎥 Deploys Plex Media Server for local or remote media streaming
- 🚫 Deploys Pi-hole for network-wide ad blocking and DNS filtering
- 🔄 Supports reproducible deployments using inventories and role-based tasks
- 📁 Plex backup folder structure supported for migrating existing media libraries

---

## 📂 Project Structure

```
PlexPihole/
├── site.yml                   # Main playbook
├── group_vars/
│   └── all.yml                # Global variables
├── inventories/
│   └── production/hosts       # Inventory file
└── roles/
    ├── docker/                # Role: installs Docker
    ├── plex/                  # Role: deploys Plex via Docker
    │   └── files/docker-compose.yml
    └── pihole/                # Role: deploys Pi-hole via Docker
```

---

## 🚀 Getting Started

1. **Update Inventory File**  
   Edit `inventories/production/hosts` and set your server IP or hostname.

2. **Configure Variables**  
   Update `group_vars/all.yml` to set your desired Docker image tags, ports, volumes, etc.

3. **Run the Playbook**

   ```bash
   ansible-playbook -i inventories/production site.yml
   ```

4. **Access Services**
   - Plex: http://<your-server-ip>:32400
   - Pi-hole Admin: http://<your-server-ip>:8080/admin

---

## ♻️ Restoring Plex Backup

If you have an old Plex library, you can mount it under the `config` volume used in `roles/plex/files/docker-compose.yml`. Make sure the folder structure matches your previous setup and correct permissions are in place.

---

## 📄 License

This project is licensed under the [MIT License](https://opensource.org/licenses/MIT).

```
MIT License

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the “Software”), to deal
in the Software without restriction...
```
