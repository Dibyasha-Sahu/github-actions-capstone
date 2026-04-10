# GitHub Actions Capstone

This project is a simple Flask app with a `/health` endpoint, containerized using Docker.

## Features
- Python Flask app with one endpoint
- Dockerfile for containerization
- Basic test script (`test.sh`) to check health 

## To run all this -> these are the cmd
- docker build -t capstone-app
- docker run -d -p 5000:5000 capstone-app
- docker ps
- open the wsl then bash test.sh
- docker stop <container name>

