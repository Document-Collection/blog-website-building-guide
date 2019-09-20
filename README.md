# hexo-guide

[![Documentation Status](https://readthedocs.org/projects/hexo-guide/badge/?version=latest)](https://hexo-guide.readthedocs.io/zh_CN/latest/?badge=latest) [![standard-readme compliant](https://img.shields.io/badge/standard--readme-OK-green.svg?style=flat-square)](https://github.com/RichardLitt/standard-readme) [![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-yellow.svg)](https://conventionalcommits.org) [![Commitizen friendly](https://img.shields.io/badge/commitizen-friendly-brightgreen.svg)](http://commitizen.github.io/cz-cli/)

> 使用`Hexo`进行网站制作

基于`Hexo`实现的个人网站 - https://www.zhujian.tech

网站制作包含以下服务：

* 网站框架：[Hexo](https://hexo.io)

* 主题：[NexT](https://github.com/zjZSTU/hexo-theme-next)

* 搜索：[Algolia](https://hexo-guide.readthedocs.io/zh_CN/latest/third-service/[Algolia]%E7%BD%91%E7%AB%99%E6%90%9C%E7%B4%A2.html)

* 评论系统：[Gitalk](https://hexo-guide.readthedocs.io/zh_CN/latest/third-service/[Gitalk]%E8%AF%84%E8%AE%BA%E7%B3%BB%E7%BB%9F.html)

* 访客和阅读次数统计：
    * [不蒜子](https://hexo-guide.readthedocs.io/zh_CN/latest/third-service/[%E4%B8%8D%E8%92%9C%E5%AD%90]%E6%96%87%E7%AB%A0%E9%98%85%E8%AF%BB%E6%AC%A1%E6%95%B0.html)
    * [百度统计](https://tongji.baidu.com/web/27249108/welcome/login)

* 持续集成：[Travis CI](https://hexo-guide.readthedocs.io/zh_CN/latest/third-service/[Travis%20CI]%E6%8C%81%E7%BB%AD%E9%9B%86%E6%88%90.html)

* 云服务：[腾讯云](https://cloud.tencent.com/?fromSource=gwzcw.1736893.1736893.1736893&gclid=Cj0KCQjwjYHpBRC4ARIsAI-3GkHCQESLZ49VY6v9zVtEgSVlnywvjdYO6VS7QN9Ia-vCQD1mQa0J8ywaAvdCEALw_wcB)

* 域名服务：[阿里云](https://wanwang.aliyun.com/domain/com/?spm=5176.10695662.1158081.1.59854234GbQWbo)

## 内容列表

- [背景](#背景)
- [安装](#安装)
- [用法](#用法)
- [主要维护人员](#主要维护人员)
- [参与贡献方式](#参与贡献方式)
- [许可证](#许可证)

## 背景

在`CSDN`上写博客很久了，在上面编辑、发布操作都比较复杂，所以打算自建网站

## 安装

需要预先安装以下工具：

```
$ pip install -U Sphinx
$ sudo apt-get install make
```

## 用法

有两种使用方式

1. 在线浏览文档：[hexo指南](https://hexo-guide.readthedocs.io/zh_CN/latest/)

2. 本地生成文档，实现如下：

    ```
    $ git clone https://github.com/zjZSTU/hexo-guide.git
    $ cd hexo-guide/docs
    $ make html
    ```
    编译完成后进入`docs/build/html`目录，打开`index.html`文件

## 主要维护人员

* zhujian - *Initial work* - [zjZSTU](https://github.com/zjZSTU)

## 参与贡献方式

欢迎任何人的参与！打开[issue](https://github.com/zjZSTU/PyNet/issues)或提交合并请求。

注意:

* `git`提交请遵守[Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0-beta.4/)
* 如果进行版本化，请遵守[Semantic Versioning 2.0.0](https://semver.org)规范
* 如果修改README，请遵守[standard-readme](https://github.com/RichardLitt/standard-readme)规范

## 许可证

[Apache License 2.0](LICENSE) © 2019 zjZSTU
