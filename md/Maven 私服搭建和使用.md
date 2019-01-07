# Maven 私服搭建和使用

下载安装Nexus3
==========

<https://www.sonatype.com/download-oss-sonatype>

![](https://ws3.sinaimg.cn/large/006tNc79ly1fyy118ng2hj30s80c278y.jpg)

修改配置
====

打开bin/nexus.vmoptions文件，可修改相应配置。

需修改服务器地址

启动
==

配置完成后，cmd打开远程客户端，进入nexus-3.0.1-01\\bin下，nexus.exe /start nexus

启动成功后，访问：localhost:8081。

默认的用户名和密码：admin/admin123，登录后看到如下图所示

![](https://ws1.sinaimg.cn/large/006tNc79ly1fyy11ts77dj30uq08gjss.jpg)

私服仓库配置
======

私服如果添加第三方jar包
-------------

登录账户：admin/admin123

![](https://ws1.sinaimg.cn/large/006tNc79ly1fyy12jwxujj30oi0ngdk8.jpg)

项目中如何使用私服
=========

方法一
---

在maven的setting文件中\<settings\>节点下找到\<profiles\>节点（无则创建），然后将下面代码加入其中：

```xml
    
<profile>
  <!--profile的id-->
  <id>dev</id>
  <repositories>
    <repository>
      <!--仓库id，repositories可以配置多个仓库，保证id不重复-->
      <id>nexus</id>
      <!--仓库地址，即nexus仓库组的地址-->
      <url>http:// 127.0.0.1:778/repository/maven-public/</url>
      <!--是否下载releases构件-->
      <releases>
        <enabled>true</enabled>
      </releases>
      <!--是否下载snapshots构件-->
      <snapshots>
        <enabled>true</enabled>
      </snapshots>
    </repository>
  </repositories>
  <pluginRepositories>
    <!-- 插件仓库，maven的运行依赖插件，也需要从私服下载插件 -->
    <pluginRepository>
      <!-- 插件仓库的id不允许重复，如果重复后边配置会覆盖前边 -->
      <id>public</id>
      <name>Public Repositories</name>
      <url>http://127.0.0.1:778/repository/maven-public/</url>
    </pluginRepository>
  </pluginRepositories>

```

上面的profile标签需要激活，在\< profiles \>节点后面加入以下代码激活

```xml
<!--使用profile定义仓库需要激活才可生效-->
<activeProfiles>
  <activeProfile>dev</activeProfile>
</activeProfiles>

```

方法二
---

在需要使用maven私服的pom文件中添加如下代码:

```xml
<repositories>
  <repository>
    <id>nexux</id>
    <name>maven-public</name>
    <url>http://127.0.0.1:778/repository/maven-public/</url>
  </repository>
</repositories>

```