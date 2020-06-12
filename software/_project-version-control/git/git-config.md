# Git Config

- `--local`. Local config for current project.
- `--global`. **Global** configs are available for all projects for the current user and stored in `~/. gitconfig`.
- `--system`. **System** configs are available for all the users/projects and stored in `/etc/gitconfig`. 

Examine

```
git config --global --list
git config --local --list
```

Set

```
# set Global git config
git config --global <key> <value>

# set current repository git config
git config <key> <value>
```

Unset

```
# unset global config
git config --global --unset <key>

# unset current repository git config
git config --unset <key>
```

