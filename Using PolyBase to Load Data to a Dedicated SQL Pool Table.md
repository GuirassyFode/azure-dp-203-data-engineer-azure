# Using PolyBase to Load Data to a Dedicated SQL Pool Table

## Introduction

PolyBase allows you to read/write data in external storage using T-SQL. This lab demonstrates how to load data into a dedicated SQL pool table in parallel from a data lake file.

## Solution

### Set Up the Environment

1. Log in to the Azure portal using the provided lab credentials in an incognito or private browser window.

2. Navigate to Azure Synapse Analytics.

3. In the upper left corner, click "Create."
   
4. Configure the workspace:
   - Resource group: Select the existing resource group.
   - Workspace name, for mine : Enter "fodessynapse."
   - Region: Ensure "East US 2" is selected.

5. Configure Data Lake Storage Gen2:
   - Account name: Enter "fodestorage."
   - File system name: Enter "fodefsn."

6. Complete the setup and wait for deployment to finish.
   ![image](https://github.com/GuirassyFode/azure-dp-203-data-engineer-azure/assets/25976326/da9508f1-d61c-4d98-b87d-04b09d825cbb)

   
   ![image](https://github.com/GuirassyFode/azure-dp-203-data-engineer-azure/assets/25976326/07b2bae2-40bb-42bd-9893-2edc84c2c63c)


### Create a Container `taxidata` in the Data Lake Account

1. Click on "acgmsstorage."

2. In the left navigation menu, under Data storage, click "Containers."

3. Click "+ Container."

4. Enter "taxidata" for Name and click "Create."

### Set Up Dedicated SQL Pool Instance

1. Navigate back to the Resource group page and click on "acgmssynapse."

2. Under "Open Synapse Studio," click "Open."

3. In Synapse workspace, click on the "Manage" icon in the left navigation menu.

4. Select "SQL pools" under the expanded Manage menu.

5. Click "+New" to create a new SQL pool.
   
6. Configure the SQL pool:
   - Dedicated SQL pool name: Enter "TaxiRidesWarehouse."
   - Performance level: Adjust to "DW100c."

7. Complete the setup and wait for deployment to finish.

### Define PolyBase Components to Read Data Lake File

1. In the Synapse workspace, click on the "Data" icon in the left navigation menu.

2. Under Data, click on the "Linked" tab.

3. Expand Azure Data Lake Storage Gen2 > acgmssynapse > taxidata container.

4. Upload the "TaxiRides.parquet" file.

5. Right-click on "TaxiRides.parquet" file, hover over "New SQL script," and select "Create external table."

   ![image](https://github.com/GuirassyFode/azure-dp-203-data-engineer-azure/assets/25976326/15954b0b-11c0-4ce4-8c00-636b6f0fa532)


7. Select the target database:
   - Select SQL pool: Choose "TaxiRidesWarehouse."
   - External table name: Enter "ExternalTaxiRides."

8. Leave other settings at default and click "Open script."

9. Review the script and execute it.

### Create Table in Dedicated SQL Pool Using CTAS

Use the CTAS (CREATE TABLE AS SELECT) command to create a new table named TaxiRides. Replace `<External Table Name>` with the name of the external table you created in the previous objective:

![image](https://github.com/GuirassyFode/azure-dp-203-data-engineer-azure/assets/25976326/ba28902a-db32-4e3d-b572-08ff50bb2629)

```sql
-- Create table TaxiRides, using CTAS (Polybase)

-- Create table TaxiRides, using CTAS (Polybase)


CREATE TABLE TaxiRides
WITH 
(
	DISTRIBUTION = ROUND_ROBIN,
	CLUSTERED COLUMNSTORE INDEX
) 
AS 
SELECT * 
FROM dbo.FodeExternalTaxiRides		-- Replace name of external table

SELECT * FROM TaxiRides











