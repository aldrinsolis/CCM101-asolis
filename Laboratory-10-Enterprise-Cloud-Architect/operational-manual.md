# CloudNova Private Web Stack — Operational Manual

## 1. Purpose and Design

This lab deploys a two-tier web application using WordPress as the web/application tier and MariaDB as the database tier.

Docker Compose manages the services and makes deployment easier to repeat. The database is not published on a host port. Named volumes preserve application and database files when containers are recreated or the virtual machine reboots.

**Lab exposure:** HTTP on TCP port `8080` and SSH on TCP port `22`.

This is a classroom environment, not a hardened public production deployment. For production, add TLS, a reverse proxy, secrets management, off-host backups, monitoring, patching procedures, and a tested recovery plan.

## 2. Suggested VM Setup

Use a Type 2 hypervisor such as VirtualBox and the official Ubuntu Server LTS ISO.

| Component | Recommended Configuration |
|---|---|
| VM Name | `CloudNova-Ubuntu` |
| Operating System | Linux / Ubuntu (64-bit) |
| CPU | 2 vCPUs |
| RAM | 4 GB minimum |
| Disk | 25–40 GB dynamically allocated |
| Network | Bridged Adapter or NAT with port forwarding |
| SSH | OpenSSH Server enabled |

**Setup instructions:**

1. Create the virtual machine in VirtualBox.
2. Install Ubuntu Server LTS.
3. Create a normal administrative user.
4. Enable OpenSSH Server during installation if available.
5. Sign in and update the operating system.

Run these commands:

```bash
sudo apt update && sudo apt full-upgrade -y
sudo apt install -y ca-certificates curl git ufw gzip
ip -br address
```

Record the VM's reachable IPv4 address. With bridged networking, the host and VM usually need to be connected to the same local network.

Avoid exposing the VM directly to the public internet.

## 3. Install Docker Engine and Compose Plugin

Follow the official Docker installation guide for Ubuntu:

[Docker Engine installation on Ubuntu](https://docs.docker.com/engine/install/ubuntu/)

The following commands use Docker's official APT repository.

### Step 1: Install prerequisites

```bash
sudo apt update
sudo apt install -y ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
```

### Step 2: Add Docker's official signing key

```bash
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
```

### Step 3: Add the Docker repository

```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}") stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

### Step 4: Install Docker

```bash
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
sudo systemctl enable --now docker
```

### Step 5: Verify the installation

```bash
sudo docker run --rm hello-world
docker compose version
```

Use `sudo docker ...` for this lab. Membership in the `docker` group effectively grants root-level control, so do not add users casually.

## 4. Place the Project and Configure Secrets

Copy the project folder to the VM using SCP or Git. The project should contain the Compose file, `.env.example`, and `automation-script.sh`.

Place the project at `/opt/cloudnova`.

```bash
sudo mkdir -p /opt/cloudnova
sudo chown "$USER":"$USER" /opt/cloudnova
cd /opt/cloudnova
```

If the project files are already in the current directory, copy the example environment file:

```bash
cp .env.example .env
nano .env
```

Edit the following settings:

- `VM_LAN_IP`: Set this to the VM's reachable LAN IPv4 address.
- Database password placeholders: Replace them with long, unique random values.

Generate two separate random values:

```bash
openssl rand -hex 24
openssl rand -hex 24
```

Copy the generated values into the appropriate password fields in `.env`. Make sure the database credentials match the variable names expected by your Compose file and backup script.

Protect the environment file:

```bash
chmod 600 .env
```

**Important:** Never commit `.env` to GitHub. The project should include a `.gitignore` rule that excludes it.

### Validate and Start the Stack

```bash
sudo docker compose config
sudo docker compose pull
sudo docker compose up -d
sudo docker compose ps
sudo docker compose logs --tail=100
```

Open the following address in your host computer's browser, replacing the placeholder with the VM's actual IP address:

`http://<VM-LAN-IP>:8080`

Complete the WordPress first-run setup wizard.

## 5. Configure UFW Firewall

**Warning:** Before enabling UFW over SSH, allow SSH first to avoid locking yourself out. Keep the VM console open while applying firewall changes if possible.

For a simple lab on a trusted private LAN, run:

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow 22/tcp comment 'SSH administration'
sudo ufw allow 8080/tcp comment 'WordPress lab web'
sudo ufw enable
sudo ufw status verbose
```

### Restrict SSH Access

For better security, restrict SSH to your actual trusted host or subnet.

Example:

```bash
sudo ufw allow from 192.168.1.0/24 to any port 22 proto tcp
```

Only use this example subnet if it matches your network. Otherwise, replace it with your actual trusted address range.

After confirming that the restricted rule works, you can remove the broad SSH rule if appropriate:

```bash
sudo ufw delete allow 22/tcp
```

### Verify Firewall and Listening Ports

```bash
sudo ufw status numbered
sudo ss -tulpn
```

Only TCP ports `22` and `8080` should be allowed inbound for this lab. MariaDB's TCP port `3306` must not be published by Docker Compose.

**Docker firewall note:** Docker-published ports may bypass some UFW filtering paths, depending on the configuration. Do not assume UFW alone fully protects a published Docker port.

Keep the lab on a trusted network, bind the published web port to the VM's LAN IP where appropriate, and consult the official Docker firewall documentation if strict source restrictions are required.

Test connectivity from another device to verify that only intended ports are reachable.

## 6. Persistent Storage and Reboot Test

Docker Compose creates named volumes for persistent storage:

- `cloudnova_mariadb_data`
- `cloudnova_wordpress_data`

The actual volume names may have different prefixes depending on the Compose project name.

### List Docker Volumes

```bash
sudo docker volume ls
```

### Test Container Recreation

```bash
sudo docker compose down
sudo docker compose up -d
sudo docker compose ps
```

**Important:** Do not use `docker compose down -v` unless you intentionally want to delete the named volumes and their data.

### Test VM Reboot

```bash
sudo reboot
```

After reconnecting to the VM:

```bash
cd /opt/cloudnova
sudo docker compose ps
```

Open the WordPress site again and confirm that previously created content still exists.

## 7. Automated Database Backup

The backup script creates compressed SQL database dumps, verifies the gzip archive, and deletes backups older than seven days. It logs activity to `/var/log/cloudnova-backup.log`.

### Step 1: Install the Script

Run these commands from the project directory:

```bash
sudo install -m 0750 automation-script.sh /opt/cloudnova/automation-script.sh
sudo touch /var/log/cloudnova-backup.log
sudo chown root:adm /var/log/cloudnova-backup.log
sudo chmod 0640 /var/log/cloudnova-backup.log
```

### Step 2: Test the Backup Manually

```bash
sudo /opt/cloudnova/automation-script.sh
sudo tail -n 50 /var/log/cloudnova-backup.log
sudo ls -lh /opt/cloudnova/backups
```

Confirm that a backup file was created and that the log does not report errors.

### Step 3: Schedule a Daily Backup

Open root's crontab:

```bash
sudo crontab -e
```

Add this line:

```cron
0 2 * * * /opt/cloudnova/automation-script.sh
```

This schedules the backup to run every day at **2:00 AM**.

Verify the scheduled job:

```bash
sudo crontab -l
```

Ensure that the VM is powered on at the scheduled time. Cron does not automatically run missed jobs when the VM is powered off.

## 8. Database Restore Procedure

Use this procedure to restore a database backup.

### Step 1: Stop WordPress

```bash
cd /opt/cloudnova
sudo docker compose stop wordpress
```

This reduces application writes while the database is being restored.

### Step 2: Choose a Backup

```bash
ls -lh /opt/cloudnova/backups/
```

Identify the backup file you want to restore.

### Step 3: Restore the Database

Replace the example filename with the actual backup filename.

```bash
gunzip -c /opt/cloudnova/backups/mariadb_YYYYMMDD_HHMMSS.sql.gz | sudo docker compose exec -T db sh -c 'exec mariadb -u"$MARIADB_USER" -p"$MARIADB_PASSWORD" "$MARIADB_DATABASE"'
```

The database service must be running, and the environment variables must match the Compose configuration.

**Caution:** Restoring a SQL dump into an existing database can overwrite or conflict with existing data. Confirm the backup and target database before proceeding.

### Step 4: Start WordPress

```bash
sudo docker compose start wordpress
```

### Step 5: Verify the Restore

- Open the WordPress website.
- Check that the site loads correctly.
- Verify that expected posts, pages, and other content exist.
- Record the restore test date and result.

For disaster recovery, copy encrypted backups to a separate machine or off-site storage. Backups stored on the same virtual disk will be lost if that disk fails.

## 9. Operations and Troubleshooting

### Useful Commands

Check service status:

```bash
sudo docker compose ps
```

View recent logs:

```bash
sudo docker compose logs -f --tail=100
```

Monitor container resource usage:

```bash
sudo docker stats
```

Check disk space:

```bash
df -h
```

Check memory usage:

```bash
free -h
```

Check Docker service status:

```bash
sudo systemctl status docker
```

Check firewall rules:

```bash
sudo ufw status verbose
```

### Common Problems

#### Browser Cannot Connect

1. Confirm the VM's IP address:

   ```bash
   ip -br address
   ```

2. Check whether the VM uses bridged or NAT networking.
3. Check container status:

   ```bash
   sudo docker compose ps
   ```

4. Verify UFW rules and any NAT port-forwarding settings.
5. Confirm that the host and VM can communicate over the network.

#### WordPress Reports a Database Connection Error

1. Wait for the database health check to pass.
2. Review the logs:

   ```bash
   sudo docker compose logs db wordpress
   ```

3. Check the `.env` values and database credentials.
4. Restart the services if necessary:

   ```bash
   sudo docker compose up -d
   ```

#### Port Already in Use

Check which process is using the port:

```bash
sudo ss -tulpn
```

Choose another available host port in `docker-compose.yml` and update the firewall rules and browser URL accordingly.

#### Disk Full

Check disk usage:

```bash
df -h
sudo docker system df
sudo ls -lh /opt/cloudnova/backups
```

Investigate the cause before removing files.

**Never delete database volume data as a cleanup shortcut.**

#### Backup Fails

Check the backup log:

```bash
sudo tail -n 100 /var/log/cloudnova-backup.log
```

Then verify:

- The database container is healthy.
- The backup script is executable.
- The environment variables are correct.
- Sufficient disk space is available.
- The backup directory exists and is writable by the script.

