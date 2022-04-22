RUNNNING APACHE KAFKA
---------------------------------------------------------------------

*1.- Download Apache Kafka*

Version 2.8.0 of Apache Kafka can be downloaded from this link:

https://archive.apache.org/dist/kafka/2.8.0/kafka_2.12-2.8.0.tgz


Useful note: this is the command to kill a process that runs in a given port
(in Ubuntu).

```

sudo kill -9 `sudo lsof -t -i:9001`

```

---------------------------------------------------------------------

*2.- Execute Zookeeper*

Once the previous file is downloaded and extracted, we have to navigate 
to the bin directory and execute this command to run Zookeeper:

```

./zookeeper-server-start.sh ../config/zookeeper.properties

```

Zookeeper runs in port 2181:

```

INFO binding to port 0.0.0.0/0.0.0.0:2181 (org.apache.zookeeper.server.NIOServerCnxnFactory)

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

Once again, we go to the bin directory, 
where we can run the Kafka Broker with this command:

```

./kafka-server-start.sh ../config/server.properties

```

---------------------------------------------------------------------

*5.- Create a topic*

Always inside the bin directory, we create a topic 
called topic-example using this command:

```
./kafka-topics.sh --create --topic topic-example -zookeeper localhost:2181 --partitions 2 --replication-factor 1

```
---------------------------------------------------------------------

*6.- Producing messages*

```
./kafka-console-producer.sh --broker-list localhost:9901 --topic topic-example

```
---------------------------------------------------------------------

*7.- Consuming messages*

```
./kafka-console-consumer.sh --bootstrap-server localhost:9901 --topic topic-example

./kafka-console-consumer.sh --bootstrap-server localhost:9901 --topic topic-example --from-beginning

```
---------------------------------------------------------------------

*8.- Listing topics*

Command to list all the topics available:

```
./kafka-topics.sh --zookeeper localhost:2181 --list

```

---------------------------------------------------------------------