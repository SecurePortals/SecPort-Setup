## The nature of dealing with software
>Now this is where things get a bit tricky. Our goal is to accomplish the following:

1. Install Pycharm
2. Install Django
3. Install Postgres
4. Set up Pycharm Interpreter
5. Create PostgreSQL Database (run my script)
6. Setup up Django Environment to point to PostgreSQL database

>And we're going to do a lot of back and forth in order to accomplish this, and will probably use Google a lot, but hey, that's how things go. I spent about a day going around between a lot of different blogs and documentation, and can't remember the exact steps I took in order to get mine to work, but this was the general workflow that got things to work for me.

## Install Pycharm

>[Install Community Pycharm](https://www.jetbrains.com/pycharm/download/#section=mac)
>PyCharm is a Python IDE (Integrated Development Environment) which allows us to have an easier time developing in Python. It's my preferred choice because I'm most comfortable using it, it has a great community for help and resources, and it's entirely open-source which makes this IDE a gem. 

## Install Django

>To install Django, we need to use pip3, which stands for Preferred Installer Program (version 3 for Python 3). It comes out of the box with Python3 so we don't need to download it from anywhere. We might want to check if it's updated:

```bsh
sudo -H pip3 install --upgrade pip
```

>And then install Django:

```bsh
pip3 install Django==2.0.4
```

## Quick note on 'sudo'

>Sudo. If you noticed in the command to upgrade pip3, we had to prepend the command with 'sudo'. 'sudo' is the. most. powerful word in the command history dictionary, because it forces the computer to do whatever you are telling it to do. In respect to our pip3 upgrade code, if we didn't have 'sudo' included in the command, then Terminal would look inside your Python3 folder, see pip3 already there, and think "why do I need to install anything? It's already here!" and then not upgrade to the latest pip3. But when the Terminal see's 'sudo', it doesn't ask questions. It will execute whatever code you send it. This is great! But what if you said something like 'sudo delete everything everywhere'? I don't think a command like that exists, per se, but the idea is that with great power comes great responsibility and 'sudo' should only be used when absolutely necessary. 

## Installing PostgreSQL

>Now I'm a little confused about this part as well, because I know that you need PostgreSQL, but I don't know about psycopgy2, which is supposed to be the same thing? Just to be sure I installed both:

```bsh
brew install postgresql
```

```bsh
pip3 install psycopg2
```

>And now we need to make sure our configuration is appropriate to run Django locally, so we're going to hop into the configuration file:

```bsh
nano /usr/local/var/postgres/postgresql.conf
```

>And look for the line that says:

```bsh
#listen_addresses =
```

>And we're going to uncomment it by deleting the '#', and then adding our Ipv6 and Ivp4 sockets so that we can connect to our postgreSQL database from the Django Engine. We're only making changes to this one line of code.

```bsh
listen_addresses = '::1, 127.0.0.1'            # what IP address(es) to listen on;
```

>And then save and quit by doing ctrl-X, hit 'y', and then enter. 

## Deploy our Django App

>Now that we got things going, let's start a new Django Project:

```bsh
django-admin startproject SecurePortals
```

>Which should create a new folder in your home directory called SecurePortals. This is the root folder for our project and everything we do will go into this folder. 

## Set Up PyCharm interpreter

>So now we can set up PyCharm so it can point to the right version of Python, so we can run some setup scripts. Open PyCharm, select the SecurePortals folder we just created as our project folder, and follow this path from the toolbar on the top:

>       PyCharm > Preferences > Project: SecurePortals > Project Interpreter > The gear on the right side of the window
>       > System Interpreter > and look for /usr/local/bin/python3.6

>Hit okay, and let's get our environment going.

## Create PostgreSQL Database

```bsh
pg_ctl -D /usr/local/var/postgres start && brew services start postgresql
```

