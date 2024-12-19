# Dockerfile: Copying Local Files to a Container

This repository contains a sample Dockerfile that demonstrates how to copy a local file into a Docker container. This Dockerfile is based on Amazon Linux 2 and sets up a simple Apache HTTP server (httpd).

## Key Features

- **Base Image**: Amazon Linux 2.
- **Software Installed**: Apache HTTP Server (httpd), wget, and unzip.
- **File Copying**: Copies `index.html` from the local directory into `/var/www/html/` inside the container.
- **Port Exposure**: Exposes port `80` for HTTP traffic.
- **Command**: Starts the Apache HTTP server in the foreground.

## Usage

1. Clone this repository to your local machine.
2. Place your `index.html` file in the same directory as the Dockerfile.
3. Build the Docker image:
   ```bash
   docker build -t amazonlinux-httpd .
   ```
4. Run the container:
   ```bash
   docker run -d -p 80:80 amazonlinux-httpd
   ```
5. Access the web server by navigating to `http://localhost` in your browser.

## Purpose

This Dockerfile is created as a reference for copying a local file into a Docker container during the build process. It helps you understand how the `COPY` command works in Dockerfiles.

## Notes

- Make sure the `index.html` file exists in the same directory as the Dockerfile before building the image.
- Modify the `COPY` command as needed to copy other files or directories.
