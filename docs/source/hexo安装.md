
# hexo安装

需要先安装`git`和`Node.js`

## `Node.js`安装

参考[Installation](https://github.com/nodejs/help/wiki/Installation)，使用源码安装Node.js

下载源码压缩包[download](https://nodejs.org/en/download/)，当前`LTS`版本为10.15.0

    node-v10.15.0-linux-x64.tar.xz

解压文件

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
        node: '    sudo ln -s /usr/local/lib/nodejs/node-$VERSION/bin/node /usr/bin/node
    sudo ln -s /usr/local/lib/nodejs/node-$VERSION/bin/npm /usr/bin/npm
    sudo ln -s /usr/local/lib/nodejs/node-$VERSION/bin/npx /usr/bin/npx10.15.0',
        openssl    sudo ln -s /usr/local/lib/nodejs/node-$VERSION/bin/node /usr/bin/node
    sudo ln -s /usr/local/lib/nodejs/node-$VERSION/bin/npm /usr/bin/npm
    sudo ln -s /usr/local/lib/nodejs/node-$VERSION/bin/npx /usr/bin/npx: '1.1.0j',
        tz: '20    sudo ln -s /usr/local/lib/nodejs/node-$VERSION/bin/node /usr/bin/node
    sudo ln -s /usr/local/lib/nodejs/node-$VERSION/bin/npm /usr/bin/npm
    sudo ln -s /usr/local/lib/nodejs/node-$VERSION/bin/npx /usr/bin/npx18e',
        unicode    sudo ln -s /usr/local/lib/nodejs/node-$VERSION/bin/node /usr/bin/node
    sudo ln -s /usr/local/lib/nodejs/node-$VERSION/bin/npm /usr/bin/npm
    sudo ln -s /usr/local/lib/nodejs/node-$VERSION/bin/npx /usr/bin/npx: '11.0',
        uv: '1.    sudo ln -s /usr/local/lib/nodejs/node-$VERSION/bin/node /usr/bin/node
    sudo ln -s /usr/local/lib/nodejs/node-$VERSION/bin/npm /usr/bin/npm
    sudo ln -s /usr/local/lib/nodejs/node-$VERSION/bin/npx /usr/bin/npx23.2',
        v8: '6.8.275.32-node.45',
        zlib: '1.2.11' }
    $ npx -v
    6.4.1

## `hexo`安装

    npm install -g hexo-cli

测试

    $hexo --version
        hexo-cli: 1.1.0
        os: Linux 4.15.0-43-generic linux x64
        http_parser: 2.8.0
        node: 10.15.0
        v8: 6.8.275.32-node.45
        uv: 1.23.2
        zlib: 1.2.11
        ares: 1.15.0
        modules: 64
        nghttp2: 1.34.0
        napi: 3
        openssl: 1.1.0j
        icu: 62.1
        unicode: 11.0
        cldr: 33.1
        tz: 2018e
