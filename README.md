# **Linux basic commands**
----------------------------------------------------------

- `sudo` is a command that lets a user run commands with superuser or root privileges, allowing them to perform administrative tasks on the system.
- `sudo -i` or `su` cammand allow you to switch a normal user to a super user or root user.
- `pwd` cammand  to check current working directory
- `cd` cammand to use for chnage the directory, # `cd` go to your home direcoty, #`cd ..` go to back one directory
-  `main 'command name'` to use for manual or see about the cammnad such as flag, operator use and more details
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
       
  
- `cat` command in Linux is used to concatenate and display the contents of files.
     1. `cat filename` Displays the contents of the specified file.
     2.  `cat > filename` Creates a new file (or overwrites an existing file) and allows you to input text into it. Press Ctrl + D to save and exit.
     3.   `cat >> filename` Appends text to an existing file. Press Ctrl + D to save and exit.
     4.   `cat file1 file2 > newfile`  the contents of file1 and file2 and writes them to newfile created.
     5.   `cat -n filename` Displays the contents of the file with line numbers.
     6.   `cat -b filename` Similar to -n, but only numbers non-blank lines.
     7.   `cat [filename] | grep [pattern` Searches for a pattern in the file and displays matching lines.

> Example..

   $ cat file : View the contents of a file
   $ cat > file : eate a new file
   $ cat part1.txt part2.txt > combined.txt : create a new file and copy multiple files's contents in new file
   $ cat >> log.txt : Append(write in a file without using editor) to an existing file 
   $ cat /etc/passwd | grep username : Displays the contents of the /etc/passwd file, which contains user account information.
  
  
