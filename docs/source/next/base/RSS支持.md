
# RSS支持

参考：[hexojs/hexo-generator-feed](https://github.com/hexojs/hexo-generator-feed)

下载插件

```
$ npm install hexo-generator-feed --save
```

修改`Hexo _config.yml`，添加

```
feed:
  type: atom
  path: atom.xml
  limit: 0
  hub:
  content:
  content_limit: 140
  content_limit_delim: ' '
  order_by: -date
  icon:
  autodiscovery: true
```

* `type`：制定类型
* `path`：生成路径
* `limit`：文章数量。使用`0`或`false`表示所有文章
* `content_limit`：文章内容限制
* `order_by`：排序

修改`NexT _config.yml`，查找`rss`属性，添加

```
# hexo-generator-feed required for rss support. Leave rss as blank to use site's feed link.
# Set rss to false to disable feed link. Set rss to specific value if you have burned your feed already.
rss: ./atom.xml
```