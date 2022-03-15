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

    - Command to set permissions (if needed): sudo chmod 644 /etc/passwd

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
sudo usermod -aG engineers sam
sudo usermod -aG engineers joe
sudo usermod -aG engineers amy
sudo usermod -aG engineers sara
3. Create a shared folder for this group at `/home/engineers`.

    - Command to create the shared folder:
/home$ mkdir engineers

4. Change ownership on the new engineers' shared folder to the `engineers` group.

    - Command to change ownership of engineer's shared folder to engineer group:
sudo chown :engineers engineers
### Step 4: Lynis Auditing

1. Command to install Lynis:
sudo apt install lynis

2. Command to see documentation and instructions:
man lynis

3. Command to run an audit:
sudo lynis audit system

4. Provide a report from the Lynis output on what can be done to harden the system.

    - Screenshot of report output:
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
  ! RUID          PID TTY    CMD
! gdm          2699 tty1   /usr/bin/Xwayland :1024 -rootless -terminate -accessx -core -listen 4 -listen 5 -displayfd 6
! gdm          2628 tty1   /usr/lib/gdm3/gdm-wayland-session gnome-session --autostart /usr/share/gdm/greeter/autostart
! gdm          2633 tty1   /usr/lib/gnome-session/gnome-session-binary --autostart /usr/share/gdm/greeter/autostart
! gdm          2640 tty1   /usr/bin/gnome-shell
! gdm          2791 tty1   /usr/lib/gnome-settings-daemon/gsd-a11y-settings
! gdm          2793 tty1   /usr/lib/gnome-settings-daemon/gsd-clipboard
! gdm          2794 tty1   /usr/lib/gnome-settings-daemon/gsd-color
! gdm          2796 tty1   /usr/lib/gnome-settings-daemon/gsd-datetime
! gdm          2797 tty1   /usr/lib/gnome-settings-daemon/gsd-housekeeping
! gdm          2802 tty1   /usr/lib/gnome-settings-daemon/gsd-keyboard
! gdm          2807 tty1   /usr/lib/gnome-settings-daemon/gsd-media-keys
! gdm          2811 tty1   /usr/lib/gnome-settings-daemon/gsd-mouse
! gdm          2813 tty1   /usr/lib/gnome-settings-daemon/gsd-power
! gdm          2815 tty1   /usr/lib/gnome-settings-daemon/gsd-print-notifications
! gdm          2823 tty1   /usr/lib/gnome-settings-daemon/gsd-rfkill
! gdm          2830 tty1   /usr/lib/gnome-settings-daemon/gsd-screensaver-proxy
! gdm          2841 tty1   /usr/lib/gnome-settings-daemon/gsd-sharing
! gdm          2843 tty1   /usr/lib/gnome-settings-daemon/gsd-smartcard
! gdm          2846 tty1   /usr/lib/gnome-settings-daemon/gsd-sound
! gdm          2848 tty1   /usr/lib/gnome-settings-daemon/gsd-wacom
! gdm          2788 tty1   /usr/lib/gnome-settings-daemon/gsd-xsettings
! gdm          2750 tty1   ibus-daemon --xim --panel disable
! gdm          2753 tty1   /usr/lib/ibus/ibus-dconf
! gdm          2935 tty1   /usr/lib/ibus/ibus-engine-simple
! gdm          2756 tty1   /usr/lib/ibus/ibus-x11 --kill-daemon
! sysadmin     4192 tty2   /usr/lib/xorg/Xorg vt2 -displayfd 3 -auth /run/user/1000/gdm/Xauthority -background none -noreset -keeptty -verbose 3
! sysadmin     4190 tty2   /usr/lib/gdm3/gdm-x-session --run-script env GNOME_SHELL_SESSION_MODE=ubuntu gnome-session --session=ubuntu
! sysadmin     4214 tty2   /usr/lib/gnome-session/gnome-session-binary --session=ubuntu
! sysadmin     4383 tty2   /usr/bin/gnome-shell
! sysadmin     4879 tty2   /usr/bin/gnome-software --gapplication-service
! sysadmin     4542 tty2   /usr/lib/gnome-settings-daemon/gsd-a11y-settings
! sysadmin     4543 tty2   /usr/lib/gnome-settings-daemon/gsd-clipboard
! sysadmin     4541 tty2   /usr/lib/gnome-settings-daemon/gsd-color
! sysadmin     4547 tty2   /usr/lib/gnome-settings-daemon/gsd-datetime
! sysadmin     4610 tty2   /usr/lib/gnome-disk-utility/gsd-disk-utility-notify
! sysadmin     4548 tty2   /usr/lib/gnome-settings-daemon/gsd-housekeeping
! sysadmin     4549 tty2   /usr/lib/gnome-settings-daemon/gsd-keyboard
! sysadmin     4553 tty2   /usr/lib/gnome-settings-daemon/gsd-media-keys
! sysadmin     4499 tty2   /usr/lib/gnome-settings-daemon/gsd-mouse
! sysadmin     4500 tty2   /usr/lib/gnome-settings-daemon/gsd-power
! sysadmin     4504 tty2   /usr/lib/gnome-settings-daemon/gsd-print-notifications
! sysadmin     4569 tty2   /usr/lib/gnome-settings-daemon/gsd-printer
! sysadmin     4505 tty2   /usr/lib/gnome-settings-daemon/gsd-rfkill
! sysadmin     4508 tty2   /usr/lib/gnome-settings-daemon/gsd-screensaver-proxy
! sysadmin     4511 tty2   /usr/lib/gnome-settings-daemon/gsd-sharing
! sysadmin     4515 tty2   /usr/lib/gnome-settings-daemon/gsd-smartcard
! sysadmin     4517 tty2   /usr/lib/gnome-settings-daemon/gsd-sound
! sysadmin     4527 tty2   /usr/lib/gnome-settings-daemon/gsd-wacom
! sysadmin     4528 tty2   /usr/lib/gnome-settings-daemon/gsd-xsettings
! sysadmin     4418 tty2   ibus-daemon --xim --panel disable
! sysadmin     4422 tty2   /usr/lib/ibus/ibus-dconf
! sysadmin     4728 tty2   /usr/lib/ibus/ibus-engine-simple
! sysadmin     4425 tty2   /usr/lib/ibus/ibus-x11 --kill-daemon
! sysadmin     4607 tty2   nautilus-desktop
! root        19539 pts/0  /bin/sh /usr/sbin/chkrootkit -x
! root        20036 pts/0  ./chkutmp
! root        20038 pts/0  ps axk tty,ruser,args -o tty,pid,ruser,args
! root        20037 pts/0  sh -c ps axk "tty,ruser,args" -o "tty,pid,ruser,args"
! root        19538 pts/0  sudo chkrootkit -x
! sysadmin     4839 pts/0  bash
chkutmp: nothing deleted
not tested

