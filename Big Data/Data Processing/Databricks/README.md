# Apache Spark with Databricks for Data Engineering..

## Introduction to Hadoop and Spark

### Hadoop
In 2006, a group of engineers at Yahoo developed a special software framework called Hadoop. They were inspired by Google MapReduce and Google File System technologies. 

Hadoop introduced a distributed computing system, where instead of using a single system, multiple systems work together. Each system processes a certain amount of data, and finally, they provide the same output.

#### Two Important Components in Hadoop:
1. HDFS
2. MapReduce
3. Yarn

#### Limitations of Hadoop:
1. **Disk-Based Storage**: Every time Hadoop runs, it stores data on disk, reads the data, processes the data, and then stores the data back on the disk. This makes data processing slower.
2. **Batch Processing**: Hadoop processes data only in batches, meaning you must wait for one process to complete before submitting another batch.

### Introduction to Apache Spark
To address the limitations of Hadoop, Apache Spark was launched in 2009 by California students (please verify).

Spark introduced a powerful concept called **RDD (Resilient Distributed Datasets)**, which is considered the backbone of Apache Spark.

#### What is Spark?
Apache Spark is a unified analytics engine for large-scale data processing, designed to be faster and more efficient than Hadoop.

#### What is RDD?
An RDD is an immutable distributed collection of objects that can be processed in parallel across a cluster. It provides fault tolerance, allowing computations to recover from failures.

#### Key Features of RDD:
1. **Immutable**
   - **Definition**: Immutable means unchangeable. Once an RDD is created, you cannot modify it. Instead, any operation (like a transformation) applied to an RDD creates a new RDD without altering the original one.

2. **Distributed**
   - **Definition**: Data in an RDD is split into partitions and stored across multiple nodes in a cluster.
   - **How It Works**: Spark divides an RDD into smaller chunks called partitions, which are distributed across nodes in a cluster. Each partition is processed independently and in parallel.
   - **Example**: If you have an RDD with 1,000,000 elements and a cluster of 10 nodes, Spark might divide this RDD into 10 partitions, with each node processing 100,000 elements.

3. **Collection of Objects**
   - **Definition**: An RDD is essentially a dataset where each element is an object. These objects can be of any data type, such as integers, strings, tuples, or even complex user-defined types.
   - **Why It Matters**:
     - **Flexibility**: RDDs can handle a wide variety of data formats.
     - **Custom Processing**: Users can apply custom transformations and actions to the objects.

4. **Processed in Parallel Across a Cluster**
   - **Definition**: Operations on an RDD are divided into tasks, and each task is processed independently on a separate node in the cluster.
   - **Why It Matters**:
     - **Speed**: Parallel processing significantly reduces the time needed to process large datasets.
     - **Resource Utilization**: Spark uses all available nodes in the cluster efficiently.
   - **Example**: If you perform a map operation on an RDD with 1 million elements distributed across 4 nodes, each node processes 250,000 elements simultaneously.

#### Putting It All Together:
1. **Immutable**: You cannot change an existing RDD. Transformations (like `map` or `filter`) create new RDDs.
2. **Distributed**: Data is split into partitions and stored across multiple nodes in the cluster.
3. **Collection of Objects**: Each RDD is a logical collection of elements (e.g., numbers, strings, or complex objects).
4. **Processed in Parallel**: Each node processes its partition of the RDD in parallel, speeding up computations.

#### Example:
Imagine you have a dataset of 1 billion records, and you want to square each number using Spark:

```python
# Distributed collection of integers
rdd = sc.parallelize(range(1, 1000000000))  

# Transform the RDD
squared_rdd = rdd.map(lambda x: x ** 2)    

# Trigger action to collect first 10 results
result = squared_rdd.take(10)              

print(result)
```

---

### Fault Tolerance:
**Fault tolerance** refers to the ability of a system, network, or application to continue operating properly in the event of a failure of some of its components. It ensures that even when errors, faults, or failures occur, the system can maintain functionality, often without any noticeable impact on users or processes.



----
### Course Notes & Resources

#### Access Course Notes
You can access the course notes at the following link:

[Course Notes on Obsidian](https://publish.obsidian.md/datavidhya/)

#### Github Repository for Code and Data
The repository containing the code and data for the course can be found here:

[Apache Spark with Data Bricks for Data Engineering](https://github.com/darshilparmar/apache-spark-with-data-bricks-for-data-engineering)

---

# Spark Important Concepts:

## 1. Why do we need Spark? Big Data Problem
For most of their history, computers became faster every year through processor speed increases: the new processors each year could run more instructions per second than the previous year’s. As a result, applications also automatically became faster every year, without any changes needed to their code.

This trend in hardware stopped around 2005: due to hard limits in heat dissipation, hardware developers stopped making individual processors faster, and switched toward adding more parallel CPU cores all running at the same speed. This change meant that suddenly applications needed to be modified to add parallelism in order to run faster, which set the stage for new programming models such as Apache Spark.

In this new world, the software developed in the past 50 years cannot automatically scale up, and neither can the traditional programming models for data processing applications, creating the need for new programming models. It is this world that Apache Spark was built for.

Apache Spark began at UC Berkeley in 2009 as the Spark research project, which was first published the following year in a paper entitled “Spark: Cluster Computing with Working Sets”

At the time, Hadoop MapReduce was the dominant parallel programming engine for clusters

---

## 2. Spark Dataframe:
A DataFrame is the most common Structured API and simply represents a table of data with rows and columns.

**Note:**
A **structured API** is a way for computers or programs to communicate with each other in a clear, organized, and predictable way. It defines a set of rules and formats for exchanging data so that both the sender and receiver understand what to expect.

![image](https://github.com/user-attachments/assets/1f5881f8-a83c-4318-a9de-0f0a4ec80cfc)
