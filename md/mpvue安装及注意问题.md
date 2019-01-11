# mpvue安装及注意的问题

## 1.安装前必要的开发环境、

1）node.js
​现在，前端工具链基本都依赖Node.js，所以请率先安装它吧。

[下载地址](https://nodejs.org/en/download/)

安装完成后，打开你的命令行输入如下命令，验证安装是否成功：

```shell
node --version
//成功的话输出类似：v10.6.0

npm --version
//成功的话输出类似：6.1.0
```



然后，我们需要执行以下命令，将npm的下载源切换到国内淘宝的镜像，以提高下载时的速度和成功率：

```
npm set registry https://registry.npm.taobao.org/
```



2）vue-cli
**vue-cli**是一个vue专用的项目脚手架工具，可以用于方便的创建vue项目骨架代码，包括我们要讲到的mpvue的项目代码。我们可以通过安装node.js后里面包含的npm工具来安装vue-cli，在命令行输入如下命令：

```
npm install vue-cli -g
```



安装完成后，输入如下命令进行验证：

```
vue -V

// 成功的话会输出如下内容：
2.9.6
```

3）微信开发者工具
这个工具是开发、调试和模拟运行微信小程序的最核心的工具了，所以必须安装。

[下载地址：](https://developers.weixin.qq.com/miniprogram/dev/devtools/download.html)

4）安装开发编程工具如：Visual Studio Code 、Sublime Text、WebStorm等

------

## 2.mpvue安装及项目创建

1）mpvue安装

在任意文件夹下打开CMD控制面板执行以下命令

```
# 创建一个基于 mpvue-quickstart 模板的新项目
$ vue init mpvue/mpvue-quickstart my-project//可以根据自己的喜好起名字
```

命令行将一步步的引导我们选择或填写项目的配置信息，如果你还不太明白这些内容的含义，可以先直接全部按回车：

```
? Project name //可以默认也可以输入新的
? wxmp appid touristappid //输入小程序appid
? Project description A Mpvue project
? Author kevinzhang <kevin.zhang@moredist.com>
? Vue build runtime
? Use Vuex? Yes
? Use ESLint to lint your code? //可以选择NO，后面检查挺讨厌的
? Pick an ESLint preset Standard
? 小程序测试，敬请关注最新微信开发者工具的“测试报告”功能 

   vue-cli · Generated "my-project".

   To get started:
   
     cd firstapp
     npm install
     npm run dev


```

上面过程vue-cli主要是先从远程的代码仓库中下载了一份注册名为`mpvue/mpvue-quickstart`的模板代码，然后根据开发者在命令行提示过程中输入的信息，生成一份经过配置后的代码。

这份代码暂时还运行不起来，因为它还缺少依赖的库，我们需要执行以下命令进行依赖库的安装：

```
cd my-project
npm install
```

等几分钟执行完成之后你可以看到该目录下多出了一个node_modules目录。

然后，执行命令让这个代码运行起来，进入开发模式：

```
# 启动项目
npm run dev
# 重建项目
npm run build
```



成功运行后，这个项目代码就进入开发模式，一旦有源代码发生修改，就会触发自动编译。因为mpvue使用的是Vue + HTML Web的开发方式开发小程序，它最终还是需要被转换成小程序的代码才可以在小程序环境运行，所以这里的自动编译的目的就是要把Web代码编译成小程序代码。编译后的代码会在`dist`目录下：

![](http://pl3tgqmrn.bkt.clouddn.com/image/xiaochengxu/xiaochengxml.png)



## 3.在小程序工具上引入项目

1）**打开微信开发者工具，选择新增项目**：

![](http://pl3tgqmrn.bkt.clouddn.com/image/xiaochengxu/xcxcj1.png)



2）**填写项目信息:**

![](http://pl3tgqmrn.bkt.clouddn.com/image/xiaochengxu/xcxcj2.png)





3）**进入小程序，在左边显示运行结果：**

![](http://pl3tgqmrn.bkt.clouddn.com/image/xiaochengxu/xcxcj3.png)



4）**小程序有可能用到的设置：**

![](http://pl3tgqmrn.bkt.clouddn.com/image/xiaochengxu/xcxcj4.png)

5）**常见错误及解决方案：**

[网友总结](https://www.jianshu.com/p/4ee222b64f58)

> 1.“未找到入口 app.json 文件，或者文件读取失败，请检查后重新编译。”
>
> ​     项目根目录下找到project.config.json
>
> ​     打开修改参数"miniprogramRoot": "dist/wx/", //当前项目下dist目录具体小程序路径
>
> 

## 小结：

本文先简要介绍一下使用mpvue开发小程序的前期准备，在后面的将一步步讲解mpvue的详细用法。