# NoSQL DataBase:

NoSQL databases are a class of database management systems that differ from traditional relational databases (RDBMS) in their data models, scalability, and flexibility. The term "NoSQL" stands for "Not Only SQL," highlighting that these databases can handle a wide variety of data models beyond the relational model. They are designed to store, retrieve, and manage large volumes of unstructured, semi-structured, or rapidly changing data.

## Types of NoSQL Databases and Their Detailed Explanations with Use Cases

NoSQL databases are generally categorized into four primary types: 
1. **key-value stores**
2. **document databases**
3. **column-family stores**
4. **graph databases**

 Each type is optimized for specific data models and use cases.

## Key-Value Stores

### Description:

Key-value stores are the simplest type of NoSQL databases. They store data as a collection of key-value pairs, where a unique key is associated with a value. The value can be any type of data, such as a string, JSON document, or even a binary object.

### Examples:

- **Redis**
- **Amazon DynamoDB**
- **Riak**

### Use Cases:

- **Caching**: Store frequently accessed data for quick retrieval to improve application performance.
- **Session Management**: Manage user sessions in web applications efficiently.
- **Real-Time Analytics**: Handle high-speed read and write operations for live data feeds.
- **Shopping Cart Data**: Maintain shopping cart details in e-commerce platforms.

### Detailed Explanation:

#### Redis:

- **What It Is**: An open-source, in-memory data structure store that can be used as a database, cache, and message broker.
- **Features**: Supports various data structures like strings, hashes, lists, sets, sorted sets with range queries, bitmaps, and geospatial indexes.
- **Use Cases**: Ideal for applications requiring rapid data access, such as leaderboards, real-time analytics, and messaging queues.
- **Companies Using Redis**:
  - Twitter uses Redis for caching and real-time analytics.
  - GitHub employs it for queuing and background job processing.


### 1. What is Redis?

**Redis (Remote Dictionary Server)** is an open-source, in-memory data structure store that can be used as a database, cache, and message broker. It supports various data structures such as strings, hashes, lists, sets, and sorted sets. Redis is known for its high performance and is often used in scenarios where low-latency and fast data access are critical.

![image](https://github.com/user-attachments/assets/f3251b56-d7f9-4535-8da6-ae8d5b30da41)


#### Key Features:
- **In-Memory Data Store:** Redis stores the entire dataset in memory, making it extremely fast for read and write operations.
- **Persistence Options:** Redis provides different levels of persistence, such as snapshotting and append-only file (AOF) mode, to save data to disk.
- **Data Structures Support:** It supports a variety of advanced data structures like lists, sets, bitmaps, and geospatial indexes.
- **High Availability:** Redis supports replication, allowing data to be copied across multiple Redis nodes for high availability.
- **Pub/Sub Messaging:** Redis has built-in publish/subscribe messaging functionality, which can be used for real-time messaging between different parts of an application.

#### Use Cases:
- **Caching:** Redis is frequently used as a caching layer in applications to store frequently accessed data like user sessions, API responses, and product catalog data.
- **Real-Time Analytics:** Applications that require real-time data aggregation, such as live dashboards or recommendation systems, can benefit from Redis’s fast read and write capabilities.
- **Session Management:** In web applications, Redis is often used to store user session data for fast retrieval.
- **Message Queues:** Redis can be used as a message broker for building real-time applications such as chat services or streaming platforms.

#### Companies Using Redis:
- **Twitter:** For real-time analytics and caching.
- **GitHub:** For background job processing and queuing.
- **Pinterest:** For user session management and feed generation.

#### Advantages:
- **Fast:** In-memory storage makes Redis one of the fastest databases available for low-latency use cases.
- **Supports Multiple Data Types:** Unlike key-value stores that support only basic key-value pairs, Redis supports complex data types.
- **Highly Available:** Supports replication and automatic failover, ensuring high availability.
- **Extensive Ecosystem:** Redis has a rich ecosystem of tools, libraries, and integrations.

#### Disadvantages:
- **Memory-Dependent:** Since Redis stores data in memory, it can be expensive to scale for large datasets.
- **Limited Querying:** Redis does not support complex querying or joins like traditional relational databases.
- **Data Persistence:** Although Redis provides persistence options, it’s primarily an in-memory store, which makes it less suitable for applications that need full durability guarantees.

---

### 2. What is Amazon DynamoDB?

**Amazon DynamoDB** is a fully managed, key-value and document NoSQL database service provided by Amazon Web Services (AWS). DynamoDB is designed to deliver fast and predictable performance at any scale, making it ideal for applications with high throughput and low-latency requirements.

![image](https://github.com/user-attachments/assets/2d11fd7e-dcb7-4739-99cf-5b7d9401f3ca)


#### Key Features:
- **Fully Managed:** DynamoDB is a serverless database, which means AWS handles all the infrastructure, scaling, backups, and performance management.
- **Automatic Scaling:** DynamoDB automatically scales up or down based on the application’s traffic and workload, ensuring consistent performance.
- **Global Tables:** Supports multi-region, fully replicated tables that allow applications to run seamlessly across multiple AWS regions.
- **TTL (Time to Live):** Allows for automatic deletion of data after a specified period, which is useful for managing data lifecycle.
- **DynamoDB Streams:** Allows applications to respond to changes in data (inserts, updates, and deletes) in near real-time.

#### Use Cases:
- **Mobile and Web Applications:** DynamoDB is ideal for storing user data, session data, and preferences for mobile or web applications.
- **E-commerce Platforms:** DynamoDB is often used to handle product catalogs, order history, and shopping carts, where high availability and scalability are important.
- **IoT Data Storage:** It can store and process large volumes of data generated by IoT devices in real time.
- **Gaming Applications:** DynamoDB is used in gaming backends to store player data, game states, and leaderboards.

#### Companies Using DynamoDB:
- **Amazon:** Uses DynamoDB to power the shopping cart, customer preferences, and order history in its retail website.
- **Airbnb:** DynamoDB helps Airbnb handle user sessions and reservation data at a global scale.
- **Samsung:** Uses DynamoDB for IoT applications and real-time data processing.

#### Advantages:
- **Fully Managed Service:** Developers don’t need to worry about managing servers, scaling, or backups.
- **Scalable:** Automatically scales based on traffic, making it ideal for applications with unpredictable or varying workloads.
- **High Availability:** DynamoDB is designed for high availability and fault tolerance, with automatic data replication across multiple AWS regions.
- **Low Latency:** Optimized for high-speed read and write operations, even at large scales.

#### Disadvantages:
- **Cost:** While DynamoDB offers great scalability, the cost can be high, especially if not optimized properly for high throughput applications.
- **Limited Query Flexibility:** It supports basic query operations but lacks the advanced querying capabilities of relational databases.
- **Vendor Lock-In:** Since DynamoDB is a managed AWS service, migrating away from it to another database can be complex.

---

### 3. What is Riak?

**Riak** is a distributed NoSQL database designed to provide high availability, fault tolerance, and scalability. It is a key-value store that emphasizes availability over consistency, following the principles of the **CAP theorem**. Riak is built to be highly resilient and to ensure data availability even in the face of hardware failures.

![image](https://github.com/user-attachments/assets/0693ed1b-ba78-41b6-b6e0-6fbe88911d1c)


#### Key Features:
- **High Availability:** Riak is designed to be highly available and partition tolerant. It uses consistent hashing to distribute data across multiple nodes, ensuring that the system can continue to operate even when some nodes are down.
- **Eventual Consistency:** Riak follows an eventually consistent model, meaning that while data may not be immediately consistent across all nodes, it will eventually become consistent.
- **Scalability:** Riak is built to scale horizontally, meaning more nodes can be added to handle larger datasets and increased traffic.
- **Replication:** Data in Riak is replicated across multiple nodes, providing redundancy and fault tolerance.
- **Multi-Data Center Replication:** Riak supports multi-datacenter replication, making it suitable for globally distributed applications.

#### Use Cases:
- **Fault-Tolerant Applications:** Riak is ideal for use cases where uptime is critical, and the system must continue to function even if some nodes fail.
- **Distributed Systems:** Riak’s architecture is built for distributed systems where data is spread across multiple locations.
- **Gaming and Social Media Applications:** Applications that require high throughput, fast response times, and high availability can benefit from Riak’s architecture.

#### Companies Using Riak:
- **The Weather Company:** Uses Riak to store and process massive amounts of real-time weather data.
- **Basho (developer of Riak):** Uses Riak in several internal and external services to ensure fault tolerance and high availability.

#### Advantages:
- **High Availability:** Riak’s focus on availability means that applications built on Riak can continue to operate even during network partitions or hardware failures.
- **Scalability:** Designed for horizontal scalability, allowing it to handle large datasets and high traffic.
- **Fault Tolerance:** Data is replicated across multiple nodes, ensuring that the system can recover from node failures.
- **Flexible Data Model:** Riak can store various types of data, from simple key-value pairs to more complex objects.

#### Disadvantages:
- **Eventual Consistency:** Riak sacrifices immediate consistency for high availability, which may not be suitable for applications that require strong consistency.
- **Complexity:** Managing and configuring Riak can be more complex compared to simpler NoSQL databases.
- **Less Active Development:** Riak's community and development have slowed down, leading some companies to move towards more actively maintained databases.

---

### Comparison Table

| **Database**   | **Type**                | **Use Cases**                                      | **Advantages**                                  | **Disadvantages**                               |
|----------------|-------------------------|---------------------------------------------------|-------------------------------------------------|------------------------------------------------|
| **Redis**      | Key-Value Store          | Caching, Session Management, Real-Time Analytics   | In-Memory Speed, Supports Complex Data Types    | Memory Dependent, Limited Querying             |
| **Amazon DynamoDB** | Key-Value/Document Store | Mobile Apps, IoT Data, E-Commerce                   | Fully Managed, Auto-Scaling, Global Tables      | Costly at Scale, Limited Query Flexibility     |
| **Riak**       | Key-Value Store          | Distributed Systems, Fault-Tolerant Applications   | High Availability, Fault Tolerance, Scalability | Eventual Consistency, Complexity               |


## Document Databases

### Description:

Document databases store data in documents similar to JSON (JavaScript Object Notation) or XML formats. Each document contains semi-structured data that can vary in structure, allowing for flexibility in data modeling.

### Examples:

- **MongoDB**
- **Couchbase**
- **Amazon DocumentDB**

### Use Cases:

- **Content Management Systems (CMS)**: Handle unstructured content like articles, blog posts, and multimedia.
- **User Profiles**: Store varying user data without a fixed schema.
- **E-commerce Platforms**: Manage product catalogs where items have different attributes.
- **Mobile Applications**: Support flexible and rapidly changing data structures.

### Detailed Explanation:

#### MongoDB:

- **What It Is**: A cross-platform, document-oriented database program that uses JSON-like documents with optional schemas.
- **Features**: Supports ad-hoc queries, indexing, replication, and load balancing.
- **Use Cases**: Ideal for applications requiring high scalability and flexibility, such as content management, real-time analytics, and big data.
- **Companies Using MongoDB**: 
  - eBay uses it for search suggestions.
  - Adobe employs it for content management systems.


### What is MongoDB?

**MongoDB** is an open-source, NoSQL document-oriented database that stores data in flexible, JSON-like documents. This makes it suitable for applications where the structure of data may change frequently or where the data itself is unstructured or semi-structured.

![image](https://github.com/user-attachments/assets/6f2790cc-7562-4fed-bcfc-3d33a87aa3e4)

#### Key Features:
- **Schema-less:** MongoDB doesn’t enforce a fixed schema, allowing documents to have varying fields and structures.
- **Document Storage:** Uses BSON (binary-encoded JSON) format to store documents, supporting nested fields and arrays.
- **Ad-hoc Queries:** Supports rich queries, including field, range queries, and regular expression searches.
- **Indexing:** MongoDB provides various indexing options like compound indexes, text indexes, and geospatial indexes to optimize query performance.
- **Horizontal Scalability:** MongoDB can scale out by distributing data across multiple servers using a feature called sharding.
- **Replication:** Provides high availability and redundancy through replica sets, where data is replicated across multiple nodes.

#### Use Cases:
- **Content Management Systems (CMS):** MongoDB is widely used to manage unstructured content such as blog posts, news articles, and multimedia.
- **E-commerce Platforms:** It can handle product catalogs where items have varying attributes (e.g., clothing, electronics) without predefined schemas.
- **Mobile and Web Applications:** Ideal for applications that handle large volumes of unstructured or semi-structured data, such as user profiles or app logs.
- **Real-Time Analytics:** MongoDB is used in real-time applications that need to process large volumes of dynamic data, such as recommendation engines or analytics dashboards.

#### Companies Using MongoDB:
- **eBay:** Uses MongoDB to power search suggestions.
- **Adobe:** Implements MongoDB for content personalization and data management.
- **Forbes:** Utilizes MongoDB to manage real-time article recommendations.

#### Advantages:
- **Flexible Data Model:** MongoDB’s document-oriented structure allows storing data in a flexible, dynamic schema.
- **Horizontal Scalability:** Sharding enables MongoDB to handle large datasets by distributing them across multiple servers.
- **Rich Query Language:** Supports complex queries with filtering, sorting, and aggregation capabilities.
- **High Availability:** Replica sets ensure data is available even if one or more nodes fail.

#### Disadvantages:
- **Memory Usage:** Since MongoDB stores data in BSON format, it can consume more memory compared to relational databases.
- **Limited Transaction Support (Earlier Versions):** Transactions across multiple documents were not supported until MongoDB 4.0, making it less suitable for certain use cases where ACID compliance is required.
- **Indexing Limitations:** Large datasets with multiple indexes can lead to performance bottlenecks.

---

### What is Couchbase?

**Couchbase** is a distributed NoSQL database that combines the capabilities of a key-value store with a document store. It is designed to provide high performance and scalability for modern web, mobile, and IoT applications. Couchbase supports a flexible schema and provides powerful querying capabilities, along with built-in full-text search and analytics.

![image](https://github.com/user-attachments/assets/54519c31-8a09-4f9c-9ec5-b854508fcfaa)

#### Key Features:
- **Document Store:** Couchbase stores data as JSON documents, allowing flexible data modeling and easy integration with modern applications.
- **Key-Value Store:** For use cases requiring ultra-fast lookups, Couchbase operates as a key-value store, ensuring low-latency access to data.
- **N1QL Query Language:** Couchbase provides N1QL, an SQL-like query language, which allows developers to run rich queries on JSON documents.
- **Replication and High Availability:** Couchbase ensures high availability with data replication across nodes. It also supports multi-node clusters to handle failover automatically.
- **Built-in Full-Text Search:** Provides native support for full-text search capabilities, making it easy to perform text-based searches across documents.
- **Mobile Integration:** Couchbase has built-in synchronization support for mobile and IoT applications through Couchbase Mobile, ensuring offline-first capabilities.

#### Use Cases:
- **Mobile Applications:** Couchbase supports real-time syncing and offline data storage, making it ideal for mobile apps that need to function without internet connectivity.
- **E-commerce Platforms:** Couchbase’s low-latency operations and scalability make it suitable for handling shopping carts, product catalogs, and user sessions.
- **Gaming Applications:** With Couchbase’s low-latency and high throughput, it is often used in gaming backends to store game states, leaderboards, and user data.
- **IoT Data Management:** Couchbase’s distributed architecture and high availability make it ideal for managing large-scale IoT data, where devices generate a continuous stream of data.

#### Companies Using Couchbase:
- **LinkedIn:** Uses Couchbase to handle data for real-time notifications and content feeds.
- **PayPal:** Implements Couchbase for user session storage and fraud detection.
- **Viber:** Utilizes Couchbase for real-time messaging and syncing between devices.

#### Advantages:
- **Low Latency and High Performance:** Couchbase is optimized for performance with in-memory caching and distributed architecture, making it ideal for real-time applications.
- **SQL-Like Querying:** N1QL provides developers with the familiarity of SQL while allowing them to query JSON documents efficiently.
- **Mobile Syncing:** Couchbase Mobile enables syncing between the server and mobile devices, supporting offline functionality.
- **Flexible Data Model:** Supports both key-value operations and document-based queries, making it versatile for various use cases.

#### Disadvantages:
- **Complex Setup:** Setting up and managing Couchbase clusters can be more complex than simpler NoSQL databases.
- **High Resource Usage:** Couchbase’s in-memory architecture can consume significant memory and CPU resources, especially for larger datasets.
- **Query Performance:** Complex queries can lead to performance issues when the dataset grows, particularly if indexing is not optimized.

---

### What is Amazon DocumentDB?

**Amazon DocumentDB** is a managed document database service that is compatible with MongoDB. It is optimized for storing, querying, and indexing JSON documents. Amazon DocumentDB provides scalability, high availability, and data durability in the AWS cloud environment, making it ideal for handling large volumes of semi-structured data.

![image](https://github.com/user-attachments/assets/09e5658c-7dea-4e67-9f2c-33e430f0770e)

#### Key Features:
- **MongoDB Compatibility:** Amazon DocumentDB is designed to be compatible with MongoDB, allowing users to migrate their MongoDB applications to Amazon DocumentDB without changing code or drivers.
- **Managed Service:** As part of AWS, Amazon DocumentDB is fully managed, with automatic backups, scaling, and patching.
- **Horizontal Scaling:** The database can automatically scale storage and compute resources as needed, providing flexibility for growing applications.
- **High Availability:** Amazon DocumentDB automatically replicates data across three availability zones, ensuring high availability and durability.
- **Backup and Restore:** Supports continuous backups with point-in-time recovery, allowing users to restore data to any second within the retention window.

#### Use Cases:
- **Content Management Systems (CMS):** Amazon DocumentDB is ideal for storing and managing unstructured content such as articles, blog posts, and multimedia.
- **Mobile and Web Applications:** It provides high availability and scalability for mobile and web apps that rely on dynamic, semi-structured data.
- **IoT Data Storage:** DocumentDB is suitable for IoT applications where devices produce semi-structured data that needs to be processed in real-time.
- **Gaming Platforms:** It can store game-related data such as user profiles, game states, and high scores, with fast access for real-time gameplay.

#### Companies Using Amazon DocumentDB:
- **Sony:** Uses Amazon DocumentDB for handling data in its video game platform.
- **Comcast:** Employs DocumentDB for content management in its streaming services.
- **Zillow:** Utilizes Amazon DocumentDB to store and process real estate data in JSON format.

#### Advantages:
- **Fully Managed:** Amazon DocumentDB handles backups, patching, scaling, and replication, freeing developers from the burden of managing infrastructure.
- **Scalable:** It can handle large amounts of data and scale seamlessly, ensuring performance as the dataset grows.
- **MongoDB-Compatible:** Developers familiar with MongoDB can easily transition to Amazon DocumentDB, as it uses the same APIs and drivers.
- **High Availability:** With data replicated across multiple availability zones, Amazon DocumentDB ensures that applications remain highly available.

#### Disadvantages:
- **Limited MongoDB Features:** While compatible with MongoDB, some features of MongoDB, such as certain aggregation functions and distributed transactions, are not supported in DocumentDB.
- **AWS Lock-In:** Since Amazon DocumentDB is a managed service within AWS, migrating data out of DocumentDB can be challenging and costly.
- **Cost:** Pricing can become expensive for large-scale applications due to the managed service fees and storage costs.

---

### Comparison Table

| **Database**             | **Type**                | **Use Cases**                                      | **Advantages**                                  | **Disadvantages**                               |
|--------------------------|-------------------------|---------------------------------------------------|-------------------------------------------------|------------------------------------------------|
| **MongoDB**              | Document Store           | CMS, E-commerce, Real-Time Analytics               | Flexible Schema, Horizontal Scalability         | Memory Usage, Limited Transaction Support       |
| **Couchbase**            | Key-Value & Document Store| Mobile Apps, IoT, E-commerce, Gaming               | Low Latency, N1QL Query Language, Mobile Syncing| Complex Setup, High Resource Usage             |
| **Amazon DocumentDB**    | Managed Document Store    | CMS, Mobile Apps, IoT, Gaming                     | Fully Managed, MongoDB-Compatible, Scalable     | Limited MongoDB Features, AWS Lock-In           |


## 3. Column-Family Stores

### Description:

Column-family stores organize data into columns and column families rather than traditional rows. This allows for efficient storage and retrieval of large datasets and is particularly well-suited for distributed systems.

### Examples:

- **Apache Cassandra**
- **Apache HBase**
- **Google Bigtable**

### Use Cases:

- **Time-Series Data**: Store sensor data, logs, and financial transactions over time.
- **Event Logging**: Record high volumes of events with low latency.
- **Real-Time Analytics**: Perform quick read and write operations on massive datasets.
- **Messaging Systems**: Handle large-scale messaging and notification systems.

### Detailed Explanation:

#### Apache Cassandra:

- **What It Is**: An open-source, distributed NoSQL database management system designed to handle large amounts of data across many commodity servers.
- **Features**: Offers high availability with no single point of failure, linear scalability, and fault tolerance.
- **Use Cases**: Ideal for applications that require high write and read throughput, such as social media platforms, IoT applications, and real-time analytics.
- **Companies Using Cassandra**: 
  - Netflix uses it for its scalability and fault tolerance.
  - Apple employs it to manage massive amounts of data.

---

## 4. Graph Databases

### Description:

Graph databases use graph structures with nodes, edges, and properties to represent and store data. They are designed to handle data whose relations are well represented as a graph, making them ideal for interconnected data.

### Examples:

- **Neo4j**
- **Amazon Neptune**
- **OrientDB**

### Use Cases:

- **Social Networks**: Model and analyze relationships between users, such as friendships and followers.
- **Recommendation Engines**: Discover relationships between products and users for personalized recommendations.
- **Fraud Detection**: Identify complex patterns and anomalies in transactional data.
- **Knowledge Graphs**: Manage and query interconnected data in domains like research and development.

### Detailed Explanation:

#### Neo4j:

- **What It Is**: An open-source graph database that uses nodes, relationships, and properties to represent and store data.
- **Features**: Supports ACID transactions, high-availability clustering, and a declarative query language called Cypher.
- **Use Cases**: Ideal for applications requiring complex relationship mapping, such as social networks, fraud detection systems, and recommendation engines.
- **Companies Using Neo4j**:
  - Walmart utilizes it for supply chain management.
  - eBay employs it for social graph analysis.


1. **Apache Cassandra:**  
   - A distributed NoSQL database designed for handling large amounts of data across many commodity servers, providing high availability with no single point of failure.
   
2. **MongoDB:**  
   - A document-oriented NoSQL database that uses JSON-like documents with optional schemas, making it highly flexible and suitable for diverse data structures.
   
3. **Amazon DynamoDB:**  
   - A fully managed NoSQL database service by AWS that provides fast and predictable performance with seamless scalability.

4. **Couchbase:**  
   - A distributed NoSQL document-oriented database with a flexible data model, consistent high performance, and easy scalability.

5. **Redis:**  
   - An in-memory NoSQL key-value store that supports various data structures such as strings, hashes, lists, sets, and more, known for its speed and versatility.

6. **Neo4j:**  
   - A graph database management system that uses graph structures for semantic queries, ideal for connected data and network analysis.

7. **Elasticsearch:**  
   - A distributed, RESTful search and analytics engine capable of storing and indexing large volumes of data, often used for log or event data.

8. **HBase:**  
   - A distributed, scalable NoSQL database built on top of HDFS (Hadoop Distributed File System), suitable for random, real-time read/write access to big data.

9. **Amazon DocumentDB:**  
   - A fully managed document database service that is MongoDB-compatible, designed for scaling, managing, and retrieving document data.

10. **Azure Cosmos DB:**  
    - A globally distributed, multi-model NoSQL database service from Azure, supporting document, key-value, graph, and column-family data models.

11. **CouchDB:**  
    - An open-source NoSQL document database that uses JSON for documents, JavaScript for MapReduce queries, and HTTP for an API.

12. **Riak:**  
    - A distributed NoSQL key-value database designed for scalability, high availability, and fault tolerance.

13. **ArangoDB:**  
    - A multi-model database that supports document, graph, and key/value data models, designed for flexibility and ease of use.

14. **OrientDB:**  
    - A multi-model database that supports graph, document, key/value, and object models, making it versatile for different use cases.

15. **Amazon Neptune:**  
    - A fully managed graph database service by AWS that supports both the property graph model and RDF model, optimized for graph applications.

---

### SQL Databases

SQL databases, also known as relational databases, use structured query language (SQL) for defining and manipulating data. They are ideal for applications requiring structured data with defined relationships.

1. **MySQL:**  
   - An open-source relational database management system (RDBMS) that uses SQL for accessing and managing data, widely used for web applications.

2. **PostgreSQL:**  
   - An open-source, object-relational database management system (ORDBMS) with an emphasis on extensibility and SQL compliance.

3. **Microsoft SQL Server:**  
   - A relational database management system developed by Microsoft, designed for enterprise-level applications with strong integration with other Microsoft products.

4. **Oracle Database:**  
   - A multi-model database management system produced by Oracle Corporation, widely used for enterprise applications, known for its reliability and robustness.

5. **SQLite:**  
   - A self-contained, serverless, zero-configuration, transactional SQL database engine, commonly used for embedded database applications.

6. **MariaDB:**  
   - An open-source relational database management system that is a fork of MySQL, offering additional features and improved performance.

7. **IBM Db2:**  
   - A family of data management products, including database servers, developed by IBM. Known for handling large-scale data and transactional workloads.

8. **Amazon Aurora:**  
   - A MySQL and PostgreSQL-compatible relational database built for the cloud, combining the performance and availability of high-end commercial databases with the simplicity and cost-effectiveness of open-source databases.

9. **Google Cloud SQL:**  
   - A fully managed relational database service on Google Cloud Platform, supporting MySQL, PostgreSQL, and SQL Server.

10. **SAP HANA:**  
    - An in-memory, column-oriented, relational database management system developed by SAP, used for high-performance analytics and transactional processing.

11. **Teradata:**  
    - A fully scalable relational database management system typically used for large data warehousing applications.

12. **Amazon Redshift (also supports NoSQL functionality):**  
    - A fully managed data warehouse service on AWS that supports SQL-based queries for large datasets.

13. **Azure SQL Database:**  
    - A fully managed relational database with built-in intelligence designed for cloud-based applications, offered as part of the Microsoft Azure platform.

14. **NuoDB:**  
    - A SQL-compliant distributed database management system designed to scale out without sacrificing SQL consistency or transactional integrity.

15. **CockroachDB:**  
    - A distributed SQL database designed for cloud infrastructure with strong consistency and horizontal scalability.

16. **Firebird:**  
    - An open-source SQL relational database management system that runs on Linux, Windows, and several Unix platforms.

17. **InterBase:**  
    - A lightweight, full-featured SQL database engine designed for embedded and small-to-medium enterprise applications.

18. **Sybase (SAP ASE):**  
    - A relational model database server designed primarily to run transaction-based applications.

---

This Markdown content provides a categorized overview of NoSQL and SQL databases, highlighting their primary uses and capabilities.
