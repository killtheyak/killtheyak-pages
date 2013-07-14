title: Use virtualenv + virtualenvwrapper with Python
updated: 2013-07-14
description: Virtualenv allows you to make isolated working copies of Python so that you can work on a specific project without affecting other projects. Virtualenvwrapper provides commands that make it simple to create and manage your virtual environments.
os: [macosx, linux]
tags: [python]
deps: [install-python]
contributors: ["http://www.github.com/sloria"] 

Install the packages.

```bash
$ pip install virtualenv
$ pip install virtualenvwrapper
```


Open your shell's profile config (e.g. `.bash_profile`, `.bashrc`, or `.zshrc`). This is usually located in your home directory.

Then add the following:

```bash
# ~/.bash_profile

# Enable virtualenvwrapper 
VIRTUALENVWRAPPER_PYTHON=/usr/local/bin/python
export WORKON_HOME=~/Envs
source /usr/local/bin/virtualenvwrapper.sh
```

Create the folder for your virtual environments.

```bash
# Reload your profile
$ source ~/.bash_profile
# Create your env directory
$ mkdir -p $WORKON_HOME
```

Now, when you log in to a new shell session, you will be able to use virtualenvwrapper.

```bash
# Create a new virtualenv
$ mkvirtualenv my-fresh-environment
# List environments
$ lsvirtualenv
# Remove an environment
$ rmvirtualenv my-polluted-environment
```

See also:

- [Virtualenvwrapper docs](http://virtualenvwrapper.readthedocs.org/en/latest/) 
