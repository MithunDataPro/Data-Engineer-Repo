# Apache Sqoop Overview
**Apache Sqoop** is a **command-line interface application** used to transfer data between **relational databases** and **Hadoop**. It efficiently imports and exports large datasets between **Hadoop Distributed File System (HDFS)** and structured data stores like **relational databases (MySQL, Oracle, SQL Server, etc.)**. **Sqoop** automates the process, minimizing manual coding, and provides connectors for popular databases.


## Why Data Engineers Use Apache Sqoop

**Data engineers leverage Apache Sqoop for several reasons:**

- **Data Migration:** Efficiently migrates large datasets from relational databases to Hadoop for processing and analytics.
- **Batch Processing:** Integrates with batch processing engines like Hadoop's MapReduce, making it easy to handle high-volume data migration tasks.
- **ETL Pipeline:** Frequently used in Extract, Transform, Load (ETL) pipelines to ingest relational data into data lakes or distributed file systems.
- **Integration with BI Tools:** Provides connectors for Business Intelligence (BI) tools and other big data ecosystems, allowing seamless data movement.


## Key Features of Apache Sqoop:

- **Data Import and Export:** Transfers data between HDFS and relational databases (both ways).
- **Incremental Load:** Supports importing only new or updated data.
- **Parallelism:** Automatically uses parallel processing to speed up the data transfer.
- **Compression Support:** Supports data compression to optimize storage and performance.
- **Integration with Hive and HBase:** Allows direct loading of data into Apache Hive or HBase tables.

## How Apache Sqoop Works

- **Connectors:** Sqoop uses connectors to establish connections with relational databases (e.g., MySQL, Oracle) and transfer data.
- **Data Import:** sqoop import command fetches data from RDBMS and stores it into HDFS in a structured format like CSV or Avro.
- **Data Export:** sqoop export allows exporting data from Hadoop to relational databases for further processing or reporting.

### Example: Importing Data from MySQL to HDFS

```bash
sqoop import \
--connect jdbc:mysql://localhost/dbname \
--username yourUsername \
--password yourPassword \
--table yourTable \
--target-dir /hdfs/target_directory \
--num-mappers 4

```
---

### Example: Exporting Data from HDFS to MySQL

```bash
sqoop export \
--connect jdbc:mysql://localhost/dbname \
--username yourUsername \
--password yourPassword \
--table yourTable \
--export-dir /hdfs/source_directory

```
