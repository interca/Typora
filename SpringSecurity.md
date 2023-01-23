# Spring-security



## 注意

1. anonymous() :匿名访问，仅允许匿名用户访问,如果登录认证后，带有token信息再去请求，这个anonymous()关联的资源就不能被访问(就相当于登陆之后不允许访问,只允许匿名的用户)
2. permitAll() 登录能访问,不登录也能访问,一般用于静态资源js等

## 一、简介

### 1、介绍

![微信截图_20220906235320](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220906235320.png)



### 2、坐标

![微信截图_20220907011457](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220907011457.png)



### 3、流程介绍

![微信截图_20220907011817](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220907011817.png)



![微信截图_20220907013723](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220907013723.png)



![微信截图_20220907020925](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220907020925.png)



![微信截图_20220907025443](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220907025443.png)



![微信截图_20220907031640](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220907031640.png)

![微信截图_20220907033057](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220907033057.png)



## 二、登录

### 1、思路分析



![微信截图_20220907034540](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220907034540.png)

### 2、数据库查询

![微信截图_20220907195617](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220907195617.png)



### 3、返回类型

![微信截图_20220907195656](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220907195656.png)



### 4、数据库加密

我们一般先加密后存入数据库

![微信截图_20220907195708](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220907195708.png)



### 5、密码加密

![微信截图_20220907200034](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220907200034.png)



![微信截图_20220907213922](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220907213922.png)



### 6、登录接口

![微信截图_20220909130648](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220909130648.png)





### 登录过程

把密码传入usernamepasswordauthenticationtoken    然后  UserviceImpl查询数据库

两个进行比较

这里前端的密码进入方法后会自动进行加密

![微信截图_20220929011053](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220929011053.png)

![微信截图_20220929011227](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220929011227.png)



### 7、认证过滤器

![微信截图_20220909154419](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220909154419.png)



### 8、配置config

![微信截图_20220909171617](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220909171617.png)



### 9、注销

![微信截图_20220911160421](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220911160421.png)



## 三、授权

### 1、概念

![微信截图_20220911162408](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220911162408.png)



### 2、开放权限

![微信截图_20220911163956](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220911163956.png)



![微信截图_20220921033221](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220921033221.png)



![微信截图_20220921033253](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220921033253.png)



### 3、权限关系表

![微信截图_20220911182057](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220911182057.png)





### 4、跨域

![微信截图_20220913023454](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220913023454.png)





## 四、异常

### 1、过滤器的异常

因为过滤器的异常不能被全局捕获

所以我们要用安全框架自带的异常

我们可以把异常存入session中

![微信截图_20220929005517](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220929005517.png)

![微信截图_20220929005549](C:\Users\waili\Desktop\usual\微信截图\spring security\微信截图_20220929005549.png)

![微信截图_20220929005559](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220929005559.png)

![微信截图_20220929005607](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220929005607.png)
