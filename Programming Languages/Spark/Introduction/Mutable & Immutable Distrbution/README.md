# Mutable & Immutable Distributions in Spark

In Apache Spark, the terms **mutable** and **immutable** refer to the way data is handled and transformed within the system, particularly in distributed data structures like RDDs (Resilient Distributed Datasets) and DataFrames.

## Immutable Distributions in Spark

- **Immutability** means once a distributed data structure (like an RDD or DataFrame) is created, it **cannot be modified**. Every transformation on this data structure results in a new RDD or DataFrame.
- **RDDs** are immutable in Spark, meaning any transformation (such as `map`, `filter`, or `reduce`) on an RDD doesn't change the original RDD but creates a new RDD with the transformed data.

### Example of Immutable Operations

```python
rdd = sc.parallelize([1, 2, 3, 4])
new_rdd = rdd.map(lambda x: x * 2)  # The original rdd is unchanged, and a new RDD is returned.

```

## Advantages of Immutability

- **Fault Tolerance**: If part of a computation fails, Spark can recompute the lost partitions by referring to the original RDD.
- **Parallelism**: Since the original data is never modified, different transformations can run in parallel without causing race conditions or data corruption.

## Mutable Distributions in Spark

- **Mutable data structures** can be modified in place, but Spark encourages immutability for distributed data to ensure consistency and fault tolerance.
- Spark generally discourages the use of mutable data when dealing with RDDs or DataFrames because mutable operations can lead to unpredictable behavior, especially in distributed environments.

### Mutable Structures: Broadcast Variables and Accumulators

1. **Broadcast Variables**: Allow caching a read-only variable on each machine, accessible to tasks running on that node. These variables can be changed in place if necessary.
2. **Accumulators**: Variables that are only "added" to, used for sums or counts across distributed nodes.

### Example of Accumulators

```python
accum = sc.accumulator(0)
rdd = sc.parallelize([1, 2, 3, 4])

def f(x):
    accum.add(x)
    return x

rdd.map(f).collect()  # Accumulator is mutable and updated as the data is processed.
print(accum.value)  # Outputs the sum of the RDD elements.

```


![image](https://github.com/user-attachments/assets/4067c42a-4126-4ad4-82c6-b36cd4d2ae9c)

