# Vim Configurations

## File Locations

```
~/.vimrc
```

## Configurations

```shell
"--set number--"
:set number


"--set tab to 4 spaces--"
set tabstop=4       " The width of a TAB is set to 4.
set shiftwidth=4    " Indents will have a width of 4.
set softtabstop=4   " Sets the number of columns for a TAB.
set expandtab       " Expand TABs to spaces.


"--auto indent--"
set autoindent      "auto indent"
set cindent         "set C auto indent"


"--Chinese encoding--"
set fileencodings=utf-8,ucs-bom,gb18030,gbk,gb2312,cp936
set termencoding=utf-8
set encoding=utf-8


"auto complete plugin for C/C++
let g:clang_use_library = 1
" path to directory where library can be found
let g:clang_library_path = '/usr/lib/llvm-3.5/lib/'


"cursor style
"Set terminal cursor on enter insert mode
let &t_SI = "\<Esc>]12;yellow\x7"
"Set terminal cursor on leave insert mode
let &t_EI = "\<Esc>]12;blue\x7"
"Reset default (gray) color on leave vim
autocmd VimLeave * silent !echo -ne "\033]112\007"
```

## Others

### 系统剪切板和vim寄存器之间的拷贝和复制

一检查安装
1首先，查看vim版本是否支持clipboard
vim --version | grep "clipboard" //clipboard前面有一个小小的减号，说明不支持。
2如果不支持的话，需要安装图形化界面的vim，或者重新编译vim
sudo apt-get install vim-gnome
3安装完成后再次执行：
vim --version | grep "clipboard" //发现已经支持clipboard

二使用
打开vim输入:reg查看vim的寄存器，当支持clipboard之后，会多出"+寄存器，表示系统剪切板。
1在vim中进入visual视图后使用"Ny(N表示特定寄存器编好)，
2选中内容复制到系统剪切板，输入命令：
"+y //按住shift依次按出 " + ,然后按y
3系统剪切板的内容粘贴到特定的寄存器（非编辑模式下）。
"+p