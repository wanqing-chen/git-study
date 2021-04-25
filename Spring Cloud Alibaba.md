# *Spring Cloud Alibaba*

## *什么是Spring Cloud Alibaba*

*阿里巴巴结合自身微服务实践，开源的微服务全家桶

*在Spring Cloud项目中孵化，很有可能成为Spring Cloud第二代的标准实现

*在业界广泛使用，已有很多成功案例（比如爱奇艺，工商银行，虎牙直播，最大的使用者还是阿里，主要是阿里自研的）

## *Spring Cloud Alibaba真实应用场景*

*大型复杂的系统，例如大型电商系统

*高并发系统，例如大型门户，秒杀系统

*需求不明确，且变更很快的系统，例如创业公司业务系统

## Spring Cloud Alibaba和Spring Cloud有什么区别和联系

![image-20210325105129398](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325105129398.png)

简单来说：Spring Cloud Alibaba是Spring Cloud的子项目，Spring Cloud Alibaba符合Spring Cloud的标准

![image-20210325105317402](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325105317402.png)

## Spring Cloud Alibaba简单总结有如下特点

*组件性能更强

*良好的可视化界面

*搭建简单，学习曲线低

*文档丰富并且是中文

## Spring Cloud Alibaba的重要组件学习

### 1.服务发现Nacos

​	①服务发现原理剖析

​	②Nacos Server/Client

​	③高可用Nacos搭建

### 2.实现负载均衡Ribbon

​	①负载均衡的常见模式

​	②RestTemplate整合Ribbon

​	③Ribbon配置自定义

​	④如何拓展Ribbon

### 3.声明式HTTP客户端-Feign

​	①如何使用Feign

​	②Feign配置自定义

​	③如何拓展Feign

### 4.服务容错Sentinel

​	①服务容错原理

​	②Sentinel

​	③Sentinel Dashboard

​	④Sentinel核心原理分析

### 5.消息驱动RocketMQ

​	①Spring Cloud Stream

​	②实现异步消息推送与消费

### 6.API网关Gateway

​	①整合Gatway

​	②三大核心

​	③聚合微服务请求

### 7.用户认证与授权

​	①认证授权的常见方案

​	②改造授权的常见方案

​	③拓展Feign

### 8.配置管理Nacos

​	①配置如何管理

​	②配置动态刷新

​	③配置管理的最佳实践

### 9.调用链监控Sleuth

​	①调用链监控原理剖析

​	②Sleuth使用

​	③Zipkin使用



# Spring Cloud学习环境准备事项

## Maven安装与配置

​	*下载     地址：https://maven.apache.org/download.cgi

​	*安装     说明文档：https://maven.apache.org/install.html

​					注意：如果IDEA版本过低，请勿下载Maven 3.6.x

​					验证：mvn -version

![image-20210325113027219](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325113027219.png)

​	*配置Aliyun Maven镜像

​		作用：加速jar包下载

​		配置说明：http://help.aliyun.com/document_detail/102512.html

![image-20210325113708654](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325113708654.png)

## IDEA配置与技巧

*IDEA配置Maven整合

*快捷键技巧

​	macOS：CheatSheet 打开软件，长按键盘上面的cmmand键，可以显示快捷键命令（好像能成为快捷键高手哈哈哈）

​	Window：HotKey Explorer、HotKey Commander、快捷键说明【建议】

![image-20210325114925858](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325114925858.png)

IDEA里面Help自带的快捷键（需要自带翻译能力）

# Spring Boot必知必会

## Spring Boot是什么？能做什么？

*是一个快速开发的脚手架

*作用：快速创建独立的，生产级的基于Spring的应用程序

*特性

​	1.无需部署WAR文件

​	2.提供starter简化配置

​	3.尽可能自动配置Spring以及第三方库

​	4.提供“生产就绪”功能，例如指标、健康检查、外部配置等

​	5.无代码生成&无XML

## 掌握必知必会如下

*快速创建应用

*应用组成分析

*开发三板斧

*Spring Boot Actuator监控

*配置管理

*Profile

### 必知必会：编写第一个Spring Boot应用

*需求

​	1.整合Spring MVC

​	2./test路径（端点）

*使用Spring Initializr快速创建Spring Boot应用

![image-20210325123024689](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325123024689.png)

![image-20210325123403889](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325123403889.png)

在项目启动前，养成下面一个良好的习惯，务必先执行 **mvn clean install**

![image-20210325124549420](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325124549420.png)

这是为了确保能够构建成功，再去启动，这主要是为了防止jar包没有下载完整，导致启动失败，或者应用各种报错![image-20210325125406175](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325125406175.png)

![image-20210325125752478](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325125752478.png)

这是直接在IDEA上启动Spring Boot应用

### 实际项目中怎么部署Spring Boot应用呢

cd target 进入到项目该目录下

![image-20210325130049635](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325130049635.png)

执行java -jar *.jar即可

### 必知必会：Spring Boot应用组成分析

*依赖：pom.xml

```xml
<!--springmvc整合-->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
```

```xml
<!--单元测试支持-->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-test</artifactId>
    <scope>test</scope>
</dependency>
```

```xml
<!--提供打包-->
<plugin>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-maven-plugin</artifactId>
</plugin>
```

*启动类：注解

```java
@SpringBootApplication
public class SpringBootDemoApplication {
	//启动类
    public static void main(String[] args) {      SpringApplication.run(SpringBootDemoApplication.class, args);
    }
}
```

*配置：application.properties，位于resources下

![image-20210325134225577](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325134225577.png)

*static目录：静态文件（.js/.css/图片）

*templates目录：模板文件

​	Spring Boot支持的模板引擎有：FreeMarker、Groovy、Thymeleaf、Mustache（但是由于前后端模式的开发，模板引擎越来越少使用了）

### 必知必会：Spring Boot开发三板斧

*加依赖

```xml
<!--boot官方提供的依赖写法：spring-boot-starter-xxx-->
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-data-jpa</artifactId>
</dependency>
```

```xml
<!--非官方呢？如mybatis 非官方提供starter:xxxspring-boot-starter--->
<dependency>
    <groupId>org.mybatis.spring.boot</groupId>
    <artifactId>mybatis-spring-boot-starter</artifactId>
    <version>2.1.4</version>
</dependency>
```

*写注解

*写配置

### 必知必会：Spring Boot Actuator

*是什么？

*如何整合？

加依赖

```xml
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-actuator</artifactId>
</dependency>
```

Exposing 2 endpoint(s) beneath base path '/actuator'

意思是actuator端点暴露了两个端点

访问/actuator返回了一堆结果

![image-20210325140631554](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325140631554.png)

随意访问一个，/actuator/health（是一个非常重要端点）

![image-20210325140755400](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325140755400.png)

**/health**

作用：是健康检查

status取值：

*UP：正常

*DOWN：遇到了问题，不正常

OUT_OF-SERVICE：资源未在使用，或者不该去使用

*UNKNOWN：不知道

```properties
management.endpoint.health.show-details=always
```

加了展示健康细节配置，在访问/health，得到

![image-20210325141212374](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325141212374.png)

**/info端点**

这是一个描述端点，用于描述应用的

```properties
#建议描述应用，当然也可以随便写
info.app-name=spring-boot-demo
info.author=wankin
info.email=xxx@email
```

![image-20210325141933113](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325141933113.png)

*actuator常用端点

这些端点都是隐藏的，只有/health和/info默认暴露

![image-20210325142219880](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325142219880.png)

```properties
#激活所有的actuator端点
management.endpoints.web.exposure.include=*

#选择激活部分端点
management.endpoints.web.exposure.include=metrics,health
#需记住actuator相关配置是以management开头
```

*actuator常用配置

*actuator健康检查详解

### 必知必会：Spring Boot配置管理

*支持的配置格式

​	有.properties和.yml两种格式

```yml
#另一种标记语言
#Yet Another Markup Language(.yml/.yaml) ==>JSON子集
#yaml有严格的缩进并且要统一，:后面的空格不能少
#在实际项目properties和yaml两种方式都可以，但一般推崇yaml
#yaml寻找大量配置时方便，根据树根寻找
#yaml在业界越来越受欢迎
#在极端情况下yaml可以表达配置顺序而properties不可以
management:
  endpoint:
    health:
      show-details: always
  endpoints:
    web:
      exposure:
        include: metrics,health
info:
  app-name: spring-boot-demo
  author: wankin
  email: xxx@email
```

Spring Boot配置管理的-17中姿势

了解即可

![image-20210325145002933](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325145002933.png)

*配置管理常用方式

1.配置文件

2.环境变量

![image-20210325145722924](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325145722924.png)

![image-20210325145441916](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325145441916.png)

有了环境变量后外部部署得在mvn clean install加上 -DskipTests 忽略掉单元测试

3.外部配置文件

4.命令行参数

*最佳实践（怎么简单怎么来）

## 有了环境变量怎么部署

**mvn clean install -DskipTests**

**java -jar spring-boot-demo-0.0.1-SNAPSHOT.jar --SOME_ENV=always**

### 必知必会：Profile

*如何实现不同环境不同配置

*怎么使用

```yaml
# 所有环境公用的配置属性
management:
  endpoint:
    health:
      show-details: always
  endpoints:
    web:
      exposure:
        include: metrics,health
info:
  app-name: spring-boot-demo
  author: wankin
  email: xxx@email
#连字符
---
# profile=x的专用属性，也就是某个环境下的专用属性
#开发环境
spring:
  profiles: dev
---
# profile=y的专用属性，也就是某个环境下的专用属性
#生产环境
spring:
  profiles: prod
server:
  tomcat:
    max-threads: 300
    max-connections: 1000
```

注意：应用以开发环境启动，使用一二两段的配置文件，反之亦然。

![image-20210325152109692](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325152109692.png)

在这里指定启动环境即可

![image-20210325152621006](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325152621006.png)

如果不值得profile，那么默认是default

```yaml
spring:
  profiles:
    active: dev
#设置默认启动的环境
```

看一下properties配置文件中怎么区别其他环境

![image-20210325153412545](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325153412545.png)

application.properties是全局配置文件，用于公用，其他的是选择生效的配置环境

![image-20210325153628659](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325153628659.png)

这里的优先级比配置文件中的高

*最佳实践（简单原则）

# springboot简单总结

*使用Spring Initializr快速创建应用

*应用组成分析

*三板斧

*Actuator

*配置管理

*Profile

# 微服务拆分与编写

## 单体架构VS微服务架构

### 	1.单体架构是什么

​			*一个归档包（例如war包）包含所有功能的应用程序，我们通常称为单体应用。而架构单体应用的方法论，就是单体应用架构。

![image-20210325154930260](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325154930260.png)

​			*单体架构的优点

​				1.架构简单

​				2.开发、测试、部署方便

​			*单体架构的缺点

​				1.复杂性高

​				2.部署慢，频率低

​				3.扩展能力受限

​				4.阻碍技术创新

### 	2.微服务是什么

​			*微服务“定义”

​				微服务架构风格是将一个单一应用程序开发为***一组小型服务***的方法，每个服务运行在***自己的进程***中，服务间通信采用***轻量级通信机制***(通常用HTTP资源API)。这些服务***围绕业务能力构建***并且可通过***全自动部署机制***独立部署。这些服务共用一个***最小型的集中式的管理***，服务可用***不同的语言***开发，使用***不同的数据存储技术***。	

### 	3.微服务的特性

​			1.每个微服务可运行在***自己的进程***中；

​			2.一系列独立运行的微服务共同构建起整个系统；

​			3.每个服务为独立的业务开发，一个微服务只关注某个特定的功能，例如订单管理，用户管理等；

​			4.可使用不同语言与数据存储技术（契合项目情况和团队实力）；

​			5.微服务之间通过轻量的通信机制进行通信，例如通过REST API进行调用；

​			6.全自动的部署机制。

### 	4.微服务全景架构图

![image-20210325161024245](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325161024245.png)

### 	5.微服务优缺点

#### 		1.微服务的优点

​				*单个服务更易于开发、维护

​				*单个微服务启动较快

​				*局部修改容易部署

​				*技术栈不受限

​				*按需伸缩

#### 		2.微服务的缺点

​				*运维要求高

​				*分布式固有的复杂性

​				*会重复劳动（不同服务可能有一样的实现，但也要重复编写）	

### 	6.微服务适用场景

​			*大型、复杂的项目

​            *有快速迭代的需求

​            *访问压力大

​			不适用微服务的场景

​			*业务稳定

​			*迭代周期长

## 业务分析与建模

### 	1.微服务拆分

​		*业界流行的拆分方法论

​			1.领域驱动设计（**D**omain **D**riven **D**esign）

​			2.面向对象（by name. / by verb）

​		*个人心得

​			1.职责划分

​			2.通用性划分

​		*合理粒度

​			1.良好地满足业务

​			2.幸福感

​			3.增量迭代（微服务相对独立）

​			4.持续进化

​		*项目（小程序的拆分）

![image-20210325170019561](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325170019561.png)

### 	2.项目架构图

​		![image-20210325170123279](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325170123279.png)

### 	3.数据库设计

​		*数据建模

​		*把表建好

![image-20210325172505056](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325172505056.png)

数据库建表

![image-20210325173225052](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325173225052.png)

### 	4.API文档

## 技术选型

*Spring Boot（快速开发）

*Spring MVC（MVC框架）

*Mybatis(持久层框架，操作数据库)+通用Mapper

*Spring Cloud Alibaba(分布式) 

## 工程结构规划图

![image-20210325192510009](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325192510009.png)

## 创建项目，整合框架

整合tk.mybatis

```xml
<dependency>
  <groupId>tk.mybatis</groupId>
  <artifactId>mapper-spring-boot-starter</artifactId>
  <version>版本号</version>
</dependency>
```

```java
// 扫描mybatis哪些包里的接口
@MapperScan("com.itmuch")
//启动类加注解
```

配置数据源

```yaml
spring:
  datasource:
    url: jdbc:mysql://localhost:3306/user_center
    hikari:
      username: root
      password: root
      # >= 6.x com.mysql.cj.jdbc.Driver
      # <= 5.x com.mysql.jdbc.Driver
      # 使用5.x的写法也可以，但不建议，5.x写法继承了6.x的com.mysql.cj.jdbc.Driver
      driver-class-name: com.mysql.cj.jdbc.Driver
```

![image-20210325195757335](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325195757335.png)

### 遇到一些错误

在配置generatorConfig.xml时出现：URI is not registered (Settings | Languages & Frameworks | Schemas and DTDs）错误

在IDEA的xml资源文件中出现URI is not registered错误，中文意思就是统一资源标识符没有注册，解决方法就是将这个标识符手动添加到IDEA中，**首先复制报红色的那串代码（只要红色的部分**），然后按照步骤添加就行。

- file --> settings- -> languages & frameworks -->Schemas and DTDs

- ![image-20210325201233749](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325201233749.png)

- ![image-20210325201248194](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325201248194.png)

- 点击下方的加号，将复制的内容粘贴进输入框，然后点击OK，再点击apply就行了。

- ![image-20210325201306099](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325201306099.png)

  ![image-20210325201708730](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325201708730.png)

  ![image-20210325201722862](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325201722862.png)

  ![image-20210325201736917](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325201736917.png)

  注意加上geneator/

  ```xml
  <!--实体生成-->
  <javaModelGenerator targetPackage="com.isea533.mybatis.model"
                      targetProject="src/main/java"/>
  <!--mapper.xml-->
  <sqlMapGenerator targetPackage="mapper"
                   targetProject="src/main/resources"/>
  <!--mapper接口生成-->
  <javaClientGenerator targetPackage="com.isea533.mybatis.mapper"
                       targetProject="src/main/java"
                       type="XMLMAPPER"/>
  <!--为哪张表生成代码-->
  <table tableName="${tableName}">
  ```

需要更改的生成位置

![image-20210325204618742](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325204618742.png)

config.properties配置文件需要的配置

![image-20210325204945617](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325204945617.png)

![image-20210325205322321](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325205322321.png)

generatorConfig.xml的配置代码

```xml
<!DOCTYPE generatorConfiguration
        PUBLIC "-//mybatis.org//DTD MyBatis Generator Configuration 1.0//EN"
        "http://mybatis.org/dtd/mybatis-generator-config_1_0.dtd">

<generatorConfiguration>
    <properties resource="generator/config.properties"/>

    <context id="Mysql" targetRuntime="MyBatis3Simple" defaultModelType="flat">
        <property name="beginningDelimiter" value="`"/>
        <property name="endingDelimiter" value="`"/>

        <plugin type="tk.mybatis.mapper.generator.MapperPlugin">
            <property name="mappers" value="tk.mybatis.mapper.common.Mapper"/>
            <property name="caseSensitive" value="true"/>
        </plugin>

        <jdbcConnection driverClass="${jdbc.driverClass}"
                        connectionURL="${jdbc.url}"
                        userId="${jdbc.user}"
                        password="${jdbc.password}">
        </jdbcConnection>

        <javaModelGenerator targetPackage="com.itmuch.usercenter.domain.entity.${moduleName}"
                            targetProject="src/main/java"/>

        <sqlMapGenerator targetPackage="com.itmuch.usercenter.dao.${moduleName}"
                         targetProject="src/main/resources"/>

        <javaClientGenerator targetPackage="com.itmuch.usercenter.dao.${moduleName}"
                             targetProject="src/main/java"
                             type="XMLMAPPER"/>

        <table tableName="${tableName}">
            <generatedKey column="id" sqlStatement="JDBC"/>
        </table>
    </context>
</generatorConfiguration>
```

config.properties的配置代码

```properties
jdbc.driverClass=com.mysql.cj.jdbc.Driver
jdbc.url=jdbc:mysql://localhost:3306/user_center
jdbc.user=root
jdbc.password=root

# 模块名称
moduleName=user
# 表名
tableName=user
```

```properties
jdbc.url=jdbc:mysql://localhost:3306/user_center?nullCatalogMeansCurrent=true
这个解决了多个同名表，使用mybatis-generator生成器时产生实体类的错误
#?nullCatalogMeansCurrent=true
```

![image-20210325212522395](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325212522395.png)

小注意点，this.更加规范

![image-20210325214201194](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210325214201194.png)

### Ctrl+R	查找替换快捷键

### Alt+Enter 补充快捷键

## 关于注解

@Data是一个Lombok组合注解；组合了@Getter；@Setter；@RequiredArgsConstructor;@ToString;@EqualsAndHashCode;

@Builder

@RequiredArgsConstructor它是为**final的属性**生成构造方法

@Builder代替了set方法  （建造者模式）![image-20210326093711938](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210326093711938.png)

@Slf4j  打印日志注解

log.info("xxxxx")

@Bean作用例子

```java
//在spring容器中，创建一个对象，类型RestTemplate；名称/ID是：restTemplate
// <bean id="restTemplate" class="xxx.RestTemplate"/>
@Bean
public RestTemplate restTemplate(){
    new RestTemplate();
```

@FunctionalInterface //通知编译器这是函数式接口，进行抽象方法检查（可写可不写）

## 改善Lombok和mybatis整合

Lombok 增加 model 代码生成时，可以直接生成 lombok 的 `@Getter@Setter@ToString@Accessors(chain = true)` 四类注解， 使用者在插件配置项中增加 `<property name="lombok" value="Getter,Setter,ToString,Accessors"/>` 即可生成对应包含注解的 model 类。

## 问题

***@Resource和@Autowired的区别**

***@Repository @Component @Service @Controller的区别和联系**

## 编写微服务

### 	1.创建小程序

### 	2.创建项目

### 	3.编写用户微服务

### 	4.编写内容微服务

​			*业务流程分析

​	![image-20210326114418766](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210326114418766.png)

​				*架构图![image-20210326114844065](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210326114844065.png)

# 项目主要开发流程

## Schema First

1. 分析业务（流程图、用例图...架构图等等）--> 建模业务，并且确定架构
2. 敲定业务流程（评审）
3. 设计API(我需要哪些API呢)/数据模型(表结构设计|类图|ER图等等)
4. 编写API文档
5. 编写代码

---

## API First

1. 分析业务（流程图、用例图...架构图等等）--> 建模业务，并且确定架构
2. 敲定业务流程（评审）
3. 设计API(我需要哪些API呢)/数据模型(表结构设计|类图|ER图等等)
4. 编写代码
5. 编写API文档

![image-20210326120508434](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210326120508434.png)

```java
@RequiredArgsConstructor(onConstructor = @__(@Autowired))
private final UserService userService;

//这是使用Lombok的一种注入方式
```

## RestTemplate通信

*简介

​	1.Spring Web提供的轻量级Http Client，用于简化Http调用

​	2.使用![image-20210326134505582](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210326134505582.png)

里面的.getForEntity（）方法和.getForObject基本一样，如果有需要返回状态码的，采用.getForEntity（）

### Spring Cloud学习存在的问题

### 如何实现负载均衡？

![image-20210326144639630](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210326144639630.png)

*微服务地址发生变化怎么办？

*如何实现负载均衡？

*用户中心挂掉怎么办？

## 什么是Spring Cloud 

*快速构建分布式系统的工具集（抽象了点）

## Spring Cloud主要功能

![image-20210326145347040](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210326145347040.png)

## Spring Cloud常用子项目

![image-20210326145545454](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210326145545454.png)

## *什么是Spring Cloud Alibaba补充*

*Spring Cloud的子项目

*致力于提供给微服务开发的一站式解决方案。

​	*包含微服务开发的必备组件

​	*基于Spring Cloud，符合Spring Cloud标准

​    *阿里的微服务解决方案

## Spring Cloud Alibaba主要功能

![image-20210326150224791](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210326150224791.png)

## 版本与兼容性

看一下Spring Boot的命名

<Version>2.1.5.RELEASE</Version>

<!--语义化的版本控制-->

<!--2：主版本，第几代-->

<!--1：次版本，一些功能的增加，但是架构没有太大的变化，是兼容的-->

<!--5：增量版本，bug修复-->

<!--release：里程碑，SNAPASHOT：开发版 M：里程碑 RELEASE :正式版-->

*Spring Cloud版本命名

​	Greewich SR1

​	Greewich:release train（发布列车）

​	Angel

​	Brixton

​	Camden

​	Dalston

​	Edgware

​	Finchley

​	Greewich

​	Hoxton

​	这些都是伦敦地铁站名

​	Service Relase:bug修复

​	Greewich SR1：Greewich版本的第一个bug修复版

​	Greewich RELEASE :Greewich版本的第一个正式版

​     Greewich RELEASE -->第一个正式版本-->发现bug --> SR1版本 -->SR2版本

*Spring Cloud生命周期

​	*版本发布规划

​	*版本发布记录

​	*  版本终止声明    

*Spring Boot、Spring Cloud、Spring Cloud Alibaba的兼容性关系

![image-20210326153358396](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210326153358396.png)

*生产环境怎么选择版本？

​	*坚决不用非稳定版本/end-of-life版本

​	*尽量用最新一代

​	   1.xxx.RELEASE版本缓一缓

​	   2.SR2之后可以大规模使用

## 服务提供者与服务消费者

服务提供者：服务的被调用方（即：为其他微服务提供接口的微服务）

服务消费者：服务的调用方（即：调用其他微服务接口的微服务）

## 剖析服务发现原理

![image-20210326160158951](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210326160158951.png)

有一个重要的心跳机制

# 什么是Nacos，引入Nacos后架构演进

![image-20210326160406523](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210326160406523.png)

如上图，**nacos是一个服务发现组件也是一个配置服务器**

![image-20210326160513867](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210326160513867.png)

搭建Nacos Server

*下载Nacos

​	执行文档：https://nacos.io/zh-cn/docs/quick-start.html

​	通过bin目录下执行：startup.cmd -m standalone

启动nacos，输入账号：nacos，密码：nacos。进入到

![image-20210327085009514](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210327085009514.png)



springcloudAlibaba依赖命名规则

  <!--spring-boot-starter-xxxx-->
        <!--xxxx-spring-boot-starter-->
        <!--spring-cloud-starter-{spring cloud子项目的名称}-[{模块名称}]-->
        <!--feign spring-cloud-starter-openfeign-->
        <!--sentinel spring-cloud-starter-alibaba-sentinel-->

## 将应用注册到Nacos

加依赖：

```xml
<dependency>
<groupId>org.springframework.cloud</groupId>
<artifactId>spring-cloud-starter-alibaba-nacos-discovery</artifactId>
</dependency>
```

```yaml
cloud:
  nacos:
    discovery:
      # 指定nacos server的地址
      server-addr: localhost:8848
#nacos的配置   
application:
    # 服务名称尽量用-，不要用_,更不要用特殊字符
    name: user-center
```

![image-20210327093431109](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210327093431109.png)

成功注册

![image-20210327093829501](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210327093829501.png)

```java
/**
 * 测试：服务发现，证明内容中心总能找到用户中心
 *
 * @return 用户中心所有实例的地址信息
 */
@GetMapping("test2")
public List<ServiceInstance> getInstances() {
    // 查询指定服务的所有实例的信息
    // consul/eureka/zookeeper...
    return this.discoveryClient.getInstances("user-center");
}
```

![image-20210327095725906](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210327095725906.png)

这是同时启动多个用户中心

## Nacos服务发现的领域模型

### 领域模型有哪些、作用是什么？

*Namespace:实现隔离，默认pubic

![image-20210329091452715](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210329091452715.png)

*Group：不同微服务可以分到一个组，默认DEFAULT_GROUP(现阶段不太适用了)

*Service：微服务

*Cluster：对指定微服务的一个虚拟划分，默认DEFAULT

*Instance:微服务实例

### 如何配置？

```yaml
# 指定namespace
# namespace: 115d6850-5837-4761-8762-98a05a0248ff
# 使用nacoa分配的uuid
# 指定集群名称
# cluster-name: NJ
```

## Nacos元数据

### 是什么？

*Nacos数据（如配置和服务）描述信息，如服务版本、权重、容灾策略、负载均衡策略、鉴权配置、各种自定义标签 (label)，从作用范围来看，分为服务级别的元信息、集群的元信息及实例的元信息。

*级别：【服务级别、集群级别、**实例级别**】

作用是什么？

*提供描述信息

*让微服务调用更加灵活

​	例如:微服务版本控制

如何配置？

*控制台设置

*配置文件指定

```yaml
#配置文件指定
metadata:
  instance: c
  haha: hehe
  version: V1
```

# 如何实现负载均衡？

*目前已经实现让A总能找到B，如何实现负载均衡？

![image-20210329094111417](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210329094111417.png)

负载均衡的两种方式

***服务器负载均衡**

![image-20210329094222670](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210329094222670.png)

***客户端侧负载均衡**

![image-20210329094441045](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210329094441045.png)

## 实现一个客户端侧负载均衡器

*随机选择实例

```java
List<ServiceInstance> instances = discoveryClient.getInstances("user-center");
List<String> targetURLS = instances.stream()
        .map(instance-> instance.getUri().toString()+"/users/{id}")
        .collect(Collectors.toList());

int i = ThreadLocalRandom.current().nextInt(targetURLS.size());
```

![image-20210329095737638](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210329095737638.png)

随机访问，实现了一个简单负载均衡

## 使用Ribbon实现负载均衡

### Ribbon是什么

Netflix开源的客户端侧负载均衡器

### 引入Ribbon后的架构演进

![image-20210329100259514](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210329100259514.png)

### 整合Ribbon实现负载均衡

1.加依赖，nacos包含了ribbon的依赖，不需要加依赖

2.写注解@LoadBalanced

```java
@Bean
@LoadBalanced
public RestTemplate restTemplate(){
    return new RestTemplate();
}
```

3.写配置，没有配置

```java
 UserDTO userDTO = this.restTemplate.getForObject(
                "http://user-center/users/{id}",
                UserDTO.class, userId
     );
```

## Ribbon的组成

![image-20210329102124113](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210329102124113.png)

不满意这些接口，可以重写覆盖。IRule最重要的组成

## Ribbon内置的负载均衡规则

![image-20210329102752500](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210329102752500.png)

## Ribbon细粒度配置自定义

1.Java代码配置

```java
@Configuration
@RibbonClient(name = "user-center",configuration = RibbonConfiguration.class)
public class UserCenterRibbonConfiguration {
}

```

2.用配置属性配置

```yaml
user-center:
  ribbon:
    NFLoadBalancerRuleClassName: com.netflix.loadbalancer.RandomRule
```

3.最佳实践总结

*尽量使用属性配置，属性方式实现不了的情况下再考虑用代码配置

*在同一个微服务内**尽量保持单一性**，比如统一使用属性配置，不要两种方式混用，增加定位代码的复杂性

代码配置方式和属性配置方式比较

​			代码配置方式                             属性配置方式

优点     基于代码，更加灵活。               易上手，配置更加直观，线上修改无需重新打包，发布优先级更高

缺点： 有小坑（父子上下文），线上修改得重新打包，发布。     极端场景下没有代码配置方式灵活

## Ribbon全局配置

方式一：让ComponentScan上下文重叠（**强烈不建议使用**）

这中实现了全局的配置

```java
//实现了全局的配置
@Configuration
@RibbonClients(defaultConfiguration = RibbonConfiguration.class)
public class UserCenterRibbonConfiguration {
}
```

## Ribbon支持的配置项

## Ribbon的饥饿加载

Ribbon默认是懒加载的，通过配置文件修改

```yaml
ribbon:
  eager-load:
    enabled: true
    clients: user-center
```

## 拓展Ribbon-权重支持

![image-20210329135750597](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210329135750597.png)

Ribbon规则不支持Nacos权重的

扩展Ribbon

```java
 public Server choose(Object o) {
        try {
            BaseLoadBalancer loadBalancer = (BaseLoadBalancer) this.getLoadBalancer();
//        log.info("lb = {}", loadBalancer);

            // 想要请求的微服务的名称
            String name = loadBalancer.getName();

            // 拿到服务发现的相关API
            NamingService namingService = nacosDiscoveryProperties.namingServiceInstance();

            // nacos client自动通过基于权重的负载均衡算法，给我们选择一个实例。
            Instance instance = namingService.selectOneHealthyInstance(name);

            log.info("选择的实例是：port = {}, instance = {}", instance.getPort(), instance);
            return new NacosServer(instance);
        } catch (NacosException e) {
            return null;
        }
    }
```

## 扩展Ribbon支持Nacos权重的三种方式

http://www.itmuch.com/spring-cloud-alibaba/ribbon-nacos-weight/

## 拓展Ribbon-同集群优先

**现在ribbon集成了同集群优先访问**

```java
@Override
public Server choose(Object key) {
    try {
        // 拿到配置文件中的集群名称 BJ
        String clusterName = nacosDiscoveryProperties.getClusterName();

        BaseLoadBalancer loadBalancer = (BaseLoadBalancer) this.getLoadBalancer();
        // 想要请求的微服务的名称
        String name = loadBalancer.getName();

        // 拿到服务发现的相关API
        NamingService namingService = nacosDiscoveryProperties.namingServiceInstance();

        // 1. 找到指定服务的所有实例 A
        List<Instance> instances = namingService.selectInstances(name, true);

        // 2. 过滤出相同集群下的所有实例 B
        List<Instance> sameClusterInstances = instances.stream()
            .filter(instance -> Objects.equals(instance.getClusterName(), clusterName))
            .collect(Collectors.toList());

        // 3. 如果B是空，就用A
        List<Instance> instancesToBeChosen = new ArrayList<>();
        if (CollectionUtils.isEmpty(sameClusterInstances)) {
            instancesToBeChosen = instances;
            log.warn("发生跨集群的调用, name = {}, clusterName = {}, instances = {}",
                name,
                clusterName,
                instances
            );
        } else {
            instancesToBeChosen = sameClusterInstances;
        }
        // 4. 基于权重的负载均衡算法，返回1个实例
        Instance instance = ExtendBalancer.getHostByRandomWeight2(instancesToBeChosen);
        log.info("选择的实例是 port = {}, instance = {}", instance.getPort(), instance);

        return new NacosServer(instance);
    } catch (NacosException e) {
        log.error("发生异常了", e);
        return null;
    }
}
```

## 拓展Ribbon-基于元数据的版本控制

至此，已经实现了

- 优先调用同集群下的实例
- 实现基于权重配置的负载均衡

但实际项目，我们可能还会有这样的需求：

一个微服务在线上可能多版本共存，例如：

- 服务提供者有两个版本：v1、v2
- 服务消费者也有两个版本：v1、v2

v1/v2是不兼容的。服务消费者v1只能调用服务提供者v1；消费者v2只能调用提供者v2。如何实现呢？

下面围绕该场景，实现微服务之间的版本控制。

### 元数据

元数据就是一堆的描述信息，以map存储。举个例子：

```yaml
spring:
  cloud:
    nacos:
        metadata: 
          # 自己这个实例的版本
          version: v1
          # 允许调用的提供者版本
          target-version: v1
```

### 需求分析

我们需要实现的有两点：

- 优先选择同集群下，符合metadata的实例
- 如果同集群加没有符合metadata的实例，就选择所有集群下，符合metadata的实例

### 写代码

```java
@Slf4j
public class NacosFinalRule extends AbstractLoadBalancerRule {
    @Autowired
    private NacosDiscoveryProperties nacosDiscoveryProperties;

    @Override
    public Server choose(Object key) {
        // 负载均衡规则：优先选择同集群下，符合metadata的实例
        // 如果没有，就选择所有集群下，符合metadata的实例

        // 1. 查询所有实例 A
        // 2. 筛选元数据匹配的实例 B
        // 3. 筛选出同cluster下元数据匹配的实例 C
        // 4. 如果C为空，就用B
        // 5. 随机选择实例
        try {
            String clusterName = this.nacosDiscoveryProperties.getClusterName();
            String targetVersion = this.nacosDiscoveryProperties.getMetadata().get("target-version");

            DynamicServerListLoadBalancer loadBalancer = (DynamicServerListLoadBalancer) getLoadBalancer();
            String name = loadBalancer.getName();

            NamingService namingService = this.nacosDiscoveryProperties.namingServiceInstance();

            // 所有实例
            List<Instance> instances = namingService.selectInstances(name, true);

            List<Instance> metadataMatchInstances = instances;
            // 如果配置了版本映射，那么只调用元数据匹配的实例
            if (StringUtils.isNotBlank(targetVersion)) {
                metadataMatchInstances = instances.stream()
                        .filter(instance -> Objects.equals(targetVersion, instance.getMetadata().get("version")))
                        .collect(Collectors.toList());
                if (CollectionUtils.isEmpty(metadataMatchInstances)) {
                    log.warn("未找到元数据匹配的目标实例！请检查配置。targetVersion = {}, instance = {}", targetVersion, instances);
                    return null;
                }
            }

            List<Instance> clusterMetadataMatchInstances = metadataMatchInstances;
            // 如果配置了集群名称，需筛选同集群下元数据匹配的实例
            if (StringUtils.isNotBlank(clusterName)) {
                clusterMetadataMatchInstances = metadataMatchInstances.stream()
                        .filter(instance -> Objects.equals(clusterName, instance.getClusterName()))
                        .collect(Collectors.toList());
                if (CollectionUtils.isEmpty(clusterMetadataMatchInstances)) {
                    clusterMetadataMatchInstances = metadataMatchInstances;
                    log.warn("发生跨集群调用。clusterName = {}, targetVersion = {}, clusterMetadataMatchInstances = {}", clusterName, targetVersion, clusterMetadataMatchInstances);
                }
            }

            Instance instance = ExtendBalancer.getHostByRandomWeight2(clusterMetadataMatchInstances);
            return new NacosServer(instance);
        } catch (Exception e) {
            log.warn("发生异常", e);
            return null;
        }
    }

    @Override
    public void initWithNiwsConfig(IClientConfig iClientConfig) {
    }
}
```

```java
负载均衡算法：
public class ExtendBalancer extends Balancer {
    /**
     * 根据权重，随机选择实例
     *
     * @param instances 实例列表
     * @return 选择的实例
     */
    public static Instance getHostByRandomWeight2(List<Instance> instances) {
        return getHostByRandomWeight(instances);
    }
}
```

## 深入理解Nacos Namespace

Nacos Namespace实现了服务的隔离，不在同一个命名空间，不能一起调用

# 使用Fegin实现远程HTTP调用

## 什么是Fegin

*Fegin是Netfilx开源的声明式HTTP客户端

*Github地址：https://github.com/openfegin/feign

## Feign的组成

![image-20210329153941194](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210329153941194.png)

## Feign细粒度配置自定义

### Java代码方式-指定日志级别

![image-20210329154831413](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210329154831413.png)

```yaml
logging:
  level:
    com.itmuch.contentcenter.feignclient.UserCenterFeignClient: debug
```

```java
/**
 *  feign的配置类
 *  这个类别加@Configuration注解了，否则必须挪到@ComponentScan能扫描的包以外
 */

public class UserCenterFeignConfiguration {
    @Bean
    public Logger.Level level(){
        // 让feign打印所有请求的细节
        return Logger.Level.FULL;
    }
```

### 配置属性方式 -属性方式

```yaml
feign:
  client:
    config:
      # 想要调用的微服务的名称
      user-center:
        loggerLevel: full
```

## Feign全局配置自定义

1.Java代码方式

方式一：让父子上下文ComponentScan重叠（**强烈不建议使用**）

方式二【唯一正确的途径】：

`@EnableFeignClients(defaultConfiguration=xxx.class)`

2.配置属性方式

```yaml
feign:
  client:
    config:
      # 全局配置
      default:
        loggerLevel: full
```

## Feign支持的配置项

*支持的配置项-代码方式

![image-20210329162505165](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210329162505165.png)

*支持的配置项-属性方式

![image-20210329162530004](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210329162530004.png)

## Feign配置最佳实践总结

*Ribbon配置 vs Feign配置

![image-20210329162848613](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210329162848613.png)

*Feign代码方式 vs 属性方式

![image-20210329163539972](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210329163539972.png)

*最佳实践总结

​	1.尽量使用属性配置，属性方式实现不了的情况再考虑用代码配置

​	2.在同一个微服务内**尽量保持单一性**，比如统一使用属性配置，不要两种方式混用，增加定位代码的复杂性

## Feign的继承

关于继承特性的争议

 *官方不建议使用（不符合微服务的解耦合），但开发者会大量使用

## Feign的多参数请求构造

*GET

*POST

```yaml
#解决两个Feign同名的问题
main:
  allow-bean-definition-overriding: true
```

# **如何使用Feign构造多参数的请求**

```
这是基于Spring Cloud Greenwich SR1，理论上支持Finchley及更高版本。
```

## GET请求多参数的URL

假设需请求的URL包含多个参数，例如`http://microservice-provider-user/get?id=1&username=张三` ，该如何使用Feign构造呢？

我们知道，Spring Cloud为Feign添加了Spring MVC的注解支持，那么不妨按照Spring MVC的写法尝试一下：

```java
@FeignClient("microservice-provider-user")
public interface UserFeignClient {
  @RequestMapping(value = "/get", method = RequestMethod.GET)
  public User get0(User user);
}
```

```java
然而，这种写法并不正确，控制台会输出类似如下的异常。
feign.FeignException: status 405 reading UserFeignClient#get0(User); content:
{"timestamp":1482676142940,"status":405,"error":"Method Not Allowed","exception":"org.springframework.web.HttpRequestMethodNotSupportedException","message":"Request method 'POST' not supported","path":"/get"}
```

```
由异常可知，尽管我们指定了GET方法，Feign依然会使用POST方法发送请求。于是导致了异常。正确写法如下
```

```java
方法一[推荐]
@FeignClient("microservice-provider-user")
public interface UserFeignClient {
  @GetMapping("/get")
  public User get0(@SpringQueryMap User user);
}
```

```java
方法二[推荐]
@FeignClient(name = "microservice-provider-user")
public interface UserFeignClient {
  @RequestMapping(value = "/get", method = RequestMethod.GET)
  public User get1(@RequestParam("id") Long id, @RequestParam("username") String username);
}
```

```java
这是最为直观的方式，URL有几个参数，Feign接口中的方法就有几个参数。使用@RequestParam注解指定请求的参数是什么。
```

## Feign脱离Ribbon使用

```java
// 脱离ribbon的使用
@FeignClient(name = "baidu", url = "http://www.baidu.com")
public interface TestBaiduFeignClient {
    @GetMapping("")
    String index();
}
```

## RestTemplate vs Feign

![image-20210329175505605](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210329175505605.png)

### 如何选择？

*原则：尽量使用Fegin，杜绝使用RestTemplate

*合理选择

## Fegin性能优化

*连接池【大概提升15%左右】

1.加依赖

```xml
<dependency>
    <groupId>io.github.openfeign</groupId>
    <artifactId>feign-httpclient</artifactId>
</dependency>
```

2.写配置

```yaml
# 让feign使用apache httpclient做请求；而不是默认的urlconnection
httpclient:
  enabled: true
  # feign的最大连接数
  max-connections: 200
    # feign单个路径的最大连接数
  max-connections-per-route: 50
```

*日志级别

建议把日志级别设置成basic，不建议full

## Feign常见问题总结

```xml
基于Spring Clou Greenwich SR1，理论支持Spring Cloud Finchley及更高版本。
```

```
一、使用案例
如何使用Feign构造多参数的请求
使用Spring Cloud Feign上传文件
使用Feign实现Form表单提交
```

二、FeignClient接口如使用`@PathVariable` ，必须指定value属性

```java
代码示例：
@FeignClient("microservice-provider-user")
public interface UserFeignClient {
  @RequestMapping(value = "/simple/{id}", method = RequestMethod.GET)
  public User findById(@PathVariable("id") Long id);
  ...
}
```

在一些早期版本中，其中的`@PathVariable("id")` 中的"id"，也就是value属性，必须指定，不能省略。

```java
三、Java代码自定义Feign Client的注意点与坑
代码示例：
@FeignClient(name = "microservice-provider-user", configuration = UserFeignConfig.class)
public interface UserFeignClient {
  @GetMapping("/users/{id}")
  User findById(@PathVariable("id") Long id);
}

/**
 * 该Feign Client的配置类，注意：
 * 1. 该类可以独立出去；
 * 2. 该类上也可添加@Configuration声明是一个配置类；
 * 配置类上也可添加@Configuration注解，声明这是一个配置类；
 * 但此时千万别将该放置在主应用程序上下文@ComponentScan所扫描的包中，
 * 否则，该配置将会被所有Feign Client共享，无法实现细粒度配置！
 * 个人建议：像我一样，不加@Configuration注解
 *
 * @author zhouli
 */
class UserFeignConfig {
  @Bean
  public Logger.Level logger() {
    return Logger.Level.FULL;
  }
}
```

配置类上也可添加`@Configuraiton` 注解，声明这是一个配置类；但此时千万别将该放置在主应用程序上下文`@ComponentScan` 所扫描的包中，**否则，该配置将会被所有Feign Client共享**（相当于变成了通用配置，其实本质还是Spring父子上下文扫描包重叠导致的问题），无法实现细粒度配置！

**个人建议**：像我一样，不加@Configuration注解，省得进坑。

**最佳实践**：尽量用配置属性自定义Feign的配置！！！

四、`@FeignClient` 注解属性

```java
@FeignClient(name = "microservice-provider-user")
```

在早期的Spring Cloud版本中，无需提供name属性，从Brixton版开始，@FeignClient必须提供name属性，否则应用将无法正常启动！

另外，name、url等属性支持占位符。例如：

```java
@FeignClient(name = "${feign.name}", url = "${feign.url}")
```

```java
五、类级别的@RequestMapping会被Spring MVC加载
@RequestMapping("/users")
@FeignClient(name = "microservice-user")
public class TestFeignClient {
    // ...
}
```

类上的`@RequestMapping` 注解也会被Spring MVC加载。**该问题现已经被解决**，早期的版本有两种解决方案：

**方案1**：不在类上加`@RequestMapping` 注解；

**方案2**：添加如下代码：

```java
@Configuration
@ConditionalOnClass({ Feign.class })
public class FeignMappingDefaultConfiguration {
    @Bean
    public WebMvcRegistrations feignWebRegistrations() {
        return new WebMvcRegistrationsAdapter() {
            @Override
            public RequestMappingHandlerMapping getRequestMappingHandlerMapping() {
                return new FeignFilterRequestMappingHandlerMapping();
            }
        };
    }

    private static class FeignFilterRequestMappingHandlerMapping extends RequestMappingHandlerMapping {
        @Override
        protected boolean isHandler(Class<?> beanType) {
            return super.isHandler(beanType) && !beanType.isInterface();
        }
    }
}
```

六、首次请求失败
http://www.itmuch.com/spring-cloud-feign-ribbon-first-request-fail/

七、如需产生Hystrix Stream监控信息，需要做一些额外操作
eign本身已经整合了Hystrix，可直接使用@FeignClient(value = "microservice-provider-user", fallback = XXX.class) 来指定fallback类，fallback类继承@FeignClient所标注的接口即可。

但是假设如需使用Hystrix Stream进行监控，默认情况下，访问http://IP:PORT/actuator/hystrix.stream 是会返回404，这是因为Feign虽然整合了Hystrix，但并没有整合Hystrix的监控。如何添加监控支持呢？需要以下几步:

```xml
第一步：添加依赖，示例：
<!-- 整合hystrix，其实feign中自带了hystrix，引入该依赖主要是为了使用其中的hystrix-metrics-event-stream，用于dashboard -->
<dependency>
  <groupId>org.springframework.cloud</groupId>
  <artifactId>spring-cloud-starter-hystrix</artifactId>
</dependency>
```

```java
第二步：在启动类上添加`@EnableCircuitBreaker` 注解，示例：
@SpringBootApplication
@EnableFeignClients
@EnableDiscoveryClient
@EnableCircuitBreaker
public class MovieFeignHystrixApplication {
  public static void main(String[] args) {
    SpringApplication.run(MovieFeignHystrixApplication.class, args);
  }
}
```

```yaml
第三步：在application.yml中添加如下内容，暴露hystrix.stream端点：
management:
  endpoints:
    web:
      exposure:
        include: 'hystrix.stream'
```

这样，访问任意Feign Client接口的API后，再访问`http://IP:PORT/actuator/hystrix.stream` ，就会展示一大堆Hystrix监控数据了。

## 引入了Fegin的架构图![image-20210329182332241](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210329182332241.png)

# 雪崩效应（级联失效、级联故障）

![image-20210330084955189](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210330084955189.png)

##   常见容错方案

 1.超时（释放够快，就不容易宕机）

 2.限流（上层来的流量减少）

 3.仓壁模式（线程池）

 4.断路器模式

​		断路器三泰转换

![image-20210330090144238](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210330090144238.png)

# 使用Sentinel实现容错

## Sentinel是什么

轻量级的流量控制、熔断降级Java库

## 整合Sentinel

加依赖

```xml
<dependency>
    <groupId>org.springframework.cloud</groupId>
    <artifactId>spring-cloud-starter-alibaba-sentinel</artifactId>
</dependency>
```

无注解，无配置

```yaml
management:
  endpoints:
    web:
      exposure:
        include: '*'
#暴露Sentinel端点
```

## Sentinel控制台

*搭建Sentinel控制台

启动方式![image-20210330095200926](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210330095200926.png)

![image-20210330095130611](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210330095130611.png)

*整合应用&控制台

```yaml
sentinel:
  transport:
    #指定sentinel控制台的地址
    dashboard: localhost:8080
```

## sentinel流控规则

直接、关联、链路

关联：当关联资源达到阈值，就限流自己

链路：只记录指定链路上的流量

快速失败：直接失败，抛异常

Warm Up：根据codeFactor（默认3）的值，从阈值/codeFactor，经过预热时长那个，才到达设置的QPS阈值

排队等待：匀速排队，让请求以匀速的速度通过，阈值类型必须设成QPS，否则无效

### 降级规则详解

降级RT：平均响应时间（秒级统计）超出阈值&&在时间窗口内通过的请求 >= 5 ---->触发降级（断路器打开）----->时间窗口结束 -----> 关闭降级

### 降级-RT-注意点

RT默认最大4900ms

​	通过-Dcsp.sentinel.statistic.max.rt=xxx修改

### 降级-异常比例

![image-20210330105521420](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210330105521420.png)

### 降级-异常数

![image-20210330105605199](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210330105605199.png)

### 降级-异常数-注意点

1.时间窗口<60秒可能会出问题

降级--断路器三态

1.Sentinel的断路器没有半开状态

## 热点规则详解

![image-20210330111451151](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210330111451151.png)

### 热点-注意点

1.参数必须是基本类型或者String

## 系统规则详解

系统-Load

1.当系统load1（1分钟的load）超过阈值，且并发线程数超过系统容量是触发，建议设置为CPU核心数*2.5.（仅对Linux/unix-like机器生效）

2.系统容量 = maxQps * minRt

​	maxQps：秒级统计出来的最大QPS

​	minRt：秒级统计出来的最小响应时间

### 系统-RT、线程数、入口QPS

RT：所有入口流量的平均RT达到阈值触发

线程数：所有入口流量的并发线程数达到阈值触发

入口QPS：所有入口流量的QPS达到阈值触发

## 授权规则详解

## 代码配置规则

！参考：https://www.imooc.com/article/289562

## Sentinel与控制台通信原理剖析

1.看着他说如何获取到微服务的监控信息的？

![image-20210330113858915](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210330113858915.png)



2.用控制台配置规则时，控制台是如何将规则发送到各个微服务的呢？

## 控制台相关配置项

### 应用端连接控制台配置项

![image-20210330114309008](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210330114309008.png)

### 控制台配置项

![image-20210330114344262](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210330114344262.png)

## Sentinel API

1.Sphu

2.Tracer

3.ContextUtil

## @SentinelResource注解

| 属性                      | 作用                                                         | 是否必须  |
| :------------------------ | :----------------------------------------------------------- | :-------- |
| value                     | 资源名称                                                     | 是        |
| entryType                 | entry类型，标记流量的方向，取值IN/OUT，默认是OUT             | 否        |
| blockHandler              | 处理BlockException的函数名称。函数要求： 1. 必须是 `public` 2.返回类型与原方法一致 3. 参数类型需要和原方法相匹配，**并在最后加 `BlockException` 类型的参数**。 4. 默认需和原方法在同一个类中。若希望使用其他类的函数，可配置 `blockHandlerClass` ，并指定blockHandlerClass里面的方法。 | 否        |
| blockHandlerClass         | 存放blockHandler的类。对应的处理函数必须static修饰，否则无法解析，其他要求：同blockHandler。 | 否        |
| fallback                  | 用于在抛出异常的时候提供fallback处理逻辑。fallback函数可以针对所有类型的异常（除了 `exceptionsToIgnore` 里面排除掉的异常类型）进行处理。函数要求： 1. 返回类型与原方法一致 2. 参数类型需要和原方法相匹配，**Sentinel 1.6开始，也可在方法最后**加 `Throwable` 类型的参数。 3.默认需和原方法在同一个类中。若希望使用其他类的函数，可配置 `fallbackClass` ，并指定fallbackClass里面的方法。 | 否        |
| fallbackClass【1.6】      | 存放fallback的类。对应的处理函数必须static修饰，否则无法解析，其他要求：同fallback。 | 否        |
| defaultFallback【1.6】    | 用于通用的 fallback 逻辑。默认fallback函数可以针对所有类型的异常（除了 `exceptionsToIgnore` 里面排除掉的异常类型）进行处理。若同时配置了 fallback 和 defaultFallback，以fallback为准。函数要求： 1. 返回类型与原方法一致 2. 方法参数列表为空，**或者有一个** `Throwable` 类型的参数。 3. 默认需要和原方法在同一个类中。若希望使用其他类的函数，可配置 `fallbackClass` ，并指定 `fallbackClass` 里面的方法。 | 否        |
| exceptionsToIgnore【1.6】 | 指定排除掉哪些异常。排除的异常不会计入异常统计，也不会进入fallback逻辑，而是原样抛出。 | 否        |
| exceptionsToTrace         | 需要trace的异常                                              | Throwable |

> **TIPS**
>
> - 1.6.0 之前的版本 fallback 函数只针对降级异常（`DegradeException`）进行处理，**不能针对业务异常进行处理**。
> - 若 blockHandler 和 fallback 都进行了配置，则被限流降级而抛出 `BlockException` 时只会进入 `blockHandler` 处理逻辑。若未配置 `blockHandler`、`fallback` 和 `defaultFallback`，则被限流降级时会将 `BlockException` **直接抛出**。
> - 从 1.4.0 版本开始，注解方式定义资源支持自动统计业务异常，无需手动调用 `Tracer.trace(ex)` 来记录业务异常。Sentinel 1.4.0 以前的版本需要自行调用 `Tracer.trace(ex)` 来记录业务异常。

## RestTemplate整合Sentinel

@SentinelRestTemplate

开关：resttemplate.sentinel.enabled

```yaml
resttemplate:
  sentinel:
    # 关闭@SentinelRestTemplate注解
    enabled: false
```

## Feign整合Sentinel

feign.sentinel.enabled = true

## Sentinel使用总结

![image-20210330142854058](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210330142854058.png)

## 规则持久化

1.拉模式  https://www.imooc.com/article/289402

**2.推模式**  https://www.imooc.com/article/289464

## 如何在生产环境使用sentinel

1.推拉模式持久化规则

​	*推模式更佳

2.AHAS

​	*开通地址：https://ahas.console.aliyun.com/

​	*开通说明：https://help.aliyun.com/document_detail/90323.html

## 集群流控

![image-20210330151308317](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210330151308317.png)

集群限流环境搭建：https://www.jianshu.com/p/a52bf4073873

sentinel配置项总结：https://www.imooc.com/article/289562

# Spring实现异步的方法

*AsyncRestTemplate

*@Async注解

*WebClient

***MQ**

# MQ适用场景

1.异步处理

2.流量削峰填谷

3.解耦微服务

# MQ的选择

流行的mq：Kafka、RabbitMQ、RocketMQ、ActiveMQ。

参考：https://www.imooc.com/article/290040

![mq-pk](https://img1.sycdn.imooc.com/5d3d9ddf0001a33a09742697.jpg)

# 搭建RocketMQ

参考：https://www.imooc.com/article/290089

## windows下RocketMQ安装部署

：--->    https://www.jianshu.com/p/4a275e779afa

## 搭建RocketMQ控制台。

```xml
一、下载代码
# 方式一、git下载，执行如下命令
git clone https://github.com/apache/rocketmq-externals.git

# 方式二、直接下载，访问如下地址即可
https://github.com/apache/rocketmq-externals/archive/master.zip

二、修改控制台代码
找到rocketmq-console/src/main/resources/application.properties 根据需求，修改配置

# 管理后台访问上下文路径，默认为空
# 如果填写，需写成/xxx的形式，例如/console
server.contextPath=

# 控制台的端口
server.port=8080

...

# if this value is empty,use env value rocketmq.config.namesrvAddr  NAMESRV_ADDR | now, you can set it in ops page.default localhost:9876
# Name Server地址
rocketmq.config.namesrvAddr=

# if you use rocketmq version < 3.5.8, rocketmq.config.isVIPChannel should be false.default true
rocketmq.config.isVIPChannel=

#rocketmq-console's data path:dashboard/monitor
rocketmq.config.dataPath=/tmp/rocketmq-console/data

#set it false if you don't want use dashboard.default true
rocketmq.config.enableDashBoardCollect=true

#set the message track trace topic if you don't want use the default one
rocketmq.config.msgTrackTopicName=

rocketmq.config.ticketKey=ticket

#Must create userInfo file: ${rocketmq.config.dataPath}/users.properties if the login is required
rocketmq.config.loginRequired=false

只修改了如下两项：
# console端口
server.port=17890
# name server地址
# 也可以不修改，在启动完console后，在控制台导航栏 - 运维 - NameSvrAddrList一栏设置
rocketmq.config.namesrvAddr=localhost:9876

2.2 修改依赖
找到

<rocketmq.version>4.4.0</rocketmq.version>

修改为
<rocketmq.version>你的RocketMQ版本</rocketmq.version>

使用的是RocketMQ 4.5.1，故而改为

<rocketmq.version>4.5.1</rocketmq.version>

2.3 修改代码
修改pom.xml后，org.apache.rocketmq.console.service.impl.MessageServiceImpl#queryMessageByTopic编译会报错，所以需要解决一下。将DefaultMQPullConsumer consumer = new DefaultMQPullConsumer(MixAll.TOOLS_CONSUMER_GROUP, null);

改为：
RPCHook rpcHook = null;
DefaultMQPullConsumer consumer = new DefaultMQPullConsumer(MixAll.TOOLS_CONSUMER_GROUP, rpcHook);
即可。
2.4 打包构建
# 切换到代码根目录
cd rocketmq-externals

# 切换到控制台目录
cd rocketmq-console

# 构建
mvn clean package -DskipTests

具体参考：https://www.imooc.com/article/290092

```


成功后效果![image-20210331094955209](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210331094955209.png)

## RocketMQ使用文档

### 运维页面

1.可以修改这个服务使用的navesvr的地址

2.可以修改这个服务是否使用VIPChannel(如果你的mq server版本小于3.5.8，请设置不使用)

### 驾驶舱

1.查看broker的消息量（总量/5分钟图）

2.查看单一主题的消息量（总量/趋势图）

### 集群页面

1.查看集群的分布情况

​	cluster与broker关系

​	broker

2.查看broker具体信息/运行信息

3.查看broker配置信息

### 主题页面

1.展示所有的主题，可以通过搜索框进行过滤

2.筛选 普通/重试/死信 主题

3.添加/更新主题

​	clusterName 创建在哪几个cluster上

​	brokerName 创建在哪几个broker上

​	topicName 主题名

​	writeQueueNums 写队列数量

​	readQueueNums 读队列数量

​	perm //2是写 4是读 6是读写

4.状态 查询消息投递状态（投递到哪些broker/哪些queue/多少量等）

5.路由 查看消息的路由（现在你发这个主题的消息会发往哪些broker，对应broker的queue信息）

6.CONSUMER管理（这个topic都被哪些group消费了，消费情况何如）

7.topic配置（查看变更当前的配置）

8.发送消息（向这个主题发送一个测试消息）

9.重置消费位点(分为在线和不在线两种情况，不过都需要检查重置是否成功)

10.删除主题 （会删除掉所有broker以及namesvr上的主题配置和路由信息）

### 消费者页面

1.展示所有的消费组，可以通过搜索框进行过滤

2.刷新页面/每隔五秒定时刷新页面

3.按照订阅组/数量/TPS/延迟 进行排序

4.添加/更新消费组

​	clusterName 创建在哪几个集群上

​	brokerName 创建在哪几个broker上

​	groupName 消费组名字

​	consumeEnable //是否可以消费 FALSE的话将无法进行消费

​	consumeBroadcastEnable //是否可以广播消费

​	retryQueueNums //重试队列的大小

​	brokerId //正常情况从哪消费

​	whichBrokerWhenConsumeSlowly//出问题了从哪消费

5.终端 在线的消费客户端查看，包括版本订阅信息和消费模式

6.消费详情 对应消费组的消费明细查看，这个消费组订阅的所有Topic的消费情况，每个queue对应的消费client查看（包括Retry消息）

7.配置 查看变更消费组的配置

8.删除 在指定的broker上删除消费组

### 发布管理页面

1.通过Topic和Group查询在线的消息生产者客户端

​	信息包含客户端主机 版本

### 消息查询页面

1.根据Topic和时间区间查询 *由于数据量大 做多只会展示2000条，多的会被忽略

2.根据Topic和Key进行查询

​	最多只会展示64条

3.根据消息主题和消息Id进行消息的查询

4.消息详情可以展示这条消息的详细信息，查看消息对应到具体消费组的消费情况（如果异常，可以查看具体的异常信息）。可以向指定的消费组重发消息。

## RocketMQ的术语与概念

1.Topic(主题） 一类消息的集合，RocketMQ的基本订阅单位

2.消息模型：Producer(生产者，生产消息） Broker(消息代理，存储消息，转发消息） Consumer(消费者，消费消息）

3.部署机构：NameServer(名字服务）生产者/消费者通过名字服务查找各自主题相应的BrokerIp列表（类似与服务发现组件nacos)

BrokerServer(代理服务器）消息中转角色 负责存储消息 转发消息

4.消费模式：Pull Consumer(拉取式消费）应用调用Consumer的拉取信息方法从Broker Server拉取消息

Push Consumer(推动式消费）Broker收到消息后主动推送给消费端，该模式实时性较高

5:Group(组）Producer Group(生产者组）同一类Producer的集合，这类Producer发送同一类消息

6:消息传播模式：Clustering(集群）相同Consumer Group的每个Consumer实例平均分摊消息

Broadcasting(广播） 相同Consumer Group的每个Consumer实例都接受全量的消息

7：消息类型：普通消息、顺序消息、定时/延时消息、事务消息

## RocketMQ进阶

## Spring消息编程模型：编写生产者

加依赖

```xml
<dependency>
    <groupId>org.apache.rocketmq</groupId>
    <artifactId>rocketmq-spring-boot-starter</artifactId>
    <version>2.0.3</version>
</dependency>
```

```yaml
rocketmq:
  name-server: 127.0.0.1:9876
  producer:
    group: test-group
  # 注意：必须指定group
```

在MQ控制台可以看到生产成功

![image-20210331134246576](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210331134246576.png)

不同MQ的使用

1.RocketMQ：RocketMQTemplate

2.ActiveMQ/Artemis：JmsTemplate

3.RabbitMQ：AmqpTemplate

4.Kafka：KafkaTemplate

## Spring消息编程模型：编写消费者

1.RocketMQ：RocketMQMessageListener

2.ActiveMQ/Artemis：JmsListener

3.RabbitMQ：RabbitListener

4.Kafka：KafkaListener

## RocketMQ实现分布式事务

![image-20210331143349824](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210331143349824.png)

### 实现分布式事务：概念术语

1.半消息：暂时无法消费的消息。生产者将消息发送到了MQ server，但这个消息会被标记为“暂不能投递”状态；消费者不会去消费这条消息。

2.消息回查：网络断开或生产者重启可能导致丢失事务消息的第二次确认。当MQ Server发现消息长时间处于半消息状态时，将向消息生产者发生请求，询问该消息的最终状态（提交或回滚）。

### 实现分布式事务：消息三态

1.Commit：提交事务消息，消费者可以消费此消息

2.Rollback：回滚事务消息，broker会删除该消息，消费者不能消费

3.UNKNOWN：broker需要回查确认该消息的状态

### 分布式事务-编码实现

# RestTemplate 用法详解

微服务环境搭建，由 provider 提供服务， consumer 通过 DiscoveryClient 先去 eureka 上获取 provider 的服务的地址，获取到地址之后再去调用相关的服务。在服务的调用过程中，使用到了一个工具，叫做 RestTemplate，RestTemplate 是由 Spring 提供的一个 HTTP 请求工具

# Spring Cloud Stream是什么？

*一个用于构建消息驱动的微服务的框架

## Spring Cloud Stream 架构

![image-20210331154026120](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210331154026120.png)

## Spring Cloud Stream编程模型

1.Destination Binder（目标绑定器）

​	与消息中间件通信的组件

2.Destination Bindings（目标绑定）

​	Binding是连接应用程序跟消息中间件的桥梁，用于消息的消费和生产，由bnder创建

3.Message(消息)

![image-20210331154342521](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210331154342521.png)

# **Spring Cloud Stream实现消息过滤消费**

在实际项目中，我们可能需要实现消息消费的过滤。

举个例子：实现消息的分流处理：

生产者生产的消息，虽然消息体可能一样，但是header不一样。可编写两个或者更多的消费者，对不同header的消息做针对性的处理！

## condition

### 生产者

生产者设置一下header，比如my-header，值根据你的需要填写：

```java
@Autowired
private Source source;

public String testStream() {
  this.source.output()
    .send(
    MessageBuilder
    .withPayload("消息体")
    .setHeader("my-header","你的header")
    .build()
  );
  return "success";
}
```

### 消费者

```java
@Service
@Slf4j
public class TestStreamConsumer {
    @StreamListener(value = Sink.INPUT,condition = "headers['my-header']=='你的header'")
    public void receive(String messageBody) {
        log.info("通过stream收到了消息：messageBody ={}", messageBody);
    }
}
```

如代码所示，使用 `StreamListener` 注解的 `condition` 属性。当 `headers['my-header']=='你的header'` 条件满足，才会进入到方法体。

## Tags

> **TIPS**
>
> 该方式只支持RoketMQ，不支持Kafka/RabbitMQ

### 生产者

```java
@Autowired
private Source source;

public String testStream() {
  this.source.output()
    .send(
    MessageBuilder
    .withPayload("消息体")
    // 注意：只能设置1个tag
    .setHeader(RocketMQHeaders.TAGS, "tag1")
    .build()
  );
  return "success";
}
```

### 消费者

- 接口

  ```java
  public interface MySink {
      String INPUT1 = "input1";
      String INPUT2 = "input2";
  
      @Input(INPUT1)
      SubscribableChannel input();
  
      @Input(INPUT2)
      SubscribableChannel input2();
  }
  ```

- 注解

  ```
  @EnableBinding({MySink.class})
  ```

- 配置

  ```yaml
  spring:
    cloud:
      stream:
        rocketmq:
          binder:
            name-server: 127.0.0.1:9876
          bindings:
            input1:
              consumer:
                # 表示input2消费带有tag1的消息
                tags: tag1
            input2:
              consumer:
                # 表示input2消费带有tag2或者tag3的消息
                tags: tag2||tag3
        bindings:
          input1:
            destination: test-topic
            group: test-group1
          input2:
            destination: test-topic
            group: test-group2
  ```

- 消费代码

  ```java
  @Service
  @Slf4j
  public class MyTestStreamConsumer {
      /**
       * 我消费带有tag1的消息
       *
       * @param messageBody 消息体
       */
      @StreamListener(MySink.INPUT1)
      public void receive1(String messageBody) {
          log.info("带有tag1的消息被消费了：messageBody ={}", messageBody);
      }
  
      /**
       * 我消费带有tag1或者tag2的消息
       *
       * @param messageBody 消息体
       */
      @StreamListener(MySink.INPUT2)
      public void receive2(String messageBody) {
          log.info("带有tag2/tag3的消息被消费了：messageBody ={}", messageBody);
      }
  }
  ```

- 日志：

  ```shell
  2019-08-04 19:10:03.799  INFO 53760 --- [MessageThread_1] c.i.u.rocketmq.MyTestStreamConsumer      : 带有tag1的消息被消费了：messageBody =消息体
  ```

## Sql 92

> **TIPS**
>
> - 该方式只支持RoketMQ，不支持Kafka/RabbitMQ
> - **用了sql，就不要用Tag**

RocketMQ支持使用SQL语法过滤消息。官方文档：`http://rocketmq.apache.org/rocketmq/filter-messages-by-sql92-in-rocketmq/`

Spring Clous Stream RocketMQ也为此特性提供了支持。

### 开启SQL 92支持

默认情况下，RocketMQ的SQL过滤支持是关闭的，要想使用SQL 92过滤消息，需要：

- 在 `conf/broker.conf` 添加

  ```properties
  enablePropertyFilter = true
  ```

- 启动RocketMQ

  ```shell
  nohup sh bin/mqbroker -n localhost:9876 -c ./conf/broker.conf &
  ```

### 生产者

```java
@Autowired
private Source source;

public String testStream() {
  this.source.output()
    .send(
    MessageBuilder
    .withPayload("消息体")
    .setHeader("index", 1000)
    .build()
  );
  return "success";
}
```

### 消费者

- 接口

  ```java
  public interface MySink {
      String INPUT1 = "input1";
      String INPUT2 = "input2";
  
      @Input(INPUT1)
      SubscribableChannel input();
  
      @Input(INPUT2)
      SubscribableChannel input2();
  }
  ```

- 注解

  ```
  @EnableBinding({MySink.class})
  ```

- 配置

  ```yaml
  spring:
    cloud:
      stream:
        rocketmq:
          binder:
            name-server: 127.0.0.1:9876
          bindings:
            input1:
              consumer:
                sql: 'index < 1000'
            input2:
              consumer:
                sql: 'index >= 1000'
        bindings:
          input1:
            destination: test-topic
            group: test-group1
          input2:
            destination: test-topic
            group: test-group2
  ```

- 消费代码

  ```java
  @Service
  @Slf4j
  public class MyTestStreamConsumer {
      /**
       * 我消费带有tag1的消息
       *
       * @param messageBody 消息体
       */
      @StreamListener(MySink.INPUT1)
      public void receive1(String messageBody) {
          log.info("index > 1000的消息被消费了：messageBody ={}", messageBody);
      }
  
      /**
       * 我消费带有tag1或者tag2的消息
       *
       * @param messageBody 消息体
       */
      @StreamListener(MySink.INPUT2)
      public void receive2(String messageBody) {
          log.info("index <=1000 的消息被消费了：messageBody ={}", messageBody);
      }
  }
  ```

- 日志

  ```
  2019-08-04 19:58:59.787  INFO 56375 --- [MessageThread_1] c.i.u.rocket
  ```

# **Spring Cloud Stream错误处理**

#### 局部处理【通用】

配置：

```yaml
spring:
  cloud:
    stream:
      bindings:
        input:
          destination: my-destination
          group: my-group
        output:
          destination: my-destination
```

代码：

```java
@Slf4j
@SpringBootApplication
@EnableBinding({Processor.class})
@EnableScheduling
public class ConsumerApplication {
    public static void main(String[] args) {
        SpringApplication.run(ConsumerApplication.class, args);
    }

    @StreamListener(value = Processor.INPUT)
    public void handle(String body) {
        throw new RuntimeException("x");
    }

    @ServiceActivator(inputChannel = "my-destination.my-group.errors")
    public void handleError(ErrorMessage message) {
        Throwable throwable = message.getPayload();
        log.error("截获异常", throwable);

        Message<?> originalMessage = message.getOriginalMessage();
        assert originalMessage != null;

        log.info("原始消息体 = {}", new String((byte[]) originalMessage.getPayload()));
    }

    @Bean
    @InboundChannelAdapter(value = Processor.OUTPUT,
            poller = @Poller(fixedDelay = "1000", maxMessagesPerPoll = "1"))
    public MessageSource<String> test() {
        return () -> new GenericMessage<>("adfdfdsafdsfa");
    }
}
```

#### 全局处理【通用】

```java
@StreamListener(value = Processor.INPUT)
public void handle(String body) {
    throw new RuntimeException("x");
}

@StreamListener("errorChannel")
public void error(Message<?> message) {
    ErrorMessage errorMessage = (ErrorMessage) message;
    System.out.println("Handling ERROR: " + errorMessage);
}
```

### 系统处理

系统处理方式，因消息中间件不同而异。如果应用没有配置错误处理，那么error将会被传播给binder，binder将error回传给消息中间件。消息中间件可以丢弃消息、requeue（重新排队，从而重新处理）或将失败的消息发送给DLQ(死信队列)。

#### 丢弃

默认情况下，错误消息将被丢弃。虽然在某些情况下可以接受，但这种方式一般不适用于生产。

#### DLQ【RabbitMQ】

> **TIPS**
>
> - 虽然RocketMQ也支持DLQ，但目前RocketMQ控制台并不支持在界面上操作，将死信放回消息队列，让客户端重新处理。所以使用很不方便，而且用法也和本节有一些差异。
> - 如使用RocketMQ，建议参考上面【应用处理】一节的用法，也可额外订阅这个Topic `%DLQ%+consumerGroup`
> - 个人给RocketMQ控制台提的Issue：`https://github.com/apache/rocketmq/issues/1334`

配置：

```yaml
spring:
  cloud:
    stream:
      bindings:
        input:
          destination: my-destination
          group: my-group
        output:
          destination: my-destination
      rabbit:
        bindings:
          input:
            consumer:
              auto-bind-dlq: true
```

代码：

```java
@StreamListener(value = Processor.INPUT)
public void handle(String body) {
    throw new RuntimeException("x");
}

@Bean
@InboundChannelAdapter(value = Processor.OUTPUT,
        poller = @Poller(fixedDelay = "1000", maxMessagesPerPoll = "1"))
public MessageSource<String> test() {
    return () -> new GenericMessage<>("adfdfdsafdsfa");
}
```

这样，消息消费失败后，就会放入死信队列。在控制台操作一下，即可将死信放回消息队列，这样，客户端就可以重新处理。

如果想获取原始错误的异常堆栈，可添加如下配置：

```yaml
spring:
  cloud:
    stream:
      rabbit:
        bindings:
          input:
            consumer:
              republish-to-dlq: true
```

#### requeue【RabbitMQ】

Rabbit/Kafka的binder依赖RetryTemplate实现重试，从而提升消息处理的成功率。然而，如果设置了`spring.cloud.stream.bindings.input.consumer.max-attempts=1` ，那么RetryTemplate则不再重试。此时可通过requeue方式处理异常。

添加如下配置：

```properties
# 默认是3，设为1则禁用重试
spring.cloud.stream.bindings.<input channel名称>.consumer.max-attempts=1
# 表示是否要requeue被拒绝的消息(即：requeue处理失败的消息)
spring.cloud.stream.rabbit.bindings.input.consumer.requeue-rejected=true
```

这样，失败的消息将会被重新提交到同一个handler进行处理，直到handler抛出 `AmqpRejectAndDontRequeueException` 异常为止。

### RetryTemplate【通用】

#### 配置方式

RetryTemplate重试也是错误处理的一种手段。

```yaml
spring:
  cloud:
    stream:
      bindings:
        <input channel名称>:
          consumer:
            # 最多尝试处理几次，默认3
            maxAttempts: 3
            # 重试时初始避退间隔，单位毫秒，默认1000
            backOffInitialInterval: 1000
            # 重试时最大避退间隔，单位毫秒，默认10000
            backOffMaxInterval: 10000
            # 避退乘数，默认2.0
            backOffMultiplier: 2.0
            # 当listen抛出retryableExceptions未列出的异常时，是否要重试
            defaultRetryable: true
            # 异常是否允许重试的map映射
            retryableExceptions:
              java.lang.RuntimeException: true
              java.lang.IllegalStateException: false
```

测试代码：

```java
@StreamListener(value = Processor.INPUT)
public void handle(String body) {
    throw new RuntimeException(body);
}

private AtomicInteger count = new AtomicInteger(0);

@Bean
@InboundChannelAdapter(value = Processor.OUTPUT,
        poller = @Poller(fixedDelay = "1000", maxMessagesPerPoll = "1"))
public MessageSource<String> test() {
    return () -> new GenericMessage<>(count.getAndAdd(1) + "");
}
```

#### 编码方式

多数场景下，使用配置方式定制重试行为都是可以满足需求的，但配置方式可能无法满足一些复杂需求。此时可使用编码方式配置RetryTemplate：

```java
@Configuration
class RetryConfiguration {
    @StreamRetryTemplate
    public RetryTemplate sinkConsumerRetryTemplate() {
        RetryTemplate retryTemplate = new RetryTemplate();
        retryTemplate.setRetryPolicy(retryPolicy());
        retryTemplate.setBackOffPolicy(backOffPolicy());

        return retryTemplate;
    }

    private ExceptionClassifierRetryPolicy retryPolicy() {
        BinaryExceptionClassifier keepRetryingClassifier = new BinaryExceptionClassifier(
                Collections.singletonList(IllegalAccessException.class
                ));
        keepRetryingClassifier.setTraverseCauses(true);

        SimpleRetryPolicy simpleRetryPolicy = new SimpleRetryPolicy(3);
        AlwaysRetryPolicy alwaysRetryPolicy = new AlwaysRetryPolicy();

        ExceptionClassifierRetryPolicy retryPolicy = new ExceptionClassifierRetryPolicy();
        retryPolicy.setExceptionClassifier(
                classifiable -> keepRetryingClassifier.classify(classifiable) ?
                        alwaysRetryPolicy : simpleRetryPolicy);

        return retryPolicy;
    }

    private FixedBackOffPolicy backOffPolicy() {
        final FixedBackOffPolicy backOffPolicy = new FixedBackOffPolicy();
        backOffPolicy.setBackOffPeriod(2);

        return backOffPolicy;
    }
}
```

然后添加配置：

```
spring.cloud.stream.bindings.<input channel名称>.consumer.retry-template-
```

# Spring Cloud Stream + RocketMQ实现分布式事务

# Spring Cloud Stream知识总结

- 概念
- Stream注解
- Spring Integration（[Spring Cloud](https://coding.imooc.com/?c=springcloud) Stream的底层）注解
- Spring Messaging（Spring消息编程模型）注解
- [Spring Cloud](https://coding.imooc.com/?c=springcloud) Stream API

## 概念

### group

组内只有1个实例消费。如果不设置group，则stream会自动为每个实例创建匿名且独立的group——于是每个实例都会消费。

组内单次只有1个实例消费，并且会轮询负载均衡。通常，在将应用程序绑定到给定目标时，最好始终指定consumer group。

### destination binder

与外部消息系统通信的组件，为构造 `Binding`提供了 2 个方法，分别是 `bindConsumer` 和 `bindProducer` ，它们分别用于构造生产者和消费者。Binder使[Spring Cloud](https://coding.imooc.com/?c=springcloud) Stream应用程序可以灵活地连接到中间件，目前spring为kafka、rabbitmq提供binder。

### destination binding

`Binding` 是连接应用程序跟消息中间件的桥梁，用于消息的消费和生产，由binder创建。

### partition

> **TIPS**
>
> 严格来说这个不是概念，而是一种Stream提高伸缩性、吞吐量的一种方式。不过不想另起标题了，写在这里吧。

一个或多个生产者将数据发送到多个消费者，并确保有共同特征标识的数据由同一个消费者处理。默认是对消息进行hashCode，然后根据分区个数取余，所以对于相同的消息，总会落到同一个消费者上。

## 注解

### Input(Stream)

示例：

```java
public interface Barista {
    @Input("inboundOrders")
    SubscribableChannel orders();
}
```

作用：

- 用于接收消息
- 为每个binding生成channel实例
- 指定channel名称
- 在spring容器中生成一个名为inboundOrders，类型为SubscribableChannel的bean
- 在spring容器中生成一个类，实现Barista接口。

### Output(Stream)

示例：

```java
public interface Source {
    @Output
    MessageChannel output();
}
```

作用：

类似Input，只是用来生产消息。

### StreamListener(Stream)

示例：

```java
@StreamListener(value = Sink.INPUT, condition = "headers['type']=='dog'")
public void handle(String body) {
    System.out.println("Received: " + body);
}

@Bean
@InboundChannelAdapter(value = Source.OUTPUT,
        poller = @Poller(fixedDelay = "1000", maxMessagesPerPoll = "2"))
public MessageSource<String> test() {
    return () -> {
        Map<String, Object> map = new HashMap<>(1);
        map.put("type", "dog");
        return new GenericMessage<>("abcdef", map);
    };
}
```

作用：

用于消费消息

condition的作用：符合条件，才进入处理方法。

condition起作用的两个条件：

- 注解的方法没有返回值
- 方法是一个独立方法，不支持Reactive API

### SendTo(messaging)

示例：

```java
// 接收INPUT这个channel的消息，并将返回值发送到OUTPUT这个channel
@StreamListener(Sink.INPUT)
@SendTo(Source.OUTPUT)
public String receive(String receiveMsg) {
   return "handle...";
}
```

作用：

用于发送消息

### InboundChannelAdapter(Integration)

示例：

```java
@Bean
@InboundChannelAdapter(value = Source.OUTPUT,
        poller = @Poller(fixedDelay = "10", maxMessagesPerPoll = "1"))
public MessageSource<String> test() {
    return () -> new GenericMessage<>("Hello Spring Cloud Stream");
}
```

作用：

表示让定义的方法生产消息。

> 注：用 `InboundChannelAdapter` 注解的方法上即使有参数也没用。即下面test方法不要有参数。

- fixedDelay：多少毫秒发送1次
- maxMessagesPerPoll：一次发送几条消息。

### ServiceActivator(Integration)

示例：

```java
@ServiceActivator(inputChannel = Sink.INPUT, outputChannel = Source.OUTPUT)
public String transform(String payload) {
    return payload.toUpperCase();
}
```

作用：

表示方法能够处理消息或消息有效内容，监听input消息，用方法体的代码处理，然后输出到output中。

### Transformer(Integration)

示例：

```java
@Transformer(inputChannel = Processor.INPUT, outputChannel = Processor.OUTPUT)
public Object transform(String message) {
  return message.toUpperCase();
}
```

作用：

和 `ServiceActivator` 类似，表示方法能够转换消息，消息头，或消息有效内容

## PollableMessageSource(Stream)

示例代码：

```java
@SpringBootApplication
@EnableBinding({ConsumerApplication.PolledProcessor.class})
@EnableScheduling
public class ConsumerApplication {
    public static void main(String[] args) {
        SpringApplication.run(ConsumerApplication.class, args);
    }

    @Autowired
    private PolledProcessor polledProcessor;

    @Scheduled(fixedDelay = 5_000)
    public void poll() {
        polledProcessor.input().poll(message -> {
            byte[] bytes = (byte[]) message.getPayload();
            String payload = new String(bytes);
            System.out.println(payload);
        });
    }

    public interface PolledProcessor {
        @Input
        PollableMessageSource input();

        @Output
        MessageChannel output();
    }

    @Bean
    @InboundChannelAdapter(value = "output",
            poller = @Poller(fixedDelay = "1000", maxMessagesPerPoll = "1"))
    public MessageSource<String> test() {
        return () -> {
            Map<String, Object> map = new HashMap<>(1);
            map.put("type", "dog");
            return new GenericMessage<>("adfdfdsafdsfa", map);
        };
    }
}
```

如果不想自己做byte数组转换，可以添加配置：

```yaml
spring:
  cloud:
    stream:
      bindings:
        output:
          # 指定content-type
          content-type: text/plain
```

作用：

允许消费者控制消费速率。

## 加入网关架构图

![image-20210331164622760](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210331164622760.png)

# Spring Cloud Gateway是什么？

*是Spring Cloud的网关（第二代）。未来会取代Zuul（第一代）

*基于Netty、Reactor以及WebFlux构建

## Spring Cloud Gateway优点

*性能强劲；是第一代网关Zuul1.X的1.6倍。

*性能强大：内置了很多实用功能，比如转发、监控、限流等

*设计优雅，易扩展

## Spring Cloud Gateway缺点

*依赖Netty与Webflux，不是Servlet编程模型，有一定的适用成本

*不能在Servlet容器下工作，也不能构建成WAR包

*不支持SpringBoot1.x

### 编写Spring Cloud Gateway

转发规律；访问${GATEWAY_URL}/{微服务X}/**/**会转发到微服务X的/* */**路径 

## Gateway核心概念

*Route（路由）

​	Spring Cloud Gateway的基础元素，可简单理解成一条转发的规则。包含：ID、目标URL、Predicate聚集合以及Filter集合

*Predicate（谓词）

即java.util.function.Predicate,Spring Cloud Gateway使用Predicate实现路由的匹配条件。

*Filter（过滤器）

修改请求以及响应

![image-20210331172806759](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210331172806759.png)

## Spring Cloud Gateway 架构

## **Spring Cloud Gateway-路由谓词工厂详解（Route Predicate Factories）**

路由谓词工厂的作用是：**符合Predicate的条件，就使用该路由的配置，否则就不管。** 只要掌握这一句，掌握路由谓词工厂就比较轻松了。

> **TIPS**
>
> Predicate是Java 8提供的一个函数式编程接口。

本文探讨了[Spring Cloud](https://coding.imooc.com/?c=springcloud) Gateway中内置的谓词工厂，包括：

| 谓词工厂   |
| :--------- |
| After      |
| Before     |
| Between    |
| Cookie     |
| Header     |
| Host       |
| Method     |
| Path       |
| Query      |
| RemoteAddr |

## 路由配置的两种形式

先来探讨[Spring Cloud](https://coding.imooc.com/?c=springcloud) Gateway路由配置的两种姿势：

### 路由到指定URL

#### 示例1：通配

```yaml
spring:
  cloud:
    gateway:
      routes:
      - id: {唯一标识}
        uri: http://www.itmuch.com
```

表示访问 `GATEWAY_URL/**` 会转发到 `http://www.itmuch.com/**`

> **TIPS**
>
> 这段配置不能直接使用，需要和下面的Predicate配合使用才行。

#### 示例2：精确匹配

```yaml
spring:
  cloud:
    gateway:
      routes:
      - id: {唯一标识}
        uri: http://www.itmuch.com/spring-cloud/spring-cloud-stream-pan-ta/
```

表示访问 `GATEWAY_URL/spring-cloud/spring-cloud-stream-pan-ta/` 会转发到 `http://www.itmuch.com/spring-cloud/spring-cloud-stream-pan-ta/`

> **TIPS**
>
> 这段配置不能直接使用，需要和下面的Predicate配合使用才行。

### 路由到服务发现组件上的微服务

#### 示例1：通配

```yaml
spring:
  cloud:
    gateway:
      routes:
      - id: {唯一标识}
        uri: lb://user-center
```

表示访问 `GATEWAY_URL/**` 会转发到 `user-center` 微服务的 `/**`

> **TIPS**
>
> 这段配置不能直接使用，需要和下面的Predicate配合使用才行。

#### 示例2：精确匹配

```yaml
spring:
  cloud:
    gateway:
      routes:
      - id: {唯一标识}
        uri: lb://user-center/shares/1
```

表示访问 `GATEWAY_URL/shares/1` 会转发到 `user-center` 微服务的 `/shares/1`

> **TIPS**
>
> 这段配置不能直接使用，需要和下面的Predicate配合使用才行。

## 谓词工厂详解

下面正式探讨路由谓词工厂。[Spring Cloud](https://coding.imooc.com/?c=springcloud) Gateway提供了十来种路由谓词工厂。为网关实现灵活的转发提供了基石。

### After

示例：

```yaml
spring:
  cloud:
    gateway:
      routes:
        - id: after_route
          uri: lb://user-center
          predicates:
            # 当且仅当请求时的时间After配置的时间时，才会转发到用户微服务
            # 目前配置不会进该路由配置，所以返回404
            # 将时间改成 < now的时间，则访问localhost:8040/** -> user-center/**
            # eg. 访问http://localhost:8040/users/1 -> user-center/users/1
            - After=2030-01-20T17:42:47.789-07:00[America/Denver]
```

> **TIPS**
>
> - 技巧：时间可使用 `System.out.println(ZonedDateTime.now());` 打印，然后即可看到时区。例如：`2019-08-10T16:50:42.579+08:00[Asia/Shanghai]`
> - 时间格式的相关逻辑：
>   - 默认时间格式：org.springframework.format.support.DefaultFormattingConversionService#addDefaultFormatters
>   - 时间格式注册：org.springframework.format.datetime.standard.DateTimeFormatterRegistrar#registerFormatters

### Before

示例：

```yaml
spring:
  cloud:
    gateway:
      routes:
        - id: before_route
          uri: lb://user-center
          predicates:
            # 当且仅当请求时的时间Before配置的时间时，才会转发到用户微服务
            # 目前配置不会进该路由配置，所以返回404
            # 将时间改成 > now的时间，则访问localhost:8040/** -> user-center/**
            # eg. 访问http://localhost:8040/users/1 -> user-center/users/1
            - Before=2018-01-20T17:42:47.789-07:00[America/Denver]
```

### Between

示例：

```yaml
spring:
  cloud:
    gateway:
      routes:
        - id: between_route
          uri: lb://user-center
          predicates:
            # 当且仅当请求时的时间Between配置的时间时，才会转发到用户微服务
            # 因此，访问localhost:8040/** -> user-center/**
            # eg. 访问http://localhost:8040/users/1 -> user-center/users/1
            - Between=2017-01-20T17:42:47.789-07:00[America/Denver], 2027-01-21T17:42:47.789-07:00[America/Denver]
```

### Cookie

示例：

```yaml
spring:
  cloud:
    gateway:
      routes:
        - id: cookie_route
          uri: lb://user-center
          predicates:
            # 当且仅当带有名为somecookie，并且值符合正则ch.p的Cookie时，才会转发到用户微服务
            # 如Cookie满足条件，则访问http://localhost:8040/** -> user-center/**
            # eg. 访问http://localhost:8040/users/1 -> user-center/users/1
            - Cookie=somecookie, ch.p
```

### Header

```yaml
spring:
  cloud:
    gateway:
      routes:
        - id: header_route
          uri: lb://user-center
          predicates:
            # 当且仅当带有名为X-Request-Id，并且值符合正则\d+的Header时，才会转发到用户微服务
            # 如Header满足条件，则访问http://localhost:8040/** -> user-center/**
            # eg. 访问http://localhost:8040/users/1 -> user-center/users/1
            - Header=X-Request-Id, \d+
```

### Host

```yaml
spring:
  cloud:
    gateway:
      routes:
        - id: host_route
          uri: lb://user-center
          predicates:
            # 当且仅当名为Host的Header符合**.somehost.org或**.anotherhost.org时，才会转发用户微服务
            # 如Host满足条件，则访问http://localhost:8040/** -> user-center/**
            # eg. 访问http://localhost:8040/users/1 -> user-center/users/1
            - Host=**.somehost.org,**.anotherhost.org
```

### Method

```yaml
spring:
  cloud:
    gateway:
      routes:
        - id: method_route
          uri: lb://user-center
          predicates:
            # 当且仅当HTTP请求方法是GET时，才会转发用户微服务
            # 如请求方法满足条件，访问http://localhost:8040/** -> user-center/**
            # eg. 访问http://localhost:8040/users/1 -> user-center/users/1
            - Method=GET
```

### Path

```yaml
spring:
  cloud:
    gateway:
      routes:
        - id: path_route
          uri: lb://user-center
          predicates:
            # 当且仅当访问路径是/users/*或者/some-path/**，才会转发用户微服务
            # segment是一个特殊的占位符，单层路径匹配
            # eg. 访问http://localhost:8040/users/1 -> user-center/users/1
            - Path=/users/{segment},/some-path/**
```

> **TIPS**
>
> ```
> https://cloud.spring.io/spring-cloud-static/Greenwich.SR2/single/spring-cloud.html#_path_route_predicate_factory
> ```

### Query

示例1：

```yaml
spring:
  cloud:
    gateway: 
      routes:
        - id: query_route
          uri: lb://user-center
          predicates:
            # 当且仅当请求带有baz的参数，才会转发到用户微服务
            # eg. 访问http://localhost:8040/users/1?baz=xx -> user-center的/users/1
            - Query=baz
```

示例2：

```yaml
spring:
  cloud:
    gateway:
      routes:
        - id: query_route
          uri: lb://user-center
          predicates:
            # 当且仅当请求带有名为foo的参数，且参数值符合正则ba.，才会转发到用户微服务
            # eg. 访问http://localhost:8040/users/1?baz=baz -> user-center的/users/1?baz=baz
            - Query=foo, ba.
```

### RemoteAddr

示例：

```yaml
spring:
  cloud:
    gateway:
      routes:
        - id: remoteaddr_route
          uri: lb://user-center
          predicates:
            # 当且仅当请求IP是192.168.1.1/24网段，例如192.168.1.10，才会转发到用户微服务
            # eg. 访问http://localhost:8040/users/1 -> user-center的/users/1
            - RemoteAddr=192.168.1.1/24
```

## 自定义路由谓词工程

## 自定义过滤器工厂

1.过滤器生命周期；pre：Gateway转发请求之前，post：Gateway转发请求之后

2.自定义过滤器工厂-方式一

​	继承：AbstractGatewayFilterFactory

配置形式：

```yaml
spring:
	cloud:
		gateway:
			routes:
				filters:
					-name: RequestSize
					args:
						maxSize: 5000000
```

自定义过滤器工厂-方式2

继承：AbstractNameValueGatewayFilterFactory

配置形式：

```yaml
spring:
	cloud:
		gateway:
			routes:
				filters:
				-AddRequestHeader=S-Header,Bar
```

自定义过滤器工厂-核心API

*exchange.getRequest().mutate().xxx //修改request

*exchange.mutate().xxx //修改exchange

*chain.filter(exchange) //传递给下一个过滤器处理

exchange.getResponse()//拿到响应

## **Spring Cloud Gateway-全局过滤器**

参考：https://www.imooc.com/article/290821

## 排错、调式技巧总结



1.Actuator监控端点;借助Actuator的监控端点，可分析全局过滤器、过滤器工厂、路由详情
2：日志;加日志，按需将如下包的日志级别设置成 debug 或 trace
org.springframework.cloud.gateway
org.springframework.http.server.reactive
org.springframework.web.reactive
org.springframework.boot.autoconfigure.web
reactor.netty
redisratelimiter

配置示例：

```yaml
logging:
  level:
    org.springframework.cloud.gateway: trace
```

3.Wiretap【从Greenwich SR3及更高版本才会支持】

Reactor Netty `HttpClient` 以及 `HttpServer` 可启用 `Wiretap` 。将`reactor.netty` 包设置成 `debug` 或 `trace` ，然后设置如下属性：

- `spring.cloud.gateway.httpserver.wiretap=true`
- `spring.cloud.gateway.httpclient.wiretap=true`

分别开启HttpServer及HttpClient的Wiretap。

## 过滤器执行顺序

1.Order越小越靠前执行

2.过滤器工厂的Order按配置顺序从1开始递增

![image-20210401094426969](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210401094426969.png)

3.如果配置了默认过滤器，则先执行相同Order的默认过滤器

![image-20210401094614596](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210401094614596.png)

4.如需自行控制Order，可返回OrderedGatewayFilter

## **Spring Cloud Gateway限流**

[Spring Cloud](https://coding.imooc.com/?c=springcloud) Gatway内置的 `RequestRateLimiterGatewayFilterFactory` 提供限流的能力，基于令牌桶算法实现。目前，它内置的 `RedisRateLimiter` ，依赖Redis存储限流配置，以及统计数据。当然你也可以实现自己的RateLimiter，只需实现 `org.springframework.cloud.gateway.filter.ratelimit.RateLimiter` 接口，或者继承 `org.springframework.cloud.gateway.filter.ratelimit.AbstractRateLimiter` 。

# 登录的设计实现

## 有状态和无状态

​	有状态优点：服务器端控制力强

​	无状态优点：去中心化、无存储，简单、任意扩容、缩容

​	有状态缺点：存在中心点，鸡蛋在一个篮子里 迁移麻烦 服务器端存储数据，加大了服务器端压力

​	无状态：服务器端控制力相对弱

## 微服务""处处安全"方案

​	1.OAuth2.0系列文章

​		http://ifeve.com/oauth2-tutorial-all/

​	2.代表实现

​		spring clouds Security

​		**Jboss Keycloak**

# JWT是什么

*JWT全称Json web token，是一个开放标准（RFC 7519），用来在各方之间安全地传输信息。JWT可被验证和信任，因为它是数字签名的。

JWT组成

![image-20210401103900262](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210401103900262.png)



*了解stream -->JDK 8 *lambda表达式 *functional -->函数式编程

## Lambda

### 什么是Lambda表达式

1.JDK8开始支持Lambda表达式，用来让程序编写更优雅

2.利用Lambda可以更简洁的实现匿名内部类与函数声明与调用

3.基于Lambad提供stream流式处理极大简化对集合的操作

### Lambda语法

![image-20210327134448292](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210327134448292.png)

```java
//1.标准Lambda使用方式
//约束条件:Lambda表达式只能实现有且只有一个抽象方法的接口,Java称为"函数式接口"
//2.Lambda允许忽略参数类型
//3.单行实现代码可以省略大括号和return
 MathOperation multiplication = (a,b)->a*b+0f;
 System.out.println(multiplication.operate(5,3));
```

### 基于Lambda实现函数式编程

​	*函数式编程是基于函数式接口并使用lambda表达的编程方式

​	*函数式编程理念是将代码作为可重用数据代入到程序运行中

​	*函数式编程强调“你想做什么”，而不是“你想怎么做”

#### 什么是函数式接口

​	*函数式接口是有且只有一个抽象方法的接口

​	*Java中拥有大量函数式接口，如java.lang.Runnable

​	*JDK8后提供了一系列新的函数式接口，位于**java.util.function**

![image-20210327143126100](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210327143126100.png)

例子 

```java
Predicate<Integer> predicate = n->n<4;
boolean result = predicate.test(10);
System.out.println(result);
List<Integer> list = Arrays.asList(1,2,3,4,5,6,7,8,9,10);
  		filter(list,n->n%2==1); //取所有奇数
        filter(list,n->n%2==0); //取所有偶数
        filter(list,n->n>5 && n%2==0); //取所有大于5的偶数
    }
    public static void filter(List<Integer> list , Predicate<Integer> predicate){
        for(Integer num:list){
            if(predicate.test(num)){
                System.out.print(num + " ");
            }
        }
        System.out.println("");
    }
}
```

**JDK8常用函数式接口**

接口                                                                       用途

Consumer<T>							对应有一个输入参数无输出的功能代码

```java
public class ConsumerSample {
    public static void main(String[] args) {
        output(s-> System.out.println("向控制台打印:" + s));
        output(s->{
            System.out.println("向XXX网站发送数据包:" + s);
        });
    }
    public static void output(Consumer<String> consumer){
        String text = "天将降大任于是人也，必先苦其心志，劳其筋骨，饿其体肤，空乏其身，行拂乱其所为。";
        consumer.accept(text);
    }
```

Function<T,R>							对应有一个输入参数且需要返回数据的功能代码

```java
/**
 * 利用Function函数式接口生成定长随机字符串
 */
public class FunctionSample {
    public static void main(String[] args) {
        Function<Integer,String> randomStringFunction = l->{
          String chars = "abcdefghijklmnopqrstuvxwyz0123456789";
            StringBuffer stringBuffer = new StringBuffer();
            Random random = new Random();
            for(int i = 0 ; i < l ; i++){
                int position = random.nextInt(chars.length());
                stringBuffer.append(chars.charAt(position));
            }
            return stringBuffer.toString();
        };
        String randomString = randomStringFunction.apply(32);
        System.out.println(randomString);
    }
} 
```

Predicate<T>							 用于条件判断，固定返回布尔值

### Stream流式处理

*Stream流式处理是建立在Lambda基础上的多数据处理技术

*Stream对集合数据处理进行高度抽象,极大简化代码量

*Stream可对集合进行迭代,去重,筛选,排序,聚合等一系列处理

### Stream例子

![image-20210327155748855](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210327155748855.png)

## Stream常用方法

接口								用途

forEach						循环遍历

map							 map方法用于映射每个元素对应的结果

filter							filter方法用于通过设置的条件过滤出元素

limit							limit方法用于获取指定数量的流

sorted						sorted方法用于对流进行排序

Collectors				  Collectors类实现将流转换成集合和聚合元素

```java
//1.基于数组进行创建
public void generator1(){
    String[] arr = {"Lily" , "Andy" , "Jackson" , "Smith"};
    Stream<String> stream = Stream.of(arr);
    stream.forEach(s->System.out.println(s));
}
 //2.基于集合进行创建
    @Test
    public void generator2(){
        List<String> list = new ArrayList<>();
        list.add("Lily");
        list.add("Andy");
        list.add("Jackson");
        list.add("Smith");
        Stream<String> stream = list.stream();
        stream.forEach(s->System.out.println(s));
    }
//这两个是最常使用的
```

```java
//3.利用generate方法创建无限长度流
@Test
public void generator3(){
    Stream<Integer> stream = Stream.generate(() -> new Random().nextInt(100000));
    stream.limit(10).forEach(i->System.out.println(i));
}
//4.基于迭代器创建流
    @Test
    public void generator4(){
        Stream<Integer> stream = Stream.iterate(1,n->n+1);
        stream.limit(100).forEach(i->System.out.println(i));
    }
    //5.基于字符序列创建流
    @Test
    public void generator5(){
        String str = "abcdefg我的";
        IntStream stream = str.chars();
        stream.forEach(c -> System.out.println((char)c));
    }
```

```java
@Test
public void case1(){
    List<String> list = Arrays.asList("1", "2", "3", "4", "5" , "6");
    int sum = list.stream() //获取stream对象
        .mapToInt(s->Integer.parseInt(s)) //mapToInt将流中每一个数据转为整数
        .filter(n->n%2==0) //filter对流数据进行过滤
        .sum();//求和
    System.out.println(sum);
}

//所有名字首字母大写
@Test
public void case2(){
    List<String> list = Arrays.asList("lily","smith","jackson");
    List newList = list.stream()
            //按规则对每一个流数据进行转换
            .map(s->s.substring(0,1).toUpperCase() + s.substring(1))
            //.forEach(s-> System.out.println(s));
            //collect对流数据进行收集,生成新的List/Set
            .collect(Collectors.toList());
    System.out.println(newList);
}

//将所有奇数从大到小进行排序,且不许出现重复
@Test
public void case3(){
    List<Integer> list = Arrays.asList(1,60,38,21,51,60,51,73);
    List newList = list.stream().distinct()//去除重复的流数据
        .filter(n->n%2==1)
        .sorted((a,b)->b-a) //流数据排序
        .collect(Collectors.toList());
    System.out.println(newList);
```

## 函数式编程与面向对象编程比较

### ![image-20210327154504541](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210327154504541.png)

# Java学习过程遇到的问题

## 在配置数据库需要加上时区配置

Java出现The server time zone value '�й���׼ʱ��' is unrecogni的解决

**原因：**

原因是因为使用了Mysql Connector/J 6.x以上的版本，然后就报了时区的错误

遇到的问题 servertime=UTC导致时间差8个小时（MySQL jdbc 6.0 版本以上必须配置此参数）

解决办法
在配置url的时候不能简单写成 ：jdbc:mysql://localhost:3306/数据库名

而是要写成 ：jdbc:mysql://localhost:3306/数据库名?serverTimezone=UTC

而UTC代表的是全球标准时间 ，但是我们使用的时间是北京时区也就是东八区，领先UTC八个小时。UTC + (＋0800) = 本地（北京）时间解决方案

url的时区使用中国标准时间。也是就

**jdbc:mysql://localhost:3306/数据库名?serverTimezone=Asia/Shanghai**

## Spring+SpringMVC 配置事务管理无效原因及解决方案。

参考：https://blog.csdn.net/qq_32588349/article/details/52097943

## &&重要关于扫描配置父子上下文

# @SpringQueryMap注解 feign的get传参方式

spring cloud项目使用feign的时候都会发现一个问题，就是get方式无法解析对象参数。其实feign是支持对象传递的，但是得是Map形式，而且不能为空，与spring在机制上不兼容，因此无法使用。

spring cloud在2.1.x版本中提供了@SpringQueryMap注解，可以传递对象参数，框架自动解析，只可惜啊，得是2.1.0以后的版本。spring 在5.0中提供了webflux踢掉了对tomcat的依赖，又提供了gateway踢掉了对zuul的依赖，2.1.x版本恐怕是准备对netflix动刀了。

```java
// Params.java`
public class Params {
    private String param1;
    private String param2;

    // [Getters and setters omitted for brevity]
}
@FeignClient("demo")
public class DemoTemplate {
	@GetMapping(path = "/demo")
    String demoEndpoint(@SpringQueryMap Params params);
}
```

```xml
报错[org.springframework.web.HttpMediaTypeNotSupportedException: Content type 'text/plain;charset=UTF-8' not supported]
```

自己在postman加上![image-20210331133938253](C:\Users\wankin.chen\AppData\Roaming\Typora\typora-user-images\image-20210331133938253.png)