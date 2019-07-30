---
title: Documentation for using Atom and Pandoc
---
# Shortkeys  

- `Alt-\` toggles tree view and A, M or delete can be used to add, move or delete files
- Ctrl-k + Ctrl-arrow allows to focus between different editors
# Pandoc
To use Pandoc to convert to pdf, you need the package platformio-ide-terminal.
This allows to use the terminal inside of Atom. Once installed, it can be called with the command Ctrl-\`.

These are the commands for using pandoc. Call the commands in the terminal.

### pandoc markdownfilename.md -s -o view.pdf
Creates a pdf called view.pdf from the file markdownfilename.md.  
Option -s for standalone and option -o for output.  
Add --toc for table of contents

# Markdown


### Beginning a document  
Between triple lines (---) write the title and author, as follows:  
\-\-\-  
title: Something  
author: myself  
\-\-\-  

### Lists  
Do two enters and - (slash). Looks like this:

- First
- Second

### Small but useful
To do a single linebreak, use two spaces and enter. To change paragraph, use two enters. A single enter doesn't do anything.

To write taken characters, use the escape character backslash \\.  
Known taken characters are:  
\-\-\-  
\`

# Using Git  
First install Git. It is required to work properly.  
On Git bash, write the following commands for set up:  
git config --global user.name "Napoleon Freitas Paajanen"  
git config --global user.email "napoleonfreitaspaajanen@gmail.com"  
currently using the following sites:  

Basics of git: https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository

Possibly in the future use "git-control" package for easier use.

# Latex
In order to use Latex commands, use double dollars \$\$. E.g.,  
$$ y \in R(A) $$
