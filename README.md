# Docker Image Tracking - CI/CD Pipeline

## Overview
This repository demonstrates a CI/CD pipeline for a Flask application using GitHub Actions and Docker. The workflow automates testing, building, and pushing a Docker image to DockerHub.

## Features
- Automated unit testing using `pytest`
- Docker image build and push using GitHub Actions
- Integration with DockerHub for easy deployment

## Project Structure
```
Docker-Image-Tracking/
│-- .github/workflows/cicd.yml   # GitHub Actions workflow file
│-- venv/                        # Virtual environment (not included in repo)
│-- .gitignore                    # Git ignore file
│-- app.py                        # Flask application
│-- Dockerfile                    # Dockerfile for building the image
│-- README.md                     # Documentation
│-- requirements.txt               # Python dependencies
│-- test_app.py                    # Unit tests for Flask app
```

## Prerequisites
Ensure you have the following installed:
- Python (3.8 or later)
- Docker
- GitHub account with Actions enabled

## Setup
1. Clone the repository:
   ```sh
   git clone https://github.com/atharvmohanjadhav/Docker-Image-Tracking.git
   cd Docker-Image-Tracking
   ```
2. Create and activate a virtual environment:
   ```sh
   python -m venv venv
   source venv/bin/activate   # For Linux/macOS
   venv\Scripts\activate      # For Windows
   ```
3. Install dependencies:
   ```sh
   pip install -r requirements.txt
   ```
4. Run the Flask application locally:
   ```sh
   python app.py
   ```

## Running Tests
To run the tests using pytest:
```sh
pytest
```

## CI/CD Workflow
The GitHub Actions workflow is defined in `.github/workflows/cicd.yml`. The pipeline consists of two jobs:
1. **Build and Test**: Runs `pytest` to check for any failing tests.
2. **Build and Publish**: After tests pass, it builds the Docker image and pushes it to DockerHub.

### Steps in Workflow:
1. Checkout the repository
2. Set up Python environment
3. Install dependencies
4. Run tests using pytest
5. Set up Docker Buildx
6. Authenticate and push the Docker image to DockerHub

## Docker Image
### Building the Docker Image
To build the Docker image locally:
```sh
docker build -t flasktest-app .
```

### Running the Docker Container
To run the container:
```sh
docker run -p 5000:5000 flasktest-app
```

### Pushing Image to DockerHub
If you want to manually push the Docker image:
```sh
docker login -u <your-dockerhub-username> -p <your-dockerhub-password>
docker tag flasktest-app <your-dockerhub-username>/flasktest-app:latest
docker push <your-dockerhub-username>/flasktest-app:latest
```

## Environment Variables
The workflow uses GitHub Secrets to store sensitive credentials like DockerHub credentials:
- `DOCKER_USERNAME` – Your DockerHub username
- `DOCKER_PASSWORD` – Your DockerHub password

## Conclusion
This repository provides an automated CI/CD pipeline for a Flask application using GitHub Actions and Docker. Contributions and improvements are welcome!

## License
This project is licensed under the MIT License.

