# Deployment Option 3: Cloud Provider (Azure)

## Azure Deployment Option #1: local git

### Prerequisites
1. Have an Azure subscription.
2. Requires a runtime stack (Python 3.7-3.9) with Linux as the OS.
3. Requires an App Service Plan with a tier of B1 or higher.

### Azure Setup - Part 1
1. Open a browser and navigate to the following URL: portal.azure.com
2. In the Azure Portal, click on the "+ Create a Resource".
3. Looking at the list of popular Azure services, navigate to "Web App" (should be at the bottom of the list) and click on "Create".
4. Once you are redirected to the "Create Web App" page, please fill in the required information:
    - Subscription
    - Resource Group
    - Web App Name
    - Publish - choose the "Code" option
    - Runtime Stack - choose the "Python 3.8" option
    - Operating System - this should default to Linux
    - Region
    - App Service Plan - choose the option that is in line with your app (recommendation: tier of B1 or higher)
5. Once you have filled in the required information, review and create the Azure App Service (Web App).
6. After the Web App deployment has completed, navigate to the Azure App Service (Web App).
7. On the Azure App Service (Web App) page, navigate to the "Deployment" section and click on the "Deployment Center" option.
8. On the "Deployment Center" page, there should be a "Settings" tab.
9. In the "Settings" tab, select the "Local Git" as your code source.
10. Then, click on the "Save" button to save the change.
11. Once the deployment has been set up, the "Settings" tab should now show the following:
    - Source: Local Git
    - Git Clone Uri: <Uri>
    - Build provider: App Service Build Service
    - Runtime stack: Python
    - Version: Python 3.8
12. Once the Azure setup has been completed, continue to the local git setup.

### Local Git Setup
1. Have a local Git repository with code you want to deploy.
2. In the local Git repository, run the following command:
```
git clone <Git_Clone_Uri>
```
3. To track files in the local Git repository, run the following command:
```
git add .
```
4. To add files to your local Git repository, run the following command:
```
git commit -m "<commit_message>"
```
5. To add a Git remote using the Git Clone Uri, run the following command:
```
git remote add azure <Git_Clone_Uri>
```
6. To To push to the Azure remote, run the following command:
```
git push azure master
```
7. Once the deployment has succeeded, continue to part 2 of the Azure setup.

### Azure Setup - Part 2
1. Return to the webpage of the Azure App Service (Web App) you created.
2. Navigate to the "Settings" section of the Azure App Service (Web App).
3. Click on the "Configuration" tab that resides within the "Settings" section.
4. Click on the "General Settings" tab within the "Configuration" page.
5. For the Startup Command, type in the following command: <br />
- If using python:
```
python -m streamlit run app.py --server.port 8000 --server.address 0.0.0.0
```
- If using python3:
```
python3 -m streamlit run app.py --server.port 8000 --server.address 0.0.0.0
```
6. Click on the "Save" button to save the change.
7. Then, navigate to the "Overview" tab of your Azure App Service (Web App).
8. Click on the "Refresh" button.
9. Once your Azure App Service (Web App) has finished refreshing itself, click on the URL: https://<web_app_name>.azurewebsites.net
10. If you were able to complete all of the steps without running into any errors, then you should be able to view your streamlit application and interact with it as intended.

### References
[Local Git deployment to Azure App Service](https://docs.microsoft.com/en-us/azure/app-service/deploy-local-git?tabs=cli)