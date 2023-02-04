# MongoDB



## 一、概述



### 应用场景

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230118034003.png" alt="微信截图_20230118034003" style="zoom: 80%;" />





<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230118044805.png" alt="微信截图_20230118044805" style="zoom:80%;" />





<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230118044838.png" alt="微信截图_20230118044838" style="zoom:80%;" />





![微信截图_20230118045139](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230118045139.png)





### 简介

介绍

![微信截图_20230118045449](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230118045449.png)



体系结构

![微信截图_20230118045614](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230118045614.png)





和sql对比
>mongoDB中的集合就是一个表，然后文档就是一列，只是他没有mysql那么严格的排列规定

![微信截图_20230118045645](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230118045645.png)



 

### 数据模型

![微信截图_20230118045735](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230118045735.png)





### 数据类型 

>不支持整形，要用函数来强制转换

![微信截图_20230118045816](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230118045816.png)



转换为整形

![微信截图_20230118045936](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230118045936.png)





### 特点

![微信截图_20230118050048](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230118050048.png)







## 二、安装启动

### 下载安装包

![微信截图_20230118050300](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230118050300.png)





![微信截图_20230118050654](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230118050654.png)





![微信截图_20230118050742](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230118050742.png)





### 建立数据存放文件

>启动方式有两种，如下

![微信截图_20230118051357](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230118051357.png)





配置文件启动

![微信截图_20230118052434](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230118052434.png)



![微信截图_20230118052519](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230118052519.png)



### 注意

>6.0开始要在官网下mongodbsh  解压后把bin目录配置到path  然后才能链接到数据库

![微信截图_20230118053844](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230118053844.png)







## 三、操作



### 集合概述

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230119003938.png" alt="微信截图_20230119003938" style="zoom:67%;" />



### 数据库

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230119004352.png" alt="微信截图_20230119004352" style="zoom:67%;" />





<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230119005233.png" alt="微信截图_20230119005233" style="zoom:67%;" />





![微信截图_20230119005357](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230119005357.png)





### 集合

![微信截图_20230119005539](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230119005539.png)





![微信截图_20230119010155](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230119010155.png)



### 文档

#### 插入

![微信截图_20230119010443](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230119010443.png)





![微信截图_20230119010514](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230119010514.png)





![微信截图_20230119010544](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230119010544.png)





![微信截图_20230119011036](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230119011036.png)





#### 查询

![微信截图_20230119011617](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230119011617.png)





批量插入，用数组括起来

![微信截图_20230119011743](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230119011743.png)





指定查询

![微信截图_20230119012354](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230119012354.png)





投影查询 

![  0、;''](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230119012537.png)





#### 异常

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230119014403.png" alt="微信截图_20230119014403" style="zoom:67%;" />







#### 更新

![微信截图_20230120034308](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230120034308.png)





覆盖修改和局部修改

![微信截图_20230120034732](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230120034732.png)





批量修改

![微信截图_20230120035218](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230120035218.png)





#### 删除

![微信截图_20230120035333](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230120035333.png)



#### 分页

>skip 跳过多少条数据

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230120035507.png" alt="微信截图_20230120035507" style="zoom:67%;" />





<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230120035701.png" alt="微信截图_20230120035701" style="zoom:67%;" />





#### 排序

![微信截图_20230120040322](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230120040322.png)





#### 复杂查询

![微信截图_20230120210500](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230120210500.png)





#### 条件查询

![微信截图_20230120211917](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230120211917.png)





多条件

![微信截图_20230120212925](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230120212925.png)







![微信截图_20230120213311](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230120213311.png)







#### and和or查询

![微信截图_20230120213357](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230120213357.png)







#### 小结

![微信截图_20230120214344](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230120214344.png)







## 四、索引

### 概念

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230120214514.png" alt="微信截图_20230120214514" style="zoom:67%;" />





### 单字索引

![微信截图_20230120214554](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230120214554.png)





### 复合索引

![微信截图_20230120215539](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230120215539.png)





### 其他索引

![微信截图_20230120220242](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230120220242.png)





### 查看

![微信截图_20230121135543](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230121135543.png)







### 创建

![微信截图_20230121140108](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230121140108.png)



![微信截图_20230121140151](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230121140151.png)







![微信截图_20230121140242](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230121140242.png)





![微信截图_20230121140425](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230121140425.png)





### 移除

![微信截图_20230121140536](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230121140536.png)







![微信截图_20230121140732](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230121140732.png)





### 覆盖查询

![微信截图_20230121141104](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230121141104.png)







## 五、JAVA操作mongoDB

### 技术

![微信截图_20230121142211](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230121142211.png)





### 依赖和配置

![微信截图_20230121143240](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230121143240.png)



![微信截图_20230121143357](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230121143357.png)





### 实体类

>这里指定集合，还有索引

![微信截图_20230121144918](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230121144918.png)





![微信截图_20230121145027](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230121145027.png)





![微信截图_20230121145051](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230121145051.png)







### 操作

```Java

@Service
public class CommentService {

    @Autowired
    private CommentRepository commentRepository;
    
    
    @Autowired
    private MongoTemplate mongoTemplate;



    /**
     * 保存一个评论
     * @param comment
     */
    public void saveComment(Comment comment){
        //如果需要自定义主键，可以在这里指定主键；如果不指定主键，MongoDB会自动生成主键
        //设置一些默认初始值。。。
        //调用dao
        commentRepository.save(comment);
    }

    /**
     * 更新评论
     * @param comment
     */
    public void updateComment(Comment comment){
        //调用dao
        commentRepository.save(comment);
    }

    /**
     * 根据id删除评论
     * @param id
     */
    public void deleteCommentById(String id){
        //调用dao
        commentRepository.deleteById(id);
    }

    /**
     * 查询所有评论
     * @return
     */
    public List<Comment> findCommentList(){
        //调用dao
        return commentRepository.findAll();
    }

    /**
     * 根据id查询评论
     * @param id
     * @return
     */
    public Comment findCommentById(String id){
        //调用dao
        return commentRepository.findById(id).get();
    }

   //分页
    public Page<Comment> findCommentListByParentid(String parentid,int page,int size) {
        return commentRepository.findByParentid(parentid,PageRequest.of(page-1,size));
    }

    
    //条件更新
    public void updateCommentLikenum(String id){
        //  查询条件
        Query query = Query.query(Criteria.where("_id").is(id));
        //  更新条件
        Update update = new Update();
        update.inc("likenum");
        mongoTemplate.updateFirst(query,update,Comment.class);
    }


}
```



![微信截图_20230127073332](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230127073332.png)



条件查找
>这里findBy是固定的，条件的名称根据具体情况来

![微信截图_20230123182747](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230123182747.png)









```
#!/bin/sh
docker run \
-p 3306:3306 \
--name mysql \
--privileged=true \
--restart unless-stopped \
-v /mnt/sda1/mysql8.0.20/mysql:/etc/mysql \
-v /mnt/sda1/mysql8.0.20/logs:/logs \
-v /mnt/sda1/mysql8.0.20/data:/var/lib/mysql \
-v ~/mysql_slave/mysql-files:/var/lib/mysql-files \
-v /etc/localtime:/etc/localtime \
-e MYSQL_ROOT_PASSWORD=hyjzzyfldgutyyds \
-d mysql:8.0.20
```

