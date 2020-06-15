# Git Problem Solving

### Question: 

Filename too long in Git for Windows

### Solutions:

Solution 1: 

```
git config core.longpaths true
```

This answer suggests not to have such setting applied to the global system (to all projects so avoiding `--system` or `--global` tag) configurations. This command only solves the problem by being specific to the current project.

Reference: [Filename too long in Git for Windows](https://stackoverflow.com/questions/22575662/filename-too-long-in-git-for-windows)

Question: 

GitHub: Clone succeeded, but checkout failed

Solutions: 

Solution 1: 

```
git reset
git checkout *
# if checkout fail
git stage
```

