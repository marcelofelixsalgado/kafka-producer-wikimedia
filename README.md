# Kafka Producer Wikimedia

This project take data from Wikimedia and put it into a local Kafka, using a Kafka producer.

## What is Wikimedia?
Wikimedia is a global movement whose mission is to bring free educational content to the world.
Through various projects, chapters, and the support structure of the non-profit Wikimedia Foundation, Wikimedia strives to bring about a world in which every single human being can freely share in the sum of all knowledge.

### Recent Wikimedia change stream:
https://stream.wikimedia.org/v2/stream/recentchange

Other sample demos:
https://codepen.io/Krinkle/pen/BwEKgW?editors=1010
https://esjewett.github.io/wm-eventsource-demo/


## Integration flow

```
Wikimedia Event Stream -> WikimeiaChangesProvider (java class) -> Local Kafka (topic: wikimedia.recentchange)
```

## Running

1- Kafka and Conduktor startup
```
doker compose up
```

2- Create Kafka topic
```
./kafka-topics.sh --create --topic=wikimedia.recentchange --partitions=3 --replication-factor=1 --bootstrap-server=localhost:9092
```

3- Run WikimediaChangesProducer.java

4- Create a local consumer to see messages coming
```
 ./kafka-console-consumer.sh --topic=wikimedia.recentchange --bootstrap-server=localhost:9092 --from-beginning
```