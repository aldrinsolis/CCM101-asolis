
# Firewall Configuration Report

## 1. Allow SSH Access

**Command:**

`sudo ufw allow ssh`

**Explanation:**

This command allows incoming SSH connections on port 22 so administrators can remotely manage the server.

## 2. Configure the Default Deny Policy

**Commands:**

`sudo ufw default deny incoming`

`sudo ufw default allow outgoing`

**Explanation:**

The first command blocks incoming connections unless a firewall rule explicitly permits them. The second command allows outgoing connections by default.

## 3. Enable the Firewall

**Command:**

`sudo ufw enable`

**Explanation:**

This activates the UFW firewall and applies its configured rules.

## 4. Allow Web Traffic

**Command:**

`sudo ufw allow 8080/tcp`

**Explanation:**

This rule permits incoming TCP traffic on port 8080 for the Nginx web application, subject to the firewall and network configuration.

## 5. Verify Firewall Rules

**Commands:**

`sudo ufw status verbose`

`sudo ufw status numbered`

**Explanation:**

These commands display the firewall's active status, default policies, and configured rules.

## 6. Why SSH Must Be Allowed First

If I enabled UFW before allowing SSH, incoming SSH connections could be blocked by the default deny policy, potentially locking me out of remote server administration.

