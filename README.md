# 📦 FastAPI CI/CD with GitHub Actions

This repository contains a FastAPI application with a complete CI/CD pipeline using GitHub Actions, which:

- Runs tests automatically on each push or pull request to the main branch
- Builds a Docker image using the app's Dockerfile
- Pushes the image to Docker Hub if tests pass

### 🚀 Workflow Overview
The GitHub Actions workflow is located in:
```bash
.github/workflows/ci_cd.yml
```

### 🔁 Triggered on:
- Push to `main`
- Pull requests to `main`

### 🔧 Workflow Steps
1. ✅ Checkout code
2. 🐍 Set up Python 3.11
3. 📦 Install dependencies
4. 🧪 Run Pytest for unit tests
5. 🐳 Log in to Docker Hub
6. 📤 Build & push Docker image to Docker Hub
7. 🔐 Secrets Configuration

Before using the workflow, add the following secrets in your GitHub repository:

| Secret Name          | Description                              |
| -------------------- | ---------------------------------------- |
| `DOCKERHUB_USERNAME` | Your Docker Hub username                 |
| `DOCKERHUB_PASSWORD` | Your Docker Hub password or access token |


To add secrets:
- Go to your GitHub repo → Settings → Secrets → Actions → New repository secret

### 🐋 Docker Image Naming
Update the image name in ci_cd.yml to match your Docker Hub repo:
```bash
tags: umarsalman/fastapi-app:latest
```

### 🧪 Local Testing (Optional)
Run tests locally before committing:
```bash
pip install -r requirements.txt
pytest
```
Build and run Docker image locally:
```bash
docker build -t umarsalman/fastapi-app .
docker run -p 80:80 umarsalman/fastapi-app
```

### 🧼 Maintenance
- To delete Docker images: do it via Docker Hub UI or use API
- To update Python version or dependencies: edit `ci_cd.yml` or `requirements.txt`

### 📂 Project Layout
```bash
.
├── app/
│   ├── main.py          # FastAPI entrypoint
│   └── tests/
│       └── test_main.py # Unit test for FastAPI route
├── requirements.txt     # Python dependencies
├── Dockerfile           # Docker build instructions
└── .github/
    └── workflows/
        └── ci_cd.yml    # GitHub Actions workflow
```