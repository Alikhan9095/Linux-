# **Linux basic commands**
----------------------------------------------------------

- `sudo` is a command that lets a user run commands with superuser or root privileges, allowing them to perform administrative tasks on the system.
- `sudo -i` or `su` cammand allow you to switch a normal user to a super user or root user.
- `pwd` cammand  to check current working directory
- `cd` cammand to use for chnage the directory.
     1. `cd` go to your home direcoty.
     2. `cd ..` go to back one directory
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
       
 ## **cat cammand**
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

## **Less cammand**

- `less` command in Linux is a powerful utility for viewing the contents of a file one screen at a time. It’s particularly useful for reading large files because it doesn't load the entire file into memory, making it faster and more efficient than cat or more for this purpose.
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

## **more cammand**

- `more` command in Linux is used to view the contents of a file one screen at a time, similar to less. However, more has fewer features and is less flexible than less. It's primarily used for viewing text files and allows basic navigation through the content.
   1. `more [filename]` Opens the specified file in the more viewer
   2. `more +[number] [filename]` Starts displaying the file from a specific line number.
   3. `more -d [filename]` Displays "[Press space to continue, 'q' to quit.]" at each prompt to make it more user-friendly.
   4. `more -c [filename]` Clears the screen before displaying each new page of text.
   5. `more -s [filename]` Squeezes multiple consecutive blank lines into a single blank line.

   > **Example**

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
     







  
  
  
