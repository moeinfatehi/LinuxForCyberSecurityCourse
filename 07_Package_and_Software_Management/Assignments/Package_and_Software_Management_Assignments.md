# Package and Software Management - Assignments

## Assignment 1: Managing Packages with APT

### Objective
Demonstrate your ability to manage software packages using APT on a Debian-based system.

### Tasks
1. Install the `curl` and `git` packages using APT.
2. Remove the `curl` package while keeping its configuration files.
3. Update all installed packages to their latest versions.
4. Add the `deadsnakes/ppa` repository and install `python3.9`.
5. List all currently configured repositories.

### Submission
- Provide a script named `apt_management.sh` that performs all the tasks mentioned above.
- Ensure the script includes comments explaining each step.

## Assignment 2: Managing Packages with RPM and YUM

### Objective
Demonstrate your ability to manage software packages using RPM and YUM on a Red Hat-based system.

### Tasks
1. Install the `htop` package using YUM.
2. Remove the `htop` package.
3. Update all installed packages to their latest versions.
4. Add a custom repository by creating a `.repo` file in `/etc/yum.repos.d/`.
5. List all currently configured repositories.

### Submission
- Provide a script named `yum_management.sh` that performs all the tasks mentioned above.
- Ensure the script includes comments explaining each step.

## Assignment 3: Installing Software from Source

### Objective
Demonstrate your ability to download, build, and install software from source code.

### Tasks
1. Download the source code for `wget` version 1.21.1 from the official website.
2. Extract the downloaded tarball.
3. Configure the build environment for `wget`.
4. Compile and install `wget` from source.
5. Verify the installation by checking the version of `wget`.

### Submission
- Provide a script named `install_from_source.sh` that performs all the tasks mentioned above.
- Ensure the script includes comments explaining each step.

## Assignment 4: Secure and Up-to-Date Software Environments

### Objective
Ensure your system is secure and up-to-date by managing package updates and verifying package integrity.

### Tasks
1. Enable automatic updates on your system.
2. Manually update all installed packages to their latest versions.
3. Verify the integrity of an installed package (e.g., `curl`).
4. Install a Snap package of your choice.
5. Install a Flatpak package of your choice from the Flathub repository.

### Submission
- Provide a script named `secure_updates.sh` that performs all the tasks mentioned above.
- Ensure the script includes comments explaining each step.

## Submission Guidelines

Submit your scripts via the course's submission platform. Ensure all scripts are executable and well-documented with comments explaining each command. The scripts should be tested to ensure they perform the tasks correctly on the appropriate Linux distribution.