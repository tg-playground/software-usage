# Vim Shortcut

### View Mode

```
// move
j, k, l, h, 10j, H, M, L

// jump line begin or end
0, ^, $

// jump next char
f {char}, F {char}, t {char}, T {char}

// jump next word
w, W, b, B, e, E

// jump next word line 
*, # 

// jump line
gg, G, 10 G

// jump next sentence
) , (

// jump next paragraph
}, {

// jump matching closing brace
%

// jump column
|, 10 |

// jump mark 
m{mark_char}, '{mark_char}

// jump latest jump
' ', ` `, 

// jump the last-changed line
' .

// page up, page down
ctrl f, ctrl b, ctrl d, ctrl u

// select, cut, copy, paste
v, V, x, y, yy, p, 10+p
dd, 10+dd, x, dw, 
df {char} // delete from current location forward to input char
dt {char} // delete from cuurent location back to input char
di", // remove content in "" 
da" // remove content and ""

// undo, redo
u, ctrl r
```

### Insert Mode

```
Ctrl + w // remove content in ""
```

### Command Mode

```
# replace all (global) in all lines
:%s/{search_val}/{replace_val}/g
# replace all (global) in specified lines 
:{start_line},{end_line}s/{search_val}/{replace_val}/g
```



## References

- [Vim Cheat Sheet](https://vim.rtorr.com/)