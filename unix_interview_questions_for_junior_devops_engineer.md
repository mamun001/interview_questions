

# .......... Unix Interview Questions For Junior DevOps Engineer  .........

## By  Mamun Rashid :: https://www.linkedin.com/in/mamunrashid/ :: Please connect with me.

### Last Updated: 2021.03.12

##

#### 1. So, what have you done with Unix? This sort of questions come up all the time!

#####   Answer: 

#####     While this seems easy, a prepared and practiced answer is significantly better than an impromptu one.

#####     Your answer would be uniqe to your experience, but, here are some possibilities.

           a. Installed Unix on VMs
           b. Searched through logs for issues on VMs
           c. Installed packages 
           d. Configured applications

##

#### 2. What are some of your favorite tools on Unix? This comes up all the time.

#####   Your answer would be uniqe to your experience, but, here are some possibilities.

           a. grep
           b. find
           c. bash
           d. awk
           e. sed
           f. netstat
           g. nc
           h. ping
 
##

#### 3. Which do you prefer: vi or nano ? and why?

        Your answer would vary based on your taste and experience.

        Some people like vi , based it is avaiable on All unix flavors and versions (even really old ones). Older professionals like it because they have been using it for years. Because 
          of that, they can edit very vety fast in vi.

        Some people like nano, because it does not require any "commands". It is a very simple text editor with many great features. 

##

#### 4. What is your favorite flavor of Unix?  This comes up all the time.

        Your answer would vary based on your taste and experience.  But, be sure to know what you like and don't hesitate to answer.
          a. Ubuntu
          b. Centos
          c. Debian
          d. Redhat

        People tend to like whatever they have used most. Now-a-days, you can do almost everything on any flavor. So, it almost does not matter.


###  5. What is the PID of init?

        Answer: 
          init is THE VERY first process that runs on Unix. It is the "parent" of all the other processes directly or indirectly. That is the key thing to understand.
          PID is 1.
      

### 6. What is the UID of root? This comes up all the time.

       Answer: Each user in Unix has a UID. "root" is the first user (automatically created) and it is THE SUPERUSER. This user has power over everything on any Unix Machine.
               UID of root is 0.

##

#### 7. Describe how a Unix Machine boots up. This comes up all the time, too.

      Answer: 
        This page has detailed explanation: https://www.thegeekstuff.com/2011/02/linux-boot-process/
        You only have to know the major steps. e.g.

        BIOS --> MBR --> GRUB --> KERNEL --> INIT --> RUN LEVEL 0 Through 6.

##

#### 8. Difference between hard link and soft link?

     Answer:
       This is kind of an advanced question. First of all, a "link" is pointer from one place in the File System to another folder or file somewhere else.
       You create a link, when , for whatever reason, you don't want to move the original file. So, you just point to it, so that that file can be gotten to from both places.

       A hard link can only be made to a file or folder in the SAME File System.
       A soft link go across File Systems.

       Also, you "delete" a hard link, the original file is also deleted. 

##

#### 9. What is the port for MySQL?

        Ans: 3306

##

#### 10. What is thge port for PostgreSQL?

         Ans: 5432

##

#### 11. What command can you use to see all the network connections on Unix VM?

     Answer:
       netstat
       e.g. netstat -a

##

#### 12. What command can you use to see the "Routing Table" on your Unix VM?

        Answer: netstat -nr

##

#### 13. What command can you use to see what path a packet takes from your Unix VM to another host?

        Answer: traceroute

##

#### 14. You have 2 servers A and B. You suspect that network communication is broken between them. What should be your first step for troubleshooting?

         Answer: ping A from B or B from A

##

#### 15. What is inode?

         Answer: Files and directories are represented internally with "inodes". Unix Kernel allows a maximum of them. You can run out of inodes before you run out of disk space.

##

#### 14. What is a thread and why do we need it?

         Answer: 
           Way back when all processes were single-threaded. What this means is that a process would run "one thing" at a time and until the CPU was done with computation, it would just have to wait for next instruction (task). This made "processing" slow. But later, machines came with multiple CPUs (sometimes called "cores"). Then, it was possible for processes to execute multiple tasks all at once. This is called MULTI-THREADING. This made parallel processing possible. This made processing much faster.

           Although, this is NOT a Unix-only concept, it is an important concept to know.

           By the way, there is a command called "strace" that lets your track all the threads on a SINGLE process running on your Unix VM.

## 

#### 15. How do you troubleshoot a network problem (e.g. your host cannot reach mysql server)? This comes up all the time!

         Answer:
           This is where understanding the OSI layers is so important.
           Let's say your VM is called A, and the mysql server is called B.

           OSI Layer 1-3:  Can you ping B from A? If not, you have to troubleshoot Layers 1-3 (e.g. physical cable, routing etc.)
           OSI Layer 4: Can you telnet (or nc) to port 3306 of server B? If not, check that server B has mysql running and is allowing port 3306 to be open.
           OSI Layer 4: Firewall: Is there any firewall rule blocking your traffic?

##

#### 16. What is quick way to see what busy your Unix Machine is?

         Answer:
           There are a few commands that can help you with this.
           For example: w, uptime, top

#### 17. Your machine is slow. How to troubleshoot this? This comes up all the time!

     Answer:
       Generally , there are 4 major factors that can make a server slow:
        a. CPU usage
        b. Memory (RAM) usage
        c. DISK I/O too heavy
        d. Some kind of network hit or DDOS attack forcing overload of one or more of the 3 factors.

      For CPU, you can use "top" command.
      For Memory, you can also use "top" command.
      For Disk I/O, you can use vmstat or iostat commands
      For DDOS atatck, you can use "netstat" command to see how many connections are hitting your Unix VM.

##

####  18. 3 steps of TCP handshake?

      Answer:
        1. Server A reaches out to Server B
        2. Server B says "I hear you"
        3. Server A says "I alos hear you"
             Then the actual communication begins.

##

#### 19. What is the difference between TCP vs UDP? This comes up all the time.

     Answer: 
       TCP is connection-based
       UDP is connection-less.
       What this means is that:
        With TCP, a connection (3-way handshake) is established first before sending real data.
        With UDP, server A sends that data to server B anyway. It does not ensure that B is actually receiving anything. Its like throwing a package out the window hoping the person gets it, but does not see if the person actually got it.

## 

#### 20. Give me an example of each OSI Layer (not a Unix question, but related and it helps you answer other questions better)

     Answer:
       Layer 1: A Physical Cable between two server OR between a server and a Switch
       Layer 2: DHCP (How a device gets a IP Address automatically)
       Layer 3: Routing from Server A to Server B. 
       Layer 4: Firewall Rules incorporating "ports"
       Layer 5: RPC (Remote Procedure Call) + All mechanisms for opening , closing, and keeping track of communication of "sessions" between 2 servers.
                 A real life comparison would be: If two people are talking to two other people in the same room. Whatever is happening in our brains to keep track, that's session layer.
       Layer 6: This is mostly about represending data. For example you are watching a video on Youtube. Whatever formating and de-formating of data is happening: is Layer 6.
       Layer 7: Layer closest to the User. It get data from user and gives it back to the user. For example, if you are watching a Youtube video, Layer 7 is what is taking your search query and playing back the video to you. 

##

#### 21. What is a LAMP Stack?

     Answer:
       PHP
       MySQL
       Apache
       Linux

       A few years ago, this was very common way to implement an application. Apache web server ran on Linux Machines. It would store its data in a MYSQL database. PHP was the language in which he front-end web pages were written. Because, each of these were open-source (free), it became very common. This is called the LAMP (L + A + M + P) stack.

##

#### 22. How can you tell what processes are running on your VM?

     Answer: ps -elf or ps -aux (depending on architecture). First one is , by far, more common these days.  

##

#### 23. What is parent process vs child process?

     Answer: 
       Often one process will spawn other processes. The new processes are child processes of the first one (parent). The way you know which is which is: your run ps -elf and you will see a column for PID and another for PPID. PPID is the process ID of the parent process that started this one.
       For example, if the init process spawns a process called FOO, FOO will have a PPID of 1.

##

### 24. What is sudo?

    Answer: 
      A regular user on a Unix VM has limited powers. But , sometime, a regular user needs power to do things that only "root" can do. In that case, there is a way to do that.
      For example:
       1. You are logged in as foo.
       2. You want to run "init 6" (same as reboot)
       3. If you run, init 6, it will fail because foo user does not have permission.
       4. So, instead , you run "sudo init 6". That will work as long as foo user is part of suoders group.

##

#### 25. How do you terminate a process? What is still does not die?

     Answer:
       kill PID
       if that does not kill it, you run: kill -9 PID   (PID of the process you want to kill)

##

#### 26. How do you look for a string "foo" in all the files in the current directory and all the directories below it (recursively)?

     Answer: 
       Use the -r command with grep.
       For example:   grep -r foo *

##

#### 27. How do you find a file named foo.txt in current directory and all the directories below it?

         Answer:
           find . -name foo.txt

#### 28. Which command will show which sub-directories and files are taking up the most space from current directory and below?

     Answer:
       du -sk *
       (Here k is kilobytes)

##

#### 29. Which command will show you the usage of ALL volumes on your Unix VM in human readable format?

     Answer: 
       df -h

#### 30. How do you show hidden files?

    Answer:
      add -a to ls command
      Example: ls -a  OR ls -la

##

#### 31. What is a regular expression?

     Answer:
       On majority of Unix commands your argument values can be formatted in such a way that it can match precisely what you are looking for.
       For example: You can do "ls" or you can do "ls a*". In the second case, you ONLY want files that starts with "a".
       Turns out that there are many more than just "*. For example you can use ^ to match beginning of lines/names. You can use [] to match a range.
       Another example:
         ls [a-c]*
         This one will only show you files or directories that start with a,b, or c.
       This is called "Regular Expression". It is a very topic and extremely powerful and can be used in many cases.

##

#### 32. Where does Chef or Puppet or Ansible fit in your stack of OS and Application?

     Answer:
         Chef , Puppet and Ansible are examples of "Configuration Management". These tools make anything that goes on top of the Unix Operating Systems.
         For example, if you are building a web server, you will want to install Apache Web Server and give it come configuration. You can automate those with Chef/Puppet/Ansible.
         This way, you can build the server a thousand times and each one will be built the exact same way. This concept, by the way, is called "immutable".
     
##

#### 33. How do you get a list of port listening on your Unix Server?

     Answer:
       netstat -an | grep LISTEN

##

#### 34. How do you test if another server  (B) is listening on port 443 when you are logged in on Server A?

     Answer:
       telnet serverBs_name_or_IP 443  OR
       nc serverBs_name_or_IP 443

##

#### 35. How do you figure out the IP address of your Unix VM?

     Answer:
       ifconfig -a

#### 36. Which command can you run to get list of commands you have ran recently?

     Answer: 
       history
##

#### 37. Which command can you run to login to Unix server B from Unix server A ?

     Answer:
       ssh IP_or_hostname_of_server_B

##

#### 38. Which command can you run to figure out how long your Unix has been up?

     Answer:
       uptime

##

#### 39. Which init level reboots your Unix VM?

     Answer: 
       init 6

##

#### 40. Which init level powers down your Unix VM?

    Answer:
      init 0

##

#### 41. You are writing a bash script (a text file). Which directive on the first line of the file tells the kernel that this is a bash script?

    Answer:
      #!/bin/sh

##

#### 42. Which fancy short cut executes the very last command you ran?

     Answer:
       !!
##

#### 43. You just ran "history". In the list you , you see a very long command in line number 43. How can you run the same command again without typing it again?

     Answer:
       !43

##

#### 44. You have a text file named foo. How can you see the content of that text file without vi or nano.

     Answer:
       cat foo    OR
       more foo   OR
       less foo

##

#### 45. How can you see the first 10 lines of a file named foo?

    Answer: 
      head foo

##

#### 46. How can you see the last 20 lines of a file named foo?

     Answer:
       tail -10 foo

##

#### 47. Unix has a concept of a "pipe".  What is a pipe?

     Answer:
       You can run a command and use the output of that command as input of second command. This is called a pipe.
       For example:   cat foo | grep john 

##

#### 48. You just installed a new binary called runfoo. But, when you run "runfoo", you get "Command Not Found". What could be the reason?

     Answer: You have not added the location where runfoo is in your PATH variable.

##

#### 49. What is a quick way to print out all your ENVIRONMENT variables on your screen?

     Answer: env

##

#### 50. You have command named kubectl. You run this command all the time and you are tired of typing "kubectl". You would rather type just "k" to run the same command. How can you achieve this?

     Answer: 
       alias k=kubectl

##

#### 51. Which command can you run to change permission of a file?

     Answer:
       chmod
       For example: chmod 700 foo   (makes foo readable, writable and executable only by owner)
##

#### 52. Which command can your run to change the ownership of a file?

     Answer:
       chown
       For example: chown john file1

##

#### 53. You have an environment variable called HOME. How can you see what HOME's value is?

     Answer:
       echo $HOME

##

#### 54. Which command shows you which users are logged in on your Unix VM?

     Answer: 
       who

##

#### 55. If a file has 644 permissions, who can execute this file?

     Answer:
       No one. 644 translates to rw-r--r--.  That means no one can execute this file, since there is no "x" permission.

##

#### 56. If a a file has 744 permissions, who can execute this file?

       Answer:
         Only the owner can. 744 translates to: rwxr--r--  . Owner has "x" permission, so he/she can execute this file.

##

#### 57. Which command can you use to copy a file?
       
         Answer: 
           cp
           For example: cp foo bar

##

#### 58. Which command can you use to rename a file?

         Answer:
           mv
           For example: mv foo bar

##

#### 59. Which option of the cp command can you use to copy over over all the permissions along with the file(s)?

         Answer:
           cp -p

##

#### 60. You have two different text files with some minor differences between them. File names are foo and bar. Which command will show you the differences?

         Answer:
           diff foo bar

##

#### 61. Which command will sort your text file (i.e. lines within that file)? File name is foo.

         Answer:
           sort foo

##

#### 62. You have a text file (foo) that has many repeat lines. How do you get rid of all the duplicates?

         Answer:
           uniq foo

##

#### 63. You just started a process from your terminal. Process started and it is not giving you any output on the screen. You don't what it is doing. You want to kill that process. Which keystrokes will kill that process?

     Answer:
       Control c

##

#### 64. You just started a process from your terminal. Process started and it is not giving you any output on the screen. You don't what it is doing. You do not want to kill that process. You just want to pause the process , so that you can get back your terminal and you can restart or kill that process later if you need to. Which key-strokes can you use to pause that process?

     Answer: 
       Control z

## 

#### 65. Let's say your pwd is /home/foo. There is a file called bar in /home. What is the relative path to that file?

    Answer:
      ../bar
      e.g. ls -l ../bar  OR
           cat ../bar

##

#### 66. Let's say you have a file on your VM and you don't know what kind of file it is (text , binary, something else) . Which command tells you what kind of file it is? File name is foo.

     Answer: 
       file foo.

##

#### 67. Very broadly speaking, which directory holds "configurations" ?

     Answer: 
       /etc

##

### 68. Very broadly speaking, which directory holds "logs" ?

    Answer:
      /var/logs

##

#### 69. Can you have for loops and while loops in Bash scripts?

     Answer:
       Yes (and a lot more!)

##

#### 70. Majority of Unix commands have a -v option. What is that for?

     Answer:
       Sometimes it if for "verbose", meaning it spits out for information that normal (for debugging purposes).
       Other times, it is to display version of the software.

##

#### 71. Which option of grep makes the search case-insensitive?

     Answer:
       grep -i

##

#### 72. Which Unix command counts lines, words, and characters in a file?

     Answer:
       wc

##

#### 73. This is an advanced question. But, it is so handy that even junior people should be aware of it. There is command in Unix that maps files (in use) , ports with processes. This helps tremendosuly in troubleshooting. Which command does this?

     Answer:
       lsof

##

#### 74. Let's that an application is constantly writing logs to /var/logs/foo file. You want to watch the logs scroll as they are written. Which command can you use?

     Answer:
       tail -f /var/logs/foo

##

#### 75. Everything you edit a file, it's modification time gets changed. Sometimes, you have a need to change the modification time of a file without actually doing any edits. How do you do that? File name is foo.

     Answer:
       touch foo

##

#### 76. You have been working on a Unix VM terminal. You are seeing some weird permission issues that you weren't expecting. You wonder which user system thinks you are. Who command shows you who you are on the system?

     Answer:
       whoami

##

#### 77. Which command shows your UID and GIDs (Group IDs)?

     Answer:
       id

##

#### 78. Which command in Unix let's you take out only certain number characters or words from each line of a text file.
         For example foo file looks like this:
         a b c d
         e f g h
         i j k l

         This command will let you take (for example) just b f and j (i.e. 2nd word from each line).

         Which command does that?

         Answer:
           cut 

##

#### 79. There are two very famous string manipulation commands in Unix. So much so that there is whole book just for these two commands. Which are these two commands?

     Answer:
       sed and awk

##

#### 80. What is the difference between these two cmmands?
         cat foo
         cat foo &

         Answer:
           1st command happens in the foreground and so you see the output on screen.
           2nd command happens in the background and so you don't see the output on screen.

##

#### 81. What is an exit code?

         Answer: Each process puts out a code before exiting that tells if it was successful or not. If it was not successful, it tries to give you a code that points to a cause.
                 This is called the "exit code"

## 

#### 82. What does exit code 0 mean?

         Answer:
           Process was successful.

##

#### 83. What is the shortcut to cd to $HOME?

     Answer:
       cd ~     (~ means Home Dir)

##

#### 84.

   

 
