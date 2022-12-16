# Mybatis-Plus

## 注意

插入或者更新数据后，原本的java对象也会更新

比如插入一条数据，主键刚开始没有的

插入后生成雪花算法

然后这个对象也会赋值id



xml文件：

```java
<select id="robTicket" parameterType="Map" resultType="int">
    select  count(*)  from gq_user_info where now()>(
    select grab_tickets_start  from gq_lecture_info where  id=#{lectureId})
    and (select grab_tickets_end  from gq_lecture_info where  id=#{lectureId})>now()
    and ticket_state=0
    and  gq_user_info.openid=#{openid};
</select>
```

## 1、配置

![微信截图_20220905082229](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220905082229.png)



## 2、接口简化开发

![微信截图_20220905082246](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220905082246.png)



## 3、类名关联数据库

![微信截图_20220905083744](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220905083744.png)



## 4、标准开发

![微信截图_20220905084426](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220905084426.png)



## 5、lombok

![微信截图_20220905090522](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220905090522.png)

![微信截图_20220905090533](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220905090533.png)





## 6、分页

![微信截图_20220905094222](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220905094222.png)



![微信截图_20220905094242](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220905094242.png)



![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221002173314.png)



## 7、开启日志

![微信截图_20220905094232](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220905094232.png)



## 8、查询

![微信截图_20220905094736](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220905094736.png)



### 1、条件查询

![微信截图_20220905100745](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220905100745.png)



### 2、lambda

![微信截图_20220905101041](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220905101041.png)



### 3、多条件

![微信截图_20220905102417](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220905102417.png)



### **4、各种条件**

lt  小于   gt 大于   le小于等于  ge大于等于  eq等于

![微信截图_20220905102916](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220905102916.png)



![微信截图_20220905104414](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220905104414.png)



![微信截图_20220905104435](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220905104435.png)



### 5、null

![微信截图_20220905105608](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220905105608.png)



### 6、部分属性

![微信截图_20220905105608](C:\Users\waili\Desktop\usual\微信截图\mybatis-plus\微信截图_20220905105608.png)



### 7、等于

![微信截图_20220905180409](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220905180409.png)





![微信截图_20220905180929](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220905180929.png)



### 8、其他

![微信截图_20220905180954](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220905180954.png)





## 9、映射

### 1、字段

![微信截图_20220906145218](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220906145218.png)



### 2、表名

![微信截图_20220906145236](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220906145236.png)



### 3、id

![微信截图_20220906150155](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220906150155.png)

![微信截图_20220906151108](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220906151108.png)



### 4、全局配置

![微信截图_20220906151525](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220906151525.png)



### 5、删除

![微信截图_20220906151915](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220906151915.png)



![微信截图_20220906154849](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220906154849.png)



## 10、锁

![微信截图_20220906160610](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220906160610.png)

![微信截图_20220906160622](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220906160622.png)



![微信截图_20220906160655](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220906160655.png)







## 11、serivce继承类



<img src="C:\Users\waili\Desktop\usual\微信截图\mybatis-plus\微信截图_20221216142852.png" alt="微信截图_20221216142852" style="zoom:150%;" />





![微信截图_20221216142936](C:\Users\waili\Desktop\usual\微信截图\mybatis-plus\微信截图_20221216142936.png)







<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221216142957.png" alt="微信截图_20221216142957" style="zoom:150%;" />





<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221216142949.png" alt="微信截图_20221216142949" style="zoom:150%;" />





还可以直接写sql

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221216143412.png" alt="微信截图_20221216143412" style="zoom:200%;" />
