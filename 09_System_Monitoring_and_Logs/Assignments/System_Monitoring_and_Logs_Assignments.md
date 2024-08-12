# System Monitoring and Logs - Assignments

## Assignment 1: Using System Monitoring Tools

### Objective
Demonstrate your ability to monitor system performance using essential Linux monitoring tools.

### Tasks
1. Use the `vmstat` command to monitor system performance for 1 minute with 5-second intervals. Save the output to a file named `vmstat_output.txt`.
2. Use the `iostat` command to monitor disk I/O statistics every 10 seconds for 1 minute. Save the output to a file named `iostat_output.txt`.
3. Install `htop` (if not already installed) and take a screenshot of `htop` running, showing CPU and memory usage.
4. Use the `mpstat` command to monitor CPU usage per core every 5 seconds for 1 minute. Save the output to a file named `mpstat_output.txt`.

### Submission
- Provide a script named `system_monitoring.sh` that performs all the tasks mentioned above.
- Ensure the script includes comments explaining each step.
- Submit the output files (`vmstat_output.txt`, `iostat_output.txt`, `mpstat_output.txt`) and the `htop` screenshot.

## Assignment 2: Configuring and Managing Logs

### Objective
Demonstrate your ability to configure and manage system logs using `rsyslog` and `logrotate`.

### Tasks
1. Configure `rsyslog` to log all authentication events (`auth,authpriv.*`) to a custom log file named `/var/log/auth_custom.log`.
2. Create a `logrotate` configuration that rotates `/var/log/auth_custom.log` daily, keeps 7 days of logs, and compresses old logs.
3. Test the `logrotate` configuration using the `logrotate` command and provide the output.

### Submission
- Provide a script named `log_management.sh` that performs all the tasks mentioned above.
- Ensure the script includes comments explaining each step.
- Submit the `rsyslog` and `logrotate` configuration files as part of your submission.

## Assignment 3: Analyzing and Searching Logs

### Objective
Demonstrate your ability to analyze and search logs using tools like `grep`, `awk`, `sed`, and `journalctl`.

### Tasks
1. Use `grep` to search for all failed SSH login attempts in `/var/log/auth.log` and save the results to a file named `ssh_failed_attempts.txt`.
2. Use `awk` to extract and count the IP addresses involved in failed SSH login attempts. Save the results to a file named `failed_ips_count.txt`.
3. Use `sed` to anonymize (replace with "REDACTED") a specific IP address (of your choice) in `/var/log/auth.log` and save the modified log to a new file named `auth_redacted.log`.
4. Use `journalctl` to display all systemd logs related to the `sshd` service for the last 24 hours. Save the output to a file named `sshd_journal.log`.

### Submission
- Provide a script named `log_analysis.sh` that performs all the tasks mentioned above.
- Ensure the script includes comments explaining each step.
- Submit the output files (`ssh_failed_attempts.txt`, `failed_ips_count.txt`, `auth_redacted.log`, and `sshd_journal.log`).

## Submission Guidelines

Submit your scripts via the course's submission platform. Ensure all scripts are executable and well-documented with comments explaining each command. The scripts should be tested to ensure they perform the tasks correctly on the appropriate Linux distribution.
