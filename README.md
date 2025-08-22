# Azure Resource Setup & Role Assignments – User Guide  

This guide provides step-by-step instructions for provisioning key Azure resources and assigning appropriate IAM roles.  

---

## 1. Azure SQL Database  
**Goal:** Deploy a single Azure SQL Database.  

**Steps:**  
1. In the Azure Portal, go to **SQL Databases**.  
2. Select **Create** → **Single database**.  
3. On the **Basics** tab:  
   - Choose subscription and resource group.  
   - Name the database.  
   - Create or select an existing server (unique name, region, admin credentials).  
   - Configure options (e.g., elastic pool = No, workload environment).  
4. Select **Review + Create**.  

**Role Assignments:**  
- SQL DB Contributor  
- SQL Security Manager  
- Reader  

🔗 [Quickstart: Create SQL Database](https://learn.microsoft.com/en-us/azure/azure-sql/database/single-database-create-quickstart)  

---

## 2. Azure Machine Learning (Workspace + Compute Instance)  
**Goal:** Set up an ML environment.  

**Steps:**  
1. In **Azure ML Studio**, create a **Workspace**.  
2. Provide workspace details (name, subscription, region, hub optional).  
3. Create the workspace.  
4. Inside the workspace → **New > Compute instance** → Provide name → **Review + Create**.  

**Role Assignments:**  
- Contributor  
- Reader  
- Owner  
- AzureML Data Scientist  

🔗 [Quickstart: Create Azure ML Resources](https://learn.microsoft.com/en-us/azure/machine-learning/quickstart-create-resources)  

---

## 3. Azure OpenAI Service  
**Goal:** Provision GPT-capable resource.  

**Steps:**  
1. In Azure Portal → **Create resource → Azure OpenAI**.  
2. Fill in basics (subscription, group, name, tier, region).  
3. Configure networking.  
4. **Review + Create**.  

**Role Assignments:**  
- Cognitive Services Contributor  
- Cognitive Services User  

🔗 [Create Azure OpenAI Resource](https://learn.microsoft.com/en-us/azure/ai-foundry/openai/how-to/create-resource)  

---

## 4. Azure App Service (Web App Deployment)  
**Goal:** Deploy a web app.  

**Steps:**  
1. Create resource → **App Service**.  
2. Configure basics (name, runtime, region, plan).  
3. **Review + Create**.  

**Role Assignments:**  
- Web Plan Contributor  
- Website Contributor  
- Reader  

🔗 [Quickstart: Create App Service](https://learn.microsoft.com/en-us/azure/app-service/quickstart)  

---

## 5. Azure Storage (Blob / Table / Queue)  
**Goal:** Create storage accounts.  

**Steps:**  
1. Create resource → **Storage account**.  
2. Configure (subscription, group, location, replication, performance).  
3. Create containers, tables, queues.  

**Role Assignments:**  
- Storage Blob Data Contributor  
- Storage Queue Data Contributor  
- Storage Table Data Contributor  
- Reader  

🔗 [Create Storage Account](https://learn.microsoft.com/en-us/azure/storage/common/storage-account-create)  

---

## 6. Azure Data Factory  
**Goal:** Create ETL pipelines.  

**Steps:**  
1. Create resource → **Data Factory**.  
2. Configure (subscription, group, name, version, region).  
3. Author pipelines.  

**Role Assignments:**  
- Data Factory Contributor  
- Reader  

🔗 [Create Data Factory](https://learn.microsoft.com/en-us/azure/data-factory/quickstart-create-data-factory-portal)  

---

## 7. Azure Service Bus / Event Grid  
**Goal:** Messaging infrastructure.  

**Service Bus Steps:**  
1. Create resource → **Service Bus**.  
2. Configure namespace, tier, region.  

**Event Grid Steps:**  
1. Create resource → **Event Grid Topic**.  
2. Add topics/subscriptions.  

**Role Assignments:**  
- Azure Service Bus Data Sender  
- Azure Service Bus Data Receiver  
- EventGrid Contributor  

🔗 [Service Bus Quickstart](https://learn.microsoft.com/en-us/azure/service-bus-messaging/service-bus-quickstart-portal)  
🔗 [Event Grid Quickstart](https://learn.microsoft.com/en-us/azure/event-grid/custom-event-quickstart-portal)  

---

## 8. Azure Logic Apps  
**Goal:** Workflow automation.  

**Steps:**  
1. Create resource → **Logic App (Consumption/Standard)**.  
2. Configure (name, group, plan).  
3. Build workflows.  

**Role Assignments:**  
- Logic App Contributor  
- Logic App Operator  
- Reader  

🔗 [Create Logic App](https://learn.microsoft.com/en-us/azure/logic-apps/quickstart-create-first-logic-app-workflow)  

---

## 9. Azure Functions  
**Goal:** Deploy function apps.  

**Steps:**  
1. Create resource → **Function App**.  
2. Configure basics (runtime, plan, region).  
3. Create and author functions.  

**Role Assignments:**  
- Function App Contributor  
- Reader  

🔗 [Create Function App](https://learn.microsoft.com/en-us/azure/azure-functions/functions-create-function-app-portal)  

---

## 10. Virtual Machine (VM)  
**Goal:** Create a VM.  

**Steps:**  
1. Create resource → **Virtual Machine**.  
2. Configure (name, OS, size, credentials, disks, networking).  
3. **Review + Create**.  

**Role Assignments:**  
- Virtual Machine Contributor  
- Reader  
- (Optional) VM login RBAC:  
  - Virtual Machine Administrator Login  
  - Virtual Machine User Login  

🔗 [Quickstart: Create VM](https://learn.microsoft.com/en-us/azure/virtual-machines/windows/quick-create-portal)  

---

## 11. Azure Cosmos DB  
**Goal:** Multi-model distributed database.  

**Steps:**  
1. Create resource → **Azure Cosmos DB**.  
2. Choose API (SQL, MongoDB, Cassandra, Gremlin, Table).  
3. Configure basics (name, location, capacity mode).  
4. Optionally enable global distribution.  

**Role Assignments:**  
- Cosmos DB Account Contributor  
- Cosmos DB Operator  
- Cosmos DB Reader  

🔗 [Create Cosmos DB Resource](https://learn.microsoft.com/en-us/azure/cosmos-db/create-cosmosdb-resources-portal)  

---

## 12. Azure AI FOUNDRY 

**1. Overview**

This document explains how to deploy Azure AI Foundry (Cognitive Services accounts of kind AIServices) across multiple resource groups using a PowerShell script. 
The script reads a CSV with resource group names and locations, then creates AI Foundry accounts in parallel with throttling to avoid Azure API limits. 

**2. Prerequisites** 

**2.1 System Requirements**

Operating System: Windows 10 or Windows 11 

Software Installation: 

To install PowerShell7 using Winget: 

Open PowerShell5. 

Run the following commands: 

**powershell**

winget search Microsoft.PowerShell 

winget install --id Microsoft.PowerShell --source winget  

For reference, here is a YouTube tutorial:  https://www.youtube.com/watch?v=BYUHFb3PwoE 

To install Azure CLI on Windows using PowerShell, run: 

**powershell** 

$ProgressPreference = 'SilentlyContinue'; Invoke-WebRequest -Uri https://aka.ms/installazurecliwindows -OutFile .\AzureCLI.msi; Start-Process msiexec.exe -Wait -ArgumentList '/I AzureCLI.msi /quiet'; Remove-Item .\AzureCLI.msi 

For guidance, see this video: https://www.youtube.com/watch?v=PP2ymD7rRWE 

**2.2 Permissions** 

Ensure you have an Azure subscription with Contributor or Owner role on the resource groups where AI Foundry will be deployed. (Permissions should already be assigned to all users.) 

You must be logged into Azure CLI with appropriate credentials. 

**2.3 CSV Input File**

Prepare a CSV file named input_details.csv with the following columns and sample data: 

DisplayName | UserPrincipalName      | rgname | Location | 
demo1       | demo1@bloodwarriors.in | demo1-rg | eastus 

rgname: Azure Resource Group name 
DisplayName: User display name 
UserPrincipalName: User email (e.g., demo1@bloodwarriors.in) 
Location: Azure region where AI Foundry will be deployed. Save this CSV file in the same directory as your deployment script. 

**3. Deployment Steps**

Step 1: Clone or Create the Deployment Script 
Save the deployment script as deploy-ai-foundry.ps1 in your working directory. 

Step 2: Prepare the CSV File 
Ensure the input_details.csv file is ready with the required resource groups and location data as described. 

Step 3: Log In to Azure 
Open PowerShell and use the following command to log in: 

az login -> Prompt -> Login with User Credentials 

az account set --subscription "dfcd9032-9c16-4e4c-a6f1-92f202ad529b" 

Step 4: Run the Deployment Script 
Execute the script by running: 

.\deploy-ai-foundry.ps1 

**4. Output**

The AI Foundry accounts will be created in each specified resource group. For example, account names will follow this format: 
demo1-ai-foundry 

---
  
## Regions Suggestions:   

1. EastUS  
2. WestUS  
3. West Europe  
4. North Europe  
5. Central US  
