
# 博客网站搭建指南

[![Documentation Status](https://readthedocs.org/projects/blog-website-building-guide/badge/?version=latest)](https://blog-website-building-guide.readthedocs.io/zh_CN/latest/?badge=latest) [![standard-readme compliant](https://img.shields.io/badge/standard--readme-OK-green.svg?style=flat-square)](https://github.com/RichardLitt/standard-readme) [![Conventional Commits](https://img.shields.io/badge/Conventional%20Commits-1.0.0-yellow.svg)](https://conventionalcommits.org) [![Commitizen friendly](https://img.shields.io/badge/commitizen-friendly-brightgreen.svg)](http://commitizen.github.io/cz-cli/)

完整的博客网站搭建指南，包含如下设置：

1. 网站搭建，当前使用`Hexo v4.0.0`
2. 主题配置，当前使用`NexT v7.5.0`
3. `CI&CD`，当前通过`Jenkins+腾讯云`实现

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

编译文档需要预先安装以下工具：

```
$ pip install -U Sphinx
$ sudo apt-get install make
```

## 用法

有两种使用方式

1. 在线浏览文档：[博客网站搭建指南](https://blog-website-building-guide.readthedocs.io/zh_CN/latest/)

2. 本地生成文档，实现如下：

    ```
    $ git clone https://github.com/zjZSTU/blog-website-building-guide.git
    $ cd blog-website-building-guide/docs
    $ make html
    ```
    编译完成后进入`docs/build/html`目录，打开`index.html`文件

## 主要维护人员

* zhujian - *Initial work* - [zjZSTU](https://github.com/zjZSTU)

## 参与贡献方式

欢迎任何人的参与！打开[issue](https://github.com/zjZSTU/hexo-guide/issues)或提交合并请求。

注意:

* `GIT`提交，请遵守[Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0-beta.4/)规范
* 语义版本化，请遵守[Semantic Versioning 2.0.0](https://semver.org)规范
* `README`编写，请遵守[standard-readme](https://github.com/RichardLitt/standard-readme)规范

## 许可证

[Apache License 2.0](LICENSE) © 2019 zjZSTU
