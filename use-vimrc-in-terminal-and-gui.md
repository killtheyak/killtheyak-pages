title: Use the same vimrc for terminal and gui
updated: 2013-07-15 00:00:00
description: If you like to use Vim in the Terminal and within varoius GUI's (Macosx
and Linux), as I do, here is parts of my .vimrc file that help to make this happen.
os: [macosx, windows, linux]
tags: [vim, gvim, macvim]
deps: []
contributors: ["http://www.github.com/gcman105"] 

##Dropbox is the glue

If you keep your .vimrc and .vim folder on **Dropbox** and then symlink into your
home directory, you are able to use **Vim** on multiple computers.

##Fonts and colors

The first snippet from my .vimrc file, shows howto test for the varoius
environments.

```vimrc
"Set the color scheme.
set background=dark
if has("gui_running")    
  let base16colorspace=256
  colorscheme base16-tomorrow
  if has("gui_macvim")
    set guifont=Source\ Code\ Pro:h12
    set mouse=a
  else
    set guifont=Source\ Code\ Pro\ 10
    set mouse=c
  end
else
  colorscheme solarized
  set mouse=c
end
```

##Use a .vimlocal on each computer

Store a file for each system in **Dropbox** and symlink .vimlocal to it.

On **Dropbox** I have:

* `.vimlocal_t430`
* `.vimlocal_mm`
* `.vimlocal_mackbook`

Then symlink .vimlocal in your home folder to the appropriate one.

The snippet below is from the very bottom of my .vimrc file.

```vimrc
source $HOME/.vimlocal
```
##Sample .vimlocal

*I try to keep my .vimlocal file really small.*

```vimrc
"Set the initial window size
set lines=43
set columns=189
```

Here is a (Gist of gcman105's .vimrc file)[https://gist.github.com/gcman105/5821422]

