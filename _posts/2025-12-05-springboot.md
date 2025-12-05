---
layout: article
title: springboot框架
tags: CS
cover: /assets/images/axure/page-single.jpg
---

### springboot项目创建

（1）JDK1.8，java8，添加Spring Web、thymeleaf（如果是前后端不分离，加上这个）依赖，create之后，配置Maven，运行BackendApplication.java文件

（2）一个地址栏中的url对应一个函数

- 前后端不分离实例（用的@Controller，而前后端分离用@RestController）：

函数`index()`对应`127.0.0.1:8080/pk/index/`

```
@Controller
@RequestMapping("/pk/")
public class IndexController {
    @RequestMapping("index/")
    public String index() {
        return "pk/index.html";
    }
}
```

在浏览器输入网址`127.0.0.1:8080/pk/index/`（注意最后有`/`，因为后端是`index/`，如果不想要有`/`则后端改为`index`），输出resources/templates/pk/index.html中的内容

- 前后端分离（@RestController = @Controller + @ResponseBody）

> 返回值处理方式
> @Controller:
> 返回字符串时被视作视图名称（模板名称）
> 需要手动添加 @ResponseBody 才能返回 JSON/文本数据
> @RestController:
> 所有方法默认返回数据内容，直接写入响应体
> 适合构建 RESTful API 接口

```
@RestController
@RequestMapping("/pk/")
public class BotInfoController {
    @RequestMapping("getbotinfo/")
    public String getBotInfo() {
        return "hhhhh";
    }
}
```

在浏览器输入网址`127.0.0.1:8080/pk/getbotinfo/`
