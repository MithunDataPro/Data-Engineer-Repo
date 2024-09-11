# Azure Data Factory (ADF) in Microsoft Fabric

Azure Data Factory (ADF) is a fully managed cloud-based data integration service that allows you to create data-driven workflows for orchestrating and automating data movement and transformation. Microsoft Fabric integrates Azure Data Factory capabilities to provide seamless data orchestration and transformation solutions.

Azure Data Factory in Microsoft Fabric enables various components and tools to work together to facilitate a fully integrated data engineering pipeline. Below, we’ll go through the primary components of ADF, focusing on Pipelines, Data Flows, and additional elements that form the foundation of a comprehensive data solution.

![image](https://github.com/user-attachments/assets/060f3b67-ebc8-43f6-b335-2b7aa0291190)

---

## 1. Pipelines
In Azure Data Factory, **Pipelines** are the fundamental building blocks that define workflows for moving and transforming data. A pipeline is a collection of activities that can ingest data from different sources, process it, and then store it in a designated sink.

### Features of Pipelines:
- **Activity Orchestration**: Pipelines enable you to create a series of activities (such as data movement or transformation activities) that are performed sequentially or in parallel.
- **Data Integration**: Pipelines allow the integration of data from various sources such as databases, file storage systems, cloud services, and more.
- **Automation**: The workflow can be fully automated with triggers (such as schedule-based or event-driven triggers) to execute pipelines at specified intervals or based on events.
- **Error Handling & Retry Logic**: Pipelines include built-in mechanisms for handling errors and retrying failed activities.
- **Linking Services**: A pipeline connects the necessary datasets to the compute resources for data transformation.

In Microsoft Fabric, the ADF Pipelines continue to function similarly, acting as the control hub for all data processing and integration activities.

---

## 2. Data Flows
**Data Flows** in Azure Data Factory are used to visually design data transformations. It is a low-code/no-code solution that enables you to perform simple data transformations through a drag-and-drop interface. In **Microsoft Fabric**, the **Data Flows Zen2** environment brings a similar user-friendly UI experience as in Power Query.

### Features of Data Flows:
- **UI-based Transformations**: The graphical user interface (GUI) allows users to build ETL (Extract, Transform, Load) processes visually, without writing code.
- **Drag and Drop**: Users can drag components to perform tasks like filtering, joining, and aggregating datasets.
- **Zen2 Integration**: Zen2 is a more powerful engine that ensures efficiency in transformation tasks, enhancing the experience for large datasets and complex data.
- **Similar to Power Query**: If you're familiar with Power Query, the data transformations in Fabric Data Flows Zen2 will feel familiar. It shares many of the same visual elements and transformation functionalities.
- **Built-in Optimizations**: Data Flows take care of optimization for your data processing jobs behind the scenes, allowing the pipeline to be executed at scale.

---

## 3. Additional Components of Azure Data Factory in Microsoft Fabric

### Linked Services
Linked Services are the connectors that allow ADF to connect to external sources or destinations such as databases, file systems, cloud services, and more. They act as connection strings to your data and compute resources.

- **Connect to On-Premise & Cloud**: Linked Services allow Azure Data Factory to connect both to on-premises systems and cloud-based systems such as Azure SQL Database, Azure Blob Storage, and others.
- **Authentication Support**: Securely connect to various systems through managed identities, shared keys, or OAuth authentication mechanisms.

---

### Datasets
Datasets in ADF represent the data structures within the sources and destinations. They define the data that will be used within a pipeline activity.

- **Input and Output Definitions**: Datasets represent the inputs and outputs for the activities in a pipeline.
- **Structured Data Handling**: Datasets define the schema and structure of the data, making it easier to map data from one system to another.

---

### Triggers
Triggers in Azure Data Factory are the means by which pipelines are initiated. There are different types of triggers, including schedule-based triggers and event-based triggers.

- **Time-Based Triggers**: Execute pipelines based on specific schedules (hourly, daily, weekly, etc.).
- **Event-Based Triggers**: Execute pipelines based on events, such as file creation in a storage account or other event-driven systems.
- **Custom Triggers**: Use custom logic to invoke pipelines when specific criteria are met.

---

### Integration Runtimes
Integration Runtimes (IR) provide the compute resources that are used to execute the pipeline's activities. Depending on the scenario, the runtime may be cloud-based, self-hosted, or Azure-managed.

- **Azure Integration Runtime**: This is used for cloud-based data movement and transformation.
- **Self-Hosted Integration Runtime**: Allows data movement and transformation between on-premises and cloud systems.
- **SSIS Integration Runtime**: Enables running SSIS packages as part of ADF pipelines.

---

### Monitoring and Alerts
Azure Data Factory comes with built-in monitoring tools that allow you to track pipeline runs, activities, and overall system performance.

- **Run History**: Track the history of your pipeline executions to see where failures or bottlenecks occurred.
- **Alerts & Notifications**: Set up alerts to notify administrators or users of failures, delays, or success statuses.
- **Detailed Logs**: View detailed logs of pipeline activities for troubleshooting or optimization purposes.

---

### Security & Governance
Security is a fundamental part of Azure Data Factory, ensuring that data is protected at every stage of the pipeline.

- **Data Encryption**: Data is encrypted in transit and at rest.
- **Role-Based Access Control (RBAC)**: Use Azure Active Directory (AAD) and role-based access control to grant specific permissions to users, ensuring data access is limited to only those who require it.
- **Data Loss Prevention**: Built-in tools to prevent data breaches and unauthorized access to sensitive information.

---

## Summary
Azure Data Factory in Microsoft Fabric serves as a versatile and scalable data integration service, providing pipelines for orchestrating workflows and data flows for transformation. Whether you are working with structured or unstructured data, ADF offers the tools and services needed to build, automate, and monitor end-to-end data solutions. Microsoft Fabric builds on these capabilities by providing a cohesive and integrated environment to work seamlessly across the cloud.

---

![image](https://github.com/user-attachments/assets/fa1ca91b-0fde-4e54-baa4-2771f3cd24fe)

