
# FAQ

执行`hexo server`出错

```
Error: ENOSPC: System limit for number of file watchers reached, watch '/home/zj/Documents/zjzstu.github.com/blogs/source/_posts/从CSDN到Hexo.md'
    at FSWatcher.start (internal/fs/watchers.js:165:26)
    at Object.watch (fs.js:1254:11)
    at createFsWatchInstance (/home/zj/Documents/zjzstu.github.com/blogs/node_modules/chokidar/lib/nodefs-handler.js:37:15)
    at setFsWatchListener (/home/zj/Documents/zjzstu.github.com/blogs/node_modules/chokidar/lib/nodefs-handler.js:80:15)
    at FSWatcher.NodeFsHandler._watchWithNodeFs (/home/zj/Documents/zjzstu.github.com/blogs/node_modules/chokidar/lib/nodefs-handler.js:228:14)
    at FSWatcher.NodeFsHandler._handleFile (/home/zj/Documents/zjzstu.github.com/blogs/node_modules/chokidar/lib/nodefs-handler.js:255:21)
    at FSWatcher.<anonymous> (/home/zj/Documents/zjzstu.github.com/blogs/node_modules/chokidar/lib/nodefs-handler.js:473:21)
    at FSReqWrap.oncomplete (fs.js:155:5)
```

参考：[Ubuntu Error: ENOSPC:System limit for number of file watchers reached](https://www.jianshu.com/p/0e134dd43ba0)

修改系统配置文件`/etc/sysctl.conf`，添加

```
fs.inotify.max_user_watches=524288
```

更新

```
$ sudo sysctl -p
fs.inotify.max_user_watches = 524288
```

再次执行`hexo server`就可以了