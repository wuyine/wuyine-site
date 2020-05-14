---
layout:       post
title:        "使用Hugo搭建一个博客网站"
date:         2020-05-13T22:06:25+08:00
categories:   ["blog" ]
tags:         ["note"]
image:        "/img/post-bg-lake.jpg"
---

工作快四年一直都没写作的习惯，学习的东西都没记录下来，感觉到很长时间没有刚开始编程时的那种进步的快感了，所以搭建一个博客网站来提供一个写作的环境，和一个记录自己学习的地方，使用开hugo，也是为了快速的将这个博客网站搭建好。

# Hugo 介绍
Hugo 是一个使用go语言写的静态生成器，官方文档的描述大概就是Hugo构建速度极快、完全跨平台、开发中支持liveReload、丰富的主题以及部署方便等优点。

## Hugo安装
macOS和linux（安装了Homebrew的话）
```
brew install hugo
```
Chocolatey(windows)
```
choco install hugo -confirm
// or if you need the “extended” Sass/SCSS version:
choco install hugo-extended -confirm 
```
Scoop (Windows)
```
scoop install hugo
// or if you need the “extended” Sass/SCSS version:
scoop install hugo-extended
```
其他安装方式建议阅读[官方文档](https://gohugo.io/getting-started/installing/)

## 使用Hugo命令创建网址
```
hugo new site sitename
```
## 添加一个主题
1. 进入[主题选择页面](https://themes.gohugo.io/)下载自己喜欢的主题
2. 将主题代码拷贝到项目下themes目录下
3. 将theme = "your themeName" 写到 config.toml配置文件中

## 写第一篇博客文章
使用 `hugo new posts/my-first-post.md` 新建一个页面，可以看到在content目录下的posts目录下出现my-first-post.md文件，里面会有以下内容
```
---
title: "My First Post"
date: 2020-05-13T22:06:25+08:00
draft: true
---
```
## 博客预览
终端输入：hugo server -D 可以看到服务器运行成功，打开浏览器输入 [http://localhost:1313/](http://localhost:1313/) 即可预览

## build
运行 `hugo` 将会把博客文件生成到项目根目录下`public`目录中

# 将博客网站部署到 github pages
网络上已经有很多教程了，也可以直接阅读[官方教程](https://pages.github.com/)，我这里简单的把步骤写下来，自己做个记录。

1. 在自己的 github 上新建一个仓库，仓库名为 username.github.io；username 为自己的用户名。
2. 在`public`目录下
```
git init 
git add .
git commit -m 'first commit'
git remote add origin 远程仓库地址
git push -u origin master
```
3. 等几分钟就可以访问  https://{your name}.github.io 看到你的博客部署成功了。