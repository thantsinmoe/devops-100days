Task : 
1. In /usr/src/kodekloudrepos/news git repository, revert the latest commit ( HEAD ) to the previous commit (JFYI the previous commit hash should be with initial commit message ).
2. Use revert news message (please use all small letters for commit message) for the new revert commit.

# Revert the latest commit
cd /usr/src/kodekloudrepos/news
git status
git revert HEAD -n 
git add .
git commit -m "revert news"