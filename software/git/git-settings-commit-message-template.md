# Git Settigns - Commit Message Template

Content

- Write commit message template 
- Set commit message template 
- Using Template to Commit 
- References

## Write commit message template 

Edit `.gitmessage`

```
vim .gitmessage
```

Add the following lines to the file:

```
# [<tag>] (If applied, this commit will...) <subject> (Max 72 char)
# |<----   Preferably using up to 50 chars   --->|<------------------->|
# Example:
# [feat] Implement automated commit messages

# (Optional) Explain why this change is being made
# |<----   Try To Limit Each Line to a Maximum Of 72 Characters   ---->|

# (Optional) Provide links or keys to any relevant tickets, articles or other resources
# Example: Github issue #23

# --- COMMIT END ---
# Tag can be 
#    feat     (new feature)
#    fix      (bug fix)
#    docs     (changes to documentation)
#    style    (formatting, missing semi colons, etc; no code change)
#    refactor (refactoring production code)
#    test     (adding or refactoring tests; no production code change)
#    chore    (updating build tasks, package manager configs, etc; no production code change)
#    version  (version bump/new release; no production code change)

#    jsrXXX   (Patches related to the implementation of jsrXXX, where XXX the JSR number)
#    jdkX     (Patches related to supporting jdkX as the host VM, where X the JDK version)
#    dbg      (Changes in debugging code/frameworks; no production code change)
#    license  (Edits regarding licensing; no production code change)
#    hack     (Temporary fix to make things move forward; please avoid it)
#    WIP      (Work In Progress; for intermediate commits to keep patches reasonably sized)
#    defaults (changes default options)
#
# Note: Multiple tags can be combined, e.g. [fix][jsr292] Fix issue X with methodhandles
# --------------------
# Remember to:
#   * Capitalize the subject line
#   * Use the imperative mood in the subject line
#   * Do not end the subject line with a period
#   * Separate subject from body with a blank line
#   * Use the body to explain what and why vs. how
#   * Can use multiple lines with "-" or "*" for bullet points in body
# --------------------
```

## Set commit message template 

There are two options to Set commit message template.

1) edit `.git/config`.

Add the following lines to the file `.git/config`

```
[commit]
	template = .gitmessage
```

2) Running the git config command line

For all git repositories

```
git config --global commit.template ~/.gitmessage
```

For a git repository

```
git config --local commit.template .gitmessage
```

## Using Template to Commit 

```
git commit
```



## References

[1] [.git-commit-template - GitHub](https://gist.github.com/zakkak/7e06725ebd1336bfebebe254de3de825)

[2] [Create A Custom Git Commit Template - Medium](https://medium.com/@alex.wasik/create-a-custom-git-commit-template-84468232a459)