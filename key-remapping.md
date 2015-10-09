NOT YET FINISHED!!!

# Remapping keys on most Linux distros
Remapping keys on most Linux distros, including Fedora, seems to be a lot more difficult than it needs to be. There's a lot of confusing and conflicting information out there. This guide is going to cover the steps I took to thoroughly customize my keyboard.

## Introduction
First of all, let's learn some terminology. X Window System (also known as X11 or X) is the standardized system used for managing windows on pretty much all Linux distros, including Fedora. X.Org Server (maintained by the X.Org Foundation) is the implementation of X11 that your machine uses. You might also stumble upon information about XFree86, which was the standard implementation of X11 until X.Org replaced it in 2004 (but there's still a few relics of it floating about in X.Org).

There are two tools that are used for keyboard configuration: XKB (X KeyBoard extension) and xmodmap. They both still work, but xmodmap is really old and falling out of use. You theoretically are supposed to be able to create a file `~/.Xmodmap` to reconfigure your key mappings, but current versions of X.Org disable this functionality. There are ways to try to force xmodmap to be used, but really, XKB is the best route to take.

## Create your custom XKB directory
Presumably, you'll want to do this re-mapping just for yourself, so I'll assume you want your xkb settings to go in _~/.xkb_ (if you really want your keyboard to apply system-wide, you can do roughly the same stuff this guide describes, but in _/usr/share/X11/xkb_ instead). For the most basic remapping, you'll need two directories inside of _.xkb_: _keymap_ and _symbols_. Here's a quick command to make those directories for you:

```
mkdir -p ~/.xkb/keymap ~/.xkb/symbols
```

## Pick your key bindings
To remap your keys, you'll need an xkb_symbols file. Edit _~/.xkb/symbols/local_ in your favorite text editor.

UNFINISHED!!!


## Make the system use your custom bindings
Now that you have a place for your XKB settings to go, you'll need to make the X server install them when it starts. To do this, you should add the following command to your _~/.xinitrc_ file ([derived from this link](http://www.vinc17.org/unix/xkb.en.html)):

```
setxkbmap -print | \
  sed -e '/xkb_symbols/s/"[[:space:]]/+local&/' > $HOME/.xkb/keymap/custom
xkbcomp -w0 -I$HOME/.xkb -R$HOME/.xkb keymap/custom $DISPLAY
```

This command retrieves your pre-existing XKB settings, then filters through them and adds a rule to include your custom symbols file. Once the keymap config file is created at _~/.xkb/keymap/custom_, it is compiled and applied to the currently running X server display. (Note that both these commands require you have the package `xorg-x11-xkb-utils` installed. You probably already have it, but if not just get it with Yum.)
