# Redis Replication

Redis 7 with 1 primary + 2 replicas and LRU eviction policy.

## Usage
```bash
vagrant up redis1    # Start primary first
vagrant up redis2 redis3
```

| Node | IP | Role |
|------|-----|------|
| redis1 | 192.168.56.96 | Primary (R/W) |
| redis2 | 192.168.56.97 | Replica (RO) |
| redis3 | 192.168.56.98 | Replica (RO) |

- Port: `6379`
- No password (lab only — add `requirepass` in redis.conf for production)

## Connect
```bash
redis-cli -h 192.168.56.96

# Or with redis-cli in PATH
redis-cli -h 192.168.56.96 ping
```

## Check replication
```bash
redis-cli -h 192.168.56.96 INFO replication
```

## Promote replica (manual failover)
```bash
vagrant ssh redis2
redis-cli REPLICAOF NO ONE
# Update redis3 to replicate from redis2:
redis-cli -h 192.168.56.98 REPLICAOF 192.168.56.97 6379
```

## Add Redis Sentinel (HA)
For automatic failover, add 3 Sentinel processes. See [Redis Sentinel docs](https://redis.io/docs/management/sentinel/).
