
# Backup Script Guide

## 1. Purpose

This Bash script automates the backup of the app-data directory. It creates a compressed archive containing the sample client data and adds a timestamp to the archive filename so that different backups can be identified.

## 2. Full Backup Script

```bash
#!/bin/bash
# Automated Backup Script for CloudNova Technologies

SOURCE_DIR="app-data"
BACKUP_DIR="backups"
TIMESTAMP=$(date +"%Y%m%d_%H%M%S")

echo "Initiating automated backup..."

# Create the backup directory if it does not exist
mkdir -p "$BACKUP_DIR"

# Compress the source directory into a tarball (.tar.gz)
tar -czf "$BACKUP_DIR/backup_$TIMESTAMP.tar.gz" "$SOURCE_DIR"

echo "Backup completed successfully at $TIMESTAMP!"
```

## 3. File Permissions

The command `chmod +x backup.sh` grants the file execute permission. This allows the user to run the script using `./backup.sh` without manually starting Bash to interpret the file.

## 4. Backup Process

1. The script identifies the source and backup directories.
2. It generates a timestamp using the `date` command.
3. It creates the backup directory if it does not already exist.
4. It uses `tar -czf` to compress the source directory into a `.tar.gz` archive.
5. It displays a completion message.

## 5. Cron Job Configuration

The cron expression used is:

```cron
0 2 * * * /root/backup.sh
```

### Explanation of the Five Time Fields

| Field | Value | Meaning |
|---|---|---|
| Minute | `0` | At minute zero |
| Hour | `2` | At 2 AM |
| Day of Month | `*` | Every day of the month |
| Month | `*` | Every month |
| Day of Week | `*` | Every day of the week |

The script path `/root/backup.sh` identifies the script that cron will execute. The schedule runs daily at 2:00 AM, based on the system's local time.

## 6. Testing and Verification

The command `ls -l backups/` lists the generated backup files. The command `tar -tzf backups/backup_*.tar.gz` can be used to inspect the contents of an archive.

## 7. Conclusion

Bash scripting and cron scheduling help automate repetitive cloud operations. Regularly checking backup files and testing restoration are important to ensure that the backup process is reliable.

