# Git Commands

<h3 id="content">Content</h3>

- [git status](#gss)
- git log
- [git diff](#gdf)
- [git add](#gad)
- [git commit](#gct)
- [git reset](#grt)
- [git clean](#gcn)
- [git rm](#grm)
- [git checkout](#gct)
- [git clone](#gce)
- [git push](#gph)
- [git fetch, git merge](#gfh)
- [git pull](#gpl)



<h3 id="gss"># git status</h3>

> 查看暂存区

```shell
$ git status  //查看暂存区，未提交的文件
```

[`back to content`](#content)



<h3 id=""># git log</h3>

> 查看提交日志

```shell
$ git log
```



<h3 id="gdf"># git diff</h3>

> 比较当前文件与本地仓库的区别，本地不同分支之间比较

```shell
$ git diff README.md  // 比较当前文件与本地仓库的区别
$ git diff temp       // 比较 master 分支与 temp 分支的区别
```

[`back to content`](#content)



<h3 id="gad"># git add</h3>

> 添加文件到本地暂存区

```shell
$ git add <filename>  //添加制定的文件名  
$ git add .       //添加当前目录下，所有修改的和新增的文件
$ git add *        //添加该目录下所有文件 
```

[`back to content`](#content)



<h3 id="gct"># git commit</h3>

> 将本地暂存区的代码提交到本地版本库

```shell
$ git commit -m "description...." //提交到本地版本库，并添加描述 
```

[`back to content`](#content)



<h3 id="grt"># git reset</h3>

> 撤销本地的 add 和 commit

撤销 git add 操作

```shell
$ git reset HEAD .  //撤销所有的已经add的文件
$ git reset HEAD <filename>   //撤销某个文件或文件夹
```

撤销 git commit 操作

```shell
$ git reset HEAD~1
```



[`back to content`](#content)



<h3 id="gcn"># git clean</h3>

> 删除 untracked files

```shell
$ git clean -f  // 删除 untracked files
$ git clean -fd  //连 untracked 的目录也一起删掉
$ git clean -xfd   //连 gitignore 的untrack 文件/目录也一起删掉 （慎用，一般这个是用来删掉编译出来的 .o之类的文件用的）
```

[`back to content`](#content)




<h3 id="grm"># git rm</h3>

> git rm 是删除文件和版本记录。rm 是删除文件，没有删除版本库的记录，提交后文件依然存在版本库。

```shell
$ git rm <filename>
```

[`back to content`](#content)




<h3 id="gct"># git checkout</h3>

restore local delete files from latest version, if you haven't git commit the deletion

```shell
$ git checkout HEAD <path>
$ git checkout HEAD .  # current dir path
```

restore local delete files from latest version, if you have git commit the deletion.

```shell
$ git checkout HEAD^ <path>
```

[`back to content`](#content)



<h3 id="gce"># git clone</h3>

> 将远程仓库代码克隆到本地

```shell
$ git clone <url>
```

[`back to content`](#content)



<h3 id="gph"># git push</h3>

> 将本地版本库代码同步到远程仓库中。即github中

```shell
$ git push -u origin master   //本地首次提交,设置默认提交的分支，这里设置的是主分支
$ git push      //设置了默认提交的仓库，不用每次提交都写分支名了。方便一点。
$ git push origin master //push到指定远程仓库。origin master 分支为主分支。
```

[`back to content`](#content)



<h3 id="gfh"># git fetch, git merge</h3>

> git fetch 将远程仓库代码更新到本地。不会自动merge

git fetch 比较本地与远程仓库的区别

方式1

```shell
$ git fetch origin master:temp //从远程获取最新的版本到本地的test分支上
$ git diff temp    //进行比较
$ git merge temp  //合并
```

方式2

```shell
$ git fetch origin master  //从远程的origin的master主分支下载最新的版本到origin/master分支上  
$ git log -p master..origin/master  //比较本地的master分支和origin/master分支的差别 
$ git merge origin/master   //进行合并  
```

[`back to content`](#content)



<h3 id="gpl"># git pull</h3>

> .git pull 和git fetch类似，将远程仓库代码更新到本地，但会自动merge。

```shell
$ git pull origin master //相当于是从远程获取最新版本并merge到本地。
```

git fetch 比 git pull 更安全一些 , 因为在merge前 ， 我们可以查看更新情况 ，然后再决定是否合并。

[`back to content`](#content)

--END--
