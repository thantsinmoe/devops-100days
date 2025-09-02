Task:
The xFusionCorp development team added updates to the project that is maintained under /opt/ecommerce.git repo and cloned under /usr/src/kodekloudrepos/ecommerce. Recently some changes were made on Git server that is hosted on Storage server in Stratos DC. The DevOps team added some new Git remotes, so we need to update remote on /usr/src/kodekloudrepos/ecommerce repository as per details mentioned below:

a. In /usr/src/kodekloudrepos/ecommerce repo add a new remote dev_ecommerce and point it to /opt/xfusioncorp_ecommerce.git repository.

b. There is a file /tmp/index.html on same server; copy this file to the repo and add/commit to master branch.

c. Finally push master branch to this new remote origin.

# Add new remote and point repository
cd /usr/src/kodekloudrepos/ecommerce/
git remote add dev_ecommerce /opt/xfusioncorp_ecommerce.git

# Copy file and git add, commit, push to master
cp /tmp/index.html .
git add index.html 
git commit -m "added index.html"
git push dev_ecommerce master

# Check changes in new repository
git --git-dir=/opt/xfusioncorp_ecommerce.git/ log --oneline