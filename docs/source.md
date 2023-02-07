---
title: 源代码
---

在源代码编辑的源码，保存后会立即生效，css修改了无需保存就会生效。如果你修改了js代码，需要保存后重新运行修改的代码块才可以生效，例如点击了按钮执行的方法等。如果你使用了sourcemap映射了源码，那将不会生效。

源代码视图的修改会在页面重新加载后失效，即页面刷新之后修改将不复存在。

打开文件快捷键

快捷键Control+P (Windows / Linux)，Command+P (Mac)

![image.png|500](https://s1.vika.cn/space/2023/01/29/b62151f97858447c98ca576950443c87)


调试快捷键

- 跳过下一个函数调用：F10
- 进入下一个函数调用(跳到函数的内部)：F11
- 跳出当前函数：Shift+F11
- 修改源码后保存：Command+S
- 跳转到代码某一行：Ctrl+G
- 查看函数定义：Command+Shift+O
- 删除一个单词：Option+Delete


#### 1) 代码片段

可以在源代码添加代码片段并且运行，代码片段是保存在浏览器中的，可以在任何页面运行。如果你经常在控制台里面执行一些代码，不妨将这些代码放到代码片段里面保存。

![image.png|500](https://s1.vika.cn/space/2023/01/30/3dc9c83b18f74926aeab6e5f96d13b37)

点击2的位置会运行代码，可以写一些工具代码在里面，方便调用，例如丢一个lodash代码进去，或者动态的append一个js文件到head里面。

```js
let script = document.createElement('script');
script.src = 'https://code.jquery.com/jquery-3.2.1.min.js';
script.crossOrigin = 'anonymous';
script.integrity = 'sha256-hwg4gsxgFZhOsEEamdOYGBf13FyQuiTwlAQgxVSNgt4=';
document.head.appendChild(script);
```

#### 2) 调试代码

我们可以通过多种方式暂停代码的执行，也就是我们常说的打断点。

A) 点击源代码左侧，就会出现断点，等到代码执行到这里的时候就会暂停，也可以右键点击添加高级断点

![image.png|240](https://s1.vika.cn/space/2023/01/30/617d61beeaea4f5eb981d7927ce8fecb)

B) 在代码中添加debugger；

C) 在DOM中使用断点，监听dom的变化；

![image.png|240](https://s1.vika.cn/space/2023/01/30/142f3095daf842369875cdca4a102be3)

D) XHR 断点，当发起的请求中包含某些字符串时暂停代码；

E) 使用其他事件监听器暂停代码；

如果你是点击了按钮触发了操作，并且导致了错误，我们可以从点击事件去开始排查，打上断点之后，我们触发了事件，就会走相关的代码，我们在源代码视图就能调试了。

![image.png|500](https://s1.vika.cn/space/2023/01/30/f7099588af804f988d9301dfdd11f695)

监控代码中的作用域和变量监视，在右侧的窗口就能看到，详细如下图所示。

![image.png|500](https://s1.vika.cn/space/2023/01/30/e419886b95ae43d4a04506a6536e398a)

F) 遇到异常的时候暂停，可以使用 throw new Error("xxx") 测试；

G) 调试方法，debug(fnName) 当执行fnName的时候，浏览器会暂停，要确保fnName是存在的并且在当前作用域下；

#### 3) 使用工作空间编辑和保存代码

相当于直接在浏览器里面进行开发，一边开发一边预览，修改的内容也会同步到本地的文件中。

![image.png|500](https://s1.vika.cn/space/2023/01/30/79dad5d16f5841f5971171b405c817d2)

注意：css修改之后会直接反应在页面上，html和js修改后不会反应到页面上；

#### 4) 调试技巧

当代码暂停执行的时候

- 可以看到此刻的变量的值，以及继承的多个作用域的值
- 可以设置一个监控的值，随着代码执行查看结果
- 可以鼠标放到方法上查看方法的属性
- 可以查看方法调用栈，右键点击调用栈的方法，可以重新执行
- 可以在作用域面板双击变量值修改作用域里面的值
- 修改方法之后保存，会默认重新执行当前方法

下面重新执行方法，官方提供的例子

```js
function foo(value) {
    console.log(value);
    bar(value);
}
 
function bar(value) {
    value++;
    console.log(value);
    debugger;
}

foo(0);
```

当我们引入了一些三方库，调试方法的时候不想进入到方法内部时，我们可以忽略这些文件，忽略后该文件中的断点将不再进入。更多操作[请查看](https://developer.chrome.com/docs/devtools/javascript/reference/#ignore-list)。

![image.png|400](https://s1.vika.cn/space/2023/01/31/dc84c5bb4fa34bb6ab21156aef18d878)

