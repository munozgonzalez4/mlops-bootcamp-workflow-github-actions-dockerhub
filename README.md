# MLOps Bootcamp: GitHub Actions + Docker Hub Workflow

This repository is a small educational example of a CI/CD pipeline for a Flask app.

The goal is to show how a project can:
- run automated tests in CI
- build a Docker image
- push it to Docker Hub
- make it available for others to pull and run

---

## What this project demonstrates

This is a simple Flask app that is tested with Pytest and packaged into a Docker container.

The general flow is:

1. Code is pushed to GitHub
2. GitHub Actions runs the test pipeline
3. The app is containerized with Docker
4. The image is pushed to Docker Hub
5. Anyone can pull and run that image locally

This is a basic example of the difference between:
- CI: Continuous Integration (test, validate, build)
- CD: Continuous Delivery/Deployment (publish and distribute the app)

---

## Project summary

This repo includes:
- a Flask application
- automated tests
- a Dockerfile for building the app image
- a GitHub Actions workflow for CI/CD
- Docker Hub integration using secrets

Tools used:
- Git
- GitHub
- Docker
- Docker Hub
- Pytest
- Flask
- GitHub Actions

---

## Repository structure

```text
.
├── app.py
├── DockerFile
├── requirements.txt
├── test_app.py
├── README.md
└── .github/workflows/cicd.yml
```

Notes:
- `app.py` contains the Flask app
- `test_app.py` contains the unit test
- `DockerFile` is used to build the container image
- `.github/workflows/cicd.yml` defines the automation pipeline

---

## How the CI/CD workflow works

The GitHub Actions workflow does the following:

### CI part
- checks out the code
- sets up Python
- installs dependencies
- runs `pytest`

### Docker part
- builds a Docker image from the project
- logs into Docker Hub
- pushes the image to Docker Hub

### CD part
- publishes the image so it can be pulled and run elsewhere

---

## Why Docker Hub is involved

Docker Hub is a repository for Docker images. After building an image, you can publish it so other people or machines can pull it and run it without needing the source code.

This repo requires Docker credentials:
- Docker username
- Docker password or personal access token

---

## How to create the required Docker secrets

To obtain Docker secrets that are required:

- Go to Docker Hub
- Log in to your account
- Create a personal access token in your Docker account settings
- In GitHub, go to the repository
- Open: `Settings` -> `Secrets and variables` -> `Actions`
- Create the secret keys for Docker username and Docker password/token

Important note from the original project notes:
- Docker password requires a token
- Account settings: `Personal access token` -> generate -> `Read, write, delete`

---

## Run the app locally with Docker

After everything is done, you can test the published image like this:

```bash
docker pull munozgonzalez4/flasktest-app
```

Then run:

```bash
docker run -p 5000:5000 munozgonzalez4/flasktest-app:latest
```

This will run the application inside the container.

The app is exposed on port `5000`, so you can open it in a browser at:

```text
http://localhost:5000
```

---

## What this project is teaching

This repo is intentionally small, but it demonstrates real-world MLOps patterns:
- automatic validation of code
- building software artifacts
- packaging an app in a container
- publishing a reusable image
- using GitHub Actions with external services like Docker Hub

This is a great beginner project for understanding the full idea of automating software delivery.

---

## Quick learning notes

- CI means verifying that the code is healthy before release
- CD means delivering the built artifact to a target environment or registry
- Docker images package the app and its dependencies into a portable unit
- Docker Hub acts as a public or private registry for those images
- GitHub Actions automates the process when code is pushed

---

## Final note

This project is meant as an educational example, so the main value is understanding the flow and the concepts, not only the final result.

The original notes are preserved here so the learning context is kept intact.