# Dockerfile: Simple Web Server for Downloading and Serving Applications  

This repository contains a Dockerfile designed to set up a lightweight HTTP server using Amazon Linux 2 and Apache HTTP Server (httpd). The server is preconfigured to download and serve a static website or application template from a given URL.  

## Purpose  

This Dockerfile is intended as a reference for:  
- **Setting up a web server** to serve static content.  
- **Downloading an application or template from the browser** using a URL.  
- Demonstrating the use of Amazon Linux 2 with Apache in a Docker container.  

## Features  
- **Base Image**: Amazon Linux 2  
- **Web Server**: Apache HTTP Server (httpd)  
- **Static Website**: A free CSS template is downloaded, extracted, and served.  

## Dockerfile Breakdown  

1. **Base Image**:  
   Uses the `amazonlinux:2` image for a lightweight and secure base.  

2. **Software Installation**:  
   Installs Apache HTTP Server (`httpd`), `wget`, and `unzip` using the Amazon Linux package manager (`yum`).  

3. **Downloading Content**:  
   Fetches the static website template (`blugoon.zip`) from the Free CSS website.  

4. **Content Setup**:  
   Extracts the downloaded template and moves its content to Apache's web root directory (`/var/www/html`).  

5. **Exposing Port**:  
   Opens port `80` to allow HTTP traffic to the container.  

6. **Command to Start the Server**:  
   Configures Apache HTTP Server to run in the foreground, keeping the container alive.  

## Usage Instructions  

### Build the Docker Image  

```bash
docker build -t apache-static-site .
```  

### Run the Docker Container  

```bash
docker run -d -p 8080:80 apache-static-site
```  

### Access the Web Application  

- Open your web browser and go to `http://localhost:8080`.  
- You will see the static website template (Blugoon) served by Apache.  

## Notes  

- The downloaded application can be replaced with any other URL by modifying the `RUN wget` command in the Dockerfile.  
- This setup is for demonstration and learning purposes; for production use, consider additional configurations for security and performance.  

