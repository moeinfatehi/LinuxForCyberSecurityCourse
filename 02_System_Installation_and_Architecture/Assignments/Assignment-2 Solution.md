#### To implement the full disk encryption on a linux machine
Here I am using a kali linux (debian distribution) virtual machine to implement the full disk encryption but for that we must ensure that
the Operating system we are using must support the full disk encryption. As the debian 8 and above distribution
supports the full disk encryption.

For that we have to implement the disk encryption during its installation. But we can also perform it after the intallation
using tools like LUKUS. It is recommended to implement it using the installation time because I ensure the complete
disk encryption.

1. Firstly install a ISO file of your favourite linux distribution which you want to install, Here I am using **Kali
Linux version 2024 ISO.** You cna simpley install it from official kali website.
2. After installation of ISO file, you must also have a virtualisation software like virtual box, Vmware workstation or hypervisior etc to create
a virtual linux machine into you host machine. For that I had my vmware workstation player 17.6.
3. Since here You have the Vmware workstation and the ISO file of you linux distribution is intalled.
4. Now open the Vmware and create a new virtual machine, and select boot from the ISO file. Also set the basic
hardware configuration like virtual disk (approx 40gb), Physical memory(min 2 gb) etc.
![Screenshot (326)](https://github.com/user-attachments/assets/c1afb3f1-31e6-4ae1-880a-090dcfbe62e2)

5. Now simpley start the virtual machine to boot in the live mode form ISO.
6. Now go through the wizard for setting up the machine name, Username, domain etc.
![Screenshot (327)](https://github.com/user-attachments/assets/7f65870a-40e1-480b-9989-6527a708eb00)

7. Now you have a wizard to set up the partion disk, To implement the FDE select the Guided -use entire disk and set up encrypted LVM and continues.
(It uses LVM tool to encryption the disk).
![Screenshot (328)](https://github.com/user-attachments/assets/7a60f30a-05f2-4c86-b27b-5f24e1c9ddcf)

8. Now next wizard pop to accept the write partion on the disk and configure LVM by Selecting Yes and continue.
![Screenshot (329)](https://github.com/user-attachments/assets/9e9535d0-f6bc-4434-ac38-45cf2df6e5ae)

9. Now the partion is created for the vm with LVM
![Screenshot (330)](https://github.com/user-attachments/assets/0893f1cc-30c9-419a-a29e-5ec7f5e7a1d9)

10. Now set passphrase for the encryption of the disk.
![Screenshot (332)](https://github.com/user-attachments/assets/22d3e452-6573-4271-8d16-a956d7a77298)

11. Now review the partions created having two mainly root and swap partions.
![Screenshot (333)](https://github.com/user-attachments/assets/d2c70f60-5b70-4c49-966f-ddab37fa54b5)

12. Now confirm the partion to be formated and LVM is implemented by selection Yes.
![Screenshot (334)](https://github.com/user-attachments/assets/8a74c524-a2d3-4d07-95a5-3583196338e1)

13. Finally, here we got the intallation of the OS starts and its necessary module.
![Screenshot (335)](https://github.com/user-attachments/assets/855d36a4-aaa5-42da-8e89-030cba6f7a5f)

14. Now select the desktop environment and next to intall
![Screenshot (336)](https://github.com/user-attachments/assets/0aabceca-29b3-4bea-a4ba-d9c9bd60a3e4)

15. Now there is installation of default module and software with the linux distribution
![Screenshot (337)](https://github.com/user-attachments/assets/bb7ef53a-7023-4e57-ade9-0286c54ebd6c)

16. **We had successful Install the Kali linux with full disk encryption using ISO image Hurry!......**

17. After encryption, the Kali operating system requires a password at boot time to decrypt your drive.
You can also use the cryptsetup utility to manage decryption keys and partitions.
