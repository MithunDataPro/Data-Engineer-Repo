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

---

![image](https://github.com/user-attachments/assets/443ed95d-90eb-4de0-988e-e6740c122c29)

## Q8. What are the components of the Spark Ecosystem?
The various components of Apache Spark are:
- **Spark Core**: Spark Core is the foundation of the entire project. All functionality in Spark is built on top of Spark Core.
- **Spark Streaming**: It allows fault-tolerant streaming of live data streams. Spark Streaming uses micro-batching to process real-time streaming data by dividing it into small batches.
- **Spark SQL**: A distributed framework for structured data processing. Spark SQL allows Spark to gain more information about the data's structure and computation, enabling optimization.
- **Spark MLlib**: A scalable machine learning library that includes high-quality algorithms and high-speed processing. MLlib makes machine learning scalable and easy to use.
- **Spark GraphX**: A graph processing API that supports parallel execution. GraphX contains fundamental operators like `subgraph` and `joinVertices` and supports tasks like clustering, classification, traversal, searching, and pathfinding.
- **SparkR**: Introduced in Apache Spark 1.4, SparkR allows data processing using R's DataFrame structure. The DataFrame concept is also extended to other languages like Pandas for Python.

## Q9. What is Spark Core?
Spark Core is the common execution engine for the entire Spark platform. It provides parallel and distributed processing for large datasets. The components of Spark are built on top of Spark Core, which provides speed through in-memory computation. Spark Core also supports APIs in Java, Scala, and Python.

RDD (Resilient Distributed Dataset) is the basic data structure of Spark Core. RDDs are immutable and partitioned collections of records that can be operated on in parallel. RDDs can be created by transformations on existing RDDs or by loading data from external storage like HDFS or HBase.

## Q10. How is data represented in Spark?
Data in Apache Spark can be represented in three ways:
- **RDD**: RDD stands for Resilient Distributed Datasets. It is a read-only partitioned collection of records and the fundamental data structure in Spark. RDDs can only be created through deterministic operations on either:
  - Data in stable storage.
  - Parallelizing an existing collection in the driver program.
  - Other RDDs.
  RDDs allow in-memory computation on large clusters in a fault-tolerant manner, speeding up tasks.
  
- **DataFrame**: Unlike an RDD, a DataFrame organizes data into named columns, similar to a table in a relational database. It is also an immutable, distributed collection of data that allows developers to impose structure on a distributed collection of data, enabling higher-level abstraction.

- **DataSet**: A Dataset is an extension of the DataFrame API. It provides a type-safe, object-oriented programming interface. Datasets also leverage Spark’s Catalyst optimizer by exposing expressions and data fields to a query planner.

## Q11. What are the abstractions of Apache Spark?
The main abstraction provided by Apache Spark is the **Resilient Distributed Dataset (RDD)**. RDDs are fault-tolerant and immutable. RDD creation begins with files in a file system, such as Hadoop, and then transformations are applied. 

Another abstraction provided by Spark is **shared variables**, which can be used in parallel operations.

## Q12. Explain the operations of Apache Spark RDD.
Apache Spark RDD supports two types of operations:
- **Transformations**: These are lazy operations that create one or more new RDDs, such as `map`, `filter`, or `reduceByKey`. Transformations create new datasets from existing ones and compute lazily, meaning they only execute when required.
  
- **Actions**: These operations trigger execution by returning a final result from RDD computations. Actions execute transformations using a lineage graph to load data into the original RDD, apply intermediate transformations, and give the final result to the driver program or file system.

## Q13. How many types of transformations are there?
There are two types of transformations in Apache Spark:
- **Narrow Transformation**: This transformation results from operations like `map` or `filter`, where the data required for computation comes from a single partition. The output RDD has a partition with records originating from a single partition in the parent RDD.
  
- **Wide Transformation**: These are transformations such as `groupByKey` or `reduceByKey`, where data required to compute records in a partition comes from multiple partitions of the parent RDD.

![image](https://github.com/user-attachments/assets/b8fd087e-41fc-4a35-950a-44905275a37b)

---

## Q14. In how many ways can RDDs be created? Explain.
There are three ways to create an RDD in Apache Spark:

- **Parallelized Collection**: 
  - In the initial stages, an RDD can be created from an existing collection in the program by passing it to the `parallelize()` method of `SparkContext`. 
  - The number of partitions should be noted; Spark will run one task per partition. The number of partitions can be set manually. For example:
    ```scala
    sc.parallelize(data, 20) // Manually sets the number of partitions to 20
    ```

- **External Datasets (Referencing a Dataset)**: 
  - An RDD can be created from any data source supported by Hadoop, such as local file systems, HDFS, Cassandra, HBase, etc. 
  - For example, to create an RDD from a text file, use the `SparkContext.textFile()` method:
    ```scala
    val rdd = sc.textFile("hdfs://path/to/file")
    ```

- **Creating RDD from an Existing RDD**: 
  - Transformations can convert one RDD into another. This means you can create an RDD from an existing RDD using transformation functions.

## Q15. What are Paired RDDs?
Paired RDDs are RDDs containing key-value pairs. A key-value pair (KVP) contains two linked data items:
- **Key**: The identifier.
- **Value**: The data corresponding to the key.

## Q16. What is meant by in-memory processing in Spark?
In-memory processing refers to storing data in random access memory (RAM) instead of slower disk drives. Data is processed in parallel, leading to:
- Increased processing speed as data is retrieved from memory rather than disk.
- Decreased execution time.

Spark’s RDDs support in-memory computation. You can cache or persist an RDD to store it in memory for faster retrieval. The difference between `cache()` and `persist()` lies in their default storage levels:
- **`cache()`**: Default storage level is `MEMORY_ONLY`.
- **`persist()`**: Offers different storage levels, such as:
  - `MEMORY_ONLY`
  - `MEMORY_AND_DISK`
  - `MEMORY_ONLY_SER`
  - `MEMORY_AND_DISK_SER`
  - `DISK_ONLY`

## Q17. How is fault tolerance achieved in Apache Spark?
Fault tolerance in Spark is achieved using the following principles:

- **Immutable RDDs**: Every RDD is immutable and tracks the lineage of deterministic operations that create it from fault-tolerant input datasets.
- **Recomputing Partitions**: If any partition of an RDD is lost due to a worker node failure, it can be re-computed from the original dataset using the lineage of operations.
- **Deterministic Transformations**: All RDD transformations are deterministic, so the final transformed RDD will be the same even if failures occur.

There are two ways data can be recovered in the event of a failure:
- **Data received and replicated**: Data is replicated across nodes, allowing retrieval in case of a failure.
- **Data received but not yet replicated**: If data is not replicated, it can only be recovered by retrieving it again from the source.

### Types of Failures:
- **Failure of Worker Node**: Worker nodes run application code on the cluster. If a worker node fails, the in-memory data may be lost. If receivers were running on the failed nodes, their buffered data will vanish.
- **Failure of Driver Node**: If the driver node running the Spark Streaming application fails, the SparkContext is lost, and all executors and their in-memory data are also lost.

![image](https://github.com/user-attachments/assets/66a67e23-f8eb-4c6b-87c8-7ff817372ed2)

---

## Q18. What is Directed Acyclic Graph (DAG)?
RDDs are formed after every transformation. At a high level, when an action is applied on RDDs, Spark creates a DAG. A DAG is a finite directed graph with no directed cycles. 
- It consists of vertices and edges where each edge is directed from one vertex to another. 
- The sequence of vertices ensures that every edge is directed from earlier to later in the sequence. 
- DAG is a generalization of the MapReduce model and allows Spark to provide stage-level execution details.
  
In the stage view, all RDDs that belong to a stage are expanded.

## Q19. What is a lineage graph?
A lineage graph refers to the graph that contains all the parent RDDs of an RDD. 
- It is the result of all transformations on an RDD and creates a logical execution plan.
- A logical execution plan begins with the first RDD and ends with the RDD that produces the result of an action.

## Q20. What is lazy evaluation in Spark?
Lazy evaluation (also known as call-by-need) is a strategy that delays execution until the value is needed. 
- In Spark, transformations are lazy, meaning they don’t execute immediately when called. 
- Instead, Spark maintains a graph of transformations and only executes them when an action is called.
- Data is not loaded until it is necessary.

## Q21. What are the benefits of lazy evaluation?
Lazy evaluation provides the following benefits:
- **Increases program manageability**.
- **Saves computation overhead** and increases system speed.
- **Reduces time and space complexity**.
- **Optimizes execution** by reducing the number of queries.

## Q22. What do you mean by persistence?
RDD persistence is an optimization technique that saves the result of RDD evaluation. 
- By persisting RDDs, the intermediate result is saved for future use, reducing computation overhead.
- RDDs can be persisted using `cache()` and `persist()` methods.
  
When an RDD is persisted, each node stores any partition of it in memory, making it reusable for future computations, speeding up further computations by ten times.

## Q23. Explain various levels of persistence in Apache Spark.
The `persist()` method allows seven levels of persistence:
- **MEMORY_ONLY**: Stores RDD as deserialized Java objects in memory. If RDD does not fit in memory, partitions are recomputed when needed.
- **MEMORY_AND_DISK**: Stores RDD as deserialized Java objects in memory and spills partitions that don't fit in memory to disk.
- **MEMORY_ONLY_SER (Java and Scala)**: Stores RDD as serialized Java objects, which are more space-efficient but harder for the CPU to read.
- **MEMORY_AND_DISK_SER (Java and Scala)**: Similar to `MEMORY_ONLY_SER`, but spills partitions that don't fit in memory to disk.
- **DISK_ONLY**: Stores RDD partitions only on disk.
- **MEMORY_ONLY_2, MEMORY_AND_DISK_2**: Replicates each partition on two cluster nodes.
- **OFF_HEAP**: Stores data in off-heap memory. Requires off-heap memory to be enabled.

## Q24. Explain the run-time architecture of Spark.
The run-time architecture of Spark consists of three main components:
1. **Driver**:
   - The `main()` method of the program runs in the driver.
   - The driver runs user code, creates RDDs, performs transformations and actions, and creates `SparkContext`.
   - The driver splits the Spark application into tasks and schedules them to run on executors.
2. **Cluster Manager**:
   - The cluster manager launches executors and, in some cases, drivers.
   - Spark depends on the cluster manager to schedule jobs within the application, either in FIFO or Round Robin fashion.
   - The resources used by a Spark application can be dynamically adjusted based on workload.
3. **Executors**:
   - Executors run tasks in the Spark job. They are launched at the start of the Spark application and run for the entire application lifetime.
   - Executors provide in-memory storage for RDDs and return results to the driver.

## Q25. Explain various cluster managers in Apache Spark.
Apache Spark supports the following cluster managers:
- **Standalone Cluster Manager**: 
  - A simple cluster manager that is easy to set up and run Spark applications in a clustered environment.
  - It consists of masters and workers, each with a configured amount of memory and CPU cores. Only one executor can be allocated per worker per application.
  
- **Hadoop YARN**:
  - YARN is a sub-project of Hadoop that manages resources and job scheduling. 
  - YARN uses a Resource Manager (RM) and per-application Application Master (AM) to manage resources.
  - The combination of the Resource Manager and Node Manager handles computation and execution.

- **Apache Mesos**:
  - Mesos handles workloads in a distributed environment and manages large-scale clusters.
  - It groups physical resources into a single virtual resource, reducing the overhead of allocating specific machines for different workloads.
  - Mesos is a resource management platform for Hadoop and Big Data clusters. It acts as the reverse of virtualization, grouping multiple physical resources into a single virtual resource.

![image](https://github.com/user-attachments/assets/f0745b46-9e5c-46de-9368-54eaf68c1fcd)


---
