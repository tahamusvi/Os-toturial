# Session 2

## Users and User Management in Linux

In Linux, like other operating systems, users are classified into different categories with varying levels of access and permissions. For example, regular users cannot delete or modify system files, but the system administrator (root user) can perform almost any operation on the system.

However, it is recommended to use the root account sparingly and instead use a regular user account for day-to-day tasks to reduce the risk of security breaches and accidents.

Linux manages user accounts and permissions through the following three files in the `/etc/` directory:

1. `/etc/passwd`:
   - This file is used for user authentication.
   - Each line in this file represents a user account and contains the following fields separated by colons:
     - `username`: The user's login name.
     - `password`: If this field contains an 'x', the password is stored in the `/etc/shadow` file in an encrypted form. If it's empty, the user has no password, and if it contains an asterisk (`*`), the account is disabled.
     - `uid`: The unique user ID number. Non-system users have IDs higher than 1000, and the root user has an ID of 0.
     - `gid`: The primary group ID of the user.
     - `gecos`: Additional information about the user, such as the full name.
     - `home_directory`: The user's home directory.
     - `login_shell`: The default shell for the user, typically `/bin/bash`.
   - To disable a user's ability to log in, you can set the `login_shell` field to `/sbin/nologin`.

2. `/etc/shadow`:
   - This file contains the encrypted passwords for user accounts.
   - Each line in this file represents a user account and contains the following fields separated by colons:
     - `name`: The user's login name.
     - `password`: The user's encrypted password.
     - `last_change`: The number of days since the password was last changed (counted from January 1, 1970).
     - `min`: The minimum number of days the user must wait before changing the password.
     - `max`: The maximum number of days the password is valid.
     - `warn`: The number of days before the password expires that the user will be warned.
     - `inactive`: The number of days of inactivity after the password expires before the account is disabled.
     - `expire`: The date when the account will be disabled (in the format YYYY-MM-DD).

3. `/etc/group`:
   - This file contains information about the groups defined on the system.
   - Each line in this file represents a group and contains the following fields separated by colons:
     - `name`: The name of the group.
     - `password`: This field is typically set to 'x', as groups usually don't have passwords.
     - `gid`: The unique group ID number.
     - `members`: The list of users who are members of the group.

Understanding these user management files and the different user roles in Linux is essential for administering and securing a Linux system effectively.

#

## passwd
The `passwd` command is used to change the password of a user account. It prompts the user to enter the current password and then to enter a new password twice to confirm it.

`passwd [username]`

This command can be used by regular users to change their own password, or by administrators to change the password of other user accounts.

# 

## vigr
The `vigr` command is used to edit the `/etc/group` file, which contains information about user groups.

`vigr`

When executed, this command opens the `/etc/group` file in the default text editor (usually Vi or Vim) for editing. Administrators can use this command to add, modify, or remove group entries.

#

## chage
Correct, the `chage` command is used to change the values of the fields in the `/etc/shadow` file. Here are the details:

The `chage` command allows you to modify the following fields in the `/etc/shadow` file:

- `-m`: Change the minimum number of days before a password can be changed.
- `-M`: Change the maximum number of days a password is valid.
- `-d`: Change the date of the last password change (in the format YYYY-MM-DD).
- `-E`: Change the expiration date of the account.
- `-I`: Change the number of inactive days after a password expires before the account is locked.
- `-W`: Change the number of days before the password expires that the user is warned.

Example:

```
chage -d 2021-04-12 test
```

This command will change the date of the last password change for the user `test` to April 12, 2021.

The `chage` command is a powerful tool for managing user account settings related to password expiration, password change policies, and account inactivity. It allows you to fine-tune the password and account security settings for individual users on the system.
#

## vipw
the `vipw` command is a useful tool for editing user-related configuration files in Linux.

By default, the `vipw` command is used to edit the `/etc/passwd` file, which contains user account information.

you can use the following options with `vipw` to edit other related files:

1. `-s`: This option allows you to edit the `/etc/shadow` file, which contains the encrypted passwords for user accounts.
2. `-g`: This option allows you to edit the `/etc/group` file, which contains information about the groups defined on the system.

So, the full usage of the `vipw` command would be:

```
vipw [options]
```

Where the available options are:

- No option: Edit the `/etc/passwd` file.
- `-s`: Edit the `/etc/shadow` file.
- `-g`: Edit the `/etc/group` file.

This flexibility of the `vipw` command makes it a convenient tool for managing user-related configuration files in a Linux system. By using the appropriate options, you can directly edit the `/etc/passwd`, `/etc/shadow`, or `/etc/group` files, which are the core user management files in Linux.

#

## useradd
 The `useradd` command is used to create a new user account in Linux.

Syntax:
```
useradd [options] username
```

Here are some of the commonly used options:

- `-d`: Specify the home directory for the new user. If this option is not used, the system will create a home directory based on the default settings.
- `-m`: Create the home directory for the new user if it doesn't already exist.
- `-s`: Specify the default shell for the new user.
- `-e`: Specify the expiration date for the account (in the format YYYY-MM-DD).
- `-g`: Specify the primary group for the new user.
- `-u`: Specify the user ID (UID) for the new user.

Examples:
```
useradd user1 -d /home/user1
useradd user1 -s /bin/zsh
useradd user1 -e 2021-4-18
useradd user1 -g head
```

These commands will create a new user named `user1` with the following settings:

1. The home directory is set to `/home/user1`.
2. The default shell is set to `/bin/zsh`.
3. The account expires on April 18, 2021.
4. The primary group for the user is set to `head`.

The `useradd` command is a powerful tool for creating new user accounts with the desired configurations. It allows you to set various user account properties, such as the home directory, default shell, group membership, and expiration date.
#

## userdel
The `userdel` command is used to delete a user account.

`userdel [options] username`

Some common options include:
- `-r`: Remove the user's home directory and mail spool.
- `-f`: Force the deletion, even if the user is currently logged in.

#

## usermod
The `usermod` command is used to modify an existing user account.

`usermod [options] username`

Some common options include:
- `-d`: Change the user's home directory.
- `-L`: Lock the user's account.
- `-U`: Unlock the user's account.
- `-u`: Change the user ID (UID) of the user.
- `-e`: Change the expiration date of the user's account (in the format YYYY-MM-DD).
- `-l`: Change the username of the user.
- `-d`: Change the home directory of the user.
- `-g`: Change the primary group of the user.
- `-s`: Change the default shell of the user.


Correct, the `usermod` command is used to modify the properties of an existing user account in Linux. Here are the details:


Examples:
```
usermod -u 1234 john  # Change the UID of user 'john' to 1234
usermod -e 2023-12-31 jane # Change the expiration date of user 'jane' to December 31, 2023
usermod -l newuser olduser # Rename the user 'olduser' to 'newuser'
usermod -d /home/newdir alice # Change the home directory of user 'alice' to '/home/newdir'
usermod -g admins bob # Change the primary group of user 'bob' to 'admins'
usermod -s /bin/zsh charlie # Change the default shell of user 'charlie' to '/bin/zsh'
```

The `usermod` command allows you to modify various user account properties, such as the user ID, expiration date, username, home directory, primary group, and default shell. This is useful when you need to update user account information or change the configuration of an existing user account.

#

## groupdel
The `groupdel` command is used to delete a user group.

`groupdel groupname`

This command removes the specified group from the system. Any files or processes owned by the group will be reassigned to a different group.

#

## groupmod
The `groupmod` command is used to modify an existing user group.

`groupmod [options] groupname`

Some common options include:
- `-n`: Change the group's name.
- `-g`: Change the group's GID (Group ID).

#


## gpasswd
The `gpasswd` command is used to administer the `/etc/group` file, which contains information about the groups on the system.

The specific usage is:

1. Assigning a regular user as the administrator of a group:
   ```
   gpasswd -A user3 head
   ```
   After running this command, the user `user3` becomes the administrator of the `head` group.

2. Adding a user to a group:
   ```
   gpasswd -a user5 head
   ```
   This command adds the user `user5` to the `head` group.

3. Removing a user from a group:
   ```
   gpasswd -d user5 head
   ```
   This command removes the user `user5` from the `head` group.

As the administrator of the `head` group, `user3` can now use these `gpasswd` commands to manage the membership of the group. The `-a` option adds a user to the group, and the `-d` option removes a user from the group.

The `gpasswd` command is a useful tool for managing group memberships and group administrators in a Linux system. It allows you to delegate group management tasks to specific users, which can be helpful in larger environments with complex group structures.