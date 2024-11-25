# PostgreSQL Installation Guide (Windows)

Follow these detailed steps to install PostgreSQL on a Windows system from scratch:

---

## Step 1: Download PostgreSQL Installer
1. Visit the [PostgreSQL official website](https://www.postgresql.org/download/).
2. Click on **Windows** to navigate to the download page.
3. Choose the latest version of PostgreSQL and download the installer.
   - Example: PostgreSQL 17.2

---

## Step 2: Run the Installer
1. Locate the downloaded installer file (e.g., `postgresql-17.2-1-windows-x64.exe`) and double-click it to start the installation process.
2. Click **Next** on the welcome screen.

---

## Step 3: Select Installation Directory
1. Choose the directory where you want PostgreSQL to be installed.
   - Default: `C:\Program Files\PostgreSQL\<version>`
   - Example: `C:\Program Files\PostgreSQL\17`
2. Click **Next**.

---

## Step 4: Select Components
1. Choose the components to install:
   - **PostgreSQL Server** (Required)
   - **pgAdmin 4** (Recommended)
   - **Command Line Tools** (Optional but useful for scripting)
   - **Stack Builder** (Optional for additional tools and extensions)
2. Click **Next**.

---

## Step 5: Set Data Directory
1. Specify the directory where PostgreSQL will store its data files.
   - Default: `C:\Program Files\PostgreSQL\<version>\data`
   - Example: `C:\Program Files\PostgreSQL\17\data`
2. Click **Next**.

---

## Step 6: Set Password for PostgreSQL Superuser (`postgres`)
1. Enter a password for the default superuser account (`postgres`).
   - Make sure to remember this password; it will be required to access the database.
2. Click **Next**.

---

## Step 7: Select Port Number
1. Specify the port number PostgreSQL should use to listen for connections.
   - Default: **5432**
   - You can change this if needed (e.g., **1997**).
2. Click **Next**.

---

## Step 8: Choose Locale
1. Select the default locale for the database cluster.
   - Default: The installer automatically selects the appropriate locale for your system.
2. Click **Next**.

---

## Step 9: Install PostgreSQL
1. Review your settings and click **Next** to begin the installation.
2. The installer will copy files and configure PostgreSQL. Wait for the process to complete.

---

## Step 10: Install Stack Builder (Optional)
1. After the installation completes, you will be prompted to launch **Stack Builder**.
   - Stack Builder allows you to install additional tools, drivers, and extensions.
2. If needed, select the PostgreSQL instance and install tools like:
   - **pgAdmin**
   - **PostGIS** (for geospatial data)
   - **ODBC/JDBC drivers**

---

# Verifying PostgreSQL Installation

### **Step 1: Add PostgreSQL to the PATH (Optional)**
1. Locate the `bin` directory of your PostgreSQL installation:
   - Example: `C:\Program Files\PostgreSQL\17\bin`
2. Add this directory to your PATH environment variable:
   - **Open Environment Variables**:
     - Press `Win + R`, type `sysdm.cpl`, and press Enter.
     - Go to the **Advanced** tab and click **Environment Variables**.
   - **Edit the PATH Variable**:
     - Under **System Variables**, find and select `Path`.
     - Click **Edit** and add the PostgreSQL `bin` directory.

---

### **Step 2: Start PostgreSQL Service**
1. Press `Win + R`, type `services.msc`, and press Enter.
2. Locate the service named **PostgreSQL (version)** (e.g., `PostgreSQL 17`).
3. Ensure the service status is **Running**. If not, right-click and select **Start**.

---

### **Step 3: Verify Installation via Command Line**
1. Open **Command Prompt**.
2. Check the PostgreSQL version:
   ```bash
   psql --version

``
- Expected output: **psql (PostgreSQL) <version>**

3. Connect to PostgreSQL:
   ```bash
   psql -U postgres -p <port>

``

- Replace **<port>** with the port you configured (e.g., **5432** or **1997**).
- Enter the password for the **postgres** user when prompted.
- If successful, you will see the PostgreSQL prompt:
  ```makefile
  postgres=#

``

---

# First Steps After Installation

### 1. List all Databases:
```sql
\l

```

### 2. Create New Databases:
```sql
CREATE DATABASE mydb;

```

### 3. Connect to a Database
```sql
\c mydb

```

### 4.  Exit **psql**
```sql
\q

```

---


