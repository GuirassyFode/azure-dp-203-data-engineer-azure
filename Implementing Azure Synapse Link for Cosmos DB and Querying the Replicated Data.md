# Implementing Azure Synapse Link for Cosmos DB and Querying the Replicated Data

This guide will walk you through the process of setting up Azure Synapse Link for Cosmos DB and querying the replicated data in Azure Synapse Analytics. This integration allows you to leverage the analytical capabilities of Azure Synapse for data stored in Cosmos DB.

## Prerequisites

- Azure Synapse Analytics workspace.
- Azure Cosmos DB account.
  ![image](https://github.com/GuirassyFode/azure-dp-203-data-engineer-azure/assets/25976326/6f3cd171-8b29-4c50-ad4a-b5645866b6d0)

  ![image](https://github.com/GuirassyFode/azure-dp-203-data-engineer-azure/assets/25976326/33f65ba6-2082-4e17-8cd6-33835c982729)



## Step 1: Set Up Azure Synapse Link for Cosmos DB

1. Open the Azure Portal and navigate to your Azure Cosmos DB account.

2. In the left-hand menu, under the "Data Explorer" section, select "Azure Synapse Link."

![image](https://github.com/GuirassyFode/azure-dp-203-data-engineer-azure/assets/25976326/e6fe34de-9f43-47c5-b8be-52564cc42d7b)


4. Enable Synapse Link for the specific container(s) you want to replicate data from by toggling the switch next to each container.

5. After enabling Synapse Link, click on "Synapse Studio" (Azure Synapse Analytics) from the Azure Portal to open the Synapse Studio interface.
   
![image](https://github.com/GuirassyFode/azure-dp-203-data-engineer-azure/assets/25976326/ff7e3f47-2c5a-492b-8c4b-b0f823c0d07a)

## Step 2: Create External Tables

1. In Synapse Studio, go to the "Develop" section.

2. Click on "External tables" and then click on the "+ New" button to create a new external table.

3. Choose the data source type as "Cosmos DB" and provide the necessary connection information for your Cosmos DB account, including the Cosmos DB account name, database name, and container name.

4. Specify the table name, schema, and column mapping. Ensure that the schema matches the structure of your Cosmos DB container.

5. Click "Create" to create the external table.
   
   ![image](https://github.com/GuirassyFode/azure-dp-203-data-engineer-azure/assets/25976326/56404fdb-b4a8-4047-973d-559fb8307613)
6. Load the data
  ![image](https://github.com/GuirassyFode/azure-dp-203-data-engineer-azure/assets/25976326/1fbaf349-0c0c-4698-9e98-a8b97199cd49)


## Step 3: Query Replicated Data

1. In Synapse Studio, go to the "Develop" section.

2. Click on "SQL scripts" and create a new SQL script to query the replicated data.

3. Write your SQL query to retrieve and analyze the data from the external table you created in the previous step. For example:

   ```sql
   SELECT * FROM your_external_table;
