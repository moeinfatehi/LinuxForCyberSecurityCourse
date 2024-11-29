### Exploring the Filesystem Hierarchy of my kali linux machine
This linux filesystem mounting starts form the root '/'. In linux there is a sigle File system tree for all the 
different storage devices and partitions. From '/' there are different directrories that are common and standarise for most linux distribution by FSH(FileSystem Hierarchy Standard).
![Screenshot (309)](https://github.com/user-attachments/assets/8e746ad4-2edb-4f99-9f30-30ce5abea70c)

1. **/boot**
![Screenshot (313)](https://github.com/user-attachments/assets/fdfecf54-303e-4623-b464-15bfbba4e451)
This directory contain the booting process related file and configuration like kernal images and bootloader. As this directory contain the
file like

vmlinuz* -> Kernal images files. It is firstly decompress and load the kernal into memory during booting.

system-map* -> Kernal files.

initrd* -> temporary file system mounting files and used to mount a temporary file system to initialise the hardware

grub -> bootloader related file like grub configuration `grub.conf`.

2. **/root**
![Screenshot (311)](https://github.com/user-attachments/assets/23fa1940-5907-4b69-80a5-b696535e7c32)
This is the home directory for root user. It contain the files related to root user activity.
This file can only be accessed by the root user and the users which has sudo permissions.
It contains dirt like Documents, Desktop, Pictures, Music etc which store different file owned and used by the root user. It also contain dirt like .ssh which contain ssh key and authorized_key.

3. **/home**
![Screenshot (312)](https://github.com/user-attachments/assets/f8b04c7a-da86-4306-8b17-437e77c90908)
This is the home directory for normal users on the system. It contain different dirt for each user. In each user directory there is file related to that particular user activity.
Each User dirtory is owned and access their owner users, root user and the users which have sudo privilage.
It also contain dirt like Documents, Desktop, Pictures, Music etc which store different file owned and used by the particular user.
In my case I had `/home/kali` for kali user.

4. **/bin**
![Screenshot (310)](https://github.com/user-attachments/assets/8e2008b2-9e1d-4d37-96ce-5a496d92163b)
This is the diretory which contain the binary file and program related to various system commands and operation which is used by all users on the system like pwd, cd, ls etc.
These are the files that are being used when the system runs in single user mode.
Here it contain file related to command and service like firefox, paste cmd, sort command etc.

 5. **/sbin**
![Screenshot (315)](https://github.com/user-attachments/assets/7f3c766b-009d-4365-9b85-d4483825a0ce)
This is the directory which also contain the binary file and programs related to various system command and services that are only used by the root user and user which have sudo access. It includes commands like systemctl, sudo ,init, ip etc.
Here it contain file related to commands like mount, systemctl, cron, init etc.

6. **/etc**
![Screenshot (314)](https://github.com/user-attachments/assets/393f7fa7-5154-4334-8fea-6f7a88847c51)
This is the directory which contain the various system configuration file related to various services.
It also contains the sensitive file like /etc/passwd and /etc/shadow. Hence this directory contain the configuration and sensitive information file.
It contains-

 /etc/resolv.conf -> DNS resolution file.

 /etc/hosts -> Host domain for a specific ip.
 
 /etc/passwd -> contain information about different user on the system.

 /etc/mysql.conf -> Mysql service related configuration file.

7. **/usr**
![Screenshot (316)](https://github.com/user-attachments/assets/47d1cb90-fe0a-460b-b0c7-e264ee5f4a3b)
It contains the various application, utilities and program installed on the system.

It contains subdirectory like-

/usr/bin -> contians the binary file related to program and application.

/usr/lib -> contain libraries and program used by different application.

/usr/share -> contain data (like wordlists) related different application and programs.
![Screenshot (317)](https://github.com/user-attachments/assets/f6ada202-15c2-4db8-a997-be81040a5068)
![Screenshot (318)](https://github.com/user-attachments/assets/97d4f98c-3f11-4eb5-9c50-04ab1c36122c)

8. **/lib**
![Screenshot (325)](https://github.com/user-attachments/assets/bf159157-9da2-4736-bcec-c987a5f52608)
It contain different libraries and system modules that are used by /bin and /sbin and other programs.
It contains libraries used by apache2 server, php, mysql etc.

9. **/var**
![Screenshot (320)](https://github.com/user-attachments/assets/399236c5-0dc4-4ad2-88f2-0525eab44760)
It contain the variable data that is being used by different application program.
It contain subdirtory like `/var/www` which contain the data being displayed and served on the webserver and also `/var/log/` logging information about different service being running on the system.

10. **/opt**
![Screenshot (319)](https://github.com/user-attachments/assets/8298ba9f-0fb5-4c62-bf59-bdbfec249c4c)
It is option directory to store the intalled program. It contain the program that is not intalled from the package manager.

11. **/tmp**
![Screenshot (321)](https://github.com/user-attachments/assets/698945d7-1a38-4bcd-9d25-f2e78273e7f7)
It mainly contain the temporary data related to various running application and service which is being deleted on reboot.

12. **/mnt**
![Screenshot (322)](https://github.com/user-attachments/assets/69110c38-8ad1-4203-83ce-bf001fbcf11a)
It is the directory which contain/temporary mount the external filesystem to device like extenal harddisk, USB device and nfs share.
In my case it is mounting the host shared folder to my virtual machine.

13. **/dev**
![Screenshot (323)](https://github.com/user-attachments/assets/d99d7243-9724-47f9-8ea6-df280b87fe12)
It is the directory which contain the hardware device related files and drivers. It also contains files for external hardware devices like printer, usb etc. 
    
14. **/media**
![Screenshot (324)](https://github.com/user-attachments/assets/5b30bc00-de74-4111-89c7-6d5fce60ec2c)
It is mainly used by removeable devices like usb-drive and CD-ROMs etc.
