# RabbitMQ Cluster

RabbitMQ 3-node cluster with management UI.

## Usage
```bash
vagrant up rabbit1    # Start primary first (creates admin user)
vagrant up rabbit2 rabbit3
```

| Node | IP | Role |
|------|-----|------|
| rabbit1 | 192.168.56.103 | Primary |
| rabbit2 | 192.168.56.104 | Member |
| rabbit3 | 192.168.56.105 | Member |

| | |
|---|---|
| Management UI | http://192.168.56.103:15672 |
| Also | http://localhost:15672 (port forward) |
| AMQP | 192.168.56.103:5672 |
| Username | admin |
| Password | admin123 |

## Check cluster status
```bash
vagrant ssh rabbit1 -c "sudo rabbitmqctl cluster_status"
```

## Connect from application
```bash
# AMQP URI (round-robin across all nodes)
amqp://admin:admin123@192.168.56.103:5672/

# With failover
amqp://admin:admin123@192.168.56.103:5672,192.168.56.104:5672,192.168.56.105:5672/
```

## Enable Quorum Queues (HA)
```bash
# Create a quorum queue via management API
curl -u admin:admin123 -X PUT http://192.168.56.103:15672/api/queues/%2F/my-queue \
  -H "content-type: application/json" \
  -d '{"durable":true,"arguments":{"x-queue-type":"quorum"}}'
```

## Enable Shovel / Federation
```bash
vagrant ssh rabbit1
sudo rabbitmq-plugins enable rabbitmq_shovel rabbitmq_shovel_management
```
