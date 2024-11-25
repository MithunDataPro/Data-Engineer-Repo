# Database History & Overview

To store data in systems for better scalability and performance, companies began building **Database Management Systems (DBMS)** like **MySQL**, **PostgreSQL**, and **Microsoft SQL Server**. These systems have revolutionized how data is stored, accessed, and managed efficiently.

## Types of Databases
There are two primary types of databases:
1. **SQL Databases**
2. **NoSQL Databases**

### SQL Databases (Relational or OLAP Databases)
SQL databases use structured schemas to store and manage data. These are ideal for handling structured data with defined relationships, making them a core tool for data engineers. 

### NoSQL Databases (Schema-less Databases)
NoSQL databases do not require a predefined schema. They support a variety of data formats such as **Dictionary**, **JSON**, and other flexible structures. These are well-suited for handling unstructured or semi-structured data.

#### Types of NoSQL Databases:
- **Document Databases**: Store data in document formats like JSON.
- **Key-Value Stores**: Use a simple key-value pair mechanism for data storage.
- **Wide-Column Stores**: Data is stored in tables but with flexible column definitions.
- **Graph Databases**: Designed for data with complex relationships, like social networks.

---

## Relational Databases
Relational databases store data as tables and define relationships between various entities. As a data engineer, you will primarily work with these databases.

### Key Concepts:
- **Primary Key**: A unique identifier for a row in a table. For example, in a `Users` table, `user_id` can be a primary key to ensure each user is uniquely identifiable.
- **Foreign Key**: A field in one table that establishes a link to the primary key in another table. This relationship helps maintain data integrity. For instance, an `Orders` table may use `user_id` as a foreign key to reference a `Users` table.

---

## Database Management System (DBMS)
A **Database Management System (DBMS)** is software developed to manage, organize, and manipulate databases efficiently.

---

## Database
A **Database** is an organized collection of data, designed for easy access, management, and updating. It ensures data is stored systematically for better retrieval and usage.

---

## Schema
A **Schema** is a structured definition that organizes database objects such as:
- Tables
- Views
- Indexes
- Sequences
- Data Types
- Operators
- Functions

---

## Table
A **Table** is a collection of data arranged in rows and columns. In a DBMS:
- A **Table** is referred to as a **relation**.
- A **Row** is referred to as a **tuple**.

### Tuple
A **Tuple** represents a single record in a table. For example, in a `Students` table:
| StudentID | Name     | Age |
|-----------|----------|-----|
| 1         | John Doe | 20  |

Here, `(1, John Doe, 20)` is a tuple.

---

## Additional Resources
For a detailed introduction to SQL for Data Engineering, visit the link below:
[SQL for Data Engineering](https://datawithdarshil.notion.site/SQL-for-Data-Engineering-b59d137564484daea85063adb2c2d429?pvs=4)

## Discord Community
for Discord Community Visit link below:
[Discord for Data Engineering](https://discord.gg/9DEre6Uu8c)

