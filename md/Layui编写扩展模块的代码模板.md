# Layui编写扩展模块的代码模板

## js模板

```javascript
layui.define(['xxxx'], function (exports) {
    "use strict";

    var MOD_NAME = '模块名称';
    var MOD_OBJ = function () {
        this.v = '1.0.1';
    };

    /**
    * 初始化表格选择器
    */
    MOD_OBJ.prototype.render = function (opt) {

        var elem = $(opt.elem);

        //默认设置
        opt.searchKey = opt.searchKey || 'keyword';
        opt.searchPlaceholder = opt.searchPlaceholder || '关键词搜索';
        opt.table.page = opt.table.page || true;
        opt.table.height = opt.table.height || 315;

         
    }
  

    exports(MOD_NAME, MOD_OBJ);
})
```

> 注意：MOD_NAME要和js文件名一致！

## 使用

```javascript
layui.use(['模块名称'], function(){
  var 模块名称 = layui.模块名称;
  // ...
});
```

或者

```javascript
var xxxx = layui.模块名称;
```