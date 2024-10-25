# Import and Export Data using SQOOP

**SQOOP** is basically used to transfer data from relational databases such as MySQL, Oracle to data warehouses such as Hadoop HDFS(Hadoop File System). Thus, when data is transferred from a relational database to HDFS, we say we are **importing data**. Otherwise, when we transfer data from HDFS to relational databases, we say we are **exporting data**.

**Note:** To import or export, the order of columns in both MySQL and Hive should be the same.

**Importing data from MySQL to HDFS**

In order to store data into HDFS, we make use of Apache Hive which provides an SQL-like interface between the user and the Hadoop distributed file system (HDFS) which integrates Hadoop. We perform the following steps:

- **Step 1:** Login into MySQL

```
mysql -u root -pcloudera

```
![image](https://github.com/user-attachments/assets/969e7bd6-5683-41f9-8da4-fcc143a49eaa)

---

- **Step 2:** Create a database and table and insert data.

```
create database geeksforgeeeks;

create table geeksforgeeeks.geeksforgeeks(author_name varchar(65), total_no_of_articles int, phone_no int, address varchar(65));

insert into geeksforgeeks values(“Rohan”,10,123456789,”Lucknow”);

```

![image](https://github.com/user-attachments/assets/de2e99f1-1c8b-4e79-abc8-0281328ba130)

---

- **Step 3:** Create a database and table in the hive where data should be imported.

```
create table geeks_hive_table(name string, total_articles int, phone_no int, address string) row format delimited fields terminated by ‘,’;

```

![image](https://github.com/user-attachments/assets/696c5cc8-714f-40e2-a45b-eb40d4b61e1e)

---

- **Step 4:** Run below the import command on Hadoop.

```
sqoop import --connect \
jdbc:mysql://127.0.0.1:3306/database_name_in_mysql \
 --username root --password cloudera \
 --table table_name_in_mysql \
 --hive-import --hive-table database_name_in_hive.table_name_in_hive \
 --m 1

```

![image](https://github.com/user-attachments/assets/3de79c01-14a4-4b47-b550-c034862d47dd)

---

In the above code following things should be noted.

- **127.0.0.1** is localhost IP address.
- **3306** is the port number for MySQL.
- **m** is the number of mappers

---

- **Step 5:** Check-in hive if data is imported successfully or not.

![image](https://github.com/user-attachments/assets/0a494554-12a1-4314-ad29-7a4a29e6341f)

---

## Exporting data from HDFS to MySQL:

To export data into MySQL from HDFS, perform the following steps: 

- **Step 1:** Create a database and table in the hive.

```
create table hive_table_export(name string,company string, phone int, age int) row format delimited fields terminated by ‘,’;

```

![image](https://github.com/user-attachments/assets/62536b28-b6cb-457e-8369-0f745bed4dea)

---

- **Step 2:** Insert data into the hive table.

```
insert into hive_table_export values("Ritik","Amazon",234567891,35);

```

![image](https://github.com/user-attachments/assets/f7a3c6c9-a981-4322-9563-5cb497c19992)

---

- **Step 3:** Create a database and table in MySQL in which data should be exported.

![image](https://github.com/user-attachments/assets/ccfe0e1b-53c9-48b0-abc1-8045b158e810)

---

- **Step 4:** Run the following command on Hadoop.

```
sqoop export --connect \
jdbc:mysql://127.0.0.1:3306/database_name_in_mysql \
 --table table_name_in_mysql \
 --username root --password cloudera \
 --export-dir /user/hive/warehouse/hive_database_name.db/table_name_in_hive \
 --m 1 \
 -- driver com.mysql.jdbc.Driver
 --input-fields-terminated-by ','

```
![image](https://github.com/user-attachments/assets/a7f7a60b-967e-41d1-bb11-8d024fdc7c8d)

---

**In the above code following things should be noted.**

- **127.0.0.1** is the localhost IP address.
- **3306** is the port number for MySQL.
- In the case of exporting data, the entire path to the table should be specified
- **m** is the number of mappers

---

- **Step 5:** Check-in MySQL if data is exported successfully or not.

![image](https://github.com/user-attachments/assets/97d154d1-9b93-4500-90df-eec2698c1bfb)

