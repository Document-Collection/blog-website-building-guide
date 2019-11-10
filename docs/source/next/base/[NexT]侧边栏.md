
# [NexT]侧边栏

侧边栏中包含多种配置，可通过修改主题`_config.yml`实现

## 头像

    # Sidebar Avatar
    avatar:
        # in theme directory(source/images): /images/avatar.gif
        # in site  directory(source/uploads): /uploads/avatar.gif
        # You can also use other linking images.
        url: #/images/avatar.gif                                         // 头像地址
        # If true, the avatar would be dispalyed in circle.
        rounded: false                                                   // 是否显示为圆形
        # The value of opacity should be choose from 0 to 1 to set the opacity of the avatar.
        opacity: 1                                                       // 不透明度 1表示完全不透明
        # If true, the avatar would be rotated with the cursor.
        rotated: false                                                   // 光标移到图标自动旋转

* `url`：图像地址。默认为NexT包下`/source/images/avatar.gif`，也可放置在站点路径`/source/uploads`文件夹内
* `rounded`：是否显示为圆形图标
* `opacity`：透明度设置[0,1]，0表示完全透明，1表示完全不透明
* `rotated`：光标移动到图标是否旋转

## 侧边栏位置

可通过设置改变侧边栏在页面上的位置

    sidebar:
        # Sidebar Position, available values: left | right (only for Pisces | Gemini).
        position: left
        #position: right

        ...
        ...

        # Back to top in sidebar.
        b2t: false
        # Scroll percent label in b2t button.
        scrollpercent: false

* `position`：可设置侧边栏在左边还是右边(针对`Pisces`或者`Gemini`主题）
* `b2t`：是否在侧边栏显示点击返回顶点按钮
* `scrollpercent`：是否显示已滚动的百分比

## 社交链接

    # Social Links
    # Usage: `Key: permalink || icon`
    # Key is the link label showing to end users.
    # Value before `||` delimeter is the target permalink.
    # Value after `||` delimeter is the name of FontAwesome icon. If icon (with or without delimeter) is not specified, globe icon will be loaded.
    #social:
        #GitHub: https://github.com/yourname || github
        #E-Mail: mailto:yourname@gmail.com || envelope
        #Weibo: https://weibo.com/yourname || weibo
        #Google: https://plus.google.com/yourname || google
        #Twitter: https://twitter.com/yourname || twitter
        #FB Page: https://www.facebook.com/yourname || facebook
        #VK Group: https://vk.com/yourname || vk
        #StackOverflow: https://stackoverflow.com/yourname || stack-overflow
        #YouTube: https://youtube.com/yourname || youtube
        #Instagram: https://instagram.com/yourname || instagram
        #Skype: skype:yourname?call|chat || skype

`NexT`内置了多个网站的链接，取消想要添加的链接注释

* `key`值是显示的选项名
* `||`前面表示链接的地址
* `||`后面表示图标，可通过[Font Awesome](https://fontawesome.com/icons?d=gallery&q=github)库自定义

比如我的自定义

    social:
        Github: https://github.com/zjZSTU || github
        CSDN: https://blog.csdn.net/u012005313 || book
        Email: mailto:zjzstu@gmail.com || envelope

*邮箱设置参考[请问怎么在侧边栏社交处添加邮箱呢](https://github.com/iissnan/hexo-theme-next/issues/1489)*

## 友情链接

    links:
        # Title: http://example.com
    
修改`Title`和链接地址
