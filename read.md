## Linux:

- 96% of world servers are linux
- We use a server for hosting the application
- Unix and Mac OS are locked i.e. with the underlying hardware
- Linux is a kernel
- Supports multiple users at the same timeHow we can connect to Linux Server

## How we can connect to Linux Server:

- Authentication and Authorisation
- What you know? Password
- What you have? RSA Key, Tokens etc
- What you are? fingerprints, palm, retina etc
- In Linux servers, we have public and private key mechanisms
- Linux Box/server/node
- Public Key is present inside the server
- We can generate Public and Private key pairs using: ssh-keygen -f <filename>
- We can connect to the linux server using SSH protocol, port-no, IP address, Username, Password/key

## Popular services and their port numbers:

- HTTP: 80
- MySQL: 3306
- DNS: 53
- SMTP: 25
- Tomcat: 8080

## Steps to Launch and connect to a server:

- Step 1: Create a Firewall (Security Group)
- Name: it as allow-all
- Inbound and outbound rules: All TCP and traffic from anywhere in the world
- Step 2: Create a key-pair using ssh-keygen command and import the public key
- Step 3: Launch a server (EC2-Instance)
- OS: RHEL-9
- keypair: choose the one which we created in step 2
- Security Group: allow-all
- Step 4: Connect to the server using ssh -i <path-to-pem> <username>@<IP address of the server>

## Linux Commands

- `command <options> <input>`
- `pwd` -> present working directory
- `#` -> root user
- `$` -> Normal user (default)
- `uname` -> which kernel are we using?
  - `uname -a` -> Detailed information of the kernel
- `ls` -> list all the files and folders in that folder
  - `ls -l` -> long listing of each file and folder
  - `ls -lr` -> Sort files in alphabetical order
  - `ls -lrt` -> Sort files from oldest to newest
    - `d` -> directory
    - `-` -> file
  - `ls -la` -> long listing including hidden files and folders
- `cd <path-of-the-directory>` -> Change directory
- `touch <filename>` -> An empty file is created with the filename
- `mkdir <folder-name>` -> Create a folder
- `cat > <filename>` -> Allows to user to enter the text inside the file
  - Once we are done with it, we need to press `ctrl + d`
  - Removes the older content and stores the new content
  - `>>` -> Appends to the older content in the file
- `cat <filename>` -> To print the contents of the file onto the terminal
- `rm <filename>`  -> To remove the file
- `rmdir <folder name>`  -> To remove an empty folder
- `rm -r <folder name>`  -> To remove a folder and its contents in a recurrsive way
- `cp <source> <destination>` -> To copy a file from one location to another
  - `-r` -> to copy the files in a recurrsive way
- `mv <source> <destination>` -> To move a file from one location to another
- `grep <word-to-find> <filename>` -> To find a text inside a file
  - Case sensitive
  - To make it case insensitive: `-i` option
- `|` -> Pass the output of a command as an input to another command
  - E.g. `cat /etc/passwd | grep sbin`
- `head filename` -> First 10 lines of the file by default
  - `-n <no: of lines>` - print those no: of lines
- `tail filename` -> Last 10 lines of the file by default
- `wget <URL>` -> to download the file from internet
- `curl <URL>` -> Show the contents of the file onto terimnal
  - `-o` to write the output to a file
  - E.g. `curl -o /tmp/web.zip https://roboshop-builds.s3.amazonaws.com/web.zip`
- `unzip -o <filename>` - to decompress the compressed file
  - `-o` to overwrite the content
- `cut -d <delimiter> -f <index of the fragement>` -> Cut the string based on a delimiter
  - `-d` -> delimiter
  - `-f` -> fragment
  - The disadvantage with this command is that, we need to calcuate the fragment number manually
- `awk -F <delimiter> {print $<index of the fragement>F}`
  - To get the last fragment, we can use **NF** i.e `awk -F <delimiter> {print $NF}`
  - We can also use `awk` for column based filtering
- By default root userID is 0

## Editors

- vim editor: Visually improved editor
- `vim <filename>` - Creates a file and opens it if its not present. If its present, it opens the file directly
  - There are 3 modes in vim:
    1. Escape mode
        - `u` - To undo the changes made
        - `yy` - Yank/copy the line where the cursor is present + `p` for paste
          - `yy` + `10p` - copies the line and past it 10 times
        - `dd` - To delete one line
        - `gg` - To shift the cursor to the top of the file
        - `shift + g` - To shift the cursor to the bottom of the file
    2. Colon mode: command mode
        - `/<word-to-search>` - It will search for the word from the top of the file
          - `n` for searching the next occurence
        - `?<word-to-search>` - It will search for the word from the bottom of the file
        - `:q` - To quit the file
        - `:q!` - To force quit the file
        - `:noh` - No highlight i.e. it will unhighlight the previous search
        - `:se nu` - To display the line numbers in the file
        - `:se nonu` - To disable displaying the line numbers in the file
        - `:wq` - To save the changes and quit
        - `:s/<word-to-search>/<replace word>` - To search a word and replace it where the cursor is placed
          - `:2s/<word-to-search>/<replace word>` - To search a word and replace it in the 2nd line
          - `:%s/<word-to-search>/<replace word>/g` - To search a word and replace all the occurrences
    3. Insert mode


## Permissions in Linux

- User / owner -> The one who created the file
- group: The group to which user belongs to
- others: Other than user and group
- When a user is created in linux, a group with the same name as user is created by default
- `chmod <permissions> <filename>` -> change permissions to a file
  - For e.g. `chmod u+x <filename>` -> The user is given with executable permissions to execute the file
  - `chmod go+r passwd`
  - `chmod +x passwd`
  - `chmod -x passwd`
  - `chmod ugo+rwx passwd`
- Who can change the permissions of the file? owner or root user
- R - 4, W - 2, X - 1
  - E.g. `chmod 750 passwd`
- Usually to public and private keys, the premissions is never greater than 400

# User Management

- Before we perform any operations related to user maangement, we should be a root user which can be switched using `sudo su -`
- To check if we are a root user or not, we can identify it on the terminal with `#` symbol or with `id` command
- For root user, the uid is 0
- Creating User: `useradd <username>`
  - Linux starts creating new users with uid >= 1000
  - Below this Linux reserves them for system users
- Setting password to user
- Reading the user information: `id <username>`
- Updating the user information
- All the information related to the users is present inside `/etc/passwd` file
  - Username, uid, gid, home location, which shell he has access to
  - We can also access the same information using: `getent passwd`
- setting a password for a user: `passwd <username>`
- By default Linux disables the password based authentication
- To enable it, we need to modify the content of `/etc/sshd/sshd_config` file (in the line where it says PasswordAuthentication No)
  - sshd_config is a crucial file, any errors in the file, removes the whole access to the server
  - Therefore, we store a backup of this file
- **Before restarting the service, we should test if the configuration that is present inside the sshd_config file is correct or not**
- To test the configuration, we can use `sshd -t`
  - If there're any errors, it will print on to the terminal
- If there are no errors, we should restart the service using `systemctl restart sshd`
- Every user has 2 types of groups:
  1. Primary Group (gid)
  2. Secondary Group (groups)
- To create a group: `groupadd <groupname>`
- To add a user to a group: `usermod -g <groupname> <username>`
  - `-g`: primary group
  - `-G`: secondary group
- To list all groups in the system: `getent group`
- To add one more secondary group to a user: `usermod -aG <groupname> <username>`
  - `-a` -> appending
- To delete a user from a group: `gpasswd -d <username> <groupname>`
- An user should always be a part of one group
- To delete a user completely:
  1. Assign the group of the user to the same as his username: `usermod -g <groupname> <username>`
  2. Delete the user using: `userdel <username>`
- To delete a group:
  1. There shouldn't be any users part of that group, therefore we should remove all the users that are part of that group
  2. `groupdel <groupname>`

## Enable SSH access to a user

- User should create a public and private key pair at first
- Share the public key with the administrator
- Admin creates a `.ssh` folder inside his home directory
- Inside the .ssh directory, we should create file called `authorised_keys`
- Change the permissions to the file as: `chmod 400 authorised_keys`
- Change ownership to the folder: `chown <username>:<groupname> -R <foldername>`

## Process management

- Everything in Linux is a process
- We can see the list of all process that are running the system using: `ps -ef`
  - To see the list of process that are active in the current terminal: `ps`
- Each process has an ID associated with it and it is called as Process Instance ID
- Root user gets the PID of 0
- In addition to that it also has a Parent Process ID (PPID) linked to it
- There are 2 kinds of process:
  1. Foreground process
  2. Background process: `&`
- To kill a process: `kill <process-id>`
  - To kill a process forcefully: `kill -9 <process-id>`

## Package management

- To install package:
  - on centos: `yum install <package-name> -y`
  - on ubuntu: `apt install <package-name> -y`
  - on Amazon Linux:
    - `sudo amazon-linux-extras install epel -y`
    - `sudo yum install <package-name> -y`
- To remove a package: `yum remove git -y`
- To get the list of all packages (including installed): `yum list all | wc -l`
  - `wc -l` -> counts number of lines in the previous command
- To get the list of all installed packages: `yum list installed | wc -l`

## Service Management

- There are 65535 ports on a server
- When ever a service is started, it will get assigned with a port number in this range
- To start a service: `systemctl start <servicename>`
- To check the status of a service: `systemctl status <servicename>`
- To enable the service at time of boot: `systemctl enable <servicename>`
- To check whether a service is working or not: `netstat -lntp`
  - Along with this, we also get the PID, port number information
- To check the memory usage on the server: `free -m`
- Check the harddisk utilisation: `df -hT`
- To check if two servers are communicating with each other or not: `telnet <IP address> <PORT>`

- `find <where-to-find> -name "hello"`: Find a file with name "hello" inside all the directories present inside linux filesystem

## Linux filesystem

- / - Linux start Directory
- /boot - At the time of boot-up, linux searches for this directory and a file called **grub.cfg** inside grub2 directory
- /root - It is home folder of super admin user
- /dev (devices) - Information realted to harddisks, external devices, keyboards etc
  - `tty` - Keyboard
- /etc (Extra Configuration) - Configuration of all the packages and services
- /home - All the other users directories are present here
- /lib or /lib64 - All the dependencies of the packages and commands
  - It is similar to dlls in windows
- /media - cd, dvd, will be mounted here
- /mnt - It is used to mount the external harddisk or Network File Storage (NFS)
- /opt - optional, third party softwares like tomcat
  - Usually it is recommended to store all those packages we want to download and run manually
- /proc - All the information related to the running process is stored here
  - Once the system is stopped, everything present in this directory are deleted
  - E.g. `cat /proc/meminfo`, `cat /proc/cpuinfo`
- /run - At the time of OS loading, it will need some temporary filesystem. It will use this directory for that purpose
  - Once the server is stopped, all th contents present in this directory are also deleted
- /bin - All the binaries for executing the commands such as pwd, ls, vim, top etc are stored here
- /sbin - System binaries i.e. Admin related commands
- /temp - For storing temporary data. The data present in this directory will be deleted once the server is restarted
- /var (Variables) - All the log files, system related messages etc.
  - To scroll through the messages, we can use `less` command
    - `shift + g` to scroll to the end
    - `gg` to scroll back to up

## inode, symlink/softlink, hard link, Tar command

- inode: For everything in the linux filesystem, there is a number associated to it i.e. a pointer to where it is stored in the harddisk.
  - We can fetch this information using: `ls -ltri`
- Softlink / Symbolic link: It is the shortcut that points to the original file which points to the inode value
  - To create a symlink, we use: `ln -s <source-file> <link-name>`
  - The inode value of the symlink file is **different** than the original one
  - If the source file is deleted, the softlink throws No such file or directory exception
- Hard link: Creates a copy of the file but points to the same inode value
  - To create a hard link, we use: `ln <source-file> <link-name>`
  - To find the source file of the hardlink, we can use the inode number
    - `find <where-to-search> -inum <inode-number>`
  - If the source file is deleted, the hard link still holds the data
- To extract the .tar.gz file, we use: `tar -xf <.tar.gz file path>`
  - `-x` - Extraction
  - `-f` - filename

## Crontab

- Scenario: We need to monitor a linux server all the time i.e. its memory, cpu resource utilisation
- For this, we create a shell script and schedule it to run every hour
- To open crontab editor: `crontab -e`
- Syntax: `* * * * * <command to execute>`
  - Ref: [https://crontab.guru/](https://crontab.guru/)
  - In this syntax, we want to execute a command **At every minute**