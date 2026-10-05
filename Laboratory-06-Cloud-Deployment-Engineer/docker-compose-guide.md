# Docker Compose Guide

## What does the services: block do?

The `services:` block defines the containers that Docker Compose will create and manage. In this project, it contains two services: `database` for MariaDB and `app` for Nextcloud.

## How does Nextcloud find the database?

The Nextcloud application uses the following environment variable:

```yaml
- MYSQL_HOST=database
