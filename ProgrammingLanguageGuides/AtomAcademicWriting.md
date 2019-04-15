---
title: Documentation for using Atom and Pandoc
---

# Pandoc
To use Pandoc to convert to pdf, you need the package platformio-ide-terminal.
This allows to use the terminal inside of Atom. Once installed, it can be called with the command Ctrl-\`.

These are the commands for using pandoc. Call the commands in the terminal.

### pandoc markdownfilename.md -s -o view.pdf
Creates a pdf called view.pdf from the file markdownfilename.md.  
Option -s for standalone and option -o for output.


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
