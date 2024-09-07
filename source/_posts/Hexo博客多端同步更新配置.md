---
title: Hexo博客多端同步更新配置
date: 2024-09-03 15:59:57
categories:
- [Life,blogs,Hexo]
tags:
- blogs,Hexo
---
本篇文章主要介绍如何在不同设备端利用git来实现博客同步更新

详细过程请参考[GiHub + Hexo 真·从零开始搭建个人博客 - Fany Full's Blog](https://fanyfull.github.io/2021/10/16/Github-Hexo-真-从零开始搭建-GitHub-静态博客/#前言)

[Hexo在多台电脑上提交和更新_hexo 多机更新-CSDN博客](https://blog.csdn.net/K1052176873/article/details/122879462)



如果你的博客系统部署在GitHub上，首先进入_config.yml配置文件，修改以下参数

```yaml
# Deployment

## Docs: https://hexo.io/docs/one-command-deployment

deploy:
  type: git
  repo: git@github.com:username/username.github.io.git
  branch: main
```

设置Git代理为socks端口

在 Git Bash 中敲入设置全局代理的命令：

git config --global http.proxy 'socks5://127.0.0.1:4781'
git config --global https.proxy 'socks5://127.0.0.1:4781'

设置Github上的默认分支

