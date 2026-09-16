# Laboratory 04 – Cloud-Native Engineer

## Mission Overview

This laboratory activity introduced the concepts of containerization and Docker in cloud-native computing. The activity focused on understanding the differences between Virtual Machines and containers, verifying a Docker environment, deploying an Nginx web server, and managing the container lifecycle. Through the activity, I practiced using Docker commands to pull images, run containers, test web applications, stop containers, and remove containers.

## Objectives

The objectives of this laboratory activity are to:

- Understand the differences between Virtual Machines and containers.
- Learn the advantages of containerization in cloud computing.
- Verify that Docker is installed and running.
- Download the official Nginx image from Docker Hub.
- Deploy an Nginx web server using Docker.
- Understand port mapping between the host and container.
- Test the Nginx web server using an HTTP request.
- Learn how to manage the Docker container lifecycle.
- Improve technical documentation and GitHub portfolio skills.

## Docker Commands Executed

### Checkpoint 3 – Enter the Docker Playground

```bash
docker --version
docker info
docker ps

docker pull nginx
docker run -d --name nginx-server -p 8080:80 nginx
docker ps
curl http://localhost:8080

docker ps
docker stop nginx-server
docker ps
docker ps -a
docker rm
nginx-server
docker ps -a

## Skills Learned

During this laboratory activity, I learned how to use Docker to deploy and manage containers.
I learned how to verify a Docker installation, download an image from Docker Hub,
create and run an Nginx container, and use port mapping to access a web server.
I also learned how to check running containers, stop a container, view stopped containers, and remove a container.
In addition, I improved my ability to document technical activities and organize laboratory outputs in a GitHub repository.

## Challenges Encountered

One challenge I encountered was understanding the difference between a Virtual Machine and a container.
Another challenge was understanding the purpose of port mapping, especially the `8080:80` configuration.
I also had to carefully execute the Docker lifecycle commands in the correct order because a container must be stopped before
it can be removed. By following the commands step by step and checking the terminal output, I was able to understand
the Docker environment better and successfully complete the deployment and lifecycle activities.
