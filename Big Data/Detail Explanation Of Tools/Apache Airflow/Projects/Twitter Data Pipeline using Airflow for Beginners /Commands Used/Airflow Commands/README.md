# Apache Airflow Standalone Commands

## 1. Initialize the Airflow Database
Before you can run Airflow, you need to initialize the database.

```bash
airflow db init

```
---

## 2. Start the Airflow Web Server

To start the Airflow web server (usually accessible at **http://localhost:8080**):
```bash
airflow webserver --port 8080

```

- **Note:** You can change the port by specifying a different port number.

---

## 3. Start the Airflow Scheduler

The scheduler is responsible for executing the **DAGs (Directed Acyclic Graphs)** in Airflow.
```bash
airflow scheduler

```
---

## 4. Start a Standalone Airflow Environment
Airflow provides a quick way to start a standalone instance, which initializes the database, web server, and scheduler in one command. This is ideal for local testing.

```bash
airflow standalone

```

---

## 5. Create an Airflow User
To create an admin user for accessing the Airflow web UI:

```bash
airflow users create \
    --username admin \
    --firstname FIRST_NAME \
    --lastname LAST_NAME \
    --role Admin \
    --email admin@example.com

```

---

## 6. List Existing Airflow Users
To list all users in Airflow:

```bash
airflow users list

```

---

## 7. Trigger a DAG Run Manually
To manually trigger a DAG (useful for testing or running ad-hoc tasks):
```bash
airflow dags trigger <dag_id>

```

Replace **<dag_id>** with the ID of the DAG you want to trigger.

---

## 8. List All DAGs
To view all the DAGs available in your Airflow instance:

```bash
airflow dags list

```
---

## 9. Pause a DAG
To pause a DAG (useful if you don’t want it to run on schedule):
```bash
airflow dags pause <dag_id>

```
Replace **<dag_id>** with the ID of the DAG you want to pause.

---

## 10. Unpause a DAG
To unpause a paused DAG:
```bash
airflow dags unpause <dag_id>

```
Replace **<dag_id>** with the ID of the DAG you want to unpause.

---
## 11. List DAG Runs
To list all runs of a specific DAG:
```bash
airflow dags list-runs -d <dag_id>

```

Replace **<dag_id>** with the ID of the DAG.

---

## 12. Show Task Instances for a DAG
To view the task instances for a specific DAG:
```bash
airflow tasks list <dag_id>

```

Replace **<dag_id>** with the ID of the DAG.

---

## 13. Test a Specific Task
To test a specific task in a DAG without affecting the DAG’s actual schedule:
```bash
airflow tasks test <dag_id> <task_id> <execution_date>

```

Replace **<dag_id>**, **<task_id>**, and **<execution_date>** accordingly.

---

## 14. Clear Task Instances
To clear task instances for a specific DAG (useful for re-running tasks):
```bash
airflow tasks clear <dag_id>

```
This command has additional options to target specific dates or tasks within a DAG.

---

## 15. Access the Airflow CLI Help
To view help for Airflow CLI commands:
```bash
airflow --help

```
These commands should help you manage and operate an Airflow standalone environment. Make sure to replace placeholders with actual IDs where needed.

