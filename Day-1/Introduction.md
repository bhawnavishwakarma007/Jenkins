# Day 1 – CI/CD (Continuous Integration & Continuous Deployment)

---
## What is CI/CD?

CI/CD is a DevOps practice that automates:

- Code integration
- Testing
- Quality checks
- Deployment

It helps deliver applications faster, safer, and more reliably.

---

## CI – Continuous Integration
### Definition

Continuous Integration is the process where developers frequently push code to a shared repository, and the code is automatically built and tested.

---
### CI Flow

Developer Code
     ↓
GitHub (Source Code)
     ↓
Build
     ↓
Testing
     ↓
Code Quality Check

---
### Build Stage

- Creates the final package

- Adds all required dependencies & libraries

**Package includes:**

- Source code
- Dependencies
- Libraries
- Executable format
---
### Testing Stage

- Verifies code functionality
- Detects bugs early
- Ensures new code doesn't break existing features
---
### Code Quality Stage

Checks:

- Code standards

- Code smells

- Vulnerabilities
---
**Tools example:** SonarQube

---
## CD – Continuous Deployment / Delivery
### Definition
CD automatically deploys the tested and approved code to servers or environments.

---
### CD Flow

CI Output (Artifact)
     ↓
Artifact Storage
     ↓
Deployment
     ↓
Application Live

---
### Artifact Tools

- Amazon S3
- JFrog
- Nexus
---

## CI/CD Tools

### Commonly used tools:

- Jenkins
- GitHub Actions
- GitLab CI/CD
- Azure DevOps
---

## Jenkins (Important for DevOps)

---
## What is Jenkins?

Jenkins is an open-source CI/CD automation server used to build, test, and deploy applications.

## Key Jenkins Details

---
- **Default Port:** 8080

- **Default Workspace:** `/var/lib/jenkins`

## Minimum System Requirements

---
- **RAM:** 2 GB

- **CPU:** 2 CPUs

## Important Jenkins Plugins

- **Pipeline**
- **Stage View** (Used to visualize CI/CD pipelines)

## Pipeline Concept

---
**Pipeline-1 (CI)**
GitHub → Build → Testing → Code Quality

**Pipeline-2 (CD)**
Artifact → Deployment → Application

## Why CI/CD is Important?

---
- Faster releases 🚀

- Early bug detection 🐞

- Automation reduces manual errors

- Improves developer productivity

- Industry-standard DevOps practice

## One-Line Interview Answer

---

"CI/CD automates the process of integrating code, testing it, checking quality, and deploying it to production reliably and quickly."