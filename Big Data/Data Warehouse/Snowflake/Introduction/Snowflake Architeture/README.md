# Data Architectures Overview

## 1. **Shared Disk Architecture**

![image](https://github.com/user-attachments/assets/6449d3c4-039b-4159-974c-647eb497574a)

### Description
- A system where multiple processing nodes share access to a common disk storage.
- All nodes can read and write to the same storage, but memory and compute resources are independent.

### Characteristics
- **Shared Storage:** Centralized disk or SAN (Storage Area Network).
- **Independent Compute:** Each node has its own CPU and memory.
- **Scalability:** Limited by the disk bandwidth; adding nodes doesn't always improve performance.
- **Use Cases:** Clustered databases, OLTP systems.

### Pros
- Simplified data management with a single storage layer.
- High availability and fault tolerance.

### Cons
- Disk I/O contention between nodes.
- Potential bottlenecks in storage access.

---

## 2. **Shared Nothing Architecture**

![image](https://github.com/user-attachments/assets/7114e955-cff0-4814-b491-b2bc2ca24688)

### Description
- A distributed computing architecture where each node has its own disk, memory, and compute.
- Nodes communicate over a network and share no hardware resources.

### Characteristics
- **Decentralized Storage:** Data is partitioned across nodes.
- **Independent Nodes:** Each node processes its own data independently.
- **Scalability:** Easy to scale horizontally by adding nodes.
- **Use Cases:** Distributed databases, Big Data systems like Hadoop, NoSQL databases.

### Pros
- Eliminates single points of failure.
- Scalability and high performance.

### Cons
- Complex to manage and maintain.
- Higher latency for inter-node communication.

---

## 3. **Snowflake Architecture**

![image](https://github.com/user-attachments/assets/1dd5cd6e-4ffa-4303-9cf5-45efae56631b)

### Description
- A modern cloud-native data warehousing architecture that uses a hybrid of shared-disk and shared-nothing approaches.

### Key Components
1. **Centralized Storage (Shared Disk):**
   - Data is stored in cloud object storage (e.g., AWS S3, Azure Blob).
   - Accessible by all compute nodes.

2. **Processing (Shared Nothing):**
   - Independent compute clusters, known as Virtual Warehouses.
   - Each cluster processes data independently without resource contention.

3. **Cloud Services Layer:**
   - Handles metadata, query optimization, security, and management.
   - Separates storage and compute for scalability and elasticity.

### Characteristics
- **Separation of Storage and Compute:** Compute can scale independently of storage.
- **Elasticity:** Automatically scales resources up and down based on workload.
- **Multi-Cluster Architecture:** Supports concurrent workloads efficiently.

### Pros
- Zero maintenance; fully managed service.
- High concurrency and scalability.
- Cost-efficient pay-as-you-go model.

### Cons
- Vendor lock-in with cloud providers.
- Network latency for large data transfers.

---

## 4. **Other Architectures**

### a. **Lambda Architecture**
- Designed for Big Data systems.
- Combines **batch processing** (for high accuracy) with **stream processing** (for low latency).
- Used for applications requiring real-time analytics.

### b. **Kappa Architecture**
- A simplified version of Lambda.
- Focuses only on stream processing.
- Suitable for scenarios where batch processing is unnecessary.

### c. **Federated Architecture**
- Combines multiple independent systems to appear as a single logical database.
- Used in environments with multiple heterogeneous data sources.

### d. **Clustered Architecture**
- Combines multiple nodes in a cluster for processing and storage.
- Nodes collaborate and share tasks.

### e. **Multi-Tier Architecture**
- Layers include:
  1. Presentation Layer (UI)
  2. Application Layer (Logic)
  3. Data Layer (Storage)
- Used in traditional web applications.

---

## Summary Table

| Architecture          | Storage              | Compute          | Scalability   | Use Cases                      |
|-----------------------|----------------------|------------------|---------------|--------------------------------|
| Shared Disk           | Centralized          | Independent      | Limited       | OLTP, Clustered Databases      |
| Shared Nothing        | Decentralized        | Independent      | High          | Distributed Databases, Big Data|
| Snowflake             | Centralized + Hybrid | Independent      | High          | Data Warehousing               |
| Lambda                | Decentralized        | Combined         | High          | Big Data Analytics             |
| Kappa                 | Decentralized        | Stream-Only      | High          | Real-Time Analytics            |
| Federated             | Distributed Sources  | Combined         | Limited       | Heterogeneous Data Integration |
| Clustered             | Shared or Distributed| Shared or Independent| Moderate | Parallel Processing            |

