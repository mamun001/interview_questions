

# .......... Unix Interview Questions For Junior DevOps Engineer  .........

## By  Mamun Rashid :: https://www.linkedin.com/in/mamunrashid/ :: Please connect with me.

### Last Updated: 2021.03.10

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



