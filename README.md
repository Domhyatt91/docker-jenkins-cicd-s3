# 🚀 Dockerized Jenkins CI/CD + DevSecOps Pipeline for AWS S3

## 📌 Project Overview

This project demonstrates an end-to-end CI/CD and DevSecOps workflow using Docker, Jenkins, GitHub, Trivy, AWS CLI, AWS IAM, and Amazon S3.

Jenkins runs inside a custom Docker container and automatically retrieves website source code from GitHub. Before deployment, Trivy performs automated security scanning for vulnerabilities and exposed secrets. If the security gate passes, Jenkins deploys the website to Amazon S3.

The project demonstrates how security can be integrated directly into a CI/CD pipeline rather than treated as a separate manual step.

---

## 🏗️ Architecture

```text
                    Developer
                        │
                        ▼
                  GitHub Repository
                        │
                        ▼
              ┌─────────────────────┐
              │       Jenkins       │
              │   Docker Container  │
              └──────────┬──────────┘
                         │
                         ▼
                 🔐 Trivy Security Scan
                  Vulnerability + Secret
                         │
                    Security Gate
                         │
                         ▼
                    AWS CLI + IAM
                         │
                         ▼
                    Amazon S3
                         │
                         ▼
                    Live Website