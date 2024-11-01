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
[Alternatively: Manually create a file named `docker-compose.yaml` in your `airflow-docker` directory and paste the contents of the file from the Airflow documentation.](https://airflow.apache.org/docs/apache-airflow/stable/docker-compose.yaml)
