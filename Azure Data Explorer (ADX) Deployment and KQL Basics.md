
Sure, here is the text converted to Markdown format:

markdown
Copy code
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
Create an ADX Cluster:
bash
Copy code
az kusto cluster create --name MyCluster --resource-group MyResourceGroup --location eastus --sku D13_v2 --capacity 2
Creating a Database
Use the Azure portal or Azure CLI to create a database in your ADX cluster:

bash
Copy code
az kusto database create --cluster-name MyCluster --database-name MyDatabase --resource-group MyResourceGroup --soft-delete-period P365D --hot-cache-period P31D
Ingesting Data
This project includes sample data and scripts to ingest data into your ADX table. See the data_ingestion/ directory for details.

Querying with KQL
KQL is a rich language designed to query large datasets quickly. Here are a few basic queries to get you started:

List all tables:

kql
Copy code
.show tables
Query data from a table:

kql
Copy code
MyTable
| where Timestamp > ago(30d)
| summarize count() by bin(Timestamp, 1d), Category
| render timechart
Contributing
Contributions are what make the open-source community such an amazing place to learn, inspire, and create. Any contributions you make are greatly appreciated.

License
Distributed under the MIT License. See LICENSE for more information.

Contact
Fode Guirassy - @https://www.linkedin.com/in/fode-guirassy-83b089229/

Project Link: https://github.com/GuirassyFode/azure-dp-203-data-engineer-azure.git

javascript
Copy code

Save this text in a file with the `.md` extension to use it as a Markdown document.