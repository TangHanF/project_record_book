# JavaScript Ajax封装

```javascript
/**
 * 通用POST请求函数(有参) 返回参数String
 * @param way 同步 false 异步 true
 * @param url 请求地址
 * @param data 请求参数
 * @param success 回调函数
 */
function ajaxNotJsonParamPOST(way , url , params , success){
    $.ajax({
        type: "POST",
        url: url,
        async: way ,
        data : params ,
        beforeSend: function(request) {
            
        },
        success: function(msg){
            success(msg);
        }
    });
}

/**
 * 通用POST请求函数(有参) 返回参数json
 * @param way 同步 false 异步 true
 * @param url 请求地址
 * @param data 请求参数
 * @param success 回调函数
 */
function ajaxParamPOST(way , url , params , success){
    $.ajax({
        type: "POST",
        url: url,
        async: way ,
        dateType: "json",
        data : params ,
        beforeSend: function(request) {
            
        },
        success: function(msg){
            success(msg);
        }
    });
}
function ajaxParamPOSTBody(way , url , params , success){
    $.ajax({
        type: "POST",
        url: url,
        async: way ,
        dataType:"json",
        contentType:"application/json",
        data:JSON.stringify(params),
        beforeSend: function(request) {
            
        },
        success: function(msg){
            success(msg);
        }
    });
}

function ajaxParamTypePOST(way , url ,contentType , data , success){
    $.ajax({
        type: "POST",
        url: url,
        async: way ,
        contentType: contentType,
        dateType: "json",
        data : data ,
        success: function(msg){
            success(msg);
        }
    });
}
/**
 * 通用GET请求函数(有参) 返回参数json
 * @param way 同步 false 异步 true
 * @param url 请求地址
 * @param data 请求参数
 * @param success 回调函数
 */
function ajaxParamGET(way , url , params , success){
    $.ajax({
        type: "GET",
        url: url,
        async: way ,
        dateType: "json",
        data : params ,
        beforeSend: function(request) {
            
        },
        success: function(msg){
            success($.parseJSON(msg));
        }
    });
}

/**
 * 通用GET请求函数(无参) 返回参数json
 * @param way 同步 false 异步 true
 * @param url 请求地址
 * @param success 回调函数
 */
function ajaxNotParamGET(way , url , success){
    $.ajax({
        type: "GET",
        url: url,
        async: way ,
        dateType: "json",
        beforeSend: function(request) {
            
        },
        success: function(msg){
            success($.parseJSON(msg));
        }
    });
}
/**
 * 通用POST请求函数(无参) 返回参数json
 * @param way 同步 false 异步 true
 * @param url 请求地址
 * @param success 回调函数
 */
function ajaxNotParamPOST(way , url , success){
    $.ajax({
        type: "POST",
        url: url,
        async: way ,
        dateType: "json",
        beforeSend: function(request) {
            
        },
        success: function(msg){
            success(msg);
        }
    });
}
```