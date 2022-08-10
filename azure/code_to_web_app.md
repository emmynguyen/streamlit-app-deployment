# Deployment Option 3: Cloud Provider (Azure)

## Azure Deployment Option #2: Code Deployment to Azure App Service (Web App)
### Prerequisites
1. Have an Azure subscription.
2. Have a GitHub repository.
3. Connect GitHub repository to Azure.
4. Requires a runtime stack (Python 3.7-3.9) with Linux as the OS.
5. Requires an App Service Plan with a tier of B1 or higher.

### Walkthrough
#### Azure Setup
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
9. In the "Settings" tab, select "GitHub" as your code source.
10. Then, fill in the following information:
    - Organization
    - Repository
    - Branch
11. Then, click on the "Save" button to save the change.
12. Once the deployment has been set up, the "Settings" tab should now show the following:
    - Source: GitHub
    - Signed in as: user
    - Organization: org
    - Repository: repo
    - Branch: branch
    - Build Provider: GitHub Actions
    - Runtime stack: Python
    - Version: Python 3.8
13. Once the Azure setup has been completed, continue to GitHub.

#### GitHub 
1. Navigate to the GitHub repository you are trying to deploy.
2. Depending on the branch you selected for deployment (typically main), select the appropriate branch.
3. For that branch, you should see that there is a recent commit where a GitHub Action workflow (.yml) was added.
4. Every GitHub repository has a set of tabs that users and developers can navigate between.
5. Click on the "Actions" tab of your GitHub repository.
6. Once you have been redirected to the "Actions" tab, you should be able to see all the GitHub Action workflows for your repository.
7. The most recent commit created the following workflow:
```
Add or update the Azure App Service build and deployment workflow config 
```
8. Since Azure created the GitHub Action workflow and committed it to your repository, this should have kicked off the GitHub Action workflow.
    - The GitHub Action workflow will work through two phases of deployment: build and deploy.
    - On GitHub, the initial run does not allow you to enable logs, but subsequent runs may prompt you to enable logs for your reference.
9. Once the GitHub Action workflow has finished, continue to part 2 of the Azure setup.
    - If the GitHub Action workflow is successful, then both phases will complete and the "deploy" phase will display the Azure App Service (Web App) URL to navigate to.
    - If the GitHub Action workflow is unsuccessful, then rerun the GitHub Action workflow and be sure to enable logs so you can troubleshoot issues/errors.

#### Azure Setup - Part 2
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
9. Once the Azure App Service (Web App) has finished refreshing itself, click on the URL: https://<web_app_name>.azurewebsites.net
10. If you were able to complete all of the steps without running into any errors, then you should be able to view your streamlit application and interact with it as intended.