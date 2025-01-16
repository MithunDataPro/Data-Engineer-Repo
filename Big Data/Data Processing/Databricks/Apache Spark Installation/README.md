# How to Use Apache Spark in Google Colab

Follow these steps to set up and use Apache Spark in Google Colab:

## 1. Install Apache Spark and Java
Run the following code in a Colab cell to install Spark and Java:

```bash
!apt-get update
!apt-get install -y openjdk-8-jdk-headless -qq > /dev/null
!wget -q https://downloads.apache.org/spark/spark-3.5.0/spark-3.5.0-bin-hadoop3.tgz
!tar xf spark-3.5.0-bin-hadoop3.tgz
!pip install -q findspark

```

## 2. Set Environment Variables
Set the environment variables to configure Spark:

```python
import os
os.environ["JAVA_HOME"] = "/usr/lib/jvm/java-8-openjdk-amd64"
os.environ["SPARK_HOME"] = "/content/spark-3.5.0-bin-hadoop3"

```

## 3. Initialize findspark
Initialize **findspark** to locate the Spark installation:

```python
import findspark
findspark.init()

```

## 4. Start a SparkSession
Create a SparkSession to interact with Spark:

```python
from pyspark.sql import SparkSession

spark = SparkSession.builder \
    .appName("Google Colab Spark Example") \
    .getOrCreate()

print("SparkSession created successfully!")

```

## 5. Use Spark
Now you can start using Spark for data processing. Here’s an example of creating and displaying a DataFrame:

```python
data = [("Alice", 29), ("Bob", 35), ("Cathy", 25)]
columns = ["Name", "Age"]

df = spark.createDataFrame(data, columns)
df.show()

```

## 6. Stop the SparkSession
When you're done, stop the SparkSession to free up resources:

```python
spark.stop()

```

### Example Use Case: Word Count
Here’s an example of performing a word count using Spark:

```python
text = ["Apache Spark is amazing.", "Google Colab makes it easy to use Spark."]
rdd = spark.sparkContext.parallelize(text)

words = rdd.flatMap(lambda line: line.split(" "))
word_counts = words.map(lambda word: (word, 1)).reduceByKey(lambda a, b: a + b)
word_counts.collect()

```

## 7. Save Your Work
Save your work or outputs to Google Drive if needed:

```python
from google.colab import drive
drive.mount('/content/drive')

```
