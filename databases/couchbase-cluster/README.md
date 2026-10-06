# Couchbase Cluster

Couchbase Server 3-node cluster with Data, Index, Query (N1QL), and Full-Text Search services.

## Usage
```bash
vagrant up couchbase1    # Bootstrap primary first
vagrant up couchbase2 couchbase3
```

| Node | IP | Services |
|------|-----|---------|
| couchbase1 | 192.168.56.86 | Data, Index, Query |
| couchbase2 | 192.168.56.87 | Data, Index |
| couchbase3 | 192.168.56.88 | Data, FTS |

| | |
|---|---|
| Web UI | http://192.168.56.86:8091 |
| Also | http://localhost:8091 (port forward) |
| Username | Administrator |
| Password | admin123 |

## Resources
- 2 GB RAM per node (6 GB total), 2 vCPU per node

## N1QL Query example
```sql
-- Via Query Workbench in the Web UI, or cbq CLI
SELECT name, email FROM default WHERE type = "user" LIMIT 10;

CREATE PRIMARY INDEX ON default;
```

## Connect with SDK
```javascript
const couchbase = require('couchbase');
const cluster = await couchbase.connect('couchbase://192.168.56.86', {
  username: 'Administrator',
  password: 'admin123',
});
const bucket = cluster.bucket('default');
const collection = bucket.defaultCollection();

await collection.upsert('key1', { name: 'Alice', type: 'user' });
const result = await collection.get('key1');
```

## Rebalance after node changes
```bash
vagrant ssh couchbase1
/opt/couchbase/bin/couchbase-cli rebalance \
  --cluster http://192.168.56.86:8091 \
  --username Administrator --password admin123
```
