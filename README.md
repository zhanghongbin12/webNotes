# webNotes
前端日常知识点笔记

> 子窗口获取父窗口的方法

```
$(window.parent.document).find("#iframe 的 id")
```

> 父窗口获取子窗口的方法

```
$(“#iframe 的 id"”).contents().find(“#id”)
```

> 在父窗口中调用子窗口的 js 方法

```
Iframe 的 name 比如叫 page;
page.Window.function();
```

> scrollHeight 兼容性

```
ie 适用 document.body.scrollHeight+10
非 ie 适用 document.documentElement.scrollHeight
```

> 判断是否是 ie 支持 ie6-ie11

```
if (!!window.ActiveXObject || "ActiveXObject" in window){
    true
}else{
    False
}
```

> 数组的添加和删除方法

- push()是向数组末端添加项的方法 返回数组的长度
- unshift()是向数组前端添加项的方法 返回数组的长度
- pop()从数组末端移除项 返回数组的长度
- shift()从数组前端移除项 返回数组的长度

> Jquery Dom 添加方式

- append() 方法在被选元素的结尾插入内容。
- prepend() 方法在被选元素的开头插入内容。
- after() 方法在被选元素之后插入内容。
- before() 方法在被选元素之前插入内容。

> Math 方法

- Math.ceil(x) 对数进行上舍入。
- Math.floor(x) 对数进行下舍入。
- Math.round(x) 把数四舍五入为最接近的整数。

> html 清除缓存

```
<meta http-equiv="Cache-Control" content="max-age=7200" />
<meta http-equiv="Expires" content="Mon, 20 Jul 2013 23:00:00 GMT" />
```

> 当前 div 到页面顶部的距离

```
$('div').offset().top
```

> 网页工作区域的高度和宽度

```
(javascript) document.documentElement.clientHeight// IE
(jqurey) $(window).height()
```

> 元素距离文档顶端和左边的偏移值

```
(javascript) DOM 元素对象.offsetTop //IE firefox
(javascript) DOM 元素对象.offsetLeft //IE firefox
(jqurey) jq 对象.offset().top
(jqurey) jq 对象.offset().left
```

> 阻止事件冒泡，阻止默认事件

1. event.stopPropagation()方法

   - 这是阻止事件的冒泡方法，不让事件向 documen 上蔓延，但是默认事件任然会
     执行，当你掉用这个方法的时候，如果点击一个连接，这个连接仍然会被打开

2. event.preventDefault()方法

   - 这是阻止默认事件的方法，调用此方法是，连接不会被打开，但是会发生冒泡，冒泡会传递到上一层的父元素

3. return false

   - 这个方法比较暴力，他会同事阻止事件冒泡也会阻止默认事件；写上此代码，连
     接不会被打开，事件也不会传递到上一层的父元素；可以理解为 return false
     就等于同时调用了 event.stopPropagation()和 event.preventDefault()

> Javascirpt 中添加多个样式可以这样

```
document.getElementById('id').style.cssText= 'color:red;font-szie:12px;'
```

> 添加和删除 class 的方法

```
document.getElementByClassName(“class”).classlist.add(“class”);
document.getElementById(“id”).classlist.remove(“class”);
```

> js 判断是否手机端登录

```
function check() {
    var userAgentInfo=navigator.userAgent;
    var Agents =new Array("Android","iPhone","SymbianOS","WindowsPhone","iPad","iPod");
var flag=true;
for(var v=0;v<Agents.length;v++) {
  if(userAgentInfo.indexOf(Agents[v])>0) {
    flag=false;
    break;
   }
 }
return flag;
}
Check()返回 true 则为 pc 端 false 则为手机端
```

> CSS 改变滚动条的样式

```
::-webkit-scrollbar {
 width: 16px; /_滚动条宽度_/
height: 16px; /_滚动条高度_/
}
::-webkit-scrollbar-track {
 -webkit-box-shadow: inset 0 0 6px rgba(0,0,0,0.3);
border-radius: 10px; /_滚动条的背景区域的圆角_/
background-color: red;/_滚动条的背景颜色_/
}

::-webkit-scrollbar-thumb {
border-radius: 10px; /_滚动条的圆角_/
-webkit-box-shadow: inset 0 0 6px rgba(0,0,0,.3);
background-color: green; /_滚动条的背景颜色_/
}
```

> Vue 生命周期以及钩子函数

- beforeCreate 创建前
- created 创建完成
- beforeMount 挂载前
- mounted 挂载结束
- beforeUpdate 更新前状态
- updated 更新完成状态
- beforeDestroy 销毁前状态
- destroyed 销毁状态

> github 第一次提交代码至远程仓库步骤

1. git clone 克隆项目

2. git add . 添加修改后的所有内容

3. git commit –m “test1” 提交到服务

4. git push -u origin master 推送到仓库

5. git pull master 更新本地代码

6. git branch newBranch 创建新的分支

7. git checkout newBranch 切换新分支

> JS/CSS/IMG 加载顺序关系之 DOMContentLoaded 事件

1. CSS 样式表影响了图片的加载速度，然而 JS 不会影响，如果想让图片尽快加载，就不要给图片使用样式，比如宽高采用标签属性即可。
2. JS 的加载执行速度影响了 DOMContentLoaded 事件的触发时间，如果想要尽快触发 DOMContentLoaded 事件，就将次要的 JS 采用动态加载的方式加载吧。

> Canvas 和 Svg 的对比

- canvas 是 html5 提供的新元素 通常通过 JS 来绘图，而 svg 存在的历史要比 canvas 久远 是 XML 用来描述二维图形的语言
  canvas 可以看做是一个画布，可以在 canvas 中引入 jpg 或 png 这类格式的图片
  而 svg，所绘制的图形为矢量图，所以 svg 中不能引入普通的图片，可以被无限放大而不会失真，很适合被用来做地图
- 再来介绍一个 svg 的 js 库：TWO.JS。其中包含 two.js 和 three.js 前者用于绘制二维图形，后者用于绘制三维图形

---

### 更多内容请看 text 文件内容
