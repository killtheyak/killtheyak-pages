title: Use PostgreSQL with Flask or Django
updated: 2015-01-17
description: A quick guide to get started using Postgres with a Flask or Django app.
os: [macosx, windows, linux]
tags: [python, django, flask]
deps: []
contributors: ["http://www.github.com/sloria",
            "https://github.com/bgschiller", 
            "https://github.com/tristaneuan",
            "https://github.com/TayHobbs"]

* Updated 2015-01-17: Update paths to `psql` binary in Postgres.app. Thanks @TayHobbs.
* Updated 2014-05-18: Fix `createdb` listing. Thanks @trastaneuan. Also fixed the footnote re: adding Postgres.app's binaries to `$PATH`.
* Updated 2014-03-29: Fix `createuser` and `createdb` commands. Thanks @bgshiller.

## Install Postgres

First, download and install Postgres for your OS [here](http://www.postgresql.org/download/).

Sidenote for MacOSX users: I have found [Postgres.app](http://postgresapp.com/) to be the simplest option[^path-warning]. Just download and run the app.

```bash
# check that you successfully installed postgres
$ which psql
/Applications/Postgres.app/Contents/Versions/9.4/bin/psql
```
## Create a new user and a database

```bash
# Create a new user
$ sudo -u postgres createuser -s $USER
Enter password for new role:
Enter it again:
Shall the new role be a superuser? (y/n) n
Shall the new role be allowed to create databases (y/n) y
Shall the new role be allowed to create more new roles? (y/n) n

# Create a new database
$ createdb -U $USER --locale=en_US.utf-8 -E utf-8 -O $USER yournewdb -T template0
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
app.config.from_pyfile('config.py')
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

[^path-warning]: **IMPORTANT**: If you use Postgres.app, make sure to add its binaries directory to your path. You can do so by adding `export PATH="/Applications/Postgres.app/Contents/Versions/9.5/bin:$PATH"
` to your `.bashrc` (or `.zshrc`, `.bash_profile`, etc.)
