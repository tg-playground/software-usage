### Theme

Notice: After git clone theme, you need remove the .git directory.

### Categories

New Page Categories (Optional)

```
$ hexo new page categories
```

Setting Page theme/xxx/_config.yml (Optional)

```
menu:
  Home: /
  Categories: /categories
  Archives: /archives
  About: /about
```

New post

```
$ hexo new {yourArticleName}
```

Setting categories for post

```
title: My New Post
date: 2019-07-07 08:36:24
categories: Java
tags:
```

Setting multiple levels categories for post

```
---
title: My New Post
date: 2019-07-07 08:36:24
categories:
- Java
- Concurrency
tags:
---
```



### Tag

```
---
title: My New Post
date: 2017-05-26 12:12:57
categories: 
- web
tags:
- jQuery
- JavaSript
---
```

### About

Add about apge

```
$ hexo new page about
```

Edit about/index.md

```
title: about
layout: page
```

Edit theme/xxx/_config.yml, Add About: /about

```
menu:
  Home: /
  Archives: /archives/
  About: /about
```

Edit theme/xxx/languages/default.yml, Add about: About

```
menu: 
  home: Home
  archives: Archives
  tags: Tags
  categories: Categories
  about: About
```

Edit your about page content in source/about/index.md

