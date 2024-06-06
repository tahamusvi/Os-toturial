# Permissions


## File Ownership and Permissions

Every file has three sets of permissions:

a) User permissions: Permissions for the file owner.
b) Group permissions: Permissions for the group the file belongs to.
c) Other permissions: Permissions for all other users.

Each set of permissions can have the following access rights:

- `r`: Read
- `w`: Write
- `x`: Execute

The `chown` command is used to change the owner of a file or directory. Only the root user can perform this operation in Linux.

Example:
```
sudo chown root:root hello.sh
```

The `chgrp` command is used to change the group ownership of a file or directory. Only the root user can perform this operation in Linux.

Example:
```
chgrp adm hello.sh
```

The `chmod` command is used to change the permissions of a file or directory.

`chmod symbolic-mode filename`

Symbolic modes:
- `u`: User (owner)
- `g`: Group
- `o`: Others
- `a`: All

Operations:
- `=`: Set
- `-`: Remove
- `+`: Add

Examples:
```
chmod u+x filename   # Add execute permission for the owner
chmod ug-x filename # Remove execute permission for the owner and group
chmod o-r filename  # Remove read permission for others
chmod o=wrx filename # Set permissions for others to read, write, and execute
chmod o=r, g=r, u=wrx filename # Set permissions for each category
```

Numeric mode:
```
chmod 755 filename  # rwx r-x r-x
chmod 744 filename  # rwx r-- r--
chmod 777 filename  # rwx rwx rwx
chmod 666 filename  # rw- rw- rw-
```

The `groups` command displays the groups the current user is a member of. The first group listed is the primary group.