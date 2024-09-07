---
title: Hexo博客shoka主题配置
date: 2024-09-03 15:46:28
categories:
- [Life,blogs,Hexo]
tags:
- blogs,Hexo
---
本篇文章主要介绍Hexo博客下的shoka主题基本配置
其他详细教程请参考[Theme Shoka Documentation](https://shoka.lostyu.me/computer-science/note/theme-shoka-doc/)

卸载默认的markdown文件渲染器

cnpm un hexo-renderer-marked --save

安装主题相关依赖

cnpm i hexo-renderer-multi-markdown-it

cnpm i hexo-autoprefixer

cnpm i hexo-algoliasearch

cnpm i hexo-symbols-count-time

cnpm i hexo-feed

cnpm i pangu

cnpm i hexo-util

设置博客根目录下的_config.yml文件，将theme参数设置为shoka

启动博客

hexo clean && hexo g && hexo s

浏览文章页面时发现代码块显示有问题，关闭服务，再次更改_config.yml文件中的参数配置如下

syntax_highlighter: #highlight.js
highlight:
  enable: false
  #line_number: true
  #auto_detect: false
  #tab_replace: ''
  #wrap: true
  #hljs: false
prismjs:
  enable: false
  #preprocess: true
  #line_number: true
  #tab_replace: ''

重新启动博客，刷新一下浏览器缓存，代码块显示正常

hexo clean && hexo g && hexo s
