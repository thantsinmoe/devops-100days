Task :
1. There are two branches in this repository, master and feature. One of the developers is working on the feature branch and their work is still in progress, however they want to merge one of the commits from the feature branch to the master branch, the message for the commit that needs to be merged into master is Update info.txt. Accomplish this task for them, also remember to push your changes eventually.

# Check branch & log
cd /usr/src/kodekloudrepos/games/
git branch
git log --oneline

# Switch to master branch & cherry-pick 
git checkout master
git cherry-pick 701b3f5
git push