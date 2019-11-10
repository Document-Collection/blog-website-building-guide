
# [NexT]添加打赏功能

可以在每篇文章末尾添加打赏链接，设置主题`_config.yml`文件

    # Reward
    # If true, reward would be displayed in every article by default.
    # And you can show or hide one article specially through add page variable `reward: true/false`.
    reward:
        enable: false
        #comment: Donate comment here
        #wechatpay: /images/wechatpay.jpg
        #alipay: /images/alipay.jpg
        #bitcoin: /images/bitcoin.jpg

设置属性`enable`为`true`，并且将微信支付和支付宝支付的截图放置在主题包下`source/images`文件夹下

        enable: true
        comment: 坚持原创技术分享，您的支持将鼓励我继续创作！
        wechatpay: /images/wechatpay.jpg
        alipay: /images/alipay.jpg
        #bitcoin: /images/bitcoin.jpg