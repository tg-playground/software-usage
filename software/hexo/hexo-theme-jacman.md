# Note of Jacman Theme of Hexo

Content

- Official Docs
- Add RSS



## Official Docs

- [如何使用 Jacman 主题](http://jacman.wuchong.me/2014/11/20/how-to-use-jacman/)
- [jacman - GitHub](https://github.com/wuchong/jacman)

## Add RSS

### 1. Install

Install hexo-generate-feed plugin

```
$ npm install hexo-generator-feed --save
```

### 2. Options

You can configure this plugin in `/_config.yml`.

```
feed:
  type: atom
  path: atom.xml
  limit: 20
  hub:
  content:
  content_limit: 140
  content_limit_delim: ' '
  order_by: -date
  icon: icon.png
  autodiscovery: true
```

### 3. Config Jacman 

Update Jacman configuration file in`/themes/jacman/_config.yml`, Edit `widgets` and `rss` options

```
#### Widgets
widgets:
- rss

rss: /atom.xml

```

### 4. View Result

```
hexo generate
hexo server
```



## References

RSS

- [hexo-generator-feed - GitHub](https://github.com/hexojs/hexo-generator-feed)
- [为hexo博客添加RSS订阅功能 - SegmentFault](https://segmentfault.com/a/1190000012647294)
- [Jacman 基于 Pacman 修改的 Hexo 主题](https://wsgzao.github.io/post/hexo-jacman/)

