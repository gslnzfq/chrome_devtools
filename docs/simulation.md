---
title: 模拟设备
---

## 设备尺寸

移动模拟视图并不能代表真实的手机运行状态，有一些局限性，例如CPU架构、性能等，如果需要真实的体验，可以尝试远程调试，直接在手机上运行页面。

![image.png|500](https://s1.vika.cn/space/2023/01/29/a00a42e87f614021827da5c383343bd4)

上图描述了不同设备宽度的示意图，用户在响应模式下，可以拖动模拟器大小来来查看不同设备的效果。对应的尺寸如下：

![image.png|500](https://s1.vika.cn/space/2023/01/29/26b448d224de42a595af97da0eafe464)

通过媒体查询面板可以查看代码中定义的对应的样式是否生效，点击对应的区域，下面的模拟器宽度会跟着变化。右键点击浅色的区域可以查看代码中的定义；

<span style="color:#21A5F1;">蓝色</span>代表最大的宽度，<span style="color:#FD7A27;">橘色</span>代表最小宽度；

![image.png|500](https://s1.vika.cn/space/2023/01/29/7e307de078f34cbb9c3313c7d3bdaf0d)

也可以通过菜单修改DPR的值，内置的iPhone的DPR都是固定的，例如iPhone 12的DPR就是3；

## 自定义设备

通过添加自定义的device可以模拟某一些app，有些app中的H5是通过userAgent来判别的。

![image.png|240](https://s1.vika.cn/space/2023/01/29/589f5972b7d9465a9c5879e318e656a9)

## 网络和CPU限流

可以通过模拟不同级别的方式观察网页的展示性能，并不是很准确。如果只限制单个，需要在性能面板去操作。

![image.png|500](https://s1.vika.cn/space/2023/01/29/7f8796e361174522bc78aafabee5f033)

## 页面截图

支持长截图和当前视口的截图。

## 传感器

可以设置定位和设备的屏幕方向。

![image.png|500](https://s1.vika.cn/space/2023/01/29/cf81b5eb4cb24097a75b9645aa245ea1)

---
