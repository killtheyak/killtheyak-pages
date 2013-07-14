title: Add color to my Terminal
updated: 2013-07-14 17:06:00
description: Let's make our `ls` and `grep` colorful.
os: [macosx]
tags: []
deps: [install-homebrew]
contributors: ["http://www.github.com/sloria"] 

## Bash 

```bash
# If you're using the bash shell, add the following to your 
# ~/.bash_profile file.

# ~/.bash_profile
# Colorful ls and grep
export CLICOLOR=1
export GREP_OPTIONS='--color=auto'
source "`brew --prefix grc`/etc/grc.bashrc"
```

## Zsh

```bash
# Another simple option is to use oh-my-zsh which comes with
# many different themes out of the box, as well as the added 
# functionality of the zsh shell

# Check out the project here: https://github.com/robbyrussell/oh-my-zsh

# Install zsh like so:
$ curl -L https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh | sh
```

Then change your `ZSH_THEME` setting in `~/.zshrc`.

```bash
# ~/.zshrc

ZSH_THEME="nanotech"

# Available themes here: https://github.com/robbyrussell/oh-my-zsh/wiki/themes
```
