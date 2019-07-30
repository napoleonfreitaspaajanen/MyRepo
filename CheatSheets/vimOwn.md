---
title: Vim selected short cuts
---

# Tips and trics  
- In insert mode, Ctrl-o allows to do one command on normal mode


**Modifying many lines at once**
- C-V for visual block + Select lines + C-I for insert + write your things + leave insertion mode
- Copying form vim: Pres SHIFT and drag cursor over text, then press enter to copy.
**.vimrc file**
- You can modify how vim works with the .vimrc file in your home directory. Here is what you should write there:  
```bash
"imap keys"
imap jj <esc>
"Set numbers on left bar"
set number
"Allow scrolling"
set mouse=a
"Set indentation"
set autoindent "Keeps the indentation level as the previous line"

"Miscellaneous"
set ruler "show cursor on lower right corner"
set showcmd "shows the incomplete commands"
filetype plugin indent on "set filetype detection and some changes related to that"
```

**VIM in Atom**  
- Load the vim-mode-plus package and the keystroke package.
Atom -> Settings -> Keybindings and write:  
'atom-text-editor.vim-mode-plus.insert-mode':
  'j k': 'vim-mode-plus:activate-normal-mode' # jk to escape

**VIM in Windows**  
To be able to copy paste from system register with `"*p`, one must install VcXsrv that allows for graphical programs to be ran on ubuntu. More information in [link](https://superuser.com/questions/1291425/windows-subsystem-linux-make-vim-use-the-clipboard). Basically do the following:  

- Install VcXsrv  
- Run XLaunch and save the config to some file  
- put `export DISPLAY=localhost:0.0` to .bashrc file

# Plugins  
Download the plugin manager vim-plug so you can add plugins.
- :PlugInstall after setting a plug to install it.
- :PlugUpdate to update
- :PlugClean to remove stuff not used
**Syntax**  
syntastic allows for syntax checks. Some commands:  

- help Syntastic  
- SyntasticCheck  
- SyntasticReset
