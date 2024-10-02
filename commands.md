Linux Command :

File and Directory Management
- is                                        :List directory contents (use ls).
- pwd                                       :Print current working directory.
- cd:                                       :Change directory.
- mkdir                                     :create a new directory.
- touch                                     :Create an empty file or update a file's timestamp.
- cp                                        :Copy files or directories.
- mv                                        :Move or rename files or directories.
- du                                        :Display disk usage of files and directories.
- rm                                        :Remove a file.
- rm -r [directory_name]                    :Recursively remove a directory.
- rm -rf [directory_name]                   :Forcefully remove a directory and its contents.
- wc                                        :Word, line, character, and byte count of a file.
- wget                                      :Download files from the web.
- cp [file_name1] [file_name2]              :Copy file1 to file2.
- cp -r [directory_name1] [directory_name2] :Recursively copy a directory.
- mv [file_name1] [file_name2]              :Move or rename a file.
- ln -s /path/to/[file_name] [link_name]    :Create a symbolic link.
- more [file_name]                          :View file content one screen at a time.
- head [file_name]                          :Display the first few lines of a file.
- tail [file_name]                          :Display the last few lines of a file.
- gpg -c [file_name]                        :Encrypt a file.
- gpg [file_name.gpg]                       :Decrypt a GPG-encrypted file.
- sudo                                      :Execute a command with superuser privileges.
- locate                                    :Find a file by its name.
- find                                      :Search for files based on criteria.
- jobs                                      :List current jobs.
- history                                   :Show command history.
- uname                                     :Display system information (e.g., kernel version).
- man                                       :Display manual for a command.
- zip                                       :Compress files into a ZIP archive.
-unzip                                      :Extract files from a ZIP archive.
- echo                                      :Output text or variables to the screen.
- hostname                                  :Show or set the system's hostname.
- chmod                                     :Change file permissions.
- chown                                     :Change file ownership.
- grep                                      :Search for patterns within files.
- tar                                       :Archive multiple files into one.
- mount                                     :Mount a filesystem.
- diff                                      :Compare the contents of two files.
- whoami                                    :Display the current user.
- sort                                      :Sort lines of text files.
- export                                    :Set environment variables.
- ssh                                       :Securely connect to a remote machine.
- service                                   :Manage system services.
- awk                                       :Pattern scanning and text processing.
- sed                                       :Stream editor for filtering and transforming text.

File Viewing and Editing
- cat                                        :View the contents of a file.
- less                                       :View file contents with backward/forward navigation.
- more                                       :View file contents one screen at a time.
- nano                                       :Simple text editor.
- vim                                        :Advanced text editor with many features.
- gedit                                      :Graphical text editor for GNOME.

Process Management
- ps                                         :Display running processes.
- top                                        :Show real-time system processes and resource usage.
- kill                                       :Terminate a process by its PID.
- killall                                    :Kill processes by name.
- pstree                                     :Show running processes as a tree.
- htop                                       :Interactive process viewer (more detailed than top).

System Information
- uname                                      :Show system information.
- df                                         :Report file system disk space usage.
- du                                         :Display disk usage of files or directories.
- free                                       :Show available memory and swap usage.
- lscpu                                      :Display CPU architecture information.
- lsblk                                      :List information about block devices.

User and Group Management
- passwd                                     :Change user password.
- useradd                                    :Create a new user.
- usermod                                    :Modify a user account.
- groupadd                                   :Add a new group.
- groupdel                                   :Delete a group.
- groups                                     :Show groups a user belongs to.
- id                                         :Display user and group IDs.

Network Configuration and Monitoring
- ifconfig                                    :Display or configure network interfaces.
- ip                                          :Show/manipulate routing, devices, and network interfaces.
- ping                                        :Test the reachability of a network host.
- netstat                                     :Network statistics and connections.
- ss                                          :Show socket statistics.
- traceroute                                  :Show the path packets take to a network host.
- ssh                                         :Securely log in to a remote machine.
- nc                                          :Netcat utility for reading/writing data across network connections.
- ip addr show                                :Show IP addresses assigned to interfaces.
- netstat -pnltu                              :List listening ports.
- netstat -nutlp                              :Show TCP and UDP connections.
- whois [domain]                              :Get information about a domain.
- dig [domain]                                :DNS lookup for a domain.
- host [domain]                               :DNS lookup.
- nslookup                                    :Query Internet name servers.

Package Management
- apt-get                                      :Package management for Debian-based distributions.
- apt                                          :High-level interface for the APT package manager.
- yum                                          :Package manager for RHEL/CentOS-based systems.
- dnf                                          :Newer package manager for Fedora/RHEL/CentOS.
- rpm                                          :Install, update, or remove packages in RPM-based systems.
- dpkg                                         :Package management for Debian-based systems.
- snap                                         :Manage snap packages.
- zypper                                       :Package manager for openSUSE and SUSE.

File Permission
- 4-read (r)                                   :Read permission for a file or directory.
- 2-write (w)                                  :Write permission for a file or directory.
- 1-execute (x)                                :Execute permission for a file or directory.

Backup Automation
- cron                                          :Automate scheduled tasks.
- system-config                                 :Configures system services (often distribution-specific).
- firewalld                                     :Manage firewall rules in Linux.
-stickybit                                      :Special permission flag for restricting directory deletion.
