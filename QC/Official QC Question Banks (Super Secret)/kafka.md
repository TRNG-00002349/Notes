# Unit: Kafka

* **What is Kafka?**
    * Kafka is a distributed streaming platform developed by LinkedIn and later open-sourced under the Apache Software Foundation.
    * It is a publish-subscribe open source message broker application.
    * It is primarily used to build real-time data pipelines and streaming applications.

* **What are the various features of Kafka?**
    * **High Throughput**: Kafka can handle large volumes of data with low latency, making it suitable for both real-time and batch processing.
    * **Durability**: Kafka persists messages on disk and replicates them across multiple brokers, ensuring data durability.
    * **Scalability**: Kafka can scale horizontally by adding more brokers to a Kafka cluster, making it capable of handling increased loads.
    * **Fault Tolerance**: Kafka's replication and partitioning mechanisms ensure that the system can recover from failures without losing data.
    * **Distributed**: Kafka operates as a distributed system, which means it can be deployed across multiple servers and data centers.

* **What are the various Kafka components?**
    * **Broker**: A Kafka broker is a server that stores data and serves clients. A Kafka cluster is made up of multiple brokers.
    * **Topic**: A topic is a category or feed name to which records are stored and published. It is a logical channel to which producers send data and from which consumers read data.
    * **Producer**: Producers are the entities that publish data to topics.
    * **Consumer**: Consumers are the entities that subscribe to topics and process the feed of published messages.

* **Explain about Producer and Consumer.**
    * **Producer**: 
        * A Kafka producer is a client that publishes messages to one or more Kafka topics. 
        * The producer is responsible for selecting which partition within the topic to publish to, either randomly or based on some key value. 
        * Producers can also manage retries in case of failures.
    * **Consumer**: 
        * A Kafka consumer subscribes to one or more Kafka topics and processes the messages. 
        * Consumers are part of a consumer group, and each message in a topic is delivered to only one consumer in the group, enabling parallel processing of messages across multiple consumers.

* **What is a Topic and How to Create It?**
    * A Kafka topic is a logical channel to which data is published by producers and from which consumers read data.
    * You can create a Kafka topic using the command-line tool:
        ```
        bin/kafka-topics.sh --create --topic my-topic --bootstrap-server localhost:9092 --partitions 3 --replication-factor 2
        ```

* **What is the Role of a Broker?**
    * A Kafka broker is a server that stores the data of a Kafka topic and serves client requests. Each broker can handle thousands of partitions and millions of messages per second. 
    * Brokers are responsible for:
        1. **Storing messages**: Each broker stores messages for the partitions it is responsible for.
        2. **Serving clients**: Brokers respond to producer and consumer requests to publish and retrieve messages.
        3. **Replication**: Brokers replicate partition data across the cluster to ensure fault tolerance.
        4. **Managing leader and follower roles**: Each partition in Kafka has a leader broker that handles all reads and writes for that partition, and follower brokers that replicate the data.

* **What is a Consumer Group?**
    * A Consumer Group is a group of consumers that work together to consume data from a Kafka topic. 
    * Each consumer in the group is assigned a subset of partitions from the topic, ensuring that each partition is consumed by only one consumer in the group.
    * This allows for parallel processing of messages across multiple consumers, and if a consumer fails, the partitions it was processing can be reassigned to other consumers in the group.

* **How to Create a Producer and Consumer?**
    * To create a simple Producer: 
        ```
        kafka-console-producer.sh --bootstrap-server localhost:9092 --topic first_topic
        ```
    * To create a simple Consumer:
        ```
        kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic first_topic --from-beginning
        ```

* **What are the Main APIs of Kafka?**
    * **Producer API**: Allows an application to publish streams of records to one or more Kafka topics.
    * **Consumer API**: Allows an application to subscribe to one or more topics and process the stream of records produced to them.
    * **Streams API**: Allows an application to process data in real-time using stream processing. It provides the ability to transform input streams to output streams.
    * **Connect API**: Allows for building and running connectors that move large data sets between Kafka and other systems.

* **What Ensures the Load Balancing of the Server in Kafka? / What do you Understand by Load Balancing in Kafka?**
    * Load balancing in Kafka is achieved through **`partitioning`**.
    * Kafka balances load by electing a **`leader`** for each partition. 
    * The leader handles all reads and writes for that partition, while the **`followers`** replicate the data. 
    * If a leader fails, a new leader is automatically elected from the followers. This entire process ensures load balancing of the servers.

* **Explain the Concept of Leader and Follower.**
    * In Kafka, each partition in a topic has one broker acting as the Leader and one or more brokers acting as Followers. 
    * The **`leader`** is responsible for all read and write operations for that partition, ensuring that the data is consistent. 
    * **`Followers`** replicate the data from the leader and serve as backup copies. 
    * If the leader fails, one of the followers is automatically promoted to be the new leader, ensuring high availability and fault tolerance.

* **What are In-Sync Replicas (ISR)?**
    * **`In-Sync Replicas (ISR)`** are the set of replicas (including the leader) that are fully up-to-date with the leader's data for a particular partition. 
    * They are **"in-sync"** because they have successfully replicated all recent messages from the leader. 
    * Only ISR members are eligible to be elected as the new leader if the current leader fails. This mechanism ensures that no data is lost in case of a leader failure.

* **Why are Replications Critical in Kafka?**
    * Replications are critical in Kafka for the following reasons:
        * **Fault Tolerance**: Replication ensures that data is not lost in case of broker failures. If a broker hosting a partition's leader fails, a follower replica can take over as the leader without data loss.
        * **High Availability**: Replication allows Kafka to continue serving requests even when some brokers are down, ensuring that the system remains available.

* **What do you Know About Partitions in Kafka?**
    * Partitions are a fundamental concept in Kafka, allowing for horizontal scalability, parallel processing, and fault tolerance. 
    * Each Kafka topic is divided into multiple partitions, and each partition is an ordered sequence of records.

* **How Do You Change the Kafka Partition? Can We Increase or Decrease the Number of Partitions?**
    * You can change the Kafka partition by using **` --alter`** command in Kafka CLI. 
    * For Example, there is a topic with 4 partitions and we want to increase it to 6.
        ```
        kafka-topics.sh --alter --topic my-topic --bootstrap-server localhost:9092 --partitions 6
        ```
    * This increases the number of partitions for "my-topic" to 6. 
    * Decreasing the number of partitions is not supported in Kafka. The reason is that decreasing partitions could lead to data loss and inconsistencies.

* **How Do You Know the Details of a Kafka Topic?**
    * You can **describe** a Kafka topic to get its details using the following command:
        ```
        kafka-topics.sh --describe --topic my-topic --bootstrap-server localhost:9092

        ```


