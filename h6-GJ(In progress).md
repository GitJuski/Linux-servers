# Indroduction

It was time for homework number six. This assignment was essentially split into two different tasks. The first task was about summarizations. In the task I was supposed to summarize two different posts by Tero Karvinen. (Karvinen 2024.) These posts were the posts I used as a guide while doing the other task. The first post is titled "Deploy Django 4 - Production Install" (Karvinen 2022, Production install) and the second one is titled "Django 4 Instant Customer Database Tutorial" (Karvinen 2022, CRM). In the other task I was supposed to do a succesfull production install of Django and create a simple app.

# Deploy Django 4 - Production Install summed up

COMING SOON...

# Django 4 Instant Customer Database Tutorial summed up

COMING SOON...

# The main task

## Essential background information

I did things little bit differently this time. I didn't write this report while doing the task like I used to do. This time I just made a short one liner notes while doing the task. I then built this report from those notes. This allowed me to fully focus on the task and I was done with it faster. I wanted to do this task from scratch, so I decided to do it on another VM. This VM had GNOME desktop environment instead of xfce which is why it looks a bit different. I have used this VM as a lab machine inside a test environment. To make it safe I had to close firewall ports, delete vulnerable users, change the network mode to NAT and purge apache2. I also decided to disable and stop the SSH. Once I was done with those I started doing this task.

My sysinfo.txt was still valid. 288 GB of free space on SSD, I was home in Vaasa and I used a good wireless connection. The VM had 4 GB of RAM, 2 processors and 50 GB of storage.

## Production install

### Apache

I started this at 2:41 PM. First I opened the VirtualBox application, selected the correct VM and hit start. Once I was in I updated the repos and upgraded packages with `sudo apt update` and `sudo apt upgrade`. Then I installed Apache with `sudo apt install apache2`. Once it was installed I made my way to the sites-available directory and there I created a new configuration file named etsycom. Inside it I wrote the config using Tero's guide as a reference since it was a bit different from the last few times. After this was done I made the directory. I disabled the default conf, enabled the new conf and did a configtest. The syntax was ok so I made an index.html file inside the correct directory and then I tested it. Localhost showed the default page. I forgot to restart the service so I did it. Well that didn't work until I realized that the /static was declared inside the config. Then I tried localhost/static/ and that worked.

### Django

I installed virtualenv. Then I created the environment (Karvinen 2022, Production install). I activated it, checked that the pip is correct and created a requirements file with django correctly written in it (Karvinen 2022, Production install). After these steps I installed django and checked the installed version. I started a new project and ran into an error which was expected since I had the directories already. I removed the directories and started the project succesfully this time. Here I deactivated the virtualenv since I was really confused on how this thing works. I understood it like it was supposed to be activated when modifying things inside these directories /publicwsgi/... Later on I noticed that I didn't remember to activate it before doing changes, so now I think that it is good to have it activated when running manage.py script but is it mandatory when for example changing setting. I need to play around with it some more to understand the logic fully. After I deactivated it I started to edit the etsycom.conf once more. I opened another shell where I copied the path to TVENV. I wrote the whole config manually by copying Tero's (Karvinen 2022, Production install) config from the guide. I wanted to write it manually to understand the config more in depth. Then I installed the wsgi module (Karvinen 2022, Production install). The installation already showed me that there was some errors on the config. I checked the cofig with configtest as well. I opened the config with sudoedit and found the error. I had put two closing directories... Maybe I should just copy these configs when tired. Well I fixed the issue and tested the config once more. I forgot `>`. I added it and the syntax was ok. I restarted the service with `sudo systemctl restart apache2` and checked the localhost. A rocket was taking off! I checked that it was running on Apache

### Disabling debug and applying static assets

I started this at 3:16 PM. First I opened the setting.py file. There I changed the DEBUG = from True to False and added localhost into the ALLOWED_HOSTS. I used touch to load the changes. Then I checked the site. Not Found was expected. I opened the settings again. This time I added `import os` at the start and `STATIC_ROOT = os.path.join(BASE_DIR, 'static/')` after the STATIC_URL. (Karvinen 2022, Production install.) At this point I noticed that I forgot to activate the env again so I changed to the publicwsgi directory and used `source env/bin/activate` before going to the etsycom and using manage.py. Then I checked that the localhost/admin shows the login screen correctly. The localhost itself doesn't show anything and the localhost/static showed an error. I deactivated the env and checked the logs and noticed that the index.html is missing since I removed it some time ago when creating the project. Here I just checked how the things are organized. Then I made a simple index.html file and checked it.

### CRM

I started this at 3:30 PM. First I made my way back to the publicwsgi, activated the venv and then made my way to the dir with manage.py. I updated the databases and created an admin user. Then I tried it and I was in. (Karvinen 2022, CRM.) Here I forgot to startapp the crm before going to add it to the installed apps. I opened the settings with the same command `nano etsycom/settings.py` and there I added crm to the installed apps (Karvinen 2022, CRM). Now this created a problem when I used manage.py startapp crm. I removed the crm from the settings and used the startapp crm (Karvinen 2022, CRM). Then I added the crm back to the settings and after that I opened the models.py. There I added a customer class. Updated the databases. Opened the admin.py and linked them together. Then went to check it but it wasn't showing. I updated the database and restarted Apache. Now it was there. There I added five objects with the add button. To make the names show I opened the models.py once again with `nano crm/models.py` and added a short function. (Karvinen 2022, CRM.) Then I did the usual and went to check the site again. It worked!

I was done at 3:54 PM

# My optional task.

I wanted to make another app since the crm app was done using Tero's step by step guide. COMING SOON...

# References

Karvinen, T. January 11, 2024. Linux Palvelimet 2024 alkukevät. Available at [https://terokarvinen.com/2024/linux-palvelimet-2024-alkukevat/](https://terokarvinen.com/2024/linux-palvelimet-2024-alkukevat/)

Karvinen, T. February 13, 2022. Deploy Django 4 - Production Install. Available at [https://terokarvinen.com/2022/deploy-django/](https://terokarvinen.com/2022/deploy-django/). Read on February 28, 2024.

Karvinen, T. February 13, 2022. Django 4 Instant Customer Database Tutorial. Available at [https://terokarvinen.com/2022/django-instant-crm-tutorial/](https://terokarvinen.com/2022/django-instant-crm-tutorial/). Read on February 28, 2024.
