# Multi-Cloud File Processing System  
AWS (S3 → Lambda → DynamoDB → CloudWatch)  
Azure (Blob → Function → Cosmos DB)

---

## Overview

This project demonstrates a multi-cloud serverless architecture where:

- Uploading a file to **Amazon S3** triggers an **AWS Lambda** function.
- The Lambda function stores file metadata in **DynamoDB**.
- Logs are monitored using **CloudWatch**.
- Uploading a file to **Azure Blob Storage** triggers an **Azure Function**.
- The Azure Function stores file metadata in **Cosmos DB**.

---

# AWS Implementation

## Step 1: Create S3 Bucket

- Service: Amazon S3  
- Bucket Name: `lambda-bucket-07-02-2026`  
- Region: `us-east-1 (N. Virginia)`  

---

## Step 2: Create Lambda Function

- Function Name: `fileupload`  
- Runtime: Python 3.x  
- Execution Role:
  - Basic Lambda permissions
  - AmazonDynamoDBFullAccess
  - AmazonS3ReadOnlyAccess

---

## Step 3: Configure S3 Trigger

- Trigger Type: S3  
- Bucket: `lambda-bucket-07-02-2026`  
- Event Type: All object create events  

---

## Step 4: Create DynamoDB Table

- Table Name: `FileMetadata`  
- Partition Key: `fileName` (String)  

---

## Lambda Code (AWS)


# Azure Blob → Function → Cosmos DB

## Overview
This project implements a serverless workflow in Azure where a file uploaded to Blob Storage triggers an Azure Function, which stores file metadata in Cosmos DB.

---

## Architecture
Blob Storage (Container: uploads)  
→ Azure Function (Blob Trigger)  
→ Cosmos DB (Database: FileDB, Container: FileMetadata)

---

## Implementation Steps

### 1. Create Storage Account
- Create Azure Storage Account.
- Create Blob container:
  uploads

### 2. Create Function App
- Runtime: Python
- Create new function using **Blob Trigger**
- Trigger path:
  uploads/{name}

### 3. Create Cosmos DB
- API: Core (SQL)
- Database name: FileDB
- Container name: FileMetadata
- Partition key: /fileName

### 4. Configure Application Settings
In Function App → Configuration → Application Settings, add:
- COSMOS_DB_URI
- COSMOS_DB_KEY

---

## Azure Function Code (Python)
