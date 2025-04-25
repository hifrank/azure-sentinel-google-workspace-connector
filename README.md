# Google Workspace Activities (using REST API) (Preview)
## Step 1. Configure OAuth client in Google Workspace
1. Login to Google Cloud Console with your Workspace Admin credentials: https://console.cloud.google.com.

2. Using the search option (available at the top middle), search for **APIs & Services**.
![alt text](gw1.png) In the **Library** ![alt text](gw2.png), search for **Admin SDK API** ![alt text](gw3.png), click and enable it ![alt text](gw4.png).

3. After enabling the **Admin SDK API**, click **Manage** ![alt text](gw5.png).

4. Create an OAuth client ![alt text](gw6.png). Click **Clients**, then **Create client** ![alt text](gw7.png).

5. In the application type, choose **Web application** ![alt text](gw8.png). Fill in the **Name** (e.g., Sentinel) and **Authorized redirect URIs** to **https://portal.azure.com/TokenAuthorize/ExtensionName/Microsoft_Azure_Security_Insights** ![alt text](gw9.png).

6. Navigate to **Data access** ![alt text](gw10.png), click **Add or remove scopes**, and select:
   - **https://www.googleapis.com/auth/admin.reports.audit.readonly**
   - **https://www.googleapis.com/auth/admin.reports.usage.readonly**
   ([reference](https://developers.google.com/workspace/admin/reports/auth?hl=zh-tw)) ![alt text](gw11.png).

7. To get the OAuth ID & secret ![alt text](gw12.png), click the client name. You should be able to get info like this ![alt text](gw13.png). Copy this info, as you will fill it in the Sentinel connector in the next step.

## Step 2. Deploy Google Workspace connector to Sentinel
1. Deploy the connector to Azure:  
   [![Deploy to Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#blade/Microsoft_Azure_CreateUIDef/CustomDeploymentBlade/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fhifrank%2Fazure-sentinel-google-workspace-connector%2Fmain%2FGWorkspace.json)

2. In the deployment wizard ![alt text](arm.png):  
   a. Select the resource group containing Sentinel.  
   b. Choose the region of the Sentinel Log Analytics workspace (e.g., East US in the example).  
   c. Enter the name of the Sentinel Log Analytics workspace (e.g., alz-law).

3. Click the **Review + create** button and deploy.

4. In Sentinel, click **Data Connectors**, find the connector named **Google Workspace Activities (using REST API) (Preview)**, and then click **Open connector page** ![alt text](connector.png).

5. In the connector page, fill in the OAuth client ID and secret in the text box ![alt text](gw14.png). Then click **Connect**. You will be redirected to the Google login page in a pop-up window. Select the Google Admin account you used and log in ![alt text](gw15.png). Review the permissions and allow access.

6. If configured correctly, you should see the connector resource provisioned. After some time, you will see data received ![alt text](gw16.png).

7. you can also search data in log analytics table **GoogleWorkspaceReports_CL** as below![alt text](gw17.png)
