Task: 
1. Project repository /opt/blog.git. This repo is cloned at /usr/src/kodekloudrepos on storage server.
   Create a new branch xfusion in /usr/src/kodekloudrepos/blog repo from master and copy the /tmp/index.html file (present on storage server itself) into the repo. Further, add/commit this file in the new branch and merge back that branch into master branch. Finally, push the changes to the origin for both of the branches.

# Create new branch
cd /usr/src/kodekloudrepos/blog/
git checkout -b xfusion

# Copy index.html file 
cp /tmp/index.html .
git add index.html
git commit -m "added index.html"

# Git megre to master branch
git checkout master
git merge xfusion

# Git push both branch
git push master
git checkout xfusion
git push -u origin xfusion