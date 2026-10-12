
# Laboratory 07 – Cloud Operations Engineer

## Mission Overview

In this laboratory, I performed basic cloud operations tasks by checking the health of an Ubuntu server, deploying an Nginx web server using Docker, generating HTTP requests, reviewing application logs, and monitoring container resources.

## Objectives

- Check the server's RAM and disk storage.
- Observe CPU usage and running processes.
- Deploy and access an Nginx container.
- Generate successful HTTP requests and a 404 error.
- Review application logs and monitor CPU and memory consumption.
- Document the results using Markdown and screenshots.

## Monitoring Commands Executed

| Command | Purpose |
|---|---|
| `free -h` | Check RAM usage and total memory. |
| `df -h /` | Check root filesystem storage. |
| `top` | Monitor CPU usage and running processes. |
| `docker run -d -p 8080:80 --name client-website nginx` | Deploy Nginx in a container. |
| `curl http://localhost:8080` | Send a request to the Nginx website. |
| `curl http://localhost:8080/hidden-admin-page` | Generate a 404 response. |
| `docker logs client-website` | Review the container's application logs. |
| `docker stats client-website` | Monitor live container resource usage. |

## Skills Learned

- Linux system resource monitoring.
- Docker container deployment and port mapping.
- HTTP request testing using curl.
- Application log analysis and error identification.
- Real-time CPU, memory, and network monitoring.
- Technical documentation and screenshot management.

