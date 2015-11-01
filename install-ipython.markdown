title: Install IPython Notebook
updated: 2014-05-23 00:00:00
description: A whip-fast guide to getting started with IPython Notebooks, the best persistent-state REPL out there
os: [macosx]
tags: [python, scientific]
deps: [use-virtualenvwrapper]
contributors: ["http://www.github.com/rachelkelly"] 


Create your virtualenv. If you are using virtualenvwrapper, run:

```sh
$ mkvirtualenv ipy
```

This can be any environment name you choose.  I call mine `ipy` for  brevity.  IPython has a bunch of dependencies and it's nice to have them all in ONE place rather than globally throughout your machine.

Then use `pip` to install the following.

- `jinja2`  
- `pyzmq`  
- `tornado`  

```sh
$ workon ipy
$ pip install jinja2 pyzmq tornado ipython
```

Then, to run a local instance of IPython Notebook: 

```sh
$ ipython notebook
```
