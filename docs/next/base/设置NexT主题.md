
# 设置NexT主题

在[主题列表](https://hexo.io/themes/)中可以找到许多主题，其中`NexT`是一个集成了许多功能的主题，并且不断有新的功能加入其中，所以在网上查询时最好参考最新的文章，同时查询主题`_config.yml`配置

## 参考

`NexT`官方实现网站：[Theme for Hexo](https://theme-next.org/)

个人实现网站：[theme-next](http://theme-next.iissnan.com/)

`NexT github`地址：[theme-next/hexo-theme-next](https://github.com/theme-next/hexo-theme-next/blob/master/docs/zh-CN/README.md)

`NexT`配置博文：

[GitHub+Hexo 搭建个人网站详细教程](https://zhuanlan.zhihu.com/p/26625249)

[Hexo设置主题以及Next主题个性设置](https://www.jianshu.com/p/b20fc983005f)

## 配置

点击进入`github`链接，下载主题包到`themes`目录下，在`_config.yml`文件中修改主题

```
# theme: landscape
theme: next
```

## 安装

安装[theme-next/hexo-theme-next](https://github.com/theme-next/hexo-theme-next)主题

    $ cd hexo
    $ git clone https://github.com/theme-next/hexo-theme-next themes/next

![](./imgs/hexo-theme-next.png)

## 两个_config.yml文件

`Hexo`和`NexT`都通过各自的配置文件`_config.yml`进行管理

`Hexo`配置文件`_config.yml`位于工程根目录；`NexT`配置文件`_config.yml`位于主题包根目录，即`themes/next/_config.yml`

下面将`Hexo`配置文件称为`Hexo _config.yml`，将`NexT`配置文件称为`NexT _config.yml`