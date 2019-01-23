
# npm和cnpm

参考：

[如何使用NPM？CNPM又是什么？](https://www.jianshu.com/p/f581cf9360a2)

[淘宝 NPM 镜像](http://npm.taobao.org/)

`npm`(`node package management`)是`node.js`的包管理器

`cnpm`是淘宝提供的`npm`镜像

>这是一个完整 npmjs.org 镜像，你可以用此代替官方版本(只读)，同步频率目前为 10分钟 一次以保证尽量与官方服务同步。

安装`cnpm`

    npm install -g cnpm --registry=https://registry.npm.taobao.org

安装完成后使用`cnpm`代替`npm`命令