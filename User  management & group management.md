# User Management(useradd,userdel,passwd,usermod,chage.lastlog)
--------------------

## Useradd or adduser command
 - `sudo adduser username`'adduser' is a more user-friendly, higher-level command. It's actually a Perl script that makes use of useradd in 
     the background but simplifies the process for you.
 - `sudo useradd -m username` 'useradd' is a basic, lower-level command for adding users. It doesn't perform many automatic steps,must 
     manually configure certain things like creating the home directory.To create a home directory, you need to explicitly specify the -m 
     option.
 - `sudo useradd -m -d /path/to/home username` Add a user with a specific home directory
 - `sudo useradd -s /bin/bash username` Add a user with a shell
 - `sudo passwd username` Create a user with a password or reset the password for existing user
 - `sudo userdel username` Delete a user
 - `sudo userdel -r username` Delete a user and their home directory
 - Key Features of `adduser`
     - Creates a home directory by default.
     - Prompts for a password during the user creation process.
     - Automatically assigns a user group.
     - Interactive prompts for user information (such as Full Name, Room Number, etc.).
     - Sets default shell and other default settings automatically.
     - `sudo adduser username` Basic Syntax
     - `sudo adduser username groupname` Add user to a specific group
     - `sudo adduser --disabled-login username` Disable account upon creation
   



## usermod command (Modifying a User) 
 - `sudo usermod -d /new/home/directory username` Change user’s home directory
 - `sudo usermod -s /bin/bash username` Change user’s login shell
 - `sudo usermod -l newusername oldusername` Change username or rename user
 - `sudo usermod -L username` Lock a user account (prevents login)
 - `sudo usermod -U username` Unlock a user account














 


