# Streamlit App Deployment
**Context:** Streamlit application deployment consists of several options: localhost, Streamlit Community Cloud, and cloud providers like AWS, Azure, and GCP. Official Streamlit documentation provides in-depth guidance on how to deploy a Streamlit application with Streamlit Community Cloud, but lacks in-depth guidance on how to deploy with other cloud providers. This repository was created to consolidate deployment methods and bridge knowledge gaps.

## Deployment Options
1. localhost
2. Docker Image
3. Streamlit Community Cloud
4. Cloud (i.e. AWS, Azure, GCP)

## Option #1: localhost
**Reference:** [Get Started](https://docs.streamlit.io/library/get-started/main-concepts) <br />
**Walkthrough:** [localhost deployment](https://github.com/thedatarubicon/streamlit-app-deployment/blob/main/localhost/localhost_deployment.md)

## Option #2: Docker Image
**Reference:** [Dockerfile Best Practices](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/) <br />
**Walkthrough:** [Docker Container + Image to localhost](https://github.com/thedatarubicon/streamlit-app-deployment/blob/main/docker/docker.md)

## Option #3: Streamlit Community Cloud
**Reference:** [Streamlit Cloud](https://docs.streamlit.io/streamlit-cloud) <br />
**Walkthrough:** [Deploy an App](https://docs.streamlit.io/streamlit-cloud/get-started/deploy-an-app)

## Option #4: Cloud Provider
**Reference:** [Streamlit Deployment Guide Wiki](https://discuss.streamlit.io/t/streamlit-deployment-guide-wiki/5099) <br />

### Azure Deployment Options
**Option 1:** Deploy code from a local Git repository to an Azure App Service (Web App) <br />
**Walkthrough:** [Local Git Deployment](https://github.com/thedatarubicon/streamlit-app-deployment/blob/main/azure/localgit_to_web_app.md)

**Option 2:** Deploy code from an existing GitHub repository to an Azure App Service (Web App) <br />
**Walkthrough:** [Code Deployment to Azure App Service](https://github.com/thedatarubicon/streamlit-app-deployment/blob/main/azure/code_to_web_app.md)

**Option 3:** Deploy a Docker Image from Azure Container Registry to an Azure App Service (Web App) <br />
**Walkthrough:** [Container Deployment to Azure App Service](https://github.com/thedatarubicon/streamlit-app-deployment/blob/main/azure/container_to_web_app.md)

**Option 4:** Deploy a Docker Image from Azure Container Registry to an Azure Container Instance (Serverless App) <br />
**Walkthrough:**

### AWS Deployment Options

### GCP Deployment Options