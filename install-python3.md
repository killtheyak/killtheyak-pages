title: Install Python 3
updated: 2013-07-13
os: [macosx]
deps: [install-homebrew]
tags: [python]
contributors: ["http://www.github.com/sloria"]

```bash
# Mac instructions
$ brew install python3
# You should now be able to run:
$ python3
# To open up the Python 3 REPL
```

If it still doesn't work, run `$ brew doctor`. You may have to make the proper symlinks with:

```bash
$ brew link python3
```
