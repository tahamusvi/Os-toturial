                           
# Session 2


## ls

The `ls` command is used to list files and directories. Various options are available to customize the behavior of this command.

`ls [options]`

Here are some of the commonly used options:

- `-l`: Display detailed information about the files and directories.
- `-1`: List one file or directory per line.
- `-t`: Sort the output by modification time, with the most recent changes first.
- `-r`: Reverse the order of the sort.
- `-s`: Display the file size for each file.
- `-R`: Recursively list subdirectories.


#

## cp

The `cp` command is used to copy files and directories.

`cp [options] source destination`

Here are some of the commonly used options for the `cp` command:

- `-r`: Copy directories recursively, including their contents.
- `-i`: Prompt before overwriting an existing file.
- `-p`: Preserve the original file attributes, such as modification time and permissions.
- `-a`: Archive mode, which is equivalent to `-dpR`.
- `-v`: Verbose mode, which displays the progress of the copy operation.
- `-f`: Force the copy operation, overwriting files without prompting.

Examples:

- Copy a file to a new location:
```
cp file1.txt /path/to/destination
```

- Copy a directory and its contents to a new location:
```
cp -r directory1 /path/to/new_directory
```

- Copy a file and preserve its attributes:
```
cp -p file1.txt /path/to/destination
```

- Copy multiple files to a directory:
```
cp file1.txt file2.txt file3.txt /path/to/destination
```

The `cp` command is a powerful tool for managing files and directories on a Unix-based system.


#



## mv

The `mv` command is used to move or rename files and directories.

`mv [options] source destination`

Here are some of the commonly used options for the `mv` command:

- `-i`: Prompt before overwriting an existing file.
- `-f`: Force the move operation, overwriting files without prompting.
- `-v`: Verbose mode, which displays the progress of the move operation.

Examples:

- Move a file to a new location:
```
mv file1.txt /path/to/destination
```

- Rename a file:
```
mv file1.txt new_file.txt
```

- Move a directory to a new location:
```
mv directory1 /path/to/new_directory
```

- Move multiple files to a directory:
```
mv file1.txt file2.txt file3.txt /path/to/destination
```

The `mv` command is a powerful tool for managing the location and names of files and directories on a Unix-based system. It can be used to both move and rename files and directories, making it a versatile command for file management tasks.



#

## rm

The `rm` command is used to delete files or directories.

`rm [options] file`

Here are some of the commonly used options for the `rm` command:

- `-r` or `-R`: Remove directories and their contents recursively.
- `-f`: Force removal without prompting.
- `-i`: Prompt before removing each file or directory.

Examples:

- Remove a file:
```
rm file1.txt
```

- Remove a directory and its contents recursively:
```
rm -r directory1
```

- Remove a file without prompting:
```
rm -f file2.txt
```

- Remove multiple files with a prompt before each removal:
```
rm -i file1.txt file2.txt file3.txt
```

The `rm` command is a powerful tool for deleting files and directories, but it should be used with caution. The `-f` option can be particularly dangerous, as it will delete files without any confirmation. It's generally recommended to use the `-i` option, which will prompt the user before each deletion, to avoid accidentally removing important files.


#


## mkdir

The `mkdir` command is used to create directories.

`mkdir [options] dir_name`

Here are some of the commonly used options for the `mkdir` command:

- `-p`: Create any necessary parent directories.
- `-m`: Set the permissions of the newly created directory.
- `-v`: Verbose mode, which displays the directories as they are created.

Examples:

- Create a new directory:
```
mkdir directory1
```

- Create a new directory and its parent directories:
```
mkdir -p /path/to/new/directory
```

- Create a new directory with specific permissions:
```
mkdir -m 755 directory2
```

- Create multiple directories at once:
```
mkdir directory1 directory2 directory3
```

The `mkdir` command is a simple but useful tool for creating directories on a Unix-based system. The `-p` option is particularly helpful when creating a directory structure that doesn't already exist, as it will automatically create any necessary parent directories.

#


## rmdir

The `rmdir` command is used to remove empty directories.

`rmdir [options] dir_name`

If the directory is not empty, you can use the `rm -r` command to remove it and its contents.

Here are some of the commonly used options for the `rmdir` command:

- `-p`: Remove the specified directory and any empty parent directories.
- `-v`: Verbose mode, which displays the directories as they are removed.

Examples:

- Remove an empty directory:
```
rmdir directory1
```

- Remove an empty directory and its parent directories:
```
rmdir -p /path/to/empty/directory
```

If the directory is not empty, you can use the `rm -r` command to remove it and its contents:

```
rm -r non_empty_directory
```

The `rmdir` command is useful for removing directories that are no longer needed, but it can only remove empty directories. If a directory has files or subdirectories, you'll need to use the `rm -r` command to remove it and its contents recursively.


#

## cd

The `cd` command is used to change the current working directory.

`cd dir_name`

Here are some additional uses of the `cd` command:

- To go back one directory, you can use `cd ..`.
- To go to the root directory, you can use `cd /`.
- To go to the home directory, you can use `cd ~`.

Examples:

- Change to a specific directory:
```
cd /path/to/directory
```

- Go back one directory:
```
cd ..
```

- Go to the root directory:
```
cd /
```

- Go to the home directory:
```
cd ~
```

The `cd` command is one of the most fundamental commands in a Unix-like operating system. It allows you to navigate through the file system and change the current working directory. Understanding how to use the `cd` command is essential for efficiently working with the command line interface.


#


## Wildcards (Globbing)

Wildcards, also known as globbing patterns, are special characters that can be used to match multiple files or directories in a single command. They are very useful when you want to perform an operation on a large number of files at once. Here are some common wildcard characters and their meanings:

- `*`: Matches any number of characters, including none.
- `?`: Matches any single character.
- `[ABC]`: Matches any one of the characters inside the brackets (A, B, or C).
- `[a-k]`: Matches any character in the range from a to k.
- `[a-z0-9]`: Matches any alphanumeric character.
- `[!x]`: Matches any character except x.

You can use these wildcards in various commands, such as `cp`, `cd`, `ls`, and more. Here are some examples:

```
# Copy all files with any extension from the current directory to the "Documents" directory
cp *.*  Documents

# Change to the "Documents" directory
cd Documents/

# Go back one directory
cd ..

# List all files starting with the letter "D"
ls D*

# List all files with a three-letter name (e.g., file1.txt, abc.jpg)
ls t?
```

Wildcards are a powerful feature of the command line interface, as they allow you to perform complex operations on multiple files and directories with a single command. Understanding and using wildcards can greatly improve your efficiency when working in the terminal.

#

## touch

The `touch` command is used to change the timestamp (date and time) of a file. If the file does not exist, it will create a new file.

There are three types of timestamps that can be modified:

1. Access time (time when the file was last accessed)
2. Modification time (time when the file's content was last modified)
3. Change time (time when the file's metadata, such as permissions, was last changed)

Here are some of the common options for the `touch` command:

- `-a`: Change only the access time.
- `-c`: Do not create a new file if it doesn't exist.
- `-d`: Use the specified date and time instead of the current time.
- `-m`: Change only the modification time.
- `-r`: Use the same timestamps as the referenced file.
- `-t`: Create a file with the specified date and time.

Examples:

```
# Create a new file or update the timestamp of an existing file
touch filename

# Update the file's timestamp to 1 AM of the current date
touch -d "1am" filename

# Update the file's timestamp to 7:50 of the current date
touch -d "07:50" filename 

# Update the file's timestamp to yesterday 9 PM
touch -d "yesterday 9pm" filename

# Copy the timestamp from one file to another
touch -r referenceFile targetFile
```

To view the access time of files, you can use the `-l` option with the `ls` command.


#

## find

The `find` command is used for hierarchical file search. Here are some of the commonly used options for the `find` command:

- `-name`: Search for files/directories by name.
- `-iname`: Similar to `-name`, but case-insensitive.
- `-type d`: Search for directories.
- `-type f`: Search for files.
- `-size +N/-N`: Search for files larger/smaller than N units. Use `c` for bytes, `k` for kilobytes, `M` for megabytes, etc.
- `-empty`: Search for empty files or directories.
- `-atime -n`: Search for files accessed within the last n days.
- `-ctime n`: Search for files with metadata changed within the last n days.
- `-mtime n`: Search for files with content modified within the last n days.
- `-amin n`: Search for files accessed within the last n minutes.
- `-cmin n`: Search for files with metadata changed within the last n minutes.
- `-mmin n`: Search for files with content modified within the last n minutes.

Examples:

```
# Search for all files and directories in the current directory
find .

# Search for all directories in the "directory/" folder
find directory/

# Search for files starting with "f" in the current directory
find . -name "f*"

# Search for files starting with "f" (case-insensitive)
find . -iname "f*"

# Search for files starting with "t" (case-insensitive) in the current directory
find . -type f -iname "t*"

# Search for directories starting with "t" (case-insensitive) in the current directory
find . -type d -iname "t*"

# Search for files of exactly 65 bytes
find . -size 65c

# Search for files larger than 5 kilobytes
find . -size +5k

# Search for empty files and directories
find . -empty

# Search for files modified within the last day
find . -mtime -1

# Search for directories accessed within the last 45 minutes
find . -amin -45 -type d
```

If you want to perform an action on the files found by the `find` command, you can use the `-exec` option, followed by the command and the `{}` or `'{}'` placeholders to represent the found files, and end with `\;`.

Example:

```
# Print the contents of files modified within the last minute
find -mmin -1 -exec cat '{}' \;

# Print the arguments for files matching the pattern "/etc/rc*"
find /etc/rc* -exec echo Arg: {} \;
```

Additionally, you can use the `file` command to determine the file type, and the `locate` command to search for files by name.

```
# Determine the file type
file filename

# Search for files matching the pattern "*.txt"
locate "*.txt"
```

The `find` command is a powerful tool for searching and managing files and directories in a hierarchical file system.


#