## CSS行为技巧

行为技巧是什么呢?行为技巧我们认为是为了不同的浏览器做出的CSS上的适应，他与我们内容无关，本质在于适配各种浏览器。

#### :open_mouth:让不支持css3的浏览器支持css3

```javascript
<!--[if lt IE 9]>
    <script src="https://cdn.bootcss.com/respond.js/1.4.2/respond.js"></script>
<![endif]—>
```



#### :innocent:使用overflow-scrolling支持弹性滚动
iOS页面非body元素的滚动操作会**非常卡**(Android不会出现此情况)，通过`overflow-scrolling:touch`调用Safari原生滚动来支持弹性滚动，增加页面滚动的流畅度

```css
body {
    -webkit-overflow-scrolling: touch;
    overflow-scrolling: touch;
}
.elem {
    overflow: auto;
}
```

#### :cupid:使用transform启动GPU硬件加速
有时执行动画可能会导致页面卡顿，可在特定元素中使用硬件加速来避免这个问题

```css
.elem {
    transform: translate3d(0, 0, 0); /* translateZ(0)亦可 */
}
```

#### :mask:使用attr()抓取data-*
在标签上自定义属性`data-*`，通过`attr()`获取其内容赋值到`content`上


```css
<a class="tooltips" href="https://www.baidu.com" data-msg="Hello World">提示框</a>

&::after {
	content: attr(data-msg);
}
```

#### :smiling_imp:使用pointer-events禁用事件触发
通过`pointer-events:none`禁用事件触发(默认事件、冒泡事件、鼠标事件、键盘事件等)，相当于`<button>`的`disabled`

