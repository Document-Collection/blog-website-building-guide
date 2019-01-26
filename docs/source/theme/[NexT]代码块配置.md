
# [NexT]代码块配置

## 高亮主题

`NexT`提供了`5`种代码块高亮主题

    # Code Highlight theme
    # Available values: normal | night | night eighties | night blue | night bright
    # https://github.com/chriskempson/tomorrow-theme
    highlight_theme: normal

参考[chriskempson/tomorrow-theme](https://github.com/chriskempson/tomorrow-theme)和[设置代码高亮主题](http://theme-next.iissnan.com/theme-settings.html#syntax-highlight-scheme)

## 代码块复制

修改主题`_config.yml`

    codeblock:
        # Manual define the border radius in codeblock
        # Leave it empty for the default 1
        border_radius:
        # Add copy button on codeblock
        copy_button:
            enable: false
            # Show text copy result
            show_result: false

设置属性`copy_button`为`true`，同时设置`show_result`为`true`，显示代码复制结果