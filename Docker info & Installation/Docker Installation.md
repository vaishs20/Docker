# Docker Installation Guide

## Ubuntu/Debian Installation

### Update Package Index
```bash
sudo apt-get update
```

### Install Required Packages
```bash
sudo apt-get install ca-certificates curl gnupg lsb-release
```

### Add Docker's Official GPG Key
```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```

### Set Up Repository
```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

### Install Docker Engine
```bash
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

### Verify Installation
```bash
sudo docker run hello-world
```

### Add User to Docker Group (to run Docker without sudo)
```bash
sudo usermod -aG docker $USER
```
*Note: Log out and back in for this to take effect*

## Windows Installation

### System Requirements
- Windows 10 64-bit: Pro, Enterprise, or Education (Build 18362 or later)
- Windows 11 64-bit
- Ensure Hyper-V and Windows Subsystem for Linux 2 (WSL2) are enabled

### Installation Steps

1. Download Docker Desktop for Windows
   - Visit [Docker Desktop for Windows](https://www.docker.com/products/docker-desktop)
   - Click "Download for Windows"

2. Run the Installer
   - Double-click on the downloaded "Docker Desktop Installer.exe"
   - Follow the installation wizard prompts
   - Select "Use WSL 2 instead of Hyper-V" when prompted (recommended)

3. Complete Installation
   - Click "Finish" when the installation completes
   - Docker Desktop will start automatically

4. Verify the Installation
   - Open Command Prompt or PowerShell
   ```cmd
   docker --version
   docker run hello-world
   ```

### Troubleshooting Windows Installation

If WSL2 is not enabled:
```cmd
# Enable WSL feature
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart

# Enable Virtual Machine Platform feature
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart

# Restart your computer

# Download and install the WSL2 Linux kernel update package
# https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi

# Set WSL2 as default
wsl --set-default-version 2
```
