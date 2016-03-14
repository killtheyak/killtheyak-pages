title: Serve a Flask App with uWSGI and nginx
updated: 2013-09-01 09:53:00
os: [macosx, windows, linux]
deps: []
tags: [python, flask]
contributors: ["http://www.github.com/mplewis"]
description: I've been having trouble with serving a Flask app via uWSGI and nginx, so I thought I'd put together some of the basics to help out others.

How this shit works
-------------------

* Flask is managed by `uWSGI`.
* `uWSGI` talks to `nginx`.
* `nginx` handles contact with the outside world.

```
[SERVER] Flask <---> uWSGI <---> nginx <---> [YOUR AUDIENCE IRL]
```

When a client connects to your server trying to reach your Flask app: 

* `nginx` opens the connection and proxies it to `uWSGI`
* `uWSGI` handles the Flask instances you have and connects one to the client
* Flask talks to the client happily

Flask
-----

Write your app. Three things that matter:

1. Flask script filename (e.g. `server_dev.py`)
2. App name (e.g. if your Flask app says this: `myapp = Flask(__name__)`, your app name is `myapp`)
3. If you have `app.run()` in your application somewhere, MAKE SURE IT'S INSIDE THE FOLLOWING CHECK:  

``` python
if __name__ == '__main__':
    app.run()
```

OTHERWISE YOU WILL START ANOTHER WSGI SERVER ALONGSIDE YOUR uWSGI SERVER.  
You do NOT want this.

uWSGI
-----

There's at least two ways to get uWSGI talking to nginx:

* Connect the two via a TCP port
* Connect the two via a filesocket

Filesockets have issues with read/write and user permissions sometimes. These aren't hard problems but I'm too lazy to figure out these problems when there's an easier way to do it with simple TCP ports.

Here's a working uWSGI setup:  
* that communiates with a web server via port `4242`
* for file `server.py`
* with app name `myapp`

```
uwsgi --socket 127.0.0.1:4242 --module server --callab myapp
```

Note that this runs without a daemon and you probably want this daemonized in case it crashes. Try using [uWSGI in emperor mode](http://uwsgi-docs.readthedocs.org/en/latest/Emperor.html) or [supervisor](http://supervisord.org/).

nginx
-----

This is easy. Super easy.
Here's an `nginx` config that works with `uwsgi` on port `4242`:

```
server {
    listen       80;
    server_name  [YOUR SERVER NAME.com];

    location / { try_files $uri @[YOUR APP NAME]; }
    location @[YOUR APP NAME] {
        uwsgi_pass 127.0.0.1:4242;
        include uwsgi_params;
    }
}
```

DON'T FORGET TO RESTART YOUR NGINX SERVER BEFORE YOU START WHINING ABOUT YOUR SERVER NOT WORKING PROPERLY

If you have any questions
-----

email me: matt@mplewis.com
