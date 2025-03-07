# Configuring Docker to Start on Boot

## Introduction
Setting Docker to automatically start on system boot so the containers and services are up and running after a system restart. This is crucial requirement in production environments.

---

## Steps to Enable Docker to Start on Boot

### 1. Check Docker Service Status
```bash
sudo systemctl status docker
```

### 2. Enable Docker Service
```bash
sudo systemctl enable docker
```

This command will configure Docker to automatically start whenever the system reboots.

### 3. Start Docker Service (Optional - if not already running)
```bash
sudo systemctl start docker
```

---

## Verifying Configuration
After a reboot, check if Docker is running:
```bash
sudo systemctl status docker
```

If needed, you can disable Docker auto-start at boot with:
```bash
sudo systemctl disable docker
```

---

## Additional Notes
- Works on **systemd-based** systems (like Ubuntu, CentOS, Debian, etc.).
- For non-systemd systems (like older distros), you might need to modify `/etc/rc.local` or other init configurations.

---

## Useful Commands Summary

| Command | Description |
|---|---|
| `sudo systemctl status docker` | Check Docker service status |
| `sudo systemctl enable docker` | Enable auto-start on boot |
| `sudo systemctl start docker` | Start Docker service |
| `sudo systemctl disable docker` | Disable auto-start on boot |

---
