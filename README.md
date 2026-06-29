# 🚀 GitHub Actions DevSecOps Capstone

A complete **CI/CD + DevSecOps pipeline** built using **GitHub Actions**, **Docker**, **Flask**, and **GitHub Security** features. This project demonstrates automated testing, Docker image building, vulnerability scanning, deployment simulation, and scheduled health checks.

---

## 📌 Project Overview

This project automates the complete software delivery process:

* ✅ Build & Test the application
* 🐳 Build Docker images
* 🔒 Scan Docker images using Trivy
* 📦 Push images to Docker Hub
* 🚀 Simulate deployment to Production
* ❤️ Scheduled Health Check
* 🔐 Secret Scanning & Push Protection
* 📦 Dependency Vulnerability Review

---

# 🛠️ Tech Stack

* Python 3
* Flask
* Docker
* GitHub Actions
* Docker Hub
* Trivy Security Scanner
* GitHub Secret Scanning
* Dependency Review Action

---

# 📂 Project Structure

```text
.github/
└── workflows/
    ├── reusable-build-test.yml
    ├── reusable-docker.yml
    ├── pr-pipeline.yml
    ├── main-pipeline.yml
    └── health-check.yml

Dockerfile
requirements.txt
app.py
README.md
day-49-devsecops.md
```

---

# ⚙️ GitHub Actions Workflows

### 🔹 PR Pipeline

Runs whenever a Pull Request is opened or updated.

* Build & Test
* Dependency Vulnerability Review
* PR Status Check

---

### 🔹 Main Pipeline

Runs whenever code is pushed to the **main** branch.

Workflow:

```
Build & Test
      ↓
Docker Build
      ↓
Trivy Image Scan
      ↓
Docker Push
      ↓
Deploy (Simulation)
```

---

### 🔹 Health Check

Runs:

* Every 12 hours (Cron)
* Manually using `workflow_dispatch`

Steps:

* Pull latest Docker image
* Run container
* Check `/health`
* Generate GitHub Step Summary

---

# 🔒 DevSecOps Features

## ✅ Trivy Image Scanning

Scans Docker images for:

* HIGH vulnerabilities
* CRITICAL vulnerabilities

Pipeline fails if critical vulnerabilities are detected.

---

## ✅ Dependency Review

Checks newly added dependencies in Pull Requests.

If a dependency contains a Critical vulnerability, the PR fails automatically.

---

## ✅ GitHub Secret Scanning

Automatically detects leaked secrets such as:

* API Keys
* AWS Keys
* Docker Tokens
* Passwords

---

## ✅ Push Protection

Blocks a push if GitHub detects a secret before it reaches the repository.

---

## 🔑 Workflow Permissions

Workflows follow the **Principle of Least Privilege** by using:

```yaml
permissions:
  contents: read
```

---

# ❤️ Health Endpoint

```
GET /health
```

Response

```json
{
  "status": "ok"
}
```

---

# ▶️ Run Locally

Build Docker image

```bash
docker build -t github-actions-capstone .
```

Run container

```bash
docker run -d -p 5000:5000 github-actions-capstone
```

Verify application

```
http://localhost:5000/health
```

Run health test

```bash
bash test.sh
```

---

# 📈 Complete DevSecOps Pipeline

```
Pull Request
      │
      ▼
Build & Test
      │
      ▼
Dependency Review
      │
      ▼
PR Passed

────────────────────────────

Merge to Main
      │
      ▼
Build & Test
      │
      ▼
Docker Build
      │
      ▼
Trivy Security Scan
      │
      ▼
Docker Push
      │
      ▼
Deploy (Simulation)

────────────────────────────

Every 12 Hours
      │
      ▼
Health Check

────────────────────────────

Always Active

GitHub Secret Scanning

GitHub Push Protection
```

---

# 📚 Key Learnings

* Reusable GitHub Actions Workflows
* CI/CD Pipeline Design
* Docker Image Build & Push
* Trivy Vulnerability Scanning
* Dependency Security Review
* GitHub Secret Scanning
* Push Protection
* Workflow Permissions
* Scheduled Automation
* DevSecOps Best Practices

---

# 👨‍💻 Author

**Dibyasha Sahu**

MCA (Artificial Intelligence) | DevOps & Cloud Enthusiast

GitHub: https://github.com/Dibyasha-Sahu
