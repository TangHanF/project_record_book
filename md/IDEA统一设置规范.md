# IDEA统一设置规范

作者：GuoF

创建日期：2017-12-5

# 一、注释模板

## 1）类注释

![img](https://ws4.sinaimg.cn/large/006tNc79ly1fyxyoc4tvoj30h90comxf.jpg)

设置方法：

![img](https://ws1.sinaimg.cn/large/006tNc79ly1fyxyolr3ylj30tf0fmt9a.jpg)

模板：

**JavaScript**：

> /**
>
> 功能描述：${END}
>
> Created by GuoF on ${DATE}.
>
> */

**Java**：

> /**
>
> *Title: <br>
>
> *Packet:${PACKAGE_NAME}<br>
>
> *Description: <br>
>
> *Author:GuoFu<br>
>
> *Create Date: ${DATE}.<br>
>
> *Modify User: <br>
>
> *Modify Date: <br>
>
> *Modify Description: <br>
>
> */

**注意：**

**1、姓名禁止使用昵称，内部开发，使用真实姓名**

**2、姓名统一使用拼音，防止中文乱码**

## 2）方法注释

设置方法：在方法名上一行输入：“/**”回车，自动生成JavaDoc注释规范，例如：

![img](https://ws2.sinaimg.cn/large/006tNc79ly1fyxyonzj54j30eh05kglh.jpg)

测试将光标定义为方法上，按下键盘Ctrl+Q即可查看该方法的相关描述信息：

![img](https://ws1.sinaimg.cn/large/006tNc79ly1fyxyopkfntj30p109emxh.jpg)

## 3）字段注释

关键字段的注释建议使用块状注释，以便日后生成javadoc文档能自动生成字段注释

![img](https://ws1.sinaimg.cn/large/006tNc79ly1fyxyopsdzhj3088039dfm.jpg)

![img](https://ws1.sinaimg.cn/large/006tNc79ly1fyxyoqv6r9j30dx062jrf.jpg)

# 二、代码模板

合理使用代码模板可以提高开发效率，例如新建一个测试类，一般很多人手动写main方法，其实IDEA内部默认快速生成main方法的提示符为：“psvm”，即当我们输入“psvm”然后按回车即可生成main方法，但是感觉比较别扭，可以修改甚至新增，例如我想输入“main”按回车生成main方法，可以按Ctrl+J，随便找一个代码片段编辑、新增即可：

![img](https://ws1.sinaimg.cn/large/006tNc79ly1fyxyorph5zj30lj07i3yu.jpg)

![img](https://ws3.sinaimg.cn/large/006tNc79ly1fyxyouolh4j30t70l23z7.jpg)

![img](https://ws3.sinaimg.cn/large/006tNc79ly1fyxyow100qj30pk0jtjs3.jpg)

# 三、注释缩进

> IDEA注释的快捷键是Ctrl+/，但是默认注释是行首，一旦注释一多，看起来很别扭，例如：

![img](https://ws1.sinaimg.cn/large/006tNc79ly1fyxyox3p0bj30k60ax74n.jpg)

> 注释符号和被注释代码之间还有一块空隙，不整齐，可进行如下设置：

![img](https://ws4.sinaimg.cn/large/006tNc79ly1fyxyoxthqij30xc0h03zd.jpg)

> 修改后的效果：

![img](https://ws4.sinaimg.cn/large/006tNc79ly1fyxyoya1qmj30ox0emjrw.jpg)

> 这样就会整齐很多
>
> 建议测试完成之后把注释删掉！

**理论上说，不建议保留已经注释掉的代码，既然注释了就没用，如果自己觉得代码可能有用可以加一个TODO表示待优化等**

# 四、代码规范检查插件

![img](https://ws1.sinaimg.cn/large/006tNc79ly1fyxyoz7scdj310w0maabs.jpg)

![img](https://ws4.sinaimg.cn/large/006tNc79ly1fyxyp08snsj30ts0s1tcd.jpg)

打开 File>>Settings >> Plugins >> Browse repositories 输入 Alibaba 搜索 **Alibaba Java Coding Guidelines** 下载安装

![img](https://ws3.sinaimg.cn/large/006tNc79ly1fyxyp19pfzj30cw0q9myb.jpg)

或者：

![img](https://ws1.sinaimg.cn/large/006tNc79ly1fyxyp23uzjj30rh05hgly.jpg)

个人感觉这个插件对于新手开发很有帮助，能从开始就纠正一些不良编码习惯，而且一些提示也是很多老手没注意到的，值得学习一下！

# 五、代码折叠

如果一些逻辑比较复杂，翻起来比较麻烦，建议进行代码折叠，IDEA中代码折叠是：

```
// <editor-fold desc="描述信息"> 
```

​    `要折叠的内容`

```
// </editor-fold>
```

每次写这么多很麻烦，这就用到了上面说的《二、代码模板》

未折叠前的代码：

![img](https://ws1.sinaimg.cn/large/006tNc79ly1fyxyp2hzyyj30q50llt9s.jpg)

折叠后的效果：

![img](https://ws4.sinaimg.cn/large/006tNc79ly1fyxyp3gcksj30zj0ay0t1.jpg)

switch顿时干净！

# 六、IDEA忽略大小写，快速代码提示自动完成（巨实用！）

IDEA有很强大的代码自动完成功能，例如声明变量 ：String str=""; 输入“St”的时候String就已经出来了，但是如果你输入“st”就不会出来，这是因为IDEA默认的代码提示是区分大小写的，有时候这很不方便，解决方式如下：

![img](https://ws2.sinaimg.cn/large/006tNc79ly1fyxyp4lptdj30lq0dlmym.jpg)

设置完成以后就不用考虑大小写问题了，编码效率顿时提升！

# 七、开启自动 import 包的功能

![img](https://ws1.sinaimg.cn/large/006tNc79ly1fyxyp6di60j30yy0jt45a.jpg)

如上图标注 1 和 2 所示，默认 IntelliJ IDEA 是没有开启自动 import 包的功能。勾选标注 1 选项，IntelliJ IDEA 将在我们书写代码的时候自动帮我们优化导入的包，比如自动去掉一些没有用到的包。勾选标注 2 选项，IntelliJ IDEA 将在我们书写代码的时候自动帮我们导入需要用到的包。但是对于那些同名的包，还是需要手动 `Alt + Enter` 进行导入的，IntelliJ IDEA 目前还无法智能到替我们做判断。**设置完成之后代码中的相关jar包会自动导入，很方便**

# 八、鼠标滚轮控制字体缩放设置方法：

![img](https://ws3.sinaimg.cn/large/006tNc79ly1fyxyp77pfcj30pg0jamyt.jpg)

# 九、控制字体大小  

在`File -> Setting -> Editor -> General`下进行设置，如图  选中`Change font size (Zoom) with Ctrl+Mouse wheel`，之后，使用`Ctrl + 鼠标滚轮` 快捷键就可以实时控制代码字体大小显示了，需要注意的是这种设置只对当前正在编辑的文件有效

# 十、放大缩小图片  

在`File -> Setting -> Editor -> Images`下进行设置，如图  ![img](https://ws1.sinaimg.cn/large/006tNc79ly1fyxyp838kuj30n00ja3zx.jpg)选中`Zoom image with mouse wheel (Ctrl+Mouse wheel)`，之后，使用`Ctrl + 鼠标滚轮` 快捷键就可以实时调整正在查看的图片的显示大小

# 十一、IDEA高效快捷键

以下是我使用频率最高的快捷键，可以大大提高工作效率：

**Ctrl+N：查找项目、工程源文件**

**Ctrl+Shit+N：查找所有文件**

以上两个操作，在模糊搜索后空格加上一个数字 会自动打开文档到指定位置，例如：

![img](https://ws1.sinaimg.cn/large/006tNc79ly1fyxyp8n2tej30gb04mjs9.jpg)很强大、实用的功能

快速两下Shift：搜索各类文件

**Ctrl+E：打开最近文件列表**

------

Ctrl+Shit+L：代码格式化

------

Shift+F11：查看已添加的书签

------

Ctrl+G：跳转到指定行号

**Alt+回车**：对相关操作进行更正，例如提示缺少包引用，按下改快捷键即可进行导包操作

例如下面一个例子方法是接口的实现，但是没有就加“override”注解。按下该快捷键：

![img](https://ws3.sinaimg.cn/large/006tNc79ly1fyxyp9j3xej30m206yzls.jpg)

Alt+F7：查找引用。例如查找当前变量在哪些地方赋值和取值

**Shift+F6**：文件名名称、类名重命名

`Command + Shift + Enter` 来快速补全分号

------

Ctrl+Tab：在已打开的tab中进行切换

------

Ctrl+Shift+U：大小写切换

------

Ctrl+F12（Command+F12）

Ctrl+Shift+I（Command+Shift+I）：独立弹窗，一般多用于在不定位类时打开类中内容例如：

![img](https://ws2.sinaimg.cn/large/006tNc79ly1fyxypaktihj319c0cowj0.jpg)

![img](https://ws4.sinaimg.cn/large/006tNc79ly1fyxypbmxaij316s0u0te2.jpg)

# 十二、其它插件

- Key Promote：快捷键提示插件，方便记忆IDEA的快捷键。
- ECTranslate：翻译插件，快捷键（Ctrl+1）

![img](https://ws3.sinaimg.cn/large/006tNc79ly1fyxyperuklj30gg08cgpt.jpg)

# 十三、其它操作

## 建议开启工具栏

![img](https://ws1.sinaimg.cn/large/006tNc79ly1fyxyphy4w8j308w0fyt9s.jpg)

## **IDEA Ctrl+D复制行数据设置**

默认情况IDEA是复制行数据或者已选择的数据，但是这样感觉不太好，我就想复制整行而非包含选择的：![img](https://ws3.sinaimg.cn/large/006tNc79ly1fyxypifiv4j30zy0o1dgj.jpg)

# 十四、自动转换properties配置文件中文Unicode编码问题

![img](https://ws2.sinaimg.cn/large/006tNc79ly1fyxypizymxj30kc04075t.jpg)

设置方式：

![img](https://ws2.sinaimg.cn/large/006tNc79ly1fyxyplyn48j313q0u0tl0.jpg)

**未完，待续...**