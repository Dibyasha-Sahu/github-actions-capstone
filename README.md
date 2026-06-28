# 🚀 GitHub Actions Capstone

A complete GitHub Actions CI/CD pipeline project built with **Python Flask**, **Docker**, and **GitHub Actions**.

The project demonstrates reusable workflows, pull request validation, Docker image build & push, deployment simulation, and scheduled health checks.

---

# 📌 Project Overview

This project contains a simple Flask application with a `/health` endpoint.

The application is:

- Containerized using Docker
- Tested automatically using GitHub Actions
- Built and pushed to Docker Hub
- Simulated deployment to a Production environment
- Monitored every 12 hours using a scheduled Health Check workflow

---

# 🛠 Tech Stack

- Python 3.12
- Flask
- Docker
- GitHub Actions
- Docker Hub

---

# 📂 Project Structure

```
github-actions-capstone/
│
├── .github/
│   └── workflows/
│       ├── reusable-build-test.yml
│       ├── reusable-docker.yml
│       ├── pr-pipeline.yml
│       ├── main-pipeline.yml
│       └── health-check.yml
│
├── app.py
├── Dockerfile
├── requirements.txt
├── test.sh
└── README.md
```

---

# 🌐 Flask Endpoint

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/health` | GET | Returns application health status |

Example Response

```json
{
    "status": "ok"
}
```

---

# 🐳 Run Locally

## Clone Repository

```bash
git clone https://github.com/Dibyasha-Sahu/github-actions-capstone.git
```

```bash
cd github-actions-capstone
```

---

## Build Docker Image

```bash
docker build -t capstone-app .
```

---

## Run Container

```bash
docker run -d -p 5000:5000 capstone-app
```

---

## Check Running Containers

```bash
docker ps
```

---

## Run Health Test

Open WSL / Git Bash

```bash
bash test.sh
```

---

## Stop Container

```bash
docker stop <container-id>
```

---

# ⚙️ GitHub Actions Workflows

## 1. Reusable Build & Test Workflow

**File**

```
.github/workflows/reusable-build-test.yml
```

### Features

- Checkout code
- Setup Python
- Install dependencies
- Run pytest
- Return test result

---

## 2. Reusable Docker Build & Push Workflow

**File**

```
.github/workflows/reusable-docker.yml
```

### Features

- Checkout repository
- Login to Docker Hub
- Build Docker Image
- Push Docker Image
- Return Docker Image URL

---

## 3. Pull Request Pipeline

**File**

```
.github/workflows/pr-pipeline.yml
```

### Trigger

- Pull Request → main

### Jobs

- Reusable Build & Test
- PR Summary Job

No Docker image is built during Pull Requests.

---

## 4. Main Branch Pipeline

**File**

```
.github/workflows/main-pipeline.yml
```

### Trigger

- Push → main

### Jobs

1. Build & Test
2. Docker Build & Push (latest)
3. Docker Build & Push (sha tag)
4. Deploy to Production Environment

---

## 5. Scheduled Health Check

**File**

```
.github/workflows/health-check.yml
```

### Trigger

- Every 12 Hours
- Manual (workflow_dispatch)

### Steps

- Login to Docker Hub
- Pull Latest Docker Image
- Start Container
- Wait 5 Seconds
- Health Check (/health)
- Stop Container
- Generate Workflow Summary

---

# 🔄 CI/CD Pipeline Architecture

```
               Pull Request
                     │
                     ▼
          Reusable Build & Test
                     │
                     ▼
            PR Checks Passed
```

```
                Push to Main
                     │
                     ▼
          Reusable Build & Test
                     │
                     ▼
      Docker Build & Push (latest)
                     │
                     ▼
      Docker Build & Push (sha-tag)
                     │
                     ▼
          Deploy to Production
```

```
           Every 12 Hours
                  │
                  ▼
        Pull Docker Image
                  │
                  ▼
         Run Health Check
                  │
                  ▼
         Generate Summary
```

---

# 📦 Docker Image Tags

The project pushes two Docker image tags:

- latest
- sha-<commit-hash>

Example

```
dibyasha27/github-actions-capstone:latest

dibyasha27/github-actions-capstone:sha-abc1234
```

---

# 📊 Workflow Badges

### Main Pipeline

[![main-pipeline](https://github.com/Dibyasha-Sahu/github-actions-capstone/actions/workflows/main-pipeline.yml/badge.svg)](https://github.com/Dibyasha-Sahu/github-actions-capstone/actions/workflows/main-pipeline.yml)

---

### PR Pipeline

[![PR Pipeline](https://github.com/Dibyasha-Sahu/github-actions-capstone/actions/workflows/pr-pipeline.yml/badge.svg?branch=test-branch)](https://github.com/Dibyasha-Sahu/github-actions-capstone/actions/workflows/pr-pipeline.yml)

---

### Health Check

[![health-check.yml](https://github.com/Dibyasha-Sahu/github-actions-capstone/actions/workflows/health-check.yml/badge.svg?branch=main)](https://github.com/Dibyasha-Sahu/github-actions-capstone/actions/workflows/health-check.yml)

---

### Reusable Docker Workflow

[![Reusable Docker Build & Push](https://github.com/Dibyasha-Sahu/github-actions-capstone/actions/workflows/reusable-docker.yml/badge.svg)](https://github.com/Dibyasha-Sahu/github-actions-capstone/actions/workflows/reusable-docker.yml)

---

### Reusable Build & Test

[![Reusable Build and Test](https://github.com/Dibyasha-Sahu/github-actions-capstone/actions/workflows/reusable-build-test.yml/badge.svg?branch=test-branch)](https://github.com/Dibyasha-Sahu/github-actions-capstone/actions/workflows/reusable-build-test.yml)

---


# 👩‍💻 Author

**Dibyasha Sahu**

GitHub:

https://github.com/Dibyasha-Sahu