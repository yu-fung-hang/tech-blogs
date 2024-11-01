# Kafka

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