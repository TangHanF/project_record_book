# 如何参与项目，构建知识库？

> 一套知识库的积累仅靠一个人的力量是不够的，如果您对知识分享充满热情，不妨让我们一块努力吧！
>
> 有很多人对Git、Github的使用不是很熟悉，不知道如何参与到项目中。下面将就如何参与到本项目，为知识库添砖加瓦做出指导性说明：

## 1、Fork本项目

> 首先从Github上找到该项目，然后Fork该项目到你自己的仓库中

![](https://ws2.sinaimg.cn/large/006tNc79ly1fyv2z101h2j31km03gdgf.jpg)

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

![](https://ws3.sinaimg.cn/large/006tNc79ly1fyv34so6jej30u804e40o.jpg)

## 4、fetch源分支的新版本到本地

```bash
git fetch upstream
```

## 5、合并代码到本地

```bash
git merge upstream/master
```

## 6、将本地仓库推送到远程仓库

```bash
git push origin master
```

## 7、发起pull request

![](https://ws2.sinaimg.cn/large/006tNc79ly1fyv3b2v2gij31io0iygps.jpg)

![](https://ws2.sinaimg.cn/large/006tNc79ly1fyv3cs0z08j317g0u0doo.jpg)

![](https://ws4.sinaimg.cn/large/006tNc79ly1fyv3dtbopbj31680u0q8p.jpg)