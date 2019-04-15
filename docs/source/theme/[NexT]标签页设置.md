
# [NexT]标签页设置

参考：

[Hexo Next主题使用汇总（不定期更新）](https://suchenrain.github.io/posts/27331/)

[[HEXO] NexT 主题提高博客颜值](https://walesexcitedmei.github.io/2018/08/30/HEXO-NexT-%E4%B8%BB%E9%A2%98%E6%8F%90%E9%AB%98%E5%8D%9A%E5%AE%A2%E9%A2%9C%E5%80%BC/)

可以使用`HTML/CSS/JS`在`markdown`文件中实现标签页功能，参考[Markdown使用-9 标签页实现](https://zj-markdown-guide.readthedocs.io/zh/latest/Markdown%E4%BD%BF%E7%94%A8-9-%E6%A0%87%E7%AD%BE%E9%A1%B5%E5%AE%9E%E7%8E%B0.html)

`NexT`主题内置了标签页实现，参考[Tabs](https://theme-next.org/docs/tag-plugins/tabs)

## 配置

在主题`_config.yml`文件中，打开标签页设置

```
# Tabs tag
tabs:
  enable: true
  transition:
    tabs: false
    labels: true
  border_radius: 0
```

## 实现

代码模板如下：

```
{% tabs Unique name, [index] %}
<!-- tab [Tab caption] [@icon] -->
Any content (support inline tags too).
<!-- endtab -->
{% endtabs %}
```

* 参数`Unique name`表示标签块标签（`tabs block tag`）
* 参数`index`表示起始显示标签页，和`Unique name`用逗号隔开
* 参数`Tab caption`表示标签页名
* 参数`icon`表示[FontAwesome](https://fontawesome.com/icons?d=gallery)符号，以`@`开头，和`Tab caption`用空格隔开

每一对`{% tabs %}`和`{% endtabs %}`表示一个标签块

每一对`<!-- tab -->`和`<!-- endtab -->`表示一个标签页，每个标签块可以包含多个标签页

**标签块名需要不一致，否则会影响实现**

### 子标签和嵌套子标签

还可以在标签页中添加子标签块和嵌套子标签块（也就是子子标签块），模板如下：

```
{% tabs Unique name, [index] %}
<!-- tab [Tab caption] [@icon] -->

{% subtabs Sub Tabs %}
<!-- tab [Tab caption] [@icon] -->
{% subtabs Sub-Sub Tabs %}

<!-- tab [Tab caption] [@icon] -->
...
{% endtabs %}

<!-- endsubtabs -->
{% endtabs %}
<!-- endsubtabs -->

<!-- endtab -->
{% endtabs %}
```

子标签块`{% subtabs Sub Tabs %}`和`<!-- endsubtabs -->`需要在标签页中实现

嵌套子标签块`{% subtabs Sub-Sub Tabs %}`和`<!-- endsubtabs -->`也需要在标签页中实现

**子标签块名和嵌套子标签块名都需要不一致，否则会影响实现**

### 示例

[标签页测试](https://www.zhujian.tech/posts/5213c80b.html)


