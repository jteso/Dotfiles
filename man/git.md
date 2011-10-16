## BASIC COMMANDS
git branch #which branches i have, and where i am
git checkout <BRANCH-NAME>	#switch
git checkout -b <BRANCH-NAME>  #create
git branch -D <BRANCH_NAME>	#delete
git commit -am "Comment for commit" #commit
git status #check the working copy
git mv fileorigen filedest
mate .git/config #check git configuration
git diff <sha1-old>..<sha1-new> -- <file> #see diff of one file
git rm --cached #remove a file that has been commited
git push github master

## HOW-TO REBASE
### integrate the latest upstream changes into your master
git checkout master
git pull
### change to your topic branch
git checkout my_topic_branch
### do the rebase
git rebase master
