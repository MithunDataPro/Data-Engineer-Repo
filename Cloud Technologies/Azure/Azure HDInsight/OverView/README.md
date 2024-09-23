# Scenarios for using HDInsight

Azure HDInsight can be used for various scenarios in big data processing. It can be historical data (data that is already collected and stored) or real-time data (data that is directly streamed from the source). The scenarios for processing such data can be summarized in the following categories:

## Batch processing (ETL)
Extract, transform, and load (ETL) is a process where unstructured or structured data is extracted from heterogeneous data sources. It's then transformed into a structured format and loaded into a data store. You can use the transformed data for data science or data warehousing.

## Data warehousing
You can use HDInsight to perform interactive queries at petabyte scales over structured or unstructured data in any format. You can also build models connecting them to BI tools.

![image](https://github.com/user-attachments/assets/7dbf034a-5ff9-4fa5-8cbe-5fdbe14053eb)


## Internet of Things (IoT)
You can use HDInsight to process streaming data that is received in real time from different kinds of devices. For more information, read this blog post from Azure that announces the public preview of Apache Kafka on HDInsight with Azure Managed disks.

![image](https://github.com/user-attachments/assets/3ce48c87-6a14-4279-868a-1dce073f0758)


## Hybrid
You can use HDInsight to extend your existing on-premises big data infrastructure to Azure to apply the advanced analytics capabilities of the cloud.

![image](https://github.com/user-attachments/assets/22427c46-bbd3-403b-81b4-95efe5ce5618)


# Open-source components in HDInsight
Azure HDInsight enables you to create clusters with open-source frameworks such as Spark, Hive, LLAP, Kafka, Hadoop and HBase. By default, these clusters include various open-source components such as Apache Ambari, Avro, Apache Hive 3, HCatalog, Apache Hadoop MapReduce, Apache Hadoop YARN, Apache Phoenix, Apache Pig, Apache Sqoop, Apache Tez, Apache Oozie, and Apache ZooKeeper.

# Programming languages in HDInsight
HDInsight clusters, including Spark, HBase, Kafka, Hadoop, and others, support many programming languages. Some programming languages aren't installed by default. For libraries, modules, or packages that aren't installed by default, use a script action to install the component.

## Programming language	Information

### Default programming language support
By default, HDInsight clusters support:
- Java
- Python
- .NET
- Go

### Java virtual machine (JVM) languages
Many languages other than Java can run on a Java virtual machine (JVM). However, if you run some of these languages, you might have to install more components on the cluster. The following JVM-based languages are supported on HDInsight clusters:
- Clojure
- Jython (Python for Java)
- Scala

### Hadoop-specific languages
HDInsight clusters support the following languages that are specific to the Hadoop technology stack:
- Pig Latin for Pig jobs
- HiveQL for Hive jobs and SparkSQL

# Development tools for HDInsight
You can use HDInsight development tools, including IntelliJ, Eclipse, Visual Studio Code, and Visual Studio, to author and submit HDInsight data queries and jobs with seamless integration with Azure.

- Azure toolkit for IntelliJ 10
- Azure toolkit for Eclipse 6
- Azure HDInsight tools for VS Code 13
- Azure data lake tools for Visual Studio 9

# Business intelligence on HDInsight
Familiar business intelligence (BI) tools retrieve, analyze, and report data that is integrated with HDInsight by using either the Power Query add-in or the Microsoft Hive ODBC Driver:

- Apache Spark BI using data visualization tools with Azure HDInsight
- Visualize Apache Hive data with Microsoft Power BI in Azure HDInsight
- Visualize Interactive Query Hive data with Power BI in Azure HDInsight
- Connect Excel to Apache Hadoop with Power Query (requires Windows)
- Connect Excel to Apache Hadoop with the Microsoft Hive ODBC Driver (requires Windows)

# In-region data residency
Spark, Hadoop, and LLAP don't store customer data, so these services automatically satisfy in-region data residency requirements specified in the Trust Center.

Kafka and HBase do store customer data. This data is automatically stored by Kafka and HBase in a single region, so this service satisfies in-region data residency requirements specified in the Trust Center.

Next steps:
- Create Apache Hadoop cluster in HDInsight
- Create Apache Spark cluster - Portal
- Enterprise security in Azure HDInsight
