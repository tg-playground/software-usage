# Git Commands

Content

- Common Operations
- Cancel Local Operations
- Versions
- Branches

## Common Operations

```shell
# get source code from remote repository
git clone <file_path>

# check your changes
git status
git diff

# reset new changes(not git add)
git checkout .

# Add changes to the staging area
git add <file_path>
git add .
git add -A

# reset `git add`
git reset <file_path>

# commit to local repository
git commit <file_path>

# reset `git commit`
git reset HEAD~1

# push to remote repository
git push
git push -u origin master

# revert the specified pushed version
git revert <commit_hash>

# fetch or pull. update changes from remote repository
git fetch origin master:temp
git diff temp
git merge
git pull

# Switch to a version of repository
git log
git checkout <commit_hash>
```

create new local repository

```shell
git init
git add README.md
git commit -m "first commit"
git remote add origin https://github.com/tagnja/test.git
git push -u origin master
```

push new local repository

```shell
git remote add origin https://github.com/tagnja/test.git
git push -u origin master
```



## Cancel Local Operations

### Cancel local `git add`

```shell
git reset <file path>
```

### Cancel Local `git commit`

```shell
git reset HEAD~1
```



## Versions

### Checkout HEAD version and Remove Local Uncommit Modify

```shell
git checkout HEAD .
```

### Getting hashes for the previous versions

```shell
git checkout <commitHash>
```

### Undo Detached (Returning to the latest version in the master branch)

```shell
git checkout master
```

### View Specified Version File

```shell
git show <commitHash>:/path/to/file
```



## Branches

```shell
# list
git branch
git branch -a
# create
git branch {new branch name}
git checkout -b {new branch name}
# delete
git branch -d {delete branch name}
# switch
git checkout {branch name}
git checkout -
```

