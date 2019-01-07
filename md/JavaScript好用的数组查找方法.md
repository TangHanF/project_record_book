# JavaScript 好用的数组查找方法

## 代码（部分ES6语法）

```javascript
/**
 * 
 * 查找数组，返回匹配到的第一个index
 * 
 * @param array 被查找的数组
 * @param feature 查找特征 或者为一个具体值，用于匹配数组遍历的值，或者为一个对象，表明所有希望被匹配的key-value
 * @param or boolean 希望命中feature全部特征或者只需命中一个特征，默认true
 * 
 * @return 数组下标  查找不到返回-1
 */
function findArray(array, feature, all = true) {
    for (let index in array) {
        let cur = array[index];
        if (feature instanceof Object) {
            let allRight = true;
            for (let key in feature) {
                let value = feature[key];
                if (cur[key] == value && !all) return index;
                if (all && cur[key] != value) {
                    allRight = false;
                    break;
                }
            }
            if (allRight) return index;
        } else {
            if (cur == feature) {
                return index;
            }
        }
    }
    return -1;
}
```

## 调用示例

```javascript
//简单值数组
var arr = [0, 1, 2, 3, 4, 5];
var index = findArray(arr, 5);

//对象数组
var arr = [{
    id : '1',
    name : 'cmx',
    age : 23
},{
    id : '2',
    name : '习大大',
    age : 60
}];

//单个特征查找
var index = findArray(arr, {id: '1'});

//多个特征全满足查找
var index = findArray(arr, {id: '1', name: 'cmx'});

//多个特征单个满足查找（只需满足其中一个）
var index = findArray(arr, {id: '1', name: '习大大'}, false
```