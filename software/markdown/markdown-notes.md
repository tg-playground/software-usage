# Markdown Notes

<h3 id="content">Content</h3>

- [Header](#header)
- [paragraph](#paragraph)
- [Emphasis](#emphasis)
- [Lists](#lists)
- [Images](#images)
- [Links](#links)
- [Blockquotes](#bq)
- [Highlighting](#hl)
- [Code](#code)
- [Task Lists](#tl)
- [Tables](#tables)
- [Emoji](#emoji)
- [Diagrams](#diagrams)
- [HTML](#html)
- Other
  - [line between](#lb)
  - [Ignore Markdown formatting](#imf)

段落



### Main

<h3 id="header">header</h3>

```
# This is an <h1> tag
## This is an <h2> tag
###### This is an <h6> tag
```

[back to content](#content)

<h3 id="paragraph">Paragraph</h3>

Using two space to new line

Two Enter

<h3 id="emphasis">Emphasis</h3>

You can indicate emphasis with bold, italic, or strikethrough text.

| Style           | Syntax             | Keyboard shortcut   | Example                                  | Output                              |
| --------------- | ------------------ | ------------------- | ---------------------------------------- | ----------------------------------- |
| Bold            | `** **` or `__ __` | command/control + b | `**This is bold text**`                  | **This is bold text**               |
| Italic          | `* *` or `_ _`     | command/control + i | `*This text is italicized*`              | *This text is italicized*           |
| Strikethrough   | `~~ ~~`            |                     | `~~This was mistaken text~~`             | ~~This was mistaken text~~          |
| Bold and italic | `** **` and `_ _`  |                     | `**This text is _extremely_ important**` | **This text is extremelyimportant** |

[back to content](#content)



<h3 id="lists">Lists</h3>

**Unordered**

Using `-`,`+`,`·`,`*`, add  a space.

```
* Item 1
* Item 2
  * Item 2a
  * Item 2b
```

**Ordered**

```
1. Item 1
2. Item 2
3. Item 3
   1. Item 3a
   2. Item 3b
```

[back to content](#content)



<h3 id="images">Images</h3>

```
![GitHub Logo](/images/logo.png)
Format: ![Alt Text](url)
```

[back to content](#content)



<h3 id="links">Links</h3>

```
http://github.com - automatic!
[GitHub](http://github.com)
or 
<url>
```



[back to content](#content)


<h3 id="bq">Blockquotes</h3>

```
As Kanye West said:

> We're living the future so
> the present is our past.
```

[back to content](#content)


<h3 id="hl">Highlighting</h3>

```
I think you should use an
`<addr>` element here instead.
```

[back to content](#content)


<h3 id="code">Code</h3>

```
​```javascript
function fancyAlert(arg) {
  if(arg) {
    $.facebox({div:'#foo'})
  }
}
​```
```

You can also simply indent your code by four spaces:

```
    function fancyAlert(arg) {
      if(arg) {
        $.facebox({div:'#foo'})
      }
    }
```

[back to content](#content)


<h3 id="tl">Task Lists</h3>

```
- [x] @mentions, #refs, [links](), **formatting**, and <del>tags</del> supported
- [x] list syntax required (any unordered or ordered list supported)
- [x] this is a complete item
- [ ] this is an incomplete item
```

[back to content](#content)


<h3 id="tables">Tables</h3>

You can create tables by assembling a list of words and dividing them with hyphens `-` (for the first row), and then separating each column with a pipe `|`:

```
First Header | Second Header
------------ | -------------
Content from cell 1 | Content from cell 2
Content in the first column | Content in the second column
```

Would become:

| First Header                | Second Header                |
| --------------------------- | ---------------------------- |
| Content from cell 1         | Content from cell 2          |
| Content in the first column | Content in the second column |

[back to content](#content)


<h3 id="emoji">Emoji</h3>

GitHub supports [emoji](https://help.github.com/articles/basic-writing-and-formatting-syntax/#using-emoji)!

To see a list of every image we support, check out the [Emoji Cheat Sheet](https://github.com/ikatyang/emoji-cheat-sheet/blob/master/README.md).

You can add emoji to your writing by typing `:EMOJICODE:`.

```
@octocat :+1: This PR looks great - it's ready to merge! :shipit:
```

@octocat :+1: This PR looks great - it's ready to merge!  :shipit: 

[back to content](#content)


<h3 id="diagrams">Diagrams</h3>

TODO


[back to content](#content)


<h3 id="html">HTML</h3>

```
newLine: <br>
Font Color: <font color="red">red</font> 
Space：&nbsp;
```

[back to content](#content)


<h3 id="lb">Line between</h3>

Using `---` to create a line between.

[back to content](#content)



<h3 id="imf">Ignore Markdown formatting</h3>

You can tell GitHub to ignore (or escape) Markdown formatting by using `\` before the Markdown character.

```
Let's rename \*our-new-project\* to \*our-old-project\*.
```

Result

Let's rename \*our-new-project\* to \*our-old-project\*.

[back to content](#content)


### References:

Mastering Markdown <https://guides.github.com/features/mastering-markdown/>

Basic writing and formatting syntax <https://help.github.com/en/articles/basic-writing-and-formatting-syntax>

Markdown: Syntax <https://daringfireball.net/projects/markdown/syntax>

--END--