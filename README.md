# **Linux basic commands**
----------------------------------------------------------

- `sudo` is a command that lets a user run commands with superuser or root privileges, allowing them to perform administrative tasks on the system.
- `sudo -i` or `su` cammand allow you to switch a normal user to a super user or root user.
- `pwd` cammand  to check current working directory
- `cd` cammand to use for chnage the directory.
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
       
 ## cat cammand
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

## Less cammand

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

## more cammand

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


     ## touch cammand (make a empty file)

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

## mkdir cammand (make a directory)

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


## CP cammand

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


## ****





     



   


  
      

                

   


     
  

       
     







  
  
  
