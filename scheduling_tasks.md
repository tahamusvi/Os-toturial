# Session 6-2: Scheduling Tasks in Linux

The best way to protect important and vital data is to backup and maintain a backup copy in another location, which could be another partition of the disk, CD/DVD, or any other system on the network. It is better to backup the important and critical data at regular intervals or at least before and after any changes to the system. We usually backup the directories such as /etc/, /var, /home, /root, /opt/, and /boot/.

#
- Backup operations can be performed automatically using the cron service.


- The tar (archive tape) command: This command can be used to package and archive (archive) all the information. In other words, it can archive or create an archive file containing multiple files and directories.

#
The syntax for the tar command is:
```
tar [options] [source_file/directory] [destination_file]
```
Where:
- The destination is the location where the backup file will be stored.
- The source is the files/directories we want to backup.

Some common options for the tar command:
- c - Create a new archive
- r - Add files to an existing archive
- p - Preserve file permissions
- P - Backup the entire contents of a directory
- f - Specify the archive file name
- g - Used for differential backups
- u - Update the archive after changes to the original files
- d - Compare the archive and the original files
- x - Extract files from the archive
- z - Compress/uncompress the archive using gzip
- j - Compress/uncompress the archive using bzip2
- C - Do not use the current directory for extraction

#
The cpio (copy in/out) command:
- o - For creating a backup
- i - For restoring a backup

#

## at 

The `at` command is used to execute a program automatically only once. To run this command, first type the following command:
```
sudo apt install at
```
This means we want to perform a task once at a specific time in the future. After running the `at` command, we enter the `at` environment and can enter the commands we want to be executed at the scheduled time line by line.

## Desired date and time for at

Some of the parameters that are used in the `at` command are as follows:
- `now`: means to execute the desired command at the current time.
- `m`: After the task is completed, an email is sent to the corresponding user.
- `c`: To view the job content
  ```
  at –c jobid
  ```
- `d`: To delete a job
  ```
  at –d job
  ```
- `letter q`: Prioritizes the job, and `letter` means the letters `z-a`, and the closer the letter is to `z`, the lower the priority of the job execution.
  ```
  at now +2 min –q v
  ```
- `min +3 now`: means to execute the desired task 3 minutes later.
- `hours +3 now`: means to execute the desired task 3 hours later.
- `days +3 now`: means to execute the desired task 3 days later.
- `weeks +3 now`: means to execute the desired task 3 weeks later.
- `months +3 now`: means to execute the desired task 3 months later.
- `tomorrow`: means to execute the desired task the next day.
- `teatime`: means to execute the desired task at 4 o'clock in the afternoon.
- `midnight`: means to execute the desired task at midnight.

## Examples:

```
at now
at> ls –l >>f1
at > echo "finished" >> f1
Ctrl+D
```
In this example, by entering the `now at` command to the system, we tell it to perform a task for us right now, and then with the `<at` prompt, we start entering the commands, and finally with `Ctrl+D` we terminate the task. Now all the commands we entered will be executed.

```
at now +3 min –f ff1
```
In this case, the commands in the `ff1` file will be automatically executed 3 minutes later.

To view the list of programs that have been scheduled using the `at` command, we use the `at -l` or `atq` commands.

To delete a job, we use the following commands:
```
at –d jobid
atrm jobid
```

There are two configuration files related to the `at` command, which are:
- `/etc/at.allow`: Only users listed in this file can run the `at` command.
- `/etc/at.deny`: Only users listed in this file cannot run the `at` command.

The way these files work is as follows:
If both files exist, only users listed in the `at.allow` file have the right to run `at`, and the `at.deny` file is ignored.
And if none of these files exist, except for `root`, no other user has the right to run the `at` command.

#