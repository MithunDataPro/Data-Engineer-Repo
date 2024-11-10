# Snowflake - Data Architecture:

**Snowflake** data architecture re-invents a new SQL query engine. It is designed for the cloud only. Snowflake doesn't utilize or built on top of any existing database technology. It doesn't even use big data software platforms like Hadoop. Snowflake provides all functionalities of an analytical database plus numbers of additional unique features and capabilities to users.

Snowflake has central data repository for storage of structured and semi-structured data. These data can be accessed from all available compute nodes in the Snowflake platform. It uses virtual warehouse as compute environment for processing the queries. While processing queries, it utilizes multi-cluster, micro-partitioning and advanced cache concepts. Snowflake's cloud services are responsible to provide end to end solution to the user like logging validation of user to result of select queries.

---

Snowflake's data architecture **has three main layers** −

- Database Storage
- Query Processing
- Cloud Services

Following is the **data architecture** diagram of Snowflake −

![image](https://github.com/user-attachments/assets/b448535a-e2c1-45d1-af46-0f09560c54a0)

---

## Database Storage:

**Snowflake** supports Amazon S3, Azure and Google Cloud to load data into Snowflake using file system. User should upload a file (.csv, .txt, .xlsx etc.) into the cloud and after they create a connection in Snowflake to bring the data. Data size is unlimited, but file size is up to 5GB as per cloud services. Once data is loaded into Snowflake, it utilizes its internal optimization and compression techniques to store the data into central repository as columnar format. The central repository is based on cloud where data stores.

Snowflake owns responsibilities to all aspects of data management like how data is stored using automatic clustering of data, organization and structure of data, compression technique by keeping data into many micro-partitions, metadata, statistics and many more. Snowflake stores data as data objects and users can't see or access them directly. Users can access these data through SQL queries either in Snowflake's UI or using programming language like Java, Python, PHP, Ruby etc.

---

## Query Processing:

Query execution is a part of processing layer or compute layer. To process a query, Snowflake requires compute environment, known as "Virtual Warehouse" in Snowflake's world. Virtual warehouse is a compute cluster. A virtual warehouse consists of CPU, Memory and temporary storage system so that it could perform SQL execution and DML (Data Manipulation Language) operations.

- SQL SELECT executions

- Updating of data using Update, Insert, Update

- Loading data into tables using COPY INTO <tables>

- Unloading data from tables using COPY INTO <locations>

However, the number of servers depends on size of virtual warehouses. For example, XSmall warehouse has 1 Server per cluster, while a Small Warehouse has 2 Servers per cluster and it gets double on increasing the size such as Large, XLarge, etc.

While executing a query, Snowflake analyzes the requested query and uses the latest micro-partitions and evaluates caching at different stages to increase performance and decrease the time for bringing the data. Decrease the time means less credit is used of a user.

---

## Cloud Services:

Cloud Service is the 'Brain' of the Snowflake. It coordinates and manages activities across Snowflake. It brings all components of Snowflake together to process user requests from logging validation to deliver query's response.

**The following services are managed at this layer −**

- It is the centralized management for all storage.

- It manages the compute environments to work with storage.

- It is responsible for upgrades, updates, patching and configuration of Snowflake at cloud.

- It performs cost-based optimizers on SQL queries.

- It gathers statistics automatically like credit used, storage capacity utilization

- Security like Authentication, Access controls based on roles and users

- It performs encryption as well as key management services.

- It stores metadata as data is loaded into the system.

---

And many more...

