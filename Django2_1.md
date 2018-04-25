## The nature of dealing with software
>Now this is where things get a bit tricky. Our goal is to accomplish the following:
1. Install Pycharm
2. Install Django
3. Install Postgres
4. Set up Pycharm Interpreter
5. Create PostgreSQL Database (run my script)
6. Setup up Django Environment to point to PostgreSQL database




```bsh
pip3 install Django==2.0.4
```

```bsh
brew install postgresql
```

```bsh
pip3 install psycopg2
```

```bsh
nano /usr/local/var/postgres/postgresql.conf
```

```bsh
pg_ctl -D /usr/local/var/postgres start && brew services start postgresql
```

```bsh
django-admin startproject SecurePortals
```
