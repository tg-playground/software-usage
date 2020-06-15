# Git Workflow



Owner

```shell
# create a new branch
$ git checkout -b new_feature
# work with your branch
$ git add <some-file>
$ git commit -m ""
$ git push origin new_feature
# pull request to master
$ git checkout master
$ git pull 
or 
$ git fetch origin master:temp 
$ git diff temp
$ git merget temp

$ git pull origin new_feature
$ git push origin master
```





### Workflow

[Git Feature Branch Workflow -Bitbucket](https://www.atlassian.com/git/tutorials/comparing-workflows/feature-branch-workflow)

[Gitflow Workflow - Bitbucket](https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow)

[GitHub Standard Fork & Pull Request Workflow - GitHub](https://gist.github.com/Chaser324/ce0505fbed06b947d962)

### Others

[Creating a pull request from a fork](https://help.github.com/en/articles/creating-a-pull-request-from-a-fork)





### References

