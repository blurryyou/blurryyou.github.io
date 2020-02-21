---
layout: post
title: Line Ending
featured: true
tags: [coding]
---

Line Ending 

记录一个大概只有我这种菜鸟才会遇到的问题。

在家办公的情况下，很多设施都没有办公室那么完备。

只用笔记本，就难以解决屏幕和键盘高度的矛盾。

我家里有台式机，有外接显示器，有外接键盘，但是却没有 Type-C 转换头。

无奈就只好临时从 Mac 换到 Windows 上来工作。

在执行 shell 脚本的时候，却反复出错：

````
$'\r': command not found
````

在阮一峰的文章[回车和换行](https://www.ruanyifeng.com/blog/2006/04/post_213.html)里看到，Windows 系统里的回车是 `\r\n`，在 Unix/Mac 里是 `\n`，这就导致了我在 Mac 下可以正常执行的 shell 在 Windows 环境中报错。

知道原因之后，解决方案也就非常简单了。

我使用的编辑器是 Sublime Text 3，通过 `View > Line Endings > Unix` 转换 Line Ending，重新保存 shell，再次执行就 OK 了。 