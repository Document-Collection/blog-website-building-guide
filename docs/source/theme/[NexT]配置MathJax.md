# [NexT]配置MathJax

参考：[数学公式](https://github.com/theme-next/hexo-theme-next/blob/master/docs/zh-CN/MATH.md)

配置`NexT`主题支持数学公式，分为两步

1. 打开`NexT`内部数学公式渲染引擎
2. 打开`hexo`渲染器

## 打开NexT内部数学公式渲染引擎

进入`themes/next/_config.yml`，找到`mathjax`配置

    # MathJax Support
    mathjax:
    enable: false
    per_page: false
    cdn: //cdn.bootcss.com/mathjax/2.7.1/latest.js?config=TeX-AMS-MML_HTMLorMML

设置属性`enable`为`true`，即打开数学公式渲染

属性`per_page`表示是否自动渲染每一页，如果为`true`就只渲染配置块中包含`mathjax: true`的文章

    ---
    title: Next Post
    date: 2019-01-19 17:36:13
    mathjax: true
    ---

## 打开`hexo`渲染器

    npm un hexo-renderer-marked --save
    npm i hexo-renderer-pandoc --save # 或者 hexo-renderer-kramed

数学公式如下

    Simple inline $a = b + c$.

    $$
    \frac{\partial u}{\partial t}
    = h^2 \left( \frac{\partial^2 u}{\partial x^2} +
    \frac{\partial^2 u}{\partial y^2} +
    \frac{\partial^2 u}{\partial z^2}\right)
    $$

启动服务器

    $ hexo clean && hexo s

![](./imgs/hexo-math.png)