# mlops-bootcamp-workflow-github-actions-dockerhub

CI: Continuous development of a flask app, including Unit Tests. Then, we build and test. This continues with a creation of a Docker Image. Then we deploy (CD).

Dockerhub is a repository for the Docker image that anyone can pull and run in their local. Requires secret keys (docker usename and docker password/token).

Tools used: Git, GitHub, Docker, Pytest, Flaks.

To obtain docker secrets that are required:
- Go to docker.com
- Login
- password requires token. Account settings: personal access token -> generate -> Read,write,delete
- go to repo in github -> secrets and variables -> actions -> create secret keys


After everything is done, to test: docker pull munozgonzalez4/flasktest-app
Then: docker run -p 5000:5000 munozgonzalez4/flasktest-app:latest
This will run in the container!!!