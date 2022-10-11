# Spring-security



## 一、简介

### 1、介绍

![微信截图_20220906235320](C:\Users\waili\Desktop\usual\微信截图\spring security\微信截图_20220906235320.png)



### 2、坐标

![微信截图_20220907011457](C:\Users\waili\Desktop\usual\微信截图\spring security\微信截图_20220907011457.png)



### 3、流程介绍

![微信截图_20220907011817](C:\Users\waili\Desktop\usual\微信截图\spring security\微信截图_20220907011817.png)



![微信截图_20220907013723](C:\Users\waili\Desktop\usual\微信截图\spring security\微信截图_20220907013723.png)



![微信截图_20220907020925](C:\Users\waili\Desktop\usual\微信截图\spring security\微信截图_20220907020925.png)



![微信截图_20220907025443](C:\Users\waili\Desktop\usual\微信截图\spring security\微信截图_20220907025443.png)



![微信截图_20220907031640](C:\Users\waili\Desktop\usual\微信截图\spring security\微信截图_20220907031640.png)

![微信截图_20220907033057](C:\Users\waili\Desktop\usual\微信截图\spring security\微信截图_20220907033057.png)



## 二、登录

### 1、思路分析



![微信截图_20220907034540](C:\Users\waili\Desktop\usual\微信截图\spring security\微信截图_20220907034540.png)

### 2、数据库查询

![微信截图_20220907195617](C:\Users\waili\Desktop\usual\微信截图\spring security\微信截图_20220907195617.png)



### 3、返回类型

![微信截图_20220907195656](C:\Users\waili\Desktop\usual\微信截图\spring security\微信截图_20220907195656.png)



### 4、数据库加密

我们一般先加密后存入数据库

![微信截图_20220907195708](C:\Users\waili\Desktop\usual\微信截图\spring security\微信截图_20220907195708.png)



### 5、密码加密

![微信截图_20220907200034](C:\Users\waili\Desktop\usual\微信截图\spring security\微信截图_20220907200034.png)



![微信截图_20220907213922](C:\Users\waili\Desktop\usual\微信截图\spring security\微信截图_20220907213922.png)



### 6、登录接口

![微信截图_20220909130648](C:\Users\waili\Desktop\usual\微信截图\spring security\微信截图_20220909130648.png)





### 登录过程

把密码传入usernamepasswordauthenticationtoken    然后  UserviceImpl查询数据库

两个进行比较

这里前端的密码进入方法后会自动进行加密

![微信截图_20220929011053](C:\Users\waili\Desktop\usual\微信截图\spring security\微信截图_20220929011053.png)

![微信截图_20220929011227](C:\Users\waili\Desktop\usual\微信截图\spring security\微信截图_20220929011227.png)



### 7、认证过滤器

![微信截图_20220909154419](C:\Users\waili\Desktop\usual\微信截图\spring security\微信截图_20220909154419.png)



### 8、配置config

![微信截图_20220909171617](C:\Users\waili\Desktop\usual\微信截图\spring security\微信截图_20220909171617.png)



### 9、注销

![微信截图_20220911160421](C:\Users\waili\Desktop\usual\微信截图\spring security\微信截图_20220911160421.png)



## 三、授权

### 1、概念

![微信截图_20220911162408](C:\Users\waili\Desktop\usual\微信截图\spring security\微信截图_20220911162408.png)



### 2、开放权限

![微信截图_20220911163956](C:\Users\waili\Desktop\usual\微信截图\spring security\微信截图_20220911163956.png)



![微信截图_20220921033221](C:\Users\waili\Desktop\usual\微信截图\spring security\微信截图_20220921033221.png)



![微信截图_20220921033253](C:\Users\waili\Desktop\usual\微信截图\spring security\微信截图_20220921033253.png)



### 3、权限关系表

![微信截图_20220911182057](C:\Users\waili\Desktop\usual\微信截图\spring security\微信截图_20220911182057.png)





### 4、跨域

![微信截图_20220913023454](C:\Users\waili\Desktop\usual\微信截图\spring security\微信截图_20220913023454.png)





## 四、异常

### 1、过滤器的异常

因为过滤器的异常不能被全局捕获

所以我们要用安全框架自带的异常

我们可以把异常存入session中

![微信截图_20220929005517](C:\Users\waili\Desktop\usual\微信截图\spring security\微信截图_20220929005517.png)

![微信截图_20220929005549](C:\Users\waili\Desktop\usual\微信截图\spring security\微信截图_20220929005549.png)

![微信截图_20220929005559](C:\Users\waili\Desktop\usual\微信截图\spring security\微信截图_20220929005559.png)

![微信截图_20220929005607](C:\Users\waili\Desktop\usual\微信截图\spring security\微信截图_20220929005607.png)
