# IDEA统一设置规范


作者：GuoF

创建日期：2017-12-5

# <font color='#ff0000'>一、注释模板</font>

## <font color='#ff0000'>1）类注释</font>

![](https://gitee.com/TangHanF/pic/raw/master/Jf6iUH.png)


设置方法：

![](https://gitee.com/TangHanF/pic/raw/master/If9Xsu.png)

模板：

**JavaScript头注释**：

``` javascript
/**
功能描述：${END}
Created by 你的姓名全拼 on ${DATE}.
*/
```

**Java头注释**：

``` javascript
/**
* Title: 
* Packet:${PACKAGE_NAME}
* Description: 
* Author:你的姓名，建议姓名全拼。不要使用中文，避免乱码
* Create Date: ${DATE}.
* Modify User: 
* Modify Date: 
* Modify Description: 
*/
```

**注意：**

- **1、姓名禁止使用昵称，内部开发，使用真实姓名**

- **2、姓名统一使用拼音，防止中文乱码**

## <font color='#ff0000'>2）方法注释</font>

设置方法：在方法名上一行输入：`/**` 回车，自动生成JavaDoc注释规范，例如：

![](https://gitee.com/TangHanF/pic/raw/master/P8mhnV.png)

测试将光标定义为方法上，按下键盘Ctrl+Q即可查看该方法的相关描述信息：

![](https://gitee.com/TangHanF/pic/raw/master/g49V8d.png)

## <font color='#ff0000'>3）字段注释</font>

关键字段的注释建议使用块状注释,快捷键同样是输入：`/**` 回车，以便日后生成javadoc文档能自动生成字段注释

![](https://gitee.com/TangHanF/pic/raw/master/XaEGcA.png)

# 二、代码模板

合理使用代码模板可以提高开发效率，例如新建一个测试类，一般很多人手动写main方法，其实IDEA内部默认快速生成main方法的提示符为：“psvm”，即当我们输入“psvm”然后按回车即可生成main方法，但是感觉比较别扭，可以修改甚至新增，例如我想输入“main”按回车生成main方法，可以按Ctrl+J，随便找一个代码片段编辑、新增即可：

![](https://gitee.com/TangHanF/pic/raw/master/lAK1hR.png)

![](https://gitee.com/TangHanF/pic/raw/master/URzxht.png)

![](https://gitee.com/TangHanF/pic/raw/master/iXyVMr.png)

# <font color='#ff0000'>三、注释缩进</font>

> IDEA注释的快捷键是 `Ctrl+/`，但是默认注释是行首，一旦注释一多，看起来很别扭，例如：

![](https://gitee.com/TangHanF/pic/raw/master/x9bKoA.png)

> 注释符号和被注释代码之间还有一块空隙，不整齐，可进行如下设置：

![](https://gitee.com/TangHanF/pic/raw/master/hHYHPh.png)

> 修改后的效果：

![](https://gitee.com/TangHanF/pic/raw/master/8nxWnp.png)

> 这样就会整齐很多
>
> 建议测试完成之后把注释删掉！

**理论上说，不建议保留已经注释掉的代码，既然注释了就没用，如果自己觉得代码可能有用可以加一个TODO表示待优化等**

# <font color='#ff0000'>四、代码规范检查插件</font>

## Alibaba Java Coding Guidelines插件

![](https://gitee.com/TangHanF/pic/raw/master/NpPtfA.png)

![](https://gitee.com/TangHanF/pic/raw/master/fq6lWJ.png)

打开 File>>Settings >> Plugins >> Browse repositories 输入 Alibaba 搜索  `Alibaba Java Coding Guidelines`  下载安装

<img src="https://gitee.com/TangHanF/pic/raw/master/9HoH90.png" style="zoom:50%;" />

或者：

![](https://gitee.com/TangHanF/pic/raw/master/LAFdF8.png)

个人感觉这个插件对于新手开发很有帮助，能从开始就纠正一些不良编码习惯，而且一些提示也是很多老手没注意到的，值得学习一下！

## FindBugs-IDEA插件

安装方法同上，在IDEA插件市场搜索`FindBugs`即可。

效果图：

![](https://gitee.com/TangHanF/pic/raw/master/PuonBT.png)

## Joker插件

## Bootstrap 4

# 五、代码折叠

如果一些逻辑比较复杂，翻起来比较麻烦，建议进行代码折叠，IDEA中代码折叠是：

```java
// <editor-fold desc="描述信息"> 
// 要折叠的内容
// </editor-fold>
```

每次写这么多很麻烦，这就用到了上面说的《二、代码模板》

未折叠前的代码：

![](https://gitee.com/TangHanF/pic/raw/master/wqwhQd.png)

折叠后的效果：

![](https://gitee.com/TangHanF/pic/raw/master/jSqEWG.png)

switch顿时干净！

# <font color='#ff0000'>六、IDEA忽略大小写，快速代码提示自动完成（巨实用！）</font>

IDEA有很强大的代码自动完成功能，例如声明变量 ：String str=""; 输入“St”的时候String就已经出来了，但是如果你输入“st”就不会出来，这是因为IDEA默认的代码提示是区分大小写的，有时候这很不方便，解决方式如下：

![](https://gitee.com/TangHanF/pic/raw/master/NQkoIx.png)

设置完成以后就不用考虑大小写问题了，编码效率顿时提升！

2018之后的版本有所改动
![](https://gitee.com/TangHanF/pic/raw/master/Nd8fBh.png)

# 七、开启自动 import 包的功能

![](https://gitee.com/TangHanF/pic/raw/master/ta4Czf.png)

如上图标注 1 和 2 所示，默认 IntelliJ IDEA 是没有开启自动 import 包的功能。勾选标注 1 选项，IntelliJ IDEA 将在我们书写代码的时候自动帮我们优化导入的包，比如自动去掉一些没有用到的包。勾选标注 2 选项，IntelliJ IDEA 将在我们书写代码的时候自动帮我们导入需要用到的包。但是对于那些同名的包，还是需要手动 `Alt + Enter` 进行导入的，IntelliJ IDEA 目前还无法智能到替我们做判断。**设置完成之后代码中的相关jar包会自动导入，很方便**

# 八、鼠标滚轮控制字体缩放设置方法

![](https://gitee.com/TangHanF/pic/raw/master/WdG6cH.png)

# 九、控制字体大小  

在`File -> Setting -> Editor -> General`下进行设置，如图  选中`Change font size (Zoom) with Ctrl+Mouse wheel`，之后，使用`Ctrl + 鼠标滚轮` 快捷键就可以实时控制代码字体大小显示了，需要注意的是这种设置只对当前正在编辑的文件有效

# 十、放大缩小图片  

在`File -> Setting -> Editor -> Images`下进行设置，如图  

![](https://gitee.com/TangHanF/pic/raw/master/nnoFis.png)

选中`Zoom image with mouse wheel (Ctrl+Mouse wheel)`，之后，使用`Ctrl + 鼠标滚轮` 快捷键就可以实时调整正在查看的图片的显示大小

# 十一、IDEA高效快捷键

以下是我使用频率最高的快捷键，可以大大提高工作效率：

**Ctrl+N：查找项目、工程源文件**

**Ctrl+Shit+N：查找所有文件**

以上两个操作，在模糊搜索后空格加上一个数字 会自动打开文档到指定位置，例如：

![](https://gitee.com/TangHanF/pic/raw/master/FEOD56.png)很强大、实用的功能

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

![](https://gitee.com/TangHanF/pic/raw/master/bNJo5j.png)

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

![](https://gitee.com/TangHanF/pic/raw/master/tImYLp.png)



# 十二、其它插件

- Key Promote：快捷键提示插件，方便记忆IDEA的快捷键。
- ECTranslate：翻译插件，快捷键（Ctrl+i）

<img src="https://gitee.com/TangHanF/pic/raw/master/8GPdCW.png" style="zoom:67%;" />

# 十三、其它操作

## 建议开启工具栏

![](https://gitee.com/TangHanF/pic/raw/master/hDUeBK.png)

## IDEA Ctrl+D复制行数据设置

默认情况IDEA是复制行数据或者已选择的数据，但是这样感觉不太好，我就想复制整行而非包含选择的：![](https://gitee.com/TangHanF/pic/raw/master/4D1tL4.png)

# <font color='#ff0000'>十四、自动转换properties配置文件中文Unicode编码问题</font>

![](https://gitee.com/TangHanF/pic/raw/master/EDBq60.png)

设置方式：

![](https://gitee.com/TangHanF/pic/raw/master/IqY39M.png)



# <font color='#ff0000'>十五、及时清理无用的import</font>

> 在一个类中可能存在不必要的import，这时要及时清理。如果未进行清理就会导致本来就没有用的相关类或者jar包删除后，原来import的地方会报错，在开发环境下还好说，IDEA编译时候就会报错，但是在生产环境下如果删除没用的类或者jar包就会存在问题。
>
> **快捷键:**
>
> - Windows版IDEA：`Ctrl+Alt+O`
>
> - MacOS版IDEA：`Ctrl+Commond+O`

> Tips:
>
> 	可在项目根目录上执行以上快捷键，已对整个项目的import进行优化



# <font color='#ff0000'>十六、统一编码设置</font>

> 目前存在的问题就是编码设置不统一，有的项目使用GBK，有的项目使用UTF8。这会导致两个直观的问题：
>
> - 乱码情况的出现
>
>   别人在导入你的项目之后可能会出现乱码的情况。有时候单独设置某个文件的编码类型解决了乱码问题，但是和IDEA全局设置的编码不一致，导致编译的时候都会报错。
>
> - 潜在的安全隐患
>
>   之前遇到过一个问题就是发送的报文在本地控制台输出的日志正常，而且报文从日志来看确实没问题，凡是服务端却一直返回错误，由于当时服务端未提供技术支持，在尝试了很多次解决方式之后最后想到了编码问题。我们用的编码是utf8，服务端是GBK，导致两端不一致，在报文中出现的中文处理乱码。
>
> **因此，在存在中文的情况下，编码问题必须得到重视。而且因为编码导致的BUG往往排查起来会比较麻烦，很少去考虑到这点，浪费大量时间**。
>
> **编码设置原则**：
>
> - 项目搭建前就要确定好编码类型
> - 代码中设置编码不要出现以下情况:
>   - new String(byte[]参数)
>   - "".getBytes()
>
> 合理的应该是：
>
> ![](https://gitee.com/TangHanF/pic/raw/master/z9XHHp.png)

## IDEA编码设置

![](https://gitee.com/TangHanF/pic/raw/master/lBgHse.png)

# 十七、善用TODO

在开发过程中善用 "//TODO" 待办事项，以便后续检查，同时也方便本人及其他项目成员快速定位。
例如，测试环境为了方便测试不检查token有效性，但是生产环境必须要检查，如果类似的情况比较多，那么到了发版时肯定会有遗漏的开关没有打开，如果在相关开关代码位置加上“//TODO 提示....”，那么发版时直接用IDEA查看一下所有TODO即可，防止遗漏

# 十八、修改IDEA内存大小

![](https://gitee.com/TangHanF/pic/raw/master/XES3Rw.png)

![](https://gitee.com/TangHanF/pic/raw/master/PY0K2b.png)



**未完，待续...**