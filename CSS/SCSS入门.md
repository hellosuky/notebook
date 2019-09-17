## SCSS入门基础练级

#### :sleeping:设置变量

---

SCSS与CSS很不一样的一点就是SCSS能够设置变量，这样我们能够保证换个颜色能够进行全局变量的更替，不会在每次更换的时候，我们需要全局搜索语句进行全局替换，这样大大增加了我们前端的工作难度。

```scss
$blue : '#1875e7'
    
 //使用
 div{
 	color:$blue;       
 }   
```



###### 镶在字符串中

SCSS能够允许我们把变量镶嵌在字符串之中，但是这时候我们就需要写成`#{}`

```scss
$side : 'left'
    
//使用
div{
    border-#{$side}-radius: 5px;      
}
```



#### :flushed:计算

---

SCSS能够允许我们在样式中进行简单的计算，例如：

```scss
div{
    margin: (14px/2) *3 + 5px
}
```



#### :anger:嵌套

---

我们能够进行选择器的嵌套。这样做能够在我们开发时候能够明显表现出各个元素之间得**层级关系**。

```scss
div{
    h2{
        color:red;
    }
}
```



#### :dizzy_face:继承

---

SCSS还能够进行继承，这样能够允许我们对一些能够复用得属性提取出来。

```scss
.class1{
    border: 1px solid #ddd;
}

//继承
。class2{
    @extend .class1;
    font-size:20px;
}
```



#### :rage:复用得代码块

---

除了我们通过继承进行复用之外，我们还能定义我们代码块`mixin`来进行复用模块,但是和继承不一样得是，这是可以进行**参数传递**得，这样我们得复用就比上面得更高级了一点，我们可以模式得提取。

```scss
@mixin left($value:10px){
    float:left;
    margin-left:$value;
}

//使用
div{
    @include left(20px)
}
```



#### :fire:语句

---

SCSS还支持条件语句与循环语句，这样能够让我们在一些场景能够进行选择性得渲染。

```scss
p{
    @if 1 + 1 == 2 { border: 1px solid }
    @else { border: 1px dotted }
}

@for $i from 1 to 10{
    .border-#{$i} {
       border: #{$i}px solid blue;
    }
}
```





[参考链接](http://www.ruanyifeng.com/blog/2012/06/sass.html)