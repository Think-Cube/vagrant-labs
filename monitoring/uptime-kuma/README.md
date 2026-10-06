# Uptime Kuma

Self-hosted uptime monitoring tool with status pages and multi-channel notifications.

## Usage
```bash
vagrant up
```

| | |
|---|---|
| IP | 192.168.56.74 |
| UI | http://192.168.56.74:3001 |
| Also | http://localhost:3003 (port forward) |

1. Open the UI and create your admin account on first visit.
2. Add monitors: HTTP(s), TCP, Ping, DNS, Docker container, and more.
3. Configure notification channels: Slack, Teams, PagerDuty, email, Telegram.
4. Create a public **Status Page** to share with stakeholders.

## Monitor all other Vagrant environments
Add HTTP monitors for each service:
- Kibana: `http://192.168.56.70:5601`
- Grafana: `http://192.168.56.71:3000`
- Prometheus: `http://192.168.56.73:9090`
- Vault: `http://192.168.56.60:8200`
- Keycloak: `http://192.168.56.61:8080`
