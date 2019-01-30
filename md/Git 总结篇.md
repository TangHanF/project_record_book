# Git 总结篇

Git有三大区（工作区、暂存区、版本库）以及几个状态（untracked、unstaged、uncommited）

# 创建版本库、绑定远程版本库

``` bash
git init
```

首次使用可以进行全局设置：

```bash
git config --global user.name "用户名"
git config --global user.email "邮箱地址"
```

创建 git 仓库:

```bash
mkdir githubgitee
cd githubgitee
git init
touch README.md
git add README.md
git commit -m "first commit"
git remote add origin git@gitee.com:TangHanF/githubgitee.git
git push -u origin master
```

如果已经有了仓库，需要和远程仓库进行绑定，需要：

```bash
git remote add origin git@gitee.com:TangHanF/githubgitee.git
git push -u origin master
```

# 纳入版本库控制

在要纳入的目录下输入：

```
git init
```

进行初始化

添加要控制的文件，利用：git add [参数] 文件1 文件2  文件3 文件夹...，例如

```
git add readme.md libs/
```

如果有很多文件需要进行add，一个一个手动添加太麻烦 可以

```
git add .
```

然后提交即可：

```
git commit -m "提交说明信息"
```

# 创建公钥、私钥

开发者向码云版本库写入最常用到的协议是 SSH 协议，因为 SSH 协议使用公钥认证，可以实现无口令访问，而若使用 HTTPS 协议每次身份认证时都需要提供口令。使用 SSH 公钥认证，就涉及到公钥的管理。

### 1.如何生成ssh公钥

------

你可以按如下命令来生成sshkey:

```sh
ssh-keygen -t rsa -C "xxxxx@xxxxx.com"  

# Generating public/private rsa key pair...
# 三次回车即可生成 ssh key
```

查看你的 public key，并把他添加到码云（Gitee.com） [SSH key添加地址](http://git.oschina.net/profile/sshkeys)

```
cat ~/.ssh/id_rsa.pub
# ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQC6eNtGpNGwstc....
```

添加后，在终端（Terminal）中输入

```
ssh -T git@git.oschina.net
```

若返回

```
Welcome to Git@OSC, yourname!
```

则证明添加成功。

------

### 2.怎么添加用户ssh key?

------

# 提交修改的文件

1. 点击右上角的![输入图片说明](https://ws1.sinaimg.cn/large/006tNc79ly1fyxvo32jz5j301b0170fg.jpg)标志,进入个人中心,然后点击左侧的ssh公钥后在下图位置填写你的ssh公钥。
2. 点击确定,然后验证密码(即你的注册账号密码)就完成了ssh公钥添加。

![输入图片说明](https://ws4.sinaimg.cn/large/006tNc79ly1fyxvo4cj1gj30uv0hnmyf.jpg)

### 3.项目的 ssh key 和用户的 ssh key 两处地方有什么不同?

------

> 项目的 ssh key 只针对项目,且我们仅对项目提供了部署公钥,即`项目下的公钥仅能拉取项目`,这通常用于生产服务器拉取仓库的代码。 而用户的 key 则是针对用户的,用户添加了 key 就对用户名下的项目和用户参加了的项目具有权限,一般而言,用户的 key 具有推送和拉取的权限,而项目的 key 则只具有拉取权限
>
> 来源： <http://git.mydoc.io/?t=180845>

首先查看一下状态，使用：

```
git status
```

返回结果：

![img](https://ws2.sinaimg.cn/large/006tNc79ly1fyxvo5a5fqj30f507ut8s.jpg)

说明有一个文件更改了，然后加入到提交更改：

```
git add -u
```

然后再看一下状态：

```
git status
```

![img](https://ws3.sinaimg.cn/large/006tNc79ly1fyxvo5tr5nj30gf07rwek.jpg)

发现颜色变了，然后开始提交

```
git commit -m "修改说明"
get push
```

![img](https://ws4.sinaimg.cn/large/006tNc79ly1fyxvo6ppugj30i806x3yu.jpg)



# Git撤销修改等

`git checkout .` #本地所有修改的。没有的提交的，都返回到原来的状态

`git stash` #把所有没有提交的修改暂存到stash里面。可用git stash pop回复。

`git reset --hard HASH` #返回到某个节点，不保留修改。

`git reset --soft HASH` #返回到某个节点。保留修改

`git rm --cached --force "文件名"` # 将添加到暂存区的文件删除

# git 绑定GitHub和Gitee（码云）

github因为服务端在国外，从我们大天朝访问比较慢，真好我们本土有个gitee，访问速度没啥问题，现在需要将代码同步到这两个平台，如何做呢？

首先我们分别在两个平台新建一个远程仓库，名称都叫做“githubgitee”吧

在GitHub上创建一个repository

![img](https://ws2.sinaimg.cn/large/006tNc79ly1fyxvo7tauwj30lt0gljs7.jpg)

在码云上创建一个repository：

![img](https://ws3.sinaimg.cn/large/006tNc79ly1fyxvo8lcqpj30j60j43yy.jpg)



然后在本地磁盘创建一个本地库：

​    创建文件夹：I:\tmp\git

​    使用git初始化

```
git init
```

结果：

![img](https://ws4.sinaimg.cn/large/006tNc79ly1fyxvo9i2ygj30ln04bdfy.jpg)



我们先将GitHub与本地仓库进行绑定

```
git remote add github https://github.com/TangHanF/githubgitee.git
```

注意：如果只绑定一个库的话，默认应该是：git remote add **origin**<https://github.com/TangHanF/githubgitee.git> 我们为了区分起了一个别名而已

然后我们使用 **git remote -v** 命令查看一下绑定情况

![img](https://ws3.sinaimg.cn/large/006tNc79ly1fyxvoaeqdoj30gc01t0sp.jpg)

此时GitHub绑定完毕，我们接着绑定码云：

```
git remote add gitee git@gitee.com:TangHanF/githubgitee.git
```

然后查看一下绑定情况：

![img](https://ws1.sinaimg.cn/large/006tNc79ly1fyxvobdqu3j30go02rq2z.jpg)

到此为止，两个托管平台绑定完毕，我们**先pull一下**

```
# 从GitHub下载一份吧
```

```
git pull github master
```

![img](https://ws1.sinaimg.cn/large/006tNc79ly1fyxvobtgigj30h6045glo.jpg)

下载完毕

我们新建一个测试文件  test1.txt  然后提交到两个平台

![img](https://ws3.sinaimg.cn/large/006tNc79ly1fyxvocat0sj30ip04jmx5.jpg)

执行如下命令：

```
# 首先查看一下当前状态
git status
# 添加新建的文件
git add test.txt
# 提交到stage区
git commit -m "提交test.txt文件，测试演示"
# 提交到github的master主干
git push github master
# 提交到gitee的master主干
git push gitee master
```



![img](https://ws4.sinaimg.cn/large/006tNc79ly1fyxvodb5tcj30cx03va9x.jpg)

![img](https://ws3.sinaimg.cn/large/006tNc79ly1fyxvoe6zmdj30dm02l0so.jpg)

![img](https://ws3.sinaimg.cn/large/006tNc79ly1fyxvoeq9lyj30i00963yy.jpg)

# git 删除远程库绑定

```
# 库名可以使用 git remote -v 查询
```

```
git remote remove 库名
```

# git 查看某一版本提交的具体内容



```bash
# --name-only 只显示文件名 
git log --name-only -1
# --pretty=format:"" 格式化commit message 这里什么都不显示
git log --pretty=format:"" -1
# 最终
git log --pretty=format:"" --name-only  -1
```

可以参考：<https://segmentfault.com/q/1010000006760132?_ea=1125366>



# git恢复删除的文件

```
git checkout 提交的记录ID 文件名称（路径）
```

例如：

```
git checkout dd1f0db src/main/java/com/gh/test/dao/CameraInfoManageDaoI.java
```

# git 配置参数的别名

比如每次输入git status很麻烦，我们可以简化为git st，怎么操作？

```
git config --global alias.st status
```

即可

配置一个`git last`，让其显示最后一次提交信息：

```
$ git config --global alias.last 'log -1'
```

这样，用`git last`就能显示最近一次的提交：

```
$ git last
commit adca45d317e6d8a4b23f9811c3d7b7f0f180bfe2
Merge: bd6ae48 291bea8
Author: Michael Liao <askxuefeng@gmail.com>
Date:   Thu Aug 22 22:49:22 2013 +0800

    merge & fix hello.py
```

可以再配置一个美化日志输出的

```
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
```





![img](https://ws2.sinaimg.cn/large/006tNc79ly1fyxvof8vxsj30qb0hl3zq.jpg)



配置Git的时候，加上`--global`是针对当前用户起作用的，如果不加，那只针对当前的仓库起作用。

配置文件放哪了？每个仓库的Git配置文件都放在`.git/config`文件中：

```
$ cat .git/config 
[core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
    ignorecase = true
    precomposeunicode = true
[remote "origin"]
    url = git@github.com:michaelliao/learngit.git
    fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
    remote = origin
    merge = refs/heads/master
[alias]
    last = log -1
```

别名就在`[alias]`后面，要删除别名，直接把对应的行删掉即可。

而当前用户的Git配置文件放在用户主目录下的一个隐藏文件`.gitconfig`中：

```
$ cat .gitconfig
[alias]
    co = checkout
    ci = commit
    br = branch
    st = status
[user]
    name = Your Name
    email = your@email.com
```

配置别名也可以直接修改这个文件，如果改错了，可以删掉文件重新通过命令配置。



# git 创建分支（branch）

用到的命令：

- git checkout -b <分支（创建分支 -b表示创建并切换，想到执行了git branch <分支名称>和git checkout <分支名称> 两条命令）
- git branch （查看分支，当前分支前面有个“*”进行标识）
- git checkout<分支名称> （切换分支）
- git mergee <分支名称> （合并分支）
- git branch -d <分支名称> （删除分支）
- git push <库名> 分支名 （将新建的分支同步到远程库）
- git push <库名>  :分支名称 或 git branch -r -d <库名>/分支名称 （将删除的分支提交到远程库，与本地同步）



例如现在创建一个名称为 dev 的分支：

1、git checkout -b dev

![img](https://ws2.sinaimg.cn/large/006tNc79ly1fyxvog23onj30e201q0ss.jpg)

2、查看一下分支情况，git branch

![img](https://ws3.sinaimg.cn/large/006tNc79ly1fyxvogrq5ij30cr02iwee.jpg)

说明当前分支在 dev上

3、然后我们修改一下文件并提交

![img](https://ws1.sinaimg.cn/large/006tNc79ly1fyxvoi15vij30hi055aa5.jpg)

![img](https://ws3.sinaimg.cn/large/006tNc79ly1fyxvoiua9aj30ea021glo.jpg)

同步到远程库：git push gitee dev

![img](https://ws1.sinaimg.cn/large/006tNc79ly1fyxvojcsl0j30id04ot9j.jpg)

远程库同步之前：

![img](https://ws3.sinaimg.cn/large/006tNc79ly1fyxvokb7t9j30a1062mx9.jpg)

提交之后：

![img](https://ws3.sinaimg.cn/large/006tNc79ly1fyxvol7066j309i0720sr.jpg)

现在我们在dev分支下修改一下内容提交：

![img](https://ws1.sinaimg.cn/large/006tNc79ly1fyxvolnehej30c703dmwz.jpg)

## 分支合并

提交之后只有dev的文件变动了，master相同文件内容没有改变，现在我们合并分支，将dev与master进行合并：**首先切换到master分支，然后git merge dev**

![img](https://ws1.sinaimg.cn/large/006tNc79ly1fyxvomouksj30fg07rt9l.jpg)

提交，同步到远程库：

![img](https://ws3.sinaimg.cn/large/006tNc79ly1fyxvopfpm6j30dl032gly.jpg)

这样的话我们就可以大胆的删除dev分支了

![img](https://ws4.sinaimg.cn/large/006tNc79ly1fyxvopvgmmj30gl01u0sw.jpg)

然后同步到远程库：

![img](https://ws1.sinaimg.cn/large/006tNc79ly1fyxvoqd2ltj30dr02fdfq.jpg)



# git 创建标签

​    为什么要创建标签？首先，我们知道，git的版本号和svn的版本号不一样，svn的版本号是一次递增的数字，很好记忆，但是git的版本号是一个很长的ID，在svn我们一般说把版本23的打包一下，很自然，但是在git上我们说把版本2de3dffd3342add...的打包一下，是不是感觉很别扭。为了好区分，在git上我们可以使用tag，相当于一个快照，实际上是指向某个commit的指针，有点类似分支，但是和分支又有不同，分支可以移动，标签不能移动。

 相关命令：

- 命令`git tag <name>`用于新建一个标签，默认为`HEAD`，也可以指定一个commit id；
- `git tag -a <tagname> -m "标签信息的描述文字"`可以指定标签信息；
- `git tag -s <tagname> -m "标签信息的描述文字"`可以用PGP签名标签；
- git tag -d <tagname> 可以删除tag标签

- 命令`git tag`可以查看所有标签。

- 命令`git push <库名称> <标签名称>`可以将标签同步到远程库。

- 命令 git push <库名称> --tags 

  可以

  一次性推送全部尚未推送到远程的本地标签


## 创建tag

   首先创建一个tag，名称：v0.5 **注意要先切换到要打tag的分支上**

```
git tag v0.5
```

​    然后查看一下tag：

```
git tag
```



![img](https://ws4.sinaimg.cn/large/006tNc79ly1fyxvorq65pj30ej01o0sm.jpg)

​    如果说我们还有一个v0.3需要打tag，但是现在错过了打tag的时间要求，现在要新增这么一个tag怎么处理，命令格式：

```
git tag <tag名称> <版本号>
```

​    首先先查看一下历史，git lg是简化的自定义的

![img](https://ws2.sinaimg.cn/large/006tNc79ly1fyxvos9spuj30n6069wfc.jpg)

​    例如我们把 3a3cfb5 - 新增src 打一个v0.3的tag：

```
git tag v0.3 3a3cfb5
```



![img](https://ws3.sinaimg.cn/large/006tNc79ly1fyxvosp1scj30fl02k3yd.jpg)

​    这样就新增了一个v0.3的tag

## 查看标签信息

​    可以使用 **git show <tag名称>** 查看标签信息

![img](https://ws3.sinaimg.cn/large/006tNc79ly1fyxvou1w2pj30k907bt8y.jpg)

​    当然了，还可以创建带有描述信息的标签，格式：**git tag -a <tag名称> -m "tag说明信息" <ID版本号>**

​    -a：指定标签名

​    -m：标签描述信息



​    最后我们将标签同步到远程库：

![img](https://ws3.sinaimg.cn/large/006tNc79ly1fyxvoujp33j30f303f74n.jpg)



## 删除tag标签

![img](https://ws4.sinaimg.cn/large/006tNc79ly1fyxvov0uclj30ep01r745.jpg)



## 将删除的tag同步到远程

这个操作相对比较麻烦，需要执行：**git push <库名> :refs/tags/<tag名称>**

![img](https://ws2.sinaimg.cn/large/006tNc79ly1fyxvovgunsj30fq029mx2.jpg)


# git log 美化

但最有意思的是 `format`，可以定制要显示的记录格式，这样的输出便于后期编程提取分析，像这样：

```
$ git log --pretty=format:"%h - %an, %ar : %s"
ca82a6d - Scott Chacon, 11 months ago : changed the version number
085bb3b - Scott Chacon, 11 months ago : removed unnecessary test code
a11bef0 - Scott Chacon, 11 months ago : first commit
```

表 2-1 列出了常用的格式占位符写法及其代表的意义。

```
选项	 说明
%H	提交对象（commit）的完整哈希字串
%h	提交对象的简短哈希字串
%T	树对象（tree）的完整哈希字串
%t	树对象的简短哈希字串
%P	父对象（parent）的完整哈希字串
%p	父对象的简短哈希字串
%an	作者（author）的名字
%ae	作者的电子邮件地址
%ad	作者修订日期（可以用 -date= 选项定制格式）
%ar	作者修订日期，按多久以前的方式显示
%cn	提交者(committer)的名字
%ce	提交者的电子邮件地址
%cd	提交日期
%cr	提交日期，按多久以前的方式显示
%s	提交说明
```



# 问题解决类

##     解决Git Bash中文乱码问题

中文出现形如：\123\213\234\212\212,输入以下命令：

```bash
git config --global core.quotepath false
```