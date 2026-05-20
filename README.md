# ML Sentiment App — CI/CD Starter Project

![Python](https://img.shields.io/badge/Python-3.11-blue)
![FastAPI](https://img.shields.io/badge/FastAPI-API-green)
![Docker](https://img.shields.io/badge/Docker-Containerization-blue)
![CI](https://img.shields.io/badge/CI-Passing-brightgreen)

A lightweight NLP microservice for sentiment analysis built with FastAPI and TextBlob.

This project demonstrates modern software engineering and DevOps practices including:

- REST API development with FastAPI
- Automated testing with Pytest
- Static code analysis with Ruff
- Type checking using MyPy
- Docker containerization
- CI/CD pipeline integration
- SBOM generation using SPDX

---

# Features
- Sentiment analysis API
- Health check endpoint
- Automated testing
- Linting and formatting checks
- Type safety validation
- Docker image build and push
- Continuous Integration pipeline
- SPDX SBOM artifact generation

---

# Tech Stack
- Python 3.11
- FastAPI
- TextBlob
- Pytest
- Ruff
- MyPy
- Docker
- Gitea Actions / GitHub Actions

---

# Project Structure
```text
ml-sentiment-app/
│
├── src/
│   └── inference.py
│
├── tests/
│   └── test_api.py
│
├── Dockerfile
├── requirements.txt
├── README.md
└── .github/workflows/
```

---

# Quick Start
## 1. Clone Repository
```bash
git clone https://github.com/manarelabsi10/ml-sentiment-app-cicd-.git
cd ml-sentiment-app-cicd-
```

---

## 2. Create Virtual Environment
### Windows
```bash
python -m venv .venv
.venv\Scripts\activate
```

### Linux / macOS
```bash
python -m venv .venv
source .venv/bin/activate
```

---

## 3. Install Dependencies
```bash
pip install -r requirements.txt
```

---

## 4. Download TextBlob Corpora
```bash
python -m textblob.download_corpora
```

---

## 5. Run the Application
```bash
uvicorn src.inference:app --reload
```

Server will start at:

```text
http://127.0.0.1:8000
```

---

# API Documentation
FastAPI automatically generates Swagger documentation.

Available at:

```text
http://127.0.0.1:8000/docs
```

---

# API Endpoints
## Health Check
```http
GET /health
```

### Response
```json
{
  "status": "ok"
}
```

---

## Sentiment Prediction
```http
POST /predict
```

### Request Body
```json
{
  "text": "I love this project"
}
```

### Example Request
```bash
curl -X POST "http://127.0.0.1:8000/predict" \
-H "Content-Type: application/json" \
-d "{\"text\":\"I love this project\"}"
```

### Example Response
```json
{
  "sentiment": "positive",
  "polarity": 0.5
}
```

---

# Running Tests
Run unit tests using:

```bash
pytest
```

---

# Code Quality Checks
## Ruff Linting
```bash
ruff check src/ tests/
```

## MyPy Type Checking
```bash
mypy src/
```

---

# Docker
## Build Docker Image

```bash
docker build -t ml-sentiment-app .
```

## Run Docker Container
```bash
docker run -p 8000:8000 ml-sentiment-app
```

---

# CI/CD Pipeline
The CI pipeline runs automatically on every push and pull request to the `main` branch.

## Pipeline Jobs

### 1. Lint
Runs Ruff static analysis on:

- `src/`
- `tests/`

---

### 2. Type Check
Runs MyPy type checking on:

- `src/`

---

### 3. Test
Runs:
- Pytest
- Coverage reporting

---

### 4. Build and Push
- Builds Docker image
- Pushes image to container registry

---

### 5. SBOM Generation
Generates SPDX SBOM artifact for software supply chain security.

---

# Container Registry
Docker images are pushed to:

```text
cisc814-registry:5000/ml-sentiment-app
```

---

# Future Improvements
- Add model persistence
- Add database integration
- Add authentication
- Deploy to Kubernetes
- Add monitoring and logging
- Add ML model versioning


