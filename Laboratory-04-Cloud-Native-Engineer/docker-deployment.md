# Docker Deployment

## Checkpoint 4 – Deploy Your First Container

### 1. Pull the Nginx Image

```bash
docker pull nginx
```

This command downloads the official Nginx image from Docker Hub.

### 2. Run the Nginx Container

```bash
docker run -d --name nginx-server -p 8080:80 nginx
```

This command runs the Nginx container in detached mode and maps host port 8080 to port 80 inside the container.

### 3. List the Running Container

```bash
docker ps
```

This command displays the currently running Docker containers and confirms that the Nginx container is running.

### 4. Test the Nginx Web Server

```bash
curl http://localhost:8080
```

This command sends an HTTP request to the Nginx web server and displays the returned HTML in the terminal.

---

## Checkpoint 5 – Container Lifecycle

### 1. List Running Containers

```bash
docker ps
```

This command lists all Docker containers that are currently running.

### 2. Stop the Running Container

```bash
docker stop nginx-server
```

This command stops the running Nginx container without removing it.

### 3. Verify the Container is Stopped

```bash
docker ps
```

This command verifies that the Nginx container is no longer running.

### 4. View All Containers

```bash
docker ps -a
```

This command displays all Docker containers, including stopped containers.

### 5. Remove the Container Completely

```bash
docker rm nginx-server
```

This command permanently removes the stopped Nginx container.

### 6. Verify the Container is Removed

```bash
docker ps -a
```

This command verifies that the Nginx container has been completely removed from the Docker environment.
