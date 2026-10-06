# ELK Stack

Elasticsearch + Logstash + Kibana 8.x — centralized log aggregation and visualization.

## Usage
```bash
vagrant up
# Wait 3-4 minutes for all services to start
```

| | |
|---|---|
| IP | 192.168.56.70 |
| Kibana | http://192.168.56.70:5601 |
| Elasticsearch | http://192.168.56.70:9200 |
| Also | http://localhost:5601 (port forward) |

## Resources
- 6 GB RAM, 4 vCPU required

## Send test logs
```bash
# Syslog via UDP
logger -n 192.168.56.70 -P 5000 "test message"

# JSON via UDP
echo '{"message":"hello elk","level":"info"}' | nc -u 192.168.56.70 5000

# Filebeat on another Vagrant VM → port 5044
```

## Explore in Kibana
1. Open http://192.168.56.70:5601
2. **Management → Stack Management → Index Patterns**
3. Create pattern: `logs-*`
4. Open **Discover** to search logs
