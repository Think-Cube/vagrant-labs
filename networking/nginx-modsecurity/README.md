# Nginx + ModSecurity + OWASP CRS

Nginx web server with ModSecurity WAF and OWASP Core Rule Set.

## Usage
```bash
vagrant up
```

| | |
|---|---|
| IP | 192.168.56.33 |
| URL | http://192.168.56.33 |
| Also | http://localhost:8080 (port forward) |

## Test WAF
```bash
# Should be blocked (SQL injection attempt)
curl "http://192.168.56.33/?id=1' OR '1'='1"
```
