# Rocketmq

## 文档

[为什么选择RocketMQ | RocketMQ (apache.org)](https://rocketmq.apache.org/zh/docs/)

## 注意

### 访问不到控制台

> 修改配置文件加上开放三个端口
>
> vi conf/broker.conf
> 设置linux的ip
>
> namesrvAddr = xxxx:9876 
> brokerIP1=xxxx
> 使用命令开放端口10909，10911，9876端口
>
> firewall-cmd --zone=public --add-port=10909/tcp --permanent
> firewall-cmd --zone=public --add-port=1091/tcp --permanent
> firewall-cmd --zone=public --add-port=9876/tcp --permanent
> systemctl restart firewalld.service
> firewall-cmd --reload

**Topic是一个逻辑上的概念，实际上Message是在每个Broker上以Queue的形式记录。**

## 一、结构

其他内容

![微信截图_20221228033336](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221228033336.png)

  



![微信截图_20221228034218](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221228034218.png)

  

### 1、基本组成  

消息

![微信截图_20221228034859](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221228034859.png)

  



topic  

![微信截图_20221228034920](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221228034920.png)

  

![微信截图_20221228035027](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221228035027.png)

  



tag

![微信截图_20221228035156](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221228035156.png)

  



queue

![微信截图_20221228035230](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221228035230.png)





![微信截图_20221228035341](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221228035341.png)





![微信截图_20221228035810](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221228035810.png)





### 分片

![微信截图_20221228035955](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221228035955.png)





消息标识

![微信截图_20221228194300](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221228194300.png)





![微信截图_20221228201643](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221228201643.png)





### 2、生产者  



![微信截图_20221228202746](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221228202746.png)



### 2、消费者  



![微信截图_20221228203317](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221228203317.png)





![微信截图_20221228205522](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221228205522.png)





![微信截图_20221228205545](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221228205545.png)







### 3、NameServer  

![微信截图_20221228205731](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221228205731.png)

  

![微信截图_20221228215631](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221228215631.png)



![微信截图_20221228220138](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221228220138.png)





### 4、路由发现  

![微信截图_20221228222835](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221228222835.png)





### 5、选择策略  

![微信截图_20221229205053](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221229205053.png)





### 6、broker    

消息实际上是保存到broker的队列中

并且每一个broker都有几个从结点

![微信截图_20221229205708](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221229205708.png)



![微信截图_20221229205802](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221229205802.png)





![微信截图_20221229210050](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221229210050.png)



![微信截图_20221229210201](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221229210201.png)





### 7、工作流程  

![微信截图_20221229212045](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221229212045.png)

  

![微信截图_20221229212937](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221229212937.png)



![微信截图_20221229215746](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221229215746.png)





![微信截图_20221230000454](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221230000454.png)
