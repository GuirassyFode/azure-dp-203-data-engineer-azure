# Implementing Azure Synapse Link for Cosmos DB and Querying the Replicated Data

This guide will walk you through the process of setting up Azure Synapse Link for Cosmos DB and querying the replicated data in Azure Synapse Analytics. This integration allows you to leverage the analytical capabilities of Azure Synapse for data stored in Cosmos DB.

![image](https://github.com/GuirassyFode/azure-dp-203-data-engineer-azure/assets/25976326/12e88e0a-9278-468e-8edf-0313c2b0f6f9)



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

7. Data Loaded
   ![image](https://github.com/GuirassyFode/azure-dp-203-data-engineer-azure/assets/25976326/c3bcb81a-05fb-4b1a-b2d6-a5e987d25b81)


## Step 3: Query Replicated Data

1. In Synapse Studio, go to the "Develop" section.
   1.1 Deploy Sysnapse account
  ![image](https://github.com/GuirassyFode/azure-dp-203-data-engineer-azure/assets/25976326/2a117822-f334-4ce8-a29e-8a425dcc1f31)
   1.2 Create Cosmos DB Nosql external table link
   ![image](https://github.com/GuirassyFode/azure-dp-203-data-engineer-azure/assets/25976326/27221a17-f411-4dd7-87a1-ff73ae0ab5ef)




3. Click on "SQL scripts" and create a new SQL script to query the replicated data.
   ![image](https://github.com/GuirassyFode/azure-dp-203-data-engineer-azure/assets/25976326/ee6c9e36-e7ab-460c-b18b-dab6270e8351)


5. Write your SQL query to retrieve and analyze the data from the external table you created in the previous step. For example:
   ![image](https://github.com/GuirassyFode/azure-dp-203-data-engineer-azure/assets/25976326/917d852a-a7e0-4176-8cbe-7a0468d784c1)


   ```sql

   -- Check if the 'cosmosdb' credential exists
IF NOT EXISTS (SELECT * FROM sys.credentials WHERE name = 'cosmosdb')
BEGIN
    -- If it doesn't exist, create the credential with the Azure Cosmos DB key
    CREATE CREDENTIAL [cosmosdb]
    WITH IDENTITY = 'SHARED ACCESS SIGNATURE',
    SECRET = 'Key'; -- Replace with your actual Cosmos DB key

    PRINT 'The credential for Azure Cosmos DB has been created.';
END
ELSE
BEGIN
    PRINT 'The credential for Azure Cosmos DB already exists.';
END

SELECT TOP 100 *
FROM OPENROWSET(
    PROVIDER = 'CosmosDB',
    CONNECTION = 'Account=fodecosmosdb;Database=RidesDB',
    OBJECT = 'RidesFeedback',
    SERVER_CREDENTIAL = 'cosmosdb' -- Use the 'cosmosdb' credential
) AS [RidesFeedback];

   SELECT * FROM your_external_table;

![image](https://github.com/GuirassyFode/azure-dp-203-data-engineer-azure/assets/25976326/9c13f647-fc0e-49d5-9145-f2ec6a18ca19)
