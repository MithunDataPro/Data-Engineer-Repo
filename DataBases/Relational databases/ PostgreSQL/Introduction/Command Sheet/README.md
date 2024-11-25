# PostgreSQL Command Cheat Sheet

Here is a comprehensive list of PostgreSQL commands categorized by functionality:

---

## **General Commands**
| Command                | Description                                      |
|------------------------|--------------------------------------------------|
| `\q`                  | Exit `psql`.                                     |
| `\l` or `\list`        | List all databases.                              |
| `\c <database_name>`   | Connect to a database.                           |
| `\conninfo`            | Display connection info.                         |
| `\g`                  | Execute the last SQL command.                    |
| `\timing`              | Toggle query execution time display.             |
| `\password`            | Change the password for the current user.        |

---

## **Database Management**
| Command                                | Description                                      |
|---------------------------------------|--------------------------------------------------|
| `CREATE DATABASE <db_name>;`          | Create a new database.                          |
| `DROP DATABASE <db_name>;`            | Delete a database.                              |
| `ALTER DATABASE <db_name> ...;`       | Modify a database (e.g., rename, change owner). |
| `\l+`                                 | List all databases with extended details.       |

---

## **User/Role Management**
| Command                                 | Description                                      |
|----------------------------------------|--------------------------------------------------|
| `CREATE USER <username> WITH PASSWORD '<password>';` | Create a new user.                             |
| `DROP USER <username>;`                | Delete a user.                                  |
| `ALTER USER <username> WITH PASSWORD '<password>';` | Change a user's password.                     |
| `GRANT ALL PRIVILEGES ON DATABASE <db_name> TO <username>;` | Grant database permissions to a user.         |
| `REVOKE ALL PRIVILEGES ON DATABASE <db_name> FROM <username>;` | Revoke permissions from a user.              |

---

## **Table Management**
| Command                                | Description                                      |
|---------------------------------------|--------------------------------------------------|
| `CREATE TABLE <table_name> (...);`    | Create a new table.                             |
| `DROP TABLE <table_name>;`            | Delete a table.                                 |
| `ALTER TABLE <table_name> ...;`       | Modify a table (e.g., rename, add/drop column). |
| `\dt`                                 | List all tables in the current database.        |
| `\d <table_name>`                     | Describe a table's structure.                   |
| `\d+ <table_name>`                    | Describe a table with detailed information.     |

---

## **Data Manipulation (DML)**
| Command                                | Description                                      |
|---------------------------------------|--------------------------------------------------|
| `INSERT INTO <table_name> VALUES (...);` | Insert a new row into a table.                 |
| `UPDATE <table_name> SET <column> = <value> WHERE <condition>;` | Update rows in a table.                     |
| `DELETE FROM <table_name> WHERE <condition>;` | Delete rows from a table.                     |
| `SELECT * FROM <table_name>;`         | Retrieve all rows from a table.                 |
| `SELECT <columns> FROM <table_name> WHERE <condition>;` | Retrieve specific rows/columns.             |

---

## **Indexes**
| Command                                | Description                                      |
|---------------------------------------|--------------------------------------------------|
| `CREATE INDEX <index_name> ON <table_name> (<column>);` | Create an index on a column.                 |
| `DROP INDEX <index_name>;`            | Delete an index.                                |

---

## **Constraints**
| Command                                | Description                                      |
|---------------------------------------|--------------------------------------------------|
| `ALTER TABLE <table_name> ADD CONSTRAINT <constraint_name> UNIQUE (<column>);` | Add a unique constraint.                |
| `ALTER TABLE <table_name> DROP CONSTRAINT <constraint_name>;` | Remove a constraint.                     |

---

## **Views**
| Command                                | Description                                      |
|---------------------------------------|--------------------------------------------------|
| `CREATE VIEW <view_name> AS SELECT ...;` | Create a new view.                             |
| `DROP VIEW <view_name>;`              | Delete a view.                                  |
| `\dv`                                 | List all views in the current database.         |

---

## **Sequences**
| Command                                | Description                                      |
|---------------------------------------|--------------------------------------------------|
| `CREATE SEQUENCE <seq_name>;`         | Create a new sequence.                          |
| `DROP SEQUENCE <seq_name>;`           | Delete a sequence.                              |
| `SELECT nextval('<seq_name>');`       | Get the next value from a sequence.             |
| `SELECT currval('<seq_name>');`       | Get the current value of a sequence.            |
| `ALTER SEQUENCE <seq_name> RESTART WITH <value>;` | Reset a sequence to a specific value.        |

---

## **Foreign Keys**
| Command                                | Description                                      |
|---------------------------------------|--------------------------------------------------|
| `ALTER TABLE <table_name> ADD FOREIGN KEY (<column>) REFERENCES <ref_table>(<ref_column>);` | Add a foreign key.              |
| `ALTER TABLE <table_name> DROP CONSTRAINT <constraint_name>;` | Remove a foreign key.                      |

---

## **Transactions**
| Command                                | Description                                      |
|---------------------------------------|--------------------------------------------------|
| `BEGIN;`                              | Start a transaction.                            |
| `COMMIT;`                             | Commit the transaction.                         |
| `ROLLBACK;`                           | Rollback the transaction.                       |

---

## **Export/Import**
| Command                                | Description                                      |
|---------------------------------------|--------------------------------------------------|
| `\copy <table_name> TO '<file_path>' CSV HEADER;` | Export a table to a CSV file.                |
| `\copy <table_name> FROM '<file_path>' CSV HEADER;` | Import a CSV file into a table.             |

---

## **Admin Commands**
| Command                                | Description                                      |
|---------------------------------------|--------------------------------------------------|
| `SHOW <parameter>;`                   | Display the value of a configuration parameter. |
| `SET <parameter> = <value>;`          | Set a configuration parameter.                  |
| `\! <shell_command>`                  | Execute a shell command from `psql`.            |
| `VACUUM;`                             | Clean up and optimize the database.             |
| `ANALYZE;`                            | Collect statistics for the query planner.       |
| `REINDEX;`                            | Rebuild indexes for performance improvement.    |

---

## **Miscellaneous**
| Command                                | Description                                      |
|---------------------------------------|--------------------------------------------------|
| `\timing`                             | Toggle query execution time display.            |
| `\x`                                  | Toggle extended display mode for query results. |
| `\watch <seconds>`                    | Repeat a query every `<seconds>` seconds.       |

---

This cheat sheet covers the most commonly used PostgreSQL commands for daily operations, development, and administration. Let me know if you'd like detailed explanations or examples for specific commands!

