
# hexo配置

参考：[Configuration](https://hexo.io/docs/configuration)

`hexo`工程配置文件是`_config.yml`

    # Hexo Configuration
    ## Docs: https://hexo.io/docs/configuration.html
    ## Source: https://github.com/hexojs/hexo/

    # Site
    title:                 // 网站标题
    subtitle:              // 网站子标题
    description:           // 网站描述
    keywords:              // 网站关键字
    author: John Doe       // 作者
    language:              // 语言，默认英语。与主题的语言设置有关，默认主题landscape的中文为zh-CN
    timezone:              // 时区

    # URL
    ## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
    url: http://yoursite.com                        // 网站地址
    root: /                                         // 网站根路径
    permalink: :year/:month/:day/:title/            // 生成静态文件保存格式
    permalink_defaults:

    # Directory
    source_dir: source                              // 源文件目录
    public_dir: public                              // 静态文件目录
    tag_dir: tags                                   // 标签目录
    archive_dir: archives                           // 存档文件目录
    category_dir: categories                        // 类别目录
    code_dir: downloads/code                        // 包含代码目录，源文件目录的子目录
    i18n_dir: :lang
    skip_render:

    # Writing
    new_post_name: :title.md # File name of new posts              // 新文章的文件名格式
    default_layout: post                                           // 默认布局
    titlecase: false # Transform title into titlecase              // 标题是否大小写
    external_link: true # Open external links in new tab
    filename_case: 0                                               // 文件名转换成小写:1或大写:2
    render_drafts: false                                           // 显示草稿
    post_asset_folder: false                                       // 是否同步生成资源文件夹
    relative_link: false
    future: true
    highlight:
    enable: true
    line_number: true
    auto_detect: false
    tab_replace:
    
    # Home page setting
    # path: Root path for your blogs index page. (default = '')
    # per_page: Posts displayed per page. (0 = disable pagination)
    # order_by: Posts order. (Order by date descending by default)
    index_generator:
    path: ''
    per_page: 10
    order_by: -date
    
    # Category & Tag
    default_category: uncategorized
    category_map:
    tag_map:

    # Date / Time format
    ## Hexo uses Moment.js to parse and display date
    ## You can customize the date format as defined in
    ## http://momentjs.com/docs/#/displaying/format/
    date_format: YYYY-MM-DD
    time_format: HH:mm:ss

    # Pagination
    ## Set per_page to 0 to disable pagination
    per_page: 10                                                 // 在一页上显示的文章数量。0禁用分页
    pagination_dir: page                                         // 分页目录

    # Extensions
    ## Plugins: https://hexo.io/plugins/
    ## Themes: https://hexo.io/themes/
    theme: landscape                                             // 主题

    # Deployment
    ## Docs: https://hexo.io/docs/deployment.html
    deploy:
    type: git                                                    // 远程服务器类型
    repo: https://github.com/zjZSTU/zjzstu.github.com.git
    branch: master
