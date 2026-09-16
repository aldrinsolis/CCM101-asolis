# Mission Reflection

This laboratory activity helped me understand how Docker containers are different from Virtual Machines. A Docker container can start within seconds because it shares the host operating system kernel and does not need to boot a complete operating system. In comparison, a Virtual Machine requires its own operating system, so the setup and boot process usually takes more time and uses more resources. Because of this, containers can provide a faster and more lightweight way to deploy applications.

Port mapping using `-p 8080:80` is necessary when running a web server inside a container because the Nginx server is listening on port 80 inside the container. The container is isolated from the host system, so port mapping provides a connection between the host and the application inside the container. In this activity, port 8080 on the host was connected to port 80 inside the Nginx container. This allowed me to access the Nginx web server using `curl http://localhost:8080`.

When the `docker rm` command is used, the specified container is permanently removed. Any data stored only inside the container's writable layer can be lost when the container is removed. This means important information should be stored using persistent storage, such as Docker volumes, when it needs to remain available after a container is deleted.

Containerization can change the way software developers and IT operations teams work together because applications can be packaged with their required dependencies in containers. Developers can create and test the same container that operations teams can deploy, making environments more consistent. This supports DevOps practices by improving collaboration, testing, automation, and deployment.

My GitHub portfolio is also evolving as I add more laboratory activities and technical documentation. This laboratory adds practical experience with Docker, Nginx, containers, networking, and container management. By organizing my files, screenshots, commands, and reflections, my GitHub repository is becoming a record of the cloud computing skills I have developed.
