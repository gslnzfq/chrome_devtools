---
title: 审查元素
---

## 1. 强制修改状态

方式1，直接右键点击节点操作，在我们开发hover等样式的时候有作用，因为鼠标hover后鼠标移走了就hover消失了。

![image.png|500](https://s1.vika.cn/space/2023/01/29/5e4dfaf4a2ee46b583dabc34be75b815)

方式2，在右侧的面板修改状态。

![image.png|500](https://s1.vika.cn/space/2023/01/29/1acb31178c2c4c158e7eb8ba58a88ef0)

## 2. 删除或隐藏元素

删除元素，选中按Delete；隐藏元素，选中按H。**仅仅在浏览器中删除，和源代码没有关系**。

## 3. 修改节点名称、内容或属性

双击节点或者双击内容即可修改，属性也可以双击，导航到下一个属性按Tab，上一个属性Shift+Tab。

样式编辑面板快捷键

- 值+0.1/-0.1，Option+Up/Down
- 值+1/-1，Up/Down
- 值+10/-10，Shift+Up/Down
- 值+100/-100，Command+Up/Down

## 4. 在控制台访问节点

使用$0访问当前选中的节点，可以右键点击节点存储为全局变量，会生成一个temp开头的变量，即使失去焦点也可以一直访问。

右键点击节点可以复制js路径，例如 document.querySelector("#type")，自动化的时候可能会用到；

![image.png|500](https://s1.vika.cn/space/2023/02/07/9ba666e373704872b4a71228b7f3410b)


## 5. HTML vs DOM

HTML represents initial page content, and the DOM represents current page content. When JavaScript adds, removes, or edits nodes, the DOM becomes different than the HTML.

HTML相当于初始的页面内容，而DOM相当于当前的页面内容，Javascript可以修改DOM，但是不能修改HTML。

## 6. 查看DOM节点的属性

选中dom节点，打开属性面板就可看到dom节点的属性，如下图所示

![image.png|600](https://s1.vika.cn/space/2023/01/30/284b7643dee44a57bad531f97341f8eb)

## 7. 使用标志查看布局

右键点击节点"标志设置"，可以展示或者取消标志；

![image.png|600](https://s1.vika.cn/space/2023/01/30/14463e71f478448bbc99b2c70ad87a49)

打开的标志会在dom树中展示，点击对应的标志可以查看布局信息，更多使用[请查看](https://developer.chrome.com/docs/devtools/elements/badges/)。

## 8. CSS查看和修改

通过样式面板可以给修改节点的样式、添加css类、添加伪类。

可以查看盒子模型(双击内部文本可以修改边距、边框、长宽等)，查看计算后的样式（查看样式覆盖、继承、样式的简写如margin等）等。

角度、阴影、动画类型都可以使用可视化调节，只需要点击对应的图标就可以了。

![image.png](https://s1.vika.cn/space/2023/01/30/7bba80b7794b4b058a219c43b54b0c99)

其他用法：

- [Inspect CSS grid layouts - Chrome Developers](https://developer.chrome.com/docs/devtools/css/grid/)
- [Inspect and debug CSS flexbox layouts - Chrome Developers](https://developer.chrome.com/docs/devtools/css/flexbox/)
- [Inspect and debug CSS container queries - Chrome Developers](https://developer.chrome.com/docs/devtools/css/container-queries/)

## 9. 调试打印的样式

打开渲染tab，模拟css类型中修改为打印，页面就会展示打印的视图。

打印的样式我们写在print的屏幕下，如下代码

```css
@media print {
	body {
		backdround: red;
	}
}
```

![image.png|300](https://s1.vika.cn/space/2023/01/30/263e172e18d34ac9b629e7f66b8d62d0)

这里除了模拟打印，还可以模拟深色模式和浅色模式的样式，以及更多的模拟选项，详细查看“渲染”配置。

