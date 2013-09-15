title: Install Homebrew
updated: 2013-07-15 00:00:00
os: [macosx]
description: Homebrew's tagline is "the missing package manager for OS X". It is by far the best package manager for Mac available and will save you hours of yak-shaving.

Works on all MacOSX >= 10.5.

*Updated 2013-09-15*: Add instructions for inserting into `PATH`.

```bash
# In your Mac Terminal, run:
$ ruby -e "$(curl -fsSL https://raw.github.com/mxcl/homebrew/go)"
```

Then, make sure `/usr/local/bin` is at the top your `PATH` environment variable.

```bash
# In your ~/.bashrc, ~/.bash_profile, or ~/.zshrc (for zsh users)
# ...
export PATH=/usr/local/bin:$PATH
```

Run `brew doctor` and try to fix as many of the listed issues as possible.

```bash
$ brew doctor
```

Thats it!

See also:

* [Homebrew][]

[Homebrew]: http://mxcl.github.io/homebrew/