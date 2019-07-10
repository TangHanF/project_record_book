# Git TortoiseGit与git结合

# 适用场景

> git服务端+gitolite

# 准备项

- 通过官方git-bash客户端生成的私钥文件(id_rsa)
- TortoiseGit客户端(Windows版本)
- git远程仓库地址(git@xxxxx:仓库名称)

# 具体配置流程

> 如果已经生成id_rsa且已经提供给git管理配置好了就不用在用ssh-keygen.exe生成了！

1、首先得用git官方客户端克隆下远程仓库才能使用TortoiseGit进行后续操作。

![image-20190330221808727](https://ws3.sinaimg.cn/large/006tKfTcly1g1l6lm5pxpj30ko0aaac4.jpg)

2、打开开始菜单，找到TortoiseGit-Puttygen

![image-20190330221320116](https://ws2.sinaimg.cn/large/006tKfTcly1g1l6gnjnkpj30de0ac0u5.jpg)

看到如下界面：

![image-20190330221356037](https://ws4.sinaimg.cn/large/006tKfTcly1g1l6h8keipj30qe0p8acn.jpg)

3、点击Load按钮加载使用官方git-bash使用ssh-keygen生成的私钥文件(id_rsa)

![image-20190330221458219](https://ws1.sinaimg.cn/large/006tKfTcly1g1l6iaygzlj30qa0pewk2.jpg)

点击确定按钮。

![image-20190330221542542](https://ws3.sinaimg.cn/large/006tKfTcly1g1l6j2wdxcj30qi0pe43g.jpg)

4、保存转换之后的私钥文件，自己起一个名字即可,例如：1.ppk。

​	注：ppk是该软件特有的格式。

5、进入克隆完成之后的仓库文件夹，右键：

![image-20190330222220334](https://ws3.sinaimg.cn/large/006tKfTcly1g1l6pz5yadj30om0sgtfk.jpg)

![image-20190330222314970](https://ws1.sinaimg.cn/large/006tKfTcly1g1l6qxct7jj312y0u0gtp.jpg)

Putty 密钥就选择第6步你保存的私钥即可，然后点击确定按钮



OK…..







# 额外说明

![image-20190330222508967](https://ws4.sinaimg.cn/large/006tKfTcly1g1l6swir9bj30yb0u00zu.jpg)

这个提交仅仅是提交到本地仓库，需要右键—选择"Git 同步"或者在提交完成之后，点击弹窗的"推送"。

![image-20190330222700768](https://ws4.sinaimg.cn/large/006tKfTcly1g1l6uu4fm0j30vc0c0dh5.jpg)

或者

![image-20190330222729646](https://ws2.sinaimg.cn/large/006tKfTcly1g1l6vcv73wj312c0rin2i.jpg)