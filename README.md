# Google Workspace Activities (using REST API) (Preview)
## Step 1. configure Oauth client in google workspace
1. Login to Google cloud console with your Workspace Admin credentials https://console.cloud.google.com.
2. Using the search option (available at the top middle), Search for APIs & Services
![alt text](gw1.png), in the Libary![alt text](gw2.png), search for admin sdk api ![alt text](gw3.png), click and enable ![alt text](gw4.png)
3. after enable Admin SDK API, click "manage"![alt text](gw5.png)
4. create Oauth client![alt text](gw6.png), click "Clients", then "Create client"![alt text](gw7.png)
5. in application type, choose Web application ![alt text](gw8.png), fill **Name**, ex. sentinel and **Authorized redirect URIs** to **https://portal.azure.com/TokenAuthorize/ExtensionName/Microsoft_Azure_Security_Insights** ![alt text](gw9.png)

6. navigate  **Data access** ![alt text](gw10.png), click **Add or remove scopes**, selct **https://www.googleapis.com/auth/admin.reports.audit.readonly** and **https://www.googleapis.com/auth/admin.reports.usage.readonly** ([referenace](https://developers.google.com/workspace/admin/reports/auth?hl=zh-tw)) ![alt text](gw11.png)
## Step 2. Deploy google workspace connector to sentinel
1. deploy connector to azure: [![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#blade/Microsoft_Azure_CreateUIDef/CustomDeploymentBlade/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fhifrank%2Fazure-sentinel-google-workspace-connector%2Fmain%2FGWorkspace.json)
2. in the deployment wizard![alt text](arm.png)<br>
   a. select resource group contains sentinel<br>
   b. region of the sentinel log analytics, ex. East US in the example<br>
   c. name of sentinel logworkspace, ex. alz-law
3. click "Review + create" button and deploy. 
4. configure connector
![alt text](connector.png)
