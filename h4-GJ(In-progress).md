# Introduction

In task x I was assigned to summarize two different posts. The first post is a report by Susanna (lehto 2022) titled "Teoriasta käytäntöön pilvipalvelimen avulla (h4)" and it can be found at [https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/](https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/) and the second post is guide by Tero (Karvinen 2017) titled "First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS" and it can be found at [https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/](https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/).

The rest of the assignment is again divided into subtasks. I'm was supposed to rent a vm from the cloud, configure it and make it host a website. Finally I also had to rent a domain name which I already had done before this assignment.

# "Teoriasta käytäntöön pilvipalvelimen avulla (h4)" summed up

COMING SOON...

# "First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS" summed up

COMING SOON...

# The main task

## Essential information

I started this task at 9:41 AM on February 7th. I was at home in Vaasa at the time. I used the picture I took last time since it was still valid. In addition to the information on the picture, I used a wireless connection which was great and I had 386 GB of free space on my SSD. Also I decided to list the specs of my virtual machine. I grabbed the information by opening Virtualbox and selecting the correct vm. Have to say that the mouse that I was using was dying. It really got on my nerves and made the whole process longer since it would usually register a click multiple times etc. A laggy mouse and a slower internet connection together weren't the best combo. I'm happy that I went ahead and bought a new mouse when taking care of other business. The new mouse made the last part of this process much more enjoyable.

## Renting a vm from the cloud

I started doing this task at 9:49 AM. I already had an account so I only had to log in. First I a new tab on my browser and searched for Linode. Opened the correct site, navigated to the top right corner and hit log in. Typed my credentials and I was in. I clicked on "create a linode", chose Debian 12 as the image, Stockholm, SE as the region and whiched to shared CPU and chose the cheapest option. Created a label and a strong root passphrase. Then I hit create Linode and it was running in under a minute. I was done with this at 10:04 AM. I had to take care of a couple of things so I decided to power off the machine for that time just to be safe.

## First steps

After taking care of a couple of mandatory things I was back at 10:24 AM. First I powered the machine on. I opened my own vm in Virtualbox by selecting it and pressing start. Did the usual by opening terminal and ran `sudo apt update` and `sudo apt upgrade`. Tried to connect with ssh and I had a problem. My VM didn't somehow have the ssh client so I installed it. I wasn't able to connect so I tried it again and again for a couple of times. Then it asked for a password and I typed it. Then I was in and I was a little confused on why it had root@localhost. I thought that I had set the name to be weppi. I ran `sudo apt update` and then I installed ufw with `sudo apt install ufw`. Then I had to make a hole in the firewall for port 22. I was using sudo even though I was root because using sudo logs the events. I checked the added rules before enabling the ufw. It was ok so I enabled the firewall.

At 11:17 AM I ran `sudo apt update` and `sudo apt upgrade`. Had a problem with upgrade. I just clicked an option that said "install a maintainers version". I then searched for it on the web and found this. After reading the answer in the digitalocean community post I came to the conclusion that I made the right choice since I didn't do any modifications to the sshd config beforehand. Then I created a user and added it to the sudo and adm groups. Connected with the new account and it works. Double checked the groups. Locked the root password. Then I disabled the root login by opening the config file and changing a value to no. Tried to login as root and it didn't work so that was good. This task was completed at 11:40 AM.

## Web server

On February 8th I continued my work. I started this doing task at 8:55 AM. Some changes to the essential information include the change of location and network connectivity. I arrived in Helsinki yesterday evening. So at this time I was in Helsinki visiting relatives and I was using a wireless connection that was notably slower than my own at home.

First I launched my VM by opening the Virtualbox application and hitting start. I opened the terminal and ran `sudo apt update`. Then I had to start the server residing in the cloud since I powered it off last time. So I searched for Linode, opened the correct site, logged in, selected the correct VM and hit "power on". I connected via ssh. When I was in I ran `sudo apt update`. I installed Apache2. I then enabled the service but to my surprise it was already enabled. After this I checked the default site with curl. I installed micro, navigated to the `/etc/apache2/sites-available` directory with `cd /etc/apache2/sites-available` made a new configuration file in `/etc/apache2/sites-available`. I'm surprised on how well I remembered this basic conf. I only needed to cheat on the "require all granted" part. Anyways then I navigated to the /home/juski dir with `cd`. There I created the correct directories and I then created an index.html file. I created another hole to test the default conf. Then I disabled the default conf and enabled my conf. I tested the conf and it was ok. Then I restarted Apache. Okay I had a problem once again. I added the error log into my new config file and opened the site again to log the error. Well the error.log has only earlier errors. Well after restarting apache, opening the site and opening the logs I realized that it logs the error but in different time... After a while of checking permission I found that the /home/juski has tight permission and that it is probably the problem with this. Well at this point I was closer to the solution but I got some things to take care of so I had to stop here and continue this later. It was 10:53 AM at that time.

I was back in business at 7:06 PM with a new mouse! Now I was in a bit of a pickle. I could mod the /home/juski dir permissions or I could use the /var/www/html as the documentroot. Either of these would probably fix the issue. I had a feeling that the permissions mod would create a security risk since I'm giving more permissions to /home/juski directory, In the other hand the whole point of this machine is to host a website and nothing else. I decided to try if the modification of permissions work. So I found a comman `namei -m` and I used `namei -m /home/juski/publicwebsite/`. The output clearly showed that the juski directory was missing permissions so I ran `sudo chmod +x juski`. After running this command an x spawned at the end of the juski line. This was almost the same as in the other VM. Well this setup works. I decided to play around with the permissions for a while to study them. In the end I gave the same permissions as in the other VM. I made a short html page and tested it. I was done at 7:41 PM.

## Domain name

Immediately after I started to work on this task. First I opened a new tab on a browser and searched for namecheap. namecheap.com is the right address so I clicked it and signed in with my credentials. I scrolled down to find the correct domain. There I clicked "manage". Here I opened the advanced dns tab and deleted the default records. I added two A-records with a 30min TTL (Time To Live). I tested it pretty much immediately and it responded! I was done with this at 8:00 PM. After this I added the access logging into the website configuration. I wanted to use ssh keys so I decided to do it as an optional personal task the next day.

## Optional task for personal use

COMING SOON...

# References

Digitalocean. October 25, 2023. sudo apt upgrade, offers some questions? A community post. Available at [https://www.digitalocean.com/community/questions/sudo-apt-upgrade-offers-some-questions](https://www.digitalocean.com/community/questions/sudo-apt-upgrade-offers-some-questions). Read on February 7, 2024.

Karvinen, T. January 11, 2024. Linux Palvelimet 2024 alkukevät. Available at [https://terokarvinen.com/2024/linux-palvelimet-2024-alkukevat/](https://terokarvinen.com/2024/linux-palvelimet-2024-alkukevat/).

Karvinen, T. September 19, 2017. First Steps on a New Virtual Private Server – an Example on DigitalOcean and Ubuntu 16.04 LTS. Available at [https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/](https://terokarvinen.com/2017/first-steps-on-a-new-virtual-private-server-an-example-on-digitalocean/). Read on February 7, 2024.

Lehto, S. February 14, 2022. Teoriasta käytäntöön pilvipalvelimen avulla (h4). Available at [https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/](https://susannalehto.fi/2022/teoriasta-kaytantoon-pilvipalvelimen-avulla-h4/). Read on February 7, 2024.
