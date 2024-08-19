# System Hardening Strategies

System hardening is the process of securing a Linux system by reducing its surface of vulnerability. This lecture will cover key strategies for hardening your Linux system, including disabling unnecessary services, securing SSH, implementing secure password policies, configuring firewalls, and applying hardening guidelines like CIS Benchmarks.

## 1. Disabling Unnecessary Services

One of the simplest ways to harden a Linux system is to disable any services that are not necessary. Running unnecessary services increases the attack surface and consumes system resources.

### 1.1 Identifying Running Services

You can identify running services using commands like `systemctl` (for systemd-based systems) or `service` (for older init systems).

#### Example: Listing All Active Services

```bash
systemctl list-units --type=service --state=running
```

### 1.2 Disabling Unnecessary Services

Once you identify unnecessary services, you can disable them to reduce the system's attack surface.

#### Example: Disabling a Service

```bash
sudo systemctl disable service_name
sudo systemctl stop service_name
```

- The `disable` command prevents the service from starting at boot, and the `stop` command immediately stops the service.

### 1.3 Securing System Daemons

System daemons (background services) can be secured by restricting their privileges, using security modules like AppArmor or SELinux, and ensuring they are only accessible to trusted users.

#### Example: Restricting a Daemon with AppArmor

```bash
sudo apparmor_parser -r /etc/apparmor.d/usr.sbin.mysqld
```

## 2. Securing SSH

SSH is a critical service for remote access, but it can also be a target for attackers. Securing SSH is one of the most important steps in system hardening.

### 2.1 Enforcing Key-Based Authentication

Key-based authentication is more secure than password-based authentication, as it requires an SSH key pair to authenticate.

#### Example: Configuring Key-Based Authentication

1. Generate an SSH key pair on the client machine:
   ```bash
   ssh-keygen -t rsa -b 4096
   ```
2. Copy the public key to the server:
   ```bash
   ssh-copy-id user@server
   ```
3. Edit the SSH configuration file on the server (`/etc/ssh/sshd_config`) to disable password authentication:
   ```bash
   PasswordAuthentication no
   ```
4. Restart the SSH service:
   ```bash
   sudo systemctl restart sshd
   ```

### 2.2 Disabling Root Login

Allowing root login over SSH is a security risk. It’s better to disable root login and use `sudo` for administrative tasks.

#### Example: Disabling Root Login

1. Edit the SSH configuration file (`/etc/ssh/sshd_config`):
   ```bash
   PermitRootLogin no
   ```
2. Restart the SSH service:
   ```bash
   sudo systemctl restart sshd
   ```

### 2.3 Implementing Two-Factor Authentication (2FA)

Two-factor authentication adds an additional layer of security by requiring a second factor (e.g., a one-time code from a mobile app) in addition to a password or SSH key.

#### Example: Setting Up 2FA with Google Authenticator

1. Install the Google Authenticator PAM module:
   ```bash
   sudo apt-get install libpam-google-authenticator
   ```
2. Run the `google-authenticator` command to set up 2FA for the current user:
   ```bash
   google-authenticator
   ```
3. Edit the `/etc/pam.d/sshd` file to add the following line:
   ```bash
   auth required pam_google_authenticator.so
   ```
4. Edit the SSH configuration file (`/etc/ssh/sshd_config`) to enable challenge-response authentication:
   ```bash
   ChallengeResponseAuthentication yes
   ```
5. Restart the SSH service:
   ```bash
   sudo systemctl restart sshd
   ```

## 3. Implementing Secure Password Policies

Ensuring that users have strong passwords is critical for system security. You can enforce password policies using the Pluggable Authentication Modules (PAM) framework.

### 3.1 Configuring Password Strength Requirements

You can configure password strength requirements using the `pam_pwquality` module.

#### Example: Enforcing Strong Passwords

1. Edit the `/etc/pam.d/common-password` file (Debian/Ubuntu) or `/etc/pam.d/system-auth` file (RHEL/CentOS) and add the following line:
   ```bash
   password requisite pam_pwquality.so retry=3 minlen=12 dcredit=-1 ucredit=-1 ocredit=-1 lcredit=-1
   ```
   - This configuration requires passwords to be at least 12 characters long and contain at least one digit, one uppercase letter, one lowercase letter, and one special character.

### 3.2 Locking Accounts After Failed Login Attempts

You can configure PAM to lock user accounts after a certain number of failed login attempts.

#### Example: Account Lockout Policy

1. Edit the `/etc/pam.d/common-auth` file (Debian/Ubuntu) or `/etc/pam.d/system-auth` file (RHEL/CentOS) and add the following line:
   ```bash
   auth required pam_tally2.so deny=5 unlock_time=900
   ```
   - This configuration locks the account after 5 failed login attempts and unlocks it after 15 minutes.

## 4. Firewall Configuration

Firewalls are a critical component of Linux security, helping control incoming and outgoing network traffic. Two common firewall tools in Linux are `ufw` (Uncomplicated Firewall) and `iptables`.

### 4.1 Configuring `ufw`

`ufw` is a user-friendly firewall tool available on Debian-based systems.

#### Example: Basic `ufw` Configuration

1. Enable `ufw`:
   ```bash
   sudo ufw enable
   ```
2. Allow SSH traffic:
   ```bash
   sudo ufw allow ssh
   ```
3. Allow specific ports (e.g., HTTP and HTTPS):
   ```bash
   sudo ufw allow 80/tcp
   sudo ufw allow 443/tcp
   ```
4. Check the firewall status:
   ```bash
   sudo ufw status
   ```

### 4.2 Managing `iptables`

`iptables` provides more granular control over firewall rules but requires more advanced configuration.

#### Example: Basic `iptables` Rules

1. Allow SSH traffic:
   ```bash
   sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT
   ```
2. Allow HTTP traffic:
   ```bash
   sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT
   ```
3. Drop all other incoming traffic:
   ```bash
   sudo iptables -P INPUT DROP
   ```

## 5. Automatic Updates and Patch Management

Keeping your system up to date with the latest security patches is essential for preventing vulnerabilities.

### 5.1 Enabling Automatic Updates

You can configure your system to automatically install security updates.

#### Example: Configuring Automatic Updates on Debian/Ubuntu

1. Install the `unattended-upgrades` package:
   ```bash
   sudo apt-get install unattended-upgrades
   ```
2. Configure automatic updates:
   ```bash
   sudo dpkg-reconfigure --priority=low unattended-upgrades
   ```

#### Example: Configuring Automatic Updates on RHEL/CentOS

1. Install the `yum-cron` package:
   ```bash
   sudo yum install yum-cron
   ```
2. Enable and start the `yum-cron` service:
   ```bash
   sudo systemctl enable yum-cron
   sudo systemctl start yum-cron
   ```

## 6. Introduction to Hardening Guidelines

Hardening guidelines provide detailed instructions for securing Linux systems. One of the most widely recognized guidelines is the CIS (Center for Internet Security) Benchmarks.

### 6.1 Overview of CIS Benchmarks

CIS Benchmarks provide security recommendations for various Linux distributions, including Ubuntu, CentOS, and Red Hat. They cover topics such as user management, network security, and system logging.

#### Example: Applying CIS Benchmarks

1. Download the CIS Benchmark for your Linux distribution from the CIS website.
2. Review the recommendations and apply relevant settings to your system.
3. Use tools like `CIS-CAT` to automate compliance checks.

### 6.2 Hardening Guidelines for Specific Services

In addition to hardening the base system, it's essential to secure specific services like web servers and databases. For example, hardening guidelines for Apache may include disabling unnecessary modules, enforcing HTTPS, and securing the configuration files.

## Conclusion

System hardening is a critical step in securing your Linux environment. By disabling unnecessary services, securing SSH, implementing strong password policies, configuring firewalls, and following hardening guidelines like CIS Benchmarks, you can significantly reduce the risk of security breaches. In the next lecture, we will dive into filesystem and data encryption to further secure your data.