## Week 4 Homework Submission File: Linux Systems Administration

Please edit this file by adding the solution commands on the line below the prompt.

Save and submit the completed file for your homework submission.


### Step 1: Ensure/Double Check Permissions on Sensitive Files

1. Permissions on `/etc/shadow` should allow only `root` read and write access.

    - Command to inspect permissions:

    ls -l /etc/shadow

    - Command to set permissions (if needed):

    The owner 'root' already has rw priviledges in the shadow file


2. Permissions on `/etc/gshadow` should allow only `root` read and write access.

    - Command to inspect permissions:

    ls -l /etc/gshadow

    - Command to set permissions (if needed):

    The owner 'root' already has rw priviledges in the gshadow file

3. Permissions on `/etc/group` should allow `root` read and write access, and allow everyone else read access only.

    - Command to inspect permissions:

    ls -l /etc/group

    - Command to set permissions (if needed):

    sudo chmod u=rw,g=rw,o=r /etc/group

4. Permissions on `/etc/passwd` should allow `root` read and write access, and allow everyone else read access only.

    - Command to inspect permissions:

    ls -l /etc/passwd

    - Command to set permissions (if needed):

    sudo chmod u=rw,u=rw,o=r /etc/passwd

### Step 2: Create User Accounts

1. Add user accounts for `sam`, `joe`, `amy`, `sara`, and `admin`.

    - Command to add each user account (include all five users): 

    sudo adduser sam
    sudo adduser joe
    sudo adduser amy
    sudo adduser sara
    sudo adduser admin

2. Ensure that only the `admin` has general sudo access.

    - Command to add `admin` to the `sudo` group:

    sudo usermod -aG sudo admin

### Step 3: Create User Group and Collaborative Folder

1. Add an `engineers` group to the system.

    - Command to add group:

    sudo addgroup engineers

2. Add users `sam`, `joe`, `amy`, and `sara` to the managed group.

    - Command to add users to `engineers` group (include all four users):

    sudo gpasswd -M sam,joe,amy,sara engineers

3. Create a shared folder for this group at `/home/engineers`.

    - Command to create the shared folder:

    sudo mkdir -p /home/engineers/engineersgroup

4. Change ownership on the new engineers' shared folder to the `engineers` group.

    - Command to change ownership of engineer's shared folder to engineer group:

    chgrp -R engineersgroup /home/engineers

### Step 4: Lynis Auditing

1. Command to install Lynis:

    sudo apt-get -y install lynis


2. Command to see documentation and instructions:

    lynis man

3. Command to run an audit:

    sudo lynis audit system

4. Provide a report from the Lynis output on what can be done to harden the system.
    - Screenshot of report output:

 Warnings (4):
  ----------------------------
  ! Version of Lynis is very old and should be updated [LYNIS] 
      https://cisofy.com/controls/LYNIS/

  ! No password set for single mode [AUTH-9308] 
      https://cisofy.com/controls/AUTH-9308/

  ! Found one or more vulnerable packages. [PKGS-7392] 
      https://cisofy.com/controls/PKGS-7392/

  ! Found some information disclosure in SMTP banner (OS or software name) [MAIL-8818] 
      https://cisofy.com/controls/MAIL-8818/




         * Consider hardening SSH configuration [SSH-7408] 
    - Details  : AllowTcpForwarding (YES --> NO)
      https://cisofy.com/controls/SSH-7408/

  * Consider hardening SSH configuration [SSH-7408] 
    - Details  : ClientAliveCountMax (3 --> 2)
      https://cisofy.com/controls/SSH-7408/

  * Consider hardening SSH configuration [SSH-7408] 
    - Details  : Compression (YES --> (DELAYED|NO))
      https://cisofy.com/controls/SSH-7408/

  * Consider hardening SSH configuration [SSH-7408] 
    - Details  : LogLevel (INFO --> VERBOSE)
      https://cisofy.com/controls/SSH-7408/

  * Consider hardening SSH configuration [SSH-7408] 
    - Details  : MaxAuthTries (6 --> 2)
      https://cisofy.com/controls/SSH-7408/

  * Consider hardening SSH configuration [SSH-7408] 
    - Details  : MaxSessions (10 --> 2)
      https://cisofy.com/controls/SSH-7408/

  * Consider hardening SSH configuration [SSH-7408] 
    - Details  : PermitRootLogin (WITHOUT-PASSWORD --> NO)
      https://cisofy.com/controls/SSH-7408/

  * Consider hardening SSH configuration [SSH-7408] 
    - Details  : Port (22 --> )
      https://cisofy.com/controls/SSH-7408/



### Bonus
1. Command to install chkrootkit:

2. Command to see documentation and instructions:

3. Command to run expert mode:

4. Provide a report from the chrootkit output on what can be done to harden the system.
    - Screenshot of end of sample output:

---
© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.
