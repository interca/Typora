# Maven

## 配置

[(61条消息) maven镜像仓库的配置_flytalei的博客-CSDN博客_在项目中配置仓库镜像](https://blog.csdn.net/flytalei/article/details/123684754)

## 1、简介

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220717173253.png" alt="微信截图_20220717173253" style="zoom:50%;" />

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220717173503.png" alt="微信截图_20220717173503" style="zoom:67%;" />





## 2、仓库

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220719202922.png" alt="微信截图_20220719202922" style="zoom:67%;" />



<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220719202959.png" alt="微信截图_20220719202959" style="zoom:67%;" />



## **3、坐标**

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220719203547.png" alt="微信截图_20220719203547" style="zoom:67%;" />



## 4、配置

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220719203831.png" alt="微信截图_20220719203831" style="zoom:67%;" />

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220719204053.png" alt="微信截图_20220719204053" style="zoom:67%;" />

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220720225123.png" alt="微信截图_20220720225123" style="zoom:67%;" />



## 5、结构

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220720233012.png" alt="微信截图_20220720233012" style="zoom:67%;" />

## 6、命令

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220720235920.png" alt="微信截图_20220720235920" style="zoom:67%;" />



## 7、IEAD配置Maven

setting file那里改成自己的存放位置

![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220731004438.png)

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220721004221.png" alt="微信截图_20220721004221" style="zoom:67%;" />



## **8、建立Maven**

普通Maven从java工程那里创建

如果是特殊的，点Maven Archetype

org.apache.maven.archetypes:maven-archetype-quickstart   选择这个是java的

org.apache.maven.archetypes:maven-archetype-webapp  这个是web的

可以手动加resources目录，添加一些资源什么的

如果启动服务器，要配置tomcat

![image-20220815202048497](https://gitee.com/hongshenghyj/typora/raw/master/img/image-20220815202048497.png)

9、依赖

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220721013645.png" alt="微信截图_20220721013645" style="zoom:67%;" />

### 依赖传递

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220721014445.png" alt="微信截图_20220721014445" style="zoom:67%;" />



### 可选依赖

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220721014704.png" alt="微信截图_20220721014704" style="zoom:67%;" />

### 排除依赖

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220721015009.png" alt="微信截图_20220721015009" style="zoom:67%;" />



### 依赖范围

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220721015241.png" alt="微信截图_20220721015241" style="zoom:67%;" />

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220721015914.png" alt="微信截图_20220721015914" style="zoom:67%;" />



## 9、生命周期

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220721020325.png" alt="微信截图_20220721020325" style="zoom:67%;" />

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220721020526.png" alt="微信截图_20220721020526" style="zoom:67%;" />

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220721020630.png" alt="微信截图_20220721020630" style="zoom:67%;" />

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220721020644.png" alt="微信截图_20220721020644" style="zoom:67%;" />

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220721020904.png" alt="微信截图_20220721020904" style="zoom:67%;" />



10、插件

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220721022428.png" alt="微信截图_20220721022428" style="zoom:50%;" />