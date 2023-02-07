---
title: 网络
---

## 基本功能

网络面板示意图

![image.png](https://s1.vika.cn/space/2023/02/07/c09063e661d94b3299a4dc6fe2d4ca4f)

① 保留日志，即使刷新页面或者页面跳转网路日志也不会消失，平常查看302这种请求比较有用。  
② 停用缓存，开启后服务器设置的请求头将不起作用，缓存相关的请求头可查看[HTTP缓存文章](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Caching)。  
③ 网络状况设置面板开关，点击后可以弹出5和6的面板。  
④ 根据请求分类查看请求，常用的有Fetch/XHR面板，和服务器联调接口的时候用的比较多。  
⑤ 修改网络状态，平常我们所说的模拟网速开关，默认是停用的。  
⑥ 自定义UA，可以通过修改这个值来模拟在app中运行。  
⑦ 页面加载情况，请求个数、请求大小、加载时间等。

## 请求详情

点击某一个请求可以查看解析后的请求和响应报文，大概如下所示

![image.png](https://s1.vika.cn/space/2023/02/07/144fede1b40c4d0e997a486ef9b7e3b6)

**标头** 包括[请求和响应头](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers)信息，报文头部是不区分大小写的，对于我们比较常用的信息有：

- 请求方法
- 请求地址
- 远程地址，一般是服务器的地址，如果我们配置了host，可以看请求的真实地址是那个
- [响应标头](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers "点击查看所有标头")
	- access-control-allow-origin: 允许访问的域，跨域时服务器端设置
	- content-length: 响应数据的大小
	- content-type: 响应的类型
	- cache-control: 设置缓存
	- expires: 资源过期时间，最小精确到秒
	- last-modified: 最后修改时间，最小精确到秒
	- etag: 文件内容hash
	- server: 服务器类型，例如nginx、tomcat、apache等
	- content-encoding: 内容的编码方式，常见的有gzip,br等，告诉浏览器怎么解析
	- set-cookie: 给浏览器设置cookie，一般是保存登录信息
	- location: 重定向之后的地址
- [请求标头](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers "点击查看所有标头")
	- cache-control: 缓存配置说明，同响应标头
	- authorization: 传给服务器的授权信息，使用 [JWT](https://en.wikipedia.org/wiki/JSON_Web_Token) 授权的时候常用
	- [cookie](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Cookies): 传输给服务器的cookie，这个值是自动携带的
	- host: 当前的域，服务器处理跨域就是根据这个判断的
	- [referer](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Referer):  当前请求页面的来源页面的地址，后台做数据统计或者防盗链都使用这个头
	- user-agent: 浏览器代理，每个浏览器是唯一的，可以通过这个值在服务器上判断浏览器支持的功能做资源下发等。
**预览**：可以预览响应的数据，例如JSON，xml，image等
**响应**：服务器返回的原始数据
**启动器**：请求的调用堆栈
**时间**：每个阶段加载的时间，鼠标放在瀑布图上展示的是一样的

## 查看时间

鼠标放在请求后面的瀑布图上可以查看请求的时间信息。

![image.png](https://s1.vika.cn/space/2023/02/07/6184e1eb496544328c95b7ab18380fd1)

### 基本指标

- Queueing: 对应上图的是排队时间，如果有下面的情况，请求将会排队
	-  有更高优先级的请求，优先级在网络面板查看
	- 当前源已经超过了浏览器的请求数量限制，chrome是6，超过6个TCP连接就会排队。HTTP2能解决这个问题。
	- 浏览器正在写入缓存数据
- Stalled: 对应上图的暂停时间，请求会因为排队的任意原因而暂停。
- Request sent: 请求开始发送，这个时间会很短。
- [Waiting for server response](https://web.dev/i18n/zh/ttfb/): 从发送请求到服务器响应第一个字节的时间，这个时间取决于服务器处理业务的时间，如果这个时间过长就要在服务器端进行优化了。
- Content Download: 浏览器直接从网络或service worker接收响应。这个值是读取响应体所花费的总时间。大于预期值可能表明网络速度较慢，或者浏览器正在忙着执行其他工作，从而延迟了读取响应。

### 其他指标

下面的指标我们平时都不太关注的

- DNS Lookup：浏览器正在解析请求的IP地址
- Initial connection：浏览器正在建立连接，包括TCP握手/重试和协商SSL
- Proxy negotiation：浏览器正在与代理服务器协商请求
- ServiceWorker Preparation：浏览器正在启动service worker
- Request to ServiceWorker：请求被发送到service worker
- Receiving Push：浏览器通过HTTP/2 Server Push接收这个响应的数据
- Reading Push：浏览器正在读取先前接收到的本地数据


## 屏蔽请求

如果我们需要屏蔽某一个请求，可以右键点击请求来屏蔽当前请求或者屏蔽当前域名的请求，有啥用呢? 屏蔽广告等，广告屏蔽插件基本就是这样实现的。

![image.png](https://s1.vika.cn/space/2023/02/07/ced7f1cd6f3e4e379c7f32447d27f63e)

再次请求时，已经展示已屏蔽了，想要恢复的话，右键点击取消屏蔽即可

![image.png](https://s1.vika.cn/space/2023/02/07/4eeb5d2a276e4f83905c4c8c9b685b71)

## 复制请求信息

请求的信息我们可以将其复制在剪切板，如图所示

![image.png](https://s1.vika.cn/space/2023/02/07/372bfe43793a448daec0c814f4dfa85e)

比较常用的就下面选项

- 复制链接地址：就是请求地址
- 复制响应数据：可以复制后台返回的json等
- 以curl格式复制：复制curl直接在terminal执行，或者请求出错了，直接发给服务器开发让定位问题

## 查看WS的消息

再调试im的使用有作用，例如直播间消息等。

![image.png](https://s1.vika.cn/space/2023/02/07/7c3aab3386254cb0ab0784c638eb43b6)


## 快捷键

- 重发当前的ajax请求：R
- 隐藏当前请求的详情面板：Escape
