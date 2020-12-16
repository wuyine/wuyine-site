---
title:       "Eggjs 使用记录"
subtitle:    ""
description: ""
date:        2020-12-14
author:      "wuyine"
image:        "/img/post-bg-lake.jpg"
tags:         ["note"]
categories:  ["Tech" ]
---

问题1：开发环境```EGG_SERVER_ENV=dev egg-bin dev``` 编辑代码不会热更新代码
解决方案：删除```EGG_SERVER_ENV=dev```即可，原因未知，后续查看 egg 源码查找问题所在