添加文件
========

生成一篇新的文章

::

    $ hexo new "My New Post"
    INFO  Created: ~/Documents/hexo-guide/website-sample/source/_posts/My-New-Post.md

生成的文件保存在\ ``source/_posts``\ 文件夹下，文件内容如下

::

    ---
    title: My New Post
    date: 2019-01-18 19:41:07
    tags:
    ---

生成了页面标题和日期，还可以添加\ **标签名**

布局
----

``Hexo``\ 指定了\ ``3``\ 种布局：\ ``post``\ 、\ ``page``\ 和\ ``draft``\ ，可在\ ``_config.yml``\ 中修改默认布局

::

    default_layout: post

默认使用\ ``post``\ 布局，完整的添加文件命令为

::

    $ hexo new [layout] <title>

不同布局的作用是指定生成文件的存储地址

+---------+-------------------------+
| 布局    | 保存路径                |
+=========+=========================+
| post    | source/\_posts          |
+---------+-------------------------+
| draft   | source/\_drafts         |
+---------+-------------------------+
| page    | 生成source/下的文件夹   |
+---------+-------------------------+

文件名修改
----------

生成文件的文件名和\ ``_config.yml``\ 文件中的\ ``new_post_name``\ 属性有关

::

    new_post_name: :title.md # File name of new posts

默认将输入标题作为文件名，还可以添加时间信息

+-------------+---------------------------------------+
| 占位符      | 描述                                  |
+=============+=======================================+
| :title      | 页面标题 (小字母，空格用连字符代替)   |
+-------------+---------------------------------------+
| :year       | 年，比如2019                          |
+-------------+---------------------------------------+
| :month      | 月，占两位，比如01                    |
+-------------+---------------------------------------+
| :i\_month   | 月，占一位，比如1                     |
+-------------+---------------------------------------+
| :day        | 日，占两位，比如08                    |
+-------------+---------------------------------------+
| :i\_day     | 日，占一位，比如8                     |
+-------------+---------------------------------------+

比如，设置为

::

    new_post_name: :year-:month-:day-:title.md

那么生成的文件名包含了时间信息和页面标题

::

    $ hexo new "Next Post" 
    INFO  Created: ~/Documents/hexo-guide/website-sample/source/_posts/2019-01-18-Next-Post.md

文件内容如下：

::

    ---
    title: Next Post
    date: 2019-01-18 19:55:52
    tags:
    ---

草稿
----

发布草稿文件
~~~~~~~~~~~~

默认情况下，服务器不会读取草稿箱内的文件，如果想要读取可以在\ ``_config.yml``\ 中修改属性

::

    render_drafts: false

或者启动服务器时添加参数

::

    hexo server --draft

移动草稿文件
~~~~~~~~~~~~

将草稿箱\ ``_drafts``\ 下的文件移动到\ ``_posts``\ 文件夹下

::

    # Third-Post.md在_drafts文件夹内
    $ hexo publish draft Third-Post
    INFO  Published: ~/Documents/hexo-guide/website-sample/source/_posts/2019-01-18-Third-Post.md
