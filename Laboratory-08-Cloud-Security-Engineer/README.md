
# Laboratory 08 – Cloud Security Engineer

## Mission Overview

In this laboratory, I learned basic cloud security practices by deploying an Nginx web application and configuring the Ubuntu firewall with UFW. I practiced controlling incoming network traffic and allowing only the connections required by the application.

## Objectives

- Understand the Principle of Least Privilege.
- Explain attack surfaces and the Default Deny policy.
- Deploy an Nginx container using Docker.
- Configure UFW firewall rules.
- Allow SSH and web traffic on port 8080.
- Verify firewall status and document the security configuration.

## Commands Executed

| Command | Purpose |
|---|---|
| `docker run -d -p 8080:80 --name secure-web-app nginx` | Deploy the Nginx web application. |
| `curl http://localhost:8080` | Test access to the application. |
| `sudo ufw allow ssh` | Allow SSH connections. |
| `sudo ufw default deny incoming` | Block incoming traffic by default. |
| `sudo ufw default allow outgoing` | Allow outgoing traffic by default. |
| `sudo ufw enable` | Activate the firewall. |
| `sudo ufw status verbose` | Check firewall status and default policies. |
| `sudo ufw allow 8080/tcp` | Add a rule allowing TCP traffic on port 8080. |
| `sudo ufw status numbered` | Display numbered firewall rules. |

## Skills Learned

- Basic cloud security principles.
- Linux firewall configuration using UFW.
- Docker application deployment.
- Network port management.
- Firewall rule verification.
- Security documentation and screenshot collection.

