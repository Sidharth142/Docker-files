#README: Running a Django Application with Docker

This guide explains how to use the Dockerfile to create a containerized environment for a Django application.
---
## What This Dockerfile Does?

1. Uses **Ubuntu** as the base image.
2. Installs **Python 3**, **pip**, and **virtual environment tools**.
3. Copies application files into the container.
4. Sets up a **Python virtual environment** and installs dependencies.
5. Exposes **port 8000** for the Django app.
6. Runs the Django development server.
---
## Dockerfile Breakdown

### 1. Base Image & Working Directory

FROM ubuntu
WORKDIR /app

- Uses Ubuntu as the base OS.
- Creates and sets **/app** as the working directory.

### 2. Install Python & Dependencies

RUN apt-get update && \
    apt-get install -y python3 python3-pip python3-venv

- Installs Python, pip, and virtual environment tools.

### 3. Copy Files & Install Requirements

COPY requirements.txt /app/
COPY devops /app/
RUN python3 -m venv /app/venv && \
    /app/venv/bin/pip install --no-cache-dir -r requirements.txt

- Copies required files into the container.
- Creates a virtual environment and installs dependencies.

### 4. Expose Port & Start Server

EXPOSE 8000
CMD ["/app/venv/bin/python3", "manage.py", "runserver", "0.0.0.0:8000"]

- Exposes **port 8000** for external access.
- Starts the Django development server.

## How to Build & Run the Container

### Step 1: Navigate to Project Directory
cd /path/to/your/project

### step 2: Build the Docker Image

docker build -t my-django-app .

Step 3: Run the Container
docker run -p 8000:8000 my-django-app

Step 4: Access the Application

Open a browser and visit:
http://localhost:8000

##Common Issues & Fixes

###1. "docker: command not found"

- Ensure **Docker** is installed:
  docker --version

### 2. "ModuleNotFoundError" in Django

- Rebuild the image:
  docker build --no-cache -t my-django-app .


### 3. "Permission Denied" in Docker Commands

- Use **sudo** or add your user to the Docker group:

  sudo usermod -aG docker $USER
  reboot

## Final Notes

- Use Gunicorn & Nginx for production.
- To stop the container:

  docker stop <container_id>
 
  Find the container ID with:

  docker ps

