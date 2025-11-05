# 🚀 GitHub Actions — CI/CD & Automation Learning

This repository contains my complete learning journey and hands-on practice with **GitHub Actions**, covering all types of actions and real-world CI/CD workflows used in production.

---

## 🧠 What I Learned

### ⚙️ Core Concepts
- Workflow syntax (`.github/workflows/`)
- Jobs, steps, runners (GitHub-hosted & self-hosted)
- Workflow triggers (`push`, `pull_request`, `schedule`, `workflow_dispatch`)
- Environment variables, secrets, and contexts
- Environments and deployment protection rules

---

## 🧩 Types of Actions

### 1️⃣ **Prebuilt Actions (Marketplace)**
Used directly from the GitHub Marketplace.

Examples:
- `actions/checkout@v4` — Clones repository
- `actions/setup-node@v4` — Sets up Node.js environment
- `actions/cache@v4` — Caches dependencies
- `docker/build-push-action@v6` — Builds and pushes Docker images
- `aquasecurity/trivy-action@master` — Security scanning

---

### 2️⃣ **Composite Actions**
Used to group multiple steps together into one reusable action.

Example:
```yaml
# .github/actions/run-tests/action.yml
name: "Run Tests"
description: "Composite action for installing deps and running tests"
runs:
  using: "composite"
  steps:
    - run: npm install
    - run: npm test


3️⃣ Docker Actions

Run inside a Docker container — used when your action needs custom dependencies.

Example:
# action.yml
name: "Docker Action Example"
runs:
  using: "docker"
  image: "Dockerfile"

# Dockerfile
FROM alpine:latest
RUN apk add curl
CMD ["echo", "Hello from Docker Action"]


4️⃣ JavaScript Actions

Custom actions written in Node.js for dynamic logic and reusability.

Example:
# action.yml
name: "JavaScript Action Example"
runs:
  using: "node20"
  main: "index.js"

// index.js
console.log("Hello from JavaScript Action!");


🔁 CI/CD in Production Setup
🧩 CI (Continuous Integration)

Linting & Unit Testing

Dependency Scanning (Trivy)

Code Quality (SonarQube)

Build & Push Docker Images

🧩 CD (Continuous Deployment)

Kubernetes manifests stored in repo

ArgoCD automatically syncs updates

Approval gates via GitHub Environments



Common Production Actions
| Purpose            | Action                                    |
| ------------------ | ----------------------------------------- |
| Checkout Code      | `actions/checkout@v4`                     |
| Setup Language     | `actions/setup-node@v4`                   |
| Cache Dependencies | `actions/cache@v4`                        |
| Run Tests          | `actions/setup-python@v5` + pytest        |
| Security Scan      | `aquasecurity/trivy-action@master`        |
| Code Quality       | `SonarSource/sonarcloud-github-action@v2` |
| Build Image        | `docker/build-push-action@v6`             |
| Deploy             | `kubectl`, `ArgoCD`, `Helm`               |
| Notify             | `slackapi/slack-github-action@v2`         |
