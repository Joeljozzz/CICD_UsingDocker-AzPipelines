# 🚀 CI/CD with Docker & Azure Pipelines

[![Python](https://img.shields.io/badge/Python-3.9-3776AB?style=flat&logo=python&logoColor=white)](https://www.python.org/)
[![Flask](https://img.shields.io/badge/Flask-2.0%2B-000000?style=flat&logo=flask&logoColor=white)](https://flask.palletsprojects.com/)
[![Docker](https://img.shields.io/badge/Docker-Container-2496ED?style=flat&logo=docker&logoColor=white)](https://www.docker.com/)
[![Azure Pipelines](https://img.shields.io/badge/Azure%20Pipelines-CI%2FCD-2560E0?style=flat&logo=azure-pipelines&logoColor=white)](https://azure.microsoft.com/services/devops/pipelines/)
[![Azure App Service](https://img.shields.io/badge/Azure%20App%20Service-Web%20App-0078D4?style=flat&logo=microsoft-azure&logoColor=white)](https://azure.microsoft.com/services/app-service/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

An automated continuous integration and continuous deployment (CI/CD) pipeline built with Azure DevOps and Docker. It packages a Python Flask web application into a container image, pushes it to Azure Container Registry (ACR), and continuously deploys it to Azure App Service (Web App for Containers).

---

## 🌟 Key Features

- **Automated CI/CD Pipeline**: Triggers automatically on code pushes to the `main` branch.
- **Docker Containerization**: Portable, lightweight packaging using `python:3.9-slim`.
- **Azure Container Registry (ACR) Integration**: Automated image build and versioned push tagged with build IDs.
- **Continuous Deployment**: Deploys updated container images directly to Azure App Service for Linux containers.
- **Cloud-Ready Web App**: Simple and scalable Flask application boilerplate.

---

## 📁 Project Structure

```text
CICD_UsingDocker-AzPipelines/
├── app.py                # Flask application entry point
├── Dockerfile            # Container build instructions
├── requirements.txt      # Python dependencies
├── azure-pipelines.yml   # Azure DevOps CI/CD pipeline definition
├── LICENSE               # MIT License
└── README.md             # Project documentation
```

---

## 🛠️ Getting Started

### Prerequisites

- [Python 3.9+](https://www.python.org/downloads/)
- [Docker](https://www.docker.com/get-started)
- [Azure DevOps Account](https://dev.azure.com/) with Azure subscription access

### Local Development

1. **Clone the repository:**
   ```bash
   git clone https://github.com/joeljose/CICD_UsingDocker-AzPipelines.git
   cd CICD_UsingDocker-AzPipelines
   ```

2. **Create and activate a virtual environment:**
   ```bash
   python -m venv .venv
   # On Windows:
   .venv\Scripts\activate
   # On macOS/Linux:
   source .venv/bin/activate
   ```

3. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Run the application:**
   ```bash
   python app.py
   ```
   Access the app at `http://localhost:5000`.

---

## 🐳 Running with Docker

1. **Build the Docker image:**
   ```bash
   docker build -t flask-cicd-app:latest .
   ```

2. **Run the container:**
   ```bash
   docker run -d -p 5000:5000 --name flask-cicd-app flask-cicd-app:latest
   ```

3. **Verify:**
   Open `http://localhost:5000` in your browser.

4. **Stop the container:**
   ```bash
   docker stop flask-cicd-app
   docker rm flask-cicd-app
   ```

---

## ☁️ Azure Pipeline Setup

1. **Configure Azure Resources:**
   - Create an **Azure Container Registry (ACR)** (e.g., `containeregdemo.azurecr.io`).
   - Create an **Azure App Service** instance configured for Linux Web App containers (e.g., `demodocker`).

2. **Set Up Azure DevOps Service Connections:**
   - Establish a **Docker Registry** service connection pointing to your ACR.
   - Establish an **Azure Resource Manager (ARM)** service connection pointing to your Azure subscription.

3. **Update Pipeline Configuration:**
   Update the placeholders in `azure-pipelines.yml`:
   ```yaml
   variables:
     dockerRegistryServiceConnection: '<your-acr-service-connection>'
     imageRepository: '<your-image-name>'
     containerRegistry: '<your-acr-login-server>'
   ```

4. **Run the Pipeline:**
   Commit and push your changes to `main` to trigger the automated build, push, and deployment workflow.

---

## 📄 License

This project is licensed under the [MIT License](LICENSE) - see the LICENSE file for details.
