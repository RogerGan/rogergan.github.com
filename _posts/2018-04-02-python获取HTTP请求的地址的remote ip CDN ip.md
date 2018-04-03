---
layout:     post
title:      "python获取HTTP请求的地址的remote ip CDN ip"
subtitle:   "技术，python"
date:       2018-04-02
author:     "chaojiang"
header-img: "img/bg-myblog.jpg"
tags:
    - python
---


之前开发了一个检测程序，用来检测服务的可靠性，相当于是一个拨测程序，不停的head一个下载地址来检查。

周末监控一直告警，后面自动恢复。

```
一般处理就是网络抖动了，但是咱们要打破砂锅问到底。

```

dig一下，发现下载域下有多个CDNip。

这次程序没有打出ip，导致问题最终还是没法找阿里云的技术支持来定位，后续加上，代码如下。

```
r = requests.head(url, timeout=30, headers=headers, stream=True, verify=False)
ip_port=r.raw._connection.sock.getpeername()

```



### 参考资料
程序员的好朋友：https://stackoverflow.com/questions/22492484/how-do-i-get-the-ip-address-from-a-http-request-using-the-requests-library

Python requests库官方介绍：：http://docs.python-requests.org/zh_CN/latest/user/advanced.html

阿里云CDN官方介绍：https://www.alibabacloud.com/help/zh/doc-detail/27101.htm?spm=a3c0i.o27102zh.b99.2.51325bccUgbVTN