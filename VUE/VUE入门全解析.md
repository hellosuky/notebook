## 目录

+ [安装](#1)
+ [Vue的生命周期](#2)
+ [Vue的基本技巧](#3)
+ [VUE的基本结构](#5)
+ [VUE数据传递](#4)
+ [开发过程技巧](#5)



+ [VUE的双向绑定](#9)
+ [给一些文件路径设置别名](#10)
+ [VUE递归组件](#11)
+ [VUE之插槽](#12)
+ [vue项目支持手机端访问](#13)
+ [vue的异步加载](#14)
+ [添加Props属性](#15)





### :weary:<span id="1">安装</span>

##### 全局安装vue包
```javascript
    npm install -g @vue/cli-init 
```

##### 安装具体项目

```javascript
    vue init webpack <项目名称>
```

安装的过程中，他会安排一些问题提问你，你只要根据自己的实际需求然后来进行安装即可，那我们一般来说会安装的是`VUE-Router`和`Estint`这两个组件。



###### Vue.js 2.0 独立构建和运行时构建的区别

Vue.js 2.0，为了支持**服务端渲染**（server-side rendering），编译器不能依赖于 DOM，所以必须将编译器和运行时分开。这就形成了独立构建（编译器 + 运行时）和运行时构建（仅运行时）。显而易见，运行时构建要小于独立构建。

**注意：VUE子文件的命名应该使用头一个字母为大写**

### :sparkles:<span id="2">Vue的生命周期</span>

![lifecycle](E:\notebook\images\lifecycle.png)

上面是一个属于VUE整个生命周期的图片，那我们值得注意的主要是这几个：

+ **created**: 这是在组件刚初始化完成时的一个钩子，我们一般用来请求我们组件一开始显示时所需要的网络数据。

+ **mounted**: 组件结束渲染的钩子，处理需要组件全部加载后的时候才能加载的东西

  

  在我们的开发中，最最最常用就是这两个了。

  ###### 使用

  ```javascript
  export default {
    name:'CityList',
    //加载的内容
    created(){
      //get my data
    },
    mounted(){
       //do your job
    }
  }
  ```

  

### :wink:<span id="3">VUE基本技巧</span>

###### 获取vue的节点

```javascript
<div class="list" ref="wrapper"></div>
  
this.dom = this.$refs.wrapper
```



###### 绑定事件

```javascript
<li class="item"
v-on:click="handleClick"
></li>

export default {
	...
  methods:{
      //定义方法
    handleClick(e){
      // do sth
    }
  }
}
```



###### 添加Props属性

```javascript
export default {
	...
  props: {
    //array
      roles: {
          type: Array,
          default: function () {
            return [1]
          }
    },
     //string
    abc: String,
    ddd: {
        type:String,
        default: 'dd'
    },
    // obj
    roles: {
      type: Object,
      default: function () {
        return { roleName: 'admin' }
      }
    }
  }
}
```



###### 	VUE的异步加载

```javascript
import Vue from 'vue'
import Router from 'vue-router'
 
Vue.use(Router)

export default new Router({
  routes: [
    {
      path: '/',
      name: 'Home',
      component: () => import('@/pages/home/Home.vue')
    }
  ]
})
```



### :anguished:<span id="4">VUE数据传递</span>



#### ###  <span id="5">开发过程技巧</span>

