# Scheduled Tasks and Process Management - Assignments

## Assignment 1: Configuring Cron Jobs

### Objective
Demonstrate your ability to configure and manage cron jobs to automate tasks.

### Tasks
1. Schedule a cron job to run a backup script (`/path/to/backup_script.sh`) every day at 2 AM.
2. Schedule a cron job to update the system packages (`sudo apt-get update && sudo apt-get upgrade -y`) every day at 3 AM.
3. List all the cron jobs for the current user.
4. Remove the cron job that updates the system packages.

### Submission
- Provide a script named `cron_jobs.sh` that performs all the tasks mentioned above.
- Ensure the script includes comments explaining each step.

## Assignment 2: Scheduling One-Time Tasks with At

### Objective
Demonstrate your ability to schedule and manage one-time tasks using the `at` command.

### Tasks
1. Schedule a one-time task to run a maintenance script (`/path/to/maintenance.sh`) at 5 PM today.
2. List all pending `at` jobs.
3. Remove the scheduled maintenance task.

### Submission
- Provide a script named `at_tasks.sh` that performs all the tasks mentioned above.
- Ensure the script includes comments explaining each step.

## Assignment 3: Monitoring and Managing Processes

### Objective
Demonstrate your ability to monitor and manage system processes using tools like `ps`, `top`, `htop`, and `kill`.

### Tasks
1. Use the `ps` command to list all processes and save the output to a file named `ps_output.txt`.
2. Install `htop` (if not already installed) and use it to monitor processes interactively.
3. Use the `kill` command to terminate a process by its PID (use a harmless process for this task, such as a dummy script).
4. Change the priority of a running process using the `renice` command.

### Submission
- Provide a script named `process_management.sh` that performs all the tasks mentioned above.
- Ensure the script includes comments explaining each step.
- Include the output files (`ps_output.txt` and `top_output.txt`) in your submission.

## Submission Guidelines

Submit your scripts via the course's submission platform. Ensure all scripts are executable and well-documented with comments explaining each command. The scripts should be tested to ensure they perform the tasks correctly on the appropriate Linux distribution.