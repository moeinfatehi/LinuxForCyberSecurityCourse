### Lecture 01: History of Linux

1. **Who launched the GNU Project in 1983?**
   - A) Linus Torvalds
   - B) Ken Thompson
   - **C) Richard Stallman**
   - D) Dennis Ritchie

2. **What is the official mascot of Linux?**
   - **A) A penguin named Tux**
   - B) A fox
   - C) A dragon
   - D) An eagle

### Lecture 02: Philosophy of Free Software

3. **Which of the following is one of the four essential freedoms defined by the Free Software Foundation?**
   - **A) The freedom to use the software for any purpose**
   - B) The freedom to sell the software for a profit
   - C) The freedom to keep the source code private
   - D) The freedom to restrict access to the software

4. **What year was the Free Software Foundation (FSF) established?**
   - A) 1983
   - **B) 1985**
   - C) 1991
   - D) 2000

### Lecture 03: Overview of Linux Distributions

5. **Which component of a Linux distribution is responsible for managing hardware resources?**
   - A) System Libraries
   - **B) Linux Kernel**
   - C) Application Software
   - D) Graphical User Interface (GUI)

6. **What is the main purpose of a package manager in a Linux distribution?**
   - A) To provide a graphical user interface
   - B) To manage hardware resources
   - **C) To automate the process of installing, updating, and removing software packages**
   - D) To perform file management tasks

7. **Which Linux distribution is specifically designed for security testing and penetration testing?**
   - A) Ubuntu
   - B) Fedora
   - C) Debian
   - **D) Kali Linux**

### Lecture 04: Real-World Applications of Linux

8. **Which sector primarily uses Linux for its stability, security, and lower total cost of ownership?**
   - A) Desktop Computing
   - **B) Enterprise Servers**
   - C) Gaming
   - D) Graphic Design

9. **Why is Linux the operating system of choice for supercomputers?**
   - A) Because of its graphical user interface
   - **B) Due to its scalability and flexibility**
   - C) Because it is proprietary software
   - D) Due to its high cost

10. **Which Linux distribution is known for being user-friendly and is popular among developers and technical professionals for personal use?**
   - A) Debian
   - B) Fedora
   - **C) Ubuntu**
   - D) CentOS


## Topic2
### Lecture 01: Installing Ubuntu

11. **What tool can be used to create a bootable USB drive for installing Ubuntu?**
    - A) Notepad
    - **B) Rufus**
    - C) Microsoft Word
    - D) Adobe Photoshop

12. **What command is used to update Ubuntu to the latest package versions after installation?**
    - A) `sudo yum update && sudo yum upgrade`
    - B) `sudo apt-get update && sudo apt-get install`
    - **C) `sudo apt update && sudo apt upgrade`**
    - D) `sudo dnf update && sudo dnf upgrade`

### Lecture 02: Understanding Linux Architecture

13. **What is the main role of the kernel in Linux architecture?**
    - A) Managing user interfaces
    - **B) Managing system resources and hardware communication**
    - C) Managing application software
    - D) Managing file systems

14. **Which layer in the Linux architecture acts as a command interpreter?**
    - A) Kernel
    - **B) Shell**
    - C) System Libraries
    - D) User Interface

15. **What is the primary function of system libraries in Linux?**
    - A) Managing hardware resources
    - **B) Providing functions for programs to perform specific operations**
    - C) Interpreting user commands
    - D) Managing network operations

### Lecture 03: Secure Installation Practices

16. **What is the recommended practice for managing the root account during installation?**
    - A) Enable root login
    - **B) Disable root login and use `sudo` for administrative tasks**
    - C) Use root login for all tasks
    - D) Create multiple root accounts

17. **Which security feature provides additional layers of security by defining access controls in Linux?**
    - **A) SELinux (Security-Enhanced Linux)**
    - B) Firewall
    - C) Cron
    - D) Swap

### Lecture 04: Understanding the Linux Filesystem Hierarchy

18. **Which directory contains essential user binaries that must be available when the system is in single-user mode?**
    - A) /etc
    - B) /home
    - **C) /bin**
    - D) /usr

19. **Where are the home directories for users typically located in the Linux filesystem?**
    - A) /root
    - B) /bin
    - **C) /home**
    - D) /usr

20. **What type of files are stored in the /var directory?**
    - A) Static boot files
    - **B) Variable data that changes as the system runs**
    - C) Device files
    - D) System libraries

21. **Which directory is used for mounting temporary filesystems?**
    - **A) /mnt**
    - B) /var
    - C) /opt
    - D) /dev

22. **What is stored in the /boot directory?**
    - A) User data
    - **B) Static boot files needed to boot the system**
    - C) Temporary files
    - D) Device files

23. **Which directory contains configuration files specific to the system?**
    - **A) /etc**
    - B) /bin
    - C) /dev
    - D) /opt

24. **Where are the device files located in the Linux filesystem?**
    - A) /bin
    - **B) /dev**
    - C) /lib
    - D) /sbin

## Topic3
### Lecture 01: Basic to Advanced Command Line Operations

25. **What command is used to display the current directory path?**
    - **A) `pwd`**
    - B) `cd`
    - C) `ls`
    - D) `mkdir`

26. **Which option with the `ls` command lists all files, including hidden files?**
    - A) `-l`
    - **B) `-a`**
    - C) `-r`
    - D) `-t`

27. **What is the function of the `grep` command?**
    - A) Copy files
    - B) Move files
    - **C) Search for patterns within files**
    - D) Delete files

### Lecture 02: File and Directory Management

28. **Which command creates a directory and all necessary parent directories?**
    - **A) `mkdir -p`**
    - B) `mkdir -r`
    - C) `mkdir -m`
    - D) `mkdir -t`

29. **What does the `cp -u` command do?**
    - A) Copies files unconditionally
    - **B) Copies files only when the source file is newer than the destination file**
    - C) Copies files and updates their timestamps
    - D) Copies files and removes the original

30. **What does `chmod 755 filename` do?**
    - A) Sets the file to be read, write, and execute for everyone
    - **B) Sets the file to be read, write, and execute for the owner, and read and execute for the group and others**
    - C) Sets the file to be read and write for the owner, and read only for the group and others
    - D) Sets the file to be read and execute for everyone

### Lecture 03: Introduction to Shell Scripting for Automating Tasks

31. **What symbol is used to start a comment in a shell script?**
    - **A) `#`**
    - B) `//`
    - C) `;`
    - D) `/* */`

32. **How do you make a shell script executable?**
    - A) Use the `cp` command
    - B) Use the `mv` command
    - **C) Use the `chmod +x` command**
    - D) Use the `ls -l` command

33. **What does the following `for` loop do?**
    ```bash
    for i in 1 2 3; do
      echo "Looping ... number $i"
    done
    ```
    - A) Prints "Looping ... number" three times
    - **B) Prints "Looping ... number 1", "Looping ... number 2", and "Looping ... number 3"**
    - C) Prints "Looping ... number" six times
    - D) Prints "Looping ... number 123"

34. **Which command is used to include and execute the contents of another script within the current script?**
    - A) `export`
    - **B) `source`**
    - C) `subshell`
    - D) `link`

35. **How do you schedule a script to run at specific times using cron?**
    - A) Use the `at` command
    - B) Use the `chmod` command
    - **C) Use the `crontab -e` command**
    - D) Use the `nano` command


### Topic 5: Networking and Firewalls

#### Lecture 01: Networking Basics and Advanced Configuration

36. **What command is used to view all network interfaces and their status?**
    - A) `ifconfig`
    - **B) `ip link show`**
    - C) `netstat`
    - D) `ping`

37. **Which file is typically used to configure DNS settings in Linux?**
    - A) `/etc/hosts`
    - **B) `/etc/resolv.conf`**
    - C) `/etc/network/interfaces`
    - D) `/etc/dns.conf`

38. **What command is used to assign an IP address to an interface using the `ip` command?**
    - A) `ip link set`
    - **B) `ip addr add`**
    - C) `ip route add`
    - D) `ip config set`

#### Lecture 02: Configuring and Securing Firewalls

39. **Which command lists all active rules in iptables?**
    - A) `iptables -A`
    - **B) `iptables -L`**
    - C) `iptables -D`
    - D) `iptables -N`

40. **What command is used to allow SSH connections on port 22 using iptables?**
    - A) `iptables -A OUTPUT -p tcp --dport 22 -j ACCEPT`
    - **B) `iptables -A INPUT -p tcp --dport 22 -j ACCEPT`**
    - C) `iptables -A FORWARD -p tcp --dport 22 -j ACCEPT`
    - D) `iptables -A PREROUTING -p tcp --dport 22 -j ACCEPT`

41. **Which command installs firewalld on an Ubuntu system?**
    - **A) `sudo apt-get install firewalld`**
    - B) `sudo yum install firewalld`
    - C) `sudo dnf install firewalld`
    - D) `sudo pacman -S firewalld`

#### Lecture 03: Setting Up Secure Remote Connections

42. **Which file should be edited to change SSH server settings?**
    - A) `/etc/ssh/ssh_config`
    - **B) `/etc/ssh/sshd_config`**
    - C) `/etc/ssh/ssh.conf`
    - D) `/etc/ssh/sshd.conf`

43. **How do you disable root login via SSH?**
    - A) `PermitRootLogin yes`
    - **B) `PermitRootLogin no`**
    - C) `DisableRootLogin yes`
    - D) `DisableRootLogin no`

44. **What command is used to restart the SSH service after making configuration changes?**
    - A) `sudo systemctl reload sshd`
    - **B) `sudo systemctl restart sshd`**
    - C) `sudo systemctl stop sshd`
    - D) `sudo systemctl start sshd`

### Topic 6: User and Permission Management

#### Lecture 01: User and Group Management Strategies

45. **Which command is used to create a new user with a home directory and default shell in Linux?**
    - **A) `sudo useradd -m -s /bin/bash username`**
    - B) `sudo adduser -d /home/username -s /bin/bash username`
    - C) `sudo newuser -m -d /home/username -s /bin/bash username`
    - D) `sudo createuser -m -s /bin/bash username`

46. **What command modifies an existing user account to change the username?**
    - A) `sudo useradd -l newusername username`
    - **B) `sudo usermod -l newusername username`**
    - C) `sudo modifyuser -l newusername username`
    - D) `sudo chuser -l newusername username`

47. **Which command deletes a user account and removes their home directory?**
    - **A) `sudo userdel -r username`**
    - B) `sudo deluser -r username`
    - C) `sudo removeuser -r username`
    - D) `sudo deleteuser -r username`

#### Lecture 02: Implementing and Managing File Permissions

48. **What does the permission string `-rw-r--r--` signify?**
    - A) The owner can read, write, and execute; the group can read and write; others can read
    - B) The owner can read and write; the group can read and write; others can read
    - **C) The owner can read and write; the group can read; others can read**
    - D) The owner can read and write; the group can read; others can read and write

49. **Which command adds execute permission for the owner of a file using symbolic notation?**
    - A) `chmod o+x filename`
    - B) `chmod g+x filename`
    - **C) `chmod u+x filename`**
    - D) `chmod a+x filename`

50. **How do you set the permissions of a file to `rwxr-xr--` using numeric notation?**
    - A) `chmod 764 filename`
    - **B) `chmod 754 filename`**
    - C) `chmod 744 filename`
    - D) `chmod 7444 filename`

#### Lecture 03: Secure Configuration of Sudo and User Privileges

51. **Which command should be used to safely edit the sudoers file?**
    - A) `sudo nano /etc/sudoers`
    - B) `sudo vim /etc/sudoers`
    - **C) `sudo visudo`**
    - D) `sudo edit /etc/sudoers`

52. **What is the purpose of the `NOPASSWD` directive in the sudoers file?**
    - A) To disable sudo for the specified user
    - **B) To allow the specified user to run sudo commands without a password prompt**
    - C) To require a password for the specified user
    - D) To log all sudo commands executed by the specified user

53. **How can you grant a specific user the ability to restart the Apache service using sudo without a password prompt?**
    - A) `username ALL=(ALL) NOPASSWD: /usr/bin/systemctl restart apache2`
    - **B) `username ALL=(ALL) NOPASSWD: /usr/bin/systemctl restart apache2`**
    - C) `username ALL=(ALL) PASSWD: /usr/bin/systemctl restart apache2`
    - D) `username ALL=(ALL) /usr/bin/systemctl restart apache2`


### Topic 7: Package and Software Management

#### Lecture 01: Introduction to Package Management

54. **Which package manager is used in Debian-based distributions like Ubuntu?**
    - A) RPM
    - **B) APT**
    - C) YUM
    - D) Pacman

55. **What is one of the main benefits of using a package manager?**
    - A) Manual handling of software updates
    - **B) Automatic dependency resolution**
    - C) Increased software costs
    - D) Manual configuration of software

#### Lecture 02: Managing Packages with APT

56. **What command updates the package list in APT?**
    - A) `sudo apt-get upgrade`
    - **B) `sudo apt-get update`**
    - C) `sudo apt-get install`
    - D) `sudo apt-get remove`

57. **Which command installs multiple packages in APT?**
    - A) `sudo apt-get add`
    - **B) `sudo apt-get install package1 package2`**
    - C) `sudo apt-get update`
    - D) `sudo apt-get purge`

#### Lecture 03: Managing Packages with RPM

58. **What command installs a package using RPM?**
    - A) `sudo rpm -e package`
    - B) `sudo rpm -q package`
    - **C) `sudo rpm -i package.rpm`**
    - D) `sudo rpm -u package`

59. **What is the purpose of the `yum` command in Red Hat-based distributions?**
    - A) To compile software from source
    - B) To update the kernel
    - **C) To handle package management and dependencies**
    - D) To manage user accounts

#### Lecture 04: Installing Software from Source

60. **Which command is used to compile source code into binaries?**
    - A) `configure`
    - B) `install`
    - **C) `make`**
    - D) `extract`

61. **What is the first step in installing software from source?**
    - **A) Download the source code**
    - B) Run the `make` command
    - C) Install dependencies
    - D) Configure the build

#### Lecture 05: Secure and Up-to-Date Software Environments

62. **What command enables automatic updates on Debian-based systems?**
    - A) `sudo apt-get install auto-updates`
    - **B) `sudo apt-get install unattended-upgrades`**
    - C) `sudo apt-get auto-upgrade`
    - D) `sudo apt-get enable updates`

63. **Which tool can verify the integrity of RPM packages?**
    - A) `dpkg`
    - **B) `rpm --checksig`**
    - C) `yum`
    - D) `apt-get check`

### Topic 8: Scheduled Tasks and Process Management

#### Lecture 01: Configuring Cron Jobs and At Tasks

64. **What is the purpose of the cron daemon (`crond`)?**
    - A) To manage user sessions
    - **B) To execute scheduled tasks at specified times**
    - C) To compile software
    - D) To manage network connections

65. **Which command lists all cron jobs for the current user?**
    - **A) `crontab -l`**
    - B) `crontab -e`
    - C) `crontab -r`
    - D) `cron -list`

66. **What special string in cron schedules a job to run once a year?**
    - A) `@weekly`
    - B) `@daily`
    - **C) `@yearly`**
    - D) `@hourly`

67. **How do you schedule a one-time task with the `at` command for 3 PM today?**
    - A) `echo "command" | at 3pm tomorrow`
    - **B) `echo "command" | at 3pm`**
    - C) `echo "command" | at 15:00`
    - D) `echo "command" | at now + 3 hours`

#### Lecture 02: Managing Processes with ps, top, htop, and kill

68. **What is the state of a process in Linux when it is waiting for I/O?**
   - A) R (Running)
   - B) S (Sleeping)
   - **C) D (Uninterruptible Sleep)**
   - D) T (Stopped)

69. **Which command provides a snapshot of current processes in Linux?**
   - **A) ps**
   - B) top
   - C) htop
   - D) kill

70. **What interactive command in `top` is used to kill a process?**
   - A) r
   - **B) k**
   - C) q
   - D) h

71. **Which command is an enhanced, interactive process viewer that offers a more user-friendly interface than `top`?**
   - A) ps
   - **B) htop**
   - C) kill
   - D) pkill

72. **Which signal does `kill -SIGTERM` send to a process?**
   - A) Forcefully terminate the process
   - **B) Gracefully terminate the process**
   - C) Reload the process
   - D) Pause the process

73. **What is the priority range that can be assigned to a process using the `nice` command?**
   - A) -10 to 10
   - B) 0 to 100
   - **C) -20 to 19**
   - D) 1 to 100

74. **What command is used to change the priority of an already running process?**
   - A) nice
   - **B) renice**
   - C) kill
   - D) htop

### Topic 9: System Monitoring and Logs

#### Lecture 01: Understanding System Monitoring Tools

75. **Which package provides a collection of performance monitoring tools, including `iostat`, `mpstat`, and `sar`?**
   - A) `net-tools`
   - **B) `sysstat`**
   - C) `nload`
   - D) `vmstat`

76. **What command provides statistics on CPU usage and I/O operations for devices and partitions?**
   - A) `mpstat`
   - **B) `iostat`**
   - C) `iftop`
   - D) `sar`

77. **Which command displays memory usage, including total, used, free, and swap memory, in a human-readable format?**
   - A) `vmstat`
   - **B) `free -h`**
   - C) `dstat`
   - D) `iftop`

78. **What is the function of the `mpstat` command in Linux?**
   - **A) Report CPU usage for each processor or core**
   - B) Display memory usage
   - C) Monitor disk I/O statistics
   - D) Monitor network traffic

79. **Which tool provides real-time network bandwidth usage on a network interface?**
   - A) `sar`
   - B) `vmstat`
   - **C) `iftop`**
   - D) `mpstat`

80. **What command is used to monitor system performance, including CPU, memory, and I/O, every 2 seconds?**
   - A) `iostat 2`
   - B) `mpstat 2`
   - **C) `vmstat 2`**
   - D) `dstat 2`


#### Lecture 02: Log Management with syslog and logrotate

81. **Which tool is widely used to centralize log messages from various services in Linux?**
   - A) logrotate
   - B) journald
   - **C) syslog**
   - D) dmesg

82. **What is the purpose of the `logrotate` utility in Linux?**
   - A) Collect system statistics
   - **B) Rotate, compress, and remove old log files**
   - C) Monitor running processes
   - D) Manage network traffic

83. **Which syslog severity level indicates a critical condition that needs immediate attention?**
   - A) debug
   - **B) crit**
   - C) notice
   - D) info

84. **What is the default configuration file for `rsyslog` on most Linux distributions?**
   - A) `/var/log/messages`
   - **B) `/etc/rsyslog.conf`**
   - C) `/etc/logrotate.conf`
   - D) `/usr/bin/rsyslog`

85. **What is the purpose of the `postrotate` script in a `logrotate` configuration?**
   - A) Create new log files
   - **B) Reload services after log rotation**
   - C) Compress log files
   - D) Remove old log files

86. **How do you specify size-based log rotation using `logrotate`?**
   - A) daily
   - **B) size 100M**
   - C) compress
   - D) rotate 7


#### Lecture 03: Analyzing and Searching Logs

87. **Which command is commonly used to search for patterns within log files?**
   - A) sed
   - **B) grep**
   - C) awk
   - D) journalctl

88. **What does the `-r` option do when used with the `grep` command?**
   - A) Show line numbers
   - B) Show lines after the matching pattern
   - **C) Search recursively through directories**
   - D) Ignore case distinctions

89. **What is the purpose of the `awk` command in log analysis?**
   - A) Edit text streams
   - **B) Process and analyze text based on patterns**
   - C) Filter and transform text
   - D) Search for text patterns

90. **Which command is used to view logs generated by `systemd`?**
   - A) grep
   - B) sed
   - **C) journalctl**
   - D) awk

91. **How can you display logs for the `sshd` service using `journalctl`?**
   - A) `journalctl -p sshd`
   - **B) `journalctl -u sshd`**
   - C) `journalctl --service sshd`
   - D) `journalctl --show sshd`

92. **What is the use of the `sed` command in log management?**
   - **A) Perform text transformations on log files**
   - B) Search for patterns in logs
   - C) Count occurrences of log entries
   - D) Monitor real-time log activity

93. **Which `journalctl` option displays only error messages in the log?**
   - **A) `-p err`**
   - B) `-u error`
   - C) `-l error`
   - D) `--errors-only`


### Topic 10: Linux Hardening and Network Security

#### Lecture 01: Introduction to Linux Security Fundamentals

94. **What is the principle of least privilege in Linux security?**
   - A) Granting all users full access to system resources
   - B) Restricting user access to only the resources necessary for their role
   - **C) Providing minimal access needed to perform tasks**
   - D) Allowing users unrestricted access

95. **Which of the following is a layered security approach?**
   - A) Disabling unused services
   - **B) Defense in Depth**
   - C) Full-disk encryption
   - D) Enabling firewall rules

96. **What command can be used to monitor authentication logs?**
   - **A) `cat /var/log/auth.log`**
   - B) `sudo auditctl`
   - C) `netstat`
   - D) `systemctl logs`


#### Lecture 02: System Hardening Strategies

97. **Which command is used to disable a service on a Linux system?**
   - **A) `systemctl disable service_name`**
   - B) `sudo service enable`
   - C) `sudo firewall disable`
   - D) `iptables -disable`

98. **What is the main purpose of key-based SSH authentication?**
   - A) Using a password for remote access
   - **B) Securing remote access with an SSH key pair**
   - C) Enabling root login
   - D) Disabling user accounts

99. **Which security measure can be implemented to prevent brute force attacks on SSH?**
   - A) Disabling SSH
   - B) Changing the SSH port
   - **C) Implementing Two-Factor Authentication (2FA)**
   - D) Allowing root login


#### Lecture 03: Filesystem and Data Encryption

100. **What is the main function of LUKS in Linux?**
   - A) Managing firewall rules
   - **B) Encrypting partitions and disks**
   - C) Configuring network interfaces
   - D) Monitoring system logs

101. **Which command is used to format a partition for LUKS encryption?**
   - A) `luksOpen`
   - B) `luksAddKey`
   - **C) `cryptsetup luksFormat`**
   - D) `fdisk luksFormat`

102. **How can encrypted swap space be enabled temporarily in Linux?**
   - A) Use an encrypted file
   - **B) Encrypt swap with a random key at each reboot**
   - C) Disable the swap space entirely
   - D) Use the `logrotate` command


#### Lecture 04: Basic Network Security

103. **Which command is used to check active network services?**
   - A) `sshd`
   - **B) `netstat -tuln`**
   - C) `iptables -l`
   - D) `ps aux`

104. **What is the function of `iptables` in Linux?**
   - A) Managing system services
   - **B) Controlling network traffic with firewall rules**
   - C) Monitoring network bandwidth
   - D) Encrypting network packets

105. **Which tool is used to scan a network for open ports and services?**
   - **A) `nmap`**
   - B) `iftop`
   - C) `iptables`
   - D) `auditd`

#### Lecture 05: Introduction to Security Tools and Best Practices

106. **What is the purpose of the `auditd` tool in Linux?**
   - A) Perform network scans
   - **B) Track and log security-related system activity**
   - C) Manage firewall rules
   - D) Encrypt files and directories

107. **Which tool can be used for file integrity monitoring in Linux?**
   - A) `auditd`
   - **B) `AIDE`**
   - C) `tcpdump`
   - D) `nmap`

108. **Which intrusion prevention tool blocks brute force attacks based on failed login attempts?**
   - A) `Snort`
   - **B) `fail2ban`**
   - C) `iptables`
   - D) `auditd`

109. **Which tool is commonly used for network intrusion detection in Linux?**
   - **A) `Snort`**
   - B) `Metasploit`
   - C) `nmap`
   - D) `Nikto`


#### Lecture 06: Practical Security Enhancements

110. **Which command is used to secure log directories by restricting access?**
   - A) `ufw allow logs`
   - B) `chmod 777 /var/log`
   - **C) `chmod 700 /var/log`**
   - D) `auditctl -w /var/log`

111. **What is the purpose of centralized logging in Linux?**
   - **A) To send logs from multiple systems to a central log server**
   - B) To encrypt log files
   - C) To rotate logs automatically
   - D) To delete old log files

112. **Which command can be used to monitor recent user logins on a Linux system?**
   - A) `ps aux`
   - **B) `last`**
   - C) `uptime`
   - D) `journalctl -u sshd`

113. **Which practice helps protect databases from unauthorized access?**
   - A) Allowing root access for all users
   - **B) Binding the database service to localhost**
   - C) Allowing all IP addresses to access the database
   - D) Disabling SSL encryption for database connections
