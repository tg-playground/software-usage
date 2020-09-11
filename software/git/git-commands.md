# Git Commands

Content

- Common Operations
- Initialize a Git Repository
- Versions
- Branches

## Common Operations

Working Directory (Workspace)

```shell
# get source code from remote repository
git clone <file_path>

# Switch to a version of repository
git log
git checkout <commit_hash>

# Switch to a branch
git branch
git checkout {branch_name}
git checkout -

# check your changes
git status
git diff

# remove new changes(not git add)
git checkout .
git restore .
```

Staging Area (Index Stage), (Staged)

```shell
# Add changes to the staging area
git add <file_path>
git add .
git add -A

# reset `git add`
git reset <file_path>
git restore --staged <file_path>

# stash
# to record the current state of the working directory
git stash (same with git stash push)
# list statsh
git stash list
# show difference
git stash show
# restore from stash
git stash apply
# Remove a single stashed state from the stash list and apply it on top
git stash pop
# Remove a single stash entry from the list of stash entries.
git stash drop [-q|--quiet] <stash_id>
# Remove all the stash entries
git stash clear
```

Local Git Directory (Local Repository) (Committed)

```shell
# commit to local repository
git commit <file_path>
git commit -m "<commit_message>"
git commit -am "<commit_message>"

# reset `git commit`
git reset HEAD~1

# merge multiple commits to one commit
git rebase -i <commit_hash>
git rebase -i HEAD~<before_latest_commit_number>

# reset `git rebase`
git rebase --abort
```

Remote Git Directory (Pushed)

```shell
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
```



## Initialize a Git Repository

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



## Versions

### Checkout HEAD version and Remove Local Uncommit Modify

```shell
git checkout HEAD .
```

### Getting hashes for the previous versions

```shell
git checkout <commit_hash>
```

### Undo Detached (Returning to the latest version in the master branch)

```shell
git checkout master
```

### View Specified Version File

```shell
git show <commit_hash>:/path/to/file
```



## Branches

```shell
# list
git branch
git branch -a
# create
git branch {new_branch_name}
git checkout -b {new_branch_name}
# delete
git branch -d {branch_name}
# switch
git checkout {branch_name}
git checkout -
```

