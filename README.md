# Linux-and-Command-Line-Mastery

## Linux File System Navigation

This section explores the use of navigaion commands in Linux File systems.

Activities include the folowing:

1 Print the current working Directory using 'pwd'

2 List all files including hidden ones with ls -la


 ![alt text](<Images/class project 1.PNG>)

3 Change directory into /etc and list its contents

   cd /etc

   ls -la

   ![alt text](<Images/class project 3.PNG>)


4  Navigate back to the home directory using relative paths

   cd ~

5  Use 'cd -' to toggle between the previous and current directories

6  Display absolute path of the 'bash' binary using 'whereis bash'

  
![alt text](<Images/class project 4.PNG>)

![alt text](<Images/class project 6.PNG>)

7  Use 'find / -type f -name "passwd"' to locate a file in the system

![alt text](<Images/class project 7.PNG>)


8  Print directory tree structure using 'tree /home/labuser' (after installing tree)


![alt text](<Images/class project 8.PNG>)
![alt text](<Images/class project 9.PNG>)

9  Use 'du -sh * 'to summarize disk usage in the current directory
  
![alt text](<Images/class project 11.PNG>)

10  Use 'file' command to check type of '/etc/hosts'

11  Count number of directories in '/etc' using 'ls -l | grep ^d | wc -l'

12  Verify symbolic link path of '/bin/sh' using 'ls -l /bin/sh'

![alt text](<Images/class project 13.PNG>)


## Linux Program Management

1  Update system repositories '

    sudo apt update


   ![alt text](<Images/class project 14.PNG>)

2  Install 'tree', 'nano', and 'nginx'

    sudo apt install -y


   ![alt text](<Images/class project 15.PNG>)


   ![alt text](<Images/class project 16.PNG>)



3  Check versions of installed programs
    
    tree --version

    nginx -v

   ![alt text](<Images/class project 18.PNG>)
   ![alt text](<Images/class project 19.PNG>)


4  Verify installation paths using

    which tree

    whereis nginx

   ![alt text](<Images/class project 20.PNG>)


5  Create and edit a sample file

    nano test.txt


   ![alt text](<Images/class project 21.PNG>)

   ![alt text](<Images/class project 22.PNG>)



6  Display directory structure using

    tree /etc/nginx


   ![alt text](<Images/class project 23.PNG>)
   ![alt text](<Images/class project 24.PNG>)


7  Start nginx service

    sudo systemctl start nginx

8  Enable nginx to start at boot

    sudo systemctl enable nginx


   ![alt text](<Images/class project 25.PNG>) 


9  Check nginx status 

    sudo systemctl status nginx


   ![alt text](<Images/class project 26.PNG>)


10  Verify if nginx is listening on port 80

    sudo ss -tuln | grep 80


   ![alt text](<Images/class project 27.PNG>) 


11  Uninstall and reinstall one package

    sudo apt remove tree

    sudo apt install tree


   ![alt text](<Images/class project 28.PNG>)
   ![alt text](<Images/class project 29.PNG>)

   ![alt text](<Images/class project 30.PNG>)



12  Search for available versions of a package

    apt-cache search nano


   ![alt text](<Images/class project 31.PNG>)


## Linx File Management


1  Create a directory 'testdir'

    mkdir testdir

2  Create an empty file

    touch example.txt

3  Write content into the file

    echo "Hello Linux" > example.txt

4  append new content into the file

    echo "Learning DevOps" >> example.txt

5  View the file contents 

    cat example.txt

6  Create a nested directory using

    mkdir -p logs/archive

7   Copy a file to another location

    cp example.txt /logs

8    Rename the file with

    mv example.txt example_renamed.txt

9   Remove a file using

    rm example_renamed.txt

10  Remove an empty directory with

    rmdir emptydir


   ![alt text](<Images/class project 32.PNG>)


11  Use 'head' and 'tail' to preview top/bottom lines of a file


   ![alt text](<Images/class project 33.PNG>)


12  To check metadata (permissions, size, etc)


    stat example.txt


13  Count number of lines in the file using

    wc -l example.txt

14  Create multiple files in one command:

    touch file{1..5}.log

15  Display human readable file sizes:

    ls -lh


   ![alt text](<Images/class project 35.PNG>)



## Linux File Ownership & Permissions


1  View current file permissions:

    ls -l example.txt

2   Change permissions to 644:

    chmod 644 example.txt

3  Add execute permission using symbolic mode:

    chmod u+x example.txt

4  Remove group write permission:

    chmod g-w example.txt

5   Change file owner to current user:

    sudo chown labuser example.txt

6   Change file group using:

    sudo chgrp labuser example.txt

7   Set recursive permissions on a directory:

    chmod -R 755 testdir

8   Verify permissions with:

    stat example.txt


   ![alt text](<Images/class project 37.PNG>)


9   Set default permissions using umask and test file creation:

    umask 022

    touch testfile
    ls -l testfile

   ![alt text](<Images/class project 38.PNG>)

   ![alt text](<Images/class project 39.PNG>)


10  Create a shared directory for group collaboration

    mkdir sharedir
    sudo groupadd groupname
    chgrp groupname sharedir
    chmod 2775


   ![alt text](<Images/class project 40.PNG>)
