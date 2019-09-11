# IDEA创建Spring Boot项目

> 作者：TangHanF（GuoFu）
>
> 日期：2018年6月15日
>
> 说明：转载请注明出处，谢谢！🤝
>
> 联系方式：guofu_gh@163.com

# 1. 新建Spring Initializr 项目

![](https://gitee.com/TangHanF/pic/raw/master/XxaSiT.png)

# 2. 填写项目信息

![](https://gitee.com/TangHanF/pic/raw/master/YxTUpl.png)

# 3. 选择项目使用的技术

![](https://gitee.com/TangHanF/pic/raw/master/kIVDis.png)

# 4. 填写项目名称

![](https://gitee.com/TangHanF/pic/raw/master/yhIKGo.png)

# 5. 项目架构及依赖

<img src="https://gitee.com/TangHanF/pic/raw/master/TfJUN3.png" style="zoom:50%;" />

# 6. 添加测试控制器

直接在入口类中编写。

```java
package com.springboot.first;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
@SpringBootApplication
public class FirstApplication {

    @RequestMapping("/")
    String index() {
        return "Hello Spring Boot";
    }
    public static void main(String[] args) {
        SpringApplication.run(FirstApplication.class, args);
    }
}
```

@SpringBootApplication是Spring Boot 项目的核心注解，主要目的是开启自动配置。main方法是一个标准的Java应用的main方法，主要作用是作为项目启动的入口。

# 7. 运行项目

把它当成一个java类运行就可以了，右键菜单中选择，如图：

<img src="https://gitee.com/TangHanF/pic/raw/master/kI4WQc.png" style="zoom:50%;" />

运行信息：
![](https://gitee.com/TangHanF/pic/raw/master/zejCeC.png)

8. 运行结果，如图：

<img src="https://gitee.com/TangHanF/pic/raw/master/3upNHk.png" style="zoom:50%;" />