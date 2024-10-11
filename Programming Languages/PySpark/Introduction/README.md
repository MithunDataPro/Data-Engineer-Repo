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


### Note:
**Hadoop** (2.x) Supports **Spark** By **Yarn** Resource Manager.

**Hadoop** (1.x) Doesn't Support **Spark**.
**Architeture** in **Hadoop** (1.x):
HDFS - Storage
Map Reduce - Data Processing & Cluster Resource Management.

**Hadoop** (2.x) **Architeture**:
HDFS - Storage
Map Reduce - Data Processing
Yarn - Cluster Resource Manager
