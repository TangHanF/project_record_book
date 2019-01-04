# 为Layui的Tab选项卡增加关闭当前、关闭其它操作


# 特别说明，教程已更新，请移步：[此处](https://github.com/TangHanF/ProjectRecord/blob/master/%E5%89%8D%E7%AB%AF/LayUI/4%E3%80%81%E3%80%90%E6%9B%B4%E6%96%B0%E3%80%91%E4%B8%BALayui%E7%9A%84Tab%E9%80%89%E9%A1%B9%E5%8D%A1%E5%A2%9E%E5%8A%A0%E5%85%B3%E9%97%AD%E5%BD%93%E5%89%8D%E3%80%81%E5%85%B3%E9%97%AD%E5%85%B6%E5%AE%83%E6%93%8D%E4%BD%9C.md)
----

- 首先管理端模板的话还是使用官方提供的，参考链接：[点此打开后台布局页面](http://www.layui.com/demo/layuiAdmin.html)

- 以下我只列举出关键代码，各位根据实际情况拷贝到自己项目适当位置
- 目前仅仅加入了：关闭当前、关闭所有，各位可以继续扩展，例如关闭左侧所有、关闭右侧所有、关闭其它，不是很难，循环判断即可。当然了，后面有时间我也会完善一下此功能

# 效果图
![](https://github.com/TangHanF/ProjectRecord/raw/master/前端/LayUI/img/tab右键菜单.png)

----------
# HTML
首先在body里面插入以下一段html:
```html
    <ul class="rightmenu">
        <li data-type="closethis">关闭当前</li>
        <li data-type="closeall">关闭所有</li>
    </ul>
```
    我们暂且就实现两个功能吧，其它功能自行扩展即可。相关CSS样式请看下面《CSS样式》部分

-------

# JS

```javascript
/**
* 注册tab右键菜单点击事件
*/
$(".rightmenu li").click(function () {
    if ($(this).attr("data-type") == "closethis") {
        var tabid = $("li[class='layui-this']").attr('lay-id');// 获取当前激活的选项卡ID
        tabDelete(tabid);
    } else if ($(this).attr("data-type") == "closeall") {
        var tabtitle = $(".layui-tab-title li");
        var ids = new Array();
        $.each(tabtitle, function (i) {
            ids[i] = $(this).attr("lay-id");
        })
        tabDeleteAll(ids);
    }
    $('.rightmenu').hide();
})
```
--------------------
```javascript
tabDelete = function (id) {
    console.log("删除的TabID："+id)
    element.tabDelete("你的Tab选项卡ID", id);//删除
}
tabDeleteAll = function (ids) {
    $.each(ids, function (i, item) {
        element.tabDelete("你的Tab选项卡ID", item);
    })
}
```
--------------------
```javascript
// 点击空白处关闭右键弹窗
$(document).click(function () {
    $('.rightmenu').hide();
})
```
----------------
```javascript
/**
* 绑定右键菜单
* @constructor
*/
function CustomRightClick () {
    //屏蔽右键
    $('.layui-tab-title li').on('contextmenu', function () {
        return false;
    })
    $('.layui-tab-title,.layui-tab-title li').click(function () {
        $('.rightmenu').hide();
    });
    $('.layui-tab-title li').on('contextmenu', function (e) {
        var popupmenu = $(".rightmenu");
        l = ($(document).width() - e.clientX) < popupmenu.width() ? (e.clientX - popupmenu.width()) : e.clientX;
        t = ($(document).height() - e.clientY) < popupmenu.height() ? (e.clientY - popupmenu.height()) : e.clientY;
        popupmenu.css({left: l, top: t}).show();
        return false;
    });
}
```

-------
# CSS样式
```css
<style>
    /**右键菜单*/
    .rightmenu {
        position: absolute;
        width: 110px;
        z-index: 9999;
        display: none;
        background-color: #fff;
        padding: 2px;
        color: #333;
        border: 1px solid #eee;
        border-radius: 2px;
        cursor: pointer;
    }

    .rightmenu li {
        text-align: center;
        display: block;
        height: 30px;
        line-height: 32px;
    }

    .rightmenu li:hover {
        background-color: #666;
        color: #fff;
    }
</style>
```


# 问题
- 右击关闭暂时只能关闭当前已经激活的Tab，没法在任意一个Tab右击自动激活再去关闭，各位可优化一下
