
# Container Observability Report

## 1. Application Logging

**Command Used:**

`docker logs client-website`

**404 Error Log:**

Paste the exact log line containing `/hidden-admin-page` and status code `404` here.

**Why Application Logs Are Important**

Application logs help engineers identify errors, failed requests, and unusual application behavior. They provide evidence that helps engineers troubleshoot problems and determine what happened before a failure.

## 2. Real-Time Container Metrics

**Command Used:**

`docker stats client-website`

- **Container Name:** client-website
- **Memory Usage:** [Enter your actual MEM USAGE value]
- **CPU Percentage:** [Enter your actual CPU % value]
- **Network I/O:** [Enter the value shown, if required]

**Observation**

Docker stats provides real-time information about the container's resource consumption. Monitoring these metrics helps identify unusually high CPU or memory usage before it affects application performance.

