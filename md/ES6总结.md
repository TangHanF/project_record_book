# ES6总结

> 作者：GuoFu
>
> 日期：2018年12月29日
>
> 说明：
>
> 联系方式：guofu_gh@163.com

[ES6总结](quiver:///notes/B9DFB529-4B47-4BB5-9E1D-4FBD70C9EA5C)

1、let、const命令
=============

**let：**

* let定义变量，变量作用域是块级作用域。所声明的变量，只在`**let**`命令所在的代码块内有效。
* `let`不允许在相同作用域内，重复声明同一个变量。

**const：**

* const定义常量，相当于java中的final关键字。const声明常量之后就必须立即初始化！

**ES6中不存在变量提升**。以前变量可以var声明前使用，变量默认值为undefined，现在let不允许这样，必须先声明才能使用。

ES5中的for循环存在一定的安全隐患，因为ES5中只有全局作用域、函数作用域，for循环中声明的计数器会出现泄露，导致其升级为全局变量，例如：

```javascript
var i
for (var i = 0;i < 10;i++ ){
    // ...
}
console.log(i);// 10 
```

此时上面的变量i就变成了全局变量。如果i变量名称取一个其他名称，例如’name’，可能就会破坏原来的name变量。所以我们在ES5中还是推荐使用jQuery的$.each()进行循环。不过使用ES6语法的话，for循环计数器使用let声明就不会出现此问题了，这样for循环也就安全了，上面的for循环可以修改为：

```javascript

for (let i = 0;i < 10;i++ ){
    // ...
}
console.log(i);// 提示变量 i 未定义错误
```

2、块级作用域
=======

块级作用域的出现，实际上使得获得广泛应用的立即执行函数表达式（IIFE）不再必要了。

```javascript
// IIFE 写法
(function () {
  var tmp = ...;
  ...
}());

// 块级作用域写法
{
  let tmp = ...;
  ...
}
```

3、解构
====

解构支持数组解构、对象解构、字符串解构、数值解构、布尔值解构、函数参数解构

解构的作用
-----

**（1）交换变量的值**

**（2）从函数返回多个值****
**

**（3）函数参数的定义****
**

**（4）提取 JSON 数据（对象解构的应用）****
**

**（5）函数参数的默认值****
**

**（6）遍历 Map 结构****
**

**（7）输入模块的指定方法****
**

3.1 数组解构
--------

```javascript
// 从数组中提取值，按照对应位置，对变量赋值。
let [a,b,c]=[1,2,3]
//a=1
//b=2
//c=3

let [a,,c]=[1,2,3]
//a=1
//c=3
```

3.2 对象解构 {…obj}
---------------

语法：

```javascript
let { 匹配模式:变量, 匹配模式:变量 } = 数据;
```

例如：

```javascript
let { foo, bar } = { foo: "aaa", bar: "bbb" };
```

以上解构的完整写法：

```javascript
let { foo:foo, bar:bar } = { foo: "aaa", bar: "bbb" };
```

定义别名：

```javascript
let { foo:fooObj, bar:barObj } = { foo: "aaa", bar: "bbb" };
//fooObj="aaa"
//barObj="bbb"
```

...是扩展运算符。**解构**

```js
// Config.js
import Settings from './Setting'
const myConfig = {
    gConfig:{...Settings}  //就是这句话
}
```

gConfig:{…Settings} 和 gConfig:Settings 这2种赋值方式的区别：

第一种，`myConfig.gConfig === Settings` 为`false`
第二种, `myConfig.gConfig === Settings` 为 `true`

一般用第一种，是为了避免对`myConfig.gConfig`进行修改的时候，影响到`Settings`

假设 setting={key:1};
第一种 gConfig={key:1}
第二种 gConfig={setting：{key:1}}

### 对象解构示例

```javascript
const node = {
    loc: {
        start: {
            line: 1,
            column: 5
        }
    }
};

let {loc, loc: {start}, loc: {start: {line}}, loc: {start: {column}}} = node;
console.log("line:"+line);
console.log("column:"+column);
```

以上代码进行了四次解构赋值，分别是loc、start、line、column，其中最后两次解构中，loc和start都是模式并非变量

3.3 字符串解构
---------

字符串的解构会将字符串转为数组

```javascript
let [a,b,c,d,e]="hello"
//a=h
//b=e
//c=l
//d=l
//e=0
```

3.4 数值和布尔值解构
------------

会先自动转为对象

3.5 函数参数解构
----------

### 3.5.1 基本

```javascript
function add([x, y]){
  return x + y;
}

add([1, 2]); // 3
```

函数`add`的参数表面上是一个数组，但在传入参数的那一刻，数组参数就被解构成变量`x`和`y`。对于函数内部的代码来说，它们能感受到的参数就是`x`和`y`。

### 3.5.2 默认参数/函数参数默认值

```javascript
function testSum({a = 0, b = 0} = {}) {
    return a + b;
}

testSum({a:1,b:2});//3
testSum({a:1,b:2});//0
```

函数testSum的参数是一个对象,并且对象的属性都有默认值：0。很多人奇怪 {a = 0, b = 0} = {} 是什么意思，其实它的意思就是说如果没有给testSum函数提供参数，就创建一个默认的空对象'{}' ，例如这么调用方法：

```javascript
testSum();// 0
```

如果把testSum的参数改为如下：

```javascript
function testSum({a = 0, b = 0} ) {
    return a + b;
}

testSum();//报错。Cannot destructure property `a` of 'undefined' or 'null'.
testSum({});//正常
```

所以，{a = 0, b = 0} = {} 其实就是方便我们在不传入参数调用方法，方法自动使用默认值处理

---

**题外话：**

****

以前ES5是不支持函数参数设置默认值的，所以很多时候很多人都会判断变量是不是null、undefined等，然后赋初始值，或者其它变通方法，例如：

```javascript
function testMethod(name){
    // 方式一：
    if (!name) 
        name="默认值";
    
    // 方式二：
    name = name || "默认值";
}
```

建议还是使用方式二，方式一略显low👎 😆。总体来说，以上关于默认值的处理还是有欠缺的地方的，如果参数传值了，但是传入的是布尔类型的false呢？结果就将传入的false改成了默认值，不是期望的吧？为了避免这个问题，通常需要先判断一下参数`y`是否被赋值，如果没有，再等于默认值。

```javascript
if (typeof y === 'undefined') {
  y = '默认值';
}
```

而ES6中就可以直接为函数参数提供默认值：

```javascript
function testMethod(name = "默认值"){
    
}
```

这种情况就和Python很像了😆，参数灵活，阅读方便，一看就知道哪些参数是可以省略的。





4、箭头函数
======

var 变量名/函数名 = （参数，参数）=\> {代码块}

```js
var f = v => v;
//等同于
var f = function(v) {
  return v;
};

var f = () => 5;
// 等同于
var f = function () { return 5 };

var sum = (num1, num2) => num1 + num2;
// 等同于
var sum = function(num1, num2) {
  return num1 + num2;
};

```

注意：如果return的是一个对象{id:id,age:age},那么箭头右边要用括号包起来().

**5、模板字符串**
===========

模板字符串采用反引号（`）标识，并且模板字符串中的空格、换行将在输出时有所保留。

```js

// 普通字符串
`In JavaScript '\n' is a line-feed.`

// 多行字符串
`In JavaScript this is
 not legal.`

console.log(`string text line 1
string text line 2`);

// 字符串中嵌入变量
let name = "Bob", time = "today";
`Hello ${name}, how are you ${time}?`

```

${主体}，其中主体可以是表达式、运算、对象属性还可以是函数，若是字符串将直接输出该字符串。

****
====

**6、含参函数的调用**
=============

```js
function say(something){
    console.log("she say"+" '"+something+"'" );
}
say`hello`;                             //she say 'hello'
```

等同于say('hello')。