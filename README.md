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

**Sign In and Create a Project**
1. Sign in at ai.azure.com with your Azure account. 

2. Once signed in, choose “Create new” or “Create a project”. 

3. Select the project type: 
- Foundry project – recommended for building agents and working with Azure AI Foundry APIs. 

4. Configure basics: 
a. Project Name 
b. Resource Group (new or existing) 
c. Location / Region 
d. Click Create and wait for provisioning. 

5. Accessing Your API Key (Endpoint & Credentials) 
- Open the project in the Azure AI Foundry portal. 
- In the Overview section, you’ll find your project endpoint—this is the URL you’ll use to call the API. 

🔗 https://learn.microsoft.com/en-us/azure/ai-foundry/how-to/create-projects 

---
  
## Regions Suggestions:   

1. EastUS  
2. WestUS  
3. West Europe  
4. North Europe  
5. Central US  
