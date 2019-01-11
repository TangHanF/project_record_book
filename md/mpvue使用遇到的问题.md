# mpvue使用遇到的问题

# 坑一：eslint连vue和js后缀文件都有严格校验

build目录的webpack.base.conf.js把器rule注释掉。
```json
  // {

      //   test: /\.(js|vue)$/,

      //   loader: 'eslint-loader',

      //   enforce: 'pre',

	//   include: [resolve('src'), resolve('test')],

      //   options: {

      //     formatter: require('eslint-friendly-formatter')

      //   }

      // },

```



# 坑二.`Cannot assign to read only property 'exports' of object '#<Object>'` 编译报错

这是因为引用第三方插件的时候,带入了`module.exports`的写法,`webpack可以使用require和export ，但是不能混合使用import 和module.exports`,你需要做的是更新根目录下的`.babelrc`文件配置

[vue引入插件Cannot assign to read only property 'exports' of object](https://link.juejin.im/?target=https%3A%2F%2Fblog.csdn.net%2Fu013034736%2Farticle%2Fdetails%2F70174425)

```
{
    "presets": [
        ["env", {
            "modules": false,
            "targets": {
                "browsers": ["> 1%", "last 2 versions", "not ie <= 8"]
            }
        }],
        "stage-2"
    ],
    "plugins": [
        ["transform-runtime", {
            "polyfill": false,
            "regenerator": true
        }]
    ],
    "env": {
        "test": {
            "presets": ["env", "stage-2"],
            "plugins": ["istanbul"]
        }
    }
}
```

