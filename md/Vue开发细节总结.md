# Vue开发细节总结

可以参考：[WebPack总结](quiver:///notes/7036AFF4-1B04-4F35-ACFA-FD67B9894130)

Vue创建项目
=======

main.js，入口文件
------------

```js
import Vue from 'vue'

import App from './App.vue'
import router from './router'
import './registerServiceWorker'

Vue.config.productionTip = false;

new Vue({
    router,
    render: h => h(App)
}).$mount('#app');
```

路由
--

```js
import Vue from 'vue'
import Router from 'vue-router'

import Home from './views/Home.vue'

Vue.use(Router)

export default new Router({
  routes: [
    {
      path: '/',
      name: 'home',
      component: Home
    },
    {
      path: '/about',
      name: 'about',
      // route level code-splitting
      // this generates a separate chunk (about.[hash].js) for this route which is lazy-loaded when the route is visited.
      component: () => import(/* webpackChunkName: "about" */ './views/About.vue')//延迟加载
    }
  ]
})
```

export default中的name作用
======================

* 类型：`string`
* 限制：只有作为组件选项时起作用。
* 详细：

  允许组件模板递归地调用自身。注意，组件在全局用 `Vue.component()` 注册时，全局 ID 自动作为组件的 name。

  指定 `name` 选项的另一个好处是便于调试。有名字的组件有更友好的警告信息。另外，当在有 [vue-devtools](https://github.com/vuejs/vue-devtools)，未命名组件将显示成 `<AnonymousComponent>`，这很没有语义。通过提供 `name` 选项，可以获得更有语义信息的组件树。

路由中的懒加载
=======

``` js
import Vue from 'vue'
import Router from 'vue-router'
import Home from './views/Home.vue'//直接引入加载

Vue.use(Router)

export default new Router({
  routes: [
    {
      path: '/',
      name: 'home',
      component: Home
    },
    {
      path: '/about',
      name: 'about',
      // route level code-splitting
      // this generates a separate chunk (about.[hash].js) for this route which is lazy-loaded when the route is visited.
      component: () => import(/* webpackChunkName: "about" */ './views/About.vue')//延迟加载
    }
  ]
})
```

组件间传值
=====

可以使用`​$emit(‘事件名称’[,参数1,参数2])`的方式注册方法，然后传入参数，然后在组件被调用处绑定该方法从形参中获取数据即可。

Vue 生成的Map文件
============

**Vue打包后出现一些map文件的解决办法：**

问题： 可能很多人在做vue项目打包，打包之后js中，会自动生成一些map文件，那我们怎么把它去掉不要呢？

 1、运行 cnpm run build 开始打包

 2、会在项目目录下自动创建dist目录，打包好的文件都在其中

**解决办法：去src/config/index.js中改一个参数：**

productionSourceMap:false

 把这个改为false。不然在最终打包的文件中会出现一些map文件，map文件的作用在于：项目打包后，代码都是经过压缩加密的，如果运行时报错，输出的错误信息无法准确得知是哪里的代码报错。

 有了map就可以像未加密的代码一样，准确的输出是哪一行哪一列有错。

Vue项目引入jQuery
=============

[Vue项目引入jQuery](quiver:///notes/76901C59-BC53-47BA-9017-37B584754E2A)

Vue项目参考结构
=========

![](https://ws3.sinaimg.cn/large/006tNc79ly1fyuqhai2ilj30te11q7a5.jpg)