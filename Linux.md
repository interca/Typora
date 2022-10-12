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

