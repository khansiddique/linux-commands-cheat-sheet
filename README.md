# linux-commands-cheat-sheet

## The cheat-sheet
This cheat sheet is based on the book "Linux Basics for Hackers" by OccupyTheWeb.
![image](https://github.com/shanickcuello/linux-commands-cheat-sheet/assets/44624042/ee196b6a-8392-4c5a-82aa-aa04bc5b7c61)

Please note that this cheat sheet is not intended to replace the book in any way. It serves simply as a reminder of the most commonly used commands. It does not provide exhaustive details of each command. For more in-depth information, I recommend using the `man` command or `--help` option to learn about each command.
The book provides detailed explanations of each command with examples, which I strongly recommend exploring. You can find it on Amazon and their website:
[Amazon Link](https://www.amazon.com/-/es/OccupyTheWeb/dp/1593278551)
[Website Link](https://www.hackers-arise.com/welcome)


### Basic Commands

| Command | Description | Example Usage |
|---------|-------------|---------------|
| `pwd`   | Prints the current working directory. | `pwd` |
| `whoami`| Displays the current username. | `whoami` |
| `cd`    | Changes the current directory. | `cd /path/to/directory` |
| `ls`    | Lists directory contents. | `ls -la` |
| `--help`| Displays help information for a command. | `ls --help` |
| `man`   | Shows the manual for a command. | `man ls` |
| `locate`| Finds files by name. | `locate filename` |
| `find`  | Searches for files in a directory hierarchy. | `find /path -name filename` |
| `which` | Shows the path of a command. | `which ls` |
| `ps`    | Displays information about running processes. | `ps aux` |
| `cat`   | Concatenates and displays file contents. | `cat file.txt` |
| `mkdir` | Creates a new directory. | `mkdir new_directory` |
| `rm`    | Removes files or directories. | `rm file.txt` `rm -rf directory_name` |
| `rmdir` | Removes empty directories. | `rmdir empty_directory` |
| `mv`    | Moves or renames files or directories. | `mv oldname.txt newname.txt` |
| `touch` | Changes file timestamps or creates an empty file. | `touch newfile.txt` |

### The Linux Filesystem 

![image](https://github.com/khansiddique/linux-commands-cheat-sheet/blob/main/linux-file-system.jpeg.png)

### Text Manipulation

| Command | Description | Example Usage |
|---------|-------------|---------------|
| `cat`   | Concatenates and displays file contents. | `cat file.txt` |
| `head`  | Outputs the first part of files. | `head -n 10 file.txt` |
| `tail`  | Outputs the last part of files. | `tail -n 10 file.txt` |
| `nl`    | Numbers lines of files. | `nl file.txt` |
| `sed`   | Stream editor for filtering and transforming text. | `sed 's/old/new/g' file.txt` |
| `more`  | View file contents one screen at a time. | `more file.txt` |
| `less`  | Similar to `more`, but with backward movement. | `less file.txt` |

### System Management Commands

| Command   | Description | Example Usage |
|-----------|-------------|---------------|
| `ps`      | Displays information about running processes. | `ps` |
| `ps aux`  | Displays detailed information about all running processes. | `ps aux` or `ps aux \| grep msfconsole`|
| `top`  | Finding the Greediest Processes with top. | `top`|
| `nice`    | Runs a command with modified scheduling priority. command:_/bin/slowprocess_ | `nice -n 10 command` or `nice -n -10 /bin/slowprocess` |
| `kill`    | Sends a signal to terminate a process. SIGHUP: -1, SIGINT: -2, SIGQUIT: -3, SIGTERM: -15, SIGKILL: -9 | `kill 1234` or `kill -1 6996` or `kill -9 6996` |
| `killall` | Kills processes by name. | `killall firefox` |
| `fg`      | Brings a background job to the foreground. | `fg %1` |
| `at`      | Schedules commands to run at a later time. `at` command is used to setup a _daemon_ -- a background process -- which is useful for scheduling a job to run once at some point in the future | `echo "command" \| at 10:00` |
| `chown`   | Changes file ownership. | `chown user:group file.txt` |
| `chmod`   | Changes file permissions. Changing permission with UGO: U - User (or owner), G - group, O - others. _Three Operations:_ `- Removes a permission, + Adds a permission, = Sets a Permission`. Changing Permission with Decimal Notation: `r-4, w-2, x-1 and 4+2+1=7`   | `chmod 755 file.txt` or  `chmod u-w file.txt` or  `chmod u+x, o+x file.txt` |

- **`NOTE:`** _daemon_ -- means a Process that runs in the background.

### Special Permissions

- The 3 general-purpose permissions, `rwx`, Linux has 3 special permissions that are slightly more complicated.
- These special permissions are: set user ID (or SUID), set group ID (or SGID), and sticky bit
- `SUID bit` : Temporarily grant the owner's priviledges or Root user priviledges (to _/etc/shadow_ file) to execute the file by setting the `SUID` bit on the program.
- `SGID bit` : SGID also grants temporary elevated permissions, but it grants the permissions of the file owner's group, rather than of the file's owner. This means that, with an SGID bit set, someone without execute permission can execute a file if the owner belongs to the group that has permission can execute that file.



| Command   | Description | Example Usage |
|-----------|-------------|---------------|
| `chmod 4644 filename`     | Granting Temporary Root permission with SUID. to set the SUID bit enter a `4` before the regular permission, so a file with a new resulting premission of 644 is representened as 4644 when the SUID bit is set.  | `chmod 4644 /etc/shadow` |
| `chmod 2644 filename` | Granting the Root Users's Group permission SGID. to set the SGID bit enter a `2` before the regular permission, so a file with a new resulting premission of 644 is representened as `2644` when the SUID bit is set.  | `chmod 2644 /etc/shadow` |
| `find`     | Special permissions, Privilege Escalation, and the Hacker: E.g. we ask Kali to start looking at the top of the file-system with the `/` syntax. It then looks everywhere below `/` for files that are owned by `root`, specified with user `root`, and that have the SUID permission bit set (-prem -4000)   | `find / -user root -perm -4000` |

**The Outmoded Sticky Bit**
- - **`NOTE:`** _sticky bit_ -- is a permission bit that you can set on a directory to allow a user to delete or rename files within that directory. However, the _sticky bit_ is a legacy of older unix systems, and modern systems (like Linux) ignore it.

### Add or Install Software Commands

| Command   | Description | Example Usage |
|-----------|-------------|---------------|
| `apt`     | Package handling utility for Debian-based systems. | `apt update` |
| `apt-get` | APT package handling utility. | `apt-get install package_name` |

### Network Commands

| Command                | Description | Example Usage |
|------------------------|-------------|---------------|
| `ifconfig`             | Configures network interfaces. | `ifconfig eth0` |
| `iwconfig`             | Configures wireless network interfaces. | `iwconfig wlan0` |
| `dhclient`             | Dynamic Host Configuration Protocol Client. | `dhclient eth0` |
| `dig`                  | DNS lookup utility. | `dig example.com` |
| `iwlist wlan0 scan`    | Scans for available wireless networks. | `iwlist wlan0 scan` |
| `nmcli dev wifi`       | Lists available Wi-Fi networks. | `nmcli dev wifi` |
| `nmcli dev wifi connect some-network password somePassword` | Connects to a Wi-Fi network using `nmcli`. | `nmcli dev wifi connect MyWiFi password MyPassword` |
| `airmon-ng`            | WLAN monitor mode enabling tool. | `airmon-ng start wlan0` |
| `airmon-ng start wlan0`| Puts interface `wlan0` into monitor mode. | `airmon-ng start wlan0` |
| `airodump-ng wlan0`    | Captures raw 802.11 frames. | `airodump-ng wlan0` |
| `aireplay-ng`          | Packet injection tool for 802.11 networks. | `aireplay-ng -0 5 -a 00:11:22:33:44:55 wlan0` |
| `aircrack-ng`          | 802.11 WEP and WPA-PSK keys cracking program. | `aircrack-ng -w wordlist.txt captured.cap` |
| `hcitool`              | Configures Bluetooth connections. | `hcitool scan` |

[802.11](https://en.wikipedia.org/wiki/IEEE_802.11)

### User Environment Variable Management Commands

| Command                       | Description | Example Usage |
|-------------------------------|-------------|---------------|
| `env`                         | Displays the current environment variables. | `env` |
| `set \| more`                  | Displays all shell variables and functions, paginated. | `set \| more` |
| `HISTSIZE`                    | Sets the number of commands to remember in the command history. | `HISTSIZE=1000` |
| `echo $HISTSIZE`              | Displays the current value of the HISTSIZE variable. | `echo $HISTSIZE` |
| `export`                      | Sets environment variables or marks shell variables for export. | `export VAR=value` |
| `export HISTSIZE`             | Exports the HISTSIZE variable to the environment. | `export HISTSIZE=1000` |
| `echo $PATH`                  | Displays the current value of the PATH variable. | `echo $PATH` |
| `PATH=$PATH:someNewDirectory`                  | Adding to the PATH variable. | `PATH=$PATH:/root/newhackingtool` |
| `someNewVariable="Some value"`| Sets a new shell variable. | `someNewVariable="Some value"` |
| `echo $someNewVariable`       | Displays the value of `someNewVariable`. | `echo $someNewVariable` |
| `unset someNewVariable`       | Removes `someNewVariable` from the shell environment. | `unset someNewVariable` |

### Compressing and Decompressing Commands

| Command         | Description | Example Usage |
|-----------------|-------------|---------------|
| `tar`           | Creates an archive from a list of files. | `tar cvf archive.tar file1 file2` |
| `tar -rvf`      | Appends files to an existing archive. | `tar -rvf archive.tar newfile` |
| `tar -xvf`      | Extracts files from an archive. | `tar -xvf archive.tar` |
| `tar -xf`       | Extracts files from an archive without verbose output. | `tar -xf archive.tar` |
| `gzip`          | Compresses files using gzip. | `gzip file.txt`  or `gzip file.*`|
| `gunzip`          | Decompresses files using gunzip. | `gunzip file.*` |
| `bzip2`         | Compresses files using bzip2. | `bzip2 file.txt` or `bzip2 file.*` |
| `bunzip2`         | Decompresses files using bzip2. | `bunzip2 file.*` |
| `compress`      | Compresses files using the compress program. | `compress file.txt` |
| `uncompress`    | Decompresses files compressed by the compress program. | `uncompress file.txt.Z` |
| `dd if=inputfile of=outputfile`    | Creating Bit-by-Bit or Physical Copies of Storage Devices. bs (block size: the number of bytes read / written per block). sector size, most often 4KB (4096 bytes) | `dd if=/dev/sdb of=/root/flashcopy` or `dd if=/dev/media of=/root/flashcopy bs=4096 conv=noerror` |

### Filesystem and Storage Device Management

| Command    | Description | Example Usage |
|------------|-------------|---------------|
| `cd`    | The Device Directory /dev. | `cd /dev` -> `ls -l` |
| `fdisk`    | To view the partitions on your Linux System. Note: HPFS/NTFS/ExFAT filesystem type. HPFS - High performance File Sysdtem , NTFS - New Technology File System , ExFAT - Extended File Allocation Table.  | `fdisk -l` |
| `lsblk`    | List Block Devices and Information with `lsblk`. | `lsblk` |

**How Linux Represents Storage Devices:**

##### Device-Naming System

| Device File    | Description | 
|------------|-------------|
| `sda`    | First SATA hard drive. | 
| `sdb`    | Second SATA hard drive. |
| `sdc`    | Third SATA hard drive. |
| `sdd`    | Fourth SATA hard drive. |

##### Drive Partitions: Partition-Labeling System

| Command    | Description | 
|------------|-------------|
| `sda1`    | The first partition (1) on the first (a) SATA drive. | 
| `sda2`    | The second partition (2) on the first (a) SATA drive. | 
| `sda3`    | The third partition (3) on the first (a) SATA drive. | 
| `sda4`    | The forth partition (4) on the first (a) SATA drive. | 

### Mounting and Unmounting Commands

| Command    | Description | Example Usage |
|------------|-------------|---------------|
| `mount`    | Mounts a filesystem. | `mount /dev/sdb1 /mnt` |
| `umount`   | Unmounts a filesystem. | `umount /mnt` |
| `fsck`     | Checks and repairs a filesystem. -p: options to have `fsck` automatically repair any problem with the device. | `fsck` -> `unmount /dev/sdb1` -> `fsck /dev/sdb1` or `fsck -p /dev/sdb1` |
| `df`       | Reports file system disk space usage. | `df -h` |

### Service and Database Commands

| Command              | Description | Example Usage |
|----------------------|-------------|---------------|
| `service`            | Controls system services. | `service apache2 start` |
| `show databases`     | Lists all databases in a DBMS. | `show databases` (MySQL) |
| `use mysql`          | Switches to the MySQL system database. | `use mysql` |
| `use somedatabase`   | Switches to a specific database in DBMS. | `use somedatabase` (MySQL) |
| `show tables`        | Lists tables in the current database. | `show tables` (MySQL) |
| `describe sometable` | Shows the structure of a table. | `describe sometable` (MySQL) |
| `su postgres`        | Switches user to `postgres` (switch user). | `su postgres` |
| `db_status`           | Checks the status of a database (generic). | `db_status` |

### Network Tracing and Proxy Commands

| Command                                     | Description | Example Usage |
|---------------------------------------------|-------------|---------------|
| `traceroute www.shanick.dev`                | Traces the route packets take to a network host. | `traceroute www.shanick.dev` |
| `proxychains`                               | Forces any TCP connection made by any given application through a proxy. | `proxychains command` |
| `proxychains nmap`       | Uses `nmap` with `proxychains` to scan a host through a proxy. | `proxychains nmap -sV -T5 10.19.15.2` |
| `cat /etc/proxychains.conf`         | Displays the content of `/etc/proxychains.conf` using `cat`. | `cat /etc/proxychains.conf` |
| `proxychains firefox www.shanick.dev`       | Opens Firefox and forces it to use a proxy specified in `proxychains.conf`. | `proxychains firefox www.shanick.dev` |

### System Information and Kernel Commands

| Command                           | Description | Example Usage |
|-----------------------------------|-------------|---------------|
| `uname -a`                        | Displays system information including kernel version. | `uname -a` |
| `cat /proc/version`               | Displays Linux kernel version information. | `cat /proc/version` |
| `sysctl -a \| less`               | Displays kernel parameters and their values interactively. | `sysctl -a \| less` |
| `lsmod`                           | Lists loaded kernel modules. | `lsmod` |
| `modprobe -a <module name>`       | Loads specified kernel module(s). | `modprobe -a usb-storage` |
| `modprobe -r <module to delete>`  | Unloads specified kernel module. | `modprobe -r usb-storage` |
| `dmesg`                           | Displays kernel ring buffer messages. | `dmesg` |

### Scheduling Tasks and Service Management

| Command          | Description | Example Usage |
|------------------|-------------|---------------|
| `crontab -e`     | Edits the user's crontab file to schedule tasks. | `crontab -e` |
| `update-rc.d`    | Updates the System V init links for service control scripts. | `update-rc.d apache2 defaults` |
| `rrconf`         | Manages configuration for RunRev scripts. | `rrconf list` |

- 0 8 * * 1 /path/to/command
- 0 indicates the minute (in this case, 0).
- 8 indicates the hour (in this case, 8 AM).
- \* \* indicates that the task will run any day of the month and any month.
- 1 indicates that the task will run every Monday (Monday is day 1 of the week in cron).
- /path/to/command is the path to the command that will be executed.


### Proxy Servers

- To make your traffic even harder to trace, you can use more than one proxy, in a strategy known as a **proxy chain**.
- Kali Linux has an excellent proxying tool called proxychains that you can set up to obscure your traffic.


| Command          | Description | Example Usage |
|------------------|-------------|---------------|
| `proxychains`     | The syntax for the proxychains command is straightforward, as shown here. | `proxychains \<the command you want proxied> \<arguments>` |
| `proxychains nmap`    | if you wanted to use proxychains to scan a site with nmap anonymously, you would enter the following. | `proxychains nmap -sT -Pn \<IP address>` |
| `rrconf`         | Manages configuration for RunRev scripts. | `rrconf list` |


--- 

# Linux Journey

## Networking Nomad 

### Network Sharing

- Network Sharing: Learn about network sharing with `rsync, scp, nfs and more`.

#### 1. File Sharing Overview
   
| Command          | Description | Example Usage |
|------------------|-------------|---------------|
| `scp`     | To copy a file over from local host to a remote host. | `$ scp myfile.txt username@remotehost.com:/remote/directory` |
| `scp`    | To copy a file from a remote host to your local host. | `$ scp username@remotehost.com:/remote/directory/myfile.txt /local/directory` |
| `scp`         | To copy over a directory from your local host to a remote host. | `$ scp -r mydir username@remotehost.com:/remote/directory` |

#### 2. rsync

- (short for remote synchronization)
- These small optimizations allow greater file transfer flexibility and makes rsync ideal for directory synchronization remotely and locally, data backups, large data transfers and more.
- let's say that you were copying over a file and your network got interrupted, therefore your copy stopped midway. Instead of re-copying everything from the beginning, rsync will only copy over the parts that didn't get copied.

  
Some commonly-used `rsync` options:

- v - verbose output
- r - recursive into directories
- h - human readable output
- z - compressed for easier transfer, great for slow connections

| Command          | Description | Example Usage |
|------------------|-------------|---------------|
| `rsync`     | Copy/sync files on the same host. | `$ rsync -zvr /my/local/directory/one /my/local/directory/two` |
| `rsync`    | Copy/sync files to local host from a remote host. | `$ rsync /local/directory username@remotehost.com:/remote/directory` |
| `rsync`         | Copy/sync files to a remote host from a local host. | `$ rsync username@remotehost.com:/remote/directory /local/directory` |

#### 3. Simple HTTP Server

- Python has a super useful tool for serving files over HTTP. 

| Command          | Description | Example Usage |
|------------------|-------------|---------------|
| `python`     | grab the IP address of the machine you ran this on and then on another machine access it in the browser with: http://IP_ADDRESS:8000. | `$ python -m SimpleHTTPServer` |

#### 4. NFS

- The most standard network file share for Linux is NFS (Network File System), NFS allows a server to share directories and files with one or more clients over the network.

| Command          | Description | Example Usage |
|------------------|-------------|---------------|
| `service` &   `mount`   | Setting up NFS client. | `$ sudo service nfsclient start` -> $ sudo mount server:/directory /mount_directory|


##### Automounting

- Let's say you use the NFS server quite often and you want to keep it permanently mounted, normally you think you'd edit the _/etc/fstab_ file, but you may not always get a connection to the server and that can cause issues on bootup. - Instead what you want to do is setup **automounting** so that you can connect to the NFS server when you need to.
- This is done with the **automount** tool or in recent versions of Linux **amd**.
- When a file is accessed in a specified directory, automount will look up the remote server and automatically mount it.

#### 5. Samba
   
- In the early days of computing, it became necessary for _Windows machines to share files with Linux machines_, thus the **Server Message Block (SMB) protocol** was born.
- SMB was used for _sharing files between Windows operating systems (Mac also has file sharing with SMB)_ and then it was later cleaned up and optimized in the form of the **Common Internet File System (CIFS) protocol**.

- Samba is what we call the Linux utilities to work with CIFS on Linux. In addition to **file sharing**, you can also _share resources like printers_.
- The Samba package includes a command line tool called **smbclient** that you can use to access any Windows or Samba server. Once you're connected to the share you can _navigate and transfer files_.

##### Create a network share with Samba


| Command          | Description | Example Usage |
|------------------|-------------|---------------|
| `apt update`     | Let's go through the basic steps to create a network share that a Windows machine can access. Maching update | `$ sudo apt update` |
| `apt install`    | Install Samba | `$ sudo apt install samba` |
| `vi`    | Setup smb.conf: The configuration file for Samba is found at /etc/samba/smb.conf, this file should tell the system what directories should be shared, their access permissions, and more options. | `$ sudo vi /etc/samba/smb.conf` |
| `smbpasswd`    | Setup up a password for Samba | `$ sudo smbpasswd -a [username]` |
| `mkdir`    | Create a shared directory | `$ mkdir /my/directory/to/share` |
| `service`    | Restart the Samba service | `$ sudo service smbd restart` |
| `smbclient`    | Accessing a Samba/Windows share via Linux | `$ smbclient //HOST/directory -U user` |
| `mount`    | Attach a Samba share to your system. Instead of transferring files one by one, you can just mount the network share on your system. | `$ sudo mount -t cifs servername:directory mountpount -o user=username,pass=password` |
| `network connection+run`    | Accessing a Samba share via Windows. In Windows, just type in the _network connection_ in the run prompt: |  `\\HOST\sharename` |










---
Pull requests are welcome for adding or removing commands, as well as for modifying or correcting errors.

---

### Reference

[Book Cheat-sheet: Linux Basics for Hackers by OccupyTheWeb](https://medium.com/@shanlogauthier/book-cheat-sheet-linux-basics-for-hackers-by-occupytheweb-9f112834740e) 
GitHub: shanickcuello/linux-commands-cheat-sheet
[Linux Journey](https://linuxjourney.com/) 


