# Graylog

Graylog 6.x log management platform backed by OpenSearch and MongoDB.

## Usage
```bash
vagrant up
# Wait 4-5 minutes for all services to initialize
```

| | |
|---|---|
| IP | 192.168.56.72 |
| UI | http://192.168.56.72:9000 |
| Also | http://localhost:9001 (port forward) |
| Username | admin |
| Password | admin |
| GELF UDP | 192.168.56.72:12201 |
| Syslog UDP/TCP | 192.168.56.72:5140 |

## Resources
- 6 GB RAM, 4 vCPU required

## Configure an Input
1. Open UI → **System → Inputs**
2. Select **GELF UDP** → **Launch new input**
3. Set port `12201` → **Save**

## Send test logs
```bash
# GELF via UDP
echo '{"version":"1.1","host":"test","short_message":"hello graylog","level":1}' \
  | nc -u 192.168.56.72 12201

# Syslog
logger -n 192.168.56.72 -P 5140 "test syslog message"
```
