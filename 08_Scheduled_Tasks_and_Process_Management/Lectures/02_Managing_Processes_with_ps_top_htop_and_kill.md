# Managing Processes with ps, top, htop, and kill

Process management is a crucial aspect of system administration in Linux. This lecture covers the tools and techniques needed to monitor and manage system processes effectively.

## Understanding Processes

A process is an instance of a running program. Each process in Linux has a unique Process ID (PID). Processes can be in various states such as running, sleeping, stopped, or zombie.

### Background and Foreground Processes

- **Foreground Process**: A process that is started and runs in the shell, occupying the shell until it completes.
- **Background Process**: A process that runs independently of the shell, allowing the shell to be used for other tasks.

#### Running a Command in the Background

To run a command in the background, append an ampersand (`&`) to the command:
```bash
command &
```

### Process States

- **R (Running)**: The process is currently being executed.
- **S (Sleeping)**: The process is waiting for an event to complete.
- **D (Uninterruptible Sleep)**: The process is waiting for I/O.
- **Z (Zombie)**: The process has completed, but its parent has not yet collected its status.
- **T (Stopped)**: The process has been stopped by a signal or the user.

## Monitoring Processes

### ps Command

The `ps` (process status) command provides a snapshot of the current processes.

#### Basic Usage

```bash
ps
```

#### Common Options

- `ps aux`: Displays detailed information about all processes.
- `ps -ef`: Displays a full-format listing.

#### Example: Displaying All Processes

```bash
ps aux
```

### top Command

The `top` command provides a dynamic, real-time view of running processes.

#### Basic Usage

```bash
top
```

#### Interactive Commands in top

- `h`: Display help.
- `k`: Kill a process.
- `r`: Renice (change priority) a process.
- `q`: Quit top.

### htop Command

The `htop` command is an interactive process viewer with a user-friendly interface. It is not installed by default on all systems.

#### Installing htop

#### Debian/Ubuntu

```bash
sudo apt-get install htop
```

#### CentOS/RHEL

```bash
sudo yum install htop
```

#### Basic Usage

```bash
htop
```

#### Interactive Commands in htop

- `F1`: Help.
- `F2`: Setup.
- `F3`: Search.
- `F4`: Filter.
- `F5`: Tree view.
- `F6`: Sort by a column.
- `F9`: Kill a process.
- `F10`: Quit htop.

## Managing Processes

### kill Command

The `kill` command sends a signal to a process, typically to terminate it.

#### Basic Usage

```bash
kill PID
```

#### Common Signals

- `-SIGTERM (15)`: Gracefully terminate a process.
- `-SIGKILL (9)`: Forcefully terminate a process.
- `-SIGHUP (1)`: Reload the process.

#### Example: Terminating a Process

```bash
kill -SIGTERM 1234
```

### pkill Command

The `pkill` command sends a signal to processes based on their name and other attributes.

#### Basic Usage

```bash
pkill process_name
```

#### Example: Terminating All Instances of a Process

```bash
pkill -SIGTERM apache2
```

### killall Command

The `killall` command sends a signal to all processes running a specified command.

#### Basic Usage

```bash
killall command_name
```

#### Example: Forcefully Terminating All Instances of a Process

```bash
killall -SIGKILL firefox
```

## Managing Process Priorities

In Linux, each process is assigned a priority, which determines the amount of CPU time the process receives. Priorities range from -20 (highest priority) to 19 (lowest priority). The default priority is 0.

### nice Command

The `nice` command starts a process with a specified priority.

#### Basic Usage

```bash
nice -n priority command
```

- **priority**: The nice value to assign, ranging from -20 to 19. A lower value means a higher priority.

#### Example: Starting a Process with a Lower Priority

```bash
nice -n 10 tar -czf archive.tar.gz /path/to/directory
```

In this example, the `tar` command is started with a nice value of 10, meaning it has a lower priority compared to processes with the default nice value of 0.

### renice Command

The `renice` command changes the priority of an existing process.

#### Basic Usage

```bash
renice priority -p PID
```

- **priority**: The new nice value to assign, ranging from -20 to 19.
- **PID**: The Process ID of the process to change.

#### Example: Changing the Priority of a Process

```bash
renice 5 -p 1234
```

In this example, the process with PID 1234 is assigned a new nice value of 5, giving it a lower priority compared to processes with a nice value closer to -20.

### Understanding Nice Values

- **-20**: Highest priority. The process will receive more CPU time compared to others.
- **0**: Default priority. Standard CPU time allocation.
- **19**: Lowest priority. The process will receive less CPU time compared to others.

#### Example: Setting the Highest Priority for a Process

```bash
nice -n -20 /path/to/important_task.sh
```

In this example, the `important_task.sh` script is started with the highest possible priority, ensuring it receives the maximum CPU time.

## Practical Examples

### Example 1: Viewing All Processes with ps

```bash
ps aux
```

### Example 2: Monitoring Processes with top

```bash
top
```

### Example 3: Interactive Process Management with htop

```bash
htop
```

### Example 4: Terminating a Process with kill

```bash
kill -SIGTERM 1234
```

### Example 5: Changing Process Priority with renice

```bash
renice 10 -p 1234
```

## Conclusion

Understanding and managing process priorities is essential for optimizing system performance. By using the `nice` and `renice` commands, you can control the CPU time allocated to processes, ensuring critical tasks have the necessary resources while less important tasks do not overwhelm the system.