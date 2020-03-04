# Git Commands

Content

- Common Operations
- Cancel Local Operations
- Versions
- Branches

## Common Operations

```shell
git clone <file path>
git status
git diff
git add <file path>
git add -A
git commit <file path>
git push
git push -u origin master
git fetch origin master:temp
git diff temp
git merge
git pull
git log
git checkout <commit hash>
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

