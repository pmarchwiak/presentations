<!---
Presentation done for team 
Meant to be used with https://github.com/adamzap/landslide
-->

# tmux

---

# Overview

- What is it?
- Installation / Configuration
- Basic Usage

---

# Terminal Multiplexers

<img src="http://tmux.sourceforge.net/tmux5.png" height="500">

---

# Terminal Multiplexers

Wikipedia:

>A terminal multiplexer is a software application that can be used to multiplex several virtual consoles, allowing a user to access multiple separate terminal sessions inside a single terminal window or remote terminal session. It is useful for dealing with multiple programs from a command line interface, and for separating programs from the Unix shell that started the program.

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

# tmux!

- Started in 2007
- 

---

# Installation

On Mac use [`homebrew`](http://mxcl.github.com/homebrew/):

    marchwiakmd$ brew install tmux

---

# Configuration

Unlike `screen`, `tmux` has nice defaults.

Some recommended tweaks to add to your `~/.tmux.conf`:
    
    # Use 1 as the first index
    set -g base-index 1                                                                                                                            
    
    # Replace C-b as the default, use what screen does                                                                                                                                                                              
    set-option -g prefix C-a                                                                                                                                                          
                                                                                                                                                                                   
    # Just click it                                                                                                                                                          
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

# Usage

Start up tmux:

    marchwiakmd$ tmux
    
Attach to existing session:

    marchwiakmd$ tmux attach
   
---
 
# Usage - Window Management

Create a new window: **C-a c**

> Note: C-a c means hold the control key and press `a`, let go, then press `c`

Switch to the next window: **C-a n**

Switch to the previous window: **C-a p**

Switch to window # 2: **C-a 2**

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
 
