# Docker Compose Guide

## What does the `services:` block do?

The `services:` block defines the containers or services that Docker Compose will create and manage. In this project, there are two services: `database`, which uses the MariaDB image, and `app`, which uses the Nextcloud image. Docker Compose uses these definitions to configure the images, environment variables, ports, and other settings for each container.

## How did the Nextcloud app container find the database container?

The Nextcloud application uses the following environment variable:

```yaml
- MYSQL_HOST=database
