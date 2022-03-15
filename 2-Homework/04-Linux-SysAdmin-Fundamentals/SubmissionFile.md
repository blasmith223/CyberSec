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

    - Command to add `admin` to the `sudo` group: sudo usermod -aG sudo admin

### Step 3: Create User Group and Collaborative Folder

1. Add an `engineers` group to the system.

    - Command to add group: sudo addgroup engineers

2. Add users `sam`, `joe`, `amy`, and `sara` to the managed group.

    - Command to add users to `engineers` group (include all four users):
    sudo usermod -aG engineers sam 
    sudo usermod -aG engineers joe
    sudo usermod -aG engineers amy
    sudo usermod -aG engineers sara
    
3. Create a shared folder for this group at `/home/engineers`.

    - Command to create the shared folder: 
    /home$ sudo mkdir engineers

4. Change ownership on the new engineers' shared folder to the `engineers` group.

    - Command to change ownership of engineer's shared folder to engineer group: 
    sudo chown :engineers engineers

### Step 4: Lynis Auditing

1. Command to install Lynis: sudo apt install lynis

2. Command to see documentation and instructions: man lynis

3. Command to run an audit: sudo lynis aduit system

4. Provide a report from the Lynis output on what can be done to harden the system.

    - Screenshot of report output:
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



### Bonus
1. Command to install chkrootkit: sudo apt install chkrootkit

2. Command to see documentation and instructions: man chkrootkit

3. Command to run expert mode: sudo chkrootkit -x

4. Provide a report from the chrootkit output on what can be done to harden the system.
    - Screenshot of end of sample output:
###
### Output of: ./ifpromisc
###
lo: not promisc and no packet sniffer sockets
enp0s3: PACKET SNIFFER(/sbin/dhclient[1232])
docker0: not promisc and no packet sniffer sockets
not infected
###
### Output of: ./chkwtmp -f /var/log/wtmp
###
not infected
not infected
###
### Output of: ./chklastlog  -f /var/log/wtmp -l /var/log/lastlog
###
 The tty of the following user process(es) were not found
 in /var/run/utmp !
! RUID          PID TTY    CMD
! gdm          2186 tty1   /usr/bin/Xwayland :1024 -rootless -terminate -accessx -core -listen 4 -listen 5 -displayfd 6
! gdm          2135 tty1   /usr/lib/gdm3/gdm-wayland-session gnome-session --autostart /usr/share/gdm/greeter/autostart
! gdm          2140 tty1   /usr/lib/gnome-session/gnome-session-binary --autostart /usr/share/gdm/greeter/autostart
! gdm          2148 tty1   /usr/bin/gnome-shell
! gdm          2291 tty1   /usr/lib/gnome-settings-daemon/gsd-a11y-settings
! gdm          2293 tty1   /usr/lib/gnome-settings-daemon/gsd-clipboard
! gdm          2295 tty1   /usr/lib/gnome-settings-daemon/gsd-color
! gdm          2299 tty1   /usr/lib/gnome-settings-daemon/gsd-datetime
! gdm          2301 tty1   /usr/lib/gnome-settings-daemon/gsd-housekeeping
! gdm          2302 tty1   /usr/lib/gnome-settings-daemon/gsd-keyboard
! gdm          2304 tty1   /usr/lib/gnome-settings-daemon/gsd-media-keys
! gdm          2306 tty1   /usr/lib/gnome-settings-daemon/gsd-mouse
! gdm          2313 tty1   /usr/lib/gnome-settings-daemon/gsd-power
! gdm          2322 tty1   /usr/lib/gnome-settings-daemon/gsd-print-notifications
! gdm          2326 tty1   /usr/lib/gnome-settings-daemon/gsd-rfkill
! gdm          2339 tty1   /usr/lib/gnome-settings-daemon/gsd-screensaver-proxy
! gdm          2342 tty1   /usr/lib/gnome-settings-daemon/gsd-sharing
! gdm          2347 tty1   /usr/lib/gnome-settings-daemon/gsd-smartcard
! gdm          2355 tty1   /usr/lib/gnome-settings-daemon/gsd-sound
! gdm          2359 tty1   /usr/lib/gnome-settings-daemon/gsd-wacom
! gdm          2290 tty1   /usr/lib/gnome-settings-daemon/gsd-xsettings
! gdm          2247 tty1   ibus-daemon --xim --panel disable
! gdm          2250 tty1   /usr/lib/ibus/ibus-dconf
! gdm          2416 tty1   /usr/lib/ibus/ibus-engine-simple
! gdm          2253 tty1   /usr/lib/ibus/ibus-x11 --kill-daemon
! sysadmin     2572 tty2   /usr/lib/xorg/Xorg vt2 -displayfd 3 -auth /run/user/1000/gdm/Xauthority -background none -noreset -keeptty -verbose 3
! sysadmin     2570 tty2   /usr/lib/gdm3/gdm-x-session --run-script env GNOME_SHELL_SESSION_MODE=ubuntu gnome-session --session=ubuntu
! sysadmin     2594 tty2   /usr/lib/gnome-session/gnome-session-binary --session=ubuntu
! sysadmin     2763 tty2   /usr/bin/gnome-shell
! sysadmin     3229 tty2   /usr/bin/gnome-software --gapplication-service
! sysadmin     2930 tty2   /usr/lib/gnome-settings-daemon/gsd-a11y-settings
! sysadmin     2931 tty2   /usr/lib/gnome-settings-daemon/gsd-clipboard
! sysadmin     2928 tty2   /usr/lib/gnome-settings-daemon/gsd-color
! sysadmin     2936 tty2   /usr/lib/gnome-settings-daemon/gsd-datetime
! sysadmin     3036 tty2   /usr/lib/gnome-disk-utility/gsd-disk-utility-notify
! sysadmin     2937 tty2   /usr/lib/gnome-settings-daemon/gsd-housekeeping
! sysadmin     2938 tty2   /usr/lib/gnome-settings-daemon/gsd-keyboard
! sysadmin     2946 tty2   /usr/lib/gnome-settings-daemon/gsd-media-keys
! sysadmin     2885 tty2   /usr/lib/gnome-settings-daemon/gsd-mouse
! sysadmin     2886 tty2   /usr/lib/gnome-settings-daemon/gsd-power
! sysadmin     2890 tty2   /usr/lib/gnome-settings-daemon/gsd-print-notifications
! sysadmin     2990 tty2   /usr/lib/gnome-settings-daemon/gsd-printer
! sysadmin     2895 tty2   /usr/lib/gnome-settings-daemon/gsd-rfkill
! sysadmin     2896 tty2   /usr/lib/gnome-settings-daemon/gsd-screensaver-proxy
! sysadmin     2901 tty2   /usr/lib/gnome-settings-daemon/gsd-sharing
! sysadmin     2908 tty2   /usr/lib/gnome-settings-daemon/gsd-smartcard
! sysadmin     2911 tty2   /usr/lib/gnome-settings-daemon/gsd-sound
! sysadmin     2914 tty2   /usr/lib/gnome-settings-daemon/gsd-wacom
! sysadmin     2918 tty2   /usr/lib/gnome-settings-daemon/gsd-xsettings
! sysadmin     2798 tty2   ibus-daemon --xim --panel disable
! sysadmin     2802 tty2   /usr/lib/ibus/ibus-dconf
! sysadmin     3102 tty2   /usr/lib/ibus/ibus-engine-simple
! sysadmin     2806 tty2   /usr/lib/ibus/ibus-x11 --kill-daemon
! sysadmin     3014 tty2   nautilus-desktop
! root        15805 pts/0  /bin/sh /usr/sbin/chkrootkit -x
! root        16240 pts/0  ./chkutmp
! root        16242 pts/0  ps axk tty,ruser,args -o tty,pid,ruser,args
! root        16241 pts/0  sh -c ps axk "tty,ruser,args" -o "tty,pid,ruser,args"
! root        15804 pts/0  sudo chkrootkit -x
! sysadmin     3221 pts/0  bash
chkutmp: nothing deleted
not tested

---
© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.
