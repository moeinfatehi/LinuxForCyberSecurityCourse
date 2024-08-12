# Log Management with syslog and logrotate

Log management is a critical component of system administration in Linux. Proper log management allows administrators to monitor system activity, diagnose issues, and maintain system security. This lecture will cover the basics of managing logs using `syslog` and `logrotate`.

## Introduction to System Logging

Logs are essential for tracking system events, errors, and user activities. They provide valuable information for troubleshooting and ensuring the security of the system. Linux systems generate logs for various services, applications, and the system kernel itself.

### The syslog Protocol

`syslog` is a standard protocol used to send log messages across an IP network. It is widely used by various applications and services to log messages in a centralized location. The messages are categorized based on severity levels and facilities.

#### Syslog Severity Levels

- **0 (emerg)**: System is unusable.
- **1 (alert)**: Action must be taken immediately.
- **2 (crit)**: Critical conditions.
- **3 (err)**: Error conditions.
- **4 (warning)**: Warning conditions.
- **5 (notice)**: Normal but significant conditions.
- **6 (info)**: Informational messages.
- **7 (debug)**: Debug-level messages.

#### Syslog Facilities

- **auth**: Authentication and authorization messages.
- **cron**: Cron jobs and scheduled tasks.
- **daemon**: System daemons.
- **kern**: Kernel messages.
- **mail**: Mail server messages.
- **syslog**: Internal syslog messages.
- **user**: User-level messages.

## Configuring and Managing Logs with rsyslog

`rsyslog` is a powerful and flexible system logging tool that extends the functionality of traditional `syslog`. It is the default logging service in many Linux distributions.

### Installing rsyslog

- **Debian/Ubuntu:**
  ```bash
  sudo apt-get install rsyslog
  ```

- **CentOS/RHEL:**
  ```bash
  sudo yum install rsyslog
  ```

### Configuring rsyslog

The main configuration file for `rsyslog` is located at `/etc/rsyslog.conf`. Additional configuration files can be placed in the `/etc/rsyslog.d/` directory.

#### Basic Configuration

- **Log to a File**: Configure a specific facility and severity level to log messages to a file.
  ```bash
  auth,authpriv.* /var/log/auth.log
  ```

- **Log to a Remote Server**: Send log messages to a remote syslog server.
  ```bash
  *.* @remote-syslog-server:514
  ```

- **Filter by Program Name**: Log messages from a specific program to a separate file.
  ```bash
  if $programname == 'sshd' then /var/log/sshd.log
  ```

### Managing Logs with logrotate

`logrotate` is a utility designed to manage the growth of log files by rotating, compressing, and removing old log files. This prevents logs from consuming too much disk space and keeps log management efficient.

### Installing logrotate

`logrotate` is typically installed by default on most Linux distributions. If it's not installed, you can install it using the following commands:

- **Debian/Ubuntu:**
  ```bash
  sudo apt-get install logrotate
  ```

- **CentOS/RHEL:**
  ```bash
  sudo yum install logrotate
  ```

### Configuring logrotate

The main configuration file for `logrotate` is located at `/etc/logrotate.conf`. Individual configuration files for specific logs can be placed in the `/etc/logrotate.d/` directory.

#### Basic Configuration

- **Daily Log Rotation**: Rotate logs daily.
  ```bash
  /var/log/cron {
      daily
      missingok
      rotate 7
      compress
      notifempty
      create 0640 root utmp
      sharedscripts
      postrotate
          /usr/bin/systemctl reload crond > /dev/null 2>/dev/null || true
      endscript
  }
  ```

- **Weekly Log Rotation**: Rotate logs weekly.
  ```bash
  /var/log/syslog {
      weekly
      missingok
      rotate 4
      compress
      notifempty
      create 0640 root adm
      sharedscripts
      postrotate
          /usr/bin/systemctl reload rsyslog > /dev/null 2>/dev/null || true
      endscript
  }
  ```

- **Size-Based Rotation**: Rotate logs when they reach a certain size.
  ```bash
  /var/log/messages {
      size 100M
      rotate 5
      compress
      delaycompress
      missingok
      notifempty
      create 0640 root root
      postrotate
          /usr/bin/systemctl reload rsyslog > /dev/null 2>/dev/null || true
      endscript
  }
  ```

### Testing logrotate Configuration

You can test your `logrotate` configuration using the `logrotate` command:

```bash
sudo logrotate -d /etc/logrotate.conf
```

The `-d` flag runs `logrotate` in debug mode, showing what actions it would take without actually performing them.

## Practical Examples

### Example 1: Logging Authentication Events with rsyslog

- Edit the `/etc/rsyslog.d/50-default.conf` file to log authentication events to a separate file:
  ```bash
  auth,authpriv.* /var/log/auth.log
  ```

### Example 2: Rotating System Logs with logrotate

- Create a custom `logrotate` configuration to rotate and compress `syslog` every week:
  ```bash
  /var/log/syslog {
      weekly
      rotate 4
      compress
      missingok
      notifempty
      create 0640 root adm
      postrotate
          /usr/bin/systemctl reload rsyslog > /dev/null 2>/dev/null || true
      endscript
  }
  ```

### Example 3: Setting Up Remote Logging with rsyslog

- Configure `rsyslog` to send all log messages to a remote syslog server:
  ```bash
  *.* @192.168.1.100:514
  ```

## Conclusion

Effective log management is essential for maintaining the security and performance of Linux systems. By mastering tools like `rsyslog` and `logrotate`, you can ensure that logs are properly managed, stored, and rotated, preventing them from consuming excessive disk space and providing valuable information for system monitoring and troubleshooting.