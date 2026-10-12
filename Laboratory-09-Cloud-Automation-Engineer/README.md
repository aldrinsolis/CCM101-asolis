
# Laboratory 09 – Cloud Automation Engineer

## Mission Overview

In this laboratory, I learned how to automate a backup process using a Bash script in a Linux environment. I created sample client data, compressed it into a backup archive, configured file permissions, and scheduled the script using cron.

## Objectives

- Understand Bash scripts, variables, and cron jobs.
- Create a sample data directory and test file.
- Write a script that creates timestamped compressed backups.
- Use Linux permissions to make a script executable.
- Schedule an automated daily backup.
- Document the commands and results in GitHub.

## Commands Executed

| Command | Purpose |
|---|---|
| `mkdir -p app-data` | Creates the sample data directory. |
| `echo "This is critical client data." > app-data/data.txt` | Creates a sample file. |
| `nano backup.sh` | Opens the text editor to create the script. |
| `chmod +x backup.sh` | Grants execute permission. |
| `./backup.sh` | Executes the backup script. |
| `ls -l backups/` | Lists the backup files. |
| `tar -tzf backups/backup_*.tar.gz` | Inspects the archive contents. |
| `crontab -l` | Displays the current cron schedule. |
| `env EDITOR=nano crontab -e` | Opens the cron table editor. |

## Skills Learned

- Writing and executing Bash scripts.
- Using variables and timestamps in automation.
- Compressing files with the `tar` command.
- Managing Linux file permissions.
- Scheduling recurring tasks with cron.
- Verifying backups and documenting technical procedures.
- Organizing and maintaining a cloud computing portfolio in GitHub.

## Screenshots

- `screenshots/script-execution.png` – Successful backup execution and archive listing.
- `screenshots/cron-schedule.png` – Installed cron schedule.

## Conclusion

This laboratory helped me understand how automation reduces repetitive manual work in cloud operations. I also learned that scheduled scripts should be tested and monitored to ensure that they run correctly and protect important data.

