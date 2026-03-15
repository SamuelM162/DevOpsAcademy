# Section 1 – Implementation – Dockerize a Python Web App

## Overview
This section demonstrates how to containerize a simple Flask web application using Docker and Docker Compose.

The application is built using Python and Flask and returns a basic "Hello World!" response on the root endpoint.

## Application
The Flask application runs inside a Docker container on port 3000.

Example endpoint:

/

Response:

Hello World!

## Dockerfile

The Dockerfile builds the application image using the lightweight Python base image.

Steps performed in the Dockerfile:

1. Use the base image `python:3.10-slim`
2. Set the working directory to `/app`
3. Copy the `requirements.txt` file
4. Install Python dependencies
5. Copy the rest of the application files
6. Expose port `3000`
7. Start the application using `python app.py`

Dockerfile used in this project:

FROM python:3.10-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install -r requirements.txt

COPY . .

EXPOSE 3000

CMD ["python", "app.py"]

## Docker Compose

Docker Compose is used to simplify building and running the container.

The application runs on port **3000 inside the container** and is mapped to **port 3001 on the host machine**.

docker-compose.yml:

services:
  flask-app:
    build: .
    ports:
      - "3001:3000"

Port mapping explanation:

Host machine: 3001  
Container: 3000

This allows the application to be accessed in the browser.

## Running the Application

Build and run the container:

docker compose up --build

After startup, open a browser and go to:

http://localhost:3001

The application should display:

Hello World!

## Conclusion

This task demonstrates basic containerization of a web application using Docker.  
Dockerfile is used to build the image, while Docker Compose simplifies running and networking the container.