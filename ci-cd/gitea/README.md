# Gitea

Lightweight self-hosted Git service with built-in CI/CD via Gitea Actions.

## Usage
```bash
vagrant up
```

| | |
|---|---|
| IP | 192.168.56.82 |
| UI | http://192.168.56.82:3000 |
| SSH | git@192.168.56.82 (port 2222) |
| Also | http://localhost:3004 (port forward) |

## Setup
1. Open UI → complete the installation wizard (SQLite, leave defaults).
2. Create an admin account.

## Clone via SSH
```bash
git clone ssh://git@192.168.56.82:2222/user/repo.git
# or add to ~/.ssh/config:
# Host gitea
#   HostName 192.168.56.82
#   Port 2222
```

## Enable Gitea Actions runner
1. In UI: **Site Administration → Runners → Create Runner Token**
2. SSH into the VM and add the token to docker-compose.yml:
```bash
vagrant ssh
# Edit /opt/gitea/docker-compose.yml, set GITEA_RUNNER_REGISTRATION_TOKEN
docker compose -f /opt/gitea/docker-compose.yml up -d act-runner
```
