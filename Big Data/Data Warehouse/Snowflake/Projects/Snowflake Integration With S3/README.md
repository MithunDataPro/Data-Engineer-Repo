# Demo Objective

**How to integrate the Snowflake Cloud Data Warehouse with AWS Cloud S3 buckets to access the files?**

## Pre-requisites:

1. **File Formats**
2. **Understanding of Stages Concept**
3. **COPY INTO Command**
4. **AWS Account (Trial version will suffice)**


![image](https://github.com/user-attachments/assets/24f6f9a9-6717-4f5e-82df-eccc7e1b55d5)

---

# Data Flow Diagram and Requirements

## Overview

The goal is to integrate an **AWS S3 Bucket** with **Snowflake** so that data files stored in the S3 bucket can be accessed and managed within the Snowflake environment. This involves creating proper AWS policies for authentication and setting up integration on Snowflake.

---

## Data Flow Steps:

1. **External Stage Object (Snowflake)**:
   - An external stage object is created in Snowflake to define a connection to the S3 bucket.
   - This acts as the staging location where Snowflake can reference and manage the files available in the S3 bucket.

2. **Integration Using AWS IAM**:
   - Snowflake uses a Snowflake-created AWS IAM user for authentication and access to the S3 bucket.
   - Proper AWS policies are created to ensure secure access.
   - Only the required authentication permissions are granted to maintain security.

3. **AWS S3 Bucket**:
   - The S3 bucket stores the data files that need to be accessed from Snowflake.
   - The files in this bucket are referenced and processed through the external stage integration.

---

## Key Requirements:

1. **Authentication**:
   - Create and configure AWS IAM policies for secure access to the S3 bucket.
   - Ensure authentication is properly set up to allow Snowflake access to the S3 bucket.

2. **Integration**:
   - Set up an external storage object (stage) in Snowflake to define the connection to the S3 bucket.
   - Ensure the stage location points directly to the S3 bucket and its files.

3. **Data Availability**:
   - Confirm that data files from the S3 bucket are successfully read and accessible within the Snowflake environment.

---

## Summary:

The integration involves configuring AWS authentication, defining an external stage object in Snowflake, and setting up secure access to the S3 bucket. Once completed, Snowflake will have access to the files stored in the S3 bucket for processing and analysis.

![image](https://github.com/user-attachments/assets/c99730f7-688b-4363-b881-8c22898ffc40)
