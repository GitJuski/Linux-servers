# Introduction

It's time for homework assignment number five. There is no need to summarize posts this time. The assignment is divided into subtasks a, b, c and an optional task m.

- In task a, I'm supposed to configure a fresh virtual machine that has Apache and an SSH-server. The machine is for hosting a website with using virtual based host technique. This task can be done locally with Virtualbox.
- In task b, I'm supposed to configure SSH key authentication for this new VM.
- Task c is about analyzing and comparing information on my domain name with outputs from commands `hosts` and `dig` and my domain name information from the renters page which is Namecheap.com in my case.
- The optional task is about installing Vagrant and configuring a virtual machine with it.

(Karvinen 2024)

# Essential information



This screenshot is still valid although I've updated the system in between. I should tell something about the specs listed, so not so tech savy people can understand the starting point as well.
- OS Name - This is the operating system name. Windows 11 is the newest Windows OS. Pro version is a version with some additional accessories. The home version is the usual version people use at home and the pro version is more tailored towards business use.
- Microsoft is the manufacturer of the said OS.
- System manufacturer is the manufacturer of the laptop that I used. Here it is Lenovo.
- System type - x64-based is the norm these days.
- System SKU - Essentially the model of this laptop is Lenovo ThinkPad T14 generation 2a.
- Processor - The processor listed is a decent processor, nothing too fancy nor nothing too bad. This could be compared to some Intel i5 processors.
- RAM - 16 GB is a good amount of RAM for a school/hobby laptop.

Additional information include,
- Location - Home in Vaasa
- Network - a good wireless connection
- Storage - An SSD with 350 GB of free space

# The main assignment

## A new virtual machine

I started doing the first task on February 16, 2024 at 11:49 PM.

First I opened the VirtualBox application. There I clicked on new. Then I selected the correct image. Changed the version to 64-bit, clicked skip unattended installation and filled other information. RAM -> 2048 MB, CPU -> 2 and Storage -> 50.59 GB. I clicked on start and selected the first option. Once in I checked that I could surf the net with firefox and checked that the console works. Then I opened the Install debian application. Clicked on launch anyway. Chose english as the language, chose Helsinki as the location, chose Finnish default keyboard layout and tested it, checked erase disk and made sure that the disk is correct and master boot record was selected, typed my credentials and finally clicked install. The installation was completed at 12:05 PM. Then it froze so I shut it down manually and started it again. I logged in and opened the terminal. It was `sudo apt update` and `sudo apt upgrade` time. Now this step and the earlier installation took a while. The upgrade was done at 12:14 PM. Then I installed ufw and enabled it, installed Apache2 and remembered to install the guest additions. In between I checked the status of Apache service. I then inserted the guest additions cd from devices. After this I made my way to the correct directory and ran the `autorun.sh` script and after it was done I rebooted. When I got back in I installed the ssh server. Then I created a new virtualhost by going to the /etc/apache/sites-available and creating a new file with sudoedit. This time I remembered the whole config for memory. Then I saved it and disabled the default conf. Then I tried to enable the new conf but it didn't work and then I realised that I didn't add the .conf suffix. Well I renamed it but forgot sudo so I grabbed the command again with up arrow key and then went to the start of the command with ctrl + a. There I added sudo and then pressed return and it worked. Then I enabled the conf and tested the config. The syntax was ok but the documentroot path was missing so I made the path and tested the config again. Then I restarted Apache, made my way to the new directory and created an index.html this time with the cat command. After the index.html file was created I used curl to check the website and it was showing properly. Then I edited the hosts file with sudoedit. There I added the anjovis.example.com and made it point to 127.0.0.1 which is the localhost. I tested it with Firefox and it worked.

I was done with this at 12:36 PM. At this point I had a lunch break.

## SSH keys
