# Introduction to BigQuery Administration

This document provides an introduction to BigQuery administration tasks, and the BigQuery features that help you accomplish them.

BigQuery administrators typically do the following types of tasks:

- Manage resources, such as projects, datasets, and tables.
- Secure resources, so that access is limited to the principals who need it.
- Manage workloads, such as jobs, queries, and compute capacity (reservations).
- Monitor resources, including quotas, jobs, and compute usage.
- Optimize workloads for best performance while controlling costs.
- Troubleshoot error messages, billing issues, and quotas.

This document gives an overview of the features that BigQuery provides to help you do these tasks.

To take a tour of BigQuery data administration features directly in the Google Cloud console, click Take the tour.

[Take the tour](https://console.cloud.google.com/getting-started?walkthrough_id=bigquery--ui-tour-data-admin&_ga=2.19943352.1667553385.1726962123-174588950.1726962123)

## Tools
BigQuery provides several interfaces you can use for administration tasks. Often a particular task can be done with multiple tools, letting you choose the tool that works best for you. For example, you can create a table by using the Explorer pane in the Google Cloud console, a `bq mk --table` command, or a `CREATE TABLE` SQL statement.

- **Google Cloud console**: The Google Cloud console has several pages dedicated to BigQuery administration. For more information, see [Use the Google Cloud console](https://cloud.google.com/bigquery/docs/reference-ui).
- **SQL statements**: The BigQuery page in the Google Cloud console has a query editor where you can do administrative tasks by using DDL and DCL statements. For more information, see [Data definition language (DDL)](https://cloud.google.com/bigquery/docs/reference/standard-sql/data-definition-language) and [Data control language (DCL)](https://cloud.google.com/bigquery/docs/reference/standard-sql/data-control-language).

You can use stored procedures to automate administration tasks that use SQL statements. For more information, see [Work with stored procedures](https://cloud.google.com/bigquery/docs/reference/standard-sql/scripting).

- **bq commands**: The `bq` command-line tool lets you do many administrative tasks by using `bq` commands. You can use the `bq` command-line tool to do tasks that aren't supported in the Google Cloud console, to prototype capabilities before encoding them in queries or API methods, or if you prefer working in a command-line interface. For more information, see [Use the bq command-line tool](https://cloud.google.com/bigquery/docs/reference/bq-cli-reference).

## Manage Resources
BigQuery resources include organizations, folders, projects, datasets, and tables. This section describes how to manage your organization's resources.

For information about the BigQuery resource hierarchy, see [Organize BigQuery resources](https://cloud.google.com/bigquery/docs/resource-hierarchy). In particular, you can create an Organization resource, which lets you do some tasks, such as setting access controls, at the organization level.

### Manage Datasets
Datasets are containers for tables. You can create tables in a dataset, and then manage them as a group. For example, you can configure a dataset's default table expiration time, which applies to all tables in the dataset unless you override it. You can copy a group of tables by making a copy of their dataset, and you can control access to tables at the dataset level.

Refer to the following documents for more information about dataset administration:

- For more information about creating, copying, moving, and updating datasets, see [Introduction to datasets](https://cloud.google.com/bigquery/docs/datasets-intro).
- For more information about dataset-level access control, see [Controlling access to datasets](https://cloud.google.com/bigquery/docs/dataset-access-control) and [Authorized datasets](https://cloud.google.com/bigquery/docs/authorized-datasets).

### Manage Tables
In BigQuery, data is stored in tables, where it can be queried. You can create tables, load data into tables from various types of sources and in various formats, partition tables based on a specific column or by ingestion time, cluster tables, update table properties, and export table data.

Refer to the following documents for more information about table administration:

- For more information about loading data into BigQuery tables, see [Introduction to loading tables](https://cloud.google.com/bigquery/docs/loading-data).
- For more information about managing tables and exporting table data, see [Introduction to tables](https://cloud.google.com/bigquery/docs/tables-intro).
- For more information about partitioning and clustering tables, see [Introduction to partitioned tables](https://cloud.google.com/bigquery/docs/partitioned-tables) and [Introduction to clustered tables](https://cloud.google.com/bigquery/docs/clustered-tables).

### Label Resources
To help organize your BigQuery resources, you can add labels to your datasets, tables, and views. Labels are key-value pairs that you can attach to a resource. After labeling your resources, you can search for them based on label values. For example, you could use labels to group datasets by department by adding labels like `dept:sales`, `dept:marketing`, or `dept:analytics`. Then you could break down your billed charges by department using the labels.

For more information, see [Introduction to labels](https://cloud.google.com/resource-manager/docs/creating-managing-labels).

### Get Resource Information
You can get information about your BigQuery resources by querying the `INFORMATION_SCHEMA` views. BigQuery provides views for each resource type. For example, the `INFORMATION_SCHEMA.TABLES` view contains information about your tables.

The following are a few examples of information you can obtain by querying `INFORMATION_SCHEMA` views:

- See when a table was created.
- Get the names and data types of each column in a table.
- Find all of the jobs running in a project.
- Get a list of the table snapshots that were created from a base table.
- For a dataset, table, view, or routine, get the DDL statement that can be used to create the resource.
- Get the options that were used to create a table (for example, table expiration).
- Find the partitioning and clustering columns on a table.
- Get a project's assigned reservation and its slot capacity.

For more information, see [Introduction to BigQuery INFORMATION_SCHEMA](https://cloud.google.com/bigquery/docs/information-schema-intro).

### Copy Data
You might want to create copies of your data for various reasons, such as protection from human error, or to retain data for comparison in the future. BigQuery provides several options for copying a table's data from a particular point in time.

- **Time travel**. You might need to access a table's state as it was sometime within the past week; for example, if the data became corrupted due to human error. BigQuery retains historical data for your tables for seven days. You can access a table's recent historical data by using the time travel feature. For more information, see [Access historical data using time travel](https://cloud.google.com/bigquery/docs/time-travel).
- **Table snapshots**. If you want to be able to access a table's state from earlier than one week in the past, consider creating table snapshots periodically. Table snapshots are lightweight, read-only copies that let you preserve the state of your tables indefinitely. With table snapshots, for example, you can compare a table's current data to the data from the beginning of the year, which isn't possible by using time travel. You are only charged for storing the data that differs between the base table and its table snapshot. For more information, see [Introduction to table snapshots](https://cloud.google.com/bigquery/docs/table-snapshots-intro).
- **Table clones**. If you want to make a lightweight, writable copy of a table, you can use table clones. You only pay for storage of the data that differs between a base table and its table clone. For example, you could create table clones in a test environment so that you can experiment with copies of production data without impacting the production data and without having to pay for storage of full copies of the tables. For more information, see [Introduction to table clones](https://cloud.google.com/bigquery/docs/table-clones-intro).

### Track Data Lineage
Data lineage is a Dataplex feature that lets you track how data moves through your systems: where it comes from, where it is passed to, and what transformations are applied to it. For more information about how data lineage can help you track data movement in your project, see [About data lineage in Dataplex](https://cloud.google.com/dataplex/docs/data-lineage).

## Secure Resources
BigQuery security is based on Google Cloud Identity and Access Management. BigQuery lets you control access to your resources at many levels, including access to the organization, folders, projects, datasets, tables, table columns, and table rows.

For information about controlling access to your BigQuery resources, see [Overview of data security and governance](https://cloud.google.com/security).

## Manage Workloads
BigQuery does many tasks on behalf of your users, including ingesting, querying, and exporting data. Each task is done by a BigQuery job. This section describes how you can monitor and manage your organization's jobs.

### Manage Jobs
Jobs are actions that BigQuery runs on a user's behalf to load, export, query, or copy data. When a user initiates one of these tasks by using the Google Cloud console, the bq command-line tool, a SQL statement, or an API call, BigQuery automatically creates a job to execute the task.

As a BigQuery administrator, you can monitor, manage, and troubleshoot your organization's jobs to ensure they are running smoothly.

For more information, see [Jobs overview](https://cloud.google.com/bigquery/docs/jobs-overview).

### Manage Reservations
When BigQuery executes queries, it uses units of computing called slots. BigQuery calculates how many slots are needed to run each query, depending on the size and complexity of the query.

BigQuery has two pricing models for charging for the slots that run your queries:

- **On-demand billing**. Your queries use a shared pool of slots, and you are charged for the number of bytes your queries process.
- **Capacity-based billing**. You assign a reservation or capacity commitment to an edition, each of which comes with their own feature set and price point to provide the best working environment for you.

These pricing models apply per project, so you can have some projects that use on-demand billing and some projects that use capacity-based billing.

With on-demand billing, after your monthly allocation of free usage is consumed, you are charged for the number of bytes that each query processes. Throughput is limited to a predefined slot quota, which is shared among the queries that run in a project.

With BigQuery editions billing, you allocate slots for your organization through autoscaling reservations and optional, but cheaper, capacity commitments. Slots for each edition come at their own price point, and offer their own set of features. For more information about BigQuery editions and the features that are associated with them, see [Introduction to BigQuery editions](https://cloud.google.com/bigquery/docs/editions-intro).

Refer to the following documents for more information about managing compute capacity for processing your queries:

- For slots, and the trade-offs between on-demand billing and capacity-based billing, see [Introduction to reservations](https://cloud.google.com/bigquery/docs/reservations-intro).
- For the different options for capacity-based billing (monthly or annual commitments), see [Commitments](https://cloud.google.com/bigquery/docs/commitments).
- For creating pools of capacity-based slots, called slot reservations, see [Work with slot reservations](https://cloud.google.com/bigquery/docs/reservations-intro).
- For allocating slot reservations to specific projects, see [Work with reservation assignments](https://cloud.google.com/bigquery/docs/reservation-assignments).
- For estimating the right number of slots to allocate to your workloads, see [Estimate slot capacity requirements](https://cloud.google.com/bigquery/docs/slots-requirements).

## Monitor Resources
Google Cloud provides the capability to monitor and audit your resources, including BigQuery resources. This section describes the Google Cloud monitoring and auditing capabilities that apply to BigQuery.

For more information, see [Introduction to BigQuery monitoring](https://cloud.google.com/bigquery/docs/monitoring-intro).

### The Cloud Monitoring Dashboard
Cloud Monitoring provides a dashboard for monitoring BigQuery. Use this dashboard to view information about BigQuery incidents, datasets, tables, projects, query times, and slot utilization.

For more information, see [View the Monitoring dashboard](https://cloud.google.com/monitoring/dashboards).

### Administration Charts and Alerts
You can use Cloud Monitoring to create custom charts based on the resources, metrics, and any aggregation that you specify.

For more information, see [Dashboards and charts](https://cloud.google.com/monitoring/charts).

You can also create alert policies that notify you if the configured alert is triggered. For example, you could create an alert that sends an email to a specified email address if the execution time of a query exceeds a specified limit.

For more information, see [Creating an alert](https://cloud.google.com/monitoring/alerts).

### Monitor Reservations
You can monitor your slot usage on the Capacity management page of the Google Cloud console. You can view your capacity commitments and see where your slot reservations have been assigned. You can also use the Slot estimator (Preview) to help you estimate your organization's capacity requirements based on historical performance metrics.

For more information, see [Monitoring BigQuery reservations](https://cloud.google.com/bigquery/docs/reservations-monitoring).

### Quotas
Google Cloud sets limits on the use of resources, including BigQuery resources, both to ensure fair usage of shared resources, and to protect you from runaway costs. You can view your usage of BigQuery resources that have quotas, and request a higher quota, if needed, by using the Google Cloud console.

For more information, see [BigQuery quotas and limits](https://cloud.google.com/bigquery/quotas).

### Audit Logs
Cloud Audit Logs maintain a record of Google Cloud events, including BigQuery events. You can use the Logs Explorer to query the logs about events related to BigQuery jobs, datasets, transfers, and more. The Logs Dashboard displays information about recent errors, and you can use Logs-based metrics to count the log entries that match a given filter.

For more information, see the [Google Cloud logging documentation](https://cloud.google.com/logging/docs).

## Optimize Workloads
You can optimize your BigQuery configuration to control both storage and query processing costs.

- For assistance managing your BigQuery storage costs, see [Optimize storage in BigQuery](https://cloud.google.com/bigquery/docs/optimizing-storage).
- For assistance managing your BigQuery processing costs, see [Control costs in BigQuery](https://cloud.google.com/bigquery/docs/billing).
- For assistance optimizing your BigQuery queries, see [Introduction to optimizing query performance](https://cloud.google.com/bigquery/docs/query-optimization-intro).
- For general information about BigQuery costs, see [BigQuery pricing](https://cloud.google.com/bigquery/pricing) and [BigQuery billing questions](https://cloud.google.com/bigquery/docs/billing).

## Reliability Guidance
This document provides an understanding of BigQuery reliability, including insight into availability, durability, data consistency, consistency of performance, and data recovery in BigQuery, as well as a review of error handling considerations. To learn more about reliability and disaster planning, see [Understand reliability](https://cloud.google.com/bigquery/docs/reliability-intro).

## Troubleshoot
In addition to the features described in this document for monitoring and managing your organization's BigQuery system, the following resources are available for troubleshooting problems that might arise:

- [BigQuery error messages](https://cloud.google.com/bigquery/docs/error-messages)
- [BigQuery billing questions](https://cloud.google.com/bigquery/docs/billing)
- [Troubleshoot quota errors](https://cloud.google.com/bigquery/docs/quotas)
  
If you need additional assistance, see [Get support](https://cloud.google.com/support).

## What's Next
For a video series on various topics related to BigQuery administration, see [BigQuery admin reference guide: recap](https://cloud.google.com/bigquery/admin-guide).

