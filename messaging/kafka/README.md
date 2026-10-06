# Apache Kafka

Kafka 3.8 in KRaft mode (no ZooKeeper) + Kafka UI web console.

## Usage
```bash
vagrant up
```

| | |
|---|---|
| IP | 192.168.56.100 |
| Bootstrap | 192.168.56.100:9092 |
| Kafka UI | http://192.168.56.100:8080 |
| Also | http://localhost:8087 (port forward) |

## Produce and consume
```bash
# Inside the VM
vagrant ssh
docker exec -it kafka-kafka-1 /opt/kafka/bin/kafka-topics.sh \
  --create --topic test --bootstrap-server localhost:9092 --partitions 3 --replication-factor 1

# Produce
docker exec -it kafka-kafka-1 /opt/kafka/bin/kafka-console-producer.sh \
  --topic test --bootstrap-server localhost:9092

# Consume
docker exec -it kafka-kafka-1 /opt/kafka/bin/kafka-console-consumer.sh \
  --topic test --bootstrap-server localhost:9092 --from-beginning
```

## From host
```bash
kafka-topics.sh --bootstrap-server 192.168.56.100:9092 --list
```

## Kafka UI
Browse topics, consumer groups, and messages at http://192.168.56.100:8080.
