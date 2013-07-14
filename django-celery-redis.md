title: Use Celery in Django with a Redis backend
updated: 2013-07-13
description: Celery is a distributed task queue for Python that allows you to run computationally expensive code asynchronously. Here's how to integrate Celery in a Django project, using Redis for the backend service.
os: [macosx, linux]
tags: [python, django]
deps: [install-homebrew]
contributors: ["http://www.github.com/sloria"] 

First, install redis:

```bash
# On MacOSX with homebrew
$ brew install redis

# On Linux
$ wget http://download.redis.io/redis-stable.tar.gz
$ tar xvzf redis-stable.tar.gz
$ cd redis-stable
$ make
```

Then, add the following to your requirements file:

```
# requirements.txt
celery-with-redis
django-celery
```

Install the new requirements:

```bash
$ pip install -r requirements.txt
```

Add the following to setup.py:

```python
# settings.py
import djcelery
djcelery.setup_loader()
...

# Add djcelery to installed apps
INSTALLED_APPS = [
    ...
    'djcelery',
    ...
]

# Celery settings
BROKER_URL = 'redis://localhost:6379/0'
CELERY_RESULT_BACKEND = 'redis://localhost:6379/0'
```

Create the database datatables:

```bash
# If you're using South:
$ python manage.py migrate djcelery
# otherwise:
$ python manage.py syncdb
```

Now to start your redis server and a celery worker.

```bash
# Start the redis server
$ redis-server
# In a new terminal window/tab, start a celery worker
$ python manage.py celeryd worker -E
# In ANOTHER terminal window/tab, enable the Django Celery monitor
# so that you can manage your tasks from your admin page
$ python manage.py celerycam
```

You are now ready to run Celery tasks. 

Tasks can be defined like so:

```python
# tasks.py (in one of your apps)
from celery import task

@task()
def add(x, y):
    return x + y
```

```python
# In some other file (such as in views or models)
from myapp.tasks import add

add.delay(2, 2)  # Asynchronous addition--Huzzah!
```

See also:

- [Celery home page](http://celeryproject.org/)
- [First steps with Django - Celery Project](http://docs.celeryproject.org/en/latest/django/first-steps-with-django.html)
- [Redis home page](http://redis.io/)


