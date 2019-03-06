# IntelliJ IDEA 控制台中文乱码处理


**解决办法：**

![](https://ws3.sinaimg.cn/large/006tKfTcly1g0thiwbs72j309q02g747.jpg)

打开Intellij的安装的bin目录（例如：C:\\Program Files\\JetBrains\\IntelliJ IDEA 14.0\\bin ），找到上图的两个文件（根据你的系统是32位或64位选择其中一个配置文件），在配置文件中添加：

`-Dfile.encoding=UTF-``8`

配置项目编码及IDE编码
------------

![](https://ws1.sinaimg.cn/large/006tKfTcly1g0thix69cxj30sq0jc41c.jpg)

进入settings，选择File Encodings，把IDE Encoding和Project Encoding配置为UTF-8，同时将下面的Default encoding for properties files也配置为UTF-8。

配置项目启动服务器参数，在tomcat配置中
----------------------

![](https://ws2.sinaimg.cn/large/006tKfTcly1g0thixpy86j30u80le77a.jpg)

在VM options 项中添加

`-Dfile.encoding=UTF-``8`

1.tomcat输出到控制台（console）出现中文乱码，设置Run/Debug Configuration中设置environment variables 来解决。

Idea=\>Run=\>Edit Configuration，弹出的对话框中，在Startup/Connection 中Run中添加environment variables

JAVA\_TOOL\_OPTIONS=-Dfile.encoding=UTF-8.如下图所示：

![](https://ws1.sinaimg.cn/large/006tKfTcly1g0thiy8snvj30u60lbgo4.jpg)

2.对于maven构建的项目，由于idea中maven的配置优先，需要在pom.xml中对maven-surefire-plugin进行配置。

 \<plugins\>

 \<plugin\>

 \<groupId\>org.apache.maven.plugins\</groupId\>

 \<artifactId\>maven-surefire-plugin\</artifactId\>

 \<version\>2.12.4\</version\>

 \<configuration\>

 \<forkMode\>once\</forkMode\>

 \<argLine\>-Dfile.encoding=UTF-8\</argLine\>

 \</configuration\>

 \</plugin\>

 \</plugins\>