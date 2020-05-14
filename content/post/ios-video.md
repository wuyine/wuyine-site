---
title: "video标签问题"
date: 2020-05-14
tags: ["note"]
categories: ["blog"]
---

# 写在前面
事情起因是公司官网有几个视频来演示功能的使用，类似于GIF图片一样放在页面中直接播放，然后发现 Iphone 手机中 Safari 浏览器中无法显示。因为自己对这部分知识比较欠缺，所以这里将这个问题记录下来。

# 问题解决
```
// html
<video autoplay loop muted>
  <source src="testvideo.mp4" type="video/mp4">
</video>
```
这个代码在pc端浏览器正常运行，没有什么问题，当运行在 Iphone 手机 Safari 浏览器中时就无法自动播放了。
经过一番搜索终于在stackoverflow中找到[答案](https://stackoverflow.com/questions/43570460/html5-video-autoplay-on-iphone#)，加上`playsinline`属性完美解决。问题虽然解决了，这部分知识还是需要记录下来。


早期在 IOS 中的 Safari 浏览器上，为了节省用户的流量和电量媒体数据仅当用户与页面交互时才加载视频数据。后面到 IOS8 中放宽了限制：可以添加`preload="metadata"`属性，允许 `<video> 和 <audio>` 元素加载足够的数据来确定媒体大小以及时长等基本信息。

## 动机
大家都喜欢在网页中加入GIF。但是GIF与现代视频编解码器相比，GIF格式是一种非常昂贵的动画图像编码方式。GIF的带宽成本可能高达十二倍，而电量使用成本却高达两倍。以至于许多最大的 GIF 提供者都已从GIF转向`<video>`元素，然而`<video>`必须要用户触发，尽管节省了网站的带宽成本和用户的电量，但是这是牺牲了用户的可用性为代价的。并且在 iPhone 上，`<video>` 开始播放时会进入全屏模式，这个场景下非常不友好。

>关于用户手势要求的注释：就是导致调用的JavaScript代码 video.play()必须直接来自于用户的触发 一 touchend，click，doubleclick，或keydown事件。因此，button.addEventListener('click', () => { video.play(); })可以正确触发， video.addEventListener('canplaythrough', () => { video.play(); })不满足要求，视频不会播放。

## WebKit 下策略
* ` <video autoplay>`对于满足以下条件的`autoplay`属性将会生效：
  + `<video>` 如果元素`autoplay`的源媒体中不包含音频，则无需用户任何手势即可自动播放。
  + `<video muted> `元素也将被允许在没有用户手势的情况下自动播放。
  + 如果某个`<video>`元素获得音频或在没有用户手势的情况下变为静音，则播放将暂停。
  + `<video autoplay>` 元素仅在屏幕上可见时才开始播放，例如当它们滚动到视口中，通过CSS可见并插入DOM时。
  + `<video autoplay>` 如果元素变为不可见，则播放将暂停，例如通过滚动到视口之外。
  
* `<video>` 对于满足以下条件`play()`方法会执行成功：
  + `<video>` 如果源媒体中不包含音频，或者`muted`属性为`true`，则无需用户任何手势。
  + 如果某个`<video>`元素获得音频或在没有用户手势的情况下变为静音，则播放将暂停。
  + ` <video>`当元素在屏幕上不可见或不在视口中时，将允许`play()`播放。
  + 如果不满足这些条件中的任何一个将会返回一个`reject`的`Promise`对象。
  
* 在iPhone上，`<video playsinline>`现在将允许元素内联播放，并且在开始播放时不会自动进入全屏模式。
  + `<video>`没有`playsinline`属性的元素将继续需要全屏模式才能在iPhone上播放。
  + 当以捏合手势退出全屏时，`<video>`元素没有`playsinline`属性也会继续内联播放。


# 关于 playsinline 属性

> 该属性已经添加到HTML规范中，旧版本中可以使用 `webkit-playsinline`