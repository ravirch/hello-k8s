# hello-k8s

A demo of a Python web application built end-to-end: local development → CI/CD pipeline → deployment on Minikube.

## What this covers

1. A simple Python app (Flask/FastAPI)
2. Docker containerization
3. GitHub Actions CI/CD (lint, test, build & push image)
4. Kubernetes manifests for Minikube deployment

## Prerequisites

- Python 3.11+
- Docker
- [Minikube](https://minikube.sigs.k8s.io/docs/start/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/)

## Run locally

```bash
python -m venv .venv
source .venv/bin/activate   # Windows: .venv\Scripts\activate
pip install -r requirements.txt
python app.py
```

App will be available at `http://localhost:5000`.

## Run with Docker

```bash
docker build -t hello-k8s .
docker run -p 5000:5000 hello-k8s
```

## Deploy to Minikube

```bash
minikube start
kubectl apply -f k8s/
minikube service hello-k8s
```

## CI/CD

GitHub Actions runs on every push:

- Lint & test the Python code
- Build the Docker image
- Push image to a container registry

See [.github/workflows/](.github/workflows/) for the pipeline definition.