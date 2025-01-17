![image](https://github.com/user-attachments/assets/8c461206-2fa9-49a3-9c8a-b78f3c23eba3)

---

# Structured API Overview

The Structured **APIs** are a tool for manipulating all sorts of data, from **unstructured log files** to **semi-structured CSV files** and **highly structured Parquet files**.

**These APIs refer to three core types of distributed collection APIs:**
- Datasets
- DataFrames
- SQL tables and views

The Structured APIs are the fundamental abstraction that you will use to write the majority of your data flows.

**Note:**
Also, In the Above Core Types In real time we maily work with Dataframes & SQL Tables & Views.


**Structured APIs:** They are the foundation of modern data processing in **Apache Spark**. They provide a **high-level abstraction** for handling structured data efficiently.

---

# Spark DataFrame:

A DataFrame is the most common Structured API and simply represents a table of data with rows and columns.

![image](https://github.com/user-attachments/assets/986a51d2-932f-44d8-ad90-69ce8f02cd85)

- The DataFrame concept is not unique to Spark. R and Python both have similar concepts. However, Python/R DataFrames (with some exceptions) exist on one machine rather than multiple machines.

- However, because Spark has language interfaces for both Python and R, it’s quite easy to convert Pandas (Python) DataFrames to Spark DataFrames, and R DataFrames to Spark DataFrames.

- To Spark, DataFrames represents immutable, lazily evaluated plans that specify what operations to apply to data residing at a location to generate some output

## Schemas:
- A schema defines the column names and types of a DataFrame. You can define schemas manually or read a schema from a data source (often called schema on read). Schemas consist of types, meaning that you need a way of specifying what lies where.

- Spark is effectively a programming language of its own. Internally, Spark uses an engine called Catalyst that maintains its own type information through the planning and processing of work.

## Columns:
Columns represent a simple type like an integer or string, a complex type like an array or map, or a null value.

## Rows 
A row is nothing more than a record of data. Each record in a DataFrame must be of type Row, as we can see when we collect the following DataFrames.

## Spark Types 
Spark Types are different data types supported by Spark, you can use following code to import types in your code

```python
  from pyspark.sql.types import *
  b = ByteType()

```

![image](https://github.com/user-attachments/assets/536bfd3e-99d9-4df1-9c53-8b01d78627a6)

It’s worth keeping in mind that the types might change over time as Spark SQL continues to grow so you may want to reference Spark’s documentation for future updates.

---

# Overview of Structured API Execution 

**Let’s walk through the execution of a single structured API query from user code to executed code. Here’s an overview of the steps:**

- Write DataFrame/Dataset/SQLCode.
- If valid code, Spark converts this to a LogicalPlan.
- Spark transforms this Logical Plan to a Physical Plan, checking for optimizations along the way.
- Spark then executes this Physical Plan(RDD manipulations) on the cluster.

![image](https://github.com/user-attachments/assets/db9116cf-c8ed-4538-97d9-d8030b4db863)

## Logical Planning 
The first phase of execution is meant to take user code and convert it into a logical plan.

![image](https://github.com/user-attachments/assets/eb3a62ad-ea84-4b2b-8e37-1cc970eedcea)

This logical plan only represents a set of abstract transformations to convert the user’s set of expressions into the most optimized version.

### - Unresolved Logical Plan:
It does this by converting user code into an unresolved logical plan. This plan is unresolved because although your code might be valid, the tables or columns that it refers to might or might not exist.
### - Catalog
Spark uses the catalog, a repository of all table and DataFrame information, to resolve columns and tables in the analyzer. The analyzer might reject the unresolved logical plan if the required table or column name does not exist in the catalog.
### - Catalyst Optimizer:
a collection of rules that attempt to optimize the logical plan by pushing down predicates or selections.

## Physical Planning 
After successfully creating an optimized logical plan, Spark then begins the physical planning process. The physical plan, often called a Spark plan, specifies how the logical plan will execute on the cluster

![image](https://github.com/user-attachments/assets/f1245153-42fb-46f5-aa14-82c06574d316)

An example of the cost comparison might be choosing how to perform a given join by looking at the physical attributes of a given table

## Execution 
Upon selecting a physical plan, Spark runs all of this code over RDDs, the lower-level programming interface of Spark. Spark performs further optimizations at runtime, generating native Java bytecode that can remove entire tasks or stages during execution. Finally the result is returned to the user.
