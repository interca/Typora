# Swagger

## 注意：

记得拦截器和安全框架要放行

```Java
"/swagger-resources/**", "/webjars/**", "/v2/**", "/swagger-ui.html/**"
```

## 1、简介

![微信截图_20220805051708](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220805051708.png)

![微信截图_20220805052059](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220805052059.png)



## 2、步骤

### 1、坐标

![微信截图_20220805053310](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220805053310.png)



### 2、编写配置类

![微信截图_20220805054538](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220805054538.png)

### 3、测试

![微信截图_20220805061311](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220805061311.png)



代码如下：

![微信截图_20220805063632](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220805063632.png)





## 3、详细信息

### 1、配置

![微信截图_20220903020430](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220903020430.png)





![微信截图_20220903020957](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220903020957.png)



### 2、按环境启动

![微信截图_20220903023013](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220903023013.png)



### 3、分组

![微信截图_20220903141330](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220903141330.png)







## 3、常见注解

### 1、类上(dto)

让前端看到字段对应的信息

已经apimodel

![微信截图_20220903182202](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220903182202.png)

首先要知道@ApiModelProperty是swagger的注解，它的作用是添加和操作属性模块的数据，下面是它内部的常用属性：

1、value()

源码：String value() default "";
1
参数类型为String，作用为此属性的简要描述。

2、name()

源码： String name() default "";
1
参数类型为String，作用为允许重写属性的名称。

3、allowableValues()

源码：String allowableValues() default "";
1
参数类型为String，作用为允许此参数存储的长度。

4、access()

源码：String access() default "";
1
参数类型为String，作用为允许从API文档中过滤属性

5、notes()

源码： String notes() default "";
1
参数类型为String，作用为该字段的注释说明

6、dataType()

源码： String dataType() default "";
1
参数类型为String，作用为参数的数据类型。

7、required()

源码：boolean required() default false;
1
参数类型为String，作用为指定参数是否可以为空，默认为false

8、 position()

源码：int position() default 0;
1
参数类型为int，作用为允许显式地对模型中的属性排序。

9、hidden()

源码：boolean hidden() default false;
1
参数类型为boolean，作用为是否允许模型属性隐藏在Swagger模型定义中，默认为false。

10、example()

源码：String example() default "";
1
参数为String类型，作用为属性的示例值。

11、readOnly()

源码：boolean readOnly() default false;
1
参数类型为boolean，作用为是否允许将属性指定为只读，默认为false。

12、reference()

源码： String reference() default "";
1
参数类型为String，作用为指定对对应类型定义的引用，重写指定的任何其他数据名称。

13、allowEmptyValue()

源码：boolean allowEmptyValue() default false;
1
参数类型为boolean，作用为是否允许传递空值，默认为false

示例：

  @ApiModelProperty(value = "主键",name = "id",
  	  allowableValues = "32",
      access = "1",
      notes = "用户的id",
      dataType = "int",
      required = false,
      position = 1,
      hidden = true,
      example = "1",
      readOnly = false,
      reference = "id",
      allowEmptyValue = false)
  @TableId(value = "id",type = IdType.AUTO)
  private int id;
————————————————
版权声明：本文为CSDN博主「我有一只小阿茶」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/weixin_44356055/article/details/109451892



### 2、controller

让前端知道什么模块

![微信截图_20220903182301](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220903182301.png)



### 3、方法和参数

![微信截图_20220903182316](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220903182316.png)

![微信截图_20220903182448](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220903182448.png)



### 4、实体类

![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220915220141.png)

![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221013113915.png)
