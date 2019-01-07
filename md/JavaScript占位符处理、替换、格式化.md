# JavaScript 占位符处理 替换 格式化

> 很多时候我们在JavaScript里面拼接一些html元素，直接是字符串拼接，涉及到很多双引号、单引号问题，慢慢就会感觉很麻烦，可读性也大大降低，拼接过程中还容易出错。我们为什么不借鉴一下Java里面或者Python里面的字符串格式化呢？

## 代码

```javascript
String.prototype.format = function() {
    if (arguments.length == 0) return this;
    var param = arguments[0];
    var s = this;
    if (typeof(param) == 'object') {
        for (var key in param) s = s.replace(new RegExp("\\{" + key + "\\}", "g"), param[key]);
        return s;
    } else {
        for (var i = 0; i < arguments.length; i++) s = s.replace(new RegExp("\\{" + i + "\\}", "g"), arguments[i]);
        return s;
    }
}
```

## 调用示例

### 对象方式
```javascript
var cameraName = "id='{id}'  class='{class}'";

var  param={id:"cm1",class:"newClass"}
console.log(cameraName.format(param));
```

### 数组方式
```javascript
var cameraName = "id='{0}'  class='{1}'";

var  param=["cm1","newClass"]
console.log(cameraName.format(param));
```