# Data Engineering Life Cycle

The Data Engineering Life Cycle involves the following stages:

### 1. **Generation**
- **Source**: Data is generated from websites, sensors, forms/feedback, and analytics.

### 2. **Ingestion**
- **Process**: Data is fetched from multiple sources.

### 3. **Storage**
- **Purpose**: Store all the fetched data for further use.

### 4. **Transformation**
- **Action**: Apply business logic and requirements to process and prepare the data.

### 5. **Serving**
- **Output**: Deliver data for analytics, machine learning, or reverse ETL through systems like data warehouses.

### **Undercurrents**
- Supportive elements like **Security**, **Data Management**, **DataOps**, **Data Architecture**, **Orchestration**, and **Software Engineering** ensure the pipeline runs effectively.

![image](https://github.com/user-attachments/assets/9ebfd331-9724-4417-ad98-8a465a75c131)


----


# What is a Data Warehouse?

A **Data Warehouse** is a centralized repository where data from multiple sources—such as transactional systems (e.g., MySQL, PostgreSQL, Microsoft SQL), applications (e.g., Instagram, Facebook), and external sources—is stored.

The primary purpose of a data warehouse is to support **business intelligence activities**, including:
- Generating **analytics**.
- Producing **reports**.
- Performing **data mining**.


## Characteristics of a Data Warehouse

1. **Subject-Oriented**  
   - Organizes data by specific business subjects (e.g., sales, customers, inventory) rather than by application.

2. **Integrated**  
   - Combines data from multiple sources into a consistent format, ensuring unified definitions and structure.

3. **Time-Variant**  
   - Maintains historical data, allowing tracking of changes over time for better analysis.

4. **Non-Volatile**  
   - Once data is stored, it remains unchanged. Updates are handled through new records rather than overwriting.


## Benefits of a Data Warehouse

1. **Improved Decision Making**  
   - Provides actionable insights by enabling complex analysis and data-driven decisions.

2. **Increased Efficiency**  
   - Simplifies and accelerates access to data for reporting and analytics.

3. **Enhanced Data Quality**  
   - Consolidates and cleanses data, ensuring accuracy and consistency.

4. **Competitive Advantage**  
   - Allows businesses to identify trends and make strategic moves faster than competitors.


### Workflow
1. **ETL Process**: Extract data from sources like CRM, ERP, billing systems, and flat files.
2. **Data Storage**: Centralize in the Data Warehouse.
3. **Output**: Use data for reporting, analytics, and data mining.


![image](https://github.com/user-attachments/assets/ed45531e-8659-4cb4-b4a4-1b512a58d561)

---

# Key Steps in Building a Data Warehouse

1. **Identify the Business Requirements**
   - Understand the goals of the business and the questions the data warehouse should answer.
   - Gather requirements from stakeholders to define the key metrics, dimensions, and data sources.

2. **Design the Dimensional Model**
   - Create a schema that organizes the data for easy querying and analysis.
   - Use a dimensional approach, such as **Star Schema** or **Snowflake Schema**, to model the data.

3. **Implement the ETL Processes**
   - Extract data from various sources.
   - Transform data to meet business requirements and align with the dimensional model.
   - Load data into the data warehouse for storage and access.

4. **Develop Data Access Tools**
   - Build reporting and analytics tools for business users to query and visualize the data.
   - Ensure tools are easy to use and meet the identified requirements.



# Dimensional Modeling: Star and Snowflake Schema

## **Star Schema**
- **Structure**:
  - A central **fact table** contains quantitative data (e.g., sales, revenue).
  - Surrounding **dimension tables** contain descriptive attributes (e.g., product, customer, time).
- **Advantages**:
  - Simpler and faster for querying.
  - Easy to understand and implement.
- **Example**:
  - A sales fact table linked to product, customer, and time dimension tables.

---

## **Snowflake Schema**
- **Structure**:
  - Similar to the star schema but with normalized dimensions.
  - Dimension tables are broken down into sub-tables to reduce redundancy.

#### Note:
# What is Redundancy?

**Redundancy** refers to the duplication of data within a database or data warehouse. 

### Examples of Redundancy:
1. **Repeated Data**: Storing the same information multiple times in different places.
   - Example: The "Customer Name" appears in multiple tables.
2. **Wasted Space**: Unnecessary duplication increases storage requirements.
3. **Potential Errors**: Updates to redundant data in one location might not be reflected in others, causing inconsistencies.

### In Dimensional Modeling:
- In **Star Schema**, redundancy exists because dimension tables are denormalized (e.g., storing full customer details in one table).
- In **Snowflake Schema**, redundancy is minimized by breaking dimensions into smaller tables (normalized dimensions).

---

# What are Normalized Dimensions?

**Normalized Dimensions** involve organizing data into smaller, related tables to remove redundancy and improve storage efficiency.

### Characteristics of Normalized Dimensions:
1. **Atomic Data**: Data is broken into its smallest components.
   - Example: Instead of storing a full address as one field, break it into `Street`, `City`, `State`, and `Postal Code`.
2. **Avoids Duplication**: Data is stored only once and referenced by keys.
3. **Uses Relationships**: Tables are linked via primary and foreign keys.

### Example: Normalized vs. Denormalized

#### **Denormalized Dimension (Redundant)**
| ProductID | ProductName | Category   | CategoryDescription |
|-----------|-------------|------------|---------------------|
| 1         | Laptop      | Electronics| Devices for work    |
| 2         | Smartphone  | Electronics| Devices for work    |
| 3         | Chair       | Furniture  | Items for seating   |

- **Redundancy**: "Electronics" and its description are repeated.

#### **Normalized Dimension**
**Product Table**  
| ProductID | ProductName | CategoryID |
|-----------|-------------|------------|
| 1         | Laptop      | 101        |
| 2         | Smartphone  | 101        |
| 3         | Chair       | 102        |

**Category Table**  
| CategoryID | Category   | CategoryDescription |
|------------|------------|---------------------|
| 101        | Electronics| Devices for work    |
| 102        | Furniture  | Items for seating   |

- **Normalized Structure**: The category data is stored once in the `Category Table` and referenced by `CategoryID` in the `Product Table`.


# Benefits of Normalized Dimensions
1. **Reduced Storage Costs**: Avoids data duplication, saving space.
2. **Data Integrity**: Easier to maintain and update as there’s no duplication.
3. **Flexibility**: Makes the schema more adaptable to changes.



# When to Use Normalization?
- Use normalization when storage efficiency and data integrity are priorities (e.g., **Snowflake Schema**).
- Avoid excessive normalization for analytical workloads where query performance is critical (e.g., **Star Schema**).

- **Advantages**:
  - Saves storage space by normalizing data.
  - More suitable for complex relationships.
- **Example**:
  - A time dimension table split into separate tables for year, month, and day.

---


# ETL Process to Implement Dimensional Models

1. **Extract**
   - Gather data from multiple sources, such as transactional databases, APIs, or flat files.
   - Examples: Sales data from MySQL, customer data from CRM, etc.

2. **Transform**
   - Clean and format the data:
     - Join multiple tables into a single source of truth.
     - Apply business logic (e.g., calculations, deduplication).
   - Map the data to the dimensional model:
     - Identify facts (e.g., sales revenue) and dimensions (e.g., customer details).
     - Normalize data for snowflake schema or denormalize for star schema.

3. **Load**
   - Populate the data warehouse with transformed data.
   - Create fact and dimension tables based on the selected schema (star or snowflake).



# When to Use Star vs. Snowflake Schema
- **Star Schema**:
  - Preferred for simpler and faster querying.
  - Suitable for smaller, straightforward datasets.
- **Snowflake Schema**:
  - Used when data storage efficiency is critical.
  - Ideal for complex data with many interrelationships.



![image](https://github.com/user-attachments/assets/2610ff79-0363-4037-b50a-60c9874e3eb7)

---

# Difference Between OLTP and OLAP

## **OLTP (Online Transaction Processing)**
- **Purpose:** Handles day-to-day transactional operations.
- **Focus:** High volume of short transactions (INSERT, UPDATE, DELETE).
- **Data Type:** Highly normalized data to reduce redundancy.
- **Performance:** Optimized for fast query execution and frequent updates.
- **Examples:** MySQL, PostgreSQL, Microsoft SQL Server.
- **Usage:** Used for operational tasks, such as order processing, inventory management.
- **Query Type:** "Who bought X?" (Transactional details).

---

## **OLAP (Online Analytical Processing)**
- **Purpose:** Supports complex analysis and business intelligence tasks.
- **Focus:** Low volume of long-running queries for data analysis.
- **Data Type:** Denormalized data for faster read operations.
- **Performance:** Optimized for read-heavy operations and aggregations.
- **Examples:** Snowflake, Amazon Redshift, Google BigQuery.
- **Usage:** Used for analytics, reporting, and forecasting.
- **Query Type:** "How many people bought X?" (Aggregated insights).

---

## **Key Differences:**

| Feature                 | OLTP (Online Transaction Processing) | OLAP (Online Analytical Processing)  |
|-------------------------|---------------------------------------|--------------------------------------|
| **Purpose**             | Transactional operations             | Analytical operations               |
| **Focus**               | Fast transactions                   | Complex queries and aggregations    |
| **Data Structure**      | Normalized                          | Denormalized                        |
| **Query Type**          | Short and simple queries            | Long and complex queries            |
| **Performance**         | Optimized for transactions          | Optimized for analytics             |
| **Examples**            | MySQL, PostgreSQL, Oracle DB        | Snowflake, Amazon Redshift, BigQuery|
| **Usage**               | Operational systems (e.g., CRM, ERP)| Decision support and business intelligence |
| **Data Volume**         | Smaller, real-time                  | Larger, historical                  |

---

## **Summary:**
- **OLTP** is designed for **real-time transactional systems** where speed and accuracy are critical.
- **OLAP** is designed for **data analysis and decision-making**, prioritizing complex queries and insights over real-time processing.



![image](https://github.com/user-attachments/assets/5bece35d-627d-43c0-a4fc-6e265624c49b)

---
