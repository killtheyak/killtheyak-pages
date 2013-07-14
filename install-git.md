title: Install and configure Git
updated: 2013-07-14 16:46:00
os: [macosx]
tags: [git]
deps: [install-homebrew]
contributors: ["http://www.github.com/sloria"] 


```bash
# MacOSX-specific instructions
$ brew update
$ brew install git
```

```bash
# If you get an error:
# `Warning: /usr/bin occurs before /usr/local/bin`
# Then add the following to your shell profile (.bash_profile, .zshrc, etc.)
export PATH="/usr/local/bin:/usr/local/sbin:~/bin:$PATH"
```

```bash
# Make sure you are using the right git binary
$ which git
# should be "/usr/local/bin/git"
```

```bash
# Configure git with your name and email
$ git config --global user.name "Django Reinhardt"
$ git config --global user.email "man_with_guitar@hotmail.com"
```
