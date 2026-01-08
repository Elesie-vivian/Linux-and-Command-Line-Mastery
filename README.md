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


## Linux File Management


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


11  Assign sticky bit to /tmp/shared and test deletion rights

    First create the path

    sudo mkdir /tmp/shared

    Assign sticky bit:

    sudo chmod 1777 /tmp/shared

    To verify that sticky bit is set:

    ls -ld /tmp/shared

   ![alt text](<Images/class project 44.PNG>)

   To test deletion righs:

   Create test users

   sudo useradd User1
   sudo useradd User2

   ![alt text](<Images/class project 44b.PNG>)


   As User1 create a File

   su - User1

   touch /tmp/shared/User1File
   ls -l /tmp/shared


   ![alt text](<Images/class project 45b.PNG>)


   Switch to User2 and attempt to delete User1's file

   su - User2
   rm /tmp/shared/User1File

   ![alt text](<Images/class project 45c.PNG>)


   As the owner, delete the file

   su - User1
   rm /tmp/shared/User1File

   ![alt text](<Images/class project 45d.PNG>)


12  Assign SGID bit to /usr/local/scripts and create a file inside it

- First, we create the path with:

    sudo mkdir -p /usr/local/scripts

- Assign SGID bit:

    sudo chmod 2755 /usr/local/scripts

- Verify the SGID bit:

    ls -ld /usr/local/scripts


    ![alt text](<Images/class project 46.PNG>)


- Create a file inside the directory:

    touch /usr/local/scripts/testfile.sh


- To verify group inheritance and confirm that the SGID bit worked as expected, 

  we check the group ownership of the newly created file using:

    ls -l /usr/local/scripts/testfile.sh


    ![alt text](<Images/class project 47.PNG>)
   


13  Change file ownership to another user and verify


   ![alt text](<Images/class project 48.PNG>)

14  Compare numeric v symbolic permissions

    Both are two different methods of setting permissions (read, write, & execute permissons), for the user,

    group and others.

    Numeric                                                            Symbolic

                                                                                   
-  Each permission type has a numerical value           Uses letters and symbols to specify changes. 
                                                   
    r (read)= 4                                         The syntax follows this pattern:
    w (write)= 2                                        
    x (execute)= 1                                      chmod [who][operator][permissions]
    No permissions = 0                             

-   The digits are added together to specify the        

    total permissions for each category.


15  Exploring permission inheritance in sudirectories:

    This is where permissions assigned to a parent folder authomatically flow down to its subfolders and 
    
    files, thereby ensuring consistent acccess control policy throughout a file hierarchy by default.


## Linux input/output redirection & commands chaining


1  Redirect command output to a file

    ls > list.txt

2   Append new output to same file

    ls /etc >> list.txt

3   Redirect standard error:

    ls /noexist 2> errors.txt

4   Combine stout and stderr using:

    ls /etc /noexist &> all_output.txt

5   Filter file contents using:

    grep "Linux" example.txt

6   Pipe multiple commands:

    cat example.txt | grep Linux | wc -l


7   Use 'sort' and 'uniq' to list unique words

*   First, we create a file:

    touch myfile.txt

*   Input text into the file:

    echo "apple banana apple orange banana"

*   List the contents of the file one after another:

    echo "apple banana apple orange banana" | grep -oE '\w+'

*   Use 'sort' and uniq to list unique words

    sort myfile.txt | uniq

    ![alt text](<Images/class project 49.PNG>)


8   Use 'cut' to extract specific columns from /etc/passwd:

*    To extract only the username(field1):

    cut -d ':' -f 1 /etc/passwd


   ![alt text](<Images/class project 50.PNG>)


*   To extract username and home directories(fields 1 and 6):

    cut -d ':' -f 1,6 /etc/passwd


    ![alt text](<Images/class project 51.PNG>)


9   Use 'awk' '{print $1}' to print first column of /etc/passwd:

    awk -F: '{print $1}' /etc/passwd

   ![alt text](<Images/class project 52.PNG>)


10  Use sed to replace a word in a file:

    sed -i 's/old_word/new_word/g' filename.txt

11   Count occurences of a keyword

    grep -o "root" /etc/passwd | wc -l
    

12 Redirect input from a file:

    cat < example .txt

13  Use pipelines to combine multiple utilities:

    This involves; chaining sequential tasks
    nesting pipelines as subtasks
    using specialized merging tools e.g;
    ls
    grep
    sort

    ls -l | grep ".txt" | wc -l

14   Test output chaining with logical operators ('||','&&')


15  Measure execution time with:

    'time cat example.txt > /dev/null


  ![alt text](<Images/class project 53.PNG>)  



## Linux Process Management

**Develop the ability to monitor and control system processes and resources**


1   List all processes with command:

    ps aux

   ![alt text](<Images/class project 54.PNG>)


2   Display top CPU commanding processes:

    top

   ![alt text](<Images/class project 55.PNG>)


3   Find PID of Nginx:

    ps aux | grep nginx

   ![alt text](<Images/class project 56.PNG>)


4   Kill a process safely:

    kill <pid>


5   Use 'killall nginx' to stop multiple instances

6    Restart nginx:

    sudo systemctl restart nginx

   ![alt text](<Images/class project 57.PNG>)


