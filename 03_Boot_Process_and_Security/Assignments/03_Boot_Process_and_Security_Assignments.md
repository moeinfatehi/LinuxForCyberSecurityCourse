# Boot Process and Security - Assessments

This document contains all assessments for the "Boot Process and Security" module. These assessments are designed to test your knowledge, understanding, and skills in securing the Linux boot process, from the initial power-on to the full loading of the operating system.

## Assignment 1: Secure Boot Configuration

### Objective
Configure Secure Boot to ensure that only verified software can be executed during the system's boot process.

### Instructions
1. Research how to enable and configure Secure Boot in your system's UEFI settings.
2. Document the steps taken to enable Secure Boot.
3. Describe how Secure Boot can prevent unauthorized modifications to the boot process.

## Assignment 2: Implementing Full Disk Encryption

### Objective
Set up Full Disk Encryption (FDE) using LUKS to protect the data stored on your system.

### Instructions
1. Install a Linux distribution that supports LUKS for disk encryption.
2. During installation, choose to encrypt your system drive using LUKS.
3. Document the installation process and configuration settings.
4. Demonstrate how to access the encrypted system by restarting and logging in.

## Assignment 3: GRUB Password Setup

### Objective
Secure the GRUB bootloader to prevent unauthorized changes to boot configurations.

### Instructions
1. Configure a GRUB password using the `grub-mkpasswd-pbkdf2` utility.
2. Update the GRUB configuration to require the password for editing boot entries.
3. Document the configuration changes and test by attempting to edit the GRUB menu at boot without entering the password.

## Quiz: Boot Process Security

- **Question 1**: What is the purpose of Secure Boot in the UEFI firmware settings?
- **Question 2**: Describe the benefits of Full Disk Encryption.
- **Question 3**: How does setting a password on GRUB enhance system security?

## Conclusion

These assessments are designed to challenge and enhance your understanding of how to secure a Linux system at the most critical point—its boot process. Successfully completing these tasks will prepare you for advanced responsibilities in system security and administration.
