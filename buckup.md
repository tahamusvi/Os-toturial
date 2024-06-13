# Session 6-1: Backup and Archiving in Linux

The key points are:

- The best way to protect important and vital data is to backup and maintain a backup copy in another location.
- This location can be another partition of the disk, CD/DVD, or any other system on the network.
- Backups should be performed regularly, at least before and after any changes to the system.
- Typically, backups are made of important directories such as /etc, /var, /home, /root, /opt, and /boot.

This simple but very effective method is for maintaining the security and availability of critical information in the system. Regular data backups are an essential preventive measure.

The policies that are proposed for backups are as follows:

1. Full backup: Backup of all the information. From the point of view of storage space and time consumption, this is not the most efficient.

2. Differential backup: Initially, a full backup is taken, and in subsequent instances, only the information that has changed since the initial backup is backed up. In other words, only the information that has changed since the initial backup is backed up. This method takes less time for the backup, but the recovery time is longer, and during recovery, we need to have the initial backup as well as one of the subsequent backup versions.

3. Incremental backup: In this method, initially, a full backup is taken, and in subsequent instances, only the information that has changed compared to the previous backup version is backed up. In this method, the backup is fast, but the recovery is time-consuming. During recovery, we need to have the initial backup as well as all the backups that were created over time, not just one of the backup versions.

In summary, the key differences are:
- Full backup: Backs up everything, but time and storage consuming.
- Differential backup: Only backs up changes since initial full backup, faster backup but slower recovery.
- Incremental backup: Only backs up changes since last backup, fastest backup but slowest recovery.

#

## cron
This program executes the tasks defined in the `/etc/crontab` file at the scheduled time. The `/etc/crontab` file has a specific format, with the rows of this file consisting of seven fields. The first five fields from the left determine the execution time of the desired command or task, the sixth field specifies the username under whose name the command or task will be executed, and the last (seventh) field specifies the command or program to be executed.

- The first field from the left represents the minutes (m) and ranges from 0-59. If `*/5` is written in this field, it means every 5 minutes.
- The second field from the left represents the hour (h) and ranges from 0-23. If `*` is in this field, it means every hour.
- The third field from the left represents the day of the month (dom) and ranges from 1-31.
- The fourth field from the left represents the month of the year (mon) and ranges from 1-12.
- The fifth field from the left represents the day of the week (dow) and ranges from 0-7.
  - (0 and 7 mean Sunday, 1 means Monday, 2 means Tuesday, 3 means Wednesday, 4 means Thursday, 5 means Friday, and 6 means Saturday)

Each user can have their own `crontab` file, which is located in the `/var/spool/cron` directory. Each user can create their own `crontab` file using the `crontab` command.

The system also has its own `crontab` file in the `/etc/crontab` or `/etc/cron.d` directory.

Similar to the `at` command, here too, the `/etc/cron.allow` and `/etc/cron.deny` files specify the authorized and unauthorized users for running `cron` and using the `cron` service.

- `crontab -e`
  Creates the `crontab` file for the desired user in the `/var/spool/cron/crontabs/` directory.
- `crontab -l`
  Displays the contents of the `crontab` file.

Example:
```
30 14 5 * * tar --czf backup1.tar.zip
```
The line above in the `crontab` file means that a backup of the user's home directory should be performed at 14:30 on the 5th of every month.

The `root` user can modify the `crontab` file of any user.
This can be done using the `crontab` command with the appropriate parameters.

Example:
```
crontab -e -u user1
```
This command will modify the `crontab` file for the `user1` user.

With the `-r` parameter, you can delete the `crontab` file.
```
crontab -r -u user1
```

There are several directories:
- `/etc/cron.hourly`
- `/etc/cron.daily`
- `/etc/cron.weekly`
- `/etc/cron.monthly`

You can use these directories to perform specific operations on an hourly, daily, weekly, and monthly basis. All you need to do is save the commands that are to be executed at these times in a file and place that file in one of the aforementioned directories, depending on when it is supposed to be executed. This way, the operations described in that file will be performed as specified.

The files inside these directories are executed in alphabetical order, so if you want the first file to be executed, you should choose the name of the file so that it is executed first.

Inside the `/etc/crontab` file, there are a few lines dedicated to specifying the execution time of the tasks under these directories. The `parts-run` expression that appears before the names of the mentioned directories causes all the files within the corresponding directory to be executed.

By default, the result of running the `cron` command is sent by email to the user who executed it.


#

## anacron
The `anacron` command can be used to execute scheduled tasks that were not performed at their scheduled time due to the system being turned off.

The `anacron` command also executes the commands inside the `/etc/anacrontab` file. After the `anacron` program is installed and the corresponding service starts, the system checks every time it turns on, and if there are any tasks that should have been executed at a specific time but were not, `anacron` will detect and execute them.

The format of the `/etc/anacrontab` file is similar to the `/etc/crontab` file, with the following differences:

- The first three fields represent the period (in days) between executions, the delay (in minutes) before the first execution, and a unique job identifier, respectively.
- The fourth field represents the command or program to be executed.
- There is no field for specifying the minute, hour, day, month, or day of the week.

For example:
```
7 10 cron.daily run-parts --report /etc/cron.daily
```
This line means that the commands in the `/etc/cron.daily` directory should be executed every 7 days, with a 10-minute delay after the system starts up.

The advantage of using `anacron` over `cron` is that `anacron` ensures that scheduled tasks are executed, even if the system was turned off at the scheduled time. `anacron` will execute the missed tasks the next time the system is turned on.

However, `anacron` is not suitable for tasks that need to be executed at a specific time, as it only ensures that the tasks are executed, not at a specific time. For such tasks, `cron` is more appropriate.


#

## zip
The `zip` command has the capability to create archive versions as well.

Syntax:
```
zip [options] destination_file source_file(s)
```

Options:
- `-r`: Compresses the contents of the directory recursively.
- `-e`: For encryption.
- `-d`: Deletes the input file in the compressed file.
- `-T`: To test the integrity of the archive file.

Examples:

1. Creating a zip archive:
   ```
   zip backup.zip file1.txt file2.txt
   ```
   This will create a zip file named `backup.zip` that contains `file1.txt` and `file2.txt`.

2. Compressing a directory recursively:
   ```
   zip -r documents.zip /path/to/documents
   ```
   This will create a zip file named `documents.zip` that contains all the files and subdirectories in the `/path/to/documents` directory.

3. Encrypting a zip file:
   ```
   zip -e secure_backup.zip important_files/
   ```
   This will create an encrypted zip file named `secure_backup.zip` that contains the contents of the `important_files/` directory.

4. Deleting a file from a zip archive:
   ```
   zip -d backup.zip file_to_delete.txt
   ```
   This will remove the `file_to_delete.txt` file from the `backup.zip` archive.

5. Testing the integrity of a zip archive:
   ```
   zip -T backup.zip
   ```
   This will test the integrity of the `backup.zip` archive.

The `zip` command is a powerful tool for compressing and archiving files and directories. It provides various options to customize the compression process, such as encryption, recursive compression, and file deletion within the archive.

#

## gzip
This program can be used to compress one or more files. If you compress multiple files with this command, it will compress each file individually.

Syntax:
```
gzip [options] file(s)
```

To extract a compressed file, we use the `gunzip` command:
```
gunzip file.gz
```

You can also use the `-d` option with the `gzip` command to extract a compressed file:
```
gzip -d file.gz
```

If you first combined multiple files into an archive using the `tar` command and then compressed the archive using `gzip`, to extract the contents, you need to first extract the `gzip` compression using `gunzip` or `gzip -d`, and then extract the `tar` archive using the `tar` command with the `xvf` options.

The file extension for a file that has first been archived and then compressed is `.tar.gz`.

Some additional options for the `gzip` command:

- `-r`: Compress directories recursively.
- `-k`: Keep the original file(s) after compression.
- `-l`: List information about the compressed file(s).
- `-v`: Verbose mode, shows the compression ratio.

The `gzip` command is useful for compressing individual files, while the `zip` command is more suitable for creating archives that contain multiple files and directories.

#

## bzip2
The `bzip2` command is similar to the `gzip` command. To extract the contents of a `bzip2` compressed file, we can use the `bunzip2` command or the `-d` option with the `bzip2` command.

Syntax:
```
bzip2 [options] file(s)
bunzip2 file.bz2
bzip2 -d file.bz2
```

The file extension for a `bzip2` compressed file is `.bz2`.

The compression level can be specified using numbers from 0 to 9, with higher numbers indicating stronger compression. You can use this as an option in the compression commands:

```
gzip -8 file.txt
```

This will create a highly compressed `file.txt.gz` file.

• The split command:
With this command, you can divide a file into multiple smaller files.

Syntax:
```
split [options] input_file output_file_prefix
```

Options:
- `-b size`: Specifies the size of the output files in bytes.

To reassemble the split files and recreate the original file, you can use the `cat` command:

```
cat file1 file2 file3 > original_file
```

The `bzip2` command provides better compression compared to `gzip`, especially for larger files, but it is also more CPU-intensive. The choice between `gzip` and `bzip2` depends on the specific requirements of your use case, such as the file size, required compression ratio, and available system resources.


#
