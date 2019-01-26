
# [NexT]首页预览

默认在首页显示每篇文章的全部内容，可使用`NexT`主题设置预览模式

    # Automatically scroll page to section which is under <!-- more --> mark.
    scroll_to_more: true

    ...
    ...

    # Automatically Excerpt. Not recommend.
    # Use <!-- more --> in the post to control excerpt accurately.
    auto_excerpt:
        enable: false
        length: 150

    # Read more button
    # If true, the read more button would be displayed in excerpt section.
    read_more_btn: true

`NexT`提供了两种预览模式

## 设置预览内容

在文章中嵌入标记

    <!-- more -->

会将其之上的内容作为预览内容

## 固定预览内容

设置属性`auto_excerpt`为`true`，会固定预览的长度