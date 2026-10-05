# Multi-Tier Architecture

## What is a Two-Tier Architecture?

A Two-Tier Architecture is a system design that separates an application into two main tiers: the Web/Application Tier and the Database Tier. Each tier has a specific responsibility and communicates with the other tier to provide the complete application service.

## The Web/Application Tier

The Web/Application Tier is responsible for serving the user interface and handling HTTP requests from users. In this laboratory, the Nextcloud container acts as the Web/Application Tier and provides the web interface that users access through port 8080.

## The Database Tier

The Database Tier is responsible for storing and managing persistent data used by the application. In this laboratory, MariaDB acts as the Database Tier and stores information such as user accounts and application data.

## Why Separate Them?

Separating the web server and database into two containers makes the system easier to manage, maintain, and scale. Each container can be updated, restarted, or configured independently, reducing the risk of one component affecting the other.
