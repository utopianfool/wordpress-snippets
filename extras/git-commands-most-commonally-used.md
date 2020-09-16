# Git Commands Most Commonally Used

## Set Up

### Create a new repository

```

git clone username@host:/path/to/repository
cd harris.hub
touch README.md
git add README.md
git commit -m "add README"
git push -u origin master

```

### Push an existing folder

```

cd existing_folder
git init
git remote add origin username@host:/path/to/repository
git add .
git commit -m "Initial commit"
git push -u origin master

```

### Push an existing Git repository

```

cd existing_repo
git remote rename origin old-origin
git remote add origin username@host:/path/to/repository
git push -u origin --all
git push -u origin --tags

```

### List the files you've changed and those you still need to add or commit

```

git status

```

### List all currently configured remote repositories

```

git remote -v

```

# Always Pull

### Fetch and merge changes on the remote server to your working directory

```

git pull

```

# Branches

Note: Remember to change to the branch before starting to work. ie check you are not in master or develop before starting to work on a branch.

### Create a new branch and switch to it

```

git checkout -b <branchname>

```

### Delete branch

```

git branch -d <branchname>

```

### Push branch to remote repository

```

git push origin <branchname>

```

# Merge

### Switch to branch you want to merge into

```

git checkout <branchname>

```

### Merge branch into main branch

```

git merge --no-ff <branchname>

```


# Drop local changes and get latest history

```

git fetch origin

git reset --hard origin/master

```


REF [Atlassian](https://confluence.atlassian.com/bitbucketserver/basic-git-commands-776639767.html)