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

Understanding the use of pipes (`|`) and redirection (`>`, `>>`, `<`, `2>`, `2>&1`) is key to mastering command line interfaces. These tools allow you to manage the flow of data in the terminal, enabling complex operations and efficient task handling.

#### Pipes (|)

Pipes allow you to send the output of one command directly into another as input. This chaining of commands is pivotal in building efficient command line workflows.

- **Example**:
  ```bash
  cat log.txt | grep "ERROR" | wc -l
  # This command sequence counts the number of lines containing "ERROR" in log.txt.
  ```

#### Redirection

Redirection is used to direct the output from commands to files or other outputs.

1. **Standard Output (stdout, file descriptor 1)** and **Standard Error (stderr, file descriptor 2)**:
   - Commands typically send their output to stdout (`1`) and their errors to stderr (`2`).
   - You can redirect these outputs to different locations.

2. **Redirecting stdout (`>` or `1>`) and stderr (`2>`) separately**:
   - **Example**:
     ```bash
     ls -l /nonexistent_directory > output.txt 2> error.txt
     # stdout (file listing) is sent to output.txt, and errors are sent to error.txt.
     ```

3. **Appending stdout (`>>` or `1>>`) and stderr (`2>>`)** to existing files:
   - **Example**:
     ```bash
     echo "Start of script execution" >> script.log
     cat missingfile.txt 2>> script.log
     # Adds a start notice to script.log and appends any error message from cat to the same log.
     ```

4. **Using `2>&1` to redirect stderr to the same location as stdout**:
   - This is useful when you want both outputs to be captured together.
   - **Example**:
     ```bash
     grep 'search_term' missingfile.txt > result.txt 2>&1
     # Redirects both the output and error messages to result.txt.
     ```
5. **Redirecting stdin (`<`)**:
    - The `<` operator is used to direct the contents of a file into a command as its standard input.
   - **Example**:
     ```bash
     grep "admin" < users.txt
     # Uses users.txt as input to search for "admin".
     ```

#### Advanced Redirection Scenarios

Here are some more mixed-use examples that illustrate the versatility and power of using various redirections in combination:

- **Combining input redirection with output and error redirection**:
  ```bash
  sort < unsorted.txt > sorted.txt 2> sort_errors.txt
  # Takes input from unsorted.txt, sorts it, and writes the output to sorted.txt while logging errors in sort_errors.txt.
  ```

- **Using multiple commands to manage outputs and errors, with input redirection**:
  ```bash
  (grep "ERROR" < app.log; echo "Search complete") > results.txt 2>&1
  # Searches for "ERROR" in app.log, adds a completion message, and directs both to results.txt, including any errors.
  ```

- **Redirecting both stdout and stderr from multiple commands**:
  ```bash
  (cat file1.txt; cat file2.txt; ls -l) > full_output.txt 2> error_output.txt
  # Outputs the contents of file1.txt, file2.txt, and the listing of the current directory to full_output.txt, while errors are logged in error_output.txt.
  ```

### Running Multiple Commands on a Single Line

Executing multiple commands on a single line in the Linux command line can enhance productivity and automate routine tasks. There are several methods to achieve this, including using semicolons, logical operators (AND and OR), and command grouping. Each method has its specific use case and behavior.

#### Using Semicolons (;)

The semicolon (`;`) allows you to execute multiple commands sequentially, regardless of whether the previous command succeeded or failed.

- **Example**:
  ```bash
  echo "Starting backup"; rsync -a /source /backup; echo "Backup completed"
  # This will echo a start message, perform the backup, and then echo a completion message.
  ```

#### Using Logical AND (&&)

The AND operator (`&&`) executes the next command only if the previous command succeeded (i.e., exited with a status of 0).

- **Example**:
  ```bash
  mkdir /new_directory && cp file.txt /new_directory
  # This will only copy file.txt to /new_directory if the directory was successfully created.
  ```

#### Using Logical OR (||)

The OR operator (`||`) executes the next command only if the previous command failed (i.e., exited with a non-zero status).

- **Example**:
  ```bash
  grep "Error" log.txt || echo "No errors found."
  # This will search for "Error" in log.txt and only echo "No errors found" if the grep command fails to find any matches.
  ```

#### Command Grouping ({ })

Command grouping using curly braces `{ }` allows you to execute a series of commands in the current shell context. Commands are separated by semicolons, and the last command must end with a semicolon.

- **Example**:
  ```bash
  { echo "Updating system"; sudo apt update; sudo apt upgrade; }
  # Executes a series of system update commands, all within the same shell.
  ```

#### Using Subshells (())

Using subshells `( )` executes the grouped commands in a subshell environment. This means that any changes to variables or the environment do not persist outside the subshell.

- **Example**:
  ```bash
  (cd /var/log; cat syslog > /tmp/syslog_backup)
  # Changes directory only in the subshell and copies syslog to /tmp without affecting the current shell's working directory.
  ```

## Conclusion

This introduction to basic and advanced command line operations is your first step into the powerful world of Linux system administration. Mastery of these skills lays the groundwork for more advanced system management and automation tasks you will learn later in this course.
