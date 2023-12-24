# Creating an Azure Synapse SQL Dedicated Pool

In this guide, we'll walk you through the steps to create an Azure Synapse SQL Dedicated Pool (formerly known as SQL Data Warehouse) in Azure Synapse Analytics.

## Prerequisites

- An Azure account. If you don't have one, you can [create a free account](https://azure.com/free).

## Step-by-Step Instructions

1. **Sign in to Azure Portal**:
   - Open your web browser and navigate to the [Azure Portal](https://portal.azure.com/).
   - Sign in with your Azure account credentials.

2. **Create a New Azure Synapse Workspace**:
   - In the Azure Portal, click on "Create a resource" or use the search bar to find "Azure Synapse Analytics."
   - Click on "Create" to start the creation process.

3. **Configure Basic Settings**:
   - Provide a unique name for your Synapse workspace.
   - Choose your subscription, resource group, and region.
   - Select "On-demand" for the pricing tier if you want to pay for resources as you use them. Select "Provisioned" if you want to preallocate resources.

4. **Additional Settings**:
   - Configure optional settings such as virtual network, firewall, and Advanced Data Security settings based on your requirements.

5. **Review + Create**:
   - Review your configuration settings to ensure they are correct.
   - Click "Create" to start the deployment process. This might take a few minutes to complete.

6. **Access Synapse Workspace**:
   - Once the deployment is successful, go to your Synapse workspace in the Azure Portal.

7. **Create a Dedicated SQL Pool (formerly Data Warehouse)**:
   - Inside your Synapse workspace, navigate to "SQL pools" in the left-hand menu.
   - Click on "New" to create a new dedicated SQL pool.
   - Provide a name, performance level (DWU or Data Warehousing Units), and other configuration details.
   - Click "Create" to provision the dedicated SQL pool.

8. **Connect and Use**:
   - After provisioning, you can connect to your dedicated SQL pool using various tools like SQL Server Management Studio (SSMS) or Azure Data Studio.
   - Load data into it, create tables, and run analytical queries to analyze your data.

## Next Steps

You've successfully created an Azure Synapse SQL Dedicated Pool. Now, explore and utilize it for your data warehousing and analytics needs. Check out the official [Azure Synapse documentation](https://docs.microsoft.com/en-us/azure/synapse-analytics/) for more in-depth information.

Good luck with your data projects!
