## Week 4 Homework Submission File: Linux Systems Administration

Please edit this file by adding the solution commands on the line below the prompt.

Save and submit the completed file for your homework submission.


### Step 1: Ensure/Double Check Permissions on Sensitive Files

1. Permissions on `/etc/shadow` should allow only `root` read and write access.

    - Command to inspect permissions: ls -l /etc/shadow

    - Command to set permissions (if needed): sudo chmod 600 /etc/shadow

2. Permissions on `/etc/gshadow` should allow only `root` read and write access.

    - Command to inspect permissions: ls -l /etc/gshadow

    - Command to set permissions (if needed): sudo chmod 600 /etc/gshadow

3. Permissions on `/etc/group` should allow `root` read and write access, and allow everyone else read access only.

    - Command to inspect permissions: ls -l /etc/group

    - Command to set permissions (if needed): sudo chmod 644 /etc/group

4. Permissions on `/etc/passwd` should allow `root` read and write access, and allow everyone else read access only.

    - Command to inspect permissions: ls -l /etc/passwd

    - Command to set permissions (if needed): sudo chmod 644 /etc/passwd/

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

2. Add users `sam`, `joe`, `amy`, and `sara` to the managed group.

    - Command to add users to `engineers` group (include all four users):

sudo usermod -aG engineers sam
sudo usermod -aG engineers joe
sudo usermod -aG engineers amy
sudo usermod -aG engineers sara


3. Create a shared folder for this group at `/home/engineers`.

    - Command to create the shared folder: 
    
        in the /home/ directory... 
     sudo mkdir engineers

4. Change ownership on the new engineers' shared folder to the `engineers` group.

    - Command to change ownership of engineer's shared folder to engineer group: 

sudo chown :engineers engineers/


### Step 4: Lynis Auditing

1. Command to install Lynis:

sudo apt install Lynis

2. Command to see documentation and instructions:

man lynis

3. Command to run an audit:

sudo lynis audit system


4. Provide a report from the Lynis output on what can be done to harden the system.

    - Screenshot of report output:

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

  * Consider hardening SSH configuration [SSH-7408] 
    - Details  : TCPKeepAlive (YES --> NO)
      https://cisofy.com/controls/SSH-7408/

  * Consider hardening SSH configuration [SSH-7408] 
    - Details  : X11Forwarding (YES --> NO)
      https://cisofy.com/controls/SSH-7408/

  * Consider hardening SSH configuration [SSH-7408] 
    - Details  : AllowAgentForwarding (YES --> NO)
      https://cisofy.com/controls/SSH-7408/

  * Check what deleted files are still in use and why. [LOGG-2190] 
      https://cisofy.com/controls/LOGG-2190/

  * Add a legal banner to /etc/issue, to warn unauthorized users [BANN-7126] 
      https://cisofy.com/controls/BANN-7126/

  * Add legal banner to /etc/issue.net, to warn unauthorized users [BANN-7130] 
      https://cisofy.com/controls/BANN-7130/

  * Enable process accounting [ACCT-9622] 
      https://cisofy.com/controls/ACCT-9622/

  * Enable sysstat to collect accounting (no results) [ACCT-9626] 
      https://cisofy.com/controls/ACCT-9626/

  * Enable auditd to collect audit information [ACCT-9628] 
      https://cisofy.com/controls/ACCT-9628/

  * Run 'docker info' to see warnings applicable to Docker daemon [CONT-8104] 
      https://cisofy.com/controls/CONT-8104/

  * One or more sysctl values differ from the scan profile and could be tweaked [KRNL-6000] 
    - Solution : Change sysctl value or disable test (skip-test=KRNL-6000:<sysctl-key>)
      https://cisofy.com/controls/KRNL-6000/

  * Harden compilers like restricting access to root user only [HRDN-7222] 
      https://cisofy.com/controls/HRDN-7222/

  Follow-up:
  ----------------------------
  - Show details of a test (lynis show details TEST-ID)
  - Check the logfile for all details (less /var/log/lynis.log)
  - Read security controls texts (https://cisofy.com)
  - Use --upload to upload data to central system (Lynis Enterprise users)

================================================================================

  Lynis security scan details:

  Hardening index : 57 [###########         ]
  Tests performed : 240
  Plugins enabled : 1

  Components:
  - Firewall               [V]
  - Malware scanner        [V]

  Lynis Modules:
  - Compliance Status      [?]
  - Security Audit         [V]
  - Vulnerability Scan     [V]

  Files:
  - Test and debug information      : /var/log/lynis.log
  - Report data                     : /var/log/lynis-report.dat

================================================================================
  Notice: Lynis update available
  Current version : 262    Latest version : 307
================================================================================

  Lynis 2.6.2

  Auditing, system hardening, and compliance for UNIX-based systems
  (Linux, macOS, BSD, and others)

  2007-2018, CISOfy - https://cisofy.com/lynis/
  Enterprise support available (compliance, plugins, interface and tools)

================================================================================

  [TIP]: Enhance Lynis audits by adding your settings to custom.prf (see /etc/lynis/default.prf for all settings)



### Bonus
1. Command to install chkrootkit:

sudo apt install chkrootkit

2. Command to see documentation and instructions:

man chkrootkit

3. Command to run expert mode:

sudo chkrootkit -x

4. Provide a report from the chrootkit output on what can be done to harden the system.
    - Screenshot of end of sample output:

    ! gdm          2167 tty1   /usr/lib/gnome-settings-daemon/gsd-sharing
! gdm          2177 tty1   /usr/lib/gnome-settings-daemon/gsd-smartcard
! gdm          2183 tty1   /usr/lib/gnome-settings-daemon/gsd-sound
! gdm          2188 tty1   /usr/lib/gnome-settings-daemon/gsd-wacom
! gdm          2123 tty1   /usr/lib/gnome-settings-daemon/gsd-xsettings
! gdm          2080 tty1   ibus-daemon --xim --panel disable
! gdm          2086 tty1   /usr/lib/ibus/ibus-dconf
! gdm          2242 tty1   /usr/lib/ibus/ibus-engine-simple
! gdm          2089 tty1   /usr/lib/ibus/ibus-x11 --kill-daemon
! sysadmin     2307 tty2   /usr/lib/xorg/Xorg vt2 -displayfd 3 -auth /run/user/1000/gdm/Xauthority -background none -noreset -keeptty -verbose 3
! sysadmin     2305 tty2   /usr/lib/gdm3/gdm-x-session --run-script env GNOME_SHELL_SESSION_MODE=ubuntu gnome-session --session=ubuntu
! sysadmin     2329 tty2   /usr/lib/gnome-session/gnome-session-binary --session=ubuntu
! sysadmin     2498 tty2   /usr/bin/gnome-shell
! sysadmin     2942 tty2   /usr/bin/gnome-software --gapplication-service
! sysadmin     2672 tty2   /usr/lib/gnome-settings-daemon/gsd-a11y-settings
! sysadmin     2673 tty2   /usr/lib/gnome-settings-daemon/gsd-clipboard
! sysadmin     2668 tty2   /usr/lib/gnome-settings-daemon/gsd-color
! sysadmin     2678 tty2   /usr/lib/gnome-settings-daemon/gsd-datetime
! sysadmin     2733 tty2   /usr/lib/gnome-disk-utility/gsd-disk-utility-notify
! sysadmin     2679 tty2   /usr/lib/gnome-settings-daemon/gsd-housekeeping
! sysadmin     2680 tty2   /usr/lib/gnome-settings-daemon/gsd-keyboard
! sysadmin     2683 tty2   /usr/lib/gnome-settings-daemon/gsd-media-keys
! sysadmin     2631 tty2   /usr/lib/gnome-settings-daemon/gsd-mouse
! sysadmin     2632 tty2   /usr/lib/gnome-settings-daemon/gsd-power
! sysadmin     2634 tty2   /usr/lib/gnome-settings-daemon/gsd-print-notifications
! sysadmin     2700 tty2   /usr/lib/gnome-settings-daemon/gsd-printer
! sysadmin     2638 tty2   /usr/lib/gnome-settings-daemon/gsd-rfkill
! sysadmin     2639 tty2   /usr/lib/gnome-settings-daemon/gsd-screensaver-proxy
! sysadmin     2641 tty2   /usr/lib/gnome-settings-daemon/gsd-sharing
! sysadmin     2642 tty2   /usr/lib/gnome-settings-daemon/gsd-smartcard
! sysadmin     2655 tty2   /usr/lib/gnome-settings-daemon/gsd-sound
! sysadmin     2659 tty2   /usr/lib/gnome-settings-daemon/gsd-wacom
! sysadmin     2660 tty2   /usr/lib/gnome-settings-daemon/gsd-xsettings
! sysadmin     2533 tty2   ibus-daemon --xim --panel disable
! sysadmin     2537 tty2   /usr/lib/ibus/ibus-dconf
! sysadmin     2806 tty2   /usr/lib/ibus/ibus-engine-simple
! sysadmin     2540 tty2   /usr/lib/ibus/ibus-x11 --kill-daemon
! sysadmin     2730 tty2   nautilus-desktop
! root        14878 pts/0  /bin/sh /usr/sbin/chkrootkit -x
! root        15312 pts/0  ./chkutmp
! root        15314 pts/0  ps axk tty,ruser,args -o tty,pid,ruser,args
! root        15313 pts/0  sh -c ps axk "tty,ruser,args" -o "tty,pid,ruser,args"
! root        14877 pts/0  sudo chkrootkit -x
! sysadmin     2886 pts/0  bash
chkutmp: nothing deleted
not tested


---
© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.
