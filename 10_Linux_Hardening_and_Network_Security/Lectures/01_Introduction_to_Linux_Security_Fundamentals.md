# Introduction to Linux Security Fundamentals

Linux security is essential for maintaining the integrity, confidentiality, and availability of systems and data. This lecture provides an overview of fundamental security concepts and introduces the basic security features in Linux.

## 1. Basic Security Concepts

### 1.1 The Importance of Security in Linux

Linux is known for its strong security model, but no system is inherently secure without proper configurations. Understanding the core principles of security helps mitigate risks and protect against common threats like unauthorized access, malware, and data breaches.

### 1.2 Common Threats and Vulnerabilities

- **Unauthorized Access**: Users gaining access to data or systems without proper permissions.
- **Privilege Escalation**: Exploiting a vulnerability to gain higher-level privileges.
- **Malware and Ransomware**: Malicious software designed to disrupt operations or steal data.
- **Social Engineering Attacks**: Attacks that trick users into giving away sensitive information.

### 1.3 The Principle of Least Privilege

The principle of least privilege is a security best practice that involves giving users and processes the minimal level of access necessary to perform their tasks. This reduces the risk of accidental or malicious changes to the system.

### 1.4 Defense in Depth

Defense in depth is a layered security approach where multiple defensive mechanisms are implemented, ensuring that if one layer is breached, others can still protect the system. Examples include using firewalls, intrusion detection systems, and regular patching.

## 2. Security Features in Linux

Linux offers several built-in security features that help protect the system and data:

### 2.1 User and File Permissions

Linux implements a robust permission system to control access to files and directories. Every file has three levels of access:
- **Owner**: The user who owns the file.
- **Group**: The group associated with the file.
- **Others**: All other users.

Each level has three types of permissions:
- **Read (r)**: Permission to read the file.
- **Write (w)**: Permission to modify the file.
- **Execute (x)**: Permission to execute the file as a program.

#### Example: Setting File Permissions

```bash
chmod 750 script.sh
```
- This command sets the permissions of `script.sh` to `rwxr-x---`, meaning the owner can read, write, and execute, the group can read and execute, and others have no access.

### 2.2 Introduction to SELinux and AppArmor

- **SELinux (Security-Enhanced Linux)**: A security module that provides a mechanism for enforcing access control policies. It can be used to restrict the actions that processes can perform, reducing the impact of security breaches.
- **AppArmor**: Another Linux security module that confines programs to a limited set of resources. Unlike SELinux, AppArmor uses path-based access controls, making it easier to configure for some users.

Note: This course will not dive deeply into SELinux or AppArmor, but it's essential to be aware of their existence and importance in securing Linux systems.

### 2.3 Using `sudo` for Privilege Management

The `sudo` command allows users to execute commands with superuser privileges, ensuring that administrative tasks are performed securely without the need to log in as the root user.

#### Example: Running a Command with `sudo`

```bash
sudo apt-get update
```
- This command updates the package list, but only users with `sudo` privileges can run it.

### 2.4 Basic Auditing and Logging

Linux maintains logs of system activity, which are essential for monitoring and detecting suspicious behavior. Important log files are typically stored in `/var/log/`.

- **Authentication Logs**: Logs related to user logins, found in `/var/log/auth.log` or `/var/log/secure` (for Red Hat-based systems).
- **System Logs**: General system activity, found in `/var/log/syslog` or `/var/log/messages`.

Using basic auditing tools like `auditd` can help track important security events on the system.

### Conclusion

This introduction to Linux security fundamentals covers the basic concepts and features that form the foundation of a secure Linux system. By understanding common threats, applying the principle of least privilege, and leveraging built-in security features like permissions and `sudo`, you can significantly reduce the risk of security breaches. The next lectures will dive deeper into hardening strategies, encryption, and network security.