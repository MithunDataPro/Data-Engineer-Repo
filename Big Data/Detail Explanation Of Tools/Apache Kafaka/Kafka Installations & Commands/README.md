# Installing Apache Kafka and Zookeeper Using Docker Compose

## Step 1: Create a `docker-compose.yml` File
Create a `docker-compose.yml` file in your project directory with the following content. This will set up Kafka and Zookeeper in Docker containers.

### `docker-compose.yml`:

```yaml
version: '3'
services:
  zookeeper:
    image: confluentinc/cp-zookeeper:latest
    container_name: zookeeper
    ports:
      - "2181:2181"
    environment:
      ZOOKEEPER_CLIENT_PORT: 2181
      ZOOKEEPER_TICK_TIME: 2000

  kafka:
    image: confluentinc/cp-kafka:latest
    container_name: kafka
    ports:
      - "9092:9092"
    environment:
      KAFKA_ZOOKEEPER_CONNECT: "zookeeper:2181"
      KAFKA_ADVERTISED_LISTENERS: PLAINTEXT://localhost:9092
      KAFKA_LISTENER_SECURITY_PROTOCOL_MAP: PLAINTEXT:PLAINTEXT
      KAFKA_BROKER_ID: 1
    depends_on:
      - zookeeper

```

---

## Step 2: Start Kafka and Zookeeper Services
Run the following command to start the services in detached mode:
```bash
docker-compose up -d

```
To stop the services, use:
```bash
docker-compose down

```

---

## Step 3: Verify Kafka is Running
After starting the services, you can verify that Kafka is running by listing the topics.
```bash
docker exec -it kafka /bin/bash

```

Once inside the Kafka container, use the following command to list topics:
```bash
kafka-topics --list --bootstrap-server localhost:9092

```

---

## Step 4: Kafka UI Suggestions
To manage and monitor Kafka through a UI, consider using one of the following tools:

#### 1. AKHQ (KafkaHQ)
**AKHQ** is a popular open-source UI for **Kafka**. Here’s how to add it to your **docker-compose.yml** file:
```yaml
  akhq:
    image: tchiotludo/akhq
    container_name: akhq
    ports:
      - "8080:8080"
    environment:
      AKHQ_CONFIGURATION: |
        akhq:
          connections:
            local:
              properties:
                bootstrap.servers: "kafka:9092"
    depends_on:
      - kafka

```

After adding this to your **docker-compose.yml**, start AKHQ with:
```bash
docker-compose up -d

```
You can access **AKHQ** in your browser at [http://localhost:8080](http://localhost:8080).

#### 2. Kafka Manager (Yahoo)
Another option is Kafka Manager by Yahoo, which also provides Kafka monitoring and management features. You can add it to your **docker-compose.yml** similarly.
```bash
docker run -d -p 9000:9000 --name kafka-manager \
   -e ZK_HOSTS="zookeeper:2181" \
   sheepkiller/kafka-manager

```

- Once running, access **Kafka Manager** in your browser at **http://localhost:9000.**

#### 3. Conduktor (Desktop Application)
- **Conduktor** is a desktop application (with a free version) that provides an interface for managing Kafka clusters.
- Download Conduktor from https://www.conduktor.io/ and install it on your machine.
- Configure it to connect to your Kafka cluster.


### Other Ways:
- Use **Prometheus** and **Grafana** for **Kafka Metrics** (Monitoring)
- **Prometheus** and **Grafana** are commonly used together to monitor Kafka metrics.
- You can set up **JMX Exporter** on your Kafka container to expose metrics for Prometheus, then configure Grafana to visualize these metrics.

---

## Basic Kafka Commands
Here are some basic commands to manage Kafka. These commands assume you’re inside the Kafka container.

#### Listing Topics
```bash
kafka-topics --list --bootstrap-server localhost:9092

```

#### Creating a Topic
```bash
kafka-topics --create --topic my_topic --bootstrap-server localhost:9092 --partitions 1 --replication-factor 1

```

#### Describing a Topic
```bash
kafka-topics --describe --topic my_topic --bootstrap-server localhost:9092

```

#### Producing Messages to a Topic
Start a producer to send messages to a topic:
```bash
kafka-console-producer --topic my_topic --bootstrap-server localhost:9092

```

Type messages and press Enter to send each message.

##### Consuming Messages from a Topic
**Start a consumer to read messages from a topic:**

```bash
kafka-console-consumer --topic my_topic --from-beginning --bootstrap-server localhost:9092

```

##### Deleting a Topic
**To delete a topic:**
```bash
kafka-topics --delete --topic my_topic --bootstrap-server localhost:9092

```

##### Viewing Consumer Groups
**List all consumer groups:**
```bash
kafka-consumer-groups --bootstrap-server localhost:9092 --list

```

##### Describing a Consumer Group
**Get details about a specific consumer group:**
```bash
kafka-consumer-groups --bootstrap-server localhost:9092 --describe --group <group_name>

```
##### Additional Notes
- **Kafka** and **Zookeeper** logs can be accessed using Docker’s **logs** command:
```bash
docker logs kafka
docker logs zookeeper

```
- To exit the Kafka container shell, type **exit**.

This setup and these commands should help you get started with Kafka in Docker, including monitoring with a UI.
