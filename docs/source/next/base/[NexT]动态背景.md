
# [NexT]动态背景

参考：[theme-next/theme-next-canvas-nest](https://github.com/theme-next/theme-next-canvas-nest)

进入主题包路径

    /path/to/themes/next/

下载

    git clone https://github.com/theme-next/theme-next-canvas-nest source/lib/canvas-nest

在主题`_config.yml`文件中设置`cavas_nest`为`true`

    # Canvas-nest
    # Dependencies: https://github.com/theme-next/theme-next-canvas-nest
    canvas_nest:
        enable: false
        onmobile: true # display on mobile or not
        color: '0,0,255' # RGB values, use ',' to separate
        opacity: 0.5 # the opacity of line: 0~1
        zIndex: -1 # z-index property of the background
        count: 99 # the number of lines

* `onmobile`：是否在手机上显示
* `color`：`RGB`颜色值，默认下显示蓝色
* `opacity`：线条的透明度
* `zIndex`：背景的`z`层属性
* `count`：线条数量