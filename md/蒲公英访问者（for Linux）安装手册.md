# 蒲公英访问者（for Linux）安装手册

[蒲公英](http://shop.oray.com/item/oraybox_2pick.html?ici=shop_oraybox&icn=service_oraybox)智能组网[蒲公英VPN](http://pgy.oray.com/download/)客户端目前已支持在Linux操作系统上使用。
目前支持的应用平台有Ubuntu、Redhat/CentOS，在蒲公英官网下载页面，根据对应的系统版本及位数进行下载。（[链接戳我](http://pgy.oray.com/download/)）
![](https://ws2.sinaimg.cn/large/006tNc79ly1fyy0r066yjj30im0bqaba.jpg)

### [一、Redhat/Centos系统安装教程](http://service.oray.com/question/4609.html#%E4%B8%80%E3%80%81Redhat/Centos%E7%B3%BB%E7%BB%9F%E5%AE%89%E8%A3%85%E6%95%99%E7%A8%8B)

### [二、Ubuntu系统安装教程](http://service.oray.com/question/4609.html#%E4%BA%8C%E3%80%81Ubuntu%E7%B3%BB%E7%BB%9F%E5%AE%89%E8%A3%85%E6%95%99%E7%A8%8B)

**注意：蒲公英访问者 for Linux安装步骤都需要在管理员权限下运行。**

---

#### 一、Redhat/Centos系统安装教程

##### 1.安装

下载安装包后，通过cd命令进入对应下载目录，输入下面的命令进行安装；
32位：**rpm -ivh PgyVistor-1.1.0.i386.rpm**
64位：**rpm -ivh PgyVistor-1.1.0.x86\_64.rpm**
![](https://ws3.sinaimg.cn/large/006tNc79ly1fyy0r0wlilj30im0dsgn7.jpg)

##### 2.运行

安装成功后，任意路径下执行“**PgyVistor**”调出交互界面，按照界面指示输入Oray官网帐号密码进行登陆；
![](https://ws2.sinaimg.cn/large/006tNc79ly1fyy0r39dgjj30im0dsdil.jpg)

##### 3.功能指令

登录成功后，键入对应序号可查询使用对应信息和功能。
![](https://ws2.sinaimg.cn/large/006tNc79ly1fyy0r3vu2zj30im07jwga.jpg)

**3.1 获取组成员信息**
输入序号“1”：显示蒲公英网络组中的成员信息以及在线状态。
![](https://ws1.sinaimg.cn/large/006tNc79ly1fyy0r4gacbj30im0dsacl.jpg)

**3.2 查看旁路路由**
输入序号“2”：可查看到旁路路由设置的规则。（[了解旁路请戳我](http://service.oray.com/question/4288.html "了解旁路请戳我")）
![](https://ws1.sinaimg.cn/large/006tNc79ly1fyy0r5yy7oj30im0ds765.jpg)

**3.3 更换帐号**
输入序号“3”：注销当前帐号，重新输入新的官网帐号密码进行登录。
![](https://ws2.sinaimg.cn/large/006tNc79ly1fyy0rbc94kj30im0dumzj.jpg)

**3.4 查看所有设置**
输入序号“4”：查看用户名、是否自动登录以及是否实时显示成员变动信息。
输入序号“5”：开启实时信息显示。
输入序号“6”：关闭实时信息显示。
![](https://ws4.sinaimg.cn/large/006tNc79ly1fyy0rcwajbj30im0dsgn4.jpg)

**3.5 切换语言**
输入序号“7”：可进行中英文切换。
![](https://ws4.sinaimg.cn/large/006tNc79ly1fyy0rh275kj30im0dt41p.jpg)

**3.6 退出并关闭VPN服务**
输入序号“8”：注销退出当前帐号并关闭蒲公英组网服务。
![](https://ws1.sinaimg.cn/large/006tNc79ly1fyy0rifdplj30im0drmyt.jpg)

**3.7 退出VPN界面**
输入序号“9”：退出访问者前台界面，服务在后台继续运行。
![](https://ws1.sinaimg.cn/large/006tNc79ly1fyy0rkdx6rj30im0drmzf.jpg)

##### 4.卸载蒲公英访问者

可在任意路径输入下方命令进行卸载蒲公英访问者服务。
命令：**rpm -e PgyVistor**
![](https://ws4.sinaimg.cn/large/006tNc79ly1fyy0rl7jrij30im0drt9k.jpg)

##### 5.查看访问者日志文件

蒲公英VPN日志文件路径：**/var/log/pgyvistor**
![](https://ws4.sinaimg.cn/large/006tNc79ly1fyy0rlt2n2j30im0drgmg.jpg)

#### 二、Ubuntu系统安装教程

##### 1.安装

下载安装包后，通过cd命令进入对应下载目录，输入下面的命令进行安装；
32位：**dpkg -i PgyVistor-1.1.0.i386.deb**
64位：**dpkg -i PgyVistor-1.1.0.x86\_64.deb**
![](https://ws1.sinaimg.cn/large/006tNc79ly1fyy0rp5lpdj30im0baq6z.jpg)

##### 2.运行

安装成功后，任意路径下执行“**PgyVistor**”调出交互界面，按照界面指示输入Oray官网帐号密码进行登陆；
![](https://ws2.sinaimg.cn/large/006tNc79ly1fyy0rq74sdj30im0baacd.jpg)

##### 3.功能指令

登录成功后，键入对应序号可查询使用对应信息和功能。（操作方式界面与Redhat/Centos系统一致）
![](https://ws1.sinaimg.cn/large/006tNc79ly1fyy0rrgtnij30im08oq6d.jpg)

##### 4.卸载蒲公英VPN

可在任意路径输入下方命令进行卸载蒲公英访问者服务。
命令：**dpkg -r PgyVistor**
![](https://ws1.sinaimg.cn/large/006tNc79ly1fyy0rtdijgj30im0baq5h.jpg)

##### 5.查看VPN日志文件

蒲公英访问者日志文件路径：**/var/log/pgyvistor**
![](https://ws3.sinaimg.cn/large/006tNc79ly1fyy0rukif5j30im0e276o.jpg)