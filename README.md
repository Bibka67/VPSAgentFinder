<div align="center">
# VPSAgentFinder

Terminal UI utility for auditing and cleaning VPS/VDS management agents, cloud-init components, SSH keys, cron jobs, and system services.

![GitHub go.mod Go version](https://img.shields.io/github/go-mod/go-version/Bibka67/VPSAgentFinder?style=for-the-badge&logo=go)
![GitHub Repo stars](https://img.shields.io/github/stars/Bibka67/VPSAgentFinder?style=for-the-badge&logo=github)
![GitHub forks](https://img.shields.io/github/forks/Bibka67/VPSAgentFinder?style=for-the-badge&logo=github)
![GitHub issues](https://img.shields.io/github/issues/Bibka67/VPSAgentFinder?style=for-the-badge&logo=github)
![GitHub License](https://img.shields.io/github/license/Bibka67/VPSAgentFinder?style=for-the-badge)

![Linux](https://img.shields.io/badge/Linux-Supported-FCC624?style=for-the-badge&logo=linux&logoColor=black)
![TUI](https://img.shields.io/badge/Interface-Terminal_UI-9146FF?style=for-the-badge)
![Bubble Tea](https://img.shields.io/badge/BubbleTea-TUI_Framework-FF69B4?style=for-the-badge)
![Security Audit](https://img.shields.io/badge/Security-Audit_Tool-red?style=for-the-badge)
![Open Source](https://img.shields.io/badge/Open_Source-Yes-success?style=for-the-badge)
</div>


## Features

* 🔍 Automatic system scan
* 📦 Detection of VPS management agents
* 🔑 SSH key discovery
* ⏰ Cron job inspection
* ⚙️ Systemd timer analysis
* ☁️ Cloud-init detection
* 🌐 Network service overview
* ✅ Interactive selection of items to remove
* 📝 Detailed action logs
* 🔄 Rescan after cleanup
* 🛡 Dry-run mode
* 📊 JSON report export

## Supported Components

### Guest Agents

* qemu-guest-agent
* google-guest-agent
* waagent
* amazon-ssm-agent

### Cloud Services

* cloud-init
* cloud-config
* cloud-final
* cloud-init-local

### Scheduled Tasks

* User crontabs
* `/etc/crontab`
* `/etc/cron.d/*`
* `/etc/cron.daily/*`
* `/etc/cron.weekly/*`

### SSH Configuration

* authorized_keys files
* root SSH keys
* user SSH keys

### Systemd

* Services
* Timers
* Startup entries

## Installation

### Quick Install

```bash
git clone https://github.com/Bibka67/VPSAgentFinder.git
cd VPSAgentFinder

go mod tidy
go build -o VPSAgentFinder ./cmd/vpsagentfinder

sudo ./VPSAgentFinder
```

### One-Line Build

```bash
git clone https://github.com/Bibka67/VPSAgentFinder.git && \
cd VPSAgentFinder && \
go mod tidy && \
go build -o VPSAgentFinder ./cmd/vpsagentfinder
```

## Requirements

* Go 1.24+
* Linux
* Root privileges for cleanup operations

Check Go version:

```bash
go version
```

## Usage

Run scanner:

```bash
sudo ./VPSAgentFinder
```

Navigation:

| Key   | Action          |
| ----- | --------------- |
| ↑ ↓   | Move            |
| Space | Select item     |
| Enter | Expand/Collapse |
| Tab   | Switch focus    |
| R     | Rescan          |
| C     | Clean selected  |
| Q     | Quit            |

## Example Interface

```text
 VPSAgentFinder

 [x] Guest Agents
     [x] qemu-guest-agent

 [ ] SSH Keys
     [x] /root/.ssh/authorized_keys

 [x] Cron Jobs
     [x] /etc/cron.d/provider

 ---------------------------------

 Found: 4
 Selected: 3

 [ Rescan ] [ Clean Selected ]
```

## Dry Run

Preview actions without making changes:

```bash
sudo ./VPSAgentFinder --dry-run
```

## Export Report

```bash
sudo ./VPSAgentFinder --export report.json
```

Example:

```json
{
  "agents": [
    "qemu-guest-agent"
  ],
  "cron_jobs": [
    "/etc/cron.d/provider"
  ],
  "ssh_keys": [
    "/root/.ssh/authorized_keys"
  ]
}
```

## Build From Source

```bash
git clone https://github.com/Bibka67/VPSAgentFinder.git
cd VPSAgentFinder

go mod download
go build -ldflags="-s -w" -o VPSAgentFinder ./cmd/vpsagentfinder
```

## Project Structure

```text
cmd/
└── vpsagentfinder/

internal/
├── scanner/
├── cleaner/
├── ui/
└── models/

docs/
```

## Disclaimer

VPSAgentFinder is an auditing and system management utility intended for systems you own or administer. Always review detected items before removal. Removing required services may affect VPS provider functionality.

## License

MIT License

## Repository

https://github.com/Bibka67/VPSAgentFinder
