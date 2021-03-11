

# ................... Unix Interview Questions For Junior DevOps Engineer  ....................

## By  Mamun Rashid :: https://www.linkedin.com/in/mamunrashid/ :: Please connect with me.

### Last Updated: 2021.03.10

##

#### 1. So, what have you done with Unix? This sort of questions come up all the time!

#####   Answer: 

#####     While this seems easy, a prepared and practiced answer is significantly better than an impromptu one.

#####     Your answer would be uniqe to your experience, but, here are some possibilities.


######     a. Installed Unix on VMs
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

####    18. 3 steps of TCP handshake?

    19. TCP vs UDP. This comes up all the time?

    20. Give me an example of each OSI Layer (not unix question, but related)

     21. What is a LAMP Stack?

    22. What processes are running on your VM?

     23. What is parent process vs child process?

   24. What is sudo?

   25. How do you terminate a process? What is still does not die?


   26. grep -r

    27. find

    28. du

    29. df -h

    30. ls -R

    31. What is regular expression?

    32. Where does Chef or Puppet or Ansible fit in your stack of OS and Application

    33. how do you get a list of port listening on a server

    34. How do you test if another server is listening on port 443?


