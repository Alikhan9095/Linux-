# **Linux basic commands**
----------------------------------------------------------

- `sudo` is a command that lets a user run commands with superuser or root privileges, allowing them to perform administrative tasks on the system.
- `sudo -i` or `su` command allow you to switch a normal user to a super user or root user.
- `whoami` command displays the username of the currently logged-in user.
- `who` Lists all users currently logged into the system.
- `w or who am i` Provides detailed information about users and their activities or Shows information about the current terminal session
- `id` Displays the current user's UID, GID, and group memberships.
- `pwd` command  to check current working directory
- `cd` command to use for chnage the directory.
     1. `cd` go to your home direcoty.
     2. `cd ..` go to back one directory
- `tree` command in Linux is used to display a directory structure in a tree-like format
-  `man command`  in Linux is used to display the manual pages of other commands and programs. It provides detailed information about how a command works, its 
      options, usage examples, and other relevant details. It is an essential tool for anyone looking to understand how to use a particular command or utility in Linux.
-  `ls` Lists the files and directories in the current directory.  and it's very usfull with diffirents flags such as below.
-  `ls 'directory pat'` list the directory/file in specfied directory
     1. `ls -ls` or `ls -l` list the directory/files with more details such as permissions,link,ownership,filetyps,fielsize,modification date etc
     2. `ls -lh` It is similar to above commands but it's show the details in human readable formats.
     3. `ls -la` or `ll` list the hidden directory/files in directory or specified directory
     4. `ls -lah` Lists all files in long format with human-readable file sizes.
     5. `ls -ltr` Lists files sorted by modification time, oldest first, in long format.
     6. `ls -R /path` Recursively lists all files and directories starting from /path.
        
> Example
       
       $ ls -lh /home/user: Lists files in /home/user with detailed information and human-readable file sizes.
       $ ls -aR: Lists all files, including hidden ones, recursively in all subdirectories.

## init ?

  - `init` is the traditional initialization system that is responsible for booting the system, managing services, and maintaining 
           system states. It is the first process started by the 
           kernel and has a `process ID (PID) of 1`.
     1. System Initialization: It initializes the system, sets up the environment, and starts other essential processes.
     2. Service Management: It manages and starts system services and processes according to the system’s runlevel.
    
  **Runlevels**
  -  Runlevels define the state of the system (e.g., single-user mode, multi-user mode). Each runlevel corresponds to a different set of 
     services and system states.
  -  Common runlevels include:
   1. 0: Halt (shutdown)
   2. 1: Single-user mode (for maintenance)
   3. 2-5: Multi-user modes (with or without GUI)
   4  6: Reboot

   - `/etc/init.d/` Directory containing scripts for starting and stopping services in the traditional SysV init system.
   - `/etc/rc.d/ or /etc/rcX.d/` Directories containing symbolic links to the init scripts for each runlevel.


      > Example
  ```
     init <runlevel> To change the system runlevel, use the init command followed by the desired runlevel:
     $ init 3, This command changes the system to runlevel 3 (multi-user mode with networking).
     $ init 6, This command reboots the system.
     $ init 0, This command shuts down the system.
  ```
    

       
       
 ## cat command
- `cat` command in Linux is used to concatenate and display the contents of files.
     1. `cat filename` Displays the contents of the specified file.
     2.  `cat > filename` Creates a new file (or overwrites an existing file) and allows you to input text into it. Press Ctrl + D to save and exit.
     3.   `cat >> filename` Appends text to an existing file. Press Ctrl + D to save and exit.
     4.   `cat file1 file2 > newfile`  the contents of file1 and file2 and writes them to newfile created.
     5.   `cat -n filename` Displays the contents of the file with line numbers.
     6.   `cat -b filename` Similar to -n, but only numbers non-blank lines.
     7.   `cat [filename] | grep [pattern]` Searches for a pattern in the file and displays matching lines.

> Example..
```
   $ cat file : View the contents of a file
   $ cat > file : eate a new file
   $ cat part1.txt part2.txt > combined.txt : create a new file and copy multiple files's contents in new file
   $ cat >> log.txt : Append(write in a file without using editor) to an existing file 
   $ cat /etc/passwd | grep username : Displays the contents of the /etc/passwd file, which contains user account information.
```

## Less command

- `less` command in Linux is a powerful utility for viewing the contents of a file one screen at a time. It’s particularly useful for reading large files because it doesn't load the entire file into memory, making it faster and more efficient than **cat or more** for this purpose.
- `less [filename]` Opens the specified file in the less viewer.
- `less file1.txt file2.txt` Open Multiple Files.


  > Navigation in `less`:
  
    1. Move Down One Line: `j or ↓`
    2. Move Up One Line: `k or ↑`
    3. Move Down One Page: `Space or Ctrl + F`
    4. Move Up One Page: `b or Ctrl + B`
    5. Go to Start of File: `g`
    6. Go to End of File: `G`
    7. Search Forward: /search_term (press n to go to the next occurrence)
    8. Search Backward: ?search_term (press n to go to the previous occurrence)
    9. Exit less: `q`

 > Common Options:

- `less -N [filename]` Displays line numbers alongside the file content.
- `less +[number] [filename]` Starts displaying the file from a specific line number.
- `less -S [filename]` Disables line wrapping, making long lines scroll horizontally.
- `less -i [filename]` Performs case-insensitive searches.
- `less -R [filename]` Displays raw control characters, useful for viewing files with colored output.
- `less /[search_term] [filename]` Opens the file and immediately searches for the specified term.

> Example..
  ```
$ less /var/log/syslog View a file
$ Search for a term in the file: /error
$ Display with line numbers: less -N script.sh
$ Disable line wrapping: less -S longfile.txt
 ```

## more command

- `more` command in Linux is used to view the contents of a file one screen at a time, similar to less. However, more has fewer features and is less flexible than less. It's primarily used for viewing text files and allows basic navigation through the content.
   1. `more [filename]` Opens the specified file in the more viewer
   2. `more +[number] [filename]` Starts displaying the file from a specific line number.
   3. `more -d [filename]` Displays "[Press space to continue, 'q' to quit.]" at each prompt to make it more user-friendly.
   4. `more -c [filename]` Clears the screen before displaying each new page of text.
   5. `more -s [filename]` Squeezes multiple consecutive blank lines into a single blank line.


> Example
  ```
     $ more /etc/passwd  View a file
     $ more +50 file.txt,  Start viewing from a specific line
     $ more -c largefile.txt,  View a file with clear screen pages:
     $  /error ,  Search within the file
     $ cat largefile.txt | more,  You can use more to view the output of other commands that produce a lot of text
  ```

  **Note**
   - `more` Simple and easy to use but has limited navigation (can’t scroll backward without buffering).
   - `less` More advanced, supports both forward and backward navigation, better for large files.


     ## touch command (make a empty file)

     - `touch` command in Linux is primarily used to create empty files or update the timestamp of existing files without modifying their content. It’s a simple yet essential command 
               for file management in the Linux environment. 
         1. `touch [filename]` Creates a new, empty file with the specified name if it doesn’t already exist.
         2. `touch [filename1] [filename2] ...` Creates multiple files at once.
         3. `touch -c [filename]` Does not create the file if it doesn't exist, but still updates the timestamps if the file exists.
         4. `touch -a [filename]` Updates only the access time of the file.
         5. `touch -m [filename]` Updates only the modification time of the file.
         6. `touch -t [[[CC]YY]MMDDhhmm[.ss]] [filename]`Sets a specific timestamp rather than the current time.The format is [[CC]YY]MMDDhhmm[.ss] (Year,Month,Day,Hour,Minute, Seconds).
         7. `touch -r [reference_file] [filename]` Sets the timestamp of filename to be the same as reference_file
            

> Examples:
  ```
      $ touch newfile.txt, Create an empty file
      $ touch file1.txt file2.txt file3.txt, Create multiple files
      $ touch -a document.txt, Update only the access time
      $ touch -m report.txt, Update only the modification time
      $ touch -t 202401010000.00 newyear.txt, Set a specific timestamp
      $ touch -r oldfile.txt newfile.txt, Copy the timestamp from another file
  ```

## mkdir command (make a directory)

- `mkdir` command in Linux is used to create directories. It allows you to create single or multiple directories at once, and you can specify the permissions and parent directories 
              if they don't already exist.
  1. `mkdir [directory_name]` Creates a new directory with the specified name.
  2. `mkdir -p [directory_path]` Creates a directory along with any necessary parent directories that don't already exist.
  3. `mkdir -m [mode] [directory_name]` Sets the permissions of the directory at the time of creation.
  4. `mkdir -v [directory_name]` Displays a message for each directory that is created.


> Exmapl

   ```
         $  mkdir directoryname, Create a single directory:
         $ mkdir folder1 folder2 folder3, Create multiple directories at once
         $ mkdir -p /home/user/docs/2024/january, Create a directory with in a directory or under specific directory or create subdirectory in parents directory, if they don’t exist.
         $ mkdir -m 700 secure_folder, Create a directory with specific permissions  (only the owner can read, write, and execute)
         $ mkdir -v logs, Verbose output when creating a directory
         $ mkdir -p project/{src,bin,lib,docs}, creates a project directory with subdirectories src, bin, lib, and docs
   ```

## **Delete or Remove file/Directory**

- **Deleting Files with rm Command**
  1. `rm [file_name]` Deletes the specified file.
  2. `rm -i [file_name]` Prompts for confirmation before deleting the file.
  3. `rm -f [file_name]` Forces the deletion of a file without asking for confirmation (useful for deleting files without write permissions).
  4. `rm -v [file_name]` Displays a message for each file that is deleted.
  5. `rm *.txt` Deletes all files with a specific pattern. For example, this command deletes all .txt files in the current directory.

- **Deleting Directories**
  1. `rmdir [directory_name]` Deletes an empty directory.
  2. `rm -r [directory_name]` Recursively deletes a directory and all its contents, including subdirectories and files.

- **Common Options with `rm -r`**
  1. `rm -rf [directory_name]` Forces the deletion of a directory and its contents without prompting for confirmation. This is a powerful command that should be used with 
                                         caution.
  2. `rm -rv [directory_name]` Recursively deletes the directory and its contents, displaying each action.

> Examples

  ```
        $ rm notes.txt, Delete a Single File:
        $ rm file1.txt file2.txt, Delete Multiple Files
        $ rm *.bak (deletes all .bak files), Delete All Files Matching a Pattern
        $ rmdir old_directory, Delete an Empty Directory:
        $ rm -r project_backup, Delete a Directory and Its Contents
        $rm -rf temp_directory, Force Delete a Directory Without Prompting
  ```

**Important Notes**
- Use with Caution: Commands like rm -rf are very powerful and can lead to accidental data loss if used carelessly. Always double-check the command and paths before execution.
- Confirm Deletion: The -i option can help prevent accidental deletions by asking for confirmation.


## CP command

- `cp` command allows you to copy files and directories from one location to another
    1. `cp [source] [destination]` Copies the file from the source to the destination
    2. `cp -r [source_directory] [destination]` Recursively copies an entire directory and its contents.
    3. `cp -i [source] [destination]` Prompts for confirmation before overwriting any files at the destination.
    4. `cp -v [source] [destination]` Displays the files being copied.
    5. `cp -a [source_directory] [destination]` Archives the source directory, preserving the structure, attributes, and symbolic links.
    6. `cp *` command is used to copy multiple files at once. The * is a wildcard that represents all files in the current directory.This command is handy when you want to copy all 
           files (but not directories) from one location to another
    7. `cp -r .* * /home/user/backup/` This command copies all files, including hidden ones, from the current directory to /home/user/backup/.
 
> Exmapl
  ```
    $ cp file.txt /home/user/, Copy a File
    $ cp file1.txt file2.txt /home/user/, Copy Multiple Files
    $ cp -r /home/user/docs /backup/, Copy a Directory and Its Contents:
    $ cp -i important.doc /backup/, Copy with Confirmation Before Overwriting
    $  cp -r .* * /home/user/backup/` This command copies all files, including hidden ones from current directory
    $ cp * /home/user/backup/,  This command copies all files,from current directory
  ```

## mv Command (Move/Rename)

- `mv`command is used to move files and directories from one location to another. It can also be used to rename files and directories.
  1. `mv [source] [destination]` Moves or renames the file or directory
  2. `mv -i [source] [destination]` Prompts for confirmation before overwriting any files at the destination.
  3. `mv -v [source] [destination]` Displays the files being moved or renamed.
  4. `mv -n [source] [destination]` Prevents overwriting files at the destination.
  5. `mv oldname.txt newname.txt` Rename a file
  6. `mv olddir newdir` Rename a directory
  7. `mv /home/user/docs /backup/` Move a directory to another location
  8. `mv file1.txt file2.txt /home/user/` Move multiple files to a directory

> Example
  ```
$ mv file.txt /home/user/, Move a File
$ mv oldname.txt newname.txt, Rename a File
$ mv /home/user/docs /backup/, Move a Directory
$ mv -i important.doc /backup/, Move with Confirmation Before Overwriting
  ```

**Practical Uses:**
-  Backups: Use cp -r to back up entire directories.
-  Organizing Files: Use mv to organize files into appropriate directories.
-  Batch Renaming: Use mv to rename multiple files with a script.


## **Memory and CPU usages**

- `cat /proc/meminfo` file provides detailed information about your system's memory usage and about the system's RAM and swap memory.
- `cat /proc/cpuinfo` Displays detailed information about each CPU core, including its vendor, model, frequency, cache size, and more.
- `lscpu` command in Linux provides detailed information about the CPU architecture of the system, display CPU-related information such as the number of CPUs, threads, cores,etc.
- `mpstat` command is part of the "sysstat" package and is used to report CPU statistics. It provides detailed information about the usage of each individual CPU or core in your system
  1. `sudo apt-get install sysstat` Debian/Ubuntu
  2. `sudo yum install sysstat` CentOS/RHEL
- `nmon` is a performance monitoring tool that provides real-time CPU, memory, disk, and network usage.
- `iostat` command provides CPU and I/O statistics.
- `uptime` command in Linux is used to find out how long the system has been running since the last reboot. It also provides information about the current time, the number of users 
          currently logged in, and the system load averages for the past 1, 5, and 15 minutes.

  ## **How to check kernel version**

  - `uname -r` command  display the kernel version
  - `hostnamectl` If you are using a systemd-based distribution, you can use hostnamectl to get the kernel version along with other system information.
  - `cat /proc/version` This command will display detailed information about the kernel version and some additional information, including the compiler used.
  - `dmesg | grep "Linux version"` command to filter out kernel version information
 
## **free command**

- `free` command in Linux is used to display information about the system's memory usage, including both physical and swap memory. It provides a snapshot of how much memory is being 
          used, how much is free, and other memory-related statistics.
    1. `free -h` Displays the output in a human-readable format (e.g., MB or GB)
    2. `free -s (specify time )`  Continuously display memory usage every specified number of seconds.

  > Exmaple
   ```
  $ free -s 5 This command will update the memory usage information every 5 seconds.
   ```

**Practical Use** 
-  `Monitor Memory Usage` Helps in checking the overall memory usage and diagnosing memory-related issues.
-  `Performance Tuning` Useful for performance tuning by understanding how much memory is being used by the system and applications.

## **top and htop commands**

****top Command****
-  `top` command in Linux is a powerful utility for monitoring system performance and resource usage in real-time. It provides a dynamic, real-time view of system processes and their 
      resource consumption such as memory, cpu, Current Time,System Uptime,Number of Users login,Load Average,task et
  1. `Tasks` Total number of tasks (processes), and their states (running, sleeping, stopped, zombie).
  2. `Memory Usage` KiB Mem: Displays memory usage including total, free, used, and buffer/cache
       1. KiB Swap: Displays swap space usage including total, free, and used.

  3. `CPU Usage` Shows the percentage of CPU usage, broken down into user space (us), system space (sy), nice (user-space processes with a modified priority, ni), idle (id), waiting 
                 (wa), hardware interrupts (hi), software interrupts (si), and steal time (st).
         
**Common Commands and Keybindings in `top`**
```
q: Quit top.
h: Display help information.
P: Sort processes by CPU usage.
M: Sort processes by memory usage.
T: Sort processes by runtime.
k: Kill a process by PID (prompts for the PID).
r: Renice a process (change its priority, prompts for PID and new priority value).
top -d <seconds> Change the refresh interval (in seconds) to update the displa
top -u <username> Display processes for a specific user.
```
**example**
```
$ top -d 5 This command refreshes the top display every 5 seconds.
```

****htop Command****
- `htop` is an interactive process viewer for Unix systems, similar to top but with a more user-friendly and visually appealing interface. It provides a real-time, color-coded display 
         of system processes and resource usage. 
**Features and Keybindings**
  
- `Process Information` Provides detailed information about each process, including PID, user, priority, memory usage, and CPU usage.
- `Color Coding` Uses colors to indicate different levels of CPU and memory usage, making it easier to interpret.
- `Resource Meters` Displays CPU, memory, and swap usage in graphical bars at the top of the screen.

  **dvanced Usage**
  + `htop -u <username>` This command displays processes for a specific user.
  + `htop -d <delay> -u <username>` This command runs htop with a spevify time of second update delay and filters processes by the specified user.

  **Example**
  ```
  $ htop -d 5 -u username This command runs htop with a 5-second update delay and filters processes by the specified user.
  ```
 
## **df and du commanda**

-  The `df` and `du` commands in Linux are essential tools for monitoring disk space usage. While they serve similar purposes, they have different focuses and use cases.

**df command**

- `df` The command stands for "disk free" and displays information about the file system disk space usages, It provides an overview of available,used, total disk space on mounted 
      filesystems. It help you ubderstand how much space is used and how much is available on each partition on file system.
    1. `df -h` Displays the output in a human-readable format (e.g., KB, MB, GB).
    2. `df -T`  Displays the type of each filesystem
    3. `df -i` Displays inode usage instead of block usage.
     
- "Check Disk Space": Determine how much space is available on your filesystems.
- "Monitor Disk Usage": Keep track of disk usage to prevent full disks that can cause system issues.

  **du command**

  - `du` command estimates and displays the disk space used by indivisual files and directories. This will display the disk usage of the current directory and all its subdirectories.
      1. `du -h` Displays the output in a human-readable format.
      2. `du -ah` Displays disk usage for all files, not just directories
  - "Identify Large Files or Directories" Use du to find out which files or directories are consuming the most space.
  - "Disk Space Management" Helps in managing disk space by identifying and cleaning up large, unnecessary files.

## Search and find commnds( grep,awk,find,locate,sort,head,tail)

1. ****grep command****
     
  - `grep` command in Linux is a powerful tool used to search for a specific pattern of text within files or output. It's often used for filtering and searching through text files, log 
       files, and command output, widely used for searching and filtering text. Whether you're parsing log files, filtering command output, or searching within code, grep is an 
       essential command for efficient text processing.
      - `grep [options] pattern [file...]` **"pattern"** The string or regular expression you want to search for in the "file" The file(s) in which to search for the pattern.
      - `grep -i "pattern" file.txt` "i" Ignore case (search is case-insensitive).
      - `grep -o "pattern" file.txt`, **"-o"** Show only the matching part of the lines.
      - `grep -r "pattern" /path/to/directory/` **"r or -R"** Recursively search through directories.
      - `grep -v "pattern" file.txt`, **"v"** Invert the match (shows lines that do not match the pattern).
      - `grep -n "pattern" file.txt`, **"n"** Show line numbers along with matching lines.
      - `grep -l "pattern" *.txt`. **"l"** List only the names of files containing the matching lines.
      - `grep -c "pattern" file.txt` **"-c"** Count the number of matching lines.
      - `grep -w "pattern" file.txt`, **"w"** Match whole words only.

> Example
```
$ grep -i "error" /var/log/syslog, This searches for "error" regardless of case specific word,Search for a Word, Case Insensitive.
$ grep "error" *.log, Search for a Pattern in Multiple Files This searches for "error" in all .log files in the current directory.
$ grep "^pattern" file.txt, Search for lines starting with a pattern
$ grep "pattern$" file.txt, Search for lines ending with a pattern
$ grep "[a-z]" file.txt, Search for lines containing a specific range of characters:
```
 
2. ****awk command****    
- `awk` command in Linux is a powerful text-processing tool used for pattern scanning and processing. It's particularly useful for extracting and manipulating data from text files and 
        streams.
    - "Scanning files" The command can scan files line by line
    - "Pattern searching" It can search for a particular text or pattern in a file.
    - `awk 'pattern {action}' file`, "pattern"A condition to match, often based on regular expressions, "action" The operation to perform on lines matching the pattern. If no action is 
       specified, awk prints the matched lines by default."file" The file or input stream to process.
    - `awk -F: '{print $1}' /etc/passwd` Specifies the field separator,This prints the first field from each line of /etc/passwd, where fields are separated by ':'.
    -  `awk '{print $1, $3}' file.txt` Print Specific Columns, This prints the first and third fields from each line of file.txt, Fields are referenced by $1, $2, ..., $n, where $1 is 
                                      the first field, $2 is the second, and so on. $0 represents the entire line.
    - `awk -F, '{print $1, $3}' file.csv` Use a Different Field Separator, This specifies a comma as the field separator and prints the first and third columns from a CSV file.
    - `awk '/error/ {print $0}' /var/log/syslog`, Print Lines Matching a Pattern, This prints all lines containing the word "error" in the /var/log/syslog file.
      

3. ****find command****
  - `find` command in Linux is a powerful tool used for searching and locating files and directories within a directory hierarchy. It offers a wide range of options for specifying 
          criteria like name, size, modification time, permissions, and more.
       - `find [path] [options] [expression]` "path" The directory in which to start the search. If omitted, find starts in the current directory, options: Flags and options that modify 
                      the behavior of the search. expression: Conditions to match files or directories. This can include name patterns, size conditions, time conditions, and more.
       - `find /path/to/search -name "filename"` This searches for a file named filename in /path/to/search. The search is case-sensitive.

4. ****sort command****
   
 - `sort` command in Linux is used to sort lines of text files. It can sort data numerically, alphabetically, and in reverse order, among other options. The command is highly versatile 
         and can handle a wide range of sorting tasks
   - `sort [options] [file...]`, options: Flags that modify the behavior of the sort, file: The file(s) to sort. If no file is specified, sort reads from standard input.
   - `sort file.txt` , This sorts the lines in file.txt alphabetically in ascending order (A-Z).
   - `sort -n file.txt` This sorts the lines in file.txt numerically (1, 2, 10, 20, ...). This is useful when dealing with numbers
   - `sort -r file.txt` This sorts the lines in file.txt in reverse order (Z-A or descending numbers).
   - `sort -u file.txt` This sorts the lines and removes any duplicates, leaving only unique lines.
   - `sort -f file.txt` se-Insensitive, This sorts the lines without considering case differences (e.g., "apple" and "Apple" are treated the same).

5. ****head & tail commands****  
- The `head` and `tail` commands in Linux are used to display the beginning and the end of a file, respectively. These commands are useful for quickly viewing the first or last few 
  lines of a file without opening the entire file.

   **head command**
   
    - `head` command outputs the first part of files. By default, it displays the first 10 lines of each file, used to quickly view the beginning.
       - `head [options] [file...]` file: The file to display. If no file is specified, head reads from standard input
       - `head file.txt` This displays the first 10 lines of file.txt.
       - `head -n 20 file.txt` This displays the first 20 lines of file.txt.

   **tail command**
   
    - `tail`command outputs the last part of files.By default,it displays the last 10 lines of each file, used for monitoring logs or checking the most recent additions to a file.
      - `tail [options] [file...]` file: The file to display. If no file is specified, tail reads from standard input.
      - `tail file.txt` This displays the last 10 lines of file.txt.
      - `tail -n 15 file.txt` This displays the last 15 lines of file.txt.
      - `tail -n 20 -f /var/log/syslog` Combine -f with -n to View Specific Lines and Follow, This displays the last 20 lines of the file and continues to follow it

        

# **Topic list and link**
-------------------------
1. [User & Group Manegement](https://github.com/Alikhan9095/Linux-/blob/main/User%20%20management%20%26%20group%20management.md)
2.  [File System, Type and File permission](https://github.com/Alikhan9095/Linux-/blob/main/File%20System%20%26%20Type%20and%20File%20Permission.md)
3. [LVM](LVM.md)






  




          

    
          

  





     



    
     

     





     



   


  
      

                

   


     
  

       
     







  
  
  
