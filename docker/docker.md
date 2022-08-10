# Deployment Option #2: Docker Container + Image
**Context:** This Docker setup is for localhost usage.

## Prerequisites
1. GitHub or local git repository
2. Docker Desktop
3. Install [Docker Desktop](https://docs.docker.com/get-docker/).
4. Install [Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli).

## Walkthrough 

### Visual Studio Code Setup
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

### Dockerize the Streamlit App
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

## References
[Dockerfile Best Practices](https://docs.docker.com/develop/develop-images/dockerfile_best-practices/)
[docker image build](https://docs.docker.com/engine/reference/commandline/image_build/)
[docker run](https://docs.docker.com/engine/reference/commandline/run/)