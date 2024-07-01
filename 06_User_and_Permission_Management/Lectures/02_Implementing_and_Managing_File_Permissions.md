# Implementing and Managing File Permissions

This lecture provides an in-depth look at managing file permissions in Linux. Properly setting and understanding file permissions is crucial for system security and effective access control.

## Basic File Permissions

In Linux, file permissions determine who can read, write, or execute a file. Permissions are assigned to three categories of users:
- **Owner**: The user who owns the file.
- **Group**: Users who are members of the file's group.
- **Others**: All other users.

### Understanding Permission Symbols

File permissions are displayed as a string of characters when using the `ls -l` command:
- The first character indicates the file type (`-` for a regular file, `d` for a directory).
- The next three characters represent the owner's permissions.
- The following three characters represent the group's permissions.
- The last three characters represent the others' permissions.

Example:
```bash
ls -l myfile.txt
-rw-r--r-- 1 user group 0 Jan 1 12:00 myfile.txt
```
- `-rw-r--r--`: The owner has read and write permissions, the group has read permissions, and others have read permissions.

### Changing File Permissions with chmod

The `chmod` command is used to change file permissions. Permissions can be set using symbolic or numeric (octal) notation.

#### Symbolic Notation

- **Adding Permissions**:
  ```bash
  chmod u+x myfile.sh
  ```
  - `u+x`: Adds execute permission for the owner.

- **Removing Permissions**:
  ```bash
  chmod g-w myfile.txt
  ```
  - `g-w`: Removes write permission for the group.

- **Setting Permissions**:
  ```bash
  chmod o=r myfile.txt
  ```
  - `o=r`: Sets read-only permission for others.

#### Numeric Notation

Permissions can also be set using a three-digit octal number. Each digit represents a category of users (owner, group, others) and is the sum of the values for read (4), write (2), and execute (1) permissions.

Example:
```bash
chmod 754 myfile.txt
```
- `7` (owner): read (4) + write (2) + execute (1) = 7
- `5` (group): read (4) + execute (1) = 5
- `4` (others): read (4) = 4

### Viewing File Permissions

Use the `ls -l` command to view file permissions:
```bash
ls -l myfile.txt
```

## Advanced Permissions

### Setuid, Setgid, and Sticky Bit

#### Setuid

The setuid bit (`s`) allows a file to be executed with the privileges of the file's owner.

Example:
```bash
chmod u+s myscript.sh
```

#### Setgid

The setgid bit (`s`) allows a file to be executed with the privileges of the file's group. For directories, it ensures new files inherit the directory's group.

Example:
```bash
chmod g+s mydir
```

#### Sticky Bit

The sticky bit is a permission bit that is set on directories to restrict file deletion. When the sticky bit is set on a directory, only the file owner, the directory owner, or the root user can delete or rename the files within that directory. This is commonly used on directories like `/tmp` to prevent users from deleting each other's files.

#### Example: Using the Sticky Bit

1. Create a directory and set the sticky bit.
   ```bash
   mkdir /tmp/shared
   chmod +t /tmp/shared
   ```

2. Verify the sticky bit is set. The sticky bit is represented by a `t` at the end of the permission string.
   ```bash
   ls -ld /tmp/shared
   drwxrwxrwt 2 root root 4096 Jan 1 12:00 /tmp/shared
   ```

3. Create two files within the directory as two different users.
   ```bash
   su - user1
   touch /tmp/shared/file1
   su - user2
   touch /tmp/shared/file2
   ```

4. Attempt to delete each other's files.
   ```bash
   su - user1
   rm /tmp/shared/file2
   rm: cannot remove '/tmp/shared/file2': Operation not permitted

   su - user2
   rm /tmp/shared/file1
   rm: cannot remove '/tmp/shared/file1': Operation not permitted
   ```

In this example, `user1` and `user2` cannot delete each other's files because the sticky bit is set on the `/tmp/shared` directory.

### Access Control Lists (ACLs)

ACLs provide a more flexible permission mechanism for file systems by allowing you to set permissions for specific users or groups beyond the traditional owner, group, and others model. 

To use ACLs, you need to ensure the `acl` package is installed on your system.

#### Installing the ACL Package

On Ubuntu, you can install the `acl` package using the following command:
```bash
sudo apt-get install acl
```

#### Example: Setting and Viewing ACLs

1. Create a file and set an ACL to grant read permissions to a specific user.
   ```bash
   touch myfile.txt
   setfacl -m u:alice:r myfile.txt
   ```

2. Verify the ACL settings.
   ```bash
   getfacl myfile.txt
   # file: myfile.txt
   # owner: user
   # group: group
   user::rw-
   user:alice:r--
   group::---
   mask::r--
   other::---
   ```

In this example, `alice` is granted read permissions on `myfile.txt`, regardless of the file's owner, group, and other permissions.


## Conclusion

Understanding and managing file permissions is crucial for maintaining security and control over a Linux system. By using basic and advanced permission settings, as well as ACLs, you can ensure that files and directories are accessible only to those who need them.