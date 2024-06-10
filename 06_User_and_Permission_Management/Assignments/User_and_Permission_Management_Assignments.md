# User and Permission Management - Assignments

## Assignment 1: Basic User and Group Management

### Objective
Demonstrate your ability to create and manage user accounts and groups in Linux.

### Tasks
1. Create a new user account named `johndoe` with a home directory and a default shell of `/bin/bash`.
2. Add the user `johndoe` to a new group named `developers`.
3. Change the username `johndoe` to `johnsmith`.
4. Delete the user `johnsmith` and ensure their home directory is removed.

### Commands
```bash
sudo useradd -m -s /bin/bash johndoe
sudo groupadd developers
sudo usermod -aG developers johndoe
sudo usermod -l johnsmith johndoe
sudo userdel -r johnsmith
```

## Assignment 2: File Permissions Management

### Objective
Manage file permissions to ensure proper access control.

### Tasks
1. Create a file named `example.txt` in your home directory.
2. Set the file permissions so that the owner can read and write, the group can read, and others have no permissions.
3. Add the setgid bit to a directory named `shared` to ensure new files inherit the group.
4. Set an ACL on `example.txt` to grant read permission to a user named `alice`.

### Commands
```bash
touch ~/example.txt
chmod 640 ~/example.txt
mkdir ~/shared
chmod g+s ~/shared
setfacl -m u:alice:r ~/example.txt
```

## Assignment 3: Advanced Permissions and ACLs

### Objective
Utilize advanced file permissions and Access Control Lists (ACLs) for fine-grained access control.

### Tasks
1. Create a directory named `project` and set the sticky bit so that only file owners can delete their files.
2. Set a default ACL on the `project` directory so that all new files are readable by the group `developers`.
3. Verify the ACL settings on the `project` directory and a new file created within it.

### Commands
```bash
mkdir ~/project
chmod +t ~/project
setfacl -d -m g:developers:r ~/project
getfacl ~/project
touch ~/project/newfile.txt
getfacl ~/project/newfile.txt
```

## Assignment 4: Configuring Sudo

### Objective
Configure sudo privileges to allow secure and controlled command execution.

### Tasks
1. Grant the user `adminuser` full sudo privileges.
2. Allow the group `developers` to restart the Apache service without a password prompt.
3. Restrict the user `limiteduser` to only run the `systemctl restart apache2` command with sudo.

### Commands
```bash
sudo visudo
```
- Add the following lines:
  ```plaintext
  adminuser ALL=(ALL:ALL) ALL
  %developers ALL=(ALL) NOPASSWD: /usr/bin/systemctl restart apache2
  limiteduser ALL=(ALL) /usr/bin/systemctl restart apache2
  ```

## Submission Guidelines

Submit a report documenting the commands used for each task, the output, and screenshots where applicable. Provide explanations for each command and the purpose of the settings configured.