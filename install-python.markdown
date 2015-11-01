title: Install Python 2 and/or 3
updated: 2013-09-15 13:50:00
os: [macosx]
deps: [install-homebrew, install-mac-xcode-compilers]
tags: [python]
contributors: ["http://www.github.com/sloria"]

*Updated 2013-09-15*: Add Xcode compilers as a dependency.

```bash
# On Mac >= 10.5 with homebrew
$ brew update
## Install Python 2
$ brew install python
## Install Python 3
$ brew install python3
## Follow any instructions that appear after each brew install
```

Make sure to follow the instructions after each install. If you missed them, just run `brew info python` or `brew info python3`.

If it still doesn't work, try to fix *every* issue listed when you run `brew doctor`. 

```bash
# Is everything working?
$ brew doctor
# Listen to the doctor
```

If everything's working, you can run both Python 2 and Python 3 on the same system.

```bash
# Run Python 2
$ python
# Run Python 3
$ python3
# Install a Python 2 package
$ pip install some-package
# Install a Python 3 package
$ pip3 install some-package
```