Task:
1. Merge the feature branch into the master branch`, but before pushing your changes complete below point.

2. Create a post-update hook in this git repository so that whenever any changes are pushed to the master branch, it creates a release tag with name release-2023-06-15, where 2023-06-15 is supposed to be the current date. For example if today is 20th June, 2023 then the release tag must be release-2023-06-20. Make sure you test the hook at least once and create a release tag for today's release.

3. Finally remember to push your changes.

# Git merge to master branch
cd /usr/src/kodekloudrepos/cluster
git checkout master
git merge feature

# Create post-update hook
cp /opt/cluster.git/hooks/post-update.sample /opt/cluster.git/hooks/post-update
vi /opt/cluster.git/hooks/post-update
    # add script
        #!/usr/bin/env bash
        echo "Starting post-update hook"
        for refname in "$@"; do 
        echo "refname is $refname"
        if [[ "$refname" == "refs/heads/master" ]]; then
            echo "Creating tag for today's release"
            TODAY="$(date +%F)"
            # Tag the commit pointed by refs/heads/master
            git tag -a "release-$TODAY" -m "Release for $TODAY" "$refname"
            echo "Tag release-$TODAY created at $(git rev-parse --short $refname)"
        fi
        done

        echo "Finished post-update hook"
        exit 0

# Push master branch and check git tag
git push origin master
git tag