# Loki + Grafana

Grafana Loki 3.x log aggregation stack with Promtail agent and Grafana dashboards.

## Usage
```bash
vagrant up
```

| | |
|---|---|
| IP | 192.168.56.71 |
| Grafana | http://192.168.56.71:3000 |
| Loki API | http://192.168.56.71:3100 |
| Also | http://localhost:3001 (port forward) |
| Username | admin |
| Password | admin |

## Query logs in Grafana
1. Open Grafana → **Explore**
2. Select **Loki** datasource
3. Use LogQL: `{job="varlogs"} |= "error"`

## Push logs from external source
```bash
# Push via HTTP API
curl -X POST http://192.168.56.71:3100/loki/api/v1/push \
  -H "Content-Type: application/json" \
  -d '{"streams":[{"stream":{"app":"myapp"},"values":[["'$(date +%s%N)'","hello loki"]]}]}'
```

## Add Promtail to another VM
Configure Promtail's `clients[].url` to `http://192.168.56.71:3100/loki/api/v1/push`.
