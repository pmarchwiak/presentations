<!---
Meant to be used with https://github.com/adamzap/landslide
-->

# tmux

Patrick Marchwiak

October 2015

---

# Overview

- Huh?
- Installation / Configuration
- Basic Usage

---

# Terminal Multiplexers

<img src="https://tmux.github.io/ss-tmux2.png" height="500">

---

# Terminal Multiplexers

A terminal multiplexer is an application that can be used to multiplex several virtual consoles, allowing a user to access multiple separate terminal sessions inside a single terminal window or remote terminal session.


Useful for dealing with multiple programs from a CLI, and for separating programs from the Unix shell that started the program.

(From [Wikipedia](http://https://en.wikipedia.org/wiki/Terminal_multiplexer))

---

# GNU Screen

Has anyone used `screen`?

---

# GNU Screen

- Released in 1987
- Hard to configure
- Still missing basic features like vertical splits

![image](http://upload.wikimedia.org/wikipedia/en/3/33/Dn330.jpg)

---

# tmux


`tmux` is intended to be a modern, BSD-licensed alternative to programs such as GNU screen. Major features include:

- A powerful, consistent, well-documented and easily scriptable command interface.
- A window may be split horizontally and vertically into panes.
Panes can be freely moved and resized, or arranged into preset layouts.
- Interactive menus to select windows, sessions or clients.
- Change the current window by searching for text in the target.
- A clean, easily extended, BSD-licensed codebase, under active development.

(From [http://tmux.sourceforge.net/](http://tmux.sourceforge.net/))

---

# Installation

On Mac use [`homebrew`](http://mxcl.github.com/homebrew/):

    me@mbp:~$ brew install tmux

---

# Usage

Start up tmux:

    me@mbp:~$ tmux

Attach to existing session:

    me@mbp:~$ tmux attach

---

# Usage - Window Management

Create a new window: **C-a c**

> Note: C-a c means hold the control key and press `a`, let go, then press `c`

Switch to the next window: **C-a n**

Switch to the previous window: **C-a p**

Switch to window the 2nd window: **C-a 2**

Rename window: **C-a ,**  then type the new name, press Enter

---

# Usage - Panes


Split vertically: **C-a |**

Split horizontally: **C-a -**

Switch to pane on left: **C-a ←**

---

# Usage - Quitting

Detach from session: **C-a d**

Close window: **C-c**

Kill window (when not responding): **C-a &**

___

# Configuration

Unlike `screen`, `tmux` has nice defaults.

Some recommended tweaks to add to your `~/.tmux.conf`:

    # Use 1 as the first index
    set -g base-index 1

    # Replace C-b as the default, use what screen does
	set-option -g prefix C-a

    # Just click it (better mouse support)
	set-option -g mouse-select-pane on
    set-option -g mouse-select-window on
    set-option -g mouse-resize-pane on

---

# Configuration

    # Scroll your way into copy mode (scrollback buffer)
    # and select text for copying with the mouse
    setw -g mode-mouse on

    # Remove delay between prefix and command
    set -s escape-time 0

    # command sequence for nested tmux sessions
    bind-key a send-prefix

    # Fix wacky colors
    set -g default-terminal "screen-256color"

    # Use intuitive bindings for splitting panes
    bind | split-window -h
    bind - split-window -v

---

# Misc

- When used for session persistence on a server, tmux must be installed there.

- Plugins available at [https://github.com/tmux-plugins](https://github.com/tmux-plugins)

 - [tmux-resurrect](https://github.com/tmux-plugins/tmux-resurrect) persists your environment across system restarts.

- Copy and paste doesn't work correctlyin iTerm2. Hold Option when selecting text.
