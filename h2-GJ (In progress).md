# Introduction

In assignment x (Karvinen 2024)  I'm supposed to summarize a post by Tero karvinen. This post is called "Command Line Basics Revisited" and it can be read [here](https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited). The post can be summarized with a couple of bullet points. The other assigment is divided into subassignments. These tasks are to be done inside a Linux environment. I used a virtual machine that has Debian on it.


## Command Line Basics Revisited summarized

- CLI (Command Line Interface) in Linux has been around for for a long time (Karvinen 2020).
- A "$" means that a normal user is using the cli (Karvinen 2020). Tero (2020) also adds that the "#" transforms the rest of the line into a comment. I'll add here that if there is a "#" instead of a "$", it means that the cli is being operated by root. This can be seen when a user switches into a root user.
- Tero (2020) explains that in Linux cli a user is always in a directory. Important commands when moving around include ```pwd``` ```ls``` ```cd``` ```less``` (Karvinen 2020).
- pwd (Print Working Directory) tells the user the current directory they are in. ls (list) lists the files and directories inside the current directory. cd (Change Directory) can be used to traverse between directories. less can be used to read the contents of a file without being able to make changes. Another command for reading file contents is cat (concatenate) which is good for files with contents that aren't too large. The less command is very useful when reading long outputs of another command. For example this ```ls | less``` command would put the output of the ls command into less (Karvinen 2020). 
- With text editors like nano or pico a user can make and modify files (Karvinen 2020). Important commands when working with files include ```mkdir``` ```mv``` ```cp``` ```rmdir``` ```rm``` (Karvinen 2020).
- mkdir creates a new directory. For example ```mkdir dire``` creates a directory named dire inside the working directory. The mv command can be used to move files or directories. It can also be used to rename files or directories. With the cp command a user can copy files or directories. ```cp -r``` copies the directory with everything inside it. The rmdir command can be used to remove an empty directory. Files can be removed with the rm command. The rm command can also be used to remove a directory with contents by using -r like this ```rm -r [target]```. (Karvinen 2020.)
- With ssh a user can remotely and securely command a target device. Tero (2020) explains that to open a remote connection with ssh a user needs to write a command like this ```ssh [username]@[server]```. To exit the session a user needs to type ```exit```. To copy a directory to the remote machine, one would need to use a command like this ```scp -r [directory] [username]@[server]:[destination]```. To be noted that the user has to be out of the remote session before running this command since it runs natively. (Karvinen 2020.)
- With the man which is short for manual a user can find useful information on commands. For example a command ```man ls```opens the manual page for the command ls. ```--help``` or ```-h``` can also be useful. They open a more compact version of useful information on commands. For example ```ls --help``` and ```wget -h```. (Karvinen 2020.)
-  To find the history of typed commands in a session, one would simply use the ```history``` command (Karvinen 2020).
-  Tero (2020) recommends the use of the tab key on a keyboard. With the tab a user can fill needed information without manually writing it. This prevents unnecessary typos. When pressing the tab key twice it shows the possible results. (Karvinen 2020.)
-   Tero (2020) states that the important directories in a Linux system include ```/``` ```/home/``` ```/home/[username]/``` ```/etc/``` ```/media/``` ```/var/log/```. Root directory is / and "everything is under /". /home/ home directories are here. A home directory for a certain user can be found at /home/[username]. "All system wide settings" can be found at /etc/. Removable media can be found at /media/. System logs can be found at /var/log/. (Karvinen 2020.)
-   It is important to practice the principle of least privilege. When higher privileges are required the user can run commands with sudo. (Karvinen 2020.)
-   Package managers are used to manage packages in Linux systems. ```sudo apt-get update``` updates the list of available packages. ```sudo apt-get install``` is used to install software. To remove a software and its settings a user can use the command ```sudo apt-get purge```. (Karvinen 2020.)

## Report

### Essential information

I opened the system information application by searching "sysinfo" in the windows search bar. 

- Lenovo Thinkpad T14 Gen 2a
- AMD Ryzen 3 PRO 5450U with Radeon Graphics, 2600 Mhz, 4 cores and 8 logical processors
- 16 GB RAM
- Windows 11 Pro
- x64-based PC
- SSD with 396 GB free space
- It was January 25, 2024. I was at home in Vaasa.
- I used a wireless connection which was great.


### Installing micro

At 11:25 AM I started to work on this assignment. First I opened the Virtualbox application. When it opened I clicked on start.

![start](Screenshots/2/start.png)

In under a minute I was at the login screen. I logged in. I opened the terminal and ran ```sudo apt update``` and ```sudo apt upgrade```.

![update](Screenshots/2/update.png)

Then I ran ```sudo apt install micro``` to install the micro text editor.

![micro](Screenshots/2/micro.png)

I tested that the app works. Ctrl + S to save and Ctrl + Q to exit.

![microtesti](Screenshots/2/microtesti.png)

![toimii](Screenshots/2/toimii.png)

Used cat to read the contents.

![cattesti](Screenshots/2/cattesti.png)

Micro was succesfully installed and it was 11:36 AM.

### Specs

Here I was supposed to list hardware information with lshw. I started doing this at 11:43 AM. First I checked if lshw was already installed. For practice I first used the ```apt list --installed | less``` to pipe the output into less. Then I used a faster method with ```apt list --installed | grep lshw```.

![aptlist](Screenshots/2/aptlist.png)

Neither method found lshw installed so I installed it with a command ```sudo apt install -y lshw```.

![lshwinstall](Screenshots/2/lshwinstall.png)

This time I used the ```-y``` to automatically confirm the intallation. Then I used the command from the post by Tero (2020)```sudo lshw -short -sanitize``` and to fit everything into a screen capture I used the Ctrl + - to make to font smaller.

![lshw](Screenshots/2/lshw.png)

The man page for lshw states that the -short and -sanitize options make the output shorter and without possible sensitive information. The output shows that the system was virtualbox, there were 8064MiB of ram and the processor was AMD Ryzen 3 PRO 5450U with Radeon Graphics. Other interesting information were 54GB VBOX HARDDISK which was the storage, different input devices and network adapter. In conclusion this command shows essential hardware information in a shorter form and without sensitive information. It uses classes to group. These classes were system, bus, memory, processor, bridge, input, storage, disk, display, network, multimedia and volume. It was 11:55 AM and I was done with this.

### Three programs

At 12:30 PM I started working on this assignment. The programs I decided to install were htop, ncdu and cowsay. I had to search for interesting programs that I haven't tried and wanted to test. I found htop and ncdu from a Reddit post (2023). To install all three at the same time I ran ```sudo apt install htop ncdu cowsay```.

![install...](Screenshots/2/install....png)

It only took a couple of seconds. I started with htop. With ```htop --help``` I could find some options.

![htophelp](Screenshots/2/htophelp.png)

I decided to run ```htop -t```.

![htop-t](Screenshots/2/htop-t.png)

This opened an interesting view where I could gain insight on what is happening on the device for example running processes.

![htop](Screenshots/2/htop.png)

I was able to scroll and exit with using a mouse which was a nice touch. Next up was ncdu. I decided to check a post by Ramuglia on I/O Flood (2023) where the basic usage of ncdu was explained. I tried ```ncdu /home``` (Ramuglia, 2023).

![ncduhome](Screenshots/2/ncduhome.png)

I navigated using the arrow keys and enter.

![ncdu](Screenshots/2/ncdu.png)

I checked the cache and went deeper until I was at the end.

![ncdu2](Screenshots/2/ncdu2.png)

![ncdu3](Screenshots/2/ncdu3.png)

![ncdu4](Screenshots/2/ncdu4.png)

I found that the Firefox startup cache was taking the most space. Last but not least I tested the cowsay program. Gurpeets (2023) post got me interested in the cowsay program. I checked the manual page with ```man cowsay```.

![mancowsay](Screenshots/2/mancowsay.png)

![man](Screenshots/2/man.png)

I made a cow and Tux say Hello! Got the ```-f tux``` from linux.fi (s.a) post.

![cowsay](Screenshots/2/cowsay.png)

![tuxsay](Screenshots/2/tuxsay.png)

I was done with this at 1:04 PM. 

### Important directories

I was instructed to find and show the important directories explained in the post by Tero (Karvinen 2020). These were ```/``` ```/home/``` ```/home/[username]/``` ```/etc/``` ```/media/``` ```/var/log/```. I started at 1:08 PM. First was the root directory. I went there with ```cd /``` and double checked it with ```pwd```.

![cdroot](Screenshots/2/cdroot.png)

Then I used ls to list the contents. Here an interesting directories are bin and sbin. Bin short for binary has binary files. For example, commands like ls or grep etc can be found here. Sbin is system bin where important system binaries are located.

![lsroot](Screenshots/2/lsroot.png)

Next up was the home directory. I traversed there with ```cd home/```. There was only one posible directory since I only had one user made.

![cdhome](Screenshots/2/cdhome.png)

As I used the tab key to speed up the process it completed the home/. Here was my users home directory.

![lshome](Screenshots/2/lshome.png)

I traversed there with ```cd juusov/```. Then to move into /etc/ I used cd ```cd /etc/``` to jump there instantly. Configuration files can be found here. For example config files for networks, sudoers file or python3.

![etsy](Screenshots/2/etsy.png)

Then I jumped into /media/ with ```cd /media/```. Removable media can be found here.

![media](Screenshots/2/media.png)

Then traversed to the /var/log/ with ```cd /var/log/```. Logs can be found here.

![logls](Screenshots/2/logls.png)

Then I just jumped back to /var/ with ```cd ..```.

![varls](Screenshots/2/varls.png)

I was done at 1:16 PM. Traversing in the cli is fast but reporting every move at the same time is slow.

### Using grep

I started this at 1:32 PM. First I wanted to see if the bluetooth service was enabled or disabled so I used ```sudo service --status-all | grep bluetooth```.

![service](Screenshots/2/service.png)

The output showed that the bluetooth service was in fact disabled. I learned the ```service --status-all``` command some time ago when I learned about Linux hardening checklists. I moved into the /bin directory with ```cd bin```. There I checked the man page of grep with ```man grep``` because I wanted to find a way of using grep to find the absolute value. I found that it can be done with ```grep -w```. Then I decided to search grep with grep from the /bin directory. I did this with ```ls | grep -w grep```.

![grep](Screenshots/2/grep.png)

This is the output without -w.

![grepgrep](Screenshots/2/grepgrep.png)

Here I checked the error logs and I wanted to find error messages that were associated with sudo. So I used ```sudo journalctl -p err | grep sudo```.

![err](Screenshots/2/err.png)

I found the -p err from journalctl manual with ```man journalctl```. Played around a bit and checked possible emergency and critical logs aswell.

![crit](Screenshots/2/crit.png)

I was done at 2:08 PM.

### Using pipes

At 2:12 PM I ran this ```journalctl | grep sudo | less``` command to read sudo logs with less.

![errless](Screenshots/2/errless.png)

Closed it with q. I was done at 2:14 PM.

### Log

I purposely caused a mistake when writing sudo pass to check the event with journalctl. I used ```journalctl -p err | grep sudo``` to find this event. The log says pretty clearly that the user "juusov" from /home/juusov inserted one incorrect password when trying to use the command useradd. The useradd binary recides in /usr/sbin.

![passfail](Screenshots/2/passfail.png)

Then I started ```journalctl -f``` on one terminal and opened a second one. With the second terminal I created a user with ```sudo adduser testi```. Then I deleted the user "testi" with ```sudo userdel testi```. Both of these succesful events can be seen on the journalctl log. First line indicates that a sudo session was opened. Before this line should be info on what command was used by who and where but it seems like I took a bad screenshot. a group named testi was added to /etc/group and /etc/gshadow. A new user was created with the name testi. Home directory was declared to be /home/testi. Default shell was configured to be bash. Password was made for user testi. "gkr-pam: couldn't update the login keyring password: no old password was entered" is probably caused by the fact that the new user testi didn't have an old password since I created it for the first time. So this can be ignored if my deduction is correct. Testi was added to the group "users". Sudo session closed. User juusov used the command (sudo) userdel testi from /home/juusov/Desktop. Juusov inserted the correct password and opened a sudo session. User testi was deleted. User testi was deleted from group "users". Group testi was removed. User testi was deleted from shadow group "users". Sudo session closed.

![success](Screenshots/2/success.png)

At 2:38 PM I was done.


# References

Gurpreet, S. August 16, 2023. 15 Fun Linux Command Line Programs to Spice Up Your Terminal. Medium. Available at [https://medium.com/@gurpreet.singh_89/15-fun-linux-command-line-programs-to-spice-up-your-terminal-abf30af73de1](https://medium.com/@gurpreet.singh_89/15-fun-linux-command-line-programs-to-spice-up-your-terminal-abf30af73de1). Read on January 25, 2024.

Karvinen, T. January 11, 2024. Linux Palvelimet 2024 alkukevät. Homework. Available at [https://terokarvinen.com/2024/linux-palvelimet-2024-alkukevat/](https://terokarvinen.com/2024/linux-palvelimet-2024-alkukevat/).

Karvinen, T. February 3, 2020. Command Line Basics Revisited. Available at [https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited](https://terokarvinen.com/2020/command-line-basics-revisited/?fromSearch=command%20line%20basics%20revisited). Read on January 25, 2024.

Linux.fi, s.a. Cowsay. Available at [https://www.linux.fi/wiki/Cowsay](https://www.linux.fi/wiki/Cowsay). Read on January 25, 2024.

Ramuglia, G. December 15, 2023. ncdu Command Guide | Managing Linux Disk Usage. I/O Floods. Blog. Available at [https://ioflood.com/blog/ncdu-linux-command/](https://ioflood.com/blog/ncdu-linux-command/). Read on January 25, 2024.

Reddit. February 15, 2023. What "nice-to-have" CLI tools do you know? Post at r/linuxquestions. Available at [https://www.reddit.com/r/linuxquestions/comments/112i1vl/what_nicetohave_cli_tools_do_you_know/?rdt=38896](https://www.reddit.com/r/linuxquestions/comments/112i1vl/what_nicetohave_cli_tools_do_you_know/?rdt=38896). Read on January 25, 2024.
