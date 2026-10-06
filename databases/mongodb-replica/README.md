# MongoDB Replica Set

MongoDB 8.0 three-member replica set (`rs0`).

## Usage
```bash
# Start all nodes — mongo1 will initiate the replica set
vagrant up
```

| Node | IP | Role |
|------|-----|------|
| mongo1 | 192.168.56.93 | Primary (elected) |
| mongo2 | 192.168.56.94 | Secondary |
| mongo3 | 192.168.56.95 | Secondary |

- Port: `27017`
- Replica set name: `rs0`

## Connect
```bash
# Single node (will redirect to primary)
mongosh mongodb://192.168.56.93:27017/?replicaSet=rs0

# Full connection string
mongosh "mongodb://192.168.56.93:27017,192.168.56.94:27017,192.168.56.95:27017/?replicaSet=rs0"
```

## Check replica set status
```javascript
rs.status()
rs.isMaster()
```

## Check replication lag
```javascript
rs.printReplicationInfo()
rs.printSecondaryReplicationInfo()
```

## Trigger failover (test)
```bash
vagrant ssh mongo1 -c "mongosh --eval 'rs.stepDown()'"
# mongo2 or mongo3 will be elected primary
```
