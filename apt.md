
# Package Management in Linux 


To use the `apt` tool, you need to use its subcommands, such as `apt`, `apt-show`, and `apt-list`. Executing `apt` commands requires the root user or using `sudo` because these commands make changes to the system's core files, such as installing, removing, and updating packages.

1. Updating the package lists:
   ```
   sudo apt update
   ```
   This command updates the list of available packages from the configured repositories. It's essential to run this before installing or upgrading packages.

2. Upgrading all installed packages:
   ```
   sudo apt upgrade
   ```
   This command upgrades all installed packages to their latest versions.

3. Full system upgrade:
   ```
   sudo apt full-upgrade
   ```
   This command performs a full system upgrade, including installing new dependencies and removing incompatible packages.

4. Upgrading to a new Ubuntu version:
   ```
   sudo do-release-upgrade -d
   ```
   This command upgrades the Ubuntu distribution to the latest version. Note that this is not recommended if you have a weak or unreliable internet connection, as the download process can be interrupted.

5. Installing a package:
   ```
   sudo apt install package_name
   ```
   This command installs the latest version of the specified package.
   You can also install a specific version of a package:
   ```
   sudo apt install package_name=version
   ```

6. Installing multiple packages:
   ```
   sudo apt install package1 package2 package3
   ```
   This command installs the specified packages.

The downloaded packages are stored in the `/var/cache/apt/archives` directory.

Some additional `apt` commands:
- `apt search package_name`: Searches for packages by name or description.
- `apt show package_name`: Displays information about a specific package.
- `apt list --installed`: Lists all installed packages.
- `apt remove package_name`: Removes a package.
- `apt autoremove`: Removes packages that were installed as dependencies and are no longer needed.

The `apt` command provides a convenient way to manage packages on Ubuntu and Debian-based Linux distributions. It simplifies the process of updating, upgrading, and installing software packages.