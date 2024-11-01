# To install Apache Airflow with Docker Compose on a Windows 11 system, follow these steps:

## 1. Prerequisites:
- **Windows 11** should be up to date.
- **Docker Desktop** installed on your system. Docker Desktop for Windows includes Docker Compose, which is needed for the setup.
- **WSL 2 (Windows Subsystem for Linux 2)** is enabled and installed, as Docker Desktop uses WSL 2 as its backend on Windows.

### Step-by-Step Prerequisites Installation:

#### i. Enable WSL 2
- Open PowerShell as Administrator and run:

```shell
wsl --install

```
- This installs WSL and Ubuntu as the default Linux distribution.

#### ii. Install Docker Desktop
- Download Docker Desktop for Windows from Docker’s official website.
- Run the installer and follow the instructions.
- During installation, ensure you select **“Use the WSL 2 based engine.**”

#### iii. Start Docker Desktop
- After installation, open Docker Desktop and ensure it’s running.
- Confirm Docker and Docker Compose are working by running:

```shell
docker --version
docker-compose --version

```

----

## 2. Download the Airflow Docker Compose File:

- Create a new directory for Airflow, which will house the necessary files. For example:

```shell
mkdir airflow-docker
cd airflow-docker

```
- Download the official Airflow **docker-compose.yaml** file

```shell
curl -LfO 'https://airflow.apache.org/docs/apache-airflow/2.6.3/docker-compose.yaml'

```
**Alternatively:** Manually create a file named `docker-compose.yaml` in your `airflow-docker` directory and paste the contents of the file from the [Airflow documentation].(https://airflow.apache.org/docs/apache-airflow/stable/docker-compose.yaml)

---

## 3. Set Up Airflow Environment Variables

- Airflow requires a **.env** file to define environment variables. In your airflow-docker directory, create the **.env** file with the following command:

```shell
echo -e "AIRFLOW_UID=$(id -u)\nAIRFLOW_GID=0" > .env

```
- **Note:** On Windows, **$(id -u)** may not work directly. If it doesn’t, replace **AIRFLOW_UID=$(id -u)** with **AIRFLOW_UID=50000.**

---

## 4. Initialize the Airflow Database

- Before starting Airflow for the first time, initialize the metadata database:

```shell
docker-compose up airflow-init

```
- This command prepares the database and sets up the necessary configurations for Airflow.

---

## 5. Start Airflow Services
- To start the Airflow services, run:

```shell
docker-compose up -d

```
- This starts Airflow in detached mode, meaning it runs in the background.

---

## 6. Access the Airflow Web UI
- Once the containers are up and running, access the Airflow web server at **http://localhost:8080**.
- The default username is **airflow**, and the password is also **airflow**.

---

## 7. Stopping and Restarting Airflow
- To stop all Airflow services, use:

```shell
docker-compose down

```
- To restart Airflow services, run:

```shell
docker-compose up -d

```

---

## 8. Troubleshooting Tips
- **Container Logs:** If there’s an issue, view logs with:

```shell
docker-compose logs

```

- **Re-Initialize Database:** If you encounter database issues, re-initialize it with:

```shell
docker-compose down --volumes --remove-orphans
docker-compose up airflow-init

```

---

## 9. Additional Configuration
- You can modify **docker-compose.yaml** to adjust settings like webserver ports or to add custom Airflow configuration options.
- To add plugins or custom DAGs, place them in the **dags**/ and **plugins**/ folders inside your **airflow-docker** directory.


---

With these steps, Apache Airflow should be running on Docker in your Windows 11 environment!
