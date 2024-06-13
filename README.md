# Os-toturial
a Os(linux) toturial for beginneras

#

## Session 2: File Management in Linux

This session covers several essential Linux command line utilities and their usage, including:

1. `ls`: Used to list files and directories, with various options to customize the output.
2. `cp`: Allows you to copy files and directories, with options to preserve attributes and handle overwriting.
3. `mv`: Enables moving or renaming files and directories.
4. `rm`: Deletes files or directories, with options to handle recursive removal and avoid prompts.
5. `mkdir`: Creates new directories, with options to create parent directories and set permissions.
6. `rmdir`: Removes empty directories.
7. `cd`: Changes the current working directory, with shortcuts to navigate the file system.
8. Wildcards (Globbing): Special characters that can be used to match multiple files or directories in a single command.
9. `touch`: Changes the timestamp (access, modification, or change time) of a file, or creates a new file if it doesn't exist.
10. `find`: A powerful command for hierarchical file search, with various options to narrow down the search criteria.

These commands are fundamental building blocks in the Linux command line environment, allowing users to perform a wide range of file management and system navigation tasks efficiently. The explanations provided give a concise overview of the syntax, common use cases, and practical examples for each command.


 [![s2](https://img.shields.io/badge/s2%20read-FCFC0F)](https://github.com/tahamusvi/Os-toturial/blob/main/file_management.md)

#

## Session 3: Mastering Basic Linux Commands


The session covers several basic Linux command line utilities and their usage. The commands discussed include:

1. `cat`: Used to create or display the contents of a file.
2. `head`: Displays the beginning contents of a file.
3. `tail`: Displays the ending contents of a file.
4. `wc`: Provides word, line, and character counts for a file.
5. `cut`: Extracts specific parts of each line from a file or text.
6. `less` and `more`: Used to display the contents of a file in a paginated manner.
7. `grep`: Searches for a specific pattern or string within a file or command output.
8. `echo`: Prints a message or string to the terminal.
9. Creating a new file using the `cat >` command.

These commands are fundamental tools in the Linux command line environment, allowing users to perform various file manipulation, inspection, and processing tasks efficiently. The explanations provided give a concise overview of the syntax and common use cases for each command.

[![s1](https://img.shields.io/badge/s3%20read-FCFC0F)](https://github.com/tahamusvi/Os-toturial/blob/main/basic_commands.md)

#

## Session 4: More Essential Linux Commands

The session covers several additional Linux command line utilities and their usage:

1. `man`: Displays the manual pages (man pages) for a given command or utility, providing detailed information about its syntax, options, and usage.
2. `whatis`: Displays a one-line description of a command or utility.
3. `which`: Locates the executable file associated with a given command.
4. `who`: Displays information about the users currently logged into the system.
5. `whoami`: Displays the username of the current user.
6. `date`: Displays or sets the current date and time on the system.
7. `pwd`: Prints the current working directory.
8. `read`: Accepts input from the user in a terminal or shell script.
9. `shutdown`: Shuts down or reboots the system.
10. `uname`: Displays information about the current operating system and hardware.
11. `sleep`: Pauses the execution of a script or command for a specified amount of time.
12. `history`: Displays the history of previously executed commands.
13. `alias`: Creates shortcuts for longer or more complex commands.
14. `hostname`: Displays or sets the system's hostname.

These commands provide a range of functionality for system administration, scripting, and general command-line management tasks in a Linux environment. The explanations give a concise overview of the syntax, common use cases, and key points for each command.

[![s1](https://img.shields.io/badge/s4%20read-FCFC0F)](https://github.com/tahamusvi/Os-toturial/blob/main/essential_commands.md)

#



## Session 5: User and Group Management in Linux

## User Management Commands
- `passwd`: Changes the password of a user account.
- `vipw`: Edits the `/etc/passwd` file, which contains user account information.
- `useradd`: Creates a new user account with various configurable options.
- `userdel`: Deletes a user account.
- `usermod`: Modifies an existing user account, such as changing the username, home directory, or shell.

## Group Management Commands
- `vigr`: Edits the `/etc/group` file, which contains group information.
- `groupdel`: Deletes a user group.
- `groupmod`: Modifies an existing user group, such as changing the group name or GID.
- `gpasswd`: Administers the `/etc/group` file, allowing you to assign group administrators, add/remove users from groups, and more.

These commands provide the tools necessary for managing user accounts and group memberships on a Linux system. Understanding how to effectively use these tools is crucial for system administration tasks, such as creating new users, modifying existing accounts, and controlling access to system resources through group memberships.

The explanations you provided cover the key functionality and usage examples for each command, making this a valuable reference for anyone working with user and group management in a Linux environment.

[![s1](https://img.shields.io/badge/s5%20read-FCFC0F)](https://github.com/tahamusvi/Os-toturial/blob/main/user_and_group.md)


#

## Session 6-1: Backup and Archiving in Linux

In this section, we'll use the `tar` and `cpio` commands to create backups and archives of files and directories. The `tar` command is the primary tool for creating archives, while `cpio` provides an alternative approach.


[![s1](https://img.shields.io/badge/s6%20read-FCFC0F)](https://github.com/tahamusvi/Os-toturial/blob/main/backup.md)

#


## Session 6-2: Scheduling Tasks in Linux

In this section, you'll learn to use the `at` and `cron` commands to schedule one-time and recurring tasks on your Linux system. Additionally, we'll cover `anacron`, which ensures scheduled tasks are executed even if the system was powered off at the scheduled time.


[![s1](https://img.shields.io/badge/s6%20read-FCFC0F)](https://github.com/tahamusvi/Os-toturial/blob/main/scheduling_tasks.md)

#


## Session 6-3: Package Management in Linux

This section focuses on `apt`, the primary package management tool for Debian-based Linux distributions like Ubuntu. We'll explore using `apt` to update package lists, upgrade installed packages, install and remove packages, search for packages, and display package information.

[![s1](https://img.shields.io/badge/s6%20read-FCFC0F)](https://github.com/tahamusvi/Os-toturial/blob/main/apt.md)


#



## Session 7: Unleashing the Power of Linux Shell Scripts
`Bash` is a command language interpreter. shell is a macro processor that executes commands. The term macro processor means
It is a function in which text and symbols are expanded to create a larger expression.

[![s1](https://img.shields.io/badge/s7%20read-FCFC0F)](https://github.com/tahamusvi/Os-toturial/blob/main/shell_scripts.md)



#



## Session 8: Exploring the Versatility of AWK

## awk
- Powerful text processing and reporting tool
- Operates on input data divided into records and fields
- Records are separated by the record separator (RS), default is newline
- Fields within records are separated by the field separator (FS), default is whitespace
- Syntax: `awk 'pattern {action}' input-file > output-file`
- Supports various expressions, statements, and internal variables

## awk Internal Variables
- `NF`: Number of fields in the current record
- `NR`: Number of the current record
- `FILENAME`: Name of the current input file
- `FS`: Field separator
- `RS`: Record separator
- `OFS`: Output field separator
- `ORS`: Output record separator

## Changing Field and Record Separators
- Set `FS` to change the field separator
  - `awk 'BEGIN { FS = "." } { print $1 }' test.txt`
- Use `-F` option to change field separator on the command line
  - `awk -F "." '{ print $1 }' test.txt`
- Set `RS` to change the record separator
  - `awk 'BEGIN { RS = "." } { print $1 }' test.txt`

The awk command provides a powerful and flexible way to process and analyze text data, with the ability to customize the field and record separators to suit the input format. The detailed explanation you provided covers the key concepts and usage examples, making this a great reference for working with awk in a Linux environment.

[![s1](https://img.shields.io/badge/s8%20read-FCFC0F)](https://github.com/tahamusvi/Os-toturial/blob/main/awk.md)



#



## Session 9: Networking Commands and Utilities in Linux

The session covers several Linux network management commands:

1. `ifconfig`: Configures and displays information about network interfaces.
2. `route`: Manages the system's IP routing table.
3. `ip`: A more advanced tool for configuring network interfaces and routing.
4. `netstat`: Provides information about network connections, routing, and interfaces.
5. `telnet`: Establishes a remote connection to a server, though it is not a secure protocol.
6. `nmap`: A powerful network scanning tool that can probe ports and services on systems.
7. `ping`: Tests the connectivity between two network nodes by sending ICMP echo requests.
8. `traceroute`: Determines the number of hops and the path taken by packets to reach a destination.
9. `arp`: Manages the Address Resolution Protocol (ARP) cache, which maps IP addresses to MAC addresses.
10. `nslookup` and `dig`: Perform DNS lookups to convert between domain names and IP addresses.
11. `wget`: Downloads files from the internet using HTTP, HTTPS, or FTP protocols.

These commands provide a wide range of functionality for network administrators and users, allowing them to configure, troubleshoot, and monitor network connectivity, services, and devices on a Linux system.

[![s1](https://img.shields.io/badge/s9%20read-FCFC0F)](https://github.com/tahamusvi/Os-toturial/blob/main/network.md)



#



## Session 10: Process Management and System Monitoring in Linux

1. `ps`: Lists running processes, with options to display more information, filter by user, and show processes running outside the terminal.
2. `Foreground Processes`: Processes that run in the foreground, blocking the terminal until they complete.
3. `Background Processes`: Processes that run in the background, allowing the user to execute other commands.
4. `Daemons`: Background processes that provide services and run with root privileges.
5. `Parent and Child Processes`: Each process has a parent process ID (PPID) and a process ID (PID).
6. `Process States`: Running, Waiting, Stopped, and Zombie.
7. `jobs`: Displays the running and suspended programs.
8. `pstree`: Displays the list of running processes in a tree-like format.
9. `top`: Provides a report on the status of processes and the allocation of memory and processor resources.
10. `kill`: Sends a termination signal to a process or a group of processes.
11. `nice`: Sets the priority of a process, allowing you to control the allocation of system resources.
12. `uptime`: Displays information about the system's uptime, number of users, and load averages.
13. `du`: Displays the disk usage of a file or directory.
14. `df`: Reports the amount of available disk space for the file system.
15. `free`: Displays the total amount of free and used physical and swap memory in the system.

These commands are essential for monitoring, managing, and troubleshooting processes and system resources in a Linux environment.

[![s1](https://img.shields.io/badge/s10%20read-FCFC0F)](https://github.com/tahamusvi/Os-toturial/blob/main/process_and_monitoring.md)



