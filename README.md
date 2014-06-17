# spark-example-kafka

This is a self-contained example project to illustrate using Spark Streaming with Kafka.

Firstly, build the JAR:

    sbt assembly

Next, create your Kafka topic:

    kafka-topics.sh --zookeeper localhost:2181 --create --topic wordcount --partitions 1 --replication-factor 1

Run the KafkaWordCountProducer to produce 10 messages per second with 100 words per message:

    bin/KafkaWordCountProducer localhost:2181 wordcount 10 100

Last but not least, run the KafkaWordCount example:

    bin/KafkaWordCount localhost:2181 KafkaWordCount wordcount 1

Check ```build.sbt``` to see how the dependencies are setup and workarounds for classpath collisions while building the assembly.
