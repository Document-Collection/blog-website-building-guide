
# [clipboard.js]代码块复制

参考：[Hexo NexT 代码块复制功能](https://www.jianshu.com/p/3e9d614c1e77)

下面使用[clipboard.js](https://github.com/zenorocha/clipboard.js)进行代码块复制

## 本地安装

    npm install clipboard --save

## NexT主题配置

下载配置文件[clipboard.min.js](https://raw.githubusercontent.com/zenorocha/clipboard.js/master/dist/clipboard.min.js)到`themes/next/source/js/src`文件夹

在`themes/next/source/js/src`目录下创建文件`clipboard-use.js`，内容如下：

    /*页面载入完成后，创建复制按钮*/
    !function (e, t, a) { 
    /* code */
    var initCopyCode = function(){
        var copyHtml = '';
        copyHtml += '<button class="btn-copy" data-clipboard-snippet="">';
        copyHtml += '  <i class="fa fa-globe"></i><span>copy</span>';
        copyHtml += '</button>';
        $(".highlight .code pre").before(copyHtml);
        new ClipboardJS('.btn-copy', {
            target: function(trigger) {
                return trigger.nextElementSibling;
            }
        });
    }
    initCopyCode();
    }(window, document);

在`themes\next\source\css\_custom\custom.style`文件中添加如下内容：

    //代码块复制按钮
    .highlight{
    //方便copy代码按钮（btn-copy）的定位
    position: relative;
    }
    .btn-copy {
        display: inline-block;
        cursor: pointer;
        background-color: #eee;
        background-image: linear-gradient(#fcfcfc,#eee);
        border: 1px solid #d5d5d5;
        border-radius: 3px;
        -webkit-user-select: none;
        -moz-user-select: none;
        -ms-user-select: none;
        user-select: none;
        -webkit-appearance: none;
        font-size: 13px;
        font-weight: 700;
        line-height: 20px;
        color: #333;
        -webkit-transition: opacity .3s ease-in-out;
        -o-transition: opacity .3s ease-in-out;
        transition: opacity .3s ease-in-out;
        padding: 2px 6px;
        position: absolute;
        right: 5px;
        top: 5px;
        opacity: 0;
    }
    .btn-copy span {
        margin-left: 5px;
    }
    .highlight:hover .btn-copy{
    opacity: 1;
    }

修改文件`themes\next\layout\_layout.swig`，在`<body>`块末尾添加

    <!-- 代码块复制功能 -->
    <script type="text/javascript" src="/js/src/clipboard.min.js"></script>  
    <script type="text/javascript" src="/js/src/clipboard-use.js"></script>