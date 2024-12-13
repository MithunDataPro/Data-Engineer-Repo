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

# Snowflake Architecture - Cloud Service Layer Breakdown

Snowflake's architecture is divided into **three main layers**: **Cloud Services Layer**, **Storage Layer**, and **Compute Layer**. Below is a detailed explanation of the **Cloud Services Layer** and its components.

---

## **Cloud Services Layer**
The **Cloud Services Layer** is the brain of Snowflake. It manages authentication, access control, metadata, query optimization, and more.

### **1. Authentication & Access Control**
#### Authentication:
- Ensures that only authorized users can log in to the Snowflake Data Warehouse.
- Verifies if the user is the correct and legitimate user.

#### Access Control:
- Controls and limits access to data based on the **role** and **need** of the user.
- Enforces data governance, ensuring that data engineers, data scientists, or other users access only the data they need.

---

### **2. Infrastructure Manager**
- Allows users to **scale up** or **scale down** resources dynamically based on workload requirements.
- Provides a **Web UI** for easy configuration and management of infrastructure.

---

### **3. Optimizer**
- Automatically optimizes SQL queries to enhance performance.
- Chooses the most efficient execution plan by analyzing:
  - **Query structure**
  - **Available metadata**
  - **Statistics about data**

---

### **4. Transaction Manager**
- Manages all transactions performed on Snowflake data.
- Ensures **ACID compliance**:
  - **Atomicity:** Transactions are all-or-nothing.
  - **Consistency:** Ensures valid states after a transaction.
  - **Isolation:** Concurrent transactions do not interfere.
  - **Durability:** Committed transactions are saved even during failures.

---

### **5. Security & Results Cache**
#### Security:
- Provides **end-to-end encryption** for data in transit and at rest.
- Ensures data is protected from unauthorized access.

#### Results Cache:
- Caches query results to improve performance.
- When the same query is run again, Snowflake retrieves the results directly from the cache instead of re-executing the query.
- Significantly reduces query response time.

---

### **6. Metadata Storage**
- Stores information about tables, schemas, and other database objects.
- Saves time by providing precomputed information instead of recalculating it every time a query runs.
- Supports query planning and optimization.

---

## **Summary**
The **Cloud Services Layer** in Snowflake is critical for managing operations and improving performance. Here is a breakdown of its main components:

| Component             | Functionality                                                                                   |
|-----------------------|------------------------------------------------------------------------------------------------|
| Authentication        | Verifies user identity during login.                                                           |
| Access Control        | Limits access to data based on user roles and responsibilities.                                |
| Infrastructure Manager| Allows scaling of resources through the Web UI.                                               |
| Optimizer             | Automatically optimizes queries for efficient execution.                                       |
| Transaction Manager   | Manages data transactions and ensures ACID compliance.                                         |
| Security              | Provides encryption to protect data in transit and at rest.                                    |
| Results Cache         | Stores query results to speed up repeat queries.                                               |
| Metadata Storage      | Stores precomputed metadata to save time and support query optimization.                       |

### **Conclusion**
The **Cloud Services Layer** integrates various functionalities like security, scalability, optimization, and transaction management, making Snowflake a highly efficient and user-friendly data warehousing solution.

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

