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

##  **Special permission Sticky bit(1), setuid(4) and setgid(2)**  
   - `setuid` When set on a file, it allows users to run the file with the permissions of the file owner.
   - `setgid` When set on a directory, newly created files within the directory inherit the group of the directory.
   - `Sticky bit` The sticky bit is a special type of permissions used in unix and Linux OS's. When set on a directory, it allows only 
      the owner of a file to delete or rename the files within the directory. and prevent from other user's to delet and rename.
     
  
1. **Sticky Bit **
  - It's represent by 't' (Meaning x is also there), and 'T' reprent when there is no 'x' for other ( where x=execure)
  - Users can create and edit their own files in the directory, Only the owner of a file, the owner of the directory, or the root user 
    can delete or rename files in that directory,Other users with write access to the directory cannot delete or rename files they do 
    not own.
  - ` chmod +t /shared` , set the sticky bit on a directory 
  - ` chmod -t /shared` , Remove the sticky bit from a directory 
  -  `chmod 1777 /directory_name`, Numeric method (use 1 in front of the usual permission digits)

> Example
 ```
  $ chmod +t /shared, set the sticky bit on a directory 
  $ ls -ld /shared, check sticky bit is set or not
  $ drwxrwxrwt 2 root root 4096 Aug 30 10:00 /shared
  $ chmod -t /directory_name, Remove sticky bit
  $ chmod 1777 /directory_name, Numeric method (use 1 in front of the usual permission digits): 
  $ chmod 0777 /directory_name, Rmove sticky using numeric method
 ```

2. **setuid(4) permission**
   - `setuid` (Set User ID) When set on a file, it allows users to run the file with the permissions of the file owner.
   - When the setuid bit is set, the file runs with the permissions of the file's owner (e.g., root), rather than the user who launched 
    the program.The 'setuid bit' is represented by an s in the owner's execute permission field when viewing permissions.
   - It’s represented by an `s` in the owner’s execute field.
   - Numeric method (use 4 in front of the usual permission digits).
   - `chmod u+s filename`, set the setuid bit on a file using the chmod command:
   - `chmod 4755 filename`, Numeric method (use 4 in front of the usual permission digits
   - `chmod u-s filename`, remove setuid by notmal
   - `chmod 0755 filename`, remove setuid by numeric method

> Example
 ```
  $ touch myscript.sh, create new file with .sh extension
  $ chmod +x myscript.sh, make the full permission to the owner of the file.
  $ chmod u+s myscript.sh, setuid on file
  $ ls -l myscript.sh,      Verify the permission
  $ -rwsr-xr-x 1 user user 0 Aug 30 10:00 myscript.sh     
  $ chmod u-s filename, Remove the setuid
  $ chmod 4755 filename, Numeric method (use 4 in front of the usual permission digits).
  $ chmod 0755 filename, Remove setuid by numeric method
 ```

3. **setgid permission**
   - `Setgid` (Set Group ID) is a special permission in Linux that can be applied to both files and directories. When the setgid bit is 
      set on a file or directory, it affects how group ownership is handled.
   - `On Files` When the setgid bit is set on an executable file, any user who executes the file temporarily assumes the group ID of the 
     file’s group, rather than their own group ID.
   - `On Directories` When the setgid bit is set on a directory, all files and subdirectories created within it inherit the group 
     ownership of the directory, instead of the primary group of the user who created them.
   - When the setgid bit is set, the group's execute permission (second set of three permissions) will have an s instead of an x
   - `chmod g+s filename` , To set the setgid bit on a file
   - `chmod 2755 filename` , Numeric method (use 2 in front of the usual permission digits)
   - `chmod g-s filename` , Removing the Setgid Bit
   - `chmod 0755 filename` remove by Numeric method.

> Example
```
 $ mkdir shared_directory, create a directory
 $ chown root:staff shared_directory, set group ownership
 $ chmod g+s shared_directory, Set the setgid bit
 $ ls -ld shared_directory, verify
 $ drwxrwsr-x 2 root staff 4096 Aug 30 12:00 shared_directory
 $ chmod 2755 filename, Numeric method (use 2 in front of the usual permission digits
 $ chmod g-s filename, Remove the  the setgid bit
 $ chmod 0755 filename, Remove the  the setgid bit by numeric method
```

## ACL (Access control list) permission
  - `ACl` It's special type of permissions, an ACL let you assing permissions for each unique user or group. suppose user1,user2, and 
     user3 on a system you must assing this permission to the directory, user1 can read and write permission.
  - With ACLs, you can set permissions for multiple users or groups, providing flexibility in how access is controlled.
  - Standard Permissions: In Linux, each file or directory has standard permissions for three entities—owner, group, and others. 
    However, with ACL, you can grant specific permissions to additional users or groups.
  - ACLs consist of entries that define the permissions for users or groups. You can have separate ACL entries for different users or 
    groups, allowing them distinct permissions (read, write, execute) on a file or directory  
  - Types of ACL Entries
    - User ACL: Permissions for individual users.
    - Group ACL: Permissions for individual groups.
    - Mask: Defines the maximum allowed permissions for users and groups.
    - Other: Same as the default Linux permission for others
  - `getfacl filename`, To view the ACLs set on a file or directory, use the getfacl command
  - `setfacl -m u:username:permissions filename` To set an ACL on a file or directory, use the setfacl command.
  - `setfacl -m g:groupname:permissions filename` Set ACL for a group
  - `setfacl -m d:u:username:permissions directoryname` ,Set default ACL for a directory: (for future files created within the directory)
  - `setfacl -x u:username filename`, To remove an ACL entry
  - `setfacl -b filename` To remove all ACLs from a file.
  - If the file has ACLs, a + symbol will appear at the end of the permission string.
  - `setfacl -x g:groupname filename`, to remove ACL from group

> Example
```
 $ $ ls -l myfile.txt
 $ -rw-rw-r--+ 1 user1 group1 4096 Aug 30 12:00 myfile.txt
 $ mkdir /shared,Create a shared directory:
 $ chmod 770 /shared, set permission 
 $ setfacl -m u:john:rwx /shared, Grant additional users specific access with ACL, This grants user john read,write,execute permission.
 $ getfacl /shared, View the ACL.
 $ setfacl -m g:groupname:permissions filename, set ACL for group
 $ setfacl -x u:username filename
 $ setfacl -b filename  # Remove all ACLs
```

4. **chattr (change attribute) command**
 - `chattr` command in Linux is used to change the attributes(set/unset) of files or directories on a file system.to secure accidental 
    deletion on modification of important files and folders even though you are logged in as root user.
 - Common File Attributes with `chattr`
     - `i` (Immutable): Once this attribute is set, the file cannot be modified, deleted, renamed, or even written to.
     - `a` (Append-only): The file can only be opened in append mode for writing. This means data can be added to the file, but the  
           existing content cannot be modified or deleted.
     - `e` (Extents): This attribute indicates that the file is using extents for mapping the blocks on disk. This is a default behavior 
           for modern file systems.
     - `A` (No Atime Updates): When set, the access time (atime) of the file is not updated, which can help in improving performance for 
           frequently read files.
     - `S` (Synchronous Updates): Ensures that all file modifications are written synchronously on the disk.

  - `chattr [operator][attributes] [filename]` Syntax of chattr
  - Operator
      - '+' to add an attribute.
      - '-' to remove an attribute.
      - '=' to set the attribute exactly as specified.
        
  - `sudo chattr +i important_file.txt`. protect a file from being modified or deleted, you can set the immutable bit using the +i flag
  - `sudo chattr -i important_file.txt` To remove the immutable bit
  - `sudo chattr +a logfile.txt` to use that existing content is not accidentally overwritten, but new data can still be appended.
  - `sudo chattr -a logfile.txt` To remove the append-only bit
  - `sudo chattr +A filename`  Disable Access Time Updates
  - `lsattr filename` Viewing File Attributes with lsattr
  - 





    
     



 


 
    





    

     

     

     


        

         





















       
       















