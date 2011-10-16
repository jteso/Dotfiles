ronn(1)
==================================================
## SYNOPSYS
 Create man pages with ruby

## WORKFLOW
### Create a man folder for your gem
mkdir man
### Generate a man page
ronn README.md > man/rubymanpage.1 && gzip man/rubymanpage.1
### Read a man page
man man/rubymanpage.1.gz

## SEE ALSO
gem-man command

