# Deployment Option 3: Cloud Provider (Azure)
**Context:** This setup can be done either through leveraging Azure CLI or Azure Portal's GUI. Since Azure Portal's GUI leverages GitHub Actions, this example focuses on the Azure CLI route.

## Azure Deployment Option #3: Azure Container Registry to Azure App Service (Web App)

### Prerequisites
1. Have an Azure subscription.
2. Have a GitHub repository.
3. Connect GitHub repository to Azure.
4. Install [Docker Desktop](https://docs.docker.com/get-docker/).
5. Install [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli).
6. Requires a runtime stack (Python 3.7-3.9) with Linux as the OS.
7. Requires an App Service Plan with a tier of B1 or higher.

### Walkthrough

#### Visual Studio Code Setup
1. Open up your GitHub repository in Visual Studio Code.
2. In your repository's root directory, create and save a requirements.txt. This file will handle package dependency installation and management.
3. In your repository's root directory, create and save a Dockerfile. This Dockerfile will handle installation and setup for the Docker container.
4. In Visual Studio Code, click on the "Terminal" menu option and then select "New Terminal". <br />
- For Linux:
```
source ./venv/bin/activate
```
- For Windows: 
```
venv\Scripts\activate
```
5. In terminal, check that you have Docker CLI and Azure CLI installed. <br />
- Docker CLI
```
docker --version
```
- Azure CLI
```
az --version
```
6. If Docker CLI and Azure CLI are already installed, let's continue. Else, install Docker CLI and Azure CLI.

#### Dockerize the Streamlit App
1. In terminal, run the following command to build the docker container and docker image:
```
docker build -t <name>:<version> .
```
2. If step 7 was successful, run the following command to start the docker container and launch the docker image:
```
docker run --rm -p 8880:8501 <name>:<version>
```
3. If step 8 was successful, then open a new browser window and type the following URL into the address bar:
```
localhost:8880
```
4. If you were able to complete all of the steps without running into any errors, then you should be able to view your streamlit application and interact with it as intended.
    - **Important:** Be sure to stop your container when you are done.

#### Azure Setup - Part 1
**Context:** You can choose to either use Azure CLI via the Azure Portal or Visual Studio Code's Terminal. This setup will leverage Visual Studio Code's Terminal for Azure CLI work.
1. Continue using the terminal in Visual Studio Code.
2. Log into Azure via Azure CLI by running the following command:
```
az login
```
3. Create an Azure Container Registry by running the following command:
```
az acr create --name <container_registry_name> --resource-group <resource_group> --sku basic --admin-enabled true
```
4. Build the docker image and save it to Azure Container Registry by running the following command:
```
az acr build --registry <container_registry_name> --resource-group <resource_group> --image <image_name> .
```
5. Create an App Service plan by running the following command:
```
az appservice plan create -g <resource_group> -n <app_service_plan> -l <location> --is-linux --sku B1
```
6. Create the Azure App Service (Web App) by running the following command:
```
az webapp create -g <resource_group> -p <app_service_plan> -n <web_app_name> -i <container_registry_name>.azurecr.io/<docker_image_name>:latest
```
7. If you navigate to the Azure Portal and to the resource group you have used to create various Azure services, you should now see 3 resources: app service, container registry, and app service plan.

**Redeployment:** To make changes and deploy the streamlit app to an existing container, run the following command:
```
az acr build --registry <container_registry_name> --resource-group <resource_group> --image <docker_image_name> .
```

#### Azure Setup - Part 2
1. Navigate to the Azure Portal, specifically to the Azure App Service (Web App) that was just created.
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

### References
[Dockerfile Best Practices](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
[docker image build](https://docs.docker.com/engine/reference/commandline/image_build/)
[docker run](https://docs.docker.com/engine/reference/commandline/run/)
[Deploy a Streamlit Web App with Azure App Service](https://towardsdatascience.com/deploying-a-streamlit-web-app-with-azure-app-service-1f09a2159743)
[Beginner Guide to Streamlit Deployment on Azure](https://towardsdatascience.com/beginner-guide-to-streamlit-deployment-on-azure-f6618eee1ba9)