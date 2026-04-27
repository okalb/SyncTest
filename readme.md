# Exercise 0: Deploy the lab resources

1. [] Log into the lab desktop using **LabUser** and +++@lab.VirtualMachine(Win11-Pro-Base).Password+++.

1. [] From the lab VM's taskbar, launch **PowerShell**.

  ![2nbm7qmn.png](../../Media/2nbm7qmn.png)

1. [] In PowerShell, run the following command:

	`az login`

1. [] When prompted, login using the following credentials:
    
  | Object | Valua |
  | -------- | -------- |
  | Email | `@lab.CloudPortalCredential(User1).Username` |
  | TAP | `@lab.CloudPortalCredential(User1).AccessToken` |

1. [] Close Microsoft Edge and return to the PowerShell window.

1. [] In the PowerShell windows execute the following command:

	`Set-Location "C:\Lab Assets\deploy"; powershell.exe -ExecutionPolicy Bypass -File ".\setup.ps1"`

>[!Note] Once the deployment scripts begins running, you can safely continue to the next exercise.


===
# Exercise 1: Building the Foundry IQ Intelligence Foundation
A dedicated **Microsoft Fabric** workspace is established to serve as the centralized foundation for all **Fabric IQ** capabilities, enabling seamless integration of data, analytics, and AI-driven insights. **Lakehouse** will created in Fabric workspace to build  **Foundry IQ** agent.

**Eva** (**Data Engineer**) is tasked by **Rupesh** to create a governed workspace where **Fabric IQ** artifacts can live securely.

## ✅ Outcome
- Fabric-enabled Workspace created  
- Capacity-backed environment configured  
- Workspace ready for:
  - Lakehouse setup  

In this section of the workshop, you will be logging into the Microsoft Fabric Portal and creating a new Fabric Workspace.

## Task 1.1: User login to Microsoft Fabric
Using a web browser of your choice, please navigate to this Microsoft Fabric link.

### Task 1.1: User login to Microsoft Fabric
Using a web browser of your choice, please navigate to this Microsoft Fabric link.

1. [] In Microsoft Edge, connect to `app.fabric.microsoft.com`  

1. [] At the Fabric login screen, enter the following information:

    | Object | Value |
    | -------- | -------- |
    | Email | `@lab.CloudPortalCredential(User1).Username` |
    | TAP | `@lab.CloudPortalCredential(User1).AccessToken` |

1. [] If prompted with "Stay signed in?" select **Yes** and proceed.

    >[!Note] If you receive a message that **You've selected Microsoft Fabric free**, select **Continue**.
![2m04cjde.png](../../Media/2m04cjde.png)
At the Fabric free, create your account pages, enter any information and select **Get Started**.

>[!Note] You can safely ignore any notifications about Microsoft Fabric (Free) license being assigned

### Task 1.2: Set up a Fabric workspace with proper capacity 

1. [] You should be able to find a New Workspace tile near the top-left area of the screen. Select it to open the Create a workspace blade on the right side.
   
   ![8g82u4mq.png](../../Media/8g82u4mq.png)

1. [] In the Create a workspace blade, enter `workspace@lab.LabInstance.Id` in the Name field.
   
   ![bysvn2ik.png](../../Media/bysvn2ik.png)
	>[!Note] You can safely ignore any messages about **PREMIUM CAPACITY SETTINGS**

1. [] Select Advanced and scroll down to see the License mode. Ensure that **Fabric** is selected.

	![k1mwhjcz.png](../../Media/k1mwhjcz.png)
    
1. [] Next, select the green **Apply** button at the bottom left of the Create a workspace blade.
   
   ![gse1xrsm.png](../../Media/gse1xrsm.png)

1. [] On the following page, you may get a pop-up titled "Introducing task flows (preview)". Select the green **Got it** button.
   
   ![hth7guac.png](../../Media/hth7guac.png)

### Task 1.3: Building a Lakehouse for Foundry IQ
In this task of the workshop, you will be creating a Lakehouse.

1. [] Select the Workspaces option and choose the **workspace@lab.LabInstance.Id** workspace.

    ![4htf5lv3.png](../../Media/4htf5lv3.png)
   
1. [] Select **+ New item** and select `Lakehouse` from the available options.

1. [] In the **New Lakehouse** dialog box, Enter `Retail_Lakehouse_@lab.LabInstance.Id` for the Name, and Ensure the **Lakehouse schemas** option is enabled

1. [] Select **Create**.

    ![LakehouseName.png](../../Media/LakehouseName.png)

    >[!Note] Wait for the Lakehouse to be successfully provisioned.Once created, the Lakehouse will open automatically.

1. [] Verify the following components are available:
   - **Tables** section
   - **Files** section

    ![BlankLakehouse.png](../../Media/BlankLakehouse.png)

    >[!Note] Both Tables and Files section is empty.

1. [] To upload files, select **...** in Files section. Mouseover the **Upload** option and select **Upload files** option.

    ![FileSelection.png](../../Media/FileSelection.png)

1. [] **Select** folder icon at right side to open and choose file path.

    ![ClickFolder.png](../../Media/ClickFolder.png)

1. [] To browse the files from your virtual machine, open File Explorer. Select the address bar, type the path `C:\FabricIQLab\Ontology`.

    ![qkfipn1a.png](../../Media/qkfipn1a.png)

1. [] Select all files from this folder and select **Upload**
    - **retail_ontology_package.iq** 
    - **fabriciq_ontology_accelerator-0.1.0-py3-none-any.whl**
    - **Zava Black Friday Return Policy**

    ![SelectAllFiles.png](../../Media/SelectAllFiles.png)
   
1. [] Close the upload window once these files have been uploaded.

    ![CurrentUploads.png](../../Media/CurrentUploads.png)

1. [] Now, the **Files** section of the Lakehosue has all three files. 

    ![LakehouseWithFiles.png](../../Media/LakehouseWithFiles.png)

### Task 1.4: Loading data into Lakehouse
#### Step 1: Import notebook 
1. [] Navigate to your **Fabric workspace**.

1. [] On the workspace homepage, select the **Import** option.

1. [] From the available options, select **Notebook**. 

1. [] Choose **From this computer** as the source.

    ![Notebookimport.png](../../Media/Notebookimport.png) 

1. [] Select **Upload** to import the notebook.

    ![UploadNotebook.png](../../Media/UploadNotebook.png) 

1. [] To browse the notebooks from your virtual machine, open File Explorer. Select the address bar, type the path `C:\FabricIQLab\Notebooks`, then select the **Generate Lakehouse Data** notebook file and select the **Open** button.

     ![NBimport.png](../../Media/NBimport.png) 

1. [] After upload, notebook will be listed in the workspace area.

    ![NotebookList.png](../../Media/NotebookList.png) 

#### Step 2: Execute notebook
1. [] Select **Generate Lakehouse Data** notebook from the list.
  
    ![NBdirection.png](../../Media/NBdirection.png)

    >[!Note] Notebook will open in a different tab without binding with any datastore (Lakehouse)

  	![NotebookwithoutLakehouse.png](../../Media/NotebookwithoutLakehouse.png) 

1. [] Select **Add data items** and select **From OneLake catalog** to open OneLake ares.

    ![ChooseOneLake.png](../../Media/ChooseOneLake.png) 

1. [] Select **Retail_Lakehouse_@lab.LabInstance.Id**, and then select **Add** to include in the notebook execution.

    ![LakehouseSelection.png](../../Media/LakehouseSelection.png) 

    >[!Note] Now, selected **Lakehouse** will be binded with Notebook.

    ![BindLakehouse.png](../../Media/BindLakehouse.png) 

    >Now, we are good to run this notebook.

1. [] select **Run all** button at top banner and execute entire notebook cell by cell.
    - First cell will install .whl file to execute all refrerenced files.
    - Second cell will execute ontology package and load data in the Lakehouse

        ![LakehouseDataCreation.png](../../Media/LakehouseDataCreation.png) 
      
1. [] Wait for the execution to complete successfully.

1. [] Navigate to the Lakehouse that was created earlier and verify that the data is successfully loaded. 

    ![LHnavigation.png](../../Media/LHnavigation.png) 

1. [] Go to the **Tables** section
   and Select the three dots (⋯) menu and select **Refresh** to load all table under **dbo** schema.

    ![tablerefresh.png](../../Media/tablerefresh.png) 

1. [] Verify that Tables are created automatically
    
    ![LakehouseData.png](../../Media/LakehouseData.png) 

### Task 1.5: Create a data agent with a Lakehouse as the data source
In this task, a **Data Agent** will be created in Fabric workspace and linked with **Lakehouse** data source.

1. [] Navigate to your **Fabric Workspace**.

1. [] In your Fabric workspace, select the **New item** button in the top command bar.

1. [] In the **New item** creation pane, use the search bar to type `Data Agent`.

1. [] Select the **Data Agent** card in the search results and select it to initiate creation.

     ![DAnavigation.png](../../Media/DAnavigation.png)

1. [] in the Input a data agent name field, enter `Retail_DataAgent_@lab.LabInstance.Id`, and select the **Create** button.

     ![FoundryDataAgent.png](../../Media/FoundryDataAgent.png)

1. [] Once the Data Agent opens, navigate to the **Data** tab in the Explorer pane, select **Add Data**, select **Data source**.

    ![datasource.png](../../Media/datasource.png)

1. [] select the **Retail_Lakehouse_@lab.LabInstance.Id** Lakehouse, then select **Add** and verify that the Lakehouse is successfully attached.

    ![FoundryDataAgentLakehouse.png](../../Media/FoundryDataAgentLakehouse.png)

1. [] Expand **Retail_Lakehouse → schemas → dbo → Tables** and select all tables (carriers, customers, demand_signals, forecasts, inventories, order_lines, orders, product_categories, products, promotions, regions, returns, shipments, stores, warehouses).

     ![LHselection.png](../../Media/LHselection.png)

>[!Note] Ensure all the above tables are selected to enable complete analytical coverage for the Retail data agent.

## Task 1.6: Validate the data agent using natural language queries
    
1. [] Select **Agent instructions** from the top menu.

     ![AgentInstructionForFoundry.png](../../Media/AgentInstructionForFoundry.png) 

1. [] In the **Agent instructions** section, remove any existing default content present in the instruction box, provide guidance to control how the agent responds by entering instructions. 

     
    ### Sample Agent Instructions (Copy & Paste)

    Copy the below instructions and paste them into the **Agent instructions** section:

     ```
     **Purpose:**
     This data agent is designed to answer analytical and operational questions for retail business users using the Retail Lakehouse data model, which contains historical transactional and master data.

     **Planning Rules**
     Understand the user intent and classify it into:
     Sales
     Inventory
     Customer
     Promotion
     Supply Chain
     Forecasting
     Since only Lakehouse data is available:
     All queries should be treated as historical analysis
     Break complex queries into:
     Entity identification
     Relationship traversal
     Metric aggregation
     Always validate:
     Time filters (date, month, year, etc.)
     Granularity (store, region, product, category)

     **Data Source Mapping**
     - Sales & Orders
     orders, order_lines
     Revenue, sales transactions, quantity sold
     - Customer Insights
     customers
     Customer segmentation and behavior
     - Product Analysis
     products, product_categories
     Product performance and category trends
     - Inventory & Supply Chain
     inventories, shipments, warehouses, stores, carriers
     Stock levels, logistics, fulfillment
     - Promotions
     promotions
     Campaign performance and impact on sales
     - Returns
     returns
     Return trends, defects, and refund analysis
     - Forecasting
     forecasts
     Planned demand and expected trends
     - Geography
     regions
     Regional performance analysis
     
     **Terminology Standardization**
     - Revenue = Sum(order_lines.LineTotalAmount)
     - Sales Volume = Sum(order_lines.quantity)
     - Inventory Level = Available stock in inventories
     - Demand = Forecast values (from forecasts table)
     - Conversion Rate = Orders / Customers
     - Return Rate = Returns / Orders
     
     **Query Behavior Rules**
     - Prefer aggregated insights over raw data unless explicitly      requested
     - Always:
     Apply relevant filters (date, region, product, etc.)
     Use joins via relationships (e.g., orders → customers →      regions)
     - For ambiguous queries:
     Ask clarifying questions OR
     Provide best assumption with explanation
     
     **Response Style**
     - Clear and business-friendly explanations
     - Include:
      - Key insights
      - Supporting metrics
      - Trends (for time-based queries)
     - Use bullet points for readability
     - Highlight:
       - Patterns
       - Anomalies
       - Comparisons
     - Avoid overly technical or database-specific language
     ```

1. [] After entering the instructions, select **Publish** to save the configuration.

    ![agentpublish.png](../../Media/agentpublish.png)

1. [] On the Publish data agent popup, select **Publish**

1. [] After adding the instructions, select the **close (✕) icon** on the **Agent instructions** tab to exit the window.

     ![agentclosing.png](../../Media/agentclosing.png)

1. [] Once closed, the main Data Agent interface will be displayed, where you can start querying the agent using natural language.

1. [] In the query input area, ask questions using natural language, for example:

    ````
    Which regions are underperforming in sales?
    ````
1. [] Submit the query and review the response generated by the Data Agent.

     ![agentresponse1.png](../../Media/agentresponse1.png)

1. [] Observe how the agent:
   - Interprets the question  
   - Queries the underlying data using the ontology  
   - Provides insights in a readable format  

1. [] Try multiple queries and refine your questions to explore additional insights.

     ```
     - Which products are frequently returned and impacting revenue?
     - Which products are at risk of stockout?
     - Which stores have the highest number of orders?
     ```

>[!Note]  Clear and specific questions provide more accurate results.  
> - Responses may vary depending on how the question is framed.  
> - The Data Agent uses the Ontology to translate natural language into meaningful queries.

## Task 1.7: Configure permissions

These setting are required for later exercises to function correctly.

### Configure AI Search service permissions

1. [] Open a new browser tab and connect to `portal.azure.com`.

1. [] If prompted for credentials, enter the following information:

    | Object | Value |
    | -------- | -------- |
    | User | `@lab.CloudPortalCredential(User1).Username` |
    | TAP | `@lab.CloudPortalCredential(User1).AccessToken` |

1. [] Select **Resource groups**, and then select **RG1**.

1. [] Select **srch-foundry-iq-lab-@lab.LabInstance.Id** (Search service).

1. [] In the left panel, expand **Settings**, and then select **Identity**.

1. [] Set the Status to **On**, and then select **Save**

	![1gadsiuz.png](../../Media/1gadsiuz.png)

1. [] Select **Yes** to confirm.

<!-- ### Configure Foundry Permissions

1. [] Use the breadcrumbs menu at the top of the screen to return to the **RG1** Resource group.

1. [] Select **foundry-iq-lab-@lab.LabInstance.Id**

1. [] On the left menu select **Access control (IAM)**.

1. [] Select **+ Add** > **Add role assignment**.

1. [] On the Role tab, search for `Azure AI User`.

1. [] Select **Azure AI User**, then select **Next**.

1. [] On the Members tab, choose **User, group, or service principal**.

1. [] Select **+ Select members**.

1. [] Search for `@lab.CloudPortalCredential(User1).Username`.

1. [] **Select the account**, then choose **Select**.

1. [] Select **Review + assign** twice. -->

### Configure Workspace permissions

1. [] Return to the **Fabric browser tab**.

1. [] Navigate to your **Fabric Workspace**.

1. [] In the upper right, select **Manage access**.

	![yjzz3r16.png](../../Media/yjzz3r16.png)

1. [] On the Manage access flyout, select **+ Add people or groups**.

	![txb80l84.png](../../Media/txb80l84.png)

1. [] Enter the name of your AI Search service `srch-foundry-iq-lab-@lab.LabInstance.Id`

1. [] In the dropdown below, select **Contributor**, and then select **Add**.

    ![3y9af9gc.png](../../Media/3y9af9gc.png)




===

# Exercise 2: 🏗️ Provision the AI Foundry Foundation

This exercise focuses on provisioning the **AI Foundry Foundation**, including the creation of a **Foundry Hub** and **Project**, and deploying foundational AI models such as **GPT‑4o** and **text-embedding-ada-002**.

Miguel provisions the following core components within Microsoft Foundry:
- Microsoft Foundry environment  
- Foundry Agent Service  
- Secure identity and governance framework  

> *"Agents must be observable, auditable, and secure - from day one."*

## ✅ Outcome
- Foundry Project successfully created  
- Base AI models deployed  
- Secure runtime environment ready for agent executio

### Task 2.1: Provision a Foundry Hub and Project 

1. [] In Microsoft Edge, navigate to the `https://portal.azure.com`.

1. [] In the Azure Portal, search **resource groups** and select Resource groups.
    ![image1.png](../../Media/image1.png)

1. [] Select the **RG1** resource group.

    ![image2.png](../../Media/image2.png)

1. [] Select **foundry-iq-lab-@lab.LabInstance.Id**.

    ![image3.png](../../Media/image3.png)

1. [] Select **Go to Foundry portal** to navigate to the Foundry project.

    ![image6.png](../../Media/image6.png)

1. [] Ensure that **New Foundry** is toggled **on** at the top of the menu bar 

  ![image7.png](../../Media/image7.png)

1. [] Select **Build** to create agents, deploy models, and build workflows.

    >[!Alert] If you do not see the Build option, ensure New Foundry is toggled on,

### Task 2.2: Deploy LLM and embedding models

In this task, you will deploy a reasoning model and an embedding model in Foundry.

1. [] On the Microsoft Foundry page, select **Models**, then select **Deploy base models**.

    ![image8.png](../../Media/image8.png)

1. [] Search for `gpt-4o` then select **gpt-4o**.

    ![image9.png](../../Media/image9.png)

1. [] Select the **Deploy** dropdown and select **Default settings**.

    ![image11.png](../../Media/image11.png)

1. [] Once the model is deployed, open the model **playground**.
   
   ![image97.png](../../Media/image97.png)

1. [] Select **Details** tab to view the **key**, **endpoint**, and **other model information**.

   ![image98.png](../../Media/image98.png)

1. [] Again navigate to **Models** section to deploy embedding model, then select **Deploy base models**.

    ![image8.png](../../Media/image8.png)

1. [] Search `text-embedding-ada-002` then select **text-embedding-ada-002**.

    ![image12.png](../../Media/image12.png)

1. [] Select the **Deploy** dropdown and select **Default settings**.

    ![image13.png](../../Media/image13.png)

### What We Learned

- How to access the Azure Portal and navigate to the Foundry portal.
- How to deploy LLM and embedding models in Foundry using default settings.

### Next Exercise

In the next exercise, we will learn how to integrate enterprise knowledge using Foundry IQ, including setting up indexed sources for unstructured files and connecting to Microsoft Fabric Lakehouse for real-time structured data retrieval.

===
# Exercise 3: Integrate Enterprise Knowledge via Foundry IQ
 
This exercise focuses on integrating enterprise knowledge using **Foundry IQ** by enabling indexed sources for unstructured data and federated sources for real-time structured data retrieval, along with connectivity to the **Microsoft Fabric Lakehouse**.
**Ryan** (Customer) asks detailed product-related questions during an engagement.

To enable accurate and context-aware responses, Miguel integrates enterprise content sources such as:
- SharePoint Product Guides  
- Internal Policy Documents  
- Campaign and Marketing Materials  

**Foundry IQ** provides permission-aware, citation-backed grounding by connecting to these knowledge sources - ensuring that agent responses are both secure and traceable.

## ✅ Outcome
- Foundry IQ Knowledge Base configured  
- Multi-source enterprise grounding enabled  
- No custom RAG code required for knowledge integration

### Task 3.1: Set up indexed sources for unstructured files and federated sources for real-time structured data retrieval. 

1. [] On the left side, select **Knowledge** to configure Foundry IQ.

    ![image14.png](../../Media/image14.png)

1. [] On the dropdown below Azure AI Search resource, and select **srch-foundry-iq-lab-@lab.LabInstance.Id**.

    ![image16.png](../../Media/image16.png)

1. [] In the Auth Type dropdown that appears, select **API Key**, and then select **Connect**.

1. [] Select **Create a knowledge base**.

    ![image17.png](../../Media/image17.png)

1. [] Select **Azure Blob Storage** to index unstructured return policy files, then select **Connect**.

    ![image18.png](../../Media/image18.png)

1. [] On the Create a knowledge source popup, enter the following information:


  | Option | Value |
  | -------- | -------- |
  | Name | `customer-loyalty-data` |
  | Storage account | **stfiqlab@lab.LabInstance.Id** |
  | Container name | **customerloyalty** |
  | Authentication type | **API Key** |
  | Embedding model | **text-embedding-ada-002-1** |

1. [] Select **Create**.

1. [] In the same **Knowledge base** page, in the **Knowledge source** section, select **Create new** and then select **Azure AI Search Index**.

    ![image23.png](../../Media/image23.png)

1. [] Enter `product-catalog` in the Name field. 

1. [] In the Select search service dropdown, select **product-catalog-index**, then select **Create**.

    ![image24.png](../../Media/image24.png)

### Task 3.2: Connect to a Microsoft Fabric Lakehouse to enable direct access to enterprise data

1. [] On the same **Knowledge base** page, in the **Knowledge source** section, select **Create new** and then select **Microsoft OneLake** to connect Lakehouse to enable direct access to enterprise data without the need for data movement.

    ![image93.png](../../Media/image93.png)

1. [] For the name enter `return-policy`.

1. [] A the bottom of the window, select the **Retal_Lakehouse_@lab.LabInstance.Id**, and then select **Create**.

1. [] At the top of the Basic configuration page, in the Name field, enter `foundry-lab-knowledgebase`

1. [] For the **Chat completion model** field, select **gpt-4o**.

1. [] Review all the **Knowledge sources**, and then select **Save knowledge base**.

    ![image96.png](../../Media/image96.png)

### What We Learned

- How to configure Foundry IQ by connecting to Azure AI Search and creating knowledge bases.
- How to index unstructured data from Azure Blob Storage and structured data from Azure AI Search indexes.
- How to connect to Microsoft Fabric Lakehouse for direct access to enterprise data.

### Next Exercise

In the next exercise, we will learn how to build intelligent agents with tool calling, including creating agent personas and implementing routing logic for user queries.

===
# Exercise 4: Build intelligent agents with tool calling
This exercise focuses on building intelligent agents with tool-calling capabilities, including defining agent personas, configuring system instructions, and attaching relevant enterprise knowledge sources.

Miguel creates a **Supervisor Agent** capable of orchestrating insights across enterprise systems by:
- Calling Fabric Data Agents for structured business insights  
- Calling Foundry IQ for unstructured enterprise knowledge  

> *"The agent shouldn't know everything - it should know who to ask."*

## ✅ Outcome
- Tool-calling Agent successfully created  
- Fabric IQ and Foundry IQ integrated for unified intelligence  
- Business-aware reasoning enabled across structured and unstructured data source

### Task 4.1: Create agent persona and system instructions

1. [] On the Microsoft Foundry page, on the left side, select **Agents**.

    ![image32.png](../../Media/image32.png)

1. [] Select **Create agent**. 

    ![image33.png](../../Media/image33.png)

1. [] Enter `Supervisor-Agent` as Agent name, then select **Create**.

    ![image34.png](../../Media/image34.png)

1. [] Once the agent is created, you will be redirected to the agent playground page. From the Model dropdown, select **gpt-4o**  and paste the following instructions in the **Instructions** section

    ```
    You are the Supervisor Agent responsible for routing user queries to the appropriate specialized agent. Analyze the user's request and determine which agent should handle it. Based on the intent of the query, call the relevant agent listed below.

    Agent Routing Rules
    1. [] Sales-Associate-Agent
    •	Call this agent when the user asks about:
          o	Product recommendations
          o	DIY project guidance
          o	Interior design suggestions
          o	Product features or comparisons
          o	Requests to visualize designs or generate images
          o	Upselling or discovering suitable products
    1. [] Rewards-Campaign-Agent
    •	Call this agent when the user asks about:
          o	Loyalty programs or reward points
          o	Promotional campaigns
          o	Discount offers or eligibility
          o	Black Friday or seasonal promotions
          o	Customer-specific discounts or campaign details
    1. [] Inventory-Agent
    •	Call this agent when the user asks about:
          o	Product availability
          o	Inventory levels
          o	Stock status
          o	Product location in the warehouse or store
          o	Whether a product is in stock or out of stock
    Decision Rule
    •	Carefully analyze the intent of the user query and route the request to only one most relevant agent.

    Output Format
    Return only the agent name no extra space or new line simple string. We want for example:
    Sales-Associate-Agent
    ```

  ![image35.png](../../Media/image35.png)

1. [] Select **Save**, then select the back arrow (**⬅**) to create additional Agents.

  ![image36.png](../../Media/image36.png)

1. [] Select **Create agent**.

  ![image37.png](../../Media/image37.png)

1. [] Paste `Sales-Associate-Agent` as Agent name and then select **Create**.

  ![image38.png](../../Media/image38.png)

1. [] Once the agent is created, you will be redirected to the playground page of the agent. From the Model drop-down, select **gpt-4o** and paste below following instructions in the **Instructions** section.

    ```
    Interior Design Agent Guidelines
    ========================================
    - You are an Interior Designer salesperson working for Zava and helps customers with DIY Projects and interior design queries.
    - Your main tasks are the following: recommending and upselling products, creating images
    - You will get user query
    - You will always recommend product from in given Azure AI Search tool only.
    - You will keep asking questions to the user and keep recommending.
    - When you get video or image, reply saying "I see you uploaded..."
    - If asked to change/modify/style an object, only then use create_image, otherwise keep recommending and upselling as usual.

    Your response should only come from the given knowledge and you must return that response in following JSON format

    answer: your answer,
    image_output: if there, otherwise empty
    products: [
      {
        "id": "<ProductId>",
        "name": "<ProductName>",
        "type": "<Category>",
        "description": "<ProductDescription>",
        "price": "<FormattedPriceWithDollarSign>"
      },
    {..},
      ...
    ]

    Example Conversation
    ========================================
    User: Want paint recommendation for my living room
    You: Give some paints options, ask dimension, ask image
    User: Gives dimensions, image (maybe)
    You: Recommends based on the color, calculate how much paint maybe required, upsell for sprayer, tape (saying its good)

    Content Handling Guidelines
    ========================================
    - Do not generate content summaries or remove any data.

    ---
    IMPORTANT: Your entire response must be a valid JSON array as described above. Do not include any other text or formatting.
    ```

  ![image39.png](../../Media/image39.png)

1. [] Select **Save**, then select the back arrow  (**⬅**) to create additional Agents.

  ![image40.png](../../Media/image40.png)

1. [] Select **Create agent**.

  ![image37.png](../../Media/image37.png)

1. [] Paste `Rewards-Campaign-Agent` as Agent name and then select **Create**.

  ![image41.png](../../Media/image41.png)

1. [] Select **gpt-4o** from the drop down and paste below following instructions in the **Instructions** section.

    ```
    Apply personalized discounts to customers based on their loyalty information and explain the applicable Black Friday promotional tiers using the provided knowledge sources.
    ________________________________________
    Response Behavior
    •	Generate responses only from the retrieved knowledge and tool outputs. Do not assume or invent any values.
    •	When a customer name is included, respond in a friendly first-person tone and include celebratory emojis such as 🎉, 😊, or 🛍️.
    •	When the internal team asks about discount tiers, provide an average discount range instead of listing every individual percentage.
    •	Ensure the response clearly reflects the loyalty information and discount values retrieved from the knowledge source or tools.
    ________________________________________
    Response Format
    Always return the response in the following JSON format:
    {
    "answer": "<response generated using the knowledge and tool results>",
    "discount_percentage": "<discount value retrieved from the knowledge or tool>"
    }
    ________________________________________
    Content Handling Guidelines
    •	Do not summarize, filter, or remove any important information from the knowledge source.
    •	Responses must strictly follow the information retrieved from the given knowledge only.
    •	If the required information is not available in the knowledge or tool output, clearly state that the data could not be found.
    ```

  ![image42.png](../../Media/image42.png)

1. [] Select **Save** and then select the back arrow (**⬅**) to create the next Agent.

  ![image43.png](../../Media/image43.png)

1. [] Select **Create agent**.

  ![image37.png](../../Media/image37.png)

1. [] Paste `Inventory-Agent` as Agent name and then select **Create**.

  ![image45.png](../../Media/image45.png)

1. [] Select **gpt-4o** from the drop down and paste below following instructions in the **Instructions** section.

    ```
    You are Inventory check agent,
    •	Your task is to check the inventory status.
    •	When a user asks to check the inventory for a product, send the product name to the Fabric Data Agent tool.
    •	Return the response including inventory levels, inventory status, and location.
    Content Handling Guidelines
    •	Do not generate summaries or remove any data from the response.
    •	The response must come only from the Fabric Data Agent tool output.
    ```

  ![image46.png](../../Media/image46.png)

1. [] Select **Save** and then select the back arrow (**⬅**) to return.

  ![image47.png](../../Media/image47.png)

### Task 4.2: Attach configured knowledge sources to the agent

1. [] Select **Rewards-Campaign-Agent**.

  ![image48.png](../../Media/image48.png)

1. [] Select **Add** from the **Knowledge** dropdown, then select **Connect to Foundry IQ**.

  ![image49.png](../../Media/image49.png)

1. [] Select **srch-foundry-iq-lab-@lab.LabInstance.Id** as the Connection, then select **foundry-lab-knowledgebase** and select **Connect**

  ![image50.png](../../Media/image50.png)

1. [] By default, **Web Search** is added. Select the three dots and **remove it** before proceeding.

1. [] Review the connected **Foundry IQ knowledge base**, then select **Save** and select **⬅** to configure Foundry IQ knowledge base to another agent.

  ![image51.png](../../Media/image51.png)

1. [] Select **Sales-Associate-Agent**.

  ![image52.png](../../Media/image52.png)

1. [] Select **Add** from the **Knowledge** dropdown, then select **Connect to Foundry IQ**.

  ![image53.png](../../Media/image53.png)

1. [] Select **srch-foundry-iq-lab-@lab.LabInstance.Id** as the Connection, then select **foundry-lab-knowledgebase** and select **Connect**

  ![image50.png](../../Media/image50.png)

1. [] By default, **Web Search** is added. Select the three dots and **remove it** before proceeding.

1. [] Review the connected **Foundry IQ knowledge base**, select **Save** and select the back arrow (**⬅**).

	![image54.png](../../Media/image54.png)

### Task 4.3: Implement agent Tool Calling capabilities


#### Copy Fabric workspace information

Before you continue to configure the agents you must first copy some information from the Fabric Workspace.

1. [] Swicth to your browser tab that has Fabric open or on a new tab open `app.fabric.microsoft.com`.

1. [] Select the Workspaces option and choose the **workspace61234584** workspace.

1. [] At the bottom of the page, select the **Retail_DataAgent_@lab.LabInstance.Id**

1. [] From the URL at the top of the browser, copy the following sections into the textboxes below:

  **Workspace ID** (The part of the URL after /groups/ and before the next /)
  @lab.TextBox(WorkspaceID)

	![6754ms52.png](../../Media/6754ms52.png)


	Artifact ID (The part of the URL after /aiskills/ and before the ?)
  @lab.TextBox(ArtifactID)

	![fzoqmxhw.png](../../Media/fzoqmxhw.png)

    >[!Alert] Do not copy the slashes or question marks, only copy the characters in between.

#### Configure Tool

1. [] Return to the **Foundry** tab in your browser.

1. [] Select **Inventory-Agent**.

  ![image57.png](../../Media/image57.png)

1. [] Under the Tools dropdown,Select **Add**, then select **Browse all tools**.

  ![image58.png](../../Media/image58.png)

1. [] Select **Fabric Data Agent**, then select **Add tool**.

  ![image59.png](../../Media/image59.png)

1. [] For the Workspace ID, enter `@lab.Variable(WorkspaceID)`

1. [] For the Artifact ID, enter `@lab.Variable(ArtifactID)`

1. [] Select **Connect**.

1. [] By default, **Web Search** is added. Select the three dots and **remove it** before proceeding.

1. [] Review the connected **Foundry Data Agent** tool, select **Save** and select **⬅**.

  ![image61.png](../../Media/image61.png)

### What We Learned

- How to create multiple agents with specific roles and instructions for routing and specialized tasks.
- How to implement tool calling by attaching knowledge sources and data agents to agents.
- How to configure agents for product recommendations, rewards campaigns, and inventory checks.

### Next Exercise

In the next exercise, we will learn how to configure multi-agent orchestration and validation using workflows to coordinate between agents.

===
# Exercise 5: 🔄 Multi-Agent Orchestration and Validation

This exercise focuses on configuring and validating **multi-agent workflows** that coordinate interactions between specialized agents to support end-to-end business processes.

During high-demand events such as **Holiday Sales**, multiple domain-specific agents collaborate to deliver seamless customer experiences:

- Interior Designer Agent recommends products  
- Rewards Agent applies eligible discounts  
- Responsible AI Agent blocks unsafe or non-compliant prompts  
- Checkout Agent finalizes the customer order  

All agent interactions are orchestrated by the **Supervisor Agent** to ensure coordinated decision-making across systems.

## ✅ Outcome
- Multi-agent orchestration successfully configured  
- Business-aligned AI workflows enabled  
- Safe and scalable automation across agent-driven processes

### Task 5.1: Configure multi-agent orchestrator and specialist agents

1. [] Select **Workflows**.

  ![image62.png](../../Media/image62.png)

1. [] Select **Create** and then select **Blank workflow**.

  ![image63.png](../../Media/image63.png)

1. [] Select **YAML**.

  ![image64.png](../../Media/image64.png)

1. [] Paste the below following **YAML script** and select **Save**.

    ```
    kind: workflow
    trigger:
      kind: OnConversationStart
      id: trigger_wf
      actions:
        - kind: SetVariable
          id: action-1768237669100
          variable: Local.Var2679
          value: =System.LastMessage
        - kind: InvokeAzureAgent
          id: action-1768237693978
          agent:
            name: Supervisor-Agent
          input:
            messages: =System.LastMessage
          output:
            autoSend: true
            messages: Local.Var5755
        - kind: ConditionGroup
          conditions:
            - condition: =Last(Local.Var5755).Text = "Sales-Associate-Agent"
              actions:
                - kind: InvokeAzureAgent
                  id: action-1768237857121
                  agent:
                    name: Sales-Associate-Agent
                  input:
                    messages: =System.LastMessage
                  output:
                    autoSend: true
              id: if-action-1768237712578-0
            - condition: =Last(Local.Var5755).Text = "Rewards-Campaign-Agent"
              actions:
                - kind: InvokeAzureAgent
                  id: action-1768237897049
                  agent:
                    name: Rewards-Campaign-Agent
                  input:
                    messages: =System.LastMessage
                  output:
                    autoSend: true
              id: if-action-1768237712578-0p9xo7ga
            - condition: =Last(Local.Var5755).Text = "Inventory-Agent"
              actions:
                - kind: InvokeAzureAgent
                  id: action-1768237934785
                  agent:
                    name: Inventory-Agent
                  input:
                    messages: =System.LastMessage
                  output:
                    autoSend: true
              id: if-action-1768237712578-ma22fceo
          id: action-1768237712578
          elseActions:
            - kind: SendActivity
              activity: " "
              id: action-1768238054760
    id: ""
    name: FoundryIQ-Workflow
    description: ""
    ```
  ![image65.png](../../Media/image65.png)

1. [] Enter `FoundryIQ-Workflow` in the Workflow Name field and select **Save** button.

  ![image66.png](../../Media/image66.png)

1. [] Review the **workflow**, select **Publish** dropdown, then select **Publish as workflow app**.

    >[!Note] You may see the workflow in a **horizontal layout** by default. If you want to change it to vertical, select the Vertical Layout button.

  ![image67.png](../../Media/image67.png)

1. [] Select the checkbox, then select **Publish**.

  ![image68.png](../../Media/image68.png)

    >[!Note] It might take few seconds to publish workflow in Foundry.
  
1. [] The workflow published successfully. Select **Close**.
  
    ![image99.png](../../Media/image99.png)


### Task 5.2: Validate the end-to-end agentic workflow

**Note:** This section demonstrates how individual agents are invoked and how they operate.
Note: Before validating the workflow, test the individual agents and approve the tools. Tool approval cannot be completed within the workflow preview and may result in errors. Also, this feature is currently in preview.

1. [] Select **Preview**.

  ![image69.png](../../Media/image69.png)

1. [] Enter prompt `Hey! I'm planning to paint my living room but I'm not sure which color would look best. Can you recommend some paint shades?,` then select **Send button**.

  ![image70.png](../../Media/image70.png)

    >[!Note] If prompted to approve the tool, select **Always approve all tools**
		![96fk8k1d.png](../../Media/96fk8k1d.png)

1. [] The **response** of the agents can be seen on the right side (See image pointer/box 1). You can also see the **called Agents** during the process on the right side and in the workflow (See image pointers/boxes 2 and 3).

    >[!Note] The response provides suitable paint shade recommendations for the living room along with brief descriptions. The expected outcome is to suggest relevant and aesthetically pleasing colors that help the user make an informed decision.

  ![image71.png](../../Media/image71.png)

1. [] Enter prompt  `Can you tell me Joe's customer loyalty tier and discount?`, then select **Send button**.

  ![image72.png](../../Media/image72.png)

1. [] The **response** of the agents can be seen on the right side (See image pointer/box 1). Note that we have received this response in JSON format.  You can also see the **called Agents** during the process on the right side and in  the workflow (See image pointers/boxes 2 and 3).

    >[!Note] The response displays Joe's loyalty details, including a personalized message and discount. The expected outcome is to identify Joe's loyalty tier as Platinum and return the 32.40% discount.

  ![image73.png](../../Media/image73.png)

1. [] Enter prompt  `Which products are at risk of stockout, and how can we optimize inventory to avoid shortages?`, then select **Send button**.

  ![image74.png](../../Media/image74.png)

1. [] The **response** of the agents can be seen on the right side (See image pointer/box 1).  You can also see the **called Agents** during the process on the right side and in  the workflow (See image pointers/boxes 2 and 3).

  ![image75.png](../../Media/image75.png)

1. [] Enter prompt  `Which products are driving high return volumes that are impacting available inventory levels, and how should inventory planning be adjusted to minimize these returns?`    
The **response** of the agents can be seen on the right side (See image pointer/box 1).  You can also see the **called Agents** during the process on the right side and in  the workflow (See image pointers/boxes 2 and 3).

  ![image100.png](../../Media/image100.png)

### Task 5.3: Inspect the execution path using the Trace tool

1. [] In the Workflow page, select **Traces**, then select **Create or connect**.
**Note:** If you do not see the option to **create or connect** to Application Insights, ignore Steps 1 and 2, as Application Insights has already been connected.

  ![image76.png](../../Media/image76.png)

1. [] Select the **foundryiq-appinsight** as Application insights resource name, then select **Connect**.

  ![image77.png](../../Media/image77.png)

1. [] Review all the **details**

  ![image78.png](../../Media/image78.png)

1. [] Select any one of the **Conversation IDs**, to review the **agent** and **tool call**.  You can also review the **input**, **output**, and **metadata** for that conversation.

  ![image79.png](../../Media/image79.png)

### What We Learned

- How to create and configure workflows for multi-agent orchestration using YAML.
- How to publish workflows as apps and validate agent interactions through previews.
- How to inspect execution paths and traces for debugging and monitoring agent performance.

### Next Exercise

In the next exercise, we will learn how to enforce guardrails and safety policies, and define evaluation metrics for assessing agent performance.

===
# Exercise 6:🛡️ Observability, Evaluation, and Guardrails
This exercise focuses on enabling end-to-end **observability**, implementing **evaluation frameworks**, and enforcing **guardrails** to ensure enterprise-grade safety and governance for AI-driven agents.

**April (CEO)** emphasizes the need for trust and transparency in automated decision-making:
> *"If AI makes decisions, I need to see, trust, and govern them."*

To meet these requirements, Miguel enables the following capabilities:
- Telemetry for agent activity and performance monitoring  
- Prompt evaluation for response quality and alignment  
- Guardrails and policy enforcement for Responsible AI  

## ✅ Outcome
- End-to-end observability implemented  
- Responsible AI policies enforced  
- Enterprise-ready agents with governance and auditability

### Task 6.1: Enforce guardrails and safety policies

1. [] From the left pane, select **Guardrails** and then select **Create**.

    ![image80.png](../../Media/image80.png)

1. [] Under the **Controls** section, select the **Risk Type** checkbox for the dropdowns : **Jailbreak**, **Content Safety**, and **Protected Materials**, then select **Next**.

    ![image81.png](../../Media/image81.png)

1. [] Under the **Select agents and models** section, select **Add agents**, select the **Name** checkbox to include all agents, then select **Save**.

    ![image82.png](../../Media/image82.png)

1. [] Select **Next**.

    ![image83.png](../../Media/image83.png)

1. [] Under the **Review** section, paste `Guardrail11` as Guardrails name, Select **Submit**.

    ![image84.png](../../Media/image84.png)

### Task 6.2: Define evaluation metrics and run offline/online assessments

1. [] Select **Evaluations** and then select **Create**.

    ![image85.png](../../Media/image85.png)

1. [] Under the **Target: Agent** section, select the **Supervisor** agent, then select **Next**.

    ![image86.png](../../Media/image86.png)

1. [] Under the **Data** section, select **Generate**. Leave other values as default and enter `10` for **Number of rows**, then select **Confirm**.

    ![image87.png](../../Media/image87.png)

1. [] Select **Next**.

    ![image88.png](../../Media/image88.png)

1. [] Under the **Criteria** section, select **Next**.

    ![image89.png](../../Media/image89.png)

1. [] Under the **Review** section, enter `eval-7gthxnri` as **Evaluation name** and select **Submit**.

    ![image90.png](../../Media/image90.png)

    > **Note:** It might take a few seconds to load.

1. [] Review the **Evaluation runs** and **Evaluators**.

    ![image91.png](../../Media/image91.png)

    >[!Alert] Do not close the page until the evaluation run status is complete.

**Note:** Similarly, perform evaluation on the other agents.

### What We Learned

- How to create and apply guardrails for content safety, jailbreak prevention, and protected materials.
- How to set up evaluations for agents using generated data and predefined criteria.
- How to monitor and assess agent performance through evaluation runs and metrics.

### Next Exercise

This concludes the "Building Foundry IQ" lab series.

## Lab Conclusion

Throughout this comprehensive lab, we journeyed from provisioning the foundational elements of ***Microsoft Foundry*** 🤖 to deploying sophisticated ***AI agents*** capable of intelligent interactions. Starting with setting up the ***Foundry Hub*** and deploying essential models like ***GPT-4o*** and ***text-embedding-ada-002***, we progressed to integrating enterprise ***knowledge*** 🧠 via ***Foundry IQ***, indexing unstructured ***data*** 📊 from ***Azure Blob Storage*** and structured ***data*** from ***AI Search indexes***, and connecting directly to ***Microsoft Fabric Lakehouse*** for seamless ***data access***.

We then delved into building intelligent ***agents*** 👥 with ***tool calling***, creating specialized ***agents*** for sales assistance, rewards campaigns, and inventory management, each equipped with tailored instructions and ***knowledge sources***. The orchestration phase taught us to coordinate multiple ***agents*** through ***workflows*** 🔄, validating their end-to-end operations and inspecting execution paths via ***traces*** for robust debugging and monitoring.

Finally, we emphasized ***observability*** and ***safety*** by implementing ***guardrails*** 🛡️ to enforce content policies and conducting ***evaluations*** 📈 to measure ***agent performance***, ensuring reliable and ethical ***AI deployments***. Happy learning as you continue to explore and build with ***Microsoft Foundry*** and ***Fabric IQ***! 🚀

