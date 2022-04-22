RUNNNING KAFKA
---------------------------------------------------------------------

*1.- Download Apache Kafka*

Version 2.8.0 of Apache Kafka was downloaded from this link:

https://archive.apache.org/dist/kafka/2.8.0/kafka_2.12-2.8.0.tgz


---------------------------------------------------------------------

*2.- Execute Zookeeper*

Once the previous file was downloaded and extracted, we have to navigate 
to the bin directory and execute this command to run Zookeeper:

```

./zookeeper-server-start.sh ../config/zookeeper.properties

```

---------------------------------------------------------------------

*3.- Configure Kafka Broker*

Then, we have go to the config directory where we have to add 
these properties to the file server.properties:

```

listeners=PLAINTEXT://localhost:9901
auto.create.topics.enable=false

```

---------------------------------------------------------------------

*4.- Run Kafka Broker*

Once again from the bin directory, we can run the Kafka Broker with this command:

```

./kafka-server-start.sh ../config/server.properties

```

---------------------------------------------------------------------