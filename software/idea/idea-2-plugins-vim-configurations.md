# IDEA Vim Plugin Configurations

## Plugins

- IdeaVim
- IdeaVimExtension

## IDEA vim's configuration file

creating a IDEA vim's configuration file in `%HOMEPATH%/.ideavimrc`, eg `C:\Users\Tom\.ideavimrc`.

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