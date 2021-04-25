# 反射

## 什么是反射及作用

*反射（Reflect）是在**运行时**动态访问类与对象的技术

*反射是JDK1.2版本后的高级特性，隶属java.lang.reflect

*大多数Java框架都基于反射实现参数配置，动态注入等特性

## 反射四个核心类

Class类；Constructor构造方法类；Method方法类；Field成员变量类。

### Class类

1.Class是JVM中代表"类和接口"的类

2.Class对象具体包含了某个特定类的结构信息

3.通过Class对象可获取对应类的构造方法/方法/成员变量

### Class核心方法

方法																用途

Class.forName()					静态方法,用于获取指定Class对象

classObj.newInstance()		通过默认构造方法创建新的对象

classObj.getConstructor()	获得指定的public修饰构造方法Constructor对象

classObj.getMethod()			获取指定的public修饰方法Method对象

classObj.getField()				获取指定的public修饰成员变量Field对象

### 利用Class创建对象

//得到员工类的类对象Class employeeClass = **Class.forName**("com.imooc.reflect.entity.Employee");

//通过员工类默认构造方法创建Employee对象

Employee employee = (Employee) employeeClass.**newInstance()**;

### Constructor构造方法类

1.Constructor类是对Java类中的构造方法的抽象

2.Contructor对象包含了具体类的某个具体构造方法的声明

3.通过Constructor对象调用带参构造方法创建对象

### Constructor类核心方法

方法																用途

classObj.getConstructor()						获取指定public修饰的构造方法对象

constructorObj.newInstance()				通过对应的构造方法创建对象利用Constructor创建对象

//得到员工类的类对象

Class employeeClass =**Class.forName** ("com.imooc.reflect.entity.Employee");

//得到Employee类包含四个参数的构造方法对象Constructor constructor = employeeClass.**getConstructor**(new Class[]{    Integer.class, String.class, Float.class, String.class});

//通过指定构造方法传入数据,创建对象Employee employee = (Employee) constructor.**newInstance**(new Object[]{                100 , "李磊" , 3000f , "研发部"});

### Method方法类

Method对象指代某个类中的方法的描述

Method对象使用classObj.getMethod()方法获取

通过Method对象调用指定对象的对应方法

### Method类核心方法

方法																			用途

classObj.getMethod()											获取指定public修饰的方法对象

methodObj.invoke()											   调用指定对象的对应方法

利用Method执行方法

...

Employee employee = (Employee) constructor.newInstance(new Object[]{100 , "李磊" , 3000f,"研发部"});

Method method = employeeClass.getMethod("updateSalary" , new Class[]{Float.class});

//执行方法,为李磊上调薪资300元method.invoke(employee , new Object[]{ 300f });

### Field成员变量类

Field对应某个具体类中的成员变量的声明

Field对象使用classObj.getField()方法获取

通过Field对象可为某对象成员变量赋值/取值

### Field类核心方法

方法                                                         用途

classObj.getField()								获取指定public修饰的成员变量对象

fieldObj.set()										 为某对象指定成员变量赋值

fieldObj.get()										获取某对象指定成员变量数值

### 利用Field赋值与取值

//获取员工姓名Field成员变量对象

Field enameField = employeeClass.getField("ename");

//成员变量赋值

enameField.set(employee,"李雷");

//成员变量取值

String ename = (String)enameField.get(employee);

### getDeclared系列方法说明

getDeclaredConstructor(s)Method(s)Field(s)||获取对应对象getConstructor(s)Method(s)Field(s)||只能获取public对象

访问非作用域内构造方法、方法、成员变量,会抛出异常

```java
 Field[] fields = employeeClass.getDeclaredFields();
            for(Field field : fields){
//                System.out.println(field.getName());
                if(field.getModifiers() == 1){ //pubilc修饰
                    Object val = field.get(employee);
                    System.out.println(field.getName() + ":" + val);
                }else if(field.getModifiers() == 2){ //private修饰
                    String methodName = "get" + field.getName().substring(0,1).toUpperCase()
                                        + field.getName().substring(1);
                    Method getMethod = employeeClass.getMethod(methodName);
                    Object ret = getMethod.invoke(employee);
                    System.out.println(field.getName() + ":" + ret);
```

## 反射在实际工程的应用

# 注解

概念：说明程序的。给计算机看的

注释：用文字描述程序的。给程序员看的

定义：注解（Annotation），也叫元数据。一种代码级别的说明。它是JDK1.5及以后版本引入的一个特性，与类、接口、枚举是在同一个层次。它可以声明在包、类、字段、方法、局部变量、方法参数等的前面，用来对这些元素进行说明，注释。

概念描述：
* JDK1.5之后的新特性
* 说明程序的
* 使用注解：@注解名称

## 作用分类：

①编写文档：通过代码里标识的注解生成文档【生成文档doc文档】
②代码分析：通过代码里标识的注解对代码进行分析【使用反射】
③编译检查：通过代码里标识的注解让编译器能够实现基本的编译检查【Override】

##  JDK中预定义的一些注解

​	 @Override	：检测被该注解标注的方法是否是继承自父类(接口)的
​	@Deprecated：该注解标注的内容，表示已过时
​	@SuppressWarnings：压制警告
​		 一般传递参数all  @SuppressWarnings("all")

自定义注解

格式：
元注解
public @interface 注解名称{
	属性列表;
}

本质：注解本质上就是一个接口，该接口默认继承Annotation接口

public interface MyAnno extends java.lang.annotation.Annotation {}

属性：接口中的抽象方法

要求：
1. 属性的返回值类型有下列取值
	* 基本数据类型
	* String
	* 枚举
	* 注解
	* 以上类型的数组

2. 定义了属性，在使用时需要给属性赋值
	1. 如果定义属性时，使用default关键字给属性默认初始化值，则使用注解时，可以不进行属性的赋值。
	2. 如果只有一个属性需要赋值，并且属性的名称是value，则value可以省略，直接定义值即可。
	3. 数组赋值时，值使用{}包裹。如果数组中只有一个值，则{}可以省略

元注解：用于描述注解的注解

@Target：描述注解能够作用的位置

ElementType取值：

TYPE：可以作用于类上

METHOD：可以作用于方法上

FIELD：可以作用于成员变量上

@Retention：描述注解被保留的阶段

@Retention(RetentionPolicy.RUNTIME)：当前被描述的注解，会保留到class字节码文件中，并被JVM读取到

@Documented：描述注解是否被抽取到api文档中

@Inherited：描述注解是否被子类继承

 在程序使用(解析)注解：获取注解中定义的属性值
	1. 获取注解定义的位置的对象  （Class，Method,Field）
	2. 获取指定的注解
		* getAnnotation(Class)
		//其实就是在内存中生成了一个该注解接口的子类实现对象

```java
            public class ProImpl implements Pro{
                public String className(){
                    return "cn.itcast.annotation.Demo1";
                }
                public String methodName(){
                    return "show";
                }
            }
3. 调用注解中的抽象方法获取配置的属性值
```