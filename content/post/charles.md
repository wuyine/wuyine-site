---
title:       "Charles抓包工具安装使用"
subtitle:    ""
description: ""
date:        2020-07-10
author:      "wuyine"
image:        "/img/post-bg-lake.jpg"
tags:         ["note"]
categories:  ["Tech" ]
---

## 安装

[进入官网](https://www.charlesproxy.com/download/)下载对应系统Charles安装包。


## 配置
进入Charles Proxy -> macOS Proxy 勾选， 就可以看到代理设置了

### 看不到 Response 
Charles -> Preferences -> Viewers -> Combine request and response 取消勾选

## https抓包

1. 安装证书：Help -> SSL Proxying -> install Charles Root Certificate 下载
2. 进入 钥匙串访问  证书 -> 双击 Charles Proxy CA -> 信任

## iphone手机抓包

1. 安装证书： chls.pro/ssl
2. 设置信任证书


### Tools -> Map Local
可代理资源为本地文件，开发调试神器