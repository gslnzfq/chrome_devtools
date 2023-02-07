---
title: 网络
---



- [x] 模拟慢网络情况
- [x] 设置禁用缓存加载
- [x] 展示加载过程中的屏幕快照
- [x] 查看网络加载每个阶段的时间
- [x] 通过不同类型展示请求，例如XHR、img、css、fonts等
- [x] 点击无线网的icon可以设置userAgent等
- [x] 拦截某一个请求不让发出
- [x] 鼠标放到请求上可以查看是从那个js文件发出来的
- [x] 保留请求日志即使页面刷新跳转
- [x] 重新发送XHR，快捷键R
- [x] 清理浏览器缓存，清理浏览器cookies
- [x] 查看websocket消息
- [x] 下载响应的数据，拷贝请求地址和curl
- [x] 查看文件Ctrl+P

**时间分阶段的展示** #前端新知识点 [官方文档](https://developer.chrome.com/docs/devtools/network/reference/)

- Queueing：有下面的请求浏览器会排队
	- 有更高优先级的请求
	- 这个源已经打开了6个TCP连接，限制同源最多6个请求。仅适用于HTTP/1.0和HTTP/1.1协议。
	- 浏览器正在磁盘高速缓存中短暂分配空间
- Stalled：请求可能因Queueing中任何原因而停止，请求在队列中，没有开始
- DNS Lookup：浏览器正在解析请求的IP地址
- Initial connection：浏览器正在建立连接，包括TCP握手/重试和协商SSL
- Proxy negotiation：浏览器正在与代理服务器协商请求
- Request sent：请求开始发送
- ServiceWorker Preparation：浏览器正在启动service worker
- Request to ServiceWorker：请求被发送到service worker
- Waiting (TTFB)：浏览器正在等待响应的第一个字节。TTFB代表时间到第一个字节。这个时间包括1个往返的延迟和服务器准备响应的时间
- Content Download：浏览器直接从网络或service worker接收响应。这个值是读取响应体所花费的总时间。大于预期值可能表明网络速度较慢，或者浏览器正在忙着执行其他工作，从而延迟了读取响应
- Receiving Push：浏览器通过HTTP/2 Server Push接收这个响应的数据
- Reading Push：浏览器正在读取先前接收到的本地数据

#前端新知识点 HTTP2的服务器推送实践

更多特性[查看这里](https://developer.chrome.com/docs/devtools/network/reference/)。

快捷键


- 重发当前的ajax请求：R
- 隐藏当前请求的详情面板：Escape