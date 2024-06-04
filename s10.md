# Session 10


## ps
- It lists the running processes.
```
    ps
```

- -f ---> It displays more information
- -u ---> It displays username
- -a ---> All process
- -e ---> running processes
- -ax --> It even displays processes that are running outside the terminal.

#

## Foreground Processes:
- When you run a command in a Linux terminal, it is executed in the foreground by default.
- Foreground processes wait for user input and display the output before returning to the prompt.
- Foreground processes block the user from executing other commands until they complete.

## Background Processes:
- Background processes do not block the terminal, allowing the user to execute other commands.
- To run a process in the background, add an '&' at the end of the command.

## Daemons:
- Daemons are background processes that usually run with root privileges.
- Daemons provide services to other processes and wait for specific events to occur.
- Daemons start during system boot and continue running until the system is shut down.

## Parent and Child Processes:
- Each process has a parent process ID (PPID) and a process ID (PID).
- The parent of all processes is usually the systemd process, which replaced the init process in most Linux distributions.

## Process States:
- Running: The process is currently executing or ready to receive CPU time.
- Waiting: The process is waiting for an event, such as user input.
- Stopped: The process execution has been halted, usually for debugging purposes.
- Zombie State: In this state, the process has finished executing, but it still remains in the process table.
#



## jobs
- Using the "jobs" command, we can see the running and suspended programs.
```
    jobs
```
#

## pstree
- The `pstree` command displays the list of running processes in a tree-like format.
```
    pstree
```
#


## jobs

- Using the `jobs` command, we can see the running and suspended programs.

```
    jobs
```

#


## top

The `top` command provides a report on the status of processes and the allocation of memory and processor resources. This command is a useful tool for monitoring the status of processes on network servers. With the help of this tool, we can observe the overall consumption of system resources, such as memory and processor.


- `n` - Specifies the number of times the display should be updated.
- `p` - Specifies a particular process to report on.
- `u` - Specifies a particular user's processes to report on.

## Examples:

- The `top` command will only be executed once.
```
top -n 1
```
- It will monitor the process with ID 1.

```
top -p 1
```
- It will monitor the processes of the user with the name "user1".

```
top -u user1
```

#

## kill

The `kill` command is used to send a termination signal to a process or a group of processes.

```
kill {kill-signal} {PID}
kill {kill-signal ID {PID}
```

To display the list of `kill` signals, use the following command:

```
kill -l
```

## Important Kill Signals in Linux

Here are some of the important kill signals in Linux:

- `SIGHUP (1)` - Hang up the process
- `SIGINT (2)` - Interrupt the process
- `SIGQUIT (3)` - Quit the process
- `SIGILL (4)` - Illegal instruction
- `SIGTRAP (5)` - Trace/breakpoint trap
- `SIGABRT (6)` - Abort the process
- `SIGFPE (8)` - Floating-point exception
- `SIGKILL (9)` - Terminate the process immediately
- `SIGUSR1 (10)` - User-defined signal 1
- `SIGSEGV (11)` - Invalid memory reference
- `SIGUSR2 (12)` - User-defined signal 2
- `SIGPIPE (13)` - Broken pipe
- `SIGALRM (14)` - Alarm clock
- `SIGTERM (15)` - Termination signal
- `SIGCHLD (17)` - Child process has stopped or terminated
- `SIGCONT (18)` - Continue the process if it has been stopped
- `SIGSTOP (19)` - Stop the process

These signals can be used with the `kill` command to control the behavior of running processes in Linux.
#


## nice

In Linux, many programs can run simultaneously. If we want to give higher priority to some processes in using system resources, we can use the `nice` command to run that process with a specific priority.

The `nice` command can set a priority value between -19 to 20 for a process when it starts. The highest priority is -19 and the lowest is 20. The default priority (nice value) for all processes is 0.

If a process is already running, we can use the `renice` command to change its priority value:

```
nice -n 'Nice Value' process_name
renice -n 'Nice Value' -p PID
```

For example:

- To start a process with a nice value of 10:
```
nice -n 10 process_name
```
- To change the nice value of a running process with PID 1234 to -5:
```
renice -n -5 -p 1234
```

The lower the nice value, the higher the priority of the process. Processes with higher nice values will have lower priority and receive fewer CPU resources.

#

## uptime

The `uptime` command displays information about how long the system has been running (uptime), the current time, the number of users logged in, and the system load averages for the past 1, 5, and 15 minutes.

The output of the `uptime` command typically looks like this:

```
 15:27:19 up 25 days, 18:36,  1 user,  load average: 0.00, 0.01, 0.05
```

This output shows:

- The current time is 15:27:19.
- The system has been running for 25 days and 18 hours and 36 minutes.
- There is 1 user currently logged in.
- The system load averages are 0.00, 0.01, and 0.05 for the past 1, 5, and 15 minutes, respectively.

The system load average is a measure of the system's performance, with a lower number indicating less load on the system.

#

## du

The `du` command displays the disk usage of a file or directory.

The basic syntax is:

```
du [options] [file_or_directory]
```

Here are some common options for the `du` command:

- `-h`: Displays the sizes in human-readable format (e.g., KB, MB, GB).
- `-s`: Displays the total size of the specified file or directory.
- `-a`: Displays the size of each file in the specified directory.
- `-c`: Displays the grand total.
- `-d <depth>`: Limits the depth of the directory tree to the specified number.

Examples:

```
# Display the disk usage of the current directory
du .

# Display the total disk usage of the /var directory
du -s /var

# Display the disk usage of each file in the /home directory
du -a /home

# Display the disk usage of the /opt directory and its subdirectories up to 2 levels deep
du -d 2 /opt
```

The `du` command is useful for identifying large files or directories that are consuming a significant amount of disk space on your system.

#

## df

The `df` (disk free) command is used to report the amount of available disk space for the file system that contains each file name argument.

The basic syntax for the `df` command is:

```
df [options] [file or directory]
```

Here are some common options for the `df` command:

- `-h`: Displays the sizes in human-readable format (e.g., KB, MB, GB).
- `-i`: Displays information about inodes instead of disk space.
- `-T`: Displays the file system type.
- `-a`: Displays information about all mounted file systems.

Examples:

```
# Display the disk usage for all mounted file systems
df

# Display the disk usage for the root file system in human-readable format
df -h /

# Display the inode information for all mounted file systems
df -i

# Display the disk usage for the /home directory
df /home
```

The output of the `df` command typically includes the following information:

- Filesystem: The name of the file system.
- Size: The total size of the file system.
- Used: The amount of space used.
- Avail: The amount of space available.
- Use%: The percentage of the file system that is used.
- Mounted on: The mount point of the file system.

The `df` command is useful for monitoring the available disk space on your system and identifying file systems that are running out of space.


#

## free

The `free` command is used to display the total amount of free and used physical and swap memory in the system, as well as the buffers and caches used by the kernel.

The basic syntax for the `free` command is:

```
free [options]
```

Here are some common options for the `free` command:

- `-h`: Displays the memory sizes in human-readable format (e.g., KB, MB, GB).
- `-m`: Displays the memory sizes in megabytes.
- `-g`: Displays the memory sizes in gigabytes.
- `-t`: Displays the total for all the fields.
- `-s <delay>`: Displays the memory usage continuously with the specified delay in seconds.

Example output:

```
              total        used        free      shared  buff/cache   available
Mem:           7.8G        2.5G        1.4G        589M        3.9G        4.4G
Swap:          2.0G          0B        2.0G
```

This output shows:

- Total memory (Mem): 7.8 GB
- Used memory: 2.5 GB
- Free memory: 1.4 GB
- Shared memory: 589 MB
- Buffers and cache: 3.9 GB
- Available memory: 4.4 GB
- Total swap space: 2.0 GB
- Used swap space: 0 GB
- Free swap space: 2.0 GB

The `free` command is useful for monitoring the memory usage of your system and identifying any potential memory-related issues.
