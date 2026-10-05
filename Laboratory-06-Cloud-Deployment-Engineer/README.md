# Laboratory 06 – Cloud Deployment Engineer

## Mission Overview

This laboratory focuses on deploying a multi-tier cloud application using Docker Compose. The project uses Nextcloud as the application tier and MariaDB as the database tier.

## Objectives

- Understand two-tier architecture.
- Create a Docker Compose configuration.
- Deploy multiple containers as one application stack.
- Connect Nextcloud to a MariaDB database.
- Verify and access the deployed Nextcloud application.
- Practice container management and technical documentation.

## Commands Executed

```bash
mkdir nextcloud-deployment
cd nextcloud-deployment
nano docker-compose.yml
docker-compose up -d
docker-compose ps
docker-compose down
