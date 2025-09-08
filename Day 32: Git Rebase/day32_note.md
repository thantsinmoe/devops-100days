Task :
1. One of the developers is working on feature branch and their work is still in progress, however there are some changes which have been pushed into the master branch, the developer now wants to rebase the feature branch with the master branch without loosing any data from the feature branch, also they don't want to add any merge commit by simply merging the master branch into the feature branch. Accomplish this task as per requirements mentioned.

3. Also remember to push your changes once done.

# Check git branch & log
cd /usr/src/kodekloudrepos/cluster
git branch
git log --oneline

# Git fetch & rebase from master branch
git fetch origin master
git rebase origin/master
git log --oneline
git push -u origin feature -f

