# Git 基本操作流程


> 现在已修改了文件为例：新增了一个readme.txt文件，如何提交？

1、`git status`:查看一下git仓库版本控制状态，是否有改动

2、`git add 提交的文件名`或者一次性添加全部改动的文件：`git add .`

3、`git commit -m "提交信息说明"`：提交到本地库

4、`git push`或者`git push git别名 分支名`，一般默认为：`git push origin master`

OK，完成

---------

- 修改提交前建议先pull（拉去/更新），避免冲突：`git pull`或`git pull git别名 分支名`

# 其它

## 文件忽略

> 文件的忽略需要在根目录创建一个“.gitignore”的文件，并将其加入的版本控制：`git add .gitignore`，以后忽略什么文件就在里面定义就行了，例如文件内容如下：

```bash
.idea/
*.iml
*.class
```

# git统一设置 


## log美化：

> git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"

## 设置别名
 
- git status简化为：git st：`git config --global alias.st status`
 
- git commit -m "xxxx" 简化为：git cm "说明"：`git config --global alias.st commit -m`
 
