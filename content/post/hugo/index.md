---
title: "Hugo + Stack 博客搭建指南"
date: 2021-09-21T05:37:05+08:00
draft: false
description: "基于Hugo和hugo-theme-stack主题的博客搭建过程"
image: "gakki.png"
tags:
  - hugo
categories:
    - 部署
---

# Hugo + Stack 博客搭建指南

Hugo是基于Go语言开发的静态网站构建工具。本博客采用hugo-theme-stack主题搭建。

## Hugo下载安装

1. 打开 Hugo 官方 GitHub 的 [**Releases**](https://github.com/gohugoio/hugo/releases) 页面
2. 选择最新的版本下载（选择 `hugo_extended_0.88.1_Windows-64bit.zip`）
3. 将压缩包内的 `hugo.exe` 文件解压至 `D:\Hugo` 文件夹目录下
4. 在 `我的电脑`鼠标右键，打开属性
5. 依次点击 `高级系统设置` - `环境变量` ，编辑系统变量中的 `Path`
6. 在环境变量界面中双击空白行，添加 `D:\Hugo`，点击确定

确认 Hugo 是否安装成功：

```
hugo version
```

## 创建站点

切换某个目录下，创建站点文件夹：

```
hugo new site MySite
```

## 主题下载

主题的挑选可以到官方的 [**主题页面**](https://themes.gohugo.io/)

本博客采用[hugo-theme-stack主题](https://github.com/CaiJimmy/hugo-theme-stack/)，该主题由国人开发维护，社区比较活跃， 强力推荐。

```
cd MySite
git init
git submodule add https://github.com/CaiJimmy/hugo-theme-stack.git themes/hugo-theme-stack
# 主题有更新时，执行git submodule update
```

复制`MySite\themes\hugo-theme-stack\exampleSite\config.yaml`到`MySite\`目录下，删除默认的`config.toml`

复制`MySite\themes\hugo-theme-stack\exampleSite\content\`目录下的文件夹到`MySite\content\`

```
# config.yaml修改
theme: hugo-theme-stack  
favicon: /img/github-alt.svg  # favicon文件需MySite\static\img\下
comments:
        enabled: false  # 关闭评论
```

更多配置请见：[hugo-theme-stack主题配置](https://docs.stack.jimmycai.com/zh/configuration/)

## 创建文章

使用如下命令，创建一篇文章：

```
# 创建带有hugo front matter的文章，draft（草稿）
# 在front matter添加tags、categories、image,可为文章添加标签、分类、特色图片
hugo new post/my-first-post.md
```

2种方式创建含图片的文章：

1. 在`content/post`目录下创建文件夹，文件夹下包含图片文件和文章，文章名需为index.md(Hugo Page Bundles)

2. 直接在`content/post`目录下建立文章文件，图片引用`MySite/static`下的图片

   ```
   例如引用MySite/static/img/github-alt.svg图片：![图片名称](/img/github-alt.svg)
   ```

## 启动 Hugo 服务

使用以下命名启动 Hugo 本地预览服务：

```
# -D表示显示草稿
hugo server -D
```

打开 [**http://localhost:1313/**](http://localhost:1313/) ，即可看到实时预览的站点（在本地的任何修改，将即时更新）。

## 其他

- [Quick Start · Hugo](https://gohugo.io/getting-started/quick-start/)
- [Emoji cheat sheet](http://www.emoji-cheat-sheet.com/):yum:

