
# [gulp]性能优化

[使用gulp插件加速hexo博客](https://blog.csdn.net/jinggege0818/article/details/82461795)

使用[gulp](https://gulpjs.com/)以及插件来压缩`html/css/js/image`等静态资源，加快博客访问速度

## 下载

下载`gulp`以及相关模块

```
$ npm install --save gulp gulp-cli gulp-htmlclean gulp-htmlmin gulp-clean-css gulp-uglify gulp-imagemin
```

* gulp-htmlclean：清理html
* gulp-htmlmin：压缩html
* gulp-clean-css：压缩css
* gulp-uglify：混淆js
* gulp-imagemin：压缩图片

当前版本

```
$ gulp -v
CLI version 2.1.0
Local version 4.0.0
```

### `gulp`失效

安装完成`gulp`后，运行失效

```
$ gulp
No command 'gulp' found, did you mean:
 Command 'gslp' from package 'ghostscript' (main)
gulp: command not found
```

在`package.json`中有相关配置信息

```
$ cat package.json | grep gulp
    "gulp": "^4.0.0",
    "gulp-clean-css": "^4.0.0",
    "gulp-cli": "^2.1.0",
    "gulp-htmlclean": "^2.7.22",
    "gulp-htmlmin": "^5.0.1",
    "gulp-imagemin": "^5.0.3",
    "gulp-uglify": "^3.0.2",
```

母鸡，我的解决方法是删掉本地`node_modules`文件夹，使用`cnpm`重新安装一遍

## 配置

在当前路径编辑`gulpfile.js`文件

```
var gulp = require('gulp');
var minifycss = require('gulp-clean-css');
var uglify = require('gulp-uglify');
var htmlmin = require('gulp-htmlmin');
var htmlclean = require('gulp-htmlclean');
var imagemin = require('gulp-imagemin');
 
// 压缩html
gulp.task('minify-html', function() {
    return gulp.src('./public/**/*.html')
        .pipe(htmlclean())
        .pipe(htmlmin({
            removeComments: true,
            minifyJS: true,
            minifyCSS: true,
            minifyURLs: true,
        }))
        .pipe(gulp.dest('./public'))
});
// 压缩css
gulp.task('minify-css', function() {
    return gulp.src('./public/**/*.css')
        .pipe(minifycss({
            compatibility: 'ie8'
        }))
        .pipe(gulp.dest('./public'));
});
// 压缩js
gulp.task('minify-js', function() {
    return gulp.src('./public/js/**/*.js')
        .pipe(uglify())
        .pipe(gulp.dest('./public'));
});
// 压缩图片
gulp.task('minify-images', function() {
    return gulp.src('./public/images/**/*.*')
        .pipe(imagemin(
        [imagemin.gifsicle({'optimizationLevel': 3}), 
        imagemin.jpegtran({'progressive': true}), 
        imagemin.optipng({'optimizationLevel': 7}), 
        imagemin.svgo()],
        {'verbose': true}))
        .pipe(gulp.dest('./public/images'))
});
// 默认任务
gulp.task('default', gulp.series(
    'minify-html','minify-css','minify-js','minify-images')
    );
// gulp.task('default', [
//     'minify-html','minify-css','minify-js','minify-images'
// ]);
```

## 执行

在运行完`hexo generate`后就可以执行`gulp`

```
$ gulp
[19:24:47] Using gulpfile ~/Documents/zjzstu.github.com/blogs/gulpfile.js
[19:24:47] Starting 'default'...
[19:24:47] Starting 'minify-html'...
[19:24:49] Finished 'minify-html' after 2.46 s
[19:24:49] Starting 'minify-css'...
[19:24:50] Finished 'minify-css' after 518 ms
[19:24:50] Starting 'minify-js'...
[19:24:50] Finished 'minify-js' after 575 ms
[19:24:50] Starting 'minify-images'...
...
...
```

再执行`hexo server`即可

## `gulp`语法问题

`gulp4.0`之前之后的语法有区别，有可能会出现问题（*我使用第二种*）：

```
$ gulp
assert.js:350
    throw err;
    ^

AssertionError [ERR_ASSERTION]: Task function must be specified
    at Gulp.set [as _setTask] (/home/zj/Documents/zjzstu.github.com/blogs/node_modules/_undertaker@1.2.0@undertaker/lib/set-task.js:10:3)
    at Gulp.task (/home/zj/Documents/zjzstu.github.com/blogs/node_modules/_undertaker@1.2.0@undertaker/lib/task.js:13:8)
    at Object.<anonymous> (/home/zj/Documents/zjzstu.github.com/blogs/gulpfile.js:47:6)
    at Module._compile (internal/modules/cjs/loader.js:689:30)
    at Object.Module._extensions..js (internal/modules/cjs/loader.js:700:10)
    at Module.load (internal/modules/cjs/loader.js:599:32)
    at tryModuleLoad (internal/modules/cjs/loader.js:538:12)
    at Function.Module._load (internal/modules/cjs/loader.js:530:3)
    at Module.require (internal/modules/cjs/loader.js:637:17)
    at require (internal/modules/cjs/helpers.js:22:18)
```

两种解决方案：

一是将`gulp`回滚到`3.9.1`，参考[运行gulp项目报错：AssertionError: Task function must be specified。](https://blog.csdn.net/adley_app/article/details/85285754)

二是修改`gulpfile.js`文件，参考[运行gulp项目报错：AssertionError: Task function must be specified。](https://blog.csdn.net/qq_31975963/article/details/83034450)

## `font-awesome`加载失败

`gulp`压缩完成后，发现图标显示出错，`font-awesome`加载失败

参考[小图标不显示 [check hexo-filter-optimize, and CDN configs maybe]](https://github.com/theme-next/hexo-filter-optimize/issues/10)和[ 添加插件后fontawesome图标失效 #8 ](https://github.com/theme-next/hexo-filter-optimize/issues/8)

有两种解决方案（*我使用第二种*）：

1. 取消`css`压缩

2. 使用`cdn`

修改主题`_config.yml`，添加

```
fontawesome: https://cdn.bootcss.com/font-awesome/4.6.2/css/font-awesome.min.css
```