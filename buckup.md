# Session 6

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