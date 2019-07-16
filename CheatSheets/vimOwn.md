---
title: Vim selected short cuts
---
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

**Vim plugings**  
Install vim-plug and follow instructions

**VIM in Atom**  
- Load the vim-mode-plus package and the keystroke package.
Atom -> Settings -> Keybindings and write:  
'atom-text-editor.vim-mode-plus.insert-mode':
  'j k': 'vim-mode-plus:activate-normal-mode' # jk to escape
