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
** example..**
       
       $ ls -lh /home/user: Lists files in /home/user with detailed information and human-readable file sizes.
       $ ls -aR: Lists all files, including hidden ones, recursively in all subdirectories.
  
- `cat` command in Linux is used to concatenate and display the contents of files
  
