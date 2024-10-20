#  Spark = Python + SQL = PySpark

## Apache Spark

**Initial Version**: Apache Spark was first introduced in **2012**.

**Intial Version** is Realeased in **May 2024** as **Spark 1.0.0**.

**Introduction**: It was developed at UC Berkeley's AMPLab by Matei Zaharia and later open-sourced in 2010, but the initial version was released officially in **2012** under the **Apache Software Foundation**. Apache Spark is a unified analytics engine for large-scale data processing, with built-in modules for streaming, SQL, machine learning, and graph processing.

Spark revolutionized the big data ecosystem by providing an easy-to-use API in languages such as Python, Java, and Scala, and offering in-memory processing capabilities, significantly faster than Hadoop’s MapReduce.

## Apache Spark Versions

1. **Apache Spark 0.5** (Released in 2012)  
   The first public release of Spark, focused on core APIs and resilient distributed datasets (RDDs). It was designed to work with Hadoop, offering faster alternatives to MapReduce.

2. **Apache Spark 1.0** (Released in May 2014)  
   Introduced DataFrames API, making Spark more user-friendly by offering high-level abstractions for distributed data. Spark Streaming and machine learning libraries (MLlib) were introduced in this version.

3. **Apache Spark 1.6** (Released in January 2016)  
   Major improvements in Spark SQL and DataFrames. Introduction of Tungsten execution engine, Catalyst optimizer, and Dataset API (combination of RDD and DataFrames).

4. **Apache Spark 2.0** (Released in July 2016)  
   Marked a big leap with Structured Streaming, an improved version of Spark Streaming. Introduction of Unified DataFrames and Datasets API, better optimizations, and significant performance enhancements.

5. **Apache Spark 2.4** (Released in November 2018)  
   Improved support for Kubernetes, enhanced Python API (PySpark), and introduced higher-order functions in SQL. It was also the last release in the Spark 2.x series.

6. **Apache Spark 3.0** (Released in June 2020)  
   Introduced Adaptive Query Execution (AQE), significant improvements in Pandas API support, better support for Kubernetes, and enhanced ANSI SQL compatibility.

7. **Apache Spark 3.1** (Released in March 2021)  
   Brought in further improvements in performance, added new data source connectors, and improved APIs for Spark SQL.

8. **Apache Spark 3.2** (Released in October 2021)  
   Introduced new features for Spark SQL and PySpark, improved support for GPU acceleration, and enhancements to the Kubernetes scheduler.

9. **Apache Spark 3.3** (Released in June 2022)  
   Enhanced support for ANSI SQL, improvements in Spark's query execution engine, and stability improvements for Spark on Kubernetes.

10. **Apache Spark 3.4** (Released in May 2023)  
   Brought further enhancements to the Catalyst Optimizer, better Python UDFs support, and continued improvements for adaptive execution and query optimization.

---

### Note:
**Hadoop** (2.x) Supports **Spark** By **Yarn** Resource Manager.

**Hadoop** (1.x) Doesn't Support **Spark**.

**Architeture** in **Hadoop** (1.x):

- HDFS - Storage
- Map Reduce - Data Processing & Cluster Resource Management.

**Hadoop** (2.x) **Architeture**:

- HDFS - Storage
- Map Reduce - Data Processing
- Yarn - Cluster Resource Manager

![image](https://github.com/user-attachments/assets/c3416051-89e3-49a6-8763-fa30c1773b64)

---


# Difference Between SparkContext and SparkSession

## 1. **SparkContext**

- **Purpose**: SparkContext is the entry point to any Spark functionality. It is the primary object that connects to the cluster and sets up the configuration for Spark jobs.
- **Introduced In**: Spark 1.x.
- **Creation**: Used to initialize the core Spark engine and enables access to Spark's basic functionalities like creating RDDs.
- **Key Role**: 
  - Responsible for low-level configurations and connecting to the cluster.
  - Creates RDDs (Resilient Distributed Datasets).
- **Limitations**: 
  - Does not provide easy access to higher-level APIs like DataFrames or Datasets.
  - Can only handle RDD-based operations, limiting support for SQL or DataFrame APIs.

## 2. **SparkSession**

- **Purpose**: SparkSession is a unified entry point for all Spark functionalities, introduced to simplify the API.
- **Introduced In**: Spark 2.0.
- **Creation**: It internally contains a SparkContext but also manages access to all Spark functionality, including SQL, streaming, and machine learning.
- **Key Role**:
  - Provides access to DataFrame and Dataset APIs.
  - Supports SQL queries, streaming data processing, and Spark's MLlib.
  - Unifies all Spark operations into a single object, simplifying the development experience.
- **Advantages**:
  - It's a replacement for SQLContext, HiveContext, and SparkContext.
  - Offers a high-level API that works with both structured and unstructured data.

## Key Differences

| Aspect            | **SparkContext**                          | **SparkSession**                                  |
|-------------------|-------------------------------------------|---------------------------------------------------|
| **Introduced In**  | Spark 1.x                                 | Spark 2.0                                         |
| **Primary Usage**  | Low-level access to Spark's core engine   | Unified access to all of Spark's APIs             |
| **API Support**    | RDD-based operations                      | Supports DataFrames, Datasets, SQL, and more      |
| **Complexity**     | Requires different contexts for SQL, etc. | Simplifies access to all functionalities in one   |
| **Replacement For**| N/A                                       | SQLContext, HiveContext, and SparkContext         |


# Explanation of the Code

```python
from pyspark.sql import SparkSession

spark = SparkSession.builder.appName("first Program").getOrCreate()


```


# Explanation of SparkSession Code

## What Happens:

### Importing SparkSession:
The line `from pyspark.sql import SparkSession` imports the `SparkSession` class from PySpark. SparkSession is the entry point for using Spark's DataFrame and SQL APIs in PySpark.

### Creating a SparkSession Object:
The code `SparkSession.builder.appName("first Program")` creates a builder for a new SparkSession.  
- The method `appName("first Program")` assigns the name **"first Program"** to the Spark application, which will be visible in the Spark UI for easier tracking and debugging.

### Calling `getOrCreate()`:
The `getOrCreate()` method checks if an existing SparkSession is active.  
- If a session already exists, it returns that session; otherwise, it creates a new one. This prevents the accidental creation of multiple sessions within the same application.

### SparkSession Creation:
After this line executes, a SparkSession is either initialized or retrieved.  
- It establishes the connection to the Spark cluster, manages resources, and provides access to Spark's high-level APIs such as DataFrame operations, SQL queries, and more.

### Result:
You now have a SparkSession object stored in the variable `spark`. You can use it to load data, create DataFrames, and perform transformations and actions through Spark's powerful APIs.

## Summary:
This code initializes a SparkSession, which serves as the entry point to interact with Apache Spark. It sets the application name to **"first Program"** and ensures only one SparkSession exists using the `getOrCreate()` method.

---

#### Note: 

**Python** Doesn't Support Datasets 

