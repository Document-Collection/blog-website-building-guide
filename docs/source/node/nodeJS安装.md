
# nodeJS安装

`hexo`框架基于`Node.JS`实现，经过实践发现同样需要了解一些有关`Node`的知识，记录一下

## 安装

参考[Installation](https://github.com/nodejs/help/wiki/Installation)，使用源码安装`Node.js`

下载已编译安装包[download](https://nodejs.org/en/download/)，当前`LTS`版本为`10.15.0`

    node-v10.15.0-linux-x64.tar.xz

解压文件，参考：[Ubuntu 下解压tar.xz方法](https://www.cnblogs.com/baby123/p/6611169.html)

    # 首先解压xz压缩包
    $ xz -d node-v10.15.0-linux-x64.tar.xz
    # 然后解压tar压缩包
    $ tar xvf node-v10.15.0-linux-x64.tar
    # 最终得到
    /home/zj/software/nodejs/node-v10.15.0-linux-x64

设置环境变量，修改`.bashrc`文件

    # Nodejs
    export NODEJS_HOME=/home/zj/software/nodejs/node-v10.15.0-linux-x64/bin
    export PATH=$NODEJS_HOME:$PATH

刷新文件

    source ~/.bashrc

测试命令

    $ node -v
    v10.15.0
    $ npm version
    { npm: '6.4.1',
    ares: '1.15.0',
    cldr: '33.1',
    http_parser: '2.8.0',
    icu: '62.1',
    modules: '64',
    napi: '3',
    nghttp2: '1.34.0',
    node: '10.15.0',
    openssl: '1.1.0j',
    tz: '2018e',
    unicode: '11.0',
    uv: '1.23.2',
    v8: '6.8.275.32-node.45',
    zlib: '1.2.11' }
    $ npx -v
    6.4.1