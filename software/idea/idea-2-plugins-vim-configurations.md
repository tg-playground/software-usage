# IDEA Vim Plugin Configurations

## Plugins

- IdeaVim
- IdeaVimExtension

## IDEA vim's configuration file

creating a IDEA vim's configuration file in `%HOMEPATH%/.ideavimrc`, eg `C:\Users\Tom\.ideavimrc`.

## IdeaVim Shortcut Conflicts

Settings --> Editor --> Vim Emulation --> Shortcut Conflicts for Active Keymap

| Shortcut     | IDEA Action                         | Default Handler | Updated Handler | Vim Action                                                   |
| ------------ | ----------------------------------- | --------------- | --------------- | ------------------------------------------------------------ |
| Ctrl+2       | Send to Right                       | Undefined       |                 |                                                              |
| Ctrl+Shift+2 | Toggle Bookmark 2                   | Undefined       |                 |                                                              |
| Ctrl+Shift+6 | Toggle Bookmark 6                   | Undefined       |                 |                                                              |
| Ctrl+A       | Select All                          | Vim             |                 | Increment the number at cursor                               |
| Ctrl+B       | Source Editor                       | Vim             |                 | move back one full screen                                    |
| Ctrl+C       | Copy                                | Vim             |                 | close the command buffer                                     |
| Ctrl+D       | Send EOF                            | Vim             |                 | Move down by half a page                                     |
| Ctrl+E       | Recent Files                        | Vim             |                 | move screen down one line (without moving cursor)            |
| Ctrl+F       | Find...                             | Vim             |                 | move forward one full screen                                 |
| Ctrl+G       | Go to Line/Column...                | Undefined       |                 | NULL                                                         |
| Ctrl+H       | Base on This Class                  | Vim             |                 | delete the character before the cursor during insert mode    |
| Ctrl+I       | Implement Members...                | Vim             |                 | go to newer position in jump list                            |
| Ctrl+J       | Insert Live Template...             | Undefined       | Vim             | begin new line during insert mode                            |
| Ctrl+K       | Commit...                           | Undefined       | IDE             | NULL                                                         |
| Ctrl+L       | Find Next / Move to Next Occurrence | Vim             |                 | NULL                                                         |
| Ctrl+M       | Commit Message History              | Vim             |                 | NULL                                                         |
| Ctrl+N       | New Folder...                       | Vim             |                 | insert (auto-complete) next match before the cursor during insert mode |
| Ctrl+O       | Create Listener                     | Vim             |                 | go to older position in jump list                            |
| Ctrl+P       | Show/Hide path text                 | Vim             |                 | insert (auto-complete) previous match before the cursor during insert mode |
| Ctrl+Q       | Quick JavaDoc                       | Undefined       | IDE             | NULL                                                         |
| Ctrl+R       | Replace...                          | Undefined       | Vim             | redo                                                         |
| Ctrl+S       | Save All                            | Vim             |                 | NULL                                                         |
| Ctrl+T       | Update Project                      | Vim             |                 | indent (move right) line one shiftwidth during insert mode   |
| Ctrl+U       | Go to Super Method                  | Vim             |                 | move back 1/2 a screen                                       |
| Ctrl+V       | Paste                               | Vim             |                 | start visual block mode                                      |
| Ctrl+W       | Extend Selection                    | Vim             |                 | delete word before the cursor during insert mode             |
| Ctrl+X       | Cut                                 | Vim             |                 | Decrement the number at cursor                               |
| Ctrl+Y       | Delete Selected Rows                | Vim             |                 | move screen up one line (without moving cursor)              |
| Ctrl+[       | Move Caret to Code Block Start      | Vim             |                 | NULL                                                         |
| Ctrl+]       | Move Caret to Code Block End        | Vim             |                 | jump to the tag under cursor                                 |

References

- [Vim Cheat Sheet](https://vim.rtorr.com/)
- [vim-shortcuts.md](https://gist.github.com/tuxfight3r/0dca25825d9f2608714b)

## Configuring on Windows

### clipboard

`C:\Users\Tom\.ideavimrc`

```
"--set copy to system clipboard (vim >=7.3.74)--"
set clipboard=unnamedplus
```

### Auto Switch Input Keyboard Configuration

Plugin: IdeaVimExtension

`C:\Users\Tom\.ideavimrc`

```
# auto switch input keyboard
set keep-english-in-normal
set keep-english-in-normal-and-restore-in-insert
```



## Configuring on MacOS or Linux

`~/.ideavimrc`

```
"--set copy to system clipboard (vim >=7.3.74)--"
set clipboard=unnamedplus
```

## References

[1] [Vim Configuration](https://www.jetbrains.com/help/idea/using-product-as-the-vim-editor.html#vimrc)