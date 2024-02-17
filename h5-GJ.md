# Introduction

It's time for homework assignment number five. There was no need to summarize posts this time. The assignment is divided into subtasks a, b, c and an optional task m.

- In task a, I was supposed to configure a fresh virtual machine that had Apache and an SSH-server installed on it. The purpose of the machine was to host a website using virtual-based host techniques. This task could be done locally within VirtualBox.
- In task b, I was supposed to configure SSH key authentication for this new VM.
- Task c was about analyzing and comparing information on my domain name with outputs from the `hosts` and `dig` commands, as well as information about my domain name from the tenant's page, which in my case is Namecheap.com.
- The optional task was to install Vagrant and configure a virtual machine with it.

(Karvinen 2024)

# Essential information

![0](Screenshots/3/1.png)

This screenshot is still valid even though I've updated the system in between. I should provide some information on the specs listed, so that those who aren't as tech-savvy can understand the starting point as well.
- OS Name - This is the operating system name. Windows 11 is the newest Windows OS. Pro version is a version with some additional features. The home version is the usual version people use at home and the pro version is more tailored towards business use.
- Microsoft is the manufacturer of the said OS.
- System manufacturer is the manufacturer of the laptop that I used. Here it is Lenovo.
- System type - x64-based is the norm these days.
- System SKU - Essentially the model of this laptop is Lenovo ThinkPad T14 generation 2a.
- Processor - The processor listed is a decent processor, nothing too fancy nor nothing too bad. This could be compared to some Intel i5 processors. A processor is like the brains of a computer.
- RAM - 16 GB is a good amount of RAM for a school/hobby laptop. The more RAM a computer has, the more tasks a computer can handle simultaneously.

Additional information includes,
- Location - At home in Vaasa
- Network - a good wireless connection
- Storage - An SSD with 350 GB of free space

# The main assignment

## A new virtual machine

I started doing the first task on February 16, 2024, at 11:49 PM.

First, I opened the VirtualBox application. There I clicked on "new".

![1](Screenshots/5/1.png)

![2](Screenshots/5/2.png)

Then I selected the correct image. Changed the version to 64-bit, clicked skip unattended installation and filled in other information. RAM -> 2048 MB, CPU -> 2 and Storage -> 50.59 GB.

![3](Screenshots/5/3.png)

I clicked on start and selected the first option.

![4](Screenshots/5/4.png)

Once I was in, I checked that I could surf the net with Firefox and checked that the console works.

![5](Screenshots/5/5.png)

![6](Screenshots/5/6.png)

![7](Screenshots/5/7.png)

Then I opened the Install Debian application. Clicked on launch anyway.

![8](Screenshots/5/8.png)

Chose English as the language, chose Helsinki as the location,

![9](Screenshots/5/9.png)

chose Finnish default keyboard layout and tested it,

![10](Screenshots/5/10.png)

checked erase disk and made sure that the disk is correct and master boot record was selected,

![11](Screenshots/5/11.png)

typed my credentials and finally clicked install.

![12](Screenshots/5/12.png)

The installation was completed at 12:05 PM. Then it froze

![13](Screenshots/5/13.png)

so, I shut it down manually and started it again. I logged in and opened the terminal.

![14](Screenshots/5/14.png)

It was `sudo apt update` and `sudo apt upgrade` time. Now this step and the earlier installation took a while. The upgrade was done at 12:14 PM. Then I installed ufw and enabled it,

![15](Screenshots/5/15.png)

installed Apache2.

![16](Screenshots/5/16.png)

and remembered to install the guest additions (GitJuski 2024).

![17](Screenshots/5/17.png)

In between I checked the status of Apache service.

![18](Screenshots/5/18.png)

I then inserted the guest additions cd from devices.

![19](Screenshots/5/19.png)

After this I made my way to the correct directory and ran the `autorun.sh` script

![20](Screenshots/5/20.png)

and after it was done, I rebooted the machine.

![21](Screenshots/5/21.png)

When I got back in, I installed the SSH server.

![22](Screenshots/5/22.png)

Then I created a new virtual host by going to the /etc/apache/sites-available and creating a new file with sudoedit.

![23](Screenshots/5/23.png)

This time I remembered the whole config for memory.

![23.2](Screenshots/5/23.2.png)

Then I saved it and disabled the default conf. Then I tried to enable the new conf, but it didn't work and then I realized that I didn't add the .conf suffix. Well, I renamed it but forgot sudo so I grabbed the command again with up arrow key and then went to the start of the command with ctrl + a. There I added sudo and then pressed return and it worked.

![24](Screenshots/5/24.png)

Then I enabled the conf and tested the config. The syntax was ok but the document root path was missing so I made the path and tested the config again.

![25](Screenshots/5/25.png)

![26](Screenshots/5/26.png)

![27](Screenshots/5/27.png)

Then I restarted Apache,

![28](Screenshots/5/28.png)

I made my way to the new directory and this time, I created an index.html file with the cat command.

![29](Screenshots/5/29.png)

After the index.html file was created I used curl to check the website and it was showing properly.

![30](Screenshots/5/30.png)

Then I edited the hosts file with sudoedit.

![31](Screenshots/5/31.png)

There I added the anjovis.example.com and made it point to 127.0.0.1 which is the localhost.

![32](Screenshots/5/32.png)

I tested it with Firefox, and it worked.

![33](Screenshots/5/33.png)

I was done with this at 12:36 PM. At this point I had a lunch break.

## SSH keys

I got back to work at 2:12 PM. I wanted to simulate this whole thing inside an internal network. Essentially, I created an isolated network where the puppet-server and the master will reside isolated from outside network and my own LAN (Local Area Network). I have done this once before with a guide from one of my favorite Youtubers Networkchuck (NetworkChuck 2021). The internal network and the dedicated DHCP (Dynamic Host Configuration Protocol) server can be made using VirtualBox tools. Mainly a tool called Vboxmanage.

First, I opened the VirtualBox application. There I clicked on the puppet machine and clicked settings.

![34](Screenshots/5/34.png)

There I opened the network tab and changed the "attached to:" option to internal network from NAT. I gave the internal network the name "Room". Then I did the same for the controller machine (master-controller).

![35](Screenshots/5/35.png)

![36](Screenshots/5/36.png)

Then I had to create a dhcp server for the network and I did it like this.

![37](Screenshots/5/37.png)

First, I opened the cmd on windows and navigated to C:\Program Files\Oracle\VirtualBox. There I opened vboxmanage and told the executable to add a DHCP server to the network called Room. I gave the DHCP an IP address of 10.30.1.1 and then I configured the IP range to be 10.30.1.110 to 10.30.1.115. The netmask was the usual /24 (255.255.255.0). --enable enabled the server. (NetworkChuck 2021.)

Then to check that it was correctly configured I used a command `vboxmanage list dhcpservers` to list them and checked the correct configuration (VirtualBox.org s.a).

![38](Screenshots/5/38.png)

Then I started both machines and logged in. On the left is the controller aka master-controller and the user masterofpuppets. On the right is the puppet machine aka puppet-box with a user anjovis.

![39](Screenshots/5/39.png)

Here I checked that the DHCP server assigned the correct IP addresses. Then I pinged Google's DNS (Domain Name System) without success and then I pinged the puppet-box and it responded.

![40](Screenshots/5/40.png)

So, these machines are isolated together in this network. On the puppet-box I opened the ports 22 and 80.

![41](Screenshots/5/41.png)

Now I was able to open a browser and navigate to the puppets IP address with the master machine. I could read the heippa text which was good.

![42](Screenshots/5/42.png)

Then I established an SSH connection to the puppet with the master. Here we can see that there were two sessions on the puppet-box.

![43](Screenshots/5/43.png)

One from :0 and one from 10.30.1.111. The one from 10.30.1.111 is the master. Then I created an SSH key pair and sent the public key to the puppet.

![44](Screenshots/5/44.png)

![45](Screenshots/5/45.png)

I checked that the key arrived inside the puppet machine.

![46](Screenshots/5/46.png)

Then I connected to the puppet without a password.

![47](Screenshots/5/47.png)

There I locked the root password.

![48](Screenshots/5/48.png)

Then I edited the sshd_config.

![49](Screenshots/5/49.png)

There I changed PasswordAuthentication to no and PermitRootLogin to no.

![50](Screenshots/5/50.png)

![51](Screenshots/5/51.png)

Then I exited the SSH connection and edited the hosts file.

![52](Screenshots/5/52.png)

There I added anjovis.example.com to point towards 10.30.1.110.

![53](Screenshots/5/53.png)

I checked the site with Firefox on the master-box and checked the access.log on puppet-box.

![54](Screenshots/5/54.png)

I set the tail to be active so I can open the site again and see the new lines. 

![55](Screenshots/5/55.png)

I was done at 2:53 PM.

I decided to take some screenshots after, to show that the site works but the connections to outside doesn't.

![56](Screenshots/5/56.png)

I also tested the SSH once more since I made the password logins prohibited.

![57](Screenshots/5/57.png)

## host and dig

I started doing this at 3:38 PM. First, I started my main VM.

![58](Screenshots/5/58.png)

There I did the usual (`sudo apt update` and `sudo apt upgrade`). Then I installed the host and dig commands (Karvinen 2024).

![59](Screenshots/5/59.png)

After the installation was done, I used them both. I wanted to put the outputs into their own files.

![60](Screenshots/5/60.png)

For example `host codehammer.shop > host_output.txt` uses the command host to lookup information from codehammer.shop and then puts the output into a new file called host_output.txt. Then I just used cat to print the insides of these said files into two separate terminal windows.

![61](Screenshots/5/61.png)

Then I navigated to namecheap.com and logged in.

![62](Screenshots/5/62.png)

There I went to the domain list and advanced domain tab. The host dig output shows two A records just like in the advanced dns tab. The dig output also shows the number 1800 which refers to the 30 min TTL (Time To Live) on the advanced tab. Both outputs also display the codehammer.shop website's IP address 172.232.159.80. Then the dig output shows the query time and the destination of the query. The server in question is Elisa's DNS server and the information was queried from there.

![63](Screenshots/5/63.png)

![65](Screenshots/5/65.png)

The host output shows that the mail is handled by eforward.registrar-servers.com which is indeed correct since I have my mail setting on email forwarding -> txt record -> @ -> v=spf1 include:spf.efwd.registrar-servers.com ~all -> automatic

![64](Screenshots/5/64.png)

I was done at 4:02 PM.

## Vagrant

I started this task at 4:20 PM. I couldn't install VirtualBox on this VM so I started looking for answers.

![66](Screenshots/5/66.png)

After a long while of researching I decided to just install it on my Windows instead.

![67](Screenshots/5/67.png)

I downloaded it. After it was done, I installed it

![68](Screenshots/5/68.png)

and after the installation I had to reboot. I opened Windows powershell and created a folder vagrant inside my user's folder with `mkdir vagrant` **(now I knew that the vagrant init command creates a file since I quickly tested vagrant during the last lecture, although I only installed the Vagrant and not the VirtualBox which is why it didn't work. Also, I had a couple of minutes to do so, so that's why I didn't go any further with it.)**. I navigated there and created the VM (Karvinen 2024).

![69](Screenshots/5/69.png)

![70](Screenshots/5/70.png)

![71](Screenshots/5/71.png)

When it was created, I connected via SSH (Karvinen 2024).

![72](Screenshots/5/72.png)

![73](Screenshots/5/73.png)

![74](Screenshots/5/74.png)

Finally I exited with exit and destroyed the machine (Karvinen 2024).

![75](Screenshots/5/75.png)

I was done at 5:32 PM.


# References

GitJuski. January 20, 2024. h1-GJ. Available at [https://github.com/GitJuski/Linux-servers/blob/main/h1-GJ.md](https://github.com/GitJuski/Linux-servers/blob/main/h1-GJ.md) Read on February 16, 2024.

Karvinen, T. January 11, 2024. Linux Palvelimet 2024 alkukevät. Available at [https://terokarvinen.com/2024/linux-palvelimet-2024-alkukevat/](https://terokarvinen.com/2024/linux-palvelimet-2024-alkukevat/)

NetworkChuck. March 5, 2021. how to build a HACKING lab (to become a hacker). A Youtube. Available at [https://www.youtube.com/watch?v=mvsiuLzpx2E](https://www.youtube.com/watch?v=mvsiuLzpx2E). Watched on February 16, 2023.

VirtualBox.org. S.a. Chapter 8. VBoxManage. Available at [https://www.virtualbox.org/manual/ch08.html](https://www.virtualbox.org/manual/ch08.html). Read on February 16, 2023.
