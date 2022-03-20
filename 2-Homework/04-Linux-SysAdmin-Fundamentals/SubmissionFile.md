## Week 4 Homework Submission File: Linux Systems Administration

Please edit this file by adding the solution commands on the line below the prompt.

Save and submit the completed file for your homework submission.


### Step 1: Ensure/Double Check Permissions on Sensitive Files

1. Permissions on `/etc/shadow` should allow only `root` read and write access.

    - Command to inspect permissions:
ls -l | grep 'shadow'
    - Command to set permissions (if needed):
Not needed in this case. Would be 'sudo chmod 600 shadow' if needed.
2. Permissions on `/etc/gshadow` should allow only `root` read and write access.

    - Command to inspect permissions:
ls -l | grep 'gshadow'
    - Command to set permissions (if needed):
Again, root has already been set to rw only. Would use command line 'sudo chmod 600 gshadow' if needed.
3. Permissions on `/etc/group` should allow `root` read and write access, and allow everyone else read access only.

    - Command to inspect permissions:
ls -l | grep 'group'
    - Command to set permissions (if needed):
sudo chmod 644 'group'
4. Permissions on `/etc/passwd` should allow `root` read and write access, and allow everyone else read access only.

    - Command to inspect permissions:
ls -l | grep 'passwd'
    - Command to set permissions (if needed):
sudo chmod 644 passwd
### Step 2: Create User Accounts

1. Add user accounts for `sam`, `joe`, `amy`, `sara`, and `admin`.

    - Command to add each user account (include all five users):
sudo adduser sam 
sudo adduser joe
sudo adduser amy
sudo adduser sarah
sudo adduser admin
2. Ensure that only the `admin` has general sudo access.

    - Command to add `admin` to the `sudo` group:
sudo usermod -aG sudo admin
### Step 3: Create User Group and Collaborative Folder

1. Add an `engineers` group to the system.

    - Command to add group:
sudo groupadd engineers
2. Add users `sam`, `joe`, `amy`, and `sara` to the managed group.

    - Command to add users to `engineers` group (include all four users):
sudo usermod -a -G engineers sam
sudo usermod -a -G engineers joe
sudo usermod -a -G engineers amy
sudo usermod -a -G engineers sarah
3. Create a shared folder for this group at `/home/engineers`.

    - Command to create the shared folder:
sudo mkdir /home/engineers 
4. Change ownership on the new engineers' shared folder to the `engineers` group.

    - Command to change ownership of engineer's shared folder to engineer group:
sudo chgrp -R engineers /home/engineers
### Step 4: Lynis Auditing

1. Command to install Lynis:
sudo apt install lynis
2. Command to see documentation and instructions:
man lynis
3. Command to run an audit:
sudo lynis audit system
4. Provide a report from the Lynis output on what can be done to harden the system.

    - Screenshot of report output:
https://drive.google.com/file/d/1w2QFlTmPACkiksP_Tq1GxVt4ufALeDPm/view?usp=sharing


### Bonus
1. Command to install chkrootkit:

2. Command to see documentation and instructions:

3. Command to run expert mode:

4. Provide a report from the chrootkit output on what can be done to harden the system.
    - Screenshot of end of sample output:

---
© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.
