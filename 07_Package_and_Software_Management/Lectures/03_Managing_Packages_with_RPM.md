# Managing Packages with RPM

RPM (Red Hat Package Manager) is a powerful package management system used by Red Hat-based distributions, such as CentOS and Fedora. RPM simplifies the process of installing, updating, and removing software packages, ensuring that dependencies are managed correctly.

## Installing Packages with RPM

### Basic Installation

To install a package using RPM, use the `rpm -i` command. This command installs the specified package.

#### Example: Installing `htop`
```bash
sudo rpm -i htop-2.2.0-3.el7.x86_64.rpm
```
- `sudo rpm -i htop-2.2.0-3.el7.x86_64.rpm`: Installs the `htop` package from the specified RPM file.

### Installing Packages with YUM

YUM (Yellowdog Updater, Modified) is a higher-level package manager that uses RPM packages but handles dependencies automatically. To install a package using YUM, use the `yum install` command.

#### Example: Installing `htop`
```bash
sudo yum install htop
```
- `sudo yum install htop`: Installs the `htop` package and resolves any dependencies.

## Removing Packages with RPM

### Basic Removal

To remove a package using RPM, use the `rpm -e` command. This command removes the specified package.

#### Example: Removing `htop`
```bash
sudo rpm -e htop
```
- `sudo rpm -e htop`: Removes the `htop` package.

### Removing Packages with YUM

To remove a package using YUM, use the `yum remove` command.

#### Example: Removing `htop`
```bash
sudo yum remove htop
```
- `sudo yum remove htop`: Removes the `htop` package and its dependencies.

## Updating Packages with YUM

### Basic Update

To update all installed packages to their latest versions, use the `yum update` command.

#### Example: Updating All Packages
```bash
sudo yum update
```
- `sudo yum update`: Updates all installed packages to their latest versions.

### Updating a Specific Package

To update a specific package, specify the package name with the `yum update` command.

#### Example: Updating `htop`
```bash
sudo yum update htop
```
- `sudo yum update htop`: Updates the `htop` package to its latest version.

## Searching for Packages with YUM

### Basic Search

To search for a package by name or description, use the `yum search` command.

#### Example: Searching for `htop`
```bash
yum search htop
```
- `yum search htop`: Searches for packages related to `htop`.

## Managing Repositories with YUM

### Adding a Repository

To add a new repository, create a new file in the `/etc/yum.repos.d/` directory with the `.repo` extension and add the repository details.

#### Example: Adding a New Repository
```bash
sudo nano /etc/yum.repos.d/example.repo
```
- Add the following content to the file:
  ```plaintext
  [example-repo]
  name=Example Repository
  baseurl=http://example.com/repo
  enabled=1
  gpgcheck=1
  gpgkey=http://example.com/repo/RPM-GPG-KEY-example
  ```

### Removing a Repository

To remove a repository, delete the corresponding `.repo` file from the `/etc/yum.repos.d/` directory.

#### Example: Removing a Repository
```bash
sudo rm /etc/yum.repos.d/example.repo
```

### Listing Repositories

To list all configured repositories, use the `yum repolist` command.

#### Example: Listing Repositories
```bash
yum repolist
```
- `yum repolist`: Lists all active repositories.

## Verifying Package Integrity

RPM can verify the integrity of packages to ensure they have not been tampered with.

### Example: Checking Package Integrity
```bash
rpm -V htop
```
- `rpm -V htop`: Verifies the integrity of the `htop` package.

## Conclusion

RPM and YUM are powerful tools for managing software packages in Red Hat-based distributions. By mastering these commands, you can ensure your system remains up to date, secure, and running smoothly. This lecture has covered the essential tasks of installing, removing, updating, and searching for packages, as well as managing repositories and verifying package integrity.