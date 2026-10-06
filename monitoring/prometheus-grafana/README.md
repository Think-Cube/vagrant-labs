# Prometheus + Grafana

Full observability stack: Prometheus, Grafana, Node Exporter, Alertmanager.

## Usage
```bash
vagrant up
```

| | |
|---|---|
| IP | 192.168.56.73 |
| Grafana | http://192.168.56.73:3000 |
| Prometheus | http://192.168.56.73:9090 |
| Alertmanager | http://192.168.56.73:9093 |
| Node Exporter | http://192.168.56.73:9100/metrics |
| Also | http://localhost:3002 (port forward) |
| Username | admin |
| Password | admin |

## Import Node Exporter dashboard
1. Grafana → **Dashboards → Import**
2. Enter ID: **1860** (Node Exporter Full)
3. Select **Prometheus** datasource → **Import**

## Add a scrape target
Edit `/opt/monitoring/prometheus.yml` on the VM, then:
```bash
docker compose -f /opt/monitoring/docker-compose.yml restart prometheus
```

## PromQL examples
```
# CPU usage
100 - (avg by(instance) (rate(node_cpu_seconds_total{mode="idle"}[5m])) * 100)

# Memory available
node_memory_MemAvailable_bytes / node_memory_MemTotal_bytes * 100

# Disk I/O
rate(node_disk_io_time_seconds_total[5m])
```
