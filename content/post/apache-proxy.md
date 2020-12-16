---
title:       "Apache 代理配置"
subtitle:    ""
description: ""
date:        2020-12-16
author:      "wuyine"
image:        "/img/post-bg-lake.jpg"
tags:         ["note"]
categories:  ["Tech" ]
---

1. ProxyPass /nc/front/ http://127.0.0.1:8000/ 路径配置

2. ProxyPassMatch ^/nc/(.*) http://127.0.0.1:8000/$1 正则匹配