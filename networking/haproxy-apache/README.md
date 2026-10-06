# HAProxy + Apache

HAProxy load balancer with 2 Apache backend servers.

## Usage
```bash
vagrant up
```

| VM | IP | Role |
|---|---|---|
| haproxy | 192.168.56.30 | Load balancer |
| apache1 | 192.168.56.31 | Backend 1 |
| apache2 | 192.168.56.32 | Backend 2 |

| URL | Description |
|---|---|
| http://192.168.56.30 | Load balanced endpoint (round-robin) |
| http://192.168.56.30:8404/stats | HAProxy statistics dashboard |
