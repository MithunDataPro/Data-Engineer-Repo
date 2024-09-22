# BigQuery Query Processing Overview

This document describes how BigQuery processes queries and provides an overview of several features that are useful for data analytics.

BigQuery is optimized to run analytic queries on large datasets, including terabytes of data in seconds and petabytes in minutes. Understanding its capabilities and how it processes queries can help you maximize your data analysis investments.

To take a tour of BigQuery's data analytics features directly in the Google Cloud console, click Take the tour.

[Take the tour](https://cloud.google.com/bigquery/docs/tour)

## Analytic Workflows
BigQuery supports several data analysis workflows:

- **Ad hoc analysis**. BigQuery uses GoogleSQL, the SQL dialect in BigQuery, to support ad hoc analysis. You can run queries in the Google Cloud console or through third-party tools that integrate with BigQuery.
- **Geospatial analysis**. BigQuery uses geography data types and GoogleSQL geography functions to let you analyze and visualize geospatial data. For information about these data types and functions, see [Introduction to geospatial analytics](https://cloud.google.com/bigquery/docs/geospatial-data).
- **Machine learning**. BigQuery ML uses GoogleSQL queries to let you create and execute machine learning (ML) models in BigQuery.
- **Business intelligence**. BigQuery BI Engine is a fast, in-memory analysis service that lets you build rich, interactive dashboards and reports without compromising performance, scalability, security, or data freshness.

## Queries
The primary unit of analysis in BigQuery is the SQL query. BigQuery has two SQL dialects: GoogleSQL and legacy SQL. GoogleSQL is the preferred dialect. It supports SQL:2011 and includes extensions that support geospatial analysis or ML.

The following sections describe how BigQuery supports and runs data queries.

### Data Sources
BigQuery lets you query the following types of data sources:

- **Data stored in BigQuery**. You can load data into BigQuery for analysis. You can also generate data by using data manipulation language (DML) statements or by writing query results into a table. You can query data stored in single-region or multi-region locations, but you cannot run a query against multiple locations even if one is a single-region location and the other is the multi-region location containing that single-region location. For more information, see [Locations, reservations, and jobs](https://cloud.google.com/bigquery/docs/locations-jobs).
- **External data**. You can query various external data sources such other Google Cloud storage services (like Cloud Storage) or database services (like Spanner or Cloud SQL). For information about how to set up connections to external sources, see [Introduction to external data sources](https://cloud.google.com/bigquery/docs/external-data-sources).
- **Multi-cloud data**. You can query data that's stored in other public clouds such as AWS or Azure. For information on how to set up connections to Amazon S3 or Azure blob storage, read an introduction to [BigQuery Omni](https://cloud.google.com/omni).
- **Public datasets**. If you don't have your own data, you can analyze any of the datasets that are available in the [public dataset marketplace](https://cloud.google.com/bigquery/public-data).

### Query Jobs
Jobs are actions that BigQuery runs on your behalf to load data, export data, query data, or copy data.

When you use the Google Cloud console or the bq tool to perform one of these jobs, a job resource is automatically created, scheduled, and run. You can also programmatically create a load, export, query, or copy job. When you create a job programmatically, BigQuery schedules and runs the job for you.

Because jobs can potentially take a long time to complete, they run asynchronously and can be polled for their status. Shorter actions, such as listing resources or getting metadata, are not managed by a job resource.

### Types of Queries
You can query BigQuery data by using one of the following query job types:

- **Interactive query jobs**. By default, BigQuery runs interactive (on-demand) query jobs as soon as possible.
- **Continuous query jobs (Preview)**. With these jobs, the query runs continuously, letting you analyze incoming data in BigQuery in real time and then write the results to a BigQuery table, or export the results to Bigtable or Pub/Sub. You can use this capability to perform time sensitive tasks, such as creating and immediately acting on insights, applying real time machine learning (ML) inference, and building event-driven data pipelines.
- **Batch query jobs**. With these jobs, BigQuery queues each batch query on your behalf and then starts the query when idle resources are available, usually within a few minutes.

You can run query jobs by using the following methods:

- Compose and run a query in the Google Cloud console.
- Run the bq query command in the [bq command-line tool](https://cloud.google.com/bigquery/docs/reference/bq-cli-reference).
- Programmatically call the jobs.query or jobs.insert method in the [BigQuery REST API](https://cloud.google.com/bigquery/docs/reference/rest).
- Use the [BigQuery client libraries](https://cloud.google.com/bigquery/docs/reference/libraries).

### Saved and Shared Queries
BigQuery lets you save queries and share queries with others.

When you save a query, it can be private (visible only to you), shared at the project level (visible to specific principals), or public (anyone can view it). For more information, see [Work with saved queries](https://cloud.google.com/bigquery/docs/saving-queries).

## How BigQuery Processes Queries
Several processes occur when BigQuery runs a query:

- **Execution tree**. When you run a query, BigQuery generates an execution tree that breaks the query into stages. These stages contain steps that can run in parallel.
- **Shuffle tier**. Stages communicate with one another by using a fast, distributed shuffle tier that stores intermediate data produced by the workers of a stage. When possible, the shuffle tier leverages technologies such as a petabit network and RAM to quickly move data to worker nodes.
- **Query plan**. When BigQuery has all the information that it needs to run a query, it generates a query plan. You can view this plan in the Google Cloud console and use it to troubleshoot or optimize query performance.
- **Query monitoring and dynamic planning**. Besides the workers that perform the work of the query plan itself, additional workers monitor and direct the overall progress of work throughout the system. As the query progresses, BigQuery might dynamically adjust the query plan to adapt to the results of the various stages.
- **Query results**. When a query is complete, BigQuery writes the results to persistent storage and returns them to the user. This design lets BigQuery serve cached results the next time that query is run.

## Query Concurrency and Performance
The performance of queries that are run repeatedly on the same data can vary because of the shared nature of the BigQuery environment, or because BigQuery dynamically adjusts the query plan while the query runs. For a typical busy system where many queries run concurrently, BigQuery uses several processes to smooth out variances in query performance:

- BigQuery runs many queries in parallel, so there's rarely a need to queue queries.
- In busy systems, queues are a major source of less-predictable performance because it's unclear how long a query might sit in the queue. The time a query is in the queue can depend more on other queries that are running or are in the queue than upon the qualities of the query itself.
- As queries start and finish, BigQuery redistributes resources fairly between new and running queries. This process ensures that query performance doesn't depend on the order in which queries are submitted but rather on the number of queries run at a given time.

## Query Optimization
After the query is complete, you can view the query plan in the Google Cloud console. You can also request execution details by using the `INFORMATION_SCHEMA.JOBS*` views or the [jobs.get](https://cloud.google.com/bigquery/docs/reference/rest/v2/jobs/get) REST API method.

The query plan includes details about query stages and steps. These details can help you identify ways to improve query performance. For example, if you notice a stage that writes a lot more output than other stages, it might mean that you need to filter earlier in the query.

For more information about the query plan and query optimization, see the following resources:

- To learn more about the query plan and see examples of how the plan information can help you to improve query performance, see [Query plan and timeline](https://cloud.google.com/bigquery/query-plan-explanation).
- For more information about query optimization in general, see [Introduction to optimizing query performance](https://cloud.google.com/bigquery/docs/query-optimization-intro).

## Query Monitoring
Monitoring and logging are crucial for running reliable applications in the cloud. BigQuery workloads are no exception, especially if your workload has high volumes or is mission critical. BigQuery provides various metrics, logs, and metadata views to help you monitor your BigQuery usage.

For more information, see the following resources:

- To learn about monitoring options in BigQuery, see [Introduction to BigQuery monitoring](https://cloud.google.com/bigquery/docs/monitoring).
- To learn about audit logs and how to analyze query behavior, see [BigQuery audit logs](https://cloud.google.com/bigquery/docs/reference/auditlogs).

## Query Pricing
BigQuery offers two pricing models for analytics:

- **On-demand pricing**. You pay for the data scanned by your queries. You have a fixed, query-processing capacity for each project, and your cost is based on the number of bytes processed.
- **Capacity-based pricing**. You purchase dedicated query-processing capacity.

For information about the two pricing models and to learn more about making reservations for capacity-based pricing, see [Introduction to reservations](https://cloud.google.com/bigquery/docs/reservations-intro).

## Quotas and Query Cost Controls
BigQuery enforces project-level quotas on running queries. For information on query quotas, see [Quotas and limits](https://cloud.google.com/bigquery/quotas).

To control query costs, BigQuery provides several options, including custom quotas and billing alerts. For more information, see [Creating custom cost controls](https://cloud.google.com/bigquery/docs/cost-controls).

## Data Analytics Features
BigQuery supports both descriptive and predictive analytics. To query your data directly to answer some statistical questions, you can use the Google Cloud console. To visually explore the data, such as for trends and anomalies, you can use tools like Tableau or Looker that integrate with BigQuery.

## BigQuery Studio
BigQuery Studio helps you discover, analyze, and run inference on data in BigQuery with the following features:

- A robust SQL editor that provides code completion, query validation, and estimation of bytes processed.
- Embedded Python notebooks built using Colab Enterprise. Notebooks provide one-click Python development runtimes, and built-in support for BigQuery DataFrames.
- A PySpark editor that lets you create stored Python procedures for Apache Spark.
- Asset management and version history for code assets such as notebooks and saved queries, built on top of Dataform.
- Assistive code development in the SQL editor and in notebooks, built on top of Gemini generative AI (Preview).
- Dataplex features for data discovery, and data profiling and data quality scans.
- The ability to view job history on a per-user or per-project basis.
- The ability to analyze saved query results by connecting to other tools such as Looker and Google Sheets, and to export saved query results for use in other applications.

To use BigQuery Studio, follow the instructions at [Enable BigQuery Studio for asset management](https://cloud.google.com/bigquery/docs/bigquery-studio-enabling). This process enables the following APIs:

- The Compute Engine API: required to execute Python functions in your project.
- The Dataform API: required to store code assets, for example notebook files.
- The Vertex AI API: required to execute Colab Enterprise Python notebooks in BigQuery.

## BigQuery ML
BigQuery ML lets you use SQL in BigQuery to perform machine learning (ML) and predictive analytics. For more information, see [Introduction to BigQuery ML](https://cloud.google.com/bigquery-ml/docs/introduction).

## Analytics Tools Integration
In addition to running queries in BigQuery, you can analyze your data with various analytics and business intelligence tools that integrate with BigQuery, such as the following:

- **Looker**. Looker is an enterprise platform for business intelligence, data applications, and embedded analytics. The Looker platform works with many datastores including BigQuery. For information on how to connect Looker to BigQuery, see [Using Looker](https://cloud.google.com/looker).
- **Looker Studio**. After you run a query, you can launch Looker Studio directly from BigQuery in the Google Cloud console. Then, in Looker Studio you can create visualizations and explore the data that's returned from the query. For information about Looker Studio, see [Looker Studio overview](https://cloud.google.com/looker-studio).
- **Connected Sheets**. You can also launch Connected Sheets directly from BigQuery in the console. Connected Sheets runs BigQuery queries on your behalf either upon your request or on a defined schedule. Results of those queries are saved in your spreadsheet for analysis and sharing. For information about Connected Sheets, see [Using connected sheets](https://cloud.google.com/connected-sheets).

## Third-party Tool Integration
Several third-party analytics tools work with BigQuery. For example, you can connect Tableau to BigQuery data and use its visualization tools to analyze and share your analysis. For more information on considerations when using third-party tools, see [Third-party tool integration](https://cloud.google.com/bigquery/partners).

ODBC and JDBC drivers are available and can be used to integrate your application with BigQuery. The intent of these drivers is to help users leverage the power of BigQuery with existing tooling and infrastructure. For information on latest release and known issues, see [ODBC and JDBC drivers for BigQuery](https://cloud.google.com/bigquery/docs/reference/odbc-jdbc-drivers).

The pandas libraries like pandas-gbq let you interact with BigQuery data in Jupyter notebooks. For information about this library and how it compares with using the BigQuery Python client library, see [Comparison with pandas-gbq](https://cloud.google.com/bigquery/docs/pandas-gbq).

You can also use BigQuery with other notebooks and analysis tools. For more information, see [Programmatic analysis tools](https://cloud.google.com/bigquery/docs/programmatic-analysis-tools).

For a full list of BigQuery analytics and broader technology partners, see the [Partners list](https://cloud.google.com/partners) on the BigQuery product page.

## What's Next
- For an introduction and overview of supported SQL statements, see [Introduction to SQL in BigQuery](https://cloud.google.com/bigquery/docs/reference/standard-sql/query-syntax).
- To learn about the GoogleSQL syntax used for querying data in BigQuery, see [Query syntax in GoogleSQL](https://cloud.google.com/bigquery/docs/reference/standard-sql/query-syntax).
- For information about reading the query explain plan, see [Using the query plan explanation](https://cloud.google.com/bigquery/query-plan-explanation).
- To learn how to schedule a recurring query, see [Scheduling queries](https://cloud.google.com/bigquery/docs/scheduling-queries).
