
# [Docker][Jenkins][GitLab][Nginx]腾讯云服务器部署

实现方式如下：

* 在本地安装`Jenkins/GitLab`
     * 上传修改到`GitLab`
     * 通过`WebHook`触发`Jenkins`进行构建
     * 构建完成后上传静态文件到云服务器
* 在云服务器上安装`Git/Nginx`
    * `Git`仓库接收到新的提交后，分离工作目录和裸仓库(`.git`)
    * `Nginx`托管工作目录地址，对外发布博客网站

相关文档链接：

* `Git`相关
    * [工作目录和裸仓库分离](https://zj-git-guide.readthedocs.io/zh_CN/latest/advanced/%E5%B7%A5%E4%BD%9C%E7%9B%AE%E5%BD%95%E5%92%8C%E8%A3%B8%E4%BB%93%E5%BA%93%E5%88%86%E7%A6%BB/)
    * [[Docker]GitLab使用](https://zj-git-guide.readthedocs.io/zh_CN/latest/platform/[Docker]GitLab%E4%BD%BF%E7%94%A8/)
* `Jenkins`相关
    * [在Docker中运行Jenkins](https://blog.zhujian.life/posts/202ee452.html)
    * [[Jenkins][Gitlab]webhook连接](https://blog.zhujian.life/posts/6ff96ec3.html)
    * [[Jenkins]Pipeline工程配置NodeJS环境](https://blog.zhujian.life/posts/d521b4ea.html)
    * [[Jenkins][GitLab][Hexo]新建Pipeline工程实现CI功能](https://blog.zhujian.life/posts/f80ec296.html)
* `Nginx`相关
    * [托管网站](https://zj-network-guide.readthedocs.io/zh_CN/latest/nginx/%E6%89%98%E7%AE%A1%E7%BD%91%E7%AB%99/)