# File System and file type and file Permission 
---------------

## File Systema and file type
 

1. **File SystemI**

  - `Root Directory (/)`The top-level directory in the Linux file system. All other directories and files are contained within it.
  - `Directories` Directories are equivalent to "folders" in other operating systems. They are containers that can hold files and other directories.
  - `Files` Everything in Linux is considered a file, including text files, executables, devices, and even directories.
  - Paths:
      - `Absolute Path` A path that starts from the root directory (/). For example, /home/user/docs/file.txt.
      - `Relative Path` A path that is relative to the current working directory. For example, if you're in "/home/user", the relative path to "docs/file.txt" would be "docs/file.txt."

  - File Types:
      - `Regular files` These are the most common files, including text, binaries, images, etc.
      - `Directories` Special files that can contain other files and directories.
      - `Symbolic Links` Pointers to other files or directories.
      - `Device files` Special files that represent hardware devices, such as /dev/sda for a hard drive.
  - Mount Points:
    - In Linux, different file systems can be mounted at specific directories called mount points. For example, a separate file system for the '/home' directory can be mounted at '/home'.
      The `mount` command is used to mount file systems.

-**Directory structure if linux file System**
  - `/bin` Contains essential user command binaries, such as ls, cp, mv, etc.
  - `/boot` Contains boot loader configuration and executable files needed to start a Linux computer, including the Linux kernel.
  - `/dev` Contains device filesfor all hardware devices connected to the system.
  - `/etc` Contains system configuration files. and the local system configuration files for the host system.
  - `/home` Contains the home directories of users.
  - `/lib` Contains shared libraries needed by the binaries in /bin and /sbin. and 
  - `/mnt` and /media` Used for mounting filesystems like USB drives, CD-ROMs, etc.
  - `/opt` Contains optional software packages.
  - `/proc` A virtual filesystem that contains information about running processes and the system.
  - `/root` The home directory of the root user.
  - `/run` Contains runtime data for processes started since the last boot.
  - `/sbin` Contains essential system binaries, typically only used by the root user.
  - `/tmp` A directory for temporary files. users may temporarily store files here. Remember that files may be removed without prior 
           notice at any time in this directory.
  - `/usr` Contains user-installed software and libraries. It's often large and contains subdirectories like '/usr/bin' for binaries, 
            '/usr/lib' for libraries, and '/usr/share' for shared data.
  - `/var` Contains variable data like logs, databases, and spool files.

> **Important File System Commands**
  - `df` Displays disk space usage of file systems.
  - `du` Shows the disk usage of files and directories.
  - `mount` Mounts a file system.
  - `umount` Unmounts a file system.
  - `fsck` Checks and repairs a file system.
  - `mkfs` Used to create a new file system on a disk partition.
  - `lsblk` Lists information about block devices.
  - `blkid` Prints the UUIDs and labels of file systems.

2. **Types of Linux file system**
    When we install the Linux operating system, Linux offers many file systems such as `Ext`, `Ext2`, `Ext3`, `Ext4`, `JFS`, `ReiserFS`, 
    `XFS`, `btrfs`, 
    and swap.
   1. ext (Extended File System), ext2, ext3,ext4
      - `Ext4` file system is the faster file system among all the Ext file systems. It is a very compatible option for the SSD (solid- 
               state drive) disks, and it is the default file system in Linux distribution.
      - `XFS` File System was considered as high-speed JFS, which is developed for parallel I/O processing.
      - `Btrfs` stands for the B tree file system. It is used for fault tolerance, repair system, fun administration, extensive storage 
                configuration, and more.
     
   > **Create file system type**
   ```
     $ sudo mkfs.ext4 /dev/sdX1, Creating a new Ext4 file system on a partition:
     $ sudo mount /dev/sdX1 /mnt/ext4_partition, Mounting an Ext4 file system:
     $ df -hT /mnt/ext4_partition, Checking the file system’s disk usage:
   ```
   2. **Btrfs (B-Tree File System)**
       - `Btrfa` Btrfs is a modern, advanced file system designed to address the limitations of older file systems
     
   > **Create file**
   ```
     $ sudo mkfs.btrfs /dev/sdX1, Creating a new Btrfs file system on a partition:
     $ sudo mount /dev/sdX1 /mnt/btrfs_partition, Mounting a Btrfs file system:
     $ sudo btrfs subvolume create /mnt/btrfs_partition/subvol1, Creating a Btrfs subvolume:
     $ sudo btrfs subvolume snapshot /mnt/btrfs_partition/subvol1 /mnt/btrfs_partition/snapshot1, Taking a snapshot of a Btrfs subvolume
   ```
   3. XFS (XFS File System)
       - `XFS` is a high-performance, journaling file system that excels in handling large files and massive storage volumes.
    
 >  **Create file**
   ```
     $ sudo mkfs.xfs /dev/sdX1, Creating a new XFS file system on a partition:
     $ sudo mount /dev/sdX1 /mnt/xfs_partition, Mounting an XFS file system:
     $ df -hT /mnt/xfs_partition, Checking the file system’s disk usage:
   ```

  
# **File permisssion**

   - **File Permission Basics**
       - `Read (r)` Permission to read the contents of the file or list the contents of a directory.
       - `Write (w)` Permission to modify the contents of the file or make changes within a directory (e.g., create or delete files).
       - `Execute (x)` Permission to execute a file (if it’s a script or binary) or enter a directory.
       - `Owner` The user who owns the file.
       - `Group` The group that owns the file. Multiple users can belong to this group.
       - `Others` All other users on the system.
     - Numeric Representation of Permissions
        - Read (r): 4
        - Write (w): 2
        - Execute (x): 1

      > **Changing Permissions**
        - `chmod` command is use for set the permission for  owner, group, other, read,write,execute.

    > Example
      ```
       $ ls -ls or ll or ls -h etc, check the permission 
       $ chmod u+x file.txt,  Add execute permission for the owner
       $ chmod g-w file.txt, Remove write permission for the group)
       $ chmod o=rx file.txt, Set read and execute permissions for others
       $ chmod 755 file.tx, set permissions by octal form by useinf 4,2,1=7 for full permissions,
      ```
  - ****Changing Ownership****
      - `chown` command is use for  change the owner and group of a file.
      - "Change owner" chown newowner file.txt
      - "Change group" chown :newgroup file.txt
      - "Change both owner and group" chown newowner:newgroup file.txt

    > Example 
    ```
     $ chmod 755 script.sh, Grant all permissions to the owner, and read and execute to group and others:
     $ chmod o-w file.txt, Revoke write permissions from others:
     $ chmod u+x file.sh, Make a file executable by the owner only:
     $ chown new-owner-name:new-group-name file.txt, chnage the owner and group of a file
    ```

##  **Special permission Sticky bit(10, setuid(4) and setgid(2)**  
   - `setuid` When set on a file, it allows users to run the file with the permissions of the file owner.
   - `setgid` When set on a directory, newly created files within the directory inherit the group of the directory.
   - `Sticky bit` The sticky bit is a special type of permissions used in unix and Linux OS's. When set on a directory, it allows only 
      the owner of a file to delete or rename the files within the directory. and prevent from other user's to delet and rename.
     
  


          
        

         





















       
       















