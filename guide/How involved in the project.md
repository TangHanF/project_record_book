# 如何参与项目，构建知识库？

> 一套知识库的积累仅靠一个人的力量是不够的，如果您对知识分享充满热情，不妨让我们一块努力吧！
>
> 有很多人对Git、Github的使用不是很熟悉，不知道如何参与到项目中。下面将就如何参与到本项目，为知识库添砖加瓦做出指导性说明：

-----
> - 假定现在你的电脑中已经安装了git，如果尚未安装请百度一下安装方法。
> - 假定安装NodeJS已经安装
> - 假定gitbook-cli等已安装（参考README.md或者《简介》中"本地部署方式"一节说明）


## 1、Fork本项目

> 首先从Github上找到该项目，然后Fork该项目到你自己的仓库中

![](https://gitee.com/TangHanF/pic/raw/master/9gsWZI.png)

## 2、Clone你Fork出来的项目到本地

> 假定你已经在自己的操作系统安装了Git，如果尚未安装Git，请百度一下 😆

```bash
git clone 自己fork项目的地址
```

例如：

```bash
git clone https://github.com/TangHanFeng/project_record_book.git
```

## 3、(**关键点**)增加源分支地址到自己项目远程分支列表中

本项目Github地址为：[https://github.com/TangHanFeng/project_record_book.git](https://github.com/TangHanFeng/project_record_book.git)，然后执行：

``` bash
git remote add upstream https://github.com/TangHanF/project_record_book.git
```

可以使用`git remote -v`查看一下远程分支列表情况，例如：

![](https://gitee.com/TangHanF/pic/raw/master/dtuL2S.png)

> **注意：** 请保证`upstream`地址是 https://github.com/TangHanF/project_record_book.git ，不然无法保持项目内容最新版！

## 4、fetch源分支的新版本到本地

```bash
git fetch upstream
```

## 5、合并代码到本地

```bash
git merge upstream/master
```

## 6、修改、新增笔记

> - 现在您本地的项目已是最新版，您可以对现有笔记进行审阅，发现问题可先[邮件联系我](mailto:guofu_gh@163.com)或者自行修改然后发起pull request。
> 
> - 如果您是新增笔记，请先明确自己要发布笔记所属的版块，例如是在：**编程开发/Java/实用代码/判断类** 中新建一篇名为"Java判断闰年"的笔记，请执行如下操作：

### 1) 修改`SUMMARY.md`目录结构

![](https://gitee.com/TangHanF/pic/raw/master/8f8d0H.png)

### 2) 执行`gitbook init`命令

> 因为上面已经对 `SUMMARY.md`做了修改，此时执行`gitbook init`就会在`md`文件夹下自动创建`Java判断闰年.md`的MarkDown文件

### 3) 编辑对应笔记内容

> 此时您就可以完善自己的笔记了，最后分享给大家！

### 4) 添加、提交您的更改

- git add 命令

- git commit 命令

## 7、将本地仓库推送到远程仓库

```bash
git push origin master
```



## 8、发起pull request

![](https://gitee.com/TangHanF/pic/raw/master/4DCQ7L.png)

![](https://gitee.com/TangHanF/pic/raw/master/r9AFF7.png)

## 9、构建书籍内容

首先，使用 gitbook build 将书籍内容输出到默认目录，也就是当前目录下的 _book 目录。
     
`gitbook build`
     
## 10、将 书籍部署到 gh-pages 分支
使用 gh-pages 这个工具，它可以将文件夹一键发布到 GitHub 项目下的 gh-pages 分支中（其他分支也可以发布，但是在本文下用到的就是 gh-pages 这个分支）。

首先先安装 gh-pages 工具:

`npm install -g gh-pages`

然后输入以下指令:

`gh-pages -d _book`

然后 _book 下的所有文档都会部署到 gh-pages 分支。大功告成。