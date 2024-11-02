# Apache Airflow: A Detailed Explanation
**Apache Airflow** is an open-source workflow management platform that allows you to programmatically **author**, **schedule**, and **monitor workflows**. It is highly scalable and extensible, making it a good choice for automating complex data pipelines.

![image](https://github.com/user-attachments/assets/ad18c13c-53c4-4be8-9bee-3a264e69cb48)

---
## Airflow Architecture
**Airflow is a distributed system that consists of the following components:**

- **Webserver:** The webserver provides a user interface for managing Airflow workflows.
- **Scheduler:** The scheduler is responsible for scheduling and running Airflow tasks.
- **Worker:** The worker nodes execute Airflow tasks.
- **Executor:** The executor is responsible for running tasks on worker nodes.
- **Metadata database:** The metadata database stores information about Airflow workflows, tasks, and other entities.

![image](https://github.com/user-attachments/assets/410b4d79-ddce-4b5b-af87-c3f904de0d05)

---

## Airflow Workflow Definition
Airflow workflows are defined in Python code. Airflow provides a number of operators that can be used to perform common tasks, such as extracting data from databases, running machine learning models, and sending email notifications.

Here is a simple Airflow workflow that extracts data from a database and loads it into a data warehouse:

```
from airflow import DAG
from airflow.operators.python_operator import PythonOperator

dag = DAG('extract_load_data', start_date='2023-11-03')

def extract_data():
    # Extract data from the database
    pass

def load_data():
    # Load data into the data warehouse
    pass

extract_data_task = PythonOperator(
    task_id='extract_data',
    python_callable=extract_data,
    dag=dag,
)

load_data_task = PythonOperator(
    task_id='load_data',
    python_callable=load_data,
    dag=dag,
)

extract_data_task >> load_data_task

```

---

## Key Concepts

### 1. Directed Acyclic Graph (DAG)
A DAG in Airflow represents the structure of a workflow. It is a collection of tasks that run with a specific order and dependency, designed to avoid cycles (hence, "acyclic"). Each DAG is defined in Python code and can be scheduled to run at intervals.

- **Example**: ETL processes, data warehousing tasks, machine learning pipelines.

### 2. Tasks
Each node in a DAG is a task, which is an individual unit of work. Tasks represent actions like data extraction, processing, or loading.

There are various types of tasks:
- **Operators**: Predefined tasks (e.g., PythonOperator for running Python code, BashOperator for bash commands).
- **Sensors**: Tasks that wait for a particular condition to be met (e.g., FileSensor waits for a file to be available).
- **Task Instances**: Represent a single run of a task in a DAG at a specific time.

### 3. Operators
Operators define the nature of each task. Some commonly used operators include:
- **PythonOperator**: Executes Python functions.
- **BashOperator**: Runs bash commands.
- **MySqlOperator, PostgresOperator**: Executes SQL queries.
- **BranchPythonOperator**: Determines branching paths in the DAG based on certain conditions.

### 4. Scheduler
The Scheduler is the core component of Airflow responsible for managing the timing of DAG executions. It monitors the DAGs and triggers tasks when their dependencies are met, based on the DAG's schedule interval.

- **Execution Date**: The date the DAG is scheduled to run, often a fixed interval in the past.
- **Start Date** and **End Date**: Define the time boundaries within which a DAG can run.

### 5. Executor
Executors define how and where tasks are executed. Airflow supports several types of executors:
- **SequentialExecutor**: Executes tasks one at a time; suitable for testing.
- **LocalExecutor**: Executes multiple tasks in parallel using the local system.
- **CeleryExecutor**: Distributes tasks across multiple worker nodes; suitable for scaling.
- **KubernetesExecutor**: Schedules tasks as Kubernetes pods.

---

## Key Components

1. **Web Server**: Provides a web-based UI to monitor and manage DAGs, view task logs, and interact with running workflows.
2. **Scheduler**: Orchestrates the execution of tasks based on DAG dependencies and scheduling.
3. **Metadata Database**: Stores information about DAGs, task states, and execution history.
4. **Worker(s)**: Run tasks. The number and type of workers depend on the executor used.

---

## DAG Structure Example

```python
from airflow import DAG
from airflow.operators.python_operator import PythonOperator
from datetime import datetime, timedelta

# Default arguments for the DAG
default_args = {
    'owner': 'airflow',
    'depends_on_past': False,
    'email_on_failure': False,
    'email_on_retry': False,
    'retries': 1,
    'retry_delay': timedelta(minutes=5),
}

# Define the DAG
dag = DAG(
    'example_dag',
    default_args=default_args,
    description='An example DAG',
    schedule_interval=timedelta(days=1),
    start_date=datetime(2023, 1, 1),
    catchup=False,
)

# Define task
def hello_world():
    print("Hello, world!")

# Task using PythonOperator
hello_task = PythonOperator(
    task_id='hello_task',
    python_callable=hello_world,
    dag=dag,
)

# Task dependency
hello_task

