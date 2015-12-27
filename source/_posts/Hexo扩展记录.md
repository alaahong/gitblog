title: Hexo扩展记录
date: 2015-12-24 14:23:42
tags: [hexo,extends,plugin]
categories: hexo
---
# Hexo扩展记录
## Hexo生成sitemap站点地图和rss atom的方法
发现自带的系统缺了很多组件，一一补全。
<!-- more -->
    http://localhost:4000/sitemap.xml
![nositemapxml](/attachpic/nositemapxml.jpg)

    Administrator@Ian MINGW64 /f/blog/blog (master)
    $ cnpm install hexo-generator-sitemap
    hexo-generator-sitemap@1.0.1 node_modules\hexo-generator-sitemap

还是没生成

     Administrator@Ian MINGW64 /f/blog/blog (master)
    $ cnpm install hexo-generator-sitemap --save
    hexo-generator-sitemap@1.0.1 node_modules\hexo-generator-sitemap

    Administrator@Ian MINGW64 /f/blog/blog (master)
    $ cnpm install hexo-generator-baidu-sitemap --save
    hexo-generator-baidu-sitemap@0.1.2 node_modules\hexo-generator-baidu-sitemap
    └── hexo-generator-baidu-sitemap@0.0.8

注意 --save 即可

_config.yml中可以对这两组xml进行配置

    feed:
        type: atom ##feed类型 atom或者rss2
        path: atom.xml ##feed路径
        limit: 20  ##feed文章最小数量
    sitemap:
        path: sitemap.xml
    baidusitemap:
        path: baidusitemap.xml

generate即可

    Administrator@Ian MINGW64 /f/blog/blog (master)
    $ hexo g
    .
    .
    INFO  Generated: baidusitemap.xml
    INFO  Generated: atom.xml
    INFO  Generated: index.html
    INFO  Generated: sitemap.xml
    INFO  63 files generated in 3.64 s


## Hexo配置404页的方法
本处采用腾讯404

在<hexo_folder>/source下新建404.html
替换以下内容

    <!DOCTYPE html>
    <html lang="en">
    <head>
        <meta charset="UTF-8">
        <title>Title</title>
    </head>
    <body>
    <script type="text/javascript" src="http://www.qq.com/404/search_children.js" charset="utf-8"
            homePageUrl="http://www.ianzhang.cn" homePageName="BackToHome"></script>
    </body>
    </html>
    
![404demo](/attachpic/404demo.jpg)

## 增加 categories 和 tags
进入项目根目录, 新建模块
    
    $ hexo new page tags
    $ hexo new page categories
    
同时修改source下面categories和tags下 对应的 index.md
增加相应的 layout: categories   layout: tags
    
如果希望菜单栏有对应的选项的话,修改主题 _config.yml ,在menu下增加  
    
    Categories: /categories
    Tags: /tags

