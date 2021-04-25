---

---

# Spring Boot 2 学习笔记

## Spring的生态

覆盖了：

- web开发；数据访问；安全控制；分布式；消息服务；移动开发；批处理等

## 为什么用SpringBoot

*能快速创建出生产级别的Spring应用。

## SpringBoot优点

- 创建独立Spring应用
- 内嵌web服务器
- 自动starter依赖，简化构建配置
- 自动配置Spring以及第三方功能
- 提供生产级别的监控、健康检查及外部化配置
- 无代码生成、无需编写XML
- SpringBoot是整合Spring技术栈的一站式框架
- SpringBoot是简化Spring技术栈的快速开发脚手架

## SpringBoot缺点

- 人称版本帝，迭代快，需要时刻关注变化
- 封装太深，内部原理复杂，不容易精通

## 基础入门-SpringBoot的大时代背景

### 微服务

- 微服务是一种架构风格
- 一个应用拆分为一组小型服务
- 每个服务运行在自己的进程内，也就是可独立部署和升级
- 服务之间使用轻量级HTTP交互
- 服务围绕业务功能拆分
- 可以由全自动部署机制独立部署
- 去中心化，服务自治。服务可以使用不同的语言、不同的存储技术

### 分布式的困难

- 远程调用；服务发现；负载均衡；服务容错；配置管理；服务监控；链路追踪；日志管理；任务调度

### 分布式的解决

- SpringBoot + SpringCloud

## SpringBoot-依赖管理特性

- 父项目做依赖管理

<parent>
	<groupId>org.springframework.boot</groupId>
	<artifactId>spring-boot-dependencies</artifactId>
	<version>2.3.4.RELEASE</version>
</parent>

它**几乎声明了所有开发中常用的依赖的版本号**，自动版本仲裁机制

## SpringBoot-自动配置特性

*自动配好Tomcat；引入Tomcat依赖；配置Tomcat

- 自动配好SpringMVC
  - 引入SpringMVC全套组件
  - 自动配好SpringMVC常用组件（功能）
- 自动配好Web常见功能，如：字符编码问题
  - SpringBoot帮我们配置好了所有web开发的常见场景

默认的包结构

- 主程序所在包及其下面的所有子包里面的组件都会被默认扫描进来
- 无需以前的包扫描配置
- **想要改变扫描路径**
  - **@SpringBootApplication(scanBasePackages=“com.lun”)**
  - **@ComponentScan 指定扫描路径**



## 使用Spring Initializer快速创建Spring Boot项目

IDEA：使用 Spring Initializer快速创建项目
IDE都支持使用Spring的项目创建向导快速创建一个Spring Boot项目；

选择我们需要的模块；向导会联网创建Spring Boot项目；

默认生成的Spring Boot项目；

主程序已经生成好了，我们只需要我们自己的逻辑
resources文件夹中目录结构
static：保存所有的静态资源； js css images；
templates：保存所有的模板页面；（Spring Boot默认jar包使用嵌入式的Tomcat，默认不支持JSP页面）；可以使用模板引擎（freemarker、thymeleaf）；
application.properties：Spring Boot应用的配置文件；可以修改一些默认设置；

## 配置文件

SpringBoot使用一个全局的配置文件，配置文件名是固定的；

•application.properties

•application.yml

配置文件的作用：修改SpringBoot自动配置的默认值；SpringBoot在底层都给我们自动配置好；

YAML（YAML Ain’t Markup Language）

 YAML A Markup Language：是一个标记语言

 YAML isn’t Markup Language：不是一个标记语言；

标记语言：

 以前的配置文件；大多都使用的是 xxxx.xml文件；

 YAML：以数据为中心，比json、xml等更适合做配置文件；

 YAML：配置例子
![image-20210327180516414](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210327180516414.png)

##  YAML语法：

### 1、基本语法

k:(空格)v：表示一对键值对（空格必须有）；

以**空格**的缩进来控制层级关系；只要是左对齐的一列数据，都是同一个层级的

![image-20210327180601427](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210327180601427.png)

属性和值也是大小写敏感；

### 2、值的写法

#### 字面量：普通的值（数字，字符串，布尔）

k: v：字面直接来写；

 字符串默认不用加上单引号或者双引号；

 “”：双引号；不会转义字符串里面的特殊字符；特殊字符会作为本身想表示的意思

 name: “zhangsan \n lisi”：输出；zhangsan 换行 lisi

 ‘’：单引号；会转义特殊字符，特殊字符最终只是一个普通的字符串数据

 name: ‘zhangsan \n lisi’：输出；zhangsan \n lisi

#### - 对象、Map（属性和值）（键值对）：

 k: v：在下一行来写对象的属性和值的关系；注意缩进

 对象还是k: v的方式

![image-20210327181429346](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210327181429346.png)

行内写法：

![image-20210327181444521](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210327181444521.png)

#### - 数组（List、Set）：

用- 值表示数组中的一个元素![image-20210327181512458](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210327181512458.png)

### 3、配置文件值注入

配置文件

```yaml
person:
    lastName: hello
    age: 18
    boss: false
    birth: 2017/12/12
    maps: {k1: v1,k2: 12}
    lists:
      - lisi
      - zhaoliu
    dog:
      name: 小狗
      age: 12
```

## 1、properties配置文件在idea中默认utf-8可能会乱码

调整

![image-20210327182127293](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210327182127293.png)

## 2、@Value获取值和@ConfigurationProperties获取值比较

![image-20210327183758791](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210327183758791.png)

配置文件yml还是properties他们都能获取到值；

如果说，我们只是在某个业务逻辑中需要获取一下配置文件中的某项值，使用@Value；

如果说，我们专门编写了一个javaBean来和配置文件进行映射，我们就直接使用@ConfigurationProperties；

## @PropertySource&@ImportResource&@Bean

@**PropertySource**：加载指定的配置文件；

@**ImportResource**：导入Spring的配置文件，让配置文件里面的内容生效；

Spring Boot里面没有Spring的配置文件，我们自己编写的配置文件，也不能自动识别；

想让Spring的配置文件生效，加载进来；@**ImportResource**标注在一个配置类上

## 4、Profile

### 1、多Profile文件

我们在主配置文件编写的时候，文件名可以是 application-{profile}.properties/yml；默认使用application.properties的配置；

### 2、yml支持多文档块方式

![image-20210327183940893](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210327183940893.png)

### 3、激活指定profile

 1、在配置文件中指定 spring.profiles.active=dev

 2、命令行：

 java -jar spring-boot-02-config-0.0.1-SNAPSHOT.jar --spring.profiles.active=dev；

 可以直接在测试的时候，配置传入命令行参数

 3、虚拟机参数；

 -Dspring.profiles.active=dev

## 5、配置文件加载位置

springboot 启动会扫描以下位置的application.properties或者application.yml文件作为Spring boot的默认配置文件

–file:./config/

–file:./

–classpath:/config/

–classpath:/

优先级由高到底，高优先级的配置会覆盖低优先级的配置；

SpringBoot会从这四个位置全部加载主配置文件；互补配置；

我们还可以通过spring.config.location来改变默认的配置文件位置

项目打包好以后，我们可以使用命令行参数的形式，启动项目的时候来指定配置文件的新位置；指定配置文件和默认加载的这些配置文件共同起作用形成互补配置；

java -jar spring-boot-02-config-02-0.0.1-SNAPSHOT.jar --spring.config.location=G:/application.properties
