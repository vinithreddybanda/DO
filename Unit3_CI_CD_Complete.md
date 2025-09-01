# Unit 3: Continuous Integration (CI) and Continuous Delivery/Deployment (CD) – Complete Guide

---

## Table of Contents
1. [What is CI/CD?](#what-is-cicd)
2. [Why Use CI/CD?](#why-use-cicd)
3. [DevOps Lifecycle & CI/CD Pipeline](#devops-lifecycle--cicd-pipeline)
4. [Technical Principles of CI/CD](#technical-principles-of-cicd)
5. [Technical Requirements for CI/CD](#technical-requirements-for-cicd)
6. [Pipeline Anatomy & YAML](#pipeline-anatomy--yaml)
7. [Common CI/CD Tools](#common-cicd-tools)
8. [Best Practices](#best-practices)
9. [Summary](#summary)

---


## 1. What is CI/CD?

**CI/CD** = **Continuous Integration** + **Continuous Delivery/Deployment**.

- **Continuous Integration (CI):** Every time you push code (or open a PR), an automated system builds your project and runs tests/linters. If anything breaks, you see it immediately.
- **Continuous Delivery (CD):** After CI passes, the system packages your app (artifact), and prepares it for deployment to environments (dev/staging/prod). A human may approve the final step.
- **Continuous Deployment:** Like Delivery, but the final release to production is automatic (no manual button).

**Simple analogies:**
- CI: Like a chef checking every ingredient as soon as it arrives, so problems are caught early.
- CD: Like a factory line that always has a finished product ready to ship at a moment’s notice.
- Continuous Deployment: The product is shipped to customers automatically as soon as it’s ready.

---


---

## 2. Why Use CI/CD?

- **Faster feedback:** Find bugs minutes after coding, not weeks later.
- **Stable main branch:** Only code that passes checks gets merged.
- **Repeatable, reliable:** No “works on my machine” — builds run in clean, identical machines.
- **Release anytime:** Build once → promote to environments safely.
- **Team velocity:** Parallel work with confidence.

---

## 3. DevOps Lifecycle & CI/CD Pipeline

DevOps defines an agile relationship between operations and development. The DevOps lifecycle includes these 7 phases:

1. **Continuous Development:** Planning and coding. Developers write code and commit frequently.
2. **Continuous Integration:** Developers merge code often. Every commit triggers automated builds and tests. (Jenkins, GitHub Actions)
3. **Continuous Testing:** Automated tests (unit, integration, E2E) run to catch bugs early. (Selenium, JUnit, TestNG)
4. **Continuous Monitoring:** Track application health, logs, and errors. (Prometheus, ELK)
5. **Continuous Feedback:** Analyze results, gather feedback, and improve the next version.
6. **Continuous Deployment:** Code is automatically deployed to production/staging. (Ansible, Docker, Kubernetes)
7. **Continuous Operations:** Fully automated release and operations, enabling rapid time to market.

**7 phases of a modern pipeline:**
Plan → Code → Build → Test → Release → Deploy → Operate/Monitor

**Simple rule:** Build once, promote (don’t rebuild for each environment).

---


---

## 4. Technical Principles of CI/CD

| Principle                | Simple Explanation |
|--------------------------|-------------------|
| Automate Everything      | Avoid manual steps; automate build, test, deploy. |
| Build Once               | Build code once, use same artifact everywhere. |
| Commit Frequently        | Small, regular code changes. |
| Test Early & Often       | Run tests at every stage, catch bugs ASAP. |
| Fail Fast                | Stop pipeline on failure, fix issues immediately. |
| Keep Builds Fast         | Optimize for quick feedback. |
| Secure the Pipeline      | Integrate security checks and protect secrets. |
| Monitor & Measure        | Track pipeline health, detect bottlenecks. |

---

## 5. Technical Requirements for CI/CD

| Requirement                | Description |
|----------------------------|-------------|
| Version Control System     | e.g., Git. Single source for code, configs, scripts. |
| CI/CD Toolchain            | Orchestrates pipeline (Jenkins, GitHub Actions, GitLab CI). |
| Build Tools                | Compile/package code (Maven, Gradle, npm). |
| Automated Testing Frameworks| Unit, integration, E2E tests (JUnit, Selenium, pytest). |
| Artifact Repository        | Stores build outputs (Nexus, JFrog, DockerHub). |
| Infrastructure as Code     | Manage infra as code (Terraform, Ansible). |
| Containerization           | Package apps in containers (Docker, Kubernetes). |
| Logging & Monitoring       | Track logs, errors, metrics (ELK, Prometheus). |
| Secret Management          | Secure API keys/passwords (Vault, K8s Secrets). |
| Environments               | Dev, staging, prod with config separation. |

**Package Managers in CI/CD:**
Handle dependencies (npm, pip, maven, nuget). Lockfiles ensure consistent builds.

---

## 6. Pipeline Anatomy & YAML

**What a pipeline is made of:**
- **Trigger:** When to run (on push, PR, tag, cron, manual click).
- **Runner/Agent:** The machine that executes steps (e.g., GitHub-hosted VM, Jenkins agent).
- **Jobs:** Logical units (build, test, deploy). Jobs can run in parallel.
- **Stages:** Groups of jobs in order (e.g., Build → Test → Deploy).
- **Steps:** The individual commands (checkout, install deps, run tests).
- **Artifacts:** Outputs you keep (build bundles, reports).
- **Cache:** Speeds repeated installs (npm/pip/maven caches).
- **Environments:** dev/staging/prod with different variables.
- **Secrets:** API keys, tokens — stored securely by the CI/CD tool (never in git).
- **Approvals:** Manual gates before risky steps (e.g., deploy to prod).

**YAML — the pipeline language:**
Pipelines are defined as YAML files in your repo. Example (GitHub Actions):
```yaml
name: CI
on: [push, pull_request]
jobs:
	build:
		runs-on: ubuntu-latest
		steps:
			- uses: actions/checkout@v4
			- run: echo "Hello from CI"
```
Use spaces for indentation (no tabs), keep indentation consistent.

---

---


## 7. Common CI/CD Tools

- **Jenkins:** Open-source automation server for building pipelines.
- **GitHub Actions:** CI/CD built into GitHub repositories.
- **GitLab CI/CD:** Integrated with GitLab for end-to-end automation.
- **CircleCI:** Cloud-based CI/CD platform.
- **Travis CI:** Popular for open-source projects.
- **Azure DevOps Pipelines:** Microsoft’s CI/CD solution.
- **Bamboo:** Atlassian’s CI/CD tool.
- **ArgoCD, Spinnaker:** For Kubernetes and cloud-native deployments.

---


## 8. Best Practices

- Commit code frequently and keep changes small.
- Write and maintain automated tests.
- Fix build and test failures immediately.
- Use feature branches and pull requests for code review.
- Keep pipelines fast (optimize build/test time).
- Secure secrets and credentials in the pipeline.
- Monitor pipeline health and deployment outcomes.
- Document the pipeline and deployment process.

---


## 9. Summary


CI/CD is the backbone of modern DevOps, enabling teams to deliver high-quality software quickly and reliably. By automating builds, tests, and deployments, CI/CD reduces manual work, increases confidence, and accelerates innovation. Mastering CI/CD principles and tools is essential for any developer or DevOps engineer.

---

For more, see the [CI/CD section of the Atlassian Guide](https://www.atlassian.com/continuous-delivery/principles/continuous-integration-vs-delivery-vs-deployment) and [Jenkins Documentation](https://www.jenkins.io/doc/).
