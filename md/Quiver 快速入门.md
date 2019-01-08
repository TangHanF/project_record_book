# Quiver 快速入门

Quiver快速入门
==========

Quiver 是一个程序员专用的记事本应用，可轻松混合文本、代码、Markdown、LaTeX 到一个记事本中。提供强大的代码编辑功能，以及对 Markdown 和 LaTeX 的编辑和即时预览，提供全文搜索功能。

[](https://github.com/HappenApps/Quiver/wiki/Quiver%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8#1---%E5%BC%80%E5%A7%8B%E4%BD%BF%E7%94%A8)1 - 开始使用
-----------------------------------------------------------------------------------------------------------------------------------------

欢迎使用 Quiver！本教程将帮助您入门。

如果你想立即开始使用 Quiver，只用记住一件事：

Quiver 的笔记是由单元格组成。

单元格可以是一段文本，代码，Markdown，或者LaTeX。一个笔记中可以混排不同类型的单元格，甚至可以给不同的代码单元格设置不同的语言。

新建一https://github.com/HappenApps/Quiver/wiki/Quiver%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8\#%E6%96%87%E6%9C%AC%E5%8D%95%E5%85%83%E6%A0%BC个笔记，开始键入你想写的内容。按"shift + 返回"(⇧⏎) 创建一个新的单元格，使用退格键合并单元格。只要知道这些你就可以开始使用 Quiver 了。

但如果你想要了解更多，请继续阅读。

[](https://github.com/HappenApps/Quiver/wiki/Quiver%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8#2---%E5%8D%95%E5%85%83%E6%A0%BC%E7%B1%BB%E5%9E%8B)2 - 单元格类型
---------------------------------------------------------------------------------------------------------------------------------------------------

目前支持五种单元格类型:

1. 文本单元格：支持富文本编辑，图像和链接。
2. 代码单元格：使用 ACE 代码编辑器，语法高亮显示支持 120+ 语言、 20 + 主题、 支持自动缩进、 代码自动补全，功能多多。
3. Markdown 单元格：支持自定义 CSS，即时预览。
4. LaTeX 单元格： 使用 MathJax 来排版笔记中的数学公式。
5. 图表单元格：使用纯文本创建序列图和流程图。

### [](https://github.com/HappenApps/Quiver/wiki/Quiver%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8#%E6%96%87%E6%9C%AC%E5%8D%95%E5%85%83%E6%A0%BC)文本单元格

![text-cell-style](https://ws3.sinaimg.cn/large/006tNc79ly1fyz4lfbwkmj30gl02bq39.jpg)

你可以使用工具栏按钮或键盘快捷方式更改文本格式。在"格式"菜单下可以找到所有格式设置选项和键盘快捷方式。

### [](https://github.com/HappenApps/Quiver/wiki/Quiver%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8#%E4%BB%A3%E7%A0%81%E5%8D%95%E5%85%83%E6%A0%BC)代码单元格

这是一个代码单元格设置为 JavaScript 模式:

    void hello()
    {
        console.log("Hello World!");
    }

这是一个代码单元格设置为 CoffeeScript 模式:

    hello = -\> console.log 'Hello World!'

代码单元格支持 120 + 语言的语法高亮、 20 + 主题、 自动缩进，代码折叠，多个游标和选择、 代码自动补全、tab 触发，Vim/Emacs 键绑定等。在 Ace 代码编辑器的网站 [http://ace.c9.io](http://ace.c9.io/) 上，你可以读到更多 Ace 代码编辑器的功能。

### [](https://github.com/HappenApps/Quiver/wiki/Quiver%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8#markdown-%E5%8D%95%E5%85%83%E6%A0%BC)Markdown 单元格

Markdown 单元格支持标准 Markdown 语法以及 GitHub Flavored Markdown (GFM)。

#### [](https://github.com/HappenApps/Quiver/wiki/Quiver%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8#%E5%9F%BA%E6%9C%AC%E6%A0%BC%E5%BC%8F)基本格式

    \# 标题 1
    \#\# 标题 2
    \#\#\# 标题 3
    \#\#\#\# 标题 4
    \#\#\#\#\# 标题 5
    \#\#\#\#\#\# 标题 6

    ---

    \*斜体\*, \*\*粗体\*\*, ~~划除~~

    `行内代码`

#### [](https://github.com/HappenApps/Quiver/wiki/Quiver%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8#%E5%88%97%E8%A1%A8)列表

    1. 第一个有序的列表项
    2. 另一个列表项
      \* 无序的子列表
    1. 实际数字不重要
      1. 有序的子列表
    4. 另一个列表项

#### [](https://github.com/HappenApps/Quiver/wiki/Quiver%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8#%E5%BC%95%E7%94%A8)引用

    \> 和平不能靠武力; 它只可以通过理解来实现。

#### [](https://github.com/HappenApps/Quiver/wiki/Quiver%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8#%E9%93%BE%E6%8E%A5)链接

    [行内链接](https://www.google.com)
    http://example.com

你可以创建链接到另一个笔记：(“笔记”菜单 -\> 复制笔记链接 -\> 粘贴)

    [01 - Getting Started](quiver:///notes/D2A1CC36-CC97-4701-A895-EFC98EF47026)

#### [](https://github.com/HappenApps/Quiver/wiki/Quiver%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8#%E8%A1%A8%E6%A0%BC)表格

    | Tables        | Are           | Cool  |
    | ------------- |:-------------:| -----:|
    | col 3 is      | right-aligned | $1600 |
    | col 2 is      | centered      |   $12 |
    | zebra stripes | are neat      |    $1 |

#### [](https://github.com/HappenApps/Quiver/wiki/Quiver%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8#gfm-%E4%BB%BB%E5%8A%A1%E5%88%97%E8%A1%A8)GFM 任务列表

    - [ ] a task list item
    - [ ] list syntax required
    - [ ] normal \*\*formatting\*\*, @mentions, \#1234 refs
    - [ ] incomplete
    - [x] completed

#### [](https://github.com/HappenApps/Quiver/wiki/Quiver%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8#%E8%A1%8C%E5%86%85-latex)行内 LaTeX

您可以在 Markdown 单元格中使用行内 LaTeX，例如，`$x^2$`。

### [](https://github.com/HappenApps/Quiver/wiki/Quiver%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8#latex-%E5%8D%95%E5%85%83%E6%A0%BC)LaTeX 单元格

使用 LaTeX 单元格可以很容易地排版数学公式。例如，

    \\begin{align}
      \\nabla \\times \\vec{\\mathbf{B}} -\\, \\frac1c\\, \\frac{\\partial\\vec{\\mathbf{E}}}{\\partial t} & = \\frac{4\\pi}{c}\\vec{\\mathbf{j}} \\\\
      \\nabla \\cdot \\vec{\\mathbf{E}} & = 4 \\pi \\rho \\\\
      \\nabla \\times \\vec{\\mathbf{E}}\\, +\\, \\frac1c\\, \\frac{\\partial\\vec{\\mathbf{B}}}{\\partial t} & = \\vec{\\mathbf{0}} \\\\
      \\nabla \\cdot \\vec{\\mathbf{B}} & = 0
    \\end{align}

预览如下：

![latex-cell-rendered](https://ws1.sinaimg.cn/large/006tNc79ly1fyz4lfmzajj30gc0570sz.jpg)

也可以在行内使用 LaTeX，例如，`$x^2$`。

您还可以在设置中添加自定义宏。添加的自定义宏可以在所有的 LaTeX 单元格中使用。

### [](https://github.com/HappenApps/Quiver/wiki/Quiver%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8#%E5%9B%BE%E8%A1%A8%E5%8D%95%E5%85%83%E6%A0%BC)图表单元格

使用图标单元格可以很方便地创建序列图和流程图。

请参照这里的语法：

* 序列图: <http://bramp.github.io/js-sequence-diagrams/>
* 流程图: <http://flowchart.js.org/>

序列图示例:

```

1. Title: Here is a title
2. A-\>B: Normal line
3. B--\>C: Dashed line
4. C-\>\>D: Open arrow
5. D--\>\>A: Dashed open arrow

```

预览如下：

![sequence-diagram-rendered](https://ws2.sinaimg.cn/large/006tNc79ly1fyz4lgolixj30dj09a74p.jpg)

流程图示例:

```

1. st=\>start: Start:\>http://www.google.com[blank]
2. e=\>end:\>http://www.google.com
3. op1=\>operation: My Operation
4. sub1=\>subroutine: My Subroutine
5. cond=\>condition: Yes
6. or No?:\>http://www.google.com
7. io=\>inputoutput: catch something...
8. 
9. st-\>op1-\>cond
10. cond(yes)-\>io-\>e
11. cond(no)-\>sub1(right)-\>op1

```

预览如下：

![flowchart-rendered](https://ws4.sinaimg.cn/large/006tNc79ly1fyz4lhj3wuj30d10fi74y.jpg)

[](https://github.com/HappenApps/Quiver/wiki/Quiver%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8#3---%E5%8D%95%E5%85%83%E6%A0%BC%E6%93%8D%E4%BD%9C)3 - 单元格操作
---------------------------------------------------------------------------------------------------------------------------------------------------

单元格操作很容易上手，但其实功能强大。

其中最重要的一个操作你已经学会了：按"shift + 返回"(⇧⏎) 来创建一个新的单元格。默认情况下新建的单元格是一个文本单元格，但你可以轻松地将其转换为其它类型的单元格。

转换单元格类型有好几种方法：你可以使用工具栏上的下拉菜单，或者键盘快捷方式 (⌥⌘1 转换为文本单元格，⌥⌘2 转换为代码单元格，⌥⌘3 转换为 Markdown 单元格，⌥⌘4 转换为 LaTeX 单元格，⌥⌘5 转换为图表单元格)。这些快捷方式可以在“单元格”菜单下找到。

另一个重要的操作是如何合并两个单元格。只需将光标放在第二个单元格的开头，然后按回退键。请注意不同类型的单元格不能合并。

有时候你可能想在当前光标位置添加一个新的单元格。你可以用“单元格”菜单下的 "New Cell At Cursor" (⇧⌘I) 菜单项实现。

你还可以剪切、复制或粘贴单元格，拆分单元格，向上或向下移动单元格。所有这些单元格操作和其相应的键盘快捷方式可以在“单元格”菜单下找到。

[](https://github.com/HappenApps/Quiver/wiki/Quiver%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8#4---%E5%9B%BE%E5%83%8F-%E6%96%87%E4%BB%B6%E5%92%8C%E9%93%BE%E6%8E%A5)4 - 图像、 文件和链接
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------

你可以拖拽或粘贴图像到文本单元格中。你也可以使用工具栏中的“插入图像”按钮 ![](https://ws1.sinaimg.cn/large/006tNc79ly1fyz4lhysxwj300m00l0h1.jpg)。

![](https://ws4.sinaimg.cn/large/006tNc79ly1fyz4lig11cj303k03kdg0.jpg)

插入的图像自动复制到当前笔记的资源文件夹中，因此即使原始图像被删除，笔记中的图像也照样可以使用。

如果将一个文件 (例如，PDF、 zip、 源文件) 拖拽到文本单元格中，你可以选择将它复制到资源文件夹，或者保存为链接。您也可以使用工具栏中的“附加文件”按钮。

如果粘贴的文本中有 URL，Quiver 会自动将其转换为链接，比如 [http://www.apple.com](http://www.apple.com/)。

另一个有用的功能是笔记链接。您可以使用“笔记”菜单下的菜单项"复制笔记链接"(⌃⌥⌘C)来复制当前笔记的链接，例如：

[02 - Cell Types](https://github.com/HappenApps/Quiver/wiki/quiver:///notes/9686AA1A-A5E9-41FF-9260-C3E0D0E9D4CB)

[03 - Cell Operations](https://github.com/HappenApps/Quiver/wiki/quiver:///notes/EDFC03DD-4E78-4405-A560-4A902FCE4312)

这样你可以很方便地交叉引用你的笔记。不同笔记本中的笔记也可以相互链接。

笔记链接在 Markdown 单元格中也可以使用。在“笔记”菜单下使用菜单项“复制笔记链接”(⌃⌥⌘C)，然后粘贴到 Markdown 单元格。例如：

    [02 - Cell Types](quiver:///notes/9686AA1A-A5E9-41FF-9260-C3E0D0E9D4CB)

它在预览或演示模式中会变成笔记链接。

[](https://github.com/HappenApps/Quiver/wiki/Quiver%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8#5---%E9%A2%84%E8%A7%88%E5%92%8C%E6%BC%94%E7%A4%BA%E6%A8%A1%E5%BC%8F)5 - 预览和演示模式
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------

### [](https://github.com/HappenApps/Quiver/wiki/Quiver%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8#%E5%8D%B3%E6%97%B6%E9%A2%84%E8%A7%88)即时预览

Quiver 支持 Markdown 和 LaTeX 的即时预览。你可以切换到同时显示编辑器和预览的双栏模式 (⌘6)。

你也可以双击列表中的笔记在新窗口打开，然后切换到双栏模式。例如：

![](https://ws2.sinaimg.cn/large/006tNc79ly1fyz4lj13o9j30ts0kftbs.jpg)

当您在编辑器中进行更改时，预览会实时更新。

默认情况下，编辑器和预览之间会同步滚动。但您可以在视图菜单中关闭此功能。

### [](https://github.com/HappenApps/Quiver/wiki/Quiver%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8#%E6%BC%94%E7%A4%BA%E6%A8%A1%E5%BC%8F)演示模式

Quiver 还支持全屏幕演示模式。您可以从“笔记”菜单中选择“启动演示”(⌃⌥⌘P)，或单击笔记右下角的“演示”按钮。

演示模式非常适合教室使用、 团队会议、 演示或者自己复习笔记。

![](https://ws2.sinaimg.cn/large/006tNc79ly1fyz4ljhz67j30m80dw3yx.jpg)

在演示模式中，你可以使用左/右箭头键来移动到列表中的上个/下个笔记。

[](https://github.com/HappenApps/Quiver/wiki/Quiver%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8#6---%E5%85%A8%E6%96%87%E6%90%9C%E7%B4%A2)6 - 全文搜索
-----------------------------------------------------------------------------------------------------------------------------------------

笔记再好，不能快速找到也没用。Quiver 的全文搜索是基于苹果操作系统中 Spotlight 使用的底层工具：Search Kit。因此 Quiver 可以瞬间搜索数以千计的笔记。

若要搜索所有的笔记，请单击右上角的搜索按钮。你可以通过关键字、 标题或 \#标签 搜索。

你也可以在一个笔记本中搜索。首先打开笔记本，在列表底部的搜索框中输入关键字或 \#标签。这也是全文搜索，不过只显示当前笔记本中的搜索结果。

如果你想在一个笔记中查找关键词，请使用 ⌘F。你会看到一个查找工具栏：

![](https://ws3.sinaimg.cn/large/006tNc79ly1fyz4ljx2w4j30lx00zt8h.jpg)

使用 ⌘G (或回车键) 跳转到下一个搜索结果。用 ⇧⌘G （或 shift + 回车）向上查找。

查找工具栏在编辑器和预览中都可以使用。

[](https://github.com/HappenApps/Quiver/wiki/Quiver%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8#7---%E6%A0%87%E7%AD%BE)7 - 标签
---------------------------------------------------------------------------------------------------------------------

Quiver 支持给笔记加标签。这是又一种整理笔记的方式。

![](https://ws4.sinaimg.cn/large/006tNc79ly1fyz4lkbjnzj308l01n744.jpg)

你可以按标签分类来浏览笔记：

![](https://ws1.sinaimg.cn/large/006tNc79ly1fyz4lksiodj305v07vdfv.jpg)

如果你从列表中同时选择多个笔记，你可以同时给他们添加或删除标签。

![](https://ws4.sinaimg.cn/large/006tNc79ly1fyz4llaqo5j30bu0a2wej.jpg)

[](https://github.com/HappenApps/Quiver/wiki/Quiver%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8#8---%E4%BA%91%E5%90%8C%E6%AD%A5)8 - 云同步
-------------------------------------------------------------------------------------------------------------------------------

Quiver 支持使用任意基于文件的云盘同步，比如 Dropbox，iCloud Drive，Google Drive。

要使用云同步，在设置中打开同步页：

![](https://ws3.sinaimg.cn/large/006tNc79ly1fyz4lm8a3nj30iq09o756.jpg)

将你的 Quiver 库文件转移到 Dropbox 或其他云盘，然后在另一台电脑上打开库文件。这样两台电脑上的笔记会随时同步。

[](https://github.com/HappenApps/Quiver/wiki/Quiver%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8#9---%E5%9B%A2%E9%98%9F%E5%8D%8F%E4%BD%9C)9 - 团队协作
-----------------------------------------------------------------------------------------------------------------------------------------

Quiver 支持好几种团队协作的方法。

### [](https://github.com/HappenApps/Quiver/wiki/Quiver%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8#%E5%85%B1%E4%BA%AB%E7%AC%94%E8%AE%B0%E6%9C%AC)共享笔记本

共享笔记本是保存在云盘上的一个笔记本。任何基于文件的云盘都可以，比如 Dropbox，iCloud Drive，Google Drive。你可以创建一个新的共享笔记本，或者将一个本地笔记本移到云盘上转换成共享笔记本。另一个团队成员可以在另一台电脑上打开共享笔记本，进行编辑。共享笔记本中的笔记会自动同步。这是一个很好的创建团队共享知识库的方法。

多个用户可以同时对同一个共享笔记本进行操作，比如添加或删除笔记，添加或删除标签。这些操作会自动同步。但是，请注意如果两个团队成员同时修改同一个笔记，Quiver 不会自动解决冲突，而是提醒其中一方笔记已被修改，需要刷新。

### [](https://github.com/HappenApps/Quiver/wiki/Quiver%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8#%E7%89%88%E6%9C%AC%E6%8E%A7%E5%88%B6)版本控制

如果你使用版本控制系统来管理你的代码和文档，建议你也用版本控制系统 （Git， SVN）来管理 Quiver 的笔记。因为 Quiver 的笔记只是普通的 JSON 文本文件，你可以作为文本文件将它们提交到存储库中。

你可以将整个 Quiver 库文件放到版本控制中，或者只放几个笔记本。用版本控制系统管理 Quiver 笔记的一个好处是：如果两个用户同时编辑一个笔记，用版本控制系统可以很方便地解决合并冲突。

[](https://github.com/HappenApps/Quiver/wiki/Quiver%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8#10---%E5%A4%87%E4%BB%BD%E5%92%8C%E6%81%A2%E5%A4%8D)10 - 备份和恢复
-----------------------------------------------------------------------------------------------------------------------------------------------------

对于那些不使用云同步或版本控制的用户，还有一种方式可以保管好您的笔记。

若要备份整个库文件，请在设置中打开备份设置页：

![](https://ws3.sinaimg.cn/large/006tNc79ly1fyz4lnflbgj30iq08tjs5.jpg)

选择“备份”来备份您的所有笔记。如果你想要从以前的备份中还原您的所有笔记，请选择“从备份恢复” 然后选择以前的备份。

[](https://github.com/HappenApps/Quiver/wiki/Quiver%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8#11---%E5%AF%BC%E5%85%A5%E4%B8%8E%E5%AF%BC%E5%87%BA)11 - 导入与导出
-----------------------------------------------------------------------------------------------------------------------------------------------------

Quiver 不会将你的笔记锁住。

Quiver 的笔记本和笔记都保存为普通的 JSON 文本文件。文件格式在此有详细的说明：<https://github.com/HappenApps/Quiver/wiki/Quiver-Data-Format>。

因此你可以放心，你的笔记永远不会无法读取。而且，Quiver 也很容易与你使用的其它工具集成。

Quiver 自带的导出器支持 HTML、 PDF 和 Markdown。你可以导出整个 Quiver 的笔记本为相互链接的 HTML 网页。

导出为 Markdown 时，代码单元格会自动转换为 Markdown 内嵌代码块。这样你可以很方便地将导出的 Markdown 文件上传到 GitHub 或其它使用 Markdown 的平台。

如果你有特殊的导入或导出的需要，你可以很容易地写一个脚本，读取 Quiver 的笔记格式，然后导出成你想要的格式。自定义脚本对于编写编程相关的书籍或教程的用户尤其有用。

几个示例脚本可以在这里找到: <https://github.com/HappenApps/Quiver/wiki/Export-Scripts>。

[](https://github.com/HappenApps/Quiver/wiki/Quiver%E5%BF%AB%E9%80%9F%E5%85%A5%E9%97%A8#12---%E8%AE%BE%E7%BD%AE)12 - 设置
-----------------------------------------------------------------------------------------------------------------------

在常规设置页，您可以更改默认的笔记列表排序、 默认单元格类型等。

![](https://ws3.sinaimg.cn/large/006tNc79ly1fyz4lo1s84j30iq0940tg.jpg)

在主题设置页，您可以管理界面的主题。Quiver 附带了几个设计精美的主题，包括一个浅色主题和一个深色主题。你也可以自己设计主题。

![](https://ws4.sinaimg.cn/large/006tNc79ly1fyz4lol3uej30iq0c5dgq.jpg)

在单元格设置页，您可以显示/隐藏行号，启用代码自动补全、 更改键绑定，创建整个应用程序范围的 LaTeX 自定义宏等。

![](https://ws4.sinaimg.cn/large/006tNc79ly1fyz4lp0fj2j30iq0efmyb.jpg)

在样式设置页，您可以给编辑器、 预览、 演示、 导出的 HTML 或 PDF 设置自定义样式。支持的所有标准的 CSS 规则，如字体大小、 文本颜色、 背景颜色等。

![](https://ws3.sinaimg.cn/large/006tNc79ly1fyz4lph4bcj30iq0ayaaw.jpg)

在快捷方式设置页，您可以设置几个系统键盘快捷方式: 将 Quiver 窗口移前、 创建新笔记，和搜索笔记。

![](https://ws3.sinaimg.cn/large/006tNc79ly1fyz4lpy765j30iq095wfb.jpg)

同步设置页和备份设置页前面已讲过了。

在高级设置页，您可以将您的设置和自定义 CSS 导出成一个 JSON 文件。这样你可以轻松地在另一台电脑上加载同样的设置。

![](https://ws1.sinaimg.cn/large/006tNc79ly1fyz4lr01fej30iq08tjs6.jpg)