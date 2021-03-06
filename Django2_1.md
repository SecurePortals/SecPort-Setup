## The nature of dealing with software
>Now this is where things get a bit tricky. Our goal is to accomplish the following:

1. Install Pycharm
2. Install Django
3. Install Postgres
4. Set up Pycharm Interpreter
5. Create PostgreSQL Database
6. Setup up Django Environment to point to PostgreSQL database
7. Install pgAdmin4

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
django-admin startproject SecurePortals --template=https://github.com/SecurePortals/SecurePortals/archive/master.zip
```

>Which should create a new folder in your home directory called SecurePortals. This is the root folder for our project and everything we do will go into this folder. 

## Set Up PyCharm interpreter

>So now we can set up PyCharm so it can point to the right version of Python, so we can run some setup scripts. Open PyCharm, select the SecurePortals folder we just created as our project folder, and follow this path from the toolbar on the top:

>       PyCharm > Preferences > Project: SecurePortals > Project Interpreter > The gear on the right side of the window
>       > System Interpreter > and look for /usr/local/bin/python3.6

>Hit okay, and let's get our environment going.

## Create PostgreSQL Database

>Whew! Almost there. We now will dive into creating our database.

## Quck note on SQL

>SQL stands for Structured Query Language, and is a very popular languaged used to interact with Relational Database Management Systems (RDMS). A RDMS is basically a database composed of tables, which each have a unique 'Primary Key' which identifies each record, and often has a 'Foreign Key' which comes from the 'Primary Key' from another table. This is where the 'relation' comes from, and it connects the data that exists in one table, to another. 

>So we have to first initialize PostgreSQL, so that it will launch whenever we start up the computer (This command should only be run once):

```bsh
pg_ctl -D /usr/local/var/postgres start && brew services start postgresql
```

>Then we need to engage in the instance of PostgreSQL that we have running, and enter some code:

```bsh
createdb
```
```bsh
psql -h localhost
```

>And now we should see something that looks like (except instead of joelherd you should see your own admin/login name):

```bsh
Joels-MacBook-Pro:~ joelherd$ psql -h localhost
psql (10.3)
Type "help" for help.

joelherd=# 
```

>We are now inside PostgreSQL! This is super great. We're going to kick off the following commands, and we're going to have a database!

```bsh
CREATE DATABASE dev_db;
CREATE DATABASE eval_db;
CREATE DATABASE test_db;
CREATE DATABASE prod_db;
CREATE ROLE dev_dba WITH LOGIN PASSWORD 'devdba1337';
CREATE ROLE prod_dba WITH LOGIN PASSWORD 'proddba1337';
GRANT ALL PRIVILEGES ON DATABASE dev_db TO dev_dba;
GRANT ALL PRIVILEGES ON DATABASE eval_db TO dev_dba;
GRANT ALL PRIVILEGES ON DATABASE test_db TO prod_dba;
GRANT ALL PRIVILEGES ON DATABASE prod_db TO prod_dba;
```

>If you notice, the sytax we're using in these commands is different then the syntax we used earlier, and that's because we're no longer coding in Bash, but instead in SQL! Cool stuff.

>Confirm your tables and users exist by entering:

```bsh
\list
\du
```

>And when you're ready to quit:

```bsh
\q
```

>To complete this step, we need to scrap the database we made under our name, which in my case is joelherd:

```bsh
dropdb 'joelherd'
```

## Install pgAdmin4

>[Install pgAdmin4](https://www.postgresql.org/ftp/pgadmin/pgadmin4/v3.0/macos/)

>pgAdmin4 is the software we'll use to look at our databases with a User Interface (UI), making it easier for us to understand the data in the database. 

## Setup up Django Environment to point to PostgreSQL database

>Okay this is the last segment for this bit, and then we can move on from setup setup setup setup... And get some work going!

>To be continued...

