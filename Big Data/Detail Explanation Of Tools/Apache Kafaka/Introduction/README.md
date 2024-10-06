Large companies contain hundreds of microservices, all needing data to operate. When we talk about technologies that they use, we come across Apache Kafka, which is used to handle trillions of data per day. In this blog, let’s understand what Kafka is and why it is so popular.

Let’s take an example of [Microservices]([Big Data/Detail Explanation Of Tools/Apache Kafaka/Introduction/Microservices](https://github.com/MithunDataPro/Data-Engineer-Repo/tree/main/Big%20Data/Detail%20Explanation%20Of%20Tools/Apache%20Kafaka/Introduction/Microservices))
 involved in ride application. When a ride is completed, this information is needed by multiple microservices.

- **Ride management service** manages ride information.  
- **Email notification service** sends a ride receipt in the email.  
- **Driver management service** manages driver information. It updates the status of the driver so that he can be allocated for the next ride.  
- **Fraud detection service** detects any fraudulent activity that had happened in the ride.

![image](https://github.com/user-attachments/assets/2bad5d8d-4a0f-49b9-9061-f27246ab35de)


In this case, we have many services that need **ride-completion** data to operate on. If synchronous calls are made to all services then we will end up making this request slower. And also it will introduce coupling between services.

We can make calls asynchronous by using a **background job processor** like [Sidekiq GitHub Repository](https://github.com/mperham/sidekiq) or [GoCraft Work GitHub Repository](https://github.com/gocraft/work). In this case, we need to add jobs in **ride-management-service**. Whenever a new service wants **ride-completion** data, we need to do code changes in **ride-management-service** to add new jobs. This won’t solve the above problem of coupling between services.

The next approach is to use some queue like [RabbitMQ Official Website](https://www.rabbitmq.com/). In this case, only one consumer can consume the data from the queue. In the above scenario, we have many consumers who need **ride-completion data**. So simple queue won’t solve our problem.

How nice would it be if we have a publisher-subscriber system here?

![image](https://github.com/user-attachments/assets/410c7a7e-cc2f-4e8d-96dd-7d24fe7324da)


Whenever an event happens, the publisher publishes messages to the messaging system. Any microservice that needs this information can subscribe to it. This type of architecture is called **event-driven architecture**. 

**It provides multiple benefits:**

- Loosely coupled microservices  
- Asynchronous communication  
- Easily scalable since services are decoupled.

![image](https://github.com/user-attachments/assets/ec768ce5-2e84-4dba-ade5-53dbb08497b9)


Apache Kafka is one such publisher-subscriber messaging system. We can have multiple consumers who can read the same events. The data sent to Kafka is persisted to some duration defined by the retention policy.

In Kafka, publishers are called producers. And subscribers are called consumers. In the above example, when a ride gets completed, producers can publish this event to Kafka, and all other services which require this event can subscribe to it. But where and how does Kafka store these events?

---

### Kafka Topic:

![image](https://github.com/user-attachments/assets/73c617e7-71b7-4385-9c54-51d74a38b415)

In Kafka, the specific location where messages are stored is called [Kafka Documentation on Topics](https://kafka.apache.org/documentation/#intro_topics). If we have to compare it with the SQL database then the topic is like a table and the message is like a row of data. But in Kafka, Message is an immutable record which means that once they are received into a topic they can not be changed. Each message that is sent is appended to a time-ordered sequence. This style of maintaining data as events is an architectural style known as [Martin Fowler - Event Sourcing](https://martinfowler.com/eaaDev/EventSourcing.html).

**There are several advantages that event sourcing provides us with:**

- Debugging is easier because we have a complete log of every change that is made.  
- Reads and writes can be scaled independently.

![image](https://github.com/user-attachments/assets/98234919-8e22-4cb9-a8cb-61aefcda0f20)


Each of these messages in the topic has a message offset value. It’s just a placeholder given to each message like the page number in the book. Each consumer of the topic reads messages at its own pace. **As we keep a bookmark for the last page we read in the book, consumers keep track of the last message it has read.**

The time for which Kafka can retain the messages in the topic is configurable called [CloudKarafka Blog - Kafka Retention Period](https://www.cloudkarafka.com/blog/2018-05-08-what-is-kafka-retention-period.html#:~:text=If%20the%20log%20retention%20is,data%20is%20not%20a%20problem.). And this value can be specified when we create a topic. If we do not specify a value for it then it picks the default value which is 7 days.

---

### Kafka Broker
The place where topics are kept and maintained are called [DataFlair - Kafka Broker Overview](https://data-flair.training/blogs/kafka-broker/). Kafka broker receives messages from producers and stores them on disk. When a consumer wants to read from a topic then it must establish a connection with a broker. Upon the connection, consumers can read from the beginning of the topic or from the time connection is made.

Kafka is a [StackPath Blog - Distributed System Overview](https://blog.stackpath.com/distributed-system/). Distributed systems consist of many workers where the work is spread across. In Kafka, these workers are called **brokers**. Brokers together form the Kafka cluster.

As we can scale the producer, it can start sending millions of data to Kafka. Due to which we might start needing more disk space, more CPU, etc in the broker machine. We might start needing to horizontally scale this topic. How do we horizontally scale the topics?

---

### Topic Partitions:

![image](https://github.com/user-attachments/assets/93622d85-603f-4011-9bc7-ed31ffc7cedf)

Kafka topics can be split into partitions and can be kept in separate Broker servers in different machines. [InstaClustr Blog - Kafka Partitions](https://www.instaclustr.com/the-power-of-kafka-partitions-how-to-get-the-most-out-of-your-kafka-cluster/) help Kafka with its ability to scale and higher levels of throughput. Producers distribute messages across partitions by some strategy like round-robin or based on a key. Each broker will hold one or more partitions and a single partition has to be stored entirely in one broker.

![image](https://github.com/user-attachments/assets/e12c1f3a-05c7-46eb-a76a-d2cfe0db01cf)


On both the producer and the broker side, writes to different partitions can be done fully in parallel. Similarly, Each of these partitions can be read by consumers in parallel. As we split the topic into partitions for scaling, we can also scale the consumers.

---

### Consumer Groups
Instead of having single consumers to read all the messages, we will have [Confluent Documentation - Kafka Consumer Groups](https://docs.confluent.io/current/clients/consumer.html#consumer-groups). Here we have independent consumers working together as a team.

![image](https://github.com/user-attachments/assets/7470a31b-b1e4-4d0f-bd50-f6158e0eda28)


Each consumer in the consumer group reads messages from one or more partitions. In the above example, there are two consumer groups reading messages from partitions of the topic.

In the above example, there are two consumer groups with 2 consumers, and each consumer reads from two partitions. Since we have multiple consumers to read from the topic, the overall performance of reading data increases.

---

### Zookeeper
[StackOverflow - Is Zookeeper a Must for Kafka?](https://stackoverflow.com/questions/23751708/is-zookeeper-a-must-for-kafka) is the centralized service for storing metadata about the cluster. It stores information regarding topic, broker, and partition metadata. It helps in monitoring and handling failures. Every time a broker starts up, it registers itself to the zookeeper. And the zookeeper keeps track of each broker by calling a health check on it.

In the older version of Kafka, the zookeeper was responsible for keeping track of the last message read by the consumer. In the newer versions, consumers are responsible for keeping track of the offset it read.

[Confluent Blog - Removing Zookeeper Dependency in Kafka](https://www.confluent.io/blog/removing-zookeeper-dependency-in-kafka/). Kafka itself stores metadata and manage the cluster as discussed in [Apache Kafka KIP-500: Replace Zookeeper with Self-Managed Metadata Quorum](https://cwiki.apache.org/confluence/display/KAFKA/KIP-500%3A+Replace+ZooKeeper+with+a+Self-Managed+Metadata+Quorum).

---

## Producer
The producer is responsible for pushing events to Kafka. As we saw earlier, producers distribute messages across partitions by some strategy like round-robin or based on a partition key. Producers always send messages to leader partitions. Producers send messages in batches which is configured by size and time.

![image](https://github.com/user-attachments/assets/554d0e4f-f755-4a05-b2e6-9663a0f895f4)


## PART-2 — Fault tolerance in Kafka
## PART-3 — Kafka Consumer Groups

## Summary
Apache Kafka helps us to have decoupled services. Today, if we say only two services need particular topic events, as the business requirements change, we might start needing the same events in other services also. And this can be easily done by just subscribing the new service to that event topic. In Apache Kafka, each of the components like producer, broker, zookeeper, and consumer can be scaled independently.

## References
- [Event sourcing, CQRS, stream processing, and Apache Kafka](https://martinfowler.com/eaaDev/EventSourcing.html)
- [Kafka for beginners](https://kafka.apache.org/quickstart)
- [Getting Started with Apache Kafka by Ryan Plant](https://developer.confluent.io/learn/kafka)
- [Zookeeper explained](https://zookeeper.apache.org/doc/current/zookeeperOver.html)
- [Kafka topic partitions](https://www.instaclustr.com/the-power-of-kafka-partitions-how-to-get-the-most-out-of-your-kafka-cluster/)
- [Kafka-all-you-need-to-know](https://data-flair.training/blogs/kafka-tutorial/)
- [Offset management](https://docs.confluent.io/platform/current/clients/consumer.html#offset-management)
