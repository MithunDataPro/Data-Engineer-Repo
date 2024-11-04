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
