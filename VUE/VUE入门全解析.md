## 目录

+ [安装](#1)
+ [Vue的生命周期](#2)
+ [Vue的基本技巧](#3)
+ [VUE的基本结构](#5)
+ [VUE数据传递](#4)

+ [VUE事件](#5)

+ [开发过程技巧](#6)

+ [VUE的高级功能](#7)





### :weary:<span id="1">安装</span>

---

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

---



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

---



###### 获取vue的节点

```javascript
<div class="list" ref="wrapper"></div>
  
this.dom = this.$refs.wrapper
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



###### computed属性

VUE里面计算属性的用途主要是用来我们处理开发过程中的复杂逻辑的。

```vue
export default {
	computed: {
		message :function(){
			//计算
			return newMessage
		}
	}
}
```



###### watch属性

这是VUE的侦听属性，感觉其实是很像上面我们说的计算属性，但有时我们还是需要一个侦听属性的，它可以用来进行数据变化进行异步操作。

```vue
export default {
	watch: {
		message :function(){
			// do sth
		}
	}
}
```



###### VUE的插槽

日常开发，将需要插槽的地方预留，如这里我们设置名字`MySlot.vue`

```vue
<template lang="html">
  <div>
    <slot></slot>
  </div>
</template>
```

现在要将内容填充在插槽中，只要像组件一样调用`MySlot.vue`组件，并将我们要插入的内容包裹在里面即可。

```vue
<my-slot>
 <div>ddd</div>
</my-slot>
```





### :anguished:<span id="4">VUE数据传递</span>

###### 将数据传递给子组件

```vue
//父组件
<template>
    <div>
      <home-swiper :swiperList="swiperList"></home-swiper>
    </div>
</template>

//子组件
export default {
  name:'HomeRecommand',
  //传递的值进行检验
  props:{
    swiperList:Array
  }
}

//子组件使用
<li v-for="item in swiperList" :key="item.id" class="recommand-item">
   //do sth
</li>
```



###### 双向绑定

```vue
<input class="search-input" v-model="keyword" placeholder="输入你想要搜索的城市"/>
```



#### :wink:<span id="5">​VUE事件</span>

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



###### VUE子组件发送自定义事件

```vue
//某组件发送
this.$emit('change','abc')

//组件接收
<div @change="handleChange">xxx</div>
methods:{
    handleChange(){
        //do sth
    }
}
```



#### :fire:<span id="6">开发过程技巧</span>

---

###### 给一些文件路径设置别名

打开`build/webpack.base.conf.js`
设置其中的`alias`,加入别名及其路径

```javascript
output: {
    path: config.build.assetsRoot,
    filename: '[name].js',
    publicPath: process.env.NODE_ENV === 'production'
      ? config.build.assetsPublicPath
      : config.dev.assetsPublicPath
  },
  resolve: {
    extensions: ['.js', '.vue', '.json'],
    alias: {
      'vue$': 'vue/dist/vue.esm.js',
      '@': resolve('src'),
      'styles':resolve('src/assets/styles')
    }
  },
```



###### vue项目支持手机端访问

在`package.json`中插入

```javascript
"scripts": {
    "dev": "webpack-dev-server --host 0.0.0.0 --inline --progress --config build/webpack.dev.conf.js",
    "start": "npm run dev",
    "lint": "eslint --ext .js,.vue src",
    "build": "node build/build.js"
  },
```
`//--host 0.0.0.0`是支持我们能够手机内网访问的关键

+ 用cmd 使用`ipconfig`查找本机ip地址
+ 手机将localhost换成本机ip地址即可访问



###### vue支持某些低配手机的promise等高级函数

```javascript
    npm install babel-polyfill
    
    //在main.js中插入
    import 'babel-polyfill'
```



###### VUE的异步加载

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



#### :girl:<span id="7">VUE的高级功能</span>

---

###### VUE的递归组件

文件名为`DetailList.vue`

```vue
<template lang="html">
  <div class="list">
    <div class="list-item" v-for="(item,index) in list" :key="index">
      <div>{{item.title}}</div>
      <div v-if="item.children" class="list-children">
        <detail-list :list="item.children"></detail-list>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name:'DetailList',
  props:{
    list:Array
  }
}
</script>
```

