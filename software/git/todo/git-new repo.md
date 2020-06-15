# Git Operations



### create a new repository on the command line

```
echo "# java-playground" >> README.md
git init
git add README.md
git commit -m "first commit"
git remote add origin git@github.com:tagnja/java-playground.git
git push -u origin master
```

### push an existing repository from the command line

```
git remote add origin git@github.com:tagnja/java-playground.git
git push -u origin master
```

