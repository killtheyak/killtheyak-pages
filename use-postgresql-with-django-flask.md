title: Use PostgreSQL with Flask or Django
updated: 2013-07-26 9:00:00
description: A quick guide to get started using Postgres with a Flask or Django app.
os: [macosx, windows, linux]
tags: [python, django, flask]
deps: []
contributors: ["http://www.github.com/sloria"] 

## Install Postgres

First, download and install Postgres for your OS [here](http://www.postgresql.org/download/).

Sidenote for MacOSX users: I have found [Postgres.app](http://postgresapp.com/) to be the simplest option[^brew-warning]. Just download and run the app.

```bash
# check that you successfully installed postgres
$ which psql
/Applications/Postgres.app/Contents/MacOS/bin/psql
```
## Create a new user and a database

```bash
# Create a new user
$ createuser -U postgres yourusername -P
Enter password for new role:
Enter it again:
Shall the new role be a superuser? (y/n) n
Shall the new role be allowed to create databases (y/n) y
Shall the new role be allowed to create more new roles? (y/n) n

# Create a new database
$ createdb -U yourusername -E utf8 -O yourusername yournewnewdb -T template0
```

## Set up Postgres with Flask or Django

```bash
# install psycopg2
$ pip install -U psycopg2
# If using SQLAlchemy
$ pip install Flask-SQLAlchemy
```

### Flask

```python
# Flask config.py
SQLALCHEMY_DATABASE_URI = "postgresql://yourusername:yourpassword@localhost/yournewdb"
```
```python
# Flask app.py
from flask import Flask
from flask.ext.sqlalchemy import SQLAlchemy

app = Flask(__name__)
app.config.from_pyfile(config.py)
db = SQLAlchemy(app)
```

### Django

```python
# Django settings.py
DATABASES = {
    'default': {
        'ENGINE': 'django.db.backends.postgresql_psycopg2',
        'NAME': 'yournewdb',
        'USER': 'yourusername',
        'PASSWORD': 'yourpassword',
        'HOST': 'localhost',
        'PORT': '5432',
}
```

That's it! Go ahead and write your models.

See also:

- [Postgres home](http://www.postgresql.org/)
- [Postgres.app](http://postgresapp.com/)

For viewing/managing your databases:

- [pgAdmin](http://www.pgadmin.org/) (Cross-platform)
- [Induction](http://inductionapp.com/) (MacOSX)

[^brew-warning]: **IMPORTANT** note for Homebrew users: The scripts added to your path by Postgres.app may conflict with your Homebrew installations. If this is a case, one quick fix is to add aliases that point to the Postgres.app binaries. For example: `alias psql="/Applications/Postgres.app/Contents/MacOS/bin/psql"`

