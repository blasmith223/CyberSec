## Week 5 Homework Submission File: Archiving and Logging Data

Please edit this file by adding the solution commands on the line below the prompt.

Save and submit the completed file for your homework submission.

---

### Step 1: Create, Extract, Compress, and Manage tar Backup Archives

1. Command to **extract** the `TarDocs.tar` archive to the current directory:
sudo tar -xvf TarDocs.tar -C /Projects/
2. Command to **create** the `Javaless_Doc.tar` archive from the `TarDocs/` directory, while excluding the `TarDocs/Documents/Java` directory:
sudo tar -cf ~/Projects/Javaless_Docs.tar --exclude "Documents/Java" ~/Projects/TarDocs/Documents
3. Command to ensure `Java/` is not in the new `Javaless_Docs.tar` archive:
tar -tf Javaless_Docs.tar | grep "Java"
**Bonus** 
- Command to create an incremental archive called `logs_backup_tar.gz` with only changed files to `snapshot.file` for the `/var/log` directory:

#### Critical Analysis Question

- Why wouldn't you use the options `-x` and `-c` at the same time with `tar`?
They will Create a new archive and Xtract the files.
---

### Step 2: Create, Manage, and Automate Cron Jobs

1. Cron job for backing up the `/var/log/auth.log` file:
* 6 * * 3 sudo tar -cvf auth_backup.tgz /var/log/auth.log >/dev/null 2>&1
---

### Step 3: Write Basic Bash Scripts

1. Brace expansion command to create the four subdirectories:
mkdir -p  {~/backups/freemem,~/backups/diskuse,~/backups/openlist,~/backups/freedisk}
2. Paste your `system.sh` script edits below:

#!/bin/bash
free -h >> ~/backups/freemem/free_mem.txt && date +%T/%d >> ~/backups/freemem/free_mem.txt
df -h >> ~/backups/diskuse/disk_usage.txt && date +%T/%d >> ~/backups/diskuse/disk_usage.txt
lsof >> ~/backups/openlist/open_list.txt && date +%T/%d >> ~/backups/openlist/open_list.txt
df -h >> ~/backups/freedisk/free_disk.txt && date +%T/%d >> ~/backups/freedisk/free_disk.txt
    I played a little and thought having the time and date display each time it runs would be beneficial and fun for learning.  All commands worked
3. Command to make the `system.sh` script executable:
chmod -x system.sh
**Optional**
- Commands to test the script and confirm its execution:
to display whole file.
more ~/backups/diskuse/disk_usage.txt 
more ~/backups/freemem/free_mem.txt 
more ~/backups/openlist/open_list.txt 
more ~/backups/freedisk/free_disk.txt
or use more to show to 10 lines or tail to show bottom 10. 
**Bonus**
- Command to copy `system` to system-wide cron directory:

---

### Step 4. Manage Log File Sizes
 
1. Run `sudo nano /etc/logrotate.conf` to edit the `logrotate` configuration file. 

    Configure a log rotation scheme that backs up authentication messages to the `/var/log/auth.log`.

    - Add your config file edits below:

    ```bash
[/var/log/auth.log {
weekely
rotate 7
notifempty
delaycompress
missingok}]
    ```
---

### Bonus: Check for Policy and File Violations

1. Command to verify `auditd` is active:

2. Command to set number of retained logs and maximum log file size:

    - Add the edits made to the configuration file below:

    ```bash
    [Your solution edits here]
    ```

3. Command using `auditd` to set rules for `/etc/shadow`, `/etc/passwd` and `/var/log/auth.log`:


    - Add the edits made to the `rules` file below:

    ```bash
    [Your solution edits here]
    ```

4. Command to restart `auditd`:

5. Command to list all `auditd` rules:

6. Command to produce an audit report:

7. Create a user with `sudo useradd attacker` and produce an audit report that lists account modifications:

8. Command to use `auditd` to watch `/var/log/cron`:

9. Command to verify `auditd` rules:

---

### Bonus (Research Activity): Perform Various Log Filtering Techniques

1. Command to return `journalctl` messages with priorities from emergency to error:

1. Command to check the disk usage of the system journal unit since the most recent boot:

1. Comand to remove all archived journal files except the most recent two:


1. Command to filter all log messages with priority levels between zero and two, and save output to `/home/sysadmin/Priority_High.txt`:

1. Command to automate the last command in a daily cronjob. Add the edits made to the crontab file below:

    ```bash
    [Your solution cron edits here]
    ```

---
© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.
