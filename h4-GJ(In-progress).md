# Introduction

In task x I was assigned to summarize two different posts. The first post is a report by Susanna (lehto 2022) titled "Teoriasta käytäntöön pilvipalvelimen avulla (h4)" and it can be found at [https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/](https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/) and the second post is guide by Tero (Karvinen 2017) titled "First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS" and it can be found at [https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/](https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/).

The rest of the assignment is again divided into subtasks. I'm was supposed to rent a vm from the cloud, configure it and make it host a website. Finally I also had to rent a domain name which I already had done before this assignment.

# "Teoriasta käytäntöön pilvipalvelimen avulla (h4)" summed up

COMING SOON...

# "First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS" summed up

COMING SOON...

# The main task

## Essential information

I started this task at 9:41 AM. I was at home in Vaasa at the time. I used the picture I took last time since it was still valid. In addition to the information on the picture, I used a wireless connection which was great and I had 386 GB of free space on my SSD. Also I decided to list the specs of my virtual machine. I grabbed the information by opening Virtualbox and selecting the correct vm.

## Renting a vm from the cloud

I started doing this task at 9:49 AM. I already had an account so I only had to log in. First I a new tab on my browser and searched for Linode. Opened the correct site, navigated to the top right corner and hit log in. Typed my credentials and I was in. I clicked on "create a linode", chose Debian 12 as the image, Stockholm, SE as the region and whiched to shared CPU and chose the cheapest option. Created a label and a strong root passphrase. Then I hit create Linode and it was running in under a minute. I was done with this at 10:04 AM. I had to take care of a couple of things so I decided to power off the machine for that time just to be safe.

## First steps

After taking care of a couple of mandatory things I was back at 10:24 AM. First I powered the machine on. I opened my own vm in Virtualbox by selecting it and pressing start. Did the usual by opening terminal and ran `sudo apt update` and `sudo apt upgrade`. Tried to connect with ssh and I had a problem. My VM didn't somehow have the ssh client so I installed it. I wasn't able to connect so I tried it again and again for a couple of times. Then it asked for a password and I typed it. Then I was in and I was a little confused on why it had root@localhost. I thought that I had set the name to be weppi. I ran `sudo apt update` and then I installed ufw with `sudo apt install ufw`. Then I had to make a hole in the firewall for port 22. I was using sudo even though I was root because using sudo logs the events. I checked the added rules before enabling the ufw. It was ok so I enabled the firewall.

At 11:17 AM I ran `sudo apt update` and `sudo apt upgrade`. Had a problem with upgrade. I just clicked an option that said "install a maintainers version". I then searched for it on the web and found this. After reading the answer in the digitalocean community post I came to the conclusion that I made the right choice since I didn't do any modifications to the sshd config beforehand. Then I created a user and added it to the sudo and adm groups. Connected with the new account and it works. Double checked the groups. Locked the root password. Then I disabled the root login by opening the config file and changing a value to no. Tried to login as root and it didn't work so that was good. This task was completed at 11:40 AM.

## Web server

COMING SOON...

## Domain name

COMING SOON...

# References

Digitalocean. October 25, 2023. sudo apt upgrade, offers some questions? A community post. Available at [https://www.digitalocean.com/community/questions/sudo-apt-upgrade-offers-some-questions](https://www.digitalocean.com/community/questions/sudo-apt-upgrade-offers-some-questions). Read on February 7, 2024.

Karvinen, T. January 11, 2024. Linux Palvelimet 2024 alkukevät. Available at [https://terokarvinen.com/2024/linux-palvelimet-2024-alkukevat/](https://terokarvinen.com/2024/linux-palvelimet-2024-alkukevat/).

Karvinen, T. September 19, 2017. First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS. Available at [https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/](https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/). Read on February 7, 2024.

Lehto, S. February 14, 2022. Teoriasta käytäntöön pilvipalvelimen avulla (h4). Available at [https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/](https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/). Read on February 7, 2024.
