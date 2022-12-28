# SpringBoot

## 常见问题：

1、druid报错，要同时引入jdbc包

2、springboot默认前端页面放到static和templates，  否则要在mvc配置指定路径

entity   和数据库对应

dto   和前端传过来数据对应

vo  返回给前端的数据

记得要忽略,idea和target的文件

maven记得配置仓库

还有就是jdk要用1.8  c盘fire下面的  所有jdk保持一致

模块那里模块sdk也要保持一致

## 技巧

拷贝工具类

BeanUtils

![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221009031156.png)





## 部署

1、打包

2、放到opt下面

3、然后执行命令

![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221207200815.png)

查看进程以及杀死(重新部署的时候)

![微信截图_20221207200858](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221207200858.png)



![微信截图_20221207200919](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221207200919.png)



**如果服务器是腾讯云  除了在控制台开放端口  还有在防火墙里面开放**



## 一、简介

### 1、前置

![微信截图_20220812014158](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220812014158.png)

![微信截图_20220812014500](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220812014500.png)

![微信截图_20220812014817](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220812014817.png)

![微信截图_20220812014910](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220812014910.png)





### 2、快速入门

![微信截图_20220812235558](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220812235558.png)

![微信截图_20220812235627](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220812235627.png)





### 3、阿里云创建

![微信截图_20220813000807](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220813000807.png)



### 4、隐藏文件

![微信截图_20220813001843](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220813001843.png)





### 5、结构原理

![微信截图_20220813005206](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220813005206.png)

![微信截图_20220813005801](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220813005801.png)

![微信截图_20220813011350](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220813011350.png)





## 二、rest风格

### 1、简介

![微信截图_20220813011858](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220813011858.png)



### 2、常见

![微信截图_20220813012400](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220813012400.png)





![微信截图_20220813013229](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220813013229.png)

![微信截图_20220813013545](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220813013545.png)

![微信截图_20220813013730](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220813013730.png)

### 3、案例

![微信截图_20220813014234](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220813014234.png)

![微信截图_20220813014327](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220813014327.png)





![微信截图_20220813014534](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220813014534.png)





### **4、接受参数**

![微信截图_20220813014806](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220813014806.png)



### 5、简化

![微信截图_20220813015846](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220813015846.png)

![微信截图_20220813021022](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220813021022.png)

![微信截图_20220813021303](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220813021303.png)

![微信截图_20220813021322](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220813021322.png)







## 三、配置

### 1、常见配置

![微信截图_20220813033558](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220813033558.png)

![微信截图_20220813033616](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220813033616.png)





### 2、共存

![微信截图_20220813033928](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220813033928.png)

### 3、优先级

![微信截图_20220814003402](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220814003402.png)

### 4、提升功能

![微信截图_20220814004210](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220814004210.png)





### 5、yml

#### 1、书写格式

![微信截图_20220814004645](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220814004645.png)

![微信截图_20220814004800](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220814004800.png)

![微信截图_20220814004853](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220814004853.png)

![微信截图_20220814004933](C:\Users\waili\Desktop\usual\微信截图\springboot\微信截图_20220814004933.png)

![微信截图_20220814005157](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220814005157.png)





#### 2、读取

第一种

![微信截图_20220814010403](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220814010403.png)

![微信截图_20220814010514](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220814010514.png)

![微信截图_20220814010521](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220814010521.png)





![微信截图_20220814010853](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220814010853.png)





第二种

![微信截图_20220814011306](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220814011306.png)

![微信截图_20220814012357](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220814012357.png)





第三种

![微信截图_20220814012500](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220814012500.png)





## 四、整合技术

### 1、junit

![微信截图_20220814014613](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220814014613.png)



![微信截图_20220814015519](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220814015519.png)





### 2、mybaits

直接在mapper层那里加一个注解就行了，很简便

设置数据源

这里在

这里只用一个sql文件就行了

![微信截图_20220814210940](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220814210940.png)

![微信截图_20220814210953](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220814210953.png)

配置文件

![微信截图_20220814211007](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220814211007.png)

![微信截图_20220814211058](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220814211058.png)

![微信截图_20220814211524](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220814211524.png)





代码：

![微信截图_20220802040332](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220802040332.png)

![微信截图_20220802040408](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220802040408.png)



### 3、druid

导入坐标

![微信截图_20220815012332](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220815012332.png)

![微信截图_20220804200920](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220804200920.png)





### 4、具体配置

![微信截图_20220815155905](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220815155905.png)





## 五、mybatisplus

### 1、说明

plus不能和mybatis一起导入，要不然报错，plus兼容配置文件

![微信截图_20220805004728](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220805004728.png)

![微信截图_20220805005150](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220805005150.png)



![微信截图_20220815022731](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220815022731.png)

### 2、依赖

![微信截图_20220805005206](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220805005206.png)

![微信截图_20220805005218](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220805005218.png)

![微信截图_20220805005235](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220805005235.png)



### **3、mapper层简化开发**

![微信截图_20220815023237](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220815023237.png)

直接继承，有几个基础的方法

这样子可以不用写一些基本方法，可以直接用mapper查询



### 4、拦截器分页

![微信截图_20220815154858](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220815154858.png)

![微信截图_20220815154932](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220815154932.png)





![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221009025909.png)







### 5、日志

![微信截图_20220815152654](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220815152654.png)

### 6、配置

![微信截图_20220815155905](C:\Users\waili\Desktop\usual\微信截图\springboot\微信截图_20220815155905.png)



### 7、按条件查询

![微信截图_20220815160224](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220815160224.png)





## 六、lombok

### 1、依赖

![微信截图_20220815015508](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220815015508.png)



### 2、常用

![微信截图_20220815015547](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220815015547.png)

![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220817180319.png)

构造器

## 七、SSMP整合

### 1、简介

![微信截图_20220815012637](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220815012637.png)

![微信截图_20220815021647](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220815021647.png)



具体看项目





## 八、传入格式

### 1、json

一般如果是对象，前端传入json,后端用requesbody接受，如果是get请求，不能用requesbody

![微信截图_20220817200643](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220817200643.png)

![微信截图_20220817201135](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220817201135.png)

![微信截图_20220817201522](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220817201522.png)





### 2、restful风格

![微信截图_20220817202420](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220817202420.png)

![微信截图_20220817202429](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220817202429.png)

![微信截图_20220817203433](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220817203433.png)





### 3、返回数据

![微信截图_20220817203840](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220817203840.png)

![微信截图_20220817204154](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220817204154.png)

![微信截图_20220817204337](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220817204337.png)

我们可以定义一个返回类

这样子就可以让前端知道我们返回的状态了

![微信截图_20220817210325](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220817210325.png)





例子：

![微信截图_20220817210405](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220817210405.png)

![微信截图_20220817210414](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220817210414.png)



### 4、book项目前端内容

### 具体看代码

![微信截图_20220819030637](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220819030637.png)



### 5、异常处理

![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220825192348.png)

## 九、运维适用



### 1、打包

记得打包前clean

然后在target目录找到文件，打开路径



![微信截图_20220819181012](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220819181012.png)

![微信截图_20220819181034](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220819181034.png)

这是运行



![微信截图_20220819181710](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220819181710.png)

### 2、端口问题

![微信截图_20220819182904](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220819182904.png)



### 3、设置临时属性

打包时候

![微信截图_20220819183534](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220819183534.png)

加载顺序

![微信截图_20220819183701](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220819183701.png)



![微信截图_20220819184124](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220819184124.png)





### 4、配置优先级

不同优先级的文件会覆盖并且互补

![微信截图_20220820153652](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220820153652.png)

![微信截图_20220820153741](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220820153741.png)

![微信截图_20220820154650](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220820154650.png)





### 5、多环境

![微信截图_20220820154832](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220820154832.png)



第一种设置

![微信截图_20220820155530](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220820155530.png)

第二种：

![微信截图_20220820155734](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220820155734.png)



第三种格式：

![微信截图_20220820155828](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220820155828.png)





### 6、多环境文件版

![微信截图_20220820160442](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220820160442.png)

![微信截图_20220820160511](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220820160511.png)

![微信截图_20220820161121](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220820161121.png)



### 7、多环境文件2

![微信截图_20220820161220](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220820161220.png)

![微信截图_20220820162718](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220820162718.png)



pom中配置(不推荐)

![微信截图_20220821101908](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220821101908.png)

![微信截图_20220821101924](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220821101924.png)

![微信截图_20220821102527](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220821102527.png)



### 8、异常

看ssm

![image-20221012190331617](https://gitee.com/hongshenghyj/typora/raw/master/img/image-20221012190331617.png)





### 9、日志



![微信截图_20220825040451](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220825040451.png)



日志级别

![微信截图_20220822234658](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220822234658.png)



分组设置

![微信截图_20220822235112](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220822235112.png)



代码中输出日志

![微信截图_20220822235137](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220822235137.png)





注解输出日志

![微信截图_20220825032728](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220825032728.png)



日志格式



![微信截图_20220825033117](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220825033117.png)





设置日志输出格式

![微信截图_20220825034025](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220825034025.png)



设置日志文件

![微信截图_20220825040321](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220825040321.png)







### 10、热部署

![微信截图_20220904203742](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220904203742.png)

‘

![微信截图_20220904204001](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220904204001.png)





手动

![微信截图_20220904204013](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220904204013.png)



热部署范围

![微信截图_20220904205401](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220904205401.png)



![微信截图_20220904205411](C:\Users\waili\Desktop\usual\微信截图\springboot\微信截图_20220904205411.png)



![微信截图_20220904211101](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220904211101.png)





### **11、第三方bean**

这里的别的地方使用这个bean名字要是dataSource才能对应上

![微信截图_20220905051926](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220905051926.png)



![微信截图_20220905052747](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220905052747.png)





enable已经定义它被spring管控

所以serverconfig不用加component

![微信截图_20220905052850](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220905052850.png)





![微信截图_20220905052902](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220905052902.png)





![微信截图_20220905053841](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220905053841.png)





![微信截图_20220905054957](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220905054957.png)



### 12、事物

![微信截图_20221005231000](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221005231000.png)

![微信截图_20221005231014](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221005231014.png)





### 13、拦截器

![微信截图_20220926013546](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220926013546.png)

![微信截图_20220926013555](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220926013555.png)
