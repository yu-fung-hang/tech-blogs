# Kafka

## How to start

```
bin/zookeeper-server-start.sh config/zookeeper.properties
bin/kafka-server-start.sh config/server.properties
```

## Test Kafka

1. Create a topic:
```
bin/kafka-topics.sh --create --topic test --bootstrap-server localhost:9092 --partitions 1 --replication-factor 1
```

2. List topics:
```
bin/kafka-topics.sh --list --bootstrap-server localhost:9092
```

3. Start a producer:
```
bin/kafka-console-producer.sh --topic test --bootstrap-server localhost:9092
```

4. Start a consumer in another terminal:
```
bin/kafka-console-consumer.sh --topic test --from-beginning --bootstrap-server localhost:9092
```

## Commands

### Topics

* create a topic:
  `bin/kafka-topics.sh --bootstrap-server rocky102:9092 --topic first --create --partitions 1 --replication-factor 3`
* list all topics: `bin/kafka-topics.sh --bootstrap-server rocky102:9092 --list`
* get a topic's details: `bin/kafka-topics.sh --bootstrap-server rocky102:9092 --topic first --describe`
* edit a topic: `bin/kafka-topics.sh --bootstrap-server rocky102:9092 --topic first --alter --partitions 3`

### Producer -> Consumer

* producer: `bin/kafka-console-producer.sh --bootstrap-server rocky102:9092 --topic first`
* consumer: `bin/kafka-console-consumer.sh --bootstrap-server rocky102:9092 --topic first`
* consumer gets messages from beginning:
  `bin/kafka-console-consumer.sh --bootstrap-server rocky102:9092 --topic first --from-beginning`