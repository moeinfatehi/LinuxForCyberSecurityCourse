# Introduction to Shell Scripting for Automating Tasks

This lecture introduces the fundamentals of shell scripting, an essential skill for automating tasks in a Linux environment. By mastering shell scripting, you can streamline your workflows, automate repetitive tasks, and manage your systems more efficiently.

## 1. Basics of Shell Scripting

### What is a Shell Script?
A shell script is a text file containing a sequence of commands for a shell to execute. It can automate almost any task that can be performed manually on the command line, making it a powerful tool for system administration.

### Creating Your First Script
To create a shell script, you simply write commands in a file and set the appropriate permissions to make it executable. Here's how to create and execute a basic script:

- **Create a script file**: Use a text editor to write commands. Save the file with a `.sh` extension, for example, `myscript.sh`.
  ```bash
  #! /bin/bash
  echo "Hello, world!"
  ```

- **Make the script executable**: Change the file's permissions to allow execution.
  ```bash
  chmod +x myscript.sh
  ```

- **Run the script**: Execute the script by specifying its path.
  ```bash
  ./myscript.sh
  ```

### Shell Script Syntax
- **Comments**: Begin with `#`, and explain what the script or commands do.
- **Variables**: Store data that can be used and manipulated in the script.
  ```bash
  name="Alice"
  echo "Hello, $name"
  ```
- **Exit Status**: Indicates the success or failure of the last command run.
  ```bash
  command
  if [ $? -eq 0 ]; then
    echo "The command succeeded."
  else
    echo "The command failed."
  fi
  ```

## 2. Control Structures

### Conditional Statements
Conditional statements allow you to make decisions in your scripts. The most common is the `if` statement, which executes a set of commands if a test is true.

```bash
if [ $USER == 'root' ]; then
  echo "You are the root user."
else
  echo "You are not the root user."
fi
```

### Loop Constructs
Loops allow you to repeat actions. The most common loops in shell scripting are `for`, `while`, and `until`.

- **For Loop**:
  ```bash
  for i in 1 2 3; do
    echo "Looping ... number $i"
  done
  ```

- **While Loop**:
  ```bash
  count=1
  while [ $count -le 5 ]; do
    echo "Count: $count"
    count=$((count + 1))
  done
  ```

- **Until Loop**:
  ```bash
  count=1
  until [ $count -gt 5 ]; do
    echo "Count: $count"
    count=$((count + 1))
  done
  ```

### Case Statements
Case statements simplify complex conditional logic and are easier to read than multiple `if-elif` statements.

```bash

#!/bin/bash
input=$1  # Assign the first argument to the variable input

case $input in
  1) echo "You selected option 1";;
  2) echo "You selected option 2";;
  3) echo "You selected option 3";;
  *) echo "Invalid option selected";;
esac

```
## 3. Functions and Modular Scripting

### Creating Functions
Functions in shell scripting allow you to encapsulate code into reusable blocks, making scripts more organized and maintainable.

```bash
greet() {
  echo "Hello, $1"
}
greet "Alice"
```

### Scope of Variables
Variables in functions can be local (limited to the scope of the function) or global (accessible throughout the script).

```bash
global_var="accessible everywhere"

my_function() {
  local local_var="only accessible in this function"
  echo "Inside function: $global_var, $local_var"
}
my_function
echo "Outside function: $global_var, $local_var (not accessible)"
```

### Source and Export
Use `source` to include and execute the contents of another script within the current script. `export` is used to make variables and functions available to child processes.

```bash
source ./my_other_script.sh  # Includes and runs the contents of my_other_script.sh
export global_var  # Makes global_var available to any child processes
```

## 4. Advanced Scripting Techniques

### Parameter Expansion
Bash provides powerful parameter expansion options that allow you to manipulate string values in variables.

```bash
filename="sample.txt"
echo "${filename%.txt}.bak"  # Outputs "sample.bak"
```

### Array Variables
Arrays store multiple values in a single variable and are particularly useful for managing lists of data.

```bash
colors=("red" "green" "blue")
echo "${colors[1]}"  # Outputs "green"
```

### Command Substitution
Command substitution allows you to use the output of a command as an argument in a script.

```bash
current_date=$(date +%Y-%m-%d)
echo "Today is $current_date"
```

## 5. Debugging and Error Handling

### Debugging Tips
Use set options such as `-x` to trace what gets executed in a script, helping to pinpoint issues.

```bash
set -x  # Enable debugging
commands here
set +x  # Disable debugging
```

### Error Handling
Implement error checking in scripts to handle unexpected situations gracefully.

```bash
if ! mkdir new_directory; then
  echo "Could not create directory"
  exit 1
fi
```

## 6. Practical Automation Examples

### System Administration Tasks
Shell scripts can automate a wide range of system administration tasks, enhancing efficiency and reducing the likelihood of human error.

```bash
# Automate system updates
sudo apt update && sudo apt upgrade -y
```

### Processing Data
Scripts can process text files or outputs from commands efficiently, allowing for automated data manipulation.

```bash
# Filter logs and email them
grep "ERROR" /var/log/app.log | mail -s "Error Logs" admin@example.com
```

### Scheduling Tasks
Cron jobs allow you to schedule scripts to run at specific times, making regular tasks like backups automatic.

```bash
# Open crontab editor
crontab -e

# Add a cron job
0 1 * * * /path/to/backup_script.sh
```

## 7. Best Practices in Shell Scripting

### Security Considerations
Always consider security when writing scripts to avoid introducing vulnerabilities.

- Avoid running scripts as root unless necessary.
- Validate all inputs to prevent injection attacks.

### Maintainability and Documentation
Well-documented scripts are easier to maintain and debug.

```bash
# Good comment
# This function calculates and displays disk usage
check_disk_usage() {
  df -h | grep /dev/sda1
}
```

### Performance Optimization
Optimize scripts for performance to ensure they run efficiently.

- Use built-in shell commands instead of external commands where possible.
- Avoid using unnecessary loops by leveraging powerful tools like `awk` and `sed`.

## Conclusion

Throughout this module, you've learned the fundamental to advanced aspects of shell scripting, covering everything from basic syntax to writing robust functions and handling errors. You've also explored practical examples of how shell scripts can automate routine tasks, making systems more efficient and reducing manual intervention.

By adhering to best practices in scripting, you can write secure, efficient, and maintainable scripts that serve as valuable tools in your system administration or cybersecurity toolkit. Mastery of these skills will not only enhance your productivity but also empower you to tackle complex automation challenges with confidence.