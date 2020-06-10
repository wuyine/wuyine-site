---
title:       "Hailstone"
subtitle:    ""
description: ""
date:        2020-06-10
author:      "wuyine"
image:        "/img/post-bg-lake.jpg"
tags:         ["note"]
categories:  ["Tech" ]
---

## 算法有穷性
![hailstone](/img/hailstone.jpg)

```js
function hailstone(n) {
  var length = 1;
  while( n > 1) {
    if ( n % 2 ) {
      n = 3 * n + 1;
    } else {
      n /= 2;
    }
    length++;
  }
  return length;
}

// hailstone(42) = { 42, 21, 64, 32, ..., 1}
```