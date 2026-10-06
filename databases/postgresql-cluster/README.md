# PostgreSQL Streaming Replication Cluster

PostgreSQL 16 cluster: 1 primary + 2 streaming replicas.

## Usage
```bash
vagrant up
# Start primary first, replicas will pg_basebackup from it
vagrant up pg-primary
vagrant up pg-replica1 pg-replica2
```

| Node | IP | Role |
|------|-----|------|
| pg-primary | 192.168.56.90 | Primary (R/W) |
| pg-replica1 | 192.168.56.91 | Replica (RO) |
| pg-replica2 | 192.168.56.92 | Replica (RO) |

- Port: `5432`
- User: `postgres` / Password: `postgres`
- Replication user: `replicator` / `replicator`

## Connect
```bash
psql -h 192.168.56.90 -U postgres
```

## Check replication status
```sql
-- On primary
SELECT client_addr, state, sync_state, sent_lsn, replay_lsn
FROM pg_stat_replication;
```

## Verify replica lag
```sql
-- On replica
SELECT now() - pg_last_xact_replay_timestamp() AS replication_lag;
```

## Promote a replica (failover)
```bash
vagrant ssh pg-replica1
sudo -u postgres pg_ctl promote -D /var/lib/postgresql/16/main
```
