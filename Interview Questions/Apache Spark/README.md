# Apache Spark Interview Questions and Answers

## Q1. What is Apache Spark?
Apache Spark is an open-source, wide-range data processing engine. It is a data processing engine with high-level APIs that allows data workers to execute streaming, machine learning, or SQL workloads. These jobs require fast, iterative access to datasets. Spark provides APIs in various languages like Python, R, Scala, and Java. Spark can be run standalone or on various cluster managers such as Standalone Deploy Mode, Apache Mesos, and Hadoop YARN.

The dynamic design of Spark allows integration with all Big Data tools. For example, Spark can access data from Hadoop data sources and run in a Hadoop cluster. However, Spark does not have its own storage system; it relies on HDFS or other file storage systems for data storage.

## Q2. Why did Spark come into existence?
Spark was developed to overcome the drawbacks of Apache Hadoop. Some of these drawbacks include:
- **Java-only applications:** Hadoop only supported Java, which posed security risks due to Java’s vulnerability to cyber crimes.
- **Batch processing only:** Hadoop did not support stream processing, a limitation overcome by Spark.
- **Disk-based processing:** Hadoop's disk-based data processing was slow, but Spark’s in-memory computation improves speed.

## Q3. What are the features of Apache Spark?
- **High processing speed:** Spark processes data much faster than other Big Data solutions.
- **Dynamic nature:** With 80+ high-level operators, it allows the creation of parallel applications.
- **Reusable code:** Code can be reused for joining streams with historical data or for batch processing.
- **Fault tolerance:** Through RDDs (Resilient Distributed Datasets), Spark provides data recovery and fault tolerance.
- **Multi-language support:** Spark supports Java, Scala, Python, and R, making it user-friendly and flexible.
- **Independent or cluster mode operation:** Spark can run independently or on cluster managers such as Hadoop YARN.
- **Cost-effective:** Compared to Hadoop, Spark is a cost-effective solution for Big Data problems, requiring less storage and fewer data centers.

## Q4. What are the limitations of Spark?
- **No file management system:** Spark requires integration with Hadoop or other cloud-based data platforms for storage.
- **In-memory capability bottlenecks:** Spark’s in-memory processing can be costly, particularly for large datasets.
- **High memory consumption:** Spark consumes a lot of memory, and issues related to memory are not handled in a user-friendly way.
- **Limited MLlib algorithms:** Some algorithms, such as Tanimoto distance, are not available in Spark’s MLlib.

## Q5. List the languages supported by Apache Spark.
Apache Spark supports the following languages:
- Scala
- Java
- R
- Python

## Q6. In what cases does Apache Spark surpass Hadoop?
Apache Spark surpasses Hadoop in the following cases:
- **Speed:** With in-memory computation, Spark increases performance by 10x to 1000x compared to Hadoop.
- **Multi-language support:** Spark supports multiple languages for distributed application development, while Hadoop primarily supports Java.
- **Unified libraries:** Spark’s core integrates libraries that handle streaming, SQL, graphs, and machine learning workloads.
- **Micro-batching:** Spark supports near real-time processing through micro-batching, which Hadoop’s batch processing cannot handle.

## Q7. Compare Hadoop and Spark.

- **Cost Efficiency:**
  - Hadoop: Requires a large number of servers, storage, and data centers, making it expensive.
  - Spark: More cost-effective due to its in-memory processing capabilities.
  
- **Performance:**
  - Hadoop: Processes data from disk, which makes it slower.
  - Spark: Processes data in memory, speeding up iterative algorithms by 10x-100x.

- **Ease of Development:**
  - Hadoop: Supports distributed application development using Java.
  - Spark: Supports Java, Scala, Python, and R, and integrates all workloads (streaming, SQL, graphs, machine learning) into a single application.

- **Failure Recovery:**
  - Hadoop: Data is written to disk after every operation.
  - Spark: Data is stored in RDDs, which can be in memory or on disk, providing full recovery from failures.

- **File Management System:**
  - Hadoop: Has its own file management system, HDFS (Hadoop Distributed File System).
  - Spark: Relies on integrating with external file management systems like HDFS.

- **Computation Model:**
  - Hadoop: Uses batch processing.
  - Spark: Uses micro-batching, allowing for near real-time data processing.

- **Lines of Code:**
  - Hadoop: 2,300,000 lines of code.
  - Spark: 20,000 lines of code.

- **Caching:**
  - Hadoop: Disk-oriented, no caching.
  - Spark: Caches partial results in memory for faster computation.

- **Scheduler:**
  - Hadoop: Requires an external job scheduler like Azkaban or Oozie.
  - Spark: Has its own flow scheduler due to in-memory computation.

- **API:**
  - Hadoop: Has a strict, low-level API.
  - Spark: More flexible and productive by abstracting many low-level details.

- **Window Criteria:**
  - Hadoop: No support for streaming, hence no window criteria.
  - Spark: Supports time-based window criteria for streaming.

- **Speed:**
  - Spark executes jobs 10x to 100x faster than Hadoop MapReduce.

- **License:**
  - Both Hadoop and Spark are licensed under Apache License 2.0.

- **DAG (Directed Acyclic Graph):**
  - Hadoop: Data flow is a chain with no loops.
  - Spark: Supports cyclic data flow in machine learning algorithms, represented by a DAG.

- **Memory Management:**
  - Hadoop: Uses static or dynamic memory management.
  - Spark: Has automatic memory management.

- **Iterative Processing:**
  - Hadoop: No iterative processing.
  - Spark: Supports iterative processing, where data iterates in batches.

- **Latency:**
  - Hadoop: Slower due to disk-based processing.
  - Spark: Faster due to RDDs caching data in memory, resulting in lower latency.

