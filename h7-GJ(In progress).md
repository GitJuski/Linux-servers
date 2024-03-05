# Introduction

The last homework assignment of this course. There's four subtasks with an additional bonus task.
- a) Create a "Hello World!" program with a language of choosing
- b) Create a new command in Linux that any user could use
- c) Do a graded lab assignment from an earlier course
- d) Create a fresh new virtual machine for the graded lab assignment
- bonus) List your optional tasks and updated tasks that you have done

(Karvinen 2024)

# Essential information



In addition to information on this screenshot, I had 287 GB of free space on my SSD, I used a wireless connection and I was home in Vaasa. With the limited time I had on March 5, 2024, I only decided to do the first two task and the other tasks later.

## Hello World!

First I opened the VirtualBox application and selected the correct machine this time being the main VM. I logged in and opened the terminal with Ctrl + Alt + T. I got a greeting from a cow since I made a script earlier today that runs every time I open the terminal.

![1](Screenshots/7/1.png)

I changed directory to a newly made directory I made earlier today. I used `cd skripti` to do this. Here's a little showcase on the simple scripts I made during the lecture.

![2](Screenshots/7/2.png)

kokeilu.sh and uusikomento were testing scripts so there were no reason for me to show them. This is a python script that takes three arguments.

![3](Screenshots/7/3.png)

A name, number 1 and number 2. If the name argument is empty it prints "You didn't give a name". Else it just greets the name. I asked ChatGPT on how to grab the argument from the terminal and use it in a python script. I used It's answer as a reference for the if else lines. Everything else I added by myself. I wanted it to work even when an IndexError or NameError would occur on these lines so I added try except blocks to counter this. The rest of the script just takes the last two arguments as variables and multiplies them in the print statement.

![4](Screenshots/7/4.png)

The pyskripti.py is just a simple if, else script with user inputs.

![5](Screenshots/7/5.png)

![6](Screenshots/7/6.png)

The skripti.sh is the shell script that runs when I open a terminal.

![7](Screenshots/7/7.png)

![8](Screenshots/7/8.png)

It gets the current hour and uses it in if, else statements. If it is under 12 It uses cowsay to print good morning, if it's under 18 it prints good day and in other cases it prints good evening. After this it prints a line with echo and under it the current date. To make it run when a terminal is opened I simply added the path to the .bashrc.

![8.0](Screenshots/7/8.0.png)

![9](Screenshots/7/9.png)

Now to the task at hand. I started part A at 5:18 PM. First I made a new file called helloword.

![10](Screenshots/7/10.png)

I added the shebang line and added the print("Hello World!").

![11](Screenshots/7/11.png)

It was done and it worked.

![12](Screenshots/7/12.png)

I was done at 5:19 PM.

## A new command

I had already made two of the scripts universal during the lecture.

![13](Screenshots/7/13.png)

I tested that it works and I even created a new user and tested it with it as well.

![14](Screenshots/7/14.png)

![15](Screenshots/7/15.png)

![16](Screenshots/7/16.png)

I was assignment to create a new command so I started at 5:34 PM. First I removed helloworld and uusikomento since I didn't need them anymore. I created a new file with the name new...

![17](Screenshots/7/17.png)

I created a simple bash script. First the shebang! Then I created a variable user that grabs the output of whoami command. Then I created a simple if, else that checks the username currently operating. If the name is voldemort it prints a message saying that he's not welcome. If the username is something else the user is welcomed.

![18](Screenshots/7/18.png)

Tested it and ran into a syntax error. Well I forgot the fi.

![19](Screenshots/7/19.png)

That's something I need to get used to. I added it and it then worked.

![20](Screenshots/7/20.png)

![21](Screenshots/7/21.png)

I added the permissions to execute the script. It had read permissions on by default.

![22](Screenshots/7/22.png)

I tested it with ./new and then I copied it over to /usr/local/bin/. It works simply with new.

![23](Screenshots/7/23.png)

I tested it with voldemort and it worked like a charm.

![24](Screenshots/7/24.png)

I was at 5:41 PM.

## Earlier lab assignment

COMING SOON...

## A fresh VM

COMING SOON...

## Optional

COMING SOON...
