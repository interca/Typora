# Linux

## 一、简介

### 1、介绍

![微信截图_20220913203428](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220913203428.png)



### 2、学习

![微信截图_20220913211624](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220913211624.png)



### 3、版本

![微信截图_20220913214409](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220913214409.png)



### 4、对比其他操作系统

![微信截图_20220913214604](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220913214604.png)





## 二、文件

一切皆文件

### 1、概述

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220919230456.png" alt="微信截图_20220919230456" style="zoom:67%;" />



### **2、vim**(重点)

在linux里对文件进行操作

![微信截图_20220920021034](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220920021034.png)



#### 2.1 模式

按i是编辑

![微信截图_20220920161308](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220920161308.png)



### 3、指令(重要)

![微信截图_20220920162515](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220920162515.png)

![微信截图_20220920164504](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220920164504.png)



### 4、重要指令

普通模式

cd命令。切换目录命令。

cd 单独一个cd，切换到用户主目录

cd ~ 切换到用户主目录

cd / 切换到[根目录](https://so.csdn.net/so/search?q=根目录&spm=1001.2101.3001.7020)

cd .. 切换到上级目录

cd ../.. 切换到上上级目录，可以此类推。

cd - 返回到上次命令目录(类似于命令回退)

|         cd         | 进入某个文件                 |
| :----------------: | ---------------------------- |
|         ls         | 展示文件内容                 |
|         i          | 进入编辑模式                 |
|        esc         | 退出                         |
|        ：w         | 保存                         |
|         u          | 回退                         |
|        ：q         | 退出                         |
|         yy         | 复制当前行                   |
|      数字+yy       | 复制下面多少行               |
|        y+$         | 复制当前单词和后面所有内容   |
|        y+^         | 前面，不包括当前单词         |
|         p          | 黏贴   前面加数字可以黏贴n行 |
|         dd         | 删除当前行                   |
|         w          | 跳到下一个单词               |
|        y+w         | 复制当前单词                 |
|        d+w         | 删除当前单词，从光标开始     |
| d+$或者^和前面一样 |                              |
|         x          | 剪切  前提是不在编辑模式     |
|         X          | 删除光标前一个单词           |
|         r          | 替换                         |



|    R     | 连续替换     |
| :------: | :----------- |
|    gg    | 移动到最前面 |
|    G     | 最末尾       |
|    e     | 当前词尾     |
| 数字+gg  | 跳到某行的头 |
|    ：    | 命令模式     |
| ：set nu | 显示行号     |
|          |              |
|          |              |
|          |              |







cd 进入某个文件

ls 展示某个文件有什么

i 进入编辑模式   esc退出

：w保存

u 回退

：q退出操作

yy 复制  前面加数字  复制多少行    y+$复制当前单词及其后面的所有东西     y+^复制前面不包括当前字符

p黏贴    前面加数字可以黏贴多行 

dd 删除当前行



编辑模式(插入模式)

![微信截图_20220921235630](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220921235630.png)





操作指令

![微信截图_20220922000248](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220922000248.png)









## 三、网络

### 1、基础操作

ping + ip可以连接主机

ctrl + shift +v是复制

ctrl + c是停止连接

ifconfig查询网络



### 2、网络连接模式

![微信截图_20221015192029](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221015192029.png)







### 3、更改网络配置

![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221103004100.png)

![微信截图_20221015202837](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221015202837.png)

![微信截图_20221015203624](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221015203624.png)







### 4、问题

![微信截图_20221015204548](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221015204548.png)



### 5、将别的ip改名字到本地

![微信截图_20221015211013](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221015211013.png)

![微信截图_20221015211022](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221015211022.png)

![微信截图_20221026125403](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221026125403.png)

连接虚拟机



### 6、远程登录

![微信截图_20221026125511](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221026125511.png)

## 



## 四、服务和进程

### 1、服务管理（6）

![微信截图_20221026204929](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221026204929.png)





### **2、服务管理(7)**

![微信截图_20221026205833](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221026205833.png)





### 3、运行级别

![微信截图_20221026211701](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221026211701.png)



![微信截图_20221026214926](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221026214926.png)



### 4、关闭防火墙

![微信截图_20221029155444](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221029155444.png)



### 5、系统命令

![微信截图_20221029155718](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221029155718.png)





![微信截图_20221029160742](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221029160742.png)





![微信截图_20221029160837](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221029160837.png)





### 6、帮助命令

![微信截图_20221029161613](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221029161613.png)





![微信截图_20221029162454](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221029162454.png)





### 7、内置命令

![微信截图_20221029162550](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221029162550.png)







## 五、常用命令



### 1、快捷键

![微信截图_20221029163338](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221029163338.png)





### 2、文件

ll也可以列出

![微信截图_20221101013851](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221101013851.png)



### 3、cd

![微信截图_20221101014920](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221101014920.png)





文件形式

![微信截图_20221101020214](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221101020214.png)



### 4、ls

![微信截图_20221101021034](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221101021034.png)





### 5、文件夹操作

![微信截图_20221101021914](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221101021914.png)





![微信截图_20221101021924](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221101021924.png)



![微信截图_20221101233359](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221101233359.png)





![微信截图_20221101235648](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221101235648.png)





![微信截图_20221102004344](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221102004344.png)





### 6、查看内容

![微信截图_20221102005657](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221102005657.png)



![微信截图_20221102010606](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221102010606.png)



