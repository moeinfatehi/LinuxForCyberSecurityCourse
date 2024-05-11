# Command Line Mastery - Assignments

This document outlines the assignments for the "Command Line Mastery" module of the course. These assignments are designed to test your knowledge and skills in using the Linux command line and shell scripting to manage systems and automate tasks effectively.

## Assignment 1: Command Line Basics

### Objective
Demonstrate basic command line skills by navigating the filesystem, creating, and manipulating files and directories.

### Tasks
1. Use the command line to navigate to your home directory and create a subdirectory named `LinuxPractices`.
2. Inside `LinuxPractices`, create a file named `practice.txt`, and enter some text into it using a command line text editor (like `nano` or `vi`).
3. List all files in the `LinuxPractices` directory showing detailed information and redirect this output to a file named `details.txt`.
4. Use command line tools to display the contents of `practice.txt` on the terminal.

## Assignment 2: Advanced File Operations and Scripting

### Objective
Use advanced command line operations and basic scripting to automate tasks.

### Tasks
1. Write a script that creates a backup of all `.txt` files in your `Documents` directory and stores them in a `Backup` directory. Ensure the script checks if the `Backup` directory exists and creates it if it does not.
2. The script should log each file it backs up with a timestamp in a log file named `backup.log`.

## Assignment 3: Shell Scripting for Automation

### Objective
Develop a shell script that automates a routine task, such as system updates or cleaning temporary files.

### Tasks
1. Write a shell script that updates the system, cleans up temporary files, and shows system information such as disk usage and memory usage. This script should log its operations in a system log file.
2. Include error handling in the script to manage any potential failures during execution.

## Assignment 4: Secure Script Execution

### Objective
Ensure a shell script can be executed securely and efficiently, with proper permissions and error handling.

### Tasks
1. Write a script that requires administrator privileges, checks for them at the start, and exits with an appropriate message if not run as root.
2. Include comments in your script to explain each section of the code and ensure it adheres to best practices for security and performance.

## Submission Guidelines

Submit your scripts and a document explaining your approach to each task, any challenges you faced, and how you overcame them. Include any assumptions or simplifications you made while designing your scripts.

## Conclusion

These assignments will help you solidify your command line skills and demonstrate your ability to use shell scripting to automate complex tasks and manage system configurations efficiently. Successfully completing these tasks will prepare you for more advanced system administration roles and challenges.
