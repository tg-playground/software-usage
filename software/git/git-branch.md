# Git Branch

### Creating a branch locally

List Branch

```
$ git branch
```

Create new branch

```
$ git branch <branch_name>
```

Switch to the new branch

```
$ git checkout <branch_name>
```

Commit the change to the new branch

```
$  git add .
$ git commit -m "Adding a change from the feature branch"
```

Switch back to the master branch

```
$ git checkout master
```

Push the feature branch to remote repository

```
$ git push origin <feature_branch>
```

### Branch Merge  to Master

```
$ git add .; git commit -m "Adding a change from the dev branch"; git push origin dev
$ git checkout master
$ git merge dev
```



### References

[1] [Branching a Repository](https://confluence.atlassian.com/bitbucket/branching-a-repository-223217999.html)

[2] [Git Branching - Basic Branching and Merging](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)