title: Install Coffeescript
updated: 2013-07-14 19:36:00
os: [macosx]
tags: [coffeescript]
deps: [install-homebrew]
contributors: ["http://www.github.com/sloria"] 

```bash
# Mac-specific instructions
# Install node
$ brew update 
$ brew install node
```

Add the node directory to your `PATH`.

```bash
# In you shell profile (.bash_profile, .zshrc, etc.), add this line
export PATH=/usr/local/share/npm/bin:$PATH
```

```bash
# Install coffee (notice the dash)
npm install -g coffee-script
```

You now have Coffeescript installed.

```bash
# To compile a file
coffee -c cupofjoe.coffee
# Watch mode--compile a file whenever it is changed
coffee -cw cupofjoe.coffee
```

See also:

- [Coffeescript.org][Coffeescript]

[Coffeescript]: http://coffeescript.org/
