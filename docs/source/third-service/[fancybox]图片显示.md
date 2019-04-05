
# [fancybox]图片显示

`hexo`页面大小有限，如果图片过大，会缩放在页面中

使用[fancybox](https://github.com/theme-next/theme-next-fancybox3)能够实现点击图片显示原先大小功能，还可以进一步放大

进入`NexT`主题路径，下载`fancybox`仓库

```
$ cd themes/next
$ git clone https://github.com/theme-next/theme-next-fancybox3 source/lib/fancybox
```

修改主题配置文件`_config.yml`

```
# Fancybox. There is support for old version 2 and new version 3.
# Choose only any one variant, do not need to install both.
# To install 2.x: https://github.com/theme-next/theme-next-fancybox
# To install 3.x: https://github.com/theme-next/theme-next-fancybox3
fancybox: true
```

重新生成即可