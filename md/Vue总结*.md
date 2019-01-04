# Vue总结*

> 作者：GuoFu
>
> 日期：2018年12月26日
>
> 说明：本文并未对Vue相关知识点进行详尽说明，仅简明扼要的说明Vue的一些关键点，详细的文档说明参考[官方网站](https://cn.vuejs.org/v2/guide/)即可。官网对于Vue使用的介绍相当详细，有一些语句需要仔细研读，不理解透彻的话在后续开发中可能就会遇到坑。
>
> 联系方式：guofu_gh@163.com

[RESTful 总结](quiver:///notes/361A6CAD-F246-45AE-8700-B81EB88004B7)

[Eslint 配置及规则说明](quiver:///notes/5EB09156-A9DD-4A99-BE79-F34FA8A5A1A3)

前言
==

* Vue.js（读音 /vjuː/, 类似于 view） 是一套构建用户界面的渐进式框架。
* Vue 不支持 IE8 及以下版本，因为 Vue 使用了 IE8 无法模拟的 ECMAScript 5 特性
* 直接下载并用 `<script>` 标签引入，`Vue` 会被注册为一个全局变量。
  * 开发版本：包含完整的警告和调试模式
  * 生产版本：删除了警告，30.96KB min+gzip

 开发过程中建议使用开发版本，不建议使用生产版本，因为使用生产版本将不会对一些不规范的写法进行提示，容易产生安全隐患！

* Vue 的核心库**只关注视图层**，采用自底向上增量开发的设计。

```js
    <script src="https://cdn.jsdelivr.net/npm/vue@2.5.21/dist/vue.js"></script>
```

一、基础知识点
=======

```js
var app = new Vue(options);
```

其中options是一些Vue的操作对象，基本的属性有：

* **el**：受Vue控制的生效范围的根元素选择器，例如：“\#app”
* **data**：Model数据模型
* **method：**定义的方法
* **computed：**计算方法
* **watch**：监听属性
* ...

示例：

```js
var app = new Vue({
    el: "#app"
    , data: {
        message: "hello world！"
        , placeholder: "输入内容"
    }
    ,method:{
        method1:function(){
            // 具体逻辑实现
        }
        ,method2:function(name){
            // 具体逻辑实现
            return name;
        }
    }
    ,computed:{
        computed1:function(){
            // 具体逻辑实现
            return 返回值;
        }
        ,computed2:function(){
            // 具体逻辑实现
            return 返回值;
        }
    }
    ...........
    ...........
    ...........
});
```

1.1 基础演示
--------

```html
<!DOCTYPE html>
<html lang="en" xmlns:v-bind="http://www.w3.org/1999/xhtml">
<head>
    <meta charset="UTF-8">
    <title>Vue学习-第一节</title>

    <!--引入Vue-->
    <script src="../js/vue.js" type="application/javascript"></script>
</head>
<body>
<div id="app">
    {{ message }}

    <input v-bind:placeholder="placeholder" style="height: 10px">
</div>

<script>
    var app = new Vue({
        el: "#app"
        , data: {
            message: "hello world！"
            , placeholder: "输入内容"
        }
    });
</script>
</body>
</html>
```

1.2 基本指令
--------

### 

* **v-text**

 更新元素的 `textContent`。如果要更新部分的 `textContent` ，需要使用 `{{ Mustache }}` 插值。

### 

* **v-html**

输出原始HTML。

### 

* **v-show**

****

### 

* **v-bind**

** 绑定属性。**

 简写为“:”，例如：

```html
        <!-- 完整语法 -->
        <a v-bind:href="url">...</a>
        <!-- 缩写 -->
        <a :href="url">...</a>
```

可以将“url”定义成data数据项，动态更新data.url则a标签的url动态更新，更加灵活。

### 

* **v-on**

** 绑定事件。**

 简写为“@”，例如：

```html
        <!-- 完整语法 -->
        <a v-on:click="doSomething">...</a>
        <!-- 缩写 -->
        <a @click="doSomething">...</a>
```

### 

* **v-model**

** 数据双向绑定。**

### 

* v-if

### 

* v-for

1.3 生命周期
--------

![Vue 实例生命周期](https://ws3.sinaimg.cn/large/006tNc79ly1fyuqpel6nmj30u023zt9s.jpg)

1. **beforeCreate**（创建前），在数据观测和初始化事件还未开始
2. **created**（创建后），完成数据观测，属性和方法的运算，初始化事件， `$el` 属性还没有显示出来
3. **beforeMount**（载入前），在挂载开始之前被调用，相关的render函数首次被调用。实例已完成以下的配置：编译模板，把data里面的数据和模板生成html。注意此时还没有挂载html到页面上。
4. **mounted**（载入后），在el 被新创建的 `vm.$el` 替换，并挂载到实例上去之后调用。实例已完成以下的配置：用上面编译好的html内容替换el属性指向的DOM对象。完成模板中的html渲染到html页面中。此过程中进行ajax交互。
5. **beforeUpdate**（更新前），在数据更新之前调用，发生在虚拟DOM重新渲染和打补丁之前。可以在该钩子中进一步地更改状态，不会触发附加的重渲染过程。
6. **updated**（更新后），在由于数据更改导致的虚拟DOM重新渲染和打补丁之后调用。调用时，组件DOM已经更新，所以可以执行依赖于DOM的操作。然而在大多数情况下，应该避免在此期间更改状态，因为这可能会导致更新无限循环。该钩子在服务器端渲染期间不被调用。
7. **beforeDestroy**（销毁前），在实例销毁之前调用。实例仍然完全可用。
8. **destroyed**（销毁后），在实例销毁之后调用。调用后，所有的事件监听器会被移除，所有的子实例也会被销毁。该钩子在服务器端渲染期间不被调用。

Vue页面第一次加载时会触发下面这几个**beforeCreate、created、beforeMount、mounted**

1.4 方法
------

**关键字：method**

**语法：**

```js
method:{
    方法名称:function(参数...){
        // 具体逻辑实现
    }
}
```

1.5 [计算属性和侦听器](https://cn.vuejs.org/v2/guide/computed.html)
-----------------------------------------------------------

**关键字：computed**

**语法：**

```js
computed:{
    计算属性名称:function(参数...){
        // 具体逻辑实现
        return 返回值;
    }
}
```

```js
<div id="example">
  <p>Original message: "{{ message }}"</p>
  <p>Computed reversed message: "{{ reversedMessage }}"</p>
</div>


var vm = new Vue({
  el: '#example',
  data: {
    message: 'Hello'
  },
  computed: {
    // 计算属性的 getter
    reversedMessage: function () {
      // `this` 指向 vm 实例
      return this.message.split('').reverse().join('')
    }
  }
})
```

结果：

Original message: "Hello"

Computed reversed message: "olleH"

以上声明了一个计算属性 `reversedMessage`

可以像绑定普通属性一样在模板中绑定计算属性

1.6 计算属性VS方法
------------

我们可以将同一函数定义为一个方法而不是一个计算属性。两种方式的最终结果确实是完全相同的。然而，不同的是计算属性是基于它们的依赖进行缓存的。只在相关依赖发生改变时它们才会重新求值。这就意味着只要 `message` 还没有发生改变，多次访问 `reversedMessage` 计算属性会立即返回之前的计算结果，而不必再次执行函数。

[](https://cn.vuejs.org/v2/guide/computed.html?_sw-precache=c584351276a7ccd129ebb9f0fee5b87c#%E4%BE%A6%E5%90%AC%E5%99%A8 "侦听器")

1.7 [侦听器](https://cn.vuejs.org/v2/guide/computed.html#%E4%BE%A6%E5%90%AC%E5%99%A8)
----------------------------------------------------------------------------------

**关键字：watch**

1.8 [Class与Style绑定](https://cn.vuejs.org/v2/guide/class-and-style.html)
-----------------------------------------------------------------------

* class与内联样式都是标签的属性，因此可以使用v-bind指令进行绑定
* v-bind:class=“{样式:条件,……}”
* v-bind:class可以与多个class样式共存
* v-bind:class可以绑定到对象。[参考链接](https://cn.vuejs.org/v2/guide/class-and-style.html#%E5%AF%B9%E8%B1%A1%E8%AF%AD%E6%B3%95)

```js
<div v-bind:class="classObject"></div>
```

```js
data: {
  classObject: {
    active: true,
    'text-danger': false
  }
}
```

* 可以把一个数组传给 `v-bind:class`，以应用一个 class 列表。[链接](https://cn.vuejs.org/v2/guide/class-and-style.html#%E6%95%B0%E7%BB%84%E8%AF%AD%E6%B3%95)
* 内联样式的绑定。[链接](https://cn.vuejs.org/v2/guide/class-and-style.html#%E7%BB%91%E5%AE%9A%E5%86%85%E8%81%94%E6%A0%B7%E5%BC%8F)
  * CSS 属性名可以用驼峰式 (camelCase) 或短横线分隔 (kebab-case，记得用单引号括起来) 来命名

1.9 [条件渲染](https://cn.vuejs.org/v2/guide/conditional.html)
----------------------------------------------------------

v-if

**v-if与v-show的区别：**

 v-if控制DOM元素的销毁和重建，v-show仅仅是控制display样式的切换。因此`v-if` 有更高的切换开销，而 `v-show` 有更高的初始渲染开销。

 如果需要非常频繁地切换，则使用 `v-show` 较好；

 如果在运行时条件很少改变，则使用 `v-if` 较好。

1.10 [列表渲染](https://cn.vuejs.org/v2/guide/list.html)
----------------------------------------------------

v-for

* 注意绑定一个唯一值，v-bind:key=“”。[参考信息](https://cn.vuejs.org/v2/style-guide/#%E4%B8%BA-v-for-%E8%AE%BE%E7%BD%AE%E9%94%AE%E5%80%BC-%E5%BF%85%E8%A6%81)
* 不推荐同时使用 `v-if` 和 `v-for`。当 `v-if` 与 `v-for` 一起使用时，`v-for` 具有比 `v-if` 更高的优先级

1.11 [事件处理](https://cn.vuejs.org/v2/guide/events.html)
------------------------------------------------------

* `v-on` 指令监听 DOM 事件，并在触发时运行一些 JavaScript 代码。
* 有时需要在内联语句处理器中访问原始的 DOM 事件。可以用特殊变量 `$event` 把它传入方法，例如：

```js
<button v-on:click="warn('Form cannot be submitted yet.', $event)">
  Submit
</button>

methods: {
  warn: function (message, event) {
    // 现在我们可以访问原生事件对象
    if (event) event.preventDefault()
    alert(message)
  }
}
```

* [事件修饰符](https://cn.vuejs.org/v2/guide/events.html#%E4%BA%8B%E4%BB%B6%E4%BF%AE%E9%A5%B0%E7%AC%A6)。语法：v-on:事件名称.事件修饰符
  * `.stop`
  * `.prevent`
  * `.capture`
  * `.self`
  * `.once`
  * `.passive`

1.12 [表单输入绑定](https://cn.vuejs.org/v2/guide/forms.html)
-------------------------------------------------------

二、组件
====

2.1 语法
------

```js
Vue.component('组件名称', {
  data: function () {
    return {
      数据属性1:值1,
      数据属性2:值2,
      ............
      ............
    }
  },
  template: '组件模板定义',
  methods:{
    ......  
  },
  computed:{
    ......  
  },
  watch:{
    ......
  }
  created:function(){
    .....
  },
  ......
})
```

**2.2 注意点**
-----------

1. 组件是可复用的 Vue 实例
2. 没有el属性
3. data必须是一个方法/函数，并return，只有这样才能保证每个实例可以维护一份被返回对象的独立的拷贝
4. 其它接收的选项与new Vue()一致（同第一点说明）
5. 组件有两种注册形式：[全局注册](https://cn.vuejs.org/v2/guide/components.html#%E7%BB%84%E4%BB%B6%E7%9A%84%E7%BB%84%E7%BB%87)[与]()[局部注册](https://cn.vuejs.org/v2/guide/components-registration.html#%E5%B1%80%E9%83%A8%E6%B3%A8%E5%86%8C)
6. 组件名称应为多个单词且有“-”连接符，这样可以避免跟现有以及未来的HTML元素名称冲突（所有的 HTML 元素名称都是单个单词）
7.

2.3 通过 Prop 向子组件传递数据（划重点）
-------------------------

[](https://cn.vuejs.org/v2/style-guide/#Prop-%E5%AE%9A%E4%B9%89-%E5%BF%85%E8%A6%81)

[参考信息](https://cn.vuejs.org/v2/style-guide/#Prop-%E5%AE%9A%E4%B9%89-%E5%BF%85%E8%A6%81)

```js
// 定义组件
Vue.component('组件名称', {
    // 基础定义方式
    prop:['Prop属性1','Prop属性2','......'],
    // 或者
    // props: {
    //     title: String,
    //     likes: Number,
    //     isPublished: Boolean,
    //     commentIds: Array,
    //     author: Object
    // },
    // 或者
    // props: {
    //     title: {
    //         type:String,
    //         required:true,
    //         default:"",
    //     },
    //     likes: Number,
    //     isPublished: Boolean,
    //     commentIds: Array,
    //     author: {
    //         type: Object,
    //         // 对象或数组默认值必须从一个工厂函数获取
    //         default: function () {
    //             return { message: 'hello' }
    //         }
    //     }
    // },
    data:function(){
        return {
            
        }
    },
    template: `
    
    `
})
```

使用基础方式定义Prop时使用**数组**的形式将属性列出；使用高级一点的方式定义Prop时使用**对象**的形式定义属性。

关于更详细的Prop验证参考：[Prop验证](https://cn.vuejs.org/v2/guide/components-props.html#Prop-%E9%AA%8C%E8%AF%81)

2.4 [通过事件向父级组件发送消息](https://cn.vuejs.org/v2/guide/components.html#%E9%80%9A%E8%BF%87%E4%BA%8B%E4%BB%B6%E5%90%91%E7%88%B6%E7%BA%A7%E7%BB%84%E4%BB%B6%E5%8F%91%E9%80%81%E6%B6%88%E6%81%AF)

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

[$emit](https://cn.vuejs.org/v2/api/#vm-emit)

```sh
$emit( eventName, […args] )
```

**示例：**

```js
// 定义组件
Vue.component('welcome-button', {
  template: `
    <button v-on:click="$emit('welcome')">
      Click me to be welcomed
    </button>
  `
})

// 使用组件
<div id="emit-example-simple">
  <welcome-button v-on:welcome="sayHi"></welcome-button>
</div>

// VUE
new Vue({
  el: '#emit-example-simple',
  methods: {
    sayHi: function () {
      alert('Hi!')
    }
  }
})
```

* eventName对应父级组件v-on绑定的事件，即父级组件v-on:eventName=“xxxxx”
* $emit( eventName, […args] )加入参数时，父级组件v-on:eventName=“xxxxx”中不用加括号接收，直接在methods对应的方法中接收形参即可：

```js
// 定义组件
Vue.component('welcome-button', {
  template: `
    <button v-on:click="$emit('welcome','这是参数')">
      Click me to be welcomed
    </button>
  `
})

// 使用组件
<div id="emit-example-simple">
  //<welcome-button v-on:welcome="sayHi(data)"></welcome-button>
  <welcome-button v-on:welcome="sayHi"></welcome-button>
</div>

// VUE
new Vue({
  el: '#emit-example-simple',
  methods: {
    sayHi: function (data) {
      alert('Hi!'+data)
    }
  }
})
```

2.5 组件间的通讯方式
------------

![](https://ws2.sinaimg.cn/large/006tNc79ly1fyuqpmu6rlj30qa0e476u.jpg)

三、[模块系统](https://cn.vuejs.org/v2/guide/components-registration.html#%E6%A8%A1%E5%9D%97%E7%B3%BB%E7%BB%9F)
=========================================================================================================

模块化组件也是Vue的一大亮点。实际开发过程中可根据业务需要、实际功能场景封装一些组件，对于前端功底不好的开发人员可以不用去考虑组件具体的样式实现，拿来即用。

 通过一种积木式累积组件，构建一个灵活的页面。

 在之后的Vue生态中，Vue文件(\*.vue)就可视为一个组件，平时开发中我们利用简单的Vue功能，使用局部注册组件或者全局注册组件即可。

四、插槽-slot
=========

插槽内可以包含任何内容，例如： 文本、HTML、组件等。

如果定义的组件没有slot插槽，那么插入的数据将会自动舍弃，假定现在有一个\<nav-link url="\#"\>\</nav-link\>的插槽，正常情况下只定义了一个url的prop属性，没有定义插槽，此时如果我们这么使用：

```js
<nav-link url="#">百度一下</nav-link>
```

此时，"百度一下"将会被舍弃。

4.1 普通插槽
--------

**\<slot\>\</slot\>**

```js
Vue.component('navigation-link', {
    props: {
        url: {
            type: String,
            required: true
        }
    },
    template: `
        <a v-bind:href="url">
            <slot></slot>
        </a>
    `
});
```

使用：

```js
<navigation-link url="https://www.baidu.com">百度一下</navigation-link>
```

其中，“百度一下”就是slot插槽的内容

4.2 具名插槽
--------

**\<slot name="插槽名称****"****\>\</slot\>**

```js
Vue.component('base-layout',{

    template:`
        <div class="container">
            <header style="background: aquamarine">
                <slot name="header"></slot>
            </header>
            
            <main style="background: #3778D5">
                 <slot></slot>
            </main>
            
            <footer style="background: aquamarine">
                 <slot name="footer"></slot>
            </footer>
        </div>
    `
});
```

使用：

```js
<base-layout>
    <template slot="header">
        <h1>页头部分</h1>
    </template>

    <p>主题内容部分.</p>

    <template slot="footer">
        <p>页脚部分</p>
    </template>
</base-layout>
```

效果图：

![](https://ws4.sinaimg.cn/large/006tNc79ly1fyuqps270yj30nu07iaau.jpg)

五、路由：VueRouter
==============

Vue Router 是 [Vue.js](http://cn.vuejs.org/)官方的路由管理器。它和 Vue.js 的核心深度集成，让构建单页面应用变得易如反掌。包含的功能有：

* 嵌套的路由/视图表
* 模块化的、基于组件的路由配置
* 路由参数、查询、通配符
* 基于 Vue.js 过渡系统的视图过渡效果
* 细粒度的导航控制
* 带有自动激活的 CSS class 的链接
* HTML5 历史模式或 hash 模式，在 IE9 中自动降级
* 自定义的滚动条行为

5.1 路由定义
--------

**html:**

```js
<div id="app">
    <router-view></router-view>
    
    <router-link to="/user/guofu/profile">profile</router-link>
    <router-link to="/userapp">userapp</router-link>
    <br>
</div>
```

**JavaScript：**

```js
const User = {
    template: `
        <div class="user">
            <h2>User {{ $route.params.id }}</h2>
            <router-view></router-view>
        </div>
    `
}
const router = new VueRouter({
    routes: [
        {
            path: "路由地址，必选。例如/user/:id，则匹配/user/zhangsan、/user/lisi",
            name:"路由名称，可选。默认名称为：default"
            component: "组件名称。即当路由匹配到信息要加载的内容/要跳转的页面。<router-view></router-view>作为承载口，例如此处可以填写上面定义的：User",
            // 以上为路由配置的基本信息，下面是children可选的，用在路由嵌套时候使用
            
            // 可选
            children: [
                {
                    // 当 /user/:id/profile 匹配成功，
                    // UserProfile 会被渲染在 User 的 <router-view> 中
                    path: "profile",
                    component: UserProfile
                }
            ],
            // 可选。注意是components，且不再是数组，二是对象。用在有多个<router-view>的时候
            components:{
                router-view的name名称:组件名称,
                ... ... ...
            },
            // 可选。具体可参考：https://router.vuejs.org/zh/guide/essentials/passing-props.html#布尔模式
            props:{}
            
        }
        // ... ... ...
    ]
});
```

5.2 路由组件延迟加载
------------

一般在路由中我们在开头都是import组件，然后在路由定义的时候使用component指定要加载的组件，如果有大量的组件需要在路由使用，这种方式就会欠妥，最好的方式就是匹配到具体路由信息之后再去加载组件：

```js
component: () => import( './views/About.vue')//延迟加载
```

---

详细的routes属性配置信息如下：

routes

类型: `Array<RouteConfig>`

`RouteConfig` 的类型定义：

```js
declare type RouteConfig = {
  path: string;
  component?: Component;
  name?: string; // 命名路由
  components?: { [name: string]: Component }; // 命名视图组件
  redirect?: string | Location | Function;
  props?: boolean | Object | Function;
  alias?: string | Array<string>;
  children?: Array<RouteConfig>; // 嵌套路由
  beforeEnter?: (to: Route, from: Route, next: Function) => void;
  meta?: any;

  // 2.6.0+
  caseSensitive?: boolean; // 匹配规则是否大小写敏感？(默认值：false)
  pathToRegexpOptions?: Object; // 编译正则的选项
}
```

[详情参考-router-构建选项](https://router.vuejs.org/zh/api/#router-%E6%9E%84%E5%BB%BA%E9%80%89%E9%A1%B9)

5.3 路由的高级使用
-----------

简单的项目我们都是直接在入口处（main.js）引入router，但是一些复杂一点的项目我们需要对路由作进一步的控制，例如跳转动画处理、token校验等，此时仅仅引入路由过于简单，因此我们需要对路由进行更细致的配置，例如：

![](https://ws3.sinaimg.cn/large/006tNc79ly1fyuqpw51e6j30bg058mxi.jpg)

index.js：路由主入口，对路由的具体控制操作

routers.js：路由信息的具体配置（路径处理）

before-close.js：相关关闭操作的钩子函数，meta属性中配置

其中，index.js的写法建议如下：

```js
// 引入Vue
import Vue from 'vue'
// 引入vue-router
import Router from 'vue-router'
// 引入自己定义的路由具体配置
import routes from './routers'

Vue.use(Router)

// 创建路由实例
const router = new Router({
  routes,
  mode: 'history'
})

// 定义路由守卫方法beforeEach、afterEach
router.beforeEach((to, from, next) => {
    
})

router.afterEach(to => {
  
})

// 重点：最后export当前的路由
export default router
```



5.4 命名视图
--------

一般一个页面有一个\<router-view\>\</router-view\>路由出口，路由匹配到的组件将会渲染在此处。当有

5.5 编程式导航
---------

[参考资料](https://router.vuejs.org/zh/guide/essentials/navigation.html)

[有关路由的详尽内容请参考此处](https://router.vuejs.org/zh/installation.html)

六、规范梳理
======

[具体参考](https://cn.vuejs.org/v2/style-guide/#%E5%9F%BA%E7%A1%80%E7%BB%84%E4%BB%B6%E5%90%8D-%E5%BC%BA%E7%83%88%E6%8E%A8%E8%8D%90)

* 组件尽量分文件保存，不要在一个js文件里面定义多个组件
* ![](resources/6D580E29E887A1F15E4AEBDC65B5F123.jpg)
* [单文件组件](https://cn.vuejs.org/v2/guide/single-file-components.html)的文件名应该要么始终是单词大写开头 (PascalCase)，要么始终是横线连接 (kebab-case)。
* ![](resources/442B9FE2F061FC76B9DD16956596558D.jpg)

* 组件名称字母全小写且必须包含一个连字符

* 组件名应该倾向于完整单词而不是缩写。

* ![](resources/84017C41EABFC5F3AC5800CB281DF21D.jpg)

* prop名规范：在声明 prop 的时候，其命名应该始终使用 camelCase，而在模板和 [JSX](https://cn.vuejs.org/v2/guide/render-function.html#JSX) 中应该始终使用 kebab-case。我们单纯的遵循每个语言的约定。在 JavaScript 中更自然的是 camelCase；而在 HTML 中则是 kebab-case。
* ![](resources/87478E54C1ABC73BB91F9099F6307DCE.jpg)
* 事件名不同于组件和 prop，事件名不存在任何自动化的大小写转换。而是触发的事件名需要完全匹配监听这个事件所用的名称

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

```js
        this.$emit('myEvent')
```

则监听这个名字的 kebab-case 版本是不会有任何效果的：

```js
        <my-component v-on:my-event="doSomething"></my-component>
```

因为 `v-on` 事件监听器在 DOM 模板中会被自动转换为全小写 (因为 HTML 是大小写不敏感的)，所以 `v-on:myEvent` 将会变成 `v-on:myevent`——导致 `myEvent` 不可能被监听到。因此，推荐始终使用 kebab-case 的事件名。

七、Vue生态需要掌握的一些技术点
=================

如果是仅仅使用Vue的基础功能的话，只要掌握HTML+CSS+JavaScript即可。但是要是用到整个Vue生态构建一个大型项目，最起码需要掌握以下内容，不然代码不管看起来还是写起来都会比较费劲：

1. [ECMAScript（ES6）](http://es6.ruanyifeng.com)
  1. [ECMAScript ES6 总结](quiver:///notes/3519FED7-7A6A-4BC0-A4E7-01439F400D76)
  2. [ES6总结](quiver:///notes/B9DFB529-4B47-4BB5-9E1D-4FBD70C9EA5C)
2. [Vue Cli 3（@vue/cli）](https://cli.vuejs.org/zh/guide/)
3. [NPM](https://www.npmjs.cn)相关内容：node.js包管理器（安装、卸载、更新、查看、搜索、发布等）
4. [WebPack](https://webpack.docschina.org/concepts/)
5. [Vue Router](https://router.vuejs.org/zh/installation.html)
6. [Vuex](https://vuex.vuejs.org/zh/) 状态管理
7. [Axois HTTP库](https://www.kancloud.cn/yunye/axios/234845) 前后端分离（[点击访问示例](https://smallsnail-wh.github.io/)）

以上仅列出主要的技术点，未做细化。在学习过程中还会遇到连带效应，由点及面，360度扩展。

[RESTful 总结](quiver:///notes/361A6CAD-F246-45AE-8700-B81EB88004B7)

Vue整体生态还是比较复杂的，涉及到的内容也比较多，深入学习的话有一定的成本。初期还是建议使用Vue的基础功能，仅当其作为提高前端开发效率的工具使用。例如应用Vue的数据绑定、动态渲染、组件化等特性；后期在Vue熟练使用之后考虑使用整个Vue生态构建项目：Vue+Webpack构建前端，SpringBoot或者普通J2EE构建后端（RESTful架构：目前最流行的 API 设计规范，用于 Web 数据接口的设计）

八、[Vue Cli 3](https://cli.vuejs.org/zh/guide/)

Vue CLI 是一个基于 Vue.js 进行快速开发的完整系统，提供：

* 通过 `@vue/cli` 搭建交互式的项目脚手架。
* 通过 `@vue/cli` + `@vue/cli-service-global` 快速开始零配置原型开发。
* 一个运行时依赖 (`@vue/cli-service`)，该依赖：
  * 可升级；
  * 基于 webpack 构建，并带有合理的默认配置；
  * 可以通过项目内的配置文件进行配置；
  * 可以通过插件进行扩展。
* 一个丰富的官方插件集合，集成了前端生态中最好的工具。
* 一套完全图形化的创建和管理 Vue.js 项目的用户界面。

Vue CLI 致力于将 Vue 生态中的工具基础标准化。它确保了各种构建工具能够基于智能的默认配置即可平稳衔接，这样你可以专注在撰写应用上，而不必花好几天去纠结配置的问题。与此同时，它也为每个工具提供了调整配置的灵活性，无需 eject。

九、常用代码块分析以及注意事项（持续增加中...）
=========================

9.1 Vue创建以及挂载根实例
----------------

**代码块一：**

```js
const app = new Vue({
    
}).$mount('#app')
```

**代码块二：**

```js
const app = new Vue({
    el:"#app"
})
```

**分析：**

以上两段代码最大的区别就是代码块一最后使用了.$mount(elementOrSelector) 而代码块二还是使用的传统方式。

如果 Vue 实例在实例化时没有收到 el 选项，则它处于“未挂载”状态，没有关联的 DOM 元素。可以使用 `vm.$mount()` 手动挂载一个未挂载的实例。

如果没有提供 `elementOrSelector` 参数，模板将被渲染为文档之外的的元素，并且你必须使用原生 DOM API 把它插入文档中。

这个方法返回实例自身，因而可以链式调用其它实例方法。

9.2 使用Webpack打包运行项目的问题
----------------------

默认配置下，编译之后项目生成在dist目录下，这里不能直接在浏览器访问（file://模式），必须要在HTTP服务容器内才能访问。

9.3 vue-cli与WebPack构建Vue脚手架步骤
-----------------------------

### 1) 全局安装 vue-cli

 npm install --global vue-cli

### 2) 创建一个基于 webpack 模板的新项目

 vue init webpack my-project

### 3) npm-安装依赖

 cd my-project

 npm install

 npm run dev

9.4 当一个页面存在多个\<router-view\>的处理
-------------------------------

我们知道，多数情况下，一个页面内存在一个\<router-view\>，但是有时候我们想同级显示，此时为了让Vue知道到底去渲染哪一个视图，就需要我们为\<router-view\>视图起一个名字以示区分。

```html
<router-view></router-view>
<router-view name='视图名称1'></router-view>
<router-view name='视图名称2'></router-view>
```

视图名称不写，默认是：default，然后就需要我们在路由里面进行配置：

```js
routes: [
  {
    path: '路径',
    components: {
        'default': 默认视图名称
        '视图名称1': 组件名称1,
        '视图名称2': 组件名称2
    }
  }
]
```

component:'组件名称' 等价于 components:{'default':'组件名称'}

9.5 render渲染
------------

```js
render:function(h,param){
    return h('html标签名称',插入的数据内容[如果是渲染嵌套标签，则需要数组参数，依次类推]);
}
```

h：创建DOM的方法，createElement

param：对象参数，视具体情况而定

返回值：虚拟DOM节点

h方法具体内容：

```js
// @returns {VNode}
createElement(
  // {String | Object | Function}
  // 一个 HTML 标签字符串，组件选项对象，或者
  // 解析上述任何一种的一个 async 异步函数。必需参数。
  'div',

  // {Object}
  // 一个包含模板相关属性的数据对象
  // 你可以在 template 中使用这些特性。可选参数。
  {
      // 和`v-bind:class`一样的 API
      // 接收一个字符串、对象或字符串和对象组成的数组
      'class': {
        foo: true,
        bar: false
      },
      // 和`v-bind:style`一样的 API
      // 接收一个字符串、对象或对象组成的数组
      style: {
        color: 'red',
        fontSize: '14px'
      },
      // 普通的 HTML 特性
      attrs: {
        id: 'foo'
      },
      // 组件 props
      props: {
        myProp: 'bar'
      },
      // DOM 属性
      domProps: {
        innerHTML: 'baz'
      },
      // 事件监听器基于 `on`
      // 所以不再支持如 `v-on:keyup.enter` 修饰器
      // 需要手动匹配 keyCode。
      on: {
        click: this.clickHandler
      },
      // 仅用于组件，用于监听原生事件，而不是组件内部使用
      // `vm.$emit` 触发的事件。
      nativeOn: {
        click: this.nativeClickHandler
      },
      // 自定义指令。注意，你无法对 `binding` 中的 `oldValue`
      // 赋值，因为 Vue 已经自动为你进行了同步。
      directives: [
        {
          name: 'my-custom-directive',
          value: '2',
          expression: '1 + 1',
          arg: 'foo',
          modifiers: {
            bar: true
          }
        }
      ],
      // 作用域插槽格式
      // { name: props => VNode | Array<VNode> }
      scopedSlots: {
        default: props => createElement('span', props.text)
      },
      // 如果组件是其他组件的子组件，需为插槽指定名称
      slot: 'name-of-slot',
      // 其他特殊顶层属性
      key: 'myKey',
      ref: 'myRef',
      // 如果你在渲染函数中向多个元素都应用了相同的 ref 名，
      // 那么 `$refs.myRef` 会变成一个数组。
      refInFor: true
  },

  // {String | Array}
  // 子虚拟节点 (VNodes)，由 `createElement()` 构建而成，
  // 也可以使用字符串来生成"文本虚拟节点"。可选参数。
  [
    '先写一些文字',
    createElement('h1', '一则头条'),
    createElement(MyComponent, {
      props: {
        someProp: 'foobar'
      }
    })
  ]
)
```

假如创建一个按钮：![](https://ws1.sinaimg.cn/large/006tNc79ly1fyuqqhosgoj302i01kglj.jpg)的HTML结构如下：

```html
<div>
    <Button type='primary' size='small' style='margin-right: 5px;' onclick='show()'>查看</Button>
</div>
```

则基于iView的渲染函数这么定义：

（render 函数传入两个参数，第一个是 h，第二个是对象，包含 row、column 和 index，分别指当前单元格数据，当前列数据，当前是第几行。）

```js
render:(h,param)=>{
    return h('div',[
        h('Button',{
            props:{
                type:'primary',
                size:'small'
            },
            style:{
                mariginRight:'5px'
            },
            on:{
                click:()=>{
                    // ....
                }
            }
        },'查看')    
    ])
}
```

理清嵌套关系，明确关键属性名，依次声明。具体参考：

[render渲染函数](https://cn.vuejs.org/v2/guide/render-function.html)

9.6 Vue+Webpack项目的import中’@’的作用
-------------------------------

这是webpack的路径别名，相关代码定义在配置文件webpack.base.config里：

```js
resolve: {
    // 自动补全的扩展名
    extensions: ['.js', '.vue', '.json'],
    // 默认路径代理
    // 例如 import Vue from 'vue'，会自动到 'vue/dist/vue.common.js'中寻找
    alias: {
        '@': resolve('src'),
        '@config': resolve('config'),
        'vue$': 'vue/dist/vue.common.js'
    }
}
```

其中resolve（）函数是文件里面自定义的函数：

```js
function resolve (dir) {
  return path.join(__dirname, '..', dir)
}
```

我们也可以自定义路径：

```js
alias: {
    '@': resolve('src'),
    '@config': resolve('config'),
    'vue$': 'vue/dist/vue.common.js'，
    '@components':path.join(__dirname, '..', 'src/components')//组件路径
}
```

9.10 注意常规函数和箭头函数在使用中'this’的区别
-----------------------------

普通函数的this表示它的直接调用者，即this根据调用情况不断变化，是执行对象；箭头函数的this是固定的，表示定义该箭头函数的所处对象，而不是执行时的对象。

参考[箭头函数与普通函数的区别](https://www.cnblogs.com/biubiuxixiya/p/8610594.html)