# Implementing Azure Synapse Link for Cosmos DB and Querying the Replicated Data

This guide will walk you through the process of setting up Azure Synapse Link for Cosmos DB and querying the replicated data in Azure Synapse Analytics. This integration allows you to leverage the analytical capabilities of Azure Synapse for data stored in Cosmos DB.

## Prerequisites

- Azure Synapse Analytics workspace.
- Azure Cosmos DB account.

## Step 1: Set Up Azure Synapse Link for Cosmos DB

1. Open the Azure Portal and navigate to your Azure Cosmos DB account.

2. In the left-hand menu, under the "Data Explorer" section, select "Azure Synapse Link."

3. Enable Synapse Link for the specific container(s) you want to replicate data from by toggling the switch next to each container.

4. After enabling Synapse Link, click on "Synapse Studio" (Azure Synapse Analytics) from the Azure Portal to open the Synapse Studio interface.

## Step 2: Create External Tables

1. In Synapse Studio, go to the "Develop" section.

2. Click on "External tables" and then click on the "+ New" button to create a new external table.

3. Choose the data source type as "Cosmos DB" and provide the necessary connection information for your Cosmos DB account, including the Cosmos DB account name, database name, and container name.

4. Specify the table name, schema, and column mapping. Ensure that the schema matches the structure of your Cosmos DB container.

5. Click "Create" to create the external table.

## Step 3: Query Replicated Data

1. In Synapse Studio, go to the "Develop" section.

2. Click on "SQL scripts" and create a new SQL script to query the replicated data.

3. Write your SQL query to retrieve and analyze the data from the external table you created in the previous step. For example:

   ```sql
   SELECT * FROM your_external_table;
