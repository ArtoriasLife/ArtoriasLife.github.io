---
title: 搭建Hexo个人博客
date: 2024-09-03 14:54:56
update: 2024/09/7
categories:
- [Life,blogs,Hexo]
tags:
- blogs
- Hexo
---

本篇文章主要介绍用`nvm`管理工具来搭建`Hexo`博客框架的操作流程

## nvm

`nvm`是`node.js version management`的简写，也就是`node.js`的一个版本管理工具，方便管理`node.js`的版本

本篇文章仅介绍在`Windows`系统下的安装，其他系统安装流程详细信息请参见[NVM官网](https://nvm.uihtm.com/)

注意事项：若之前下载安装过相关`node.js`版本，请先卸载再安装

### 下载nvm

访问[GitHub](https://github.com/coreybutler/nvm-windows/releases)下载最新的`Windows`版本`nvm-setup.exe`

### 安装nvm

1. 双击`nvm-setup.exe`应用程序，点击同意协议

2. 选择`nvm`安装路径以及`node.js`安装路径，然后点击`Install`安装即可

3. 按下`Win + R`输入`cmd`，再输入`nvm`命令，返回结果会显示`Running version 1.1.12.`等命令说明，安装成功后，下面继续安装`node.js`

## Node.js环境

> Node.js® 是一个免费、开源、跨平台的 JavaScript 运行时环境，它让开发人员能够创建服务器、Web 应用、命令行工具和脚本

有关详细信息请访问[node.js官网](https://nodejs.org/zh-cn)

### nvm切换国内镜像

建议先切换成国内镜像进行安装，来避免不必要的麻烦，下面使用命令行切换，二者选其一就行

1. 阿里云镜像

```bash
nvm npm_mirror https://npmmirror.com/mirrors/npm/ 
nvm node_mirror https://npmmirror.com/mirrors/node/
```

2. 腾讯云镜像 

```bash
nvm npm_mirror http://mirrors.cloud.tencent.com/npm/ 
nvm node_mirror http://mirrors.cloud.tencent.com/nodejs-release/
```

### nvm安装node.js

1. 显示可下载版本的部分列表，结果显示如下

```bash
nvm list available
```

```bash
# 结果显示如下
|   CURRENT    |     LTS      |  OLD STABLE  | OLD UNSTABLE |
|--------------|--------------|--------------|--------------|
|    22.7.0    |   20.17.0    |   0.12.18    |   0.11.16    |
|    22.6.0    |   20.16.0    |   0.12.17    |   0.11.15    |
|    22.5.1    |   20.15.1    |   0.12.16    |   0.11.14    |
|    22.5.0    |   20.15.0    |   0.12.15    |   0.11.13    |
|    22.4.1    |   20.14.0    |   0.12.14    |   0.11.12    |
|    22.4.0    |   20.13.1    |   0.12.13    |   0.11.11    |
|    22.3.0    |   20.13.0    |   0.12.12    |   0.11.10    |
|    22.2.0    |   20.12.2    |   0.12.11    |    0.11.9    |
|    22.1.0    |   20.12.1    |   0.12.10    |    0.11.8    |
|    22.0.0    |   20.12.0    |    0.12.9    |    0.11.7    |
|    21.7.3    |   20.11.1    |    0.12.8    |    0.11.6    |
|    21.7.2    |   20.11.0    |    0.12.7    |    0.11.5    |
|    21.7.1    |   20.10.0    |    0.12.6    |    0.11.4    |
|    21.7.0    |    20.9.0    |    0.12.5    |    0.11.3    |
|    21.6.2    |   18.20.4    |    0.12.4    |    0.11.2    |
|    21.6.1    |   18.20.3    |    0.12.3    |    0.11.1    |
|    21.6.0    |   18.20.2    |    0.12.2    |    0.11.0    |
|    21.5.0    |   18.20.1    |    0.12.1    |    0.9.12    |
|    21.4.0    |   18.20.0    |    0.12.0    |    0.9.11    |
|    21.3.0    |   18.19.1    |   0.10.48    |    0.9.10    |

This is a partial list. For a complete list, visit https://nodejs.org/en/download/releases
```

2. 根据选择安装最新或指定版本

```bash
# 安装最新版本，一般不建议安装最新版本
nvm install latest

# 安装指定版本，例如安装 20.16.0 版本
nvm install 20.16.0
```

```bash
# 结果显示如下
Downloading node.js version 20.16.0 (64-bit)...
Extracting node and npm...
Complete
npm v10.8.1 installed successfully.


Installation complete. If you want to use this version, type

nvm use 20.16.0
```

3. 查看目前已经安装的版本

```bash
nvm list
nvm ls
```

```bash
# 结果显示如下
* 20.17.0 (Currently using 64-bit executable)
  20.16.0
```

笔者前面已经安装过相关版本，在使用的 node 版本前面有 `*`标记

4. 使用或切换到指定版本

```bash
# 切换指定版本，例如切换到 20.16.0 版本
nvm use 20.16.0
```

5. 检查是否成功，返回相关版本号则代表正常

```bash
# 查看 node 版本号
node -v

# 查看 npm 版本号
npm -v
```

## 安装Git

访问[64-bit Git for Windows Setup](https://github.com/git-for-windows/git/releases/download/v2.46.0.windows.1/Git-2.46.0-64-bit.exe).进行下载后安装，安装目录自行选择，之后一直选择`next`就行

详细安装流程可参考[Git 详细安装教程-CSDN博客](https://blog.csdn.net/mukes/article/details/115693833)

## Hexo博客框架

### 采用 cnpm 替代默认的 npm

由于国内访问`npm`源比较慢，故此采用`cnpm`，配置命令如下

```bash
npm install -g cnpm --registry=https://registry.npmmirror.com
```

- `cnpm`相关命令

  - 安装模块`cnpm install [name]`

  - 同步模块`cnpm sync cnpmcore`

如果只是想使用默认的`npm`命令行工具，也可通过如下设置国内镜像

```bash
npm config set registry https://registry.npmmirror.com
```

### 安装Hexo博客框架

1. 两种命令行安装方式

```bash
#利用cnpm安装模块命令
cnpm install hexo-cli -g

#利用默认的 npm 命令
npm install hexo-cli -g
```

2. 按下`Win + R`输入`cmd`进入控制台后，创建并初始化博客文件根目录

```bash
#切换到D盘
D:

#在当前盘下新建 Blogs 文件夹
mkdir Blogs

# 初始化 Blogs 文件夹
hexo init Blogs
```

```bash
# 初始化完成结果如下所示
INFO  Cloning hexo-starter https://github.com/hexojs/hexo-starter.git
INFO  Install dependencies
INFO  Start blogging with Hexo!
```

3. 更新相关依赖

```bash
# 进入 Blogs 文件夹
cd Blogs

# 更新相关依赖，这里使用的cnpm，若想使用npm，将其替换就行
cnpm install

#查看项目文件夹结构
dir
```

```bash
#项目文件夹结构如下所示
.
├── _config.yml
├── package.json
├── scaffolds
├── source
|   ├── _drafts
|   └── _posts
└── themes
```

3. 输入以下命令清除缓存并生成静态文件后，启动本地服务

```bash
hexo clean &&　hexo generate && hexo server
```

4. 访问博客网站，默认情况下，访问网址为： `http://localhost:4000/`
