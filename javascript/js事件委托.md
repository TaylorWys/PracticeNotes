# JavaScript的事件委托（面试频率也不低）
>
## 概念铺垫
>
**事件冒泡**和**事件捕获**
>
    事件传递定义了元素事件触发的顺序。如果你将 <p> 元素插入到 <div> 元素中，用户点击 <p> 元素, 哪个元素的 "click" 事件先被触发呢？
>
**事件冒泡**
>
    在 冒泡 中，内部元素的事件会先被触发，然后再触发外部元素，即： <p> 元素的点击事件先触发，然后会触发 <div> 元素的点击事件。
>
**事件捕获**
>
    在 捕获 中，外部元素的事件会先被触发，然后才会触发内部元素的事件，即： <div> 元素的点击事件先触发 ，然后再触发 <p> 元素的点击事件。
>
## 什么是事件委托?
>
事件委托——给父元素绑定事件，用来监听子元素的冒泡事件，并找到是哪个子元素的事件。
>
## 事件委托的优点
>
事件委托技术可以避免对每个字元素添加事件监听器，减少操作DOM节点的次数，从而减少浏览器的重绘和重排，提高代码的性能。  
使用事件委托，只有父元素与DOM存在交互，其他的操作都是在JS虚拟内存中完成的，这样就大大提高了性能。

## 举例
>  
```html
<ul id="parent-list">
	<li id="post-1">Item 1</li>
	<li id="post-2">Item 2</li>
	<li id="post-3">Item 3</li>
	<li id="post-4">Item 4</li>
	<li id="post-5">Item 5</li>
	<li id="post-6">Item 6</li>
</ul>
```
捕获真正被点击的li元素并输出，实现方法：
>
```javascript
// 找到父元素，添加监听器...
document.getElementById("parent-list").addEventListener("click",function(e) {
	// e.target是被点击的元素!
	// 如果被点击的是li元素
	if(e.target && e.target.nodeName == "LI") {
		// 找到目标，输出ID!
		console.log("List item ",e.target.id.replace("post-")," was clicked!");
	}
});
```
>