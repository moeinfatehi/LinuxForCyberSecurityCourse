# Basic to Advanced Command Line Operations

Welcome to the first lecture of the "Command Line Mastery" module. This section is designed to introduce you to the Linux command line, starting with the basics and progressively moving to more advanced operations. By the end of this lecture, you will be comfortable navigating and manipulating the filesystem, understanding command syntax, and utilizing powerful command line tools.

## Introduction to the Command Line

The command line, or terminal, is a powerful tool used to interact directly with the operating system through commands. Unlike graphical user interfaces (GUIs), the command line provides a text-based interface where users type commands to perform tasks.

## Getting Started with the Command Line

### Opening the Terminal

- Learn how to open the terminal in various Linux distributions. This is usually found in the utilities section of the applications menu.

### Basic Command Syntax

- **Command**: The action or utility you want to perform.
- **Options**: Modifiers that alter the behavior of the command.
- **Arguments**: The targets of the command, such as files or directories.

Example:
```bash
ls -l /home/user
```
- `ls` is the command to list directory contents.
- `-l` is an option to list in long format.
- `/home/user` is the argument specifying where to list the files.

## Essential Command Line Operations

### Navigating the Filesystem

- `pwd` (Print Working Directory): Displays the current directory path.
  ```bash
  pwd
  ```
- `cd` (Change Directory): Moves to another directory.
  ```bash
  cd /var/log  # Move to the /var/log directory
  cd ..        # Move up one directory
  cd           # Move to the user's home directory
  ```

- `ls` (List): Shows files in the current directory. Use `-l` for detailed information and `-a` to show hidden files.
  ```bash
  ls -l        # List in long format
  ls -a        # List all files, including hidden files
  ls -la /etc  # List all files in /etc in long format
  ```

### Manipulating Files and Directories

- `mkdir` (Make Directory): Creates a new directory.
  ```bash
  mkdir new_folder
  ```

- `touch`: Creates a new empty file or updates the timestamp of an existing file.
  ```bash
  touch newfile.txt
  ```

- `cp` (Copy): Copies files or directories.
  ```bash
  cp original.txt backup.txt  # Copy original.txt to backup.txt
  cp -r old_dir new_dir       # Recursively copy old_dir to new_dir
  ```

- `mv` (Move): Moves or renames files or directories.
  ```bash
  mv oldname.txt newname.txt  # Rename or move a file within the same directory
  mv myfile.txt ~/Documents/  # Move myfile.txt to the Documents directory
  ```

- `rm` (Remove): Deletes files or directories. Use `-r` for directories.
  ```bash
  rm unwanted.txt             # Delete a file
  rm -r old_directory         # Recursively delete a directory
  ```

### Viewing and Managing File Content

- `cat` (Concatenate): Displays the content of a file on the screen.
  ```bash
  cat file.txt
  ```

- `more` and `less`: Paginate through text files.
  ```bash
  less log.txt  # Open log.txt in less for scrollable viewing
  ```

- `head` and `tail`: Show the beginning or end of files, respectively.
  ```bash
  head -n 5 file.txt  # Show the first 5 lines of file.txt
  tail -n 5 file.txt  # Show the last 5 lines of file.txt
  ```

- `nano`, `vi`: Open text editors to modify files directly from the terminal.
  ```bash
  nano myfile.txt  # Open myfile.txt in nano for editing
  vi myfile.txt    # Open myfile.txt in vi for editing
  ```

### Searching and Filtering

- `grep`: Searches for patterns within files. Combine with regular expressions for powerful search capabilities.
  ```bash
  grep 'error' logfile.txt  # Search for 'error' in logfile.txt
  ```

- `find`: Searches for files and directories based on criteria like name, size, or modification time.
  ```bash
  find /home/user -name '*.txt'  # Find all .txt files in /home/user
  ```

### Pipes and Redirection

Understanding how to use pipes (`|`) and redirection (`>`, `>>`, `<`) effectively can greatly enhance your command line efficiency:

- **Pipes**: Use a pipe to send the output of one command to another command as input.
  ```bash
  cat file.txt | grep 'search'  # Display lines from file.txt that contain 'search'
  ```

- **Redirection**: Redirect the output of a command to a file, or use a file as input.
  ```bash
  echo "Hello, World!" > hello.txt   # Write "Hello, World!" to hello.txt
  grep 'search' < input.txt > results.txt  # Search 'search' in input.txt and save results to results.txt
  ```

## Conclusion

This introduction to basic and advanced command line operations is your first step into the powerful world of Linux system administration. Mastery of these skills lays the groundwork for more advanced system management and automation tasks you will learn later in this course.
