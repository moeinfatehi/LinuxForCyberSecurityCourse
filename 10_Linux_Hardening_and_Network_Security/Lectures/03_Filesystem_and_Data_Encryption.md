# Filesystem and Data Encryption

Encrypting your data is a crucial part of securing a Linux system, especially in environments where sensitive information is stored. This lecture will cover how to encrypt your files, directories, and entire partitions using Linux Unified Key Setup (LUKS), as well as other encryption techniques such as encrypting home directories and swap space.

## 1. Introduction to Filesystem and Data Encryption

Filesystem and data encryption protect your data by ensuring that even if someone gains unauthorized access to the physical storage, they won’t be able to read the data without the correct encryption key.

Encryption is particularly important for laptops, servers, and any system where sensitive data is stored.

## 2. Encrypting Partitions with LUKS

LUKS (Linux Unified Key Setup) is the standard for Linux disk encryption. It is commonly used to encrypt partitions or entire disks, providing strong encryption to protect data at rest.

### 2.1 Installing LUKS

LUKS is typically available by default on most Linux distributions, but it requires the `cryptsetup` package to manage encrypted volumes.

#### Installation (if not already installed):

- **Debian/Ubuntu:**
  ```bash
  sudo apt-get install cryptsetup
  ```

- **CentOS/RHEL:**
  ```bash
  sudo yum install cryptsetup
  ```

### 2.2 Creating an Encrypted Partition with LUKS

1. **Partition the Disk**: Create a new partition using `fdisk` or `parted`.
2. **Initialize LUKS on the Partition**:
   ```bash
   sudo cryptsetup luksFormat /dev/sdX1
   ```
   - Replace `/dev/sdX1` with the partition you want to encrypt.
3. **Open the Encrypted Partition**:
   ```bash
   sudo cryptsetup luksOpen /dev/sdX1 encrypted_partition
   ```
   - This creates a decrypted mapping at `/dev/mapper/encrypted_partition`.
4. **Format the Encrypted Partition**:
   ```bash
   sudo mkfs.ext4 /dev/mapper/encrypted_partition
   ```
5. **Mount the Encrypted Partition**:
   ```bash
   sudo mount /dev/mapper/encrypted_partition /mnt
   ```

### 2.3 Automating the Mounting of Encrypted Partitions

To ensure your encrypted partition is automatically mounted at boot, you can configure `/etc/crypttab` and `/etc/fstab`.

1. **Edit `/etc/crypttab`**:
   ```bash
   encrypted_partition /dev/sdX1 none luks
   ```
2. **Edit `/etc/fstab`** to mount the decrypted partition:
   ```bash
   /dev/mapper/encrypted_partition /mnt ext4 defaults 0 2
   ```

### 2.4 Managing LUKS Volumes

You can add additional keys, remove keys, or change passphrases on your LUKS volumes using `cryptsetup`.

#### Example: Adding a New Key

```bash
sudo cryptsetup luksAddKey /dev/sdX1
```

#### Example: Removing a Key

```bash
sudo cryptsetup luksRemoveKey /dev/sdX1
```

## 3. Encrypting Swap Space

Encrypting your swap space prevents sensitive information that may be written to swap from being exposed to unauthorized access.

### 3.1 Temporary Swap Encryption with Random Keys

One approach is to encrypt swap space with a random key that changes at every reboot. This method is secure and easy to implement.

#### Example: Configuring Encrypted Swap Space

1. **Turn off Swap**:
   ```bash
   sudo swapoff -a
   ```
2. **Edit `/etc/crypttab`**:
   ```bash
   cryptswap1 /dev/sdX2 /dev/urandom swap,cipher=aes-xts-plain64,size=256
   ```
   - Replace `/dev/sdX2` with your swap partition.
3. **Edit `/etc/fstab`**:
   ```bash
   /dev/mapper/cryptswap1 none swap sw 0 0
   ```
4. **Turn Swap Back On**:
   ```bash
   sudo swapon -a
   ```

### 3.2 Persistent Swap Encryption

If you need encrypted swap that persists across reboots (e.g., for hibernation), you can set it up similarly to encrypted partitions using LUKS.

## 4. Secure File Storage with Encrypted Directories

Encrypting individual files or directories is useful when full-disk encryption is not practical. `eCryptfs` is a popular tool for this purpose, and it's often used to encrypt home directories.

### 4.1 Encrypting Home Directories with `eCryptfs`

1. **Install `eCryptfs`**:
   - **Debian/Ubuntu**:
     ```bash
     sudo apt-get install ecryptfs-utils
     ```

2. **Set Up Encrypted Home Directory**:
   - Encrypt the home directory for a new or existing user by running:
     ```bash
     sudo ecryptfs-setup-private
     ```
   - Follow the prompts to configure encryption for your home directory.

### 4.2 Mounting and Unmounting Encrypted Directories

Encrypted directories can be mounted and unmounted as needed, providing secure storage for sensitive files.

#### Example: Manually Mounting an Encrypted Directory

```bash
ecryptfs-mount-private
```

#### Example: Manually Unmounting an Encrypted Directory

```bash
ecryptfs-umount-private
```

## 5. Secure Backup Practices

It's important to secure your backups, ensuring that sensitive data remains protected even when stored off-site or on external drives.

### 5.1 Encrypting Backup Data

Encrypting your backups ensures that even if the backup media is lost or stolen, the data remains secure.

#### Example: Creating an Encrypted Backup with `tar` and `gpg`

1. **Create a Compressed Archive**:
   ```bash
   tar -czvf backup.tar.gz /path/to/data
   ```
2. **Encrypt the Archive**:
   ```bash
   gpg --output backup.tar.gz.gpg --symmetric backup.tar.gz
   ```
   - This command uses symmetric encryption to protect the backup with a passphrase.

### 5.2 Automating Encrypted Backups

Automating encrypted backups with cron jobs or other scheduling tools ensures that your data is regularly secured without manual intervention.

#### Example: Automating Encrypted Backups with `cron`

1. **Create a Backup Script**:
   ```bash
   #!/bin/bash
   tar -czvf /backup/backup.tar.gz /path/to/data
   gpg --output /backup/backup.tar.gz.gpg --symmetric /backup/backup.tar.gz
   rm /backup/backup.tar.gz
   ```

2. **Schedule the Script with `cron`**:
   ```bash
   crontab -e
   ```
   Add the following line to run the script daily at midnight:
   ```bash
   0 0 * * * /path/to/backup_script.sh
   ```

## Conclusion

Encrypting your files, directories, partitions, and backups is a crucial part of securing your Linux system. By implementing LUKS encryption, encrypted home directories, and secure backup practices, you can ensure that your data remains protected even in the event of unauthorized access or physical theft. In the next lecture, we will cover basic network security measures to protect your system from external threats.