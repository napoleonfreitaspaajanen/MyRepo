---
title: Command line and Tmux configurations
---

# Terminal  
set up vim copy-paste with a X terminal using the instructions in vimcopypaste picture.  

Set up vim and tmux integration with vim-tmux-navigator plugin for vim (follow instructions)

# Basics  of tmux
exit tmux with C-a :exit-session  

# Configuration of tmux
The settings are changed in .tmux.conf file.  

```
# set C-a as command  
unbind C-b
set-option -g prefix C-a
bind-key C-a send-prefix
```
