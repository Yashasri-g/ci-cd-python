# CI/CD Python Application

## Overview

This repository demonstrates a complete Continuous Integration and Continuous Deployment (CI/CD) pipeline for a simple Python application.

The project includes:

- A basic Python application
- Unit testing using `pytest`
- Automated testing with GitHub Actions
- Docker containerization
- Automated Docker image build and push to DockerHub using GitHub Secrets

This project showcases how to move from local development to an automated, production-ready CI/CD workflow.

---

## Project Structure

```

ci-cd-python/
│
├── app.py
├── test_app.py
├── requirements.txt
├── Dockerfile
└── .github/
└── workflows/
└── ci.yml

```

---

## Files Description

- **app.py** – Contains the core application logic (simple addition function).
- **test_app.py** – Unit tests written using `pytest`.
- **requirements.txt** – Project dependencies.
- **Dockerfile** – Defines the container image configuration.
- **ci.yml** – GitHub Actions workflow for CI/CD automation.

---

## Tech Stack

- Python 3.10
- Pytest
- GitHub Actions
- Docker
- DockerHub

---

## CI/CD Pipeline Workflow

The pipeline is triggered on:

- Push to `main`
- Pull requests targeting `main`

### Pipeline Stages

### 1. Test Stage
- Checkout repository
- Setup Python
- Install dependencies
- Run unit tests using `pytest`

### 2. Build Stage
- Build Docker image

### 3. Deploy Stage
- Login to DockerHub using GitHub Secrets
- Tag Docker image
- Push image to DockerHub

### Pipeline Flow

```

Push → Test → Build Docker Image → Push to DockerHub

````

Deployment only runs if all previous stages succeed.

---

## Running Locally

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/ci-cd-python.git
cd ci-cd-python
````

### 2. Create Virtual Environment

```bash
python -m venv .venv
```

Activate:

**Windows:**

```bash
.venv\Scripts\activate
```

**Mac/Linux:**

```bash
source .venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Run Tests

```bash
pytest
```

---

## Running with Docker

### Build Docker Image

```bash
docker build -t ci-cd-python .
```

### Run Container

```bash
docker run ci-cd-python
```

---

## GitHub Secrets Configuration

To enable Docker image push in CI/CD:

1. Go to Repository → **Settings** → **Secrets and variables** → **Actions**
2. Add the following secrets:

* `DOCKER_USERNAME`
* `DOCKER_PASSWORD` (or Docker access token)

These secrets are securely injected into the workflow during deployment.

---

## Key Learning Outcomes

* Writing structured YAML workflows
* Understanding CI/CD pipeline stages
* Using GitHub Actions runners
* Managing secrets securely
* Containerizing Python applications
* Automating Docker image publishing

---

## Future Improvements

* Add code coverage reporting
* Add linting (flake8)
* Add security scanning (bandit)
* Implement version tagging instead of `latest`
* Deploy container to a cloud environment (AWS, Render, etc.)

---

## Author

Developed as a hands-on project to understand end-to-end CI/CD automation using Python and Docker.
