# Installing Software from Source

Installing software from source code provides greater control over the installation process, allowing for customization and optimization specific to your system. This approach is commonly used for software that is not available in package repositories or when you need a specific version or configuration.

## Prerequisites

Before installing software from source, ensure you have the necessary development tools and libraries. On Debian-based systems, you can install these tools using `build-essential`. On Red Hat-based systems, you can use `Development Tools`.

### Installing Development Tools on Debian-based Systems

```bash
sudo apt-get update
sudo apt-get install build-essential
```

### Installing Development Tools on Red Hat-based Systems

```bash
sudo yum groupinstall "Development Tools"
```

## General Steps for Installing Software from Source

### Step 1: Download the Source Code

Source code is typically distributed in compressed archive files (e.g., `.tar.gz`, `.tar.bz2`, `.zip`). Download the source code from the official website or a trusted source.

#### Example: Downloading `wget` Source Code

```bash
wget https://ftp.gnu.org/gnu/wget/wget-1.21.1.tar.gz
```

### Step 2: Extract the Source Code

Extract the downloaded archive to access the source code files.

#### Example: Extracting `wget` Source Code

```bash
tar -xzvf wget-1.21.1.tar.gz
```

### Step 3: Configure the Build

Navigate to the extracted source code directory and run the `configure` script to prepare the build environment. This script checks for necessary dependencies and configures the build options.

#### Example: Configuring `wget`

```bash
cd wget-1.21.1
./configure
```

### Common `configure` Options

- **`--prefix=PREFIX`**: Specify the installation directory (default is `/usr/local`).
- **`--enable-feature`**: Enable a specific feature.
- **`--disable-feature`**: Disable a specific feature.

#### Example: Configuring `wget` with Custom Prefix

```bash
./configure --prefix=/opt/wget
```

### Step 4: Build the Software

Compile the source code into executable binaries using the `make` command.

#### Example: Building `wget`

```bash
make
```

### Step 5: Install the Software

Install the compiled binaries and any other necessary files to the specified directory using the `make install` command. This step typically requires superuser privileges.

#### Example: Installing `wget`

```bash
sudo make install
```

### Step 6: Verify the Installation

Ensure the software is installed correctly by checking its version or running a basic command.

#### Example: Verifying `wget`

```bash
/opt/wget/bin/wget --version
```

## Managing Software Installed from Source

### Uninstalling Software

To uninstall software installed from source, navigate to the source code directory and run the `make uninstall` command. This step also typically requires superuser privileges.

#### Example: Uninstalling `wget`

```bash
cd wget-1.21.1
sudo make uninstall
```

### Keeping Track of Source Installations

Since software installed from source is not tracked by the system's package manager, it is important to maintain documentation of installed software, including the source directory, configuration options, and installation paths.

## Conclusion

Installing software from source provides flexibility and control over the installation process, allowing for customization to meet specific needs. By following the general steps outlined in this lecture, you can successfully download, configure, build, and install software from source code. This knowledge is essential for handling software that is not available in package repositories or when specific configurations are required.