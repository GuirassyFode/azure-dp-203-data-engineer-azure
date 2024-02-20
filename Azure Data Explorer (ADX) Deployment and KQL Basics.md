# Azure Data Explorer (ADX) Deployment and KQL Basics

This project guides you through the deployment of an Azure Data Explorer (ADX) cluster, Microsoft's powerful big data analytics platform. You'll learn how to create a table, ingest data into it, and execute basic Kusto Query Language (KQL) queries. KQL powers the analytics capabilities in ADX, offering a rich language designed for real-time, large-scale data analytics.

## Introduction

Azure Data Explorer is a fast, fully managed data analytics service for real-time analysis on large volumes of data streaming from applications, websites, IoT devices, and more. This project covers the fundamentals of setting up ADX, ingesting data, and querying that data with KQL.

## Prerequisites

Before starting, ensure you have the following:

- An Azure account with an active subscription. [Create one for free](https://azure.microsoft.com/free/).
- Azure CLI or PowerShell installed and configured. [Learn more](https://docs.microsoft.com/en-us/cli/azure/).
- Basic understanding of SQL or database concepts.

## Setup Instructions

### Deploying ADX Cluster

1. **Create a Resource Group (if necessary):**
   ```bash
   az group create --name MyResourceGroup --location eastus




2. Create an ADX Cluster:
   az kusto cluster create --name MyCluster --resource-group MyResourceGroup --location eastus --sku D13_v2 --capacity 2
   
![image](https://github.com/GuirassyFode/azure-dp-203-data-engineer-azure/assets/25976326/b55f5d54-410b-46c4-b877-1990f1c40b97)

   
4. Creating a Database
Use the Azure portal or Azure CLI to create a database in your ADX cluster:

az kusto database create --cluster-name MyCluster --database-name MyDatabase --resource-group MyResourceGroup --soft-delete-period P365D --hot-cache-period P31D

![image](https://github.com/GuirassyFode/azure-dp-203-data-engineer-azure/assets/25976326/96fe8a8f-5b85-40d0-b450-780911a598c2)

4. Ingesting Data
This project includes sample data and scripts to ingest data into your ADX table. See the data_ingestion/ directory for details.

![image](https://github.com/GuirassyFode/azure-dp-203-data-engineer-azure/assets/25976326/82e519dd-658b-44b1-af5c-bcf74c9a3462)


5. Querying with KQL
KQL is a rich language designed to query large datasets quickly. Here are a few basic queries to get you started:

   List all tables:
   .show tables
![image](https://github.com/GuirassyFode/azure-dp-203-data-engineer-azure/assets/25976326/27b7e3a1-567e-4e12-bf9f-88e120c94926)

   
6. Upload a file into ADX
   ![image](https://github.com/GuirassyFode/azure-dp-203-data-engineer-azure/assets/25976326/daa40573-6985-4cce-949b-e35c99b42f50)

7. View uploaded file
   
![image](https://github.com/GuirassyFode/azure-dp-203-data-engineer-azure/assets/25976326/25ef04e4-44c9-42ee-960d-0cad86b5538f)

![image](https://github.com/GuirassyFode/azure-dp-203-data-engineer-azure/assets/25976326/9fe59f3d-70f5-4663-a750-1eebb88da9ea)


Contact
Fode Guirassy - @https://www.linkedin.com/in/fode-guirassy-83b089229/

Project Link: https://github.com/GuirassyFode/azure-dp-203-data-engineer-azure.git



Save this text in a file with the `.md` extension to use it as a Markdown document.

