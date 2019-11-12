
# [腾讯云][Travis CI]持续部署到云服务器

[[腾讯云]部署云服务器](https://hexo-guide.readthedocs.io/zh_CN/latest/third-service/[%E8%85%BE%E8%AE%AF%E4%BA%91]%E9%83%A8%E7%BD%B2%E4%BA%91%E6%9C%8D%E5%8A%A1%E5%99%A8.html)已实现`hexo`部署到云服务器，下一步利用自动部署工具`Travis CI`

实现原理如下：

上传文档到`github`，`Travis CI`执行自动部署脚本，生成静态文件并推送到云服务器

要解决的问题是**云服务器的`ssh`密钥连接** 和 **`ssh`服务器公钥检查**问题

`.travis.yml`修改如下：

    themes/next/dist: xenial
    language: node_js
    node_js:
    - node
    - 10.15.0
    cache: npm
    branches:
    only:
    - dev
    before_install:
    - openssl aes-256-cbc -K $encrypted_2cf61c1c8bc9_key -iv $encrypted_2cf61c1c8bc9_iv
    -in tencent_id_rsa.enc -out ~/.ssh/tencent_id_rsa -d
    - chmod 600 ~/.ssh/tencent_id_rsa
    - echo -e "Host 132.232.142.219\n\tStrictHostKeyChecking no\n" >> ~/.ssh/config
    - npm install -g hexo-cli
    install:
    - cd ./blogs/
    - git clone https://github.com/zjZSTU/hexo-theme-next.git themes/next
    - git clone https://github.com/theme-next/theme-next-canvas-nest themes/next/source/lib/canvas-nest
    - git clone https://github.com/theme-next/theme-next-algolia-instant-search themes/next/source/lib/algolia-instant-search
    - npm install
    before_script:
    - git config --global user.name $USER_NAME
    - git config --global user.email $USER_EMAIL
    script:
    - pwd
    - hexo clean
    - hexo generate
    - hexo algolia
    after_success:
    - eval "$(ssh-agent -s)"
    - ssh-add ~/.ssh/tencent_id_rsa
    - git clone ubuntu@132.232.142.219:/home/ubuntu/git/zhujian.tech.git upload_git
    - cd upload_git
    - rm -rf !(.git)
    - cp -r ../public/* ./
    - git add .
    - git commit -m "Update blogs"
    - git push --force ubuntu@132.232.142.219:/home/ubuntu/git/zhujian.tech.git master
    - cd ..
    - sed -i'' "s~https://github.com/zjZSTU/zjzstu.github.com.git~https://${GITHUB_REPO_TOKEN}@github.com/zjZSTU/zjzstu.github.com.git~"
    _config.yml
    - sed -i'' "s~git@git.dev.tencent.com:zjZSTU/zjZSTU.coding.me.git~https://zjZSTU:${CODING_REPO_TOKEN}@git.coding.net/zjZSTU/zjZSTU.coding.me.git~"
    _config.yml
    - hexo deploy

## `ssh`服务器公钥检查

参考：

[[Ubuntu 16.04]SSH禁用公钥检查](https://zj-linux-guide.readthedocs.io/zh_CN/latest/commands/[Ubuntu%2016.04]SSH%E7%A6%81%E7%94%A8%E5%85%AC%E9%92%A5%E6%A3%80%E6%9F%A5.html)

[Adding to SSH Known Hosts](https://docs.travis-ci.com/user/ssh-known-hosts/)

设置配置文件`~/.ssh/config`，禁止`SSH`服务器公钥检查

    before_install:
    - echo -e "Host 132.232.142.219\n\tStrictHostKeyChecking no\n" >> ~/.ssh/config

## 云服务器的`ssh`密钥连接

将私钥上传到`Travis CI`，为了保密需要使用`Travis CI`命令行工具

### 加密文件

参考：

[Encrypting Files](https://docs.travis-ci.com/user/encrypting-files/)

[配置文件](https://segmentfault.com/a/1190000009093621#articleHeader3)

#### 安装Travis CI命令行工具

首先安装Ruby，参考：[安装 Ruby](https://www.ruby-lang.org/zh_cn/documentation/installation/#apt)

    $ sudo apt-get install ruby-full

然后安装命令行工具

    $ gem install travis

#### 加密敏感文件

进入本地仓库根目录

首先登录到github账户

    $ travis login --auto
    We need your GitHub login to identify you.
    This information will not be sent to Travis CI, only to api.github.com.
    The password will not be displayed.

    Try running with --github-token or --auto if you don't want to enter your password anyway.

    Username: zjZSTU
    Password for zjZSTU: *********
    Successfully logged in as zjZSTU!

然后加密私钥

    $ travis encrypt-file ~/.ssh/tencent_id_rsa --add
    Detected repository as zjZSTU/zjzstu.github.com, is this correct? |yes| 
    encrypting /home/zj/.ssh/tencent_id_rsa for zjZSTU/zjzstu.github.com
    storing result as tencent_id_rsa.enc
    storing secure env variables for decryption

    Make sure to add tencent_id_rsa.enc to the git repository.
    Make sure not to add /home/zj/.ssh/tencent_id_rsa to the git repository.
    Commit all changes to your .travis.yml.

操作完成后会在`Travis CI`对应仓库的`settings`的环境变量中出现

    encrypted_2cf61c1c8bc9_iv
    encrypted_2cf61c1c8bc9_key

同时添加参数`--add`会自动在`.travis.yml`中添加解密私钥操作

    before_install:
    - openssl aes-256-cbc -K $encrypted_2cf61c1c8bc9_key -iv $encrypted_2cf61c1c8bc9_iv
    -in tencent_id_rsa.enc -out ~/.ssh/tencent_id_rsa -d
    ...
    ...

**注意 1：工具默认添加会出现转义符`\`，需要手动去除，否则之后运行会报错**

错误信息如下：

    $ openssl aes-256-cbc -K $encrypted_2cf61c1c8bc9_key -iv $encrypted_2cf61c1c8bc9_iv -in tencent_id_rsa.enc -out ~\/.ssh/tencent_id_rsa -d
    ~/.ssh/tencent_id_rsa: No such file or directory
    140369404802720:error:02001002:system library:fopen:No such file or directory:bss_file.c:398:fopen('~/.ssh/tencent_id_rsa','w')
    140369404802720:error:20074002:BIO routines:FILE_CTRL:system lib:bss_file.c:400:
    The command "openssl aes-256-cbc -K $encrypted_2cf61c1c8bc9_key -iv $encrypted_2cf61c1c8bc9_iv -in tencent_id_rsa.enc -out ~\/.ssh/tencent_id_rsa -d" failed and exited with 1 during .

**注意 2：如果要加密多个文件，需要首先打包这个文件再进行加密操作，因为命令行工具会覆盖加密条目，参考：[Encrypting multiple files](https://docs.travis-ci.com/user/encrypting-files/#encrypting-multiple-files)**

#### 解析私钥

需要设置私钥权限，否则`Travis CI`不执行该私钥

    before_install:
    - openssl aes-256-cbc -K $encrypted_2cf61c1c8bc9_key -iv $encrypted_2cf61c1c8bc9_iv
    -in tencent_id_rsa.enc -out ~/.ssh/tencent_id_rsa -d
    - chmod 600 ~/.ssh/tencent_id_rsa

需要添加私钥到缓存中

    after_success:
    - eval "$(ssh-agent -s)"
    - ssh-add ~/.ssh/tencent_id_rsa

## 部署到云服务器

有两种方法，一种是直接用`scp`命令将静态文件传输到云服务器指定位置，另一种就是部署到`git`的裸仓库，再通过钩子生成静态文件

当前使用第二种方法

    after_success:
    ...
    ...
    - git clone ubuntu@132.232.142.219:/home/ubuntu/git/zhujian.tech.git upload_git
    - cd upload_git
    - rm -rf !(.git)
    - cp -r ../public/* ./
    - git add .
    - git commit -m "Update blogs"
    - git push --force ubuntu@132.232.142.219:/home/ubuntu/git/zhujian.tech.git master
    ...
    ...

### `remote: error: denying non-fast-forward refs/heads/master (you should pull first)`

参考：[git – 如何强制将重置推送到远程存储库？](http://www.voidcn.com/article/p-semtiymh-bso.html)

这是由于远程仓库设置了不能快进，修改云服务器仓库配置文件`.git/config`

    $ cat config 
    [core]
        repositoryformatversion = 0
        filemode = true
        bare = true
        sharedrepository = 1
    [receive]
        denyNonFastforwards = true
    
将选项`denyNonFastforwards`设置为`false`，既可以执行强制推送操作了，代码也可修改如下

    after_success:
    ...
    ...
    # - git clone ubuntu@132.232.142.219:/home/ubuntu/git/zhujian.tech.git upload_git
    - mkdir upload_git
    - cd upload_git
    - git init
    # - rm -rf !(.git)
    - cp -r ../public/* ./
    - git add .
    - git commit -m "Update blogs"
    - git push --force ubuntu@132.232.142.219:/home/ubuntu/git/zhujian.tech.git master
    ...
    ...

或者在工程`_config.yml`中的`deploy`小节设置


