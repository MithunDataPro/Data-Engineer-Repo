# Microsoft Fabric: In-Depth Overview

## What is Microsoft Fabric?
Microsoft Fabric is an end-to-end analytics and data platform designed for enterprises that require a unified solution. It encompasses data movement, processing, ingestion, transformation, real-time event routing, and report building. It offers a comprehensive suite of services including Data Engineering, Data Factory, Data Science, Real-Time Analytics, Data Warehouse, and Databases.

With Fabric, you don't need to assemble different services from multiple vendors. Instead, it offers a seamlessly integrated, user-friendly platform that simplifies your analytics requirements. Operating on a Software as a Service (SaaS) model, Fabric brings simplicity and integration to your solutions.

Microsoft Fabric integrates separate components into a cohesive stack. Instead of relying on different databases or data warehouses, you can centralize data storage with OneLake. AI capabilities are seamlessly embedded within Fabric, eliminating the need for manual integration. With Fabric, you can easily transition your raw data into actionable insights for business users.

![image](https://github.com/user-attachments/assets/1596d39d-2183-478f-974e-51eed6e313b3)

## Unification with SaaS foundation:

Microsoft Fabric is built on a foundation of Software as a Service (SaaS). It combines both new and existing components from Power BI, Azure Synapse Analytics, Azure Data Factory, and more services into a unified environment. These components are then tailored into customized user experiences.

![image](https://github.com/user-attachments/assets/9a892320-af6a-4777-a385-883e893ae9b6)

Fabric integrates workloads such as Data Engineering, Data Factory, Data Science, Data Warehouse, Real-Time Intelligence, Industry solutions, and Power BI into a shared SaaS foundation. Each of these experiences is tailored for distinct user roles like data engineers, scientists, or warehousing professionals, and they serve a specific task. The entire Fabric stack has AI integration and it accelerates the data journey. These workloads work together seemlessly and provide the following advantages:

Access to an extensive range of deeply integrated analytics in the industry.
Shared experiences across experiences that are familiar and easy to learn.
Easy access to, and readily reuse all assets.
Unified data lake storage that preserves data in its original location while using your preferred analytics tools.
Centralized administration and governance across all experiences.
Fabric seamlessly integrates data and services, enabling unified management, governance, and discovery. It ensures security for items, data, and row-level access. You can centrally configure core enterprise capabilities. Permissions are automatically applied across all the underlying services. Additionally, data sensitivity labels inherit automatically across the items in the suite. Governance is powered by Purview, which is built into Fabric.

Fabric allows creators to concentrate on producing their best work, freeing them from the need to integrate, manage, or even understand the underlying infrastructure.

---

## Components of Microsoft Fabric:

Fabric offers a comprehensive set of analytics experiences designed to work together seamlessly. The platform tailors each of these experiences to a specific persona and a specific task:

![image](https://github.com/user-attachments/assets/9b3f423e-d612-4966-9004-48eb609a8f79)

# Microsoft Fabric - Key Components and Features

## Power BI
Power BI lets you easily connect to your data sources, visualize, and discover what's important, and share that with anyone or everyone you want. This integrated experience allows business owners to access all data in Fabric quickly and intuitively, enabling them to make better decisions with data.  
For more information, see [What is Power BI?](https://docs.microsoft.com/power-bi/).

## Data Factory
Data Factory provides a modern data integration experience to ingest, prepare, and transform data from a rich set of data sources. It incorporates the simplicity of Power Query, and you can use more than 200 native connectors to connect to data sources on-premises and in the cloud.  
For more information, see [What is Data Factory in Microsoft Fabric?](https://docs.microsoft.com/data-factory/).

## Data Activator
Data Activator is a no-code experience in Fabric that allows you to specify actions, such as email notifications and Power Automate workflows, to launch when Data Activator detects specific patterns or conditions in your changing data. It monitors data in Power BI reports and eventstreams; when the data hits certain thresholds or matches other patterns, it automatically takes the appropriate action.  
For more information, see [What is Data Activator?](https://docs.microsoft.com/data-activator/).

## Industry Solutions
Fabric provides industry-specific data solutions that address unique industry needs and challenges. These solutions include data management, analytics, and decision-making capabilities.  
For more information, see [Industry Solutions in Microsoft Fabric](https://docs.microsoft.com/industry-solutions/).

## Real-Time Intelligence
Real-Time Intelligence is an end-to-end solution for event-driven scenarios, streaming data, and data logs. It enables the extraction of insights, visualization, and action on data in motion by handling data ingestion, transformation, storage, analytics, visualization, tracking, AI, and real-time actions. The Real-Time hub in Real-Time Intelligence provides a wide variety of no-code connectors, converging into a catalog of organizational data that is protected, governed, and integrated across Fabric.  
For more information, see [What is Real-Time Intelligence in Fabric?](https://docs.microsoft.com/real-time-intelligence/).

## Synapse Data Engineering
Synapse Data Engineering provides a Spark platform with great authoring experiences. It enables you to create, manage, and optimize infrastructures for collecting, storing, processing, and analyzing vast data volumes. Fabric Spark's integration with Data Factory allows you to schedule and orchestrate notebooks and Spark jobs.  
For more information, see [What is Data Engineering in Microsoft Fabric?](https://docs.microsoft.com/synapse-data-engineering/).

## Synapse Data Science
Synapse Data Science enables you to build, deploy, and operationalize machine learning models from Fabric. It integrates with Azure Machine Learning to provide built-in experiment tracking and model registry. Data scientists can enrich organizational data with predictions, and business analysts can integrate those predictions into their BI reports, allowing a shift from descriptive to predictive insights.  
For more information, see [What is Data Science in Microsoft Fabric?](https://docs.microsoft.com/synapse-data-science/).

## Synapse Data Warehouse
Synapse Data Warehouse provides industry-leading SQL performance and scale. It separates compute from storage, enabling independent scaling of both components. Additionally, it natively stores data in the open Delta Lake format.  
For more information, see [What is Data Warehousing in Microsoft Fabric?](https://docs.microsoft.com/synapse-data-warehouse/).

## Microsoft Fabric and Data Mesh Architecture
Microsoft Fabric enables organizations and individuals to turn large and complex data repositories into actionable workloads and analytics. It is an implementation of the **data mesh architecture**, designed to provide decentralized and domain-driven data management.


---

![image](https://github.com/user-attachments/assets/ca01e22c-aaf3-48e6-9dc1-c3aa82946f6c)

---

# Microsoft Fabric: OneLake and Real-Time Hub

## OneLake: The Unification of Lakehouses
The Microsoft Fabric platform unifies the OneLake and lakehouse architecture across an enterprise.

### What is OneLake?
A data lake is the foundation on which all the Fabric workloads are built. Microsoft Fabric Lake is also known as **OneLake**. OneLake is built into the Fabric platform and provides a unified location to store all organizational data where the workloads operate.

- **Built on ADLS (Azure Data Lake Storage) Gen2**: OneLake provides a single SaaS experience and a tenant-wide store for data, serving both professional and citizen developers. 
- **Simplified Experience**: OneLake simplifies Fabric experiences by eliminating the need to understand infrastructure concepts such as resource groups, RBAC (Role-Based Access Control), Azure Resource Manager, redundancy, or regions. You don't need an Azure account to use Fabric.
- **Eliminating Data Silos**: OneLake eliminates data silos that individual developers often create when provisioning their own storage accounts. Instead, it provides a unified storage system for all developers, ensuring easy data discovery, sharing, and uniform enforcement of policy and security settings.  
For more information, see [What is OneLake?](https://docs.microsoft.com/onelake/).

### OneLake and Lakehouse Data Hierarchy
OneLake is hierarchical in nature to simplify management across your organization. There's only **one OneLake per tenant**, and it provides a single-pane-of-glass file-system namespace that spans across users, regions, and clouds. OneLake organizes data into manageable containers for easy handling.

- **Tenant**: The tenant maps to the root of OneLake and is at the top level of the hierarchy.
- **Workspaces**: You can create multiple workspaces (similar to folders) within a tenant. 
- **Lakehouses**: A lakehouse is a collection of files, folders, and tables that represent a database over a data lake.

![image](https://github.com/user-attachments/assets/be76d4be-fad3-4714-8999-43ebbc2885ad)

Every developer and business unit in the tenant can easily create their own workspaces in OneLake, ingest data into their own lakehouses, and start processing, analyzing, and collaborating on the data—similar to how OneDrive works in Microsoft Office.

For more information, see [What is a lakehouse?](https://docs.microsoft.com/lakehouse/).

### OneLake Integration
All Microsoft Fabric compute experiences, such as **Data Engineering**, **Data Warehouse**, **Data Factory**, **Power BI**, and **Real-Time Intelligence**, are prewired to OneLake. These experiences use OneLake as their native store without requiring extra configuration.

- **Shortcut Feature**: OneLake allows instant mounting of your existing Platform as a Service (PaaS) storage accounts into OneLake with the Shortcut feature. No need to migrate or move your existing data. You can use shortcuts to access data stored in **Azure Data Lake Storage**.
- **Data Sharing**: Shortcuts allow easy sharing of data between users and applications without duplicating information. You can create shortcuts to other storage systems, enabling you to compose and analyze data across clouds with transparent, intelligent caching that reduces egress costs and brings data closer to compute.

![image](https://github.com/user-attachments/assets/a7fdb518-11ce-4346-8c54-1f324214c523)

---

## Real-Time Hub: The Unification of Data Streams
The Real-Time hub is the central location for handling **data-in-motion** in Microsoft Fabric.

### What is the Real-Time Hub?
The Real-Time hub provides a unified SaaS experience and a tenant-wide logical place for all data-in-motion. It lists all data streams from various sources, allowing customers to discover, ingest, manage, and react to data streams.

- **Supported Streams**: Includes data streams, Microsoft sources (e.g., Azure Event Hubs, Azure IoT Hub, Azure SQL DB CDC, Azure Cosmos DB CDC, PostgreSQL DB CDC), and Fabric events (both system and external events from Azure, Microsoft 365, or other clouds).
- **Centralized Management**: The Real-Time hub enables users to easily discover, ingest, manage, and consume data-in-motion from a wide variety of sources, so that they can collaborate and develop streaming applications within a single location.

For more information, see [What is the Real-Time Hub?](https://docs.microsoft.com/real-time-hub/).

---

## Fabric Solutions for ISVs
Microsoft Fabric offers flexible integration paths for Independent Software Vendors (ISVs) looking to incorporate their solutions into the Fabric ecosystem. ISVs can choose one of the following integration paths:

### 1. **Interop**
Integrate your solution with the OneLake Foundation, establishing basic connections and interoperability with Fabric.

### 2. **Develop on Fabric**
Build your solution on top of the Fabric platform or seamlessly embed Fabric's functionalities into your existing applications. Fabric capabilities are easily accessible in this integration path.

### 3. **Build a Fabric Workload**
Create customized workloads and experiences in Fabric, tailoring your offerings to maximize their impact within the Fabric ecosystem.

For more information, see the [Fabric ISV Partner Ecosystem](https://docs.microsoft.com/isv-ecosystem/).

---

## Related Content
- [Microsoft Fabric Terminology](https://docs.microsoft.com/fabric-terminology/)
- [Create a Workspace](https://docs.microsoft.com/create-workspace/)
- [Navigate to Your Items from the Microsoft Fabric Home Page](https://docs.microsoft.com/fabric-home/)
- [End-to-End Tutorials in Microsoft Fabric](https://docs.microsoft.com/fabric-tutorials/)

---

## Microsoft Fabric Architecture

The architecture of **Microsoft Fabric** is designed around three key pillars:
1. **Data Engineering**:
   - Data ingestion, transformation, and movement of large-scale data using **Data Factory** and **Synapse Data Engineering**.
   - **Delta Lake** is used for storing clean data in a structured, scalable way.

2. **Data Science**:
   - Advanced analytics and machine learning processes are powered by **Synapse Data Science**, where users can build ML models on top of ingested and transformed data.

3. **Data Analysis**:
   - Tools like **Power BI** and **Data Activator** are used to visualize and analyze the data in real-time and provide business insights. Users can also set up alerts based on analytics outputs.

- **Serverless Compute**: Microsoft Fabric uses serverless compute, meaning you only pay for what you use, and there's no need for infrastructure management.
- **One Lake**: The platform supports **One Lake**, which is a unified storage system where all the data ingested or transformed is stored, making it easier to query and process at scale.

![image](https://github.com/user-attachments/assets/474f9c4c-92a1-4d2e-8c57-df2c646621c3)

---

![image](https://github.com/user-attachments/assets/357b6d54-2830-488f-9c5a-f3e5880ae68d)

---

## Difference Between Microsoft Fabric & Azure Cloud

- **Unified Experience**: 
   - Microsoft Fabric integrates various tools like Data Factory, Synapse, Power BI, etc., into a single environment, providing end-to-end data analytics solutions. 
   - Azure Cloud, on the other hand, offers a wide array of standalone services for various cloud needs, such as storage, computing, networking, and app development.

- **Scope**:
   - Microsoft Fabric is heavily focused on **data analytics**, processing, and insights.
   - Azure Cloud is a broader platform that covers all aspects of cloud computing (e.g., Virtual Machines, IoT services, AI models, etc.).

- **Management**:
   - Microsoft Fabric offers **managed services** in a unified dashboard. Azure provides more flexibility but requires the management of individual services.

---

## What Can Be Built Using Microsoft Fabric?

- **End-to-End Data Analytics Pipelines**: Ingesting raw data, transforming it, performing machine learning tasks, and visualizing it all in one place.
- **Real-Time Data Streaming**: Using tools like **Synapse Real-Time Analytics**, you can process real-time data streams and provide up-to-date insights or trigger alerts.
- **Predictive Models**: With **Synapse Data Science**, you can build predictive models and integrate them with live data streams.
- **Business Intelligence Platforms**: **Power BI** can be leveraged to create advanced dashboards for stakeholders, powered by real-time data feeds from Synapse Analytics.

---

## Advantages & Disadvantages of Microsoft Fabric

### Advantages:
- **Unified Platform**: All tools required for data ingestion, transformation, analytics, and visualization are available under one roof.
- **Scalability**: Automatically scales with data volume, thanks to its serverless architecture.
- **Real-Time Processing**: Built-in capabilities to process streaming data in real-time.
- **No Infrastructure Management**: Fully managed services mean that users don’t have to worry about infrastructure complexities.
- **Tight Integration**: Seamless integration with Microsoft products like Power BI and Azure Machine Learning.

### Disadvantages:
- **Learning Curve**: Although it simplifies processes, users need to learn how to navigate between tools and services.
- **Azure Dependency**: It is heavily reliant on the Azure ecosystem. Users must already be familiar with Microsoft Azure services.
- **Cost**: The pricing model can escalate depending on the number of resources used, which might be a drawback for small-scale projects.

---

## Companies Currently Using Microsoft Fabric

While **Microsoft Fabric** is relatively new, many organizations already leveraging **Microsoft Synapse Analytics** and **Power BI** are incorporating Fabric into their data pipelines. Examples include:

- **Financial Institutions**: Using it for real-time transaction monitoring and risk assessment.
- **Retail Chains**: To manage large datasets across distributed stores, providing insights into sales, inventory, and customer behaviors in real-time.
- **Healthcare Providers**: Using real-time analytics to track patient data and enhance service delivery.
- **Manufacturing Firms**: Implementing predictive maintenance models and production efficiency tracking with real-time data streams.

---

# Microsoft Fabric Terminology

Learn the definitions of terms used in Microsoft Fabric, including terms specific to Synapse Data Warehouse, Synapse Data Engineering, Synapse Data Science, Real-Time Intelligence, Data Factory, and Power BI.

## General Terms

### Capacity:
Capacity is a dedicated set of resources that is available at a given time to be used. Capacity defines the ability of a resource to perform an activity or to produce output. Different items consume different capacity at a certain time. Fabric offers capacity through the Fabric SKU and Trials. For more information, see What is capacity?

### Experience:
A collection of capabilities targeted to a specific functionality. The Fabric experiences include Synapse Data Warehouse, Synapse Data Engineering, Synapse Data Science, Real-Time Intelligence, Data Factory, and Power BI.

### Item:
An item a set of capabilities within an experience. Users can create, edit, and delete them. Each item type provides different capabilities. For example, the Data Engineering experience includes the lakehouse, notebook, and Spark job definition items.

### Tenant:
A tenant is a single instance of Fabric for an organization and is aligned with a Microsoft Entra ID.

### Workspace:
A workspace is a collection of items that brings together different functionality in a single environment designed for collaboration. It acts as a container that uses capacity for the work that is executed, and provides controls for who can access the items in it. For example, in a workspace, users create reports, notebooks, semantic models, etc. For more information, see Workspaces article.

## Synapse Data Engineering

### Lakehouse:
A lakehouse is a collection of files, folders, and tables that represent a database over a data lake used by the Apache Spark engine and SQL engine for big data processing. A lakehouse includes enhanced capabilities for ACID transactions when using the open-source Delta formatted tables. The lakehouse item is hosted within a unique workspace folder in Microsoft OneLake. It contains files in various formats (structured and unstructured) organized in folders and subfolders. For more information, see What is a lakehouse?

### Notebook:
A Fabric notebook is a multi-language interactive programming tool with rich functions. Which include authoring code and markdown, running and monitoring a Spark job, viewing and visualizing result, and collaborating with the team. It helps data engineers and data scientist to explore and process data, and build machine learning experiments with both code and low-code experience. It can be easily transformed to a pipeline activity for orchestration.

### Spark application:
An Apache Spark application is a program written by a user using one of Spark's API languages (Scala, Python, Spark SQL, or Java) or Microsoft-added languages (.NET with C# or F#). When an application runs, it's divided into one or more Spark jobs that run in parallel to process the data faster. For more information, see Spark application monitoring.

### Apache Spark job:
A Spark job is part of a Spark application that is run in parallel with other jobs in the application. A job consists of multiple tasks. For more information, see Spark job monitoring.

### Apache Spark job definition:
A Spark job definition is a set of parameters, set by the user, indicating how a Spark application should be run. It allows you to submit batch or streaming jobs to the Spark cluster. For more information, see What is an Apache Spark job definition?

### V-order:
A write optimization to the parquet file format that enables fast reads and provides cost efficiency and better performance. All the Fabric engines write v-ordered parquet files by default.

## Data Factory

### Connector:
Data Factory offers a rich set of connectors that allow you to connect to different types of data stores. Once connected, you can transform the data. For more information, see connectors.

### Data pipeline:
In Data Factory, a data pipeline is used for orchestrating data movement and transformation. These pipelines are different from the deployment pipelines in Fabric. For more information, see Pipelines in the Data Factory overview.

### Dataflow Gen2:
Dataflows provide a low-code interface for ingesting data from hundreds of data sources and transforming your data. Dataflows in Fabric are referred to as Dataflow Gen2. Dataflow Gen1 exists in Power BI. Dataflow Gen2 offers extra capabilities compared to Dataflows in Azure Data Factory or Power BI. You can't upgrade from Gen1 to Gen2. For more information, see Dataflows in the Data Factory overview.

### Trigger:
An automation capability in Data Factory that initiates pipelines based on specific conditions, such as schedules or data availability.

## Synapse Data Science

### Data Wrangler:
Data Wrangler is a notebook-based tool that provides users with an immersive experience to conduct exploratory data analysis. The feature combines a grid-like data display with dynamic summary statistics and a set of common data-cleansing operations, all available with a few selected icons. Each operation generates code that can be saved back to the notebook as a reusable script.

### Experiment:
A machine learning experiment is the primary unit of organization and control for all related machine learning runs. For more information, see Machine learning experiments in Microsoft Fabric.

### Model:
A machine learning model is a file trained to recognize certain types of patterns. You train a model over a set of data, and you provide it with an algorithm that it uses to reason over and learn from that data set. For more information, see Machine learning model.

### Run:
A run corresponds to a single execution of model code. In MLflow, tracking is based on experiments and runs.

## Synapse Data Warehouse

### SQL analytics endpoint:
Each Lakehouse has a SQL analytics endpoint that allows a user to query delta table data with TSQL over TDS. For more information, see SQL analytics endpoint.

### Synapse Data Warehouse:
The Synapse Data Warehouse functions as a traditional data warehouse and supports the full transactional T-SQL capabilities you would expect from an enterprise data warehouse. For more information, see Synapse Data Warehouse.

## Real-Time Intelligence

### KQL database:
The KQL database holds data in a format that you can execute KQL queries against. For more information, see Query a KQL database.

### KQL Queryset:
The KQL Queryset is the item used to run queries, view results, and manipulate query results on data from your Data Explorer database. The queryset includes the databases and tables, the queries, and the results. The KQL Queryset allows you to save queries for future use, or export and share queries with others. For more information, see Query data in the KQL Queryset.

### Event stream:
The Microsoft Fabric event streams feature provides a centralized place in the Fabric platform to capture, transform, and route real-time events to destinations with a no-code experience. An event stream consists of various streaming data sources, ingestion destinations, and an event processor when the transformation is needed. For more information, see Microsoft Fabric event streams.

## OneLake

### Shortcut:
Shortcuts are embedded references within OneLake that point to other file store locations. They provide a way to connect to existing data without having to directly copy it. For more information, see OneLake shortcuts.

## Related Content
- Navigate to your items from Microsoft Fabric Home page
- Discover data items in the OneLake data hub
- End-to-end tutorials in Microsoft Fabric

