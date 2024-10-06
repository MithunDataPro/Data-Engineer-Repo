# Directed Acyclic Graph (DAG)

A Directed Acyclic Graph (DAG) is a conceptual representation of a series of activities. The order of the activities is represented by a graph, which is visually presented as a set of circles, each circle represent an activity, connected by lines, which represent the execution flow from one activity to another. **Circles are known as vertices** and **connecting lines are known as edges**.

![image](https://github.com/user-attachments/assets/2b389bfd-3ba8-43f0-87a2-7561031cde50)


**Directed** here means that each edge has a defined direction, that represents a unidirectional flow from one vertex to another.

**Acyclic** here means that there are no loops or cycles in the graph, so that for any given vertex, if we follow an edge that connects that vertex to another, there is no path in the graph to get back to that initial vertex.

## Directed Acyclic Graph (DAG) in Apache Spark

**DAG in Apache Spark** in similar terms is a set of Vertices and Edges, where vertices represent the **RDDs** and the edges represent the **Transformations** to be applied on **RDD**. There are finite number of vertices and edges in a Spark DAG, where each edge directed from one vertex to another.

This is how Spark Application model looks like:

![image](https://github.com/user-attachments/assets/06dfd124-e631-4b09-8555-f26b52ac4c84)

- **Application** — A user program built on Spark using its APIs. It consists of a driver program and executors on the cluster.

- **Job** — A parallel computation consisting of multiple tasks that gets spawned in response to a Spark action (e.g., save(), collect()). During interactive sessions with Spark shells, the **driver** converts your Spark application into one or more Spark jobs. It then transforms each job into a **DAG**. This, in essence, is Spark’s **execution plan**, where each node within a **DAG** could be a single or multiple Spark stages. **So a Spark job is created whenever an action is called.**

- **Stage** — Each job gets divided into smaller sets of tasks called **stages** that depend on each other. As part of the DAG nodes, stages are created based on what operations can be performed serially or in parallel. Not all Spark operations can happen in a single stage, so they may be divided into multiple stages. Often stages are delineated on the operator’s computation boundaries, where they dictate data transfer among Spark executors.

- **Task** — A single unit of work or execution that will be sent to a Spark executor. Each stage is comprised of Spark tasks (a unit of execution), which are fed across each Spark executor, each task maps to a single partition of data.

## Dive Deep into DAGs

Let’s learn more about DAGs by writing some code and understanding about the jobs, stages and tasks via SparkUI.

### Create a Dataframe

```
df_emp=spark.read.csv(‘<path>/emp.csv’,header=True)
df_emp.show(15)

```

### Output::

![image](https://github.com/user-attachments/assets/15c76231-5dbe-4b15-a758-2ae28dfe55ab)

---

**DAG Output**: Spark triggered two jobs for the above piece of code.

![image](https://github.com/user-attachments/assets/cb627f74-f69d-4079-9736-37bf57aa31f8)


**When inferSchema is enabled, Spark reads the CSV file two times. In this case, InferSchema is not invoked.**

### DAG for Job Id 0

![image](https://github.com/user-attachments/assets/222ca12b-ae63-4fb5-90fa-d2fb6c62d403)


DAG for Job ID 0 is further divided into three parts:

1. **Scan text**

   - **FileScanRDD [0]** represents reading the data from a file, basically involves: **Number of Files Read, File System Read, Data Size Total, Size of Files Read Total,** and **Rows Output**.
   - **MapPartitionsRDD [1]** Runs the series of computations on the RDD partitions created by FileScanRDD process. In our case, it is creating partitions of the data read from the CSV file.

2. **WholeStageCodegen (1)**

   - **WholeStageCodegen** is a physical query optimization in Spark SQL that fuses multiple physical operators together into a single Java function.
   - In simple terms, at this step, the calculations written on dataframes are computed to generate the Java code to build underlying RDDs.

3. **mapPartitionsInternal**

   - MapPartitionsRDD [1] runs the series of computations on the RDD partitions created by FileScanRDD process. In our case, it is creating partitions of the data read from the CSV file.

 **Detailed DAG for Stage 0:**

![image](https://github.com/user-attachments/assets/f918bf9d-52f7-4d0a-b9d6-13a8d5451b61)

**DAG for job Id 1.**

![image](https://github.com/user-attachments/assets/0a91bff0-5b99-4750-871e-bf74f58ceea1)


Steps are similar to Job ID 0 and have been explained above.

1. **Scan csv**
   - FileScanRDD [0] represents reading the data from a file, basically involves:- Number of Files Read, File System Read, Data Size Total, Size of Files Read Total, and Rows Output.
   - MapPartitionsRDD [1] runs the series of computations on the RDD partitions created by FileScanRDD process. In our case it is creating partitions of the data read from csv file.

2. **mapPartitionsInternal**
   - MapPartitionsRDD [1] runs the series of computations on the RDD partitions created by FileScanRDD process. In our case it is creating partitions of the data read from csv file.

![image](https://github.com/user-attachments/assets/3acc5f12-aa1f-4a49-9884-76b9832c8874)

---

#### Apply group by and aggregates.

```
#use same dataframe to apply groupby and sum operation
sum_df=df_emp.groupBy('DEPTNO').sum('SAL')
sum_df.show(5)

```

#### Output:

![image](https://github.com/user-attachments/assets/98da7dc4-691d-41d2-b046-2fed81473bcb)

![image](https://github.com/user-attachments/assets/391e663b-1c50-429f-bf90-dfd3957955c8)


Scan csv and WholeStageCodegen we have already discussed above. In groupby operation we have another operation which is Exchange. Exchange occurs when there is a Wide transformation.

---

#### **Exchange**

- **Exchange represents Shuffle** i.e., physical data movement on the cluster among several nodes.

- **Exchange** is one of the most expensive operations in a Spark job.

![image](https://github.com/user-attachments/assets/36166802-77d1-4716-abe2-9d91042b3f7f)


Stage6 is skipped because the evaluations are being performed in Stage5 above.

![image](https://github.com/user-attachments/assets/3c18fa14-beb4-4545-b357-8eabe38fa463)


Under the hood spark has a two-stage plan to execute the group by operation.

· **Step1** reads the data from dataset and fills it to the output exchange, where in our DAG represents Exchange box in stage5 or 6.

· **Step2** reads the data from output exchange and brings it to the input exchange for stage1 to process, represented by **AQEShuffleRead** in Stage7.

The process of input and output exchange is known as **Shuffle sort**.

## Summary

- **Understanding about DAGs.**
- **Coding and SparkUI deep dive into DAGs.**

