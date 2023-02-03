# 	Elasticsearch



# 1.部署单点es

## 1.1.创建网络

因为我们还需要部署kibana容器，因此需要让es和kibana容器互联。这里先创建一个网络：

```sh
docker network create es-net
```



## 1.2.加载镜像

这里我们采用elasticsearch的7.12.1版本的镜像，这个镜像体积非常大，接近1G。不建议大家自己pull。

课前资料提供了镜像的tar包：

![image-20210510165308064](https://gitee.com/hongshenghyj/typora/raw/master/img/image-20210510165308064.png)

大家将其上传到虚拟机中，然后运行命令加载即可：

```sh
# 导入数据
docker load -i es.tar
```

同理还有`kibana`的tar包也需要这样做。



## 1.3.运行

运行docker命令，部署单点es：

```sh
docker run -d \
	--name es \
    -e "ES_JAVA_OPTS=-Xms512m -Xmx512m" \
    -e "discovery.type=single-node" \
    -v es-data:/usr/share/elasticsearch/data \
    -v es-plugins:/usr/share/elasticsearch/plugins \
    --privileged \
    --network es-net \
    -p 9200:9200 \
    -p 9300:9300 \
elasticsearch:7.12.1
```

命令解释：

- `-e "cluster.name=es-docker-cluster"`：设置集群名称
- `-e "http.host=0.0.0.0"`：监听的地址，可以外网访问
- `-e "ES_JAVA_OPTS=-Xms512m -Xmx512m"`：内存大小
- `-e "discovery.type=single-node"`：非集群模式
- `-v es-data:/usr/share/elasticsearch/data`：挂载逻辑卷，绑定es的数据目录
- `-v es-logs:/usr/share/elasticsearch/logs`：挂载逻辑卷，绑定es的日志目录
- `-v es-plugins:/usr/share/elasticsearch/plugins`：挂载逻辑卷，绑定es的插件目录
- `--privileged`：授予逻辑卷访问权
- `--network es-net` ：加入一个名为es-net的网络中
- `-p 9200:9200`：端口映射配置



在浏览器中输入：http://192.168.150.101:9200 即可看到elasticsearch的响应结果：

![image-20210506101053676](https://gitee.com/hongshenghyj/typora/raw/master/img/image-20210506101053676.png)





# 2.部署kibana

kibana可以给我们提供一个elasticsearch的可视化界面，便于我们学习。

## 2.1.部署

运行docker命令，部署kibana

```sh
docker run -d \
--name kibana \
-e ELASTICSEARCH_HOSTS=http://es:9200 \
--network=es-net \
-p 5601:5601  \
kibana:7.12.1
```

- `--network es-net` ：加入一个名为es-net的网络中，与elasticsearch在同一个网络中
- `-e ELASTICSEARCH_HOSTS=http://es:9200"`：设置elasticsearch的地址，因为kibana已经与elasticsearch在一个网络，因此可以用容器名直接访问elasticsearch
- `-p 5601:5601`：端口映射配置

kibana启动一般比较慢，需要多等待一会，可以通过命令：

```sh
docker logs -f kibana
```

查看运行日志，当查看到下面的日志，说明成功：

![image-20210109105135812](https://gitee.com/hongshenghyj/typora/raw/master/img/image-20210109105135812.png)

此时，在浏览器输入地址访问：http://192.168.150.101:5601，即可看到结果

## 2.2.DevTools

kibana中提供了一个DevTools界面：

![image-20210506102630393](https://gitee.com/hongshenghyj/typora/raw/master/img/image-20210506102630393.png)

这个界面中可以编写DSL来操作elasticsearch。并且对DSL语句有自动补全功能。



# 3.安装IK分词器



## 3.1.在线安装ik插件（较慢）

```shell
# 进入容器内部
docker exec -it elasticsearch /bin/bash

# 在线下载并安装
./bin/elasticsearch-plugin  install https://github.com/medcl/elasticsearch-analysis-ik/releases/download/v7.12.1/elasticsearch-analysis-ik-7.12.1.zip

#退出
exit
#重启容器
docker restart elasticsearch
```

## 3.2.离线安装ik插件（推荐）

### 1）查看数据卷目录

安装插件需要知道elasticsearch的plugins目录位置，而我们用了数据卷挂载，因此需要查看elasticsearch的数据卷目录，通过下面命令查看:

```sh
docker volume inspect es-plugins
```

显示结果：

```json
[
    {
        "CreatedAt": "2022-05-06T10:06:34+08:00",
        "Driver": "local",
        "Labels": null,
        "Mountpoint": "/var/lib/docker/volumes/es-plugins/_data",
        "Name": "es-plugins",
        "Options": null,
        "Scope": "local"
    }
]
```

说明plugins目录被挂载到了：`/var/lib/docker/volumes/es-plugins/_data `这个目录中。



### 2）解压缩分词器安装包

下面我们需要把课前资料中的ik分词器解压缩，重命名为ik

![image-20210506110249144](https://gitee.com/hongshenghyj/typora/raw/master/img/image-20210506110249144.png)

### 3）上传到es容器的插件数据卷中

也就是`/var/lib/docker/volumes/es-plugins/_data `：

![image-20210506110704293](https://gitee.com/hongshenghyj/typora/raw/master/img/image-20210506110704293.png)



###  4）重启容器

```shell
# 4、重启容器
docker restart es
```

```sh
# 查看es日志
docker logs -f es
```

### 5）测试：

IK分词器包含两种模式：

* `ik_smart`：最少切分

* `ik_max_word`：最细切分



```json
GET /_analyze
{
  "analyzer": "ik_max_word",
  "text": "黑马程序员学习java太棒了"
}
```

结果：

```json
{
  "tokens" : [
    {
      "token" : "黑马",
      "start_offset" : 0,
      "end_offset" : 2,
      "type" : "CN_WORD",
      "position" : 0
    },
    {
      "token" : "程序员",
      "start_offset" : 2,
      "end_offset" : 5,
      "type" : "CN_WORD",
      "position" : 1
    },
    {
      "token" : "程序",
      "start_offset" : 2,
      "end_offset" : 4,
      "type" : "CN_WORD",
      "position" : 2
    },
    {
      "token" : "员",
      "start_offset" : 4,
      "end_offset" : 5,
      "type" : "CN_CHAR",
      "position" : 3
    },
    {
      "token" : "学习",
      "start_offset" : 5,
      "end_offset" : 7,
      "type" : "CN_WORD",
      "position" : 4
    },
    {
      "token" : "java",
      "start_offset" : 7,
      "end_offset" : 11,
      "type" : "ENGLISH",
      "position" : 5
    },
    {
      "token" : "太棒了",
      "start_offset" : 11,
      "end_offset" : 14,
      "type" : "CN_WORD",
      "position" : 6
    },
    {
      "token" : "太棒",
      "start_offset" : 11,
      "end_offset" : 13,
      "type" : "CN_WORD",
      "position" : 7
    },
    {
      "token" : "了",
      "start_offset" : 13,
      "end_offset" : 14,
      "type" : "CN_CHAR",
      "position" : 8
    }
  ]
}
```





## 3.3 扩展词词典

随着互联网的发展，“造词运动”也越发的频繁。出现了很多新的词语，在原有的词汇列表中并不存在。比如：“奥力给”，“传智播客” 等。

所以我们的词汇也需要不断的更新，IK分词器提供了扩展词汇的功能。

1）打开IK分词器config目录：

![image-20210506112225508](https://gitee.com/hongshenghyj/typora/raw/master/img/image-20210506112225508.png)

2）在IKAnalyzer.cfg.xml配置文件内容添加：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE properties SYSTEM "http://java.sun.com/dtd/properties.dtd">
<properties>
        <comment>IK Analyzer 扩展配置</comment>
        <!--用户可以在这里配置自己的扩展字典 *** 添加扩展词典-->
        <entry key="ext_dict">ext.dic</entry>
</properties>
```

3）新建一个 ext.dic，可以参考config目录下复制一个配置文件进行修改

```properties
传智播客
奥力给
```

4）重启elasticsearch 

```sh
docker restart es

# 查看 日志
docker logs -f elasticsearch
```

![image-20201115230900504](https://gitee.com/hongshenghyj/typora/raw/master/img/image-20201115230900504.png)

日志中已经成功加载ext.dic配置文件

5）测试效果：

```json
GET /_analyze
{
  "analyzer": "ik_max_word",
  "text": "传智播客Java就业超过90%,奥力给！"
}
```

> 注意当前文件的编码必须是 UTF-8 格式，严禁使用Windows记事本编辑

## 3.4 停用词词典

在互联网项目中，在网络间传输的速度很快，所以很多语言是不允许在网络上传递的，如：关于宗教、政治等敏感词语，那么我们在搜索时也应该忽略当前词汇。

IK分词器也提供了强大的停用词功能，让我们在索引时就直接忽略当前的停用词汇表中的内容。

1）IKAnalyzer.cfg.xml配置文件内容添加：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE properties SYSTEM "http://java.sun.com/dtd/properties.dtd">
<properties>
        <comment>IK Analyzer 扩展配置</comment>
        <!--用户可以在这里配置自己的扩展字典-->
        <entry key="ext_dict">ext.dic</entry>
         <!--用户可以在这里配置自己的扩展停止词字典  *** 添加停用词词典-->
        <entry key="ext_stopwords">stopword.dic</entry>
</properties>
```

3）在 stopword.dic 添加停用词

```properties
习大大
```

4）重启elasticsearch 

```sh
# 重启服务
docker restart elasticsearch
docker restart kibana

# 查看 日志
docker logs -f elasticsearch
```

日志中已经成功加载stopword.dic配置文件

5）测试效果：

```json
GET /_analyze
{
  "analyzer": "ik_max_word",
  "text": "传智播客Java就业率超过95%,习大大都点赞,奥力给！"
}
```

> 注意当前文件的编码必须是 UTF-8 格式，严禁使用Windows记事本编辑





# 4.部署es集群

部署es集群可以直接使用docker-compose来完成，不过要求你的Linux虚拟机至少有**4G**的内存空间



首先编写一个docker-compose文件，内容如下：

```sh
version: '2.2'
services:
  es01:
    image: docker.elastic.co/elasticsearch/elasticsearch:7.12.1
    container_name: es01
    environment:
      - node.name=es01
      - cluster.name=es-docker-cluster
      - discovery.seed_hosts=es02,es03
      - cluster.initial_master_nodes=es01,es02,es03
      - bootstrap.memory_lock=true
      - "ES_JAVA_OPTS=-Xms512m -Xmx512m"
    ulimits:
      memlock:
        soft: -1
        hard: -1
    volumes:
      - data01:/usr/share/elasticsearch/data
    ports:
      - 9200:9200
    networks:
      - elastic
  es02:
    image: docker.elastic.co/elasticsearch/elasticsearch:7.12.1
    container_name: es02
    environment:
      - node.name=es02
      - cluster.name=es-docker-cluster
      - discovery.seed_hosts=es01,es03
      - cluster.initial_master_nodes=es01,es02,es03
      - bootstrap.memory_lock=true
      - "ES_JAVA_OPTS=-Xms512m -Xmx512m"
    ulimits:
      memlock:
        soft: -1
        hard: -1
    volumes:
      - data02:/usr/share/elasticsearch/data
    networks:
      - elastic
  es03:
    image: docker.elastic.co/elasticsearch/elasticsearch:7.12.1
    container_name: es03
    environment:
      - node.name=es03
      - cluster.name=es-docker-cluster
      - discovery.seed_hosts=es01,es02
      - cluster.initial_master_nodes=es01,es02,es03
      - bootstrap.memory_lock=true
      - "ES_JAVA_OPTS=-Xms512m -Xmx512m"
    ulimits:
      memlock:
        soft: -1
        hard: -1
    volumes:
      - data03:/usr/share/elasticsearch/data
    networks:
      - elastic

volumes:
  data01:
    driver: local
  data02:
    driver: local
  data03:
    driver: local

networks:
  elastic:
    driver: bridge
```



Run `docker-compose` to bring up the cluster:

```sh
docker-compose up
```









# 笔记

## 一、简介

### 概念

![微信截图_20221225015128](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221225015128.png)



用途

![微信截图_20221225015357](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221225015357.png)



elastic stack介绍

![微信截图_20221225015500](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221225015500.png)





### 发展

![微信截图_20221225015630](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221225015630.png)





![微信截图_20221225015700](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221225015700.png)





![微信截图_20221225015751](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221225015751.png)





## **二、结构**



### 倒排索引



传统数据库

![微信截图_20221225015919](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221225015919.png)





elasticsearch使用了倒排索引机制

![微信截图_20221225020442](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221225020442.png)





![微信截图_20221225020508](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221225020508.png)







### 文档

>一个数据就是一条文档，用json存储

![微信截图_20221225020616](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221225020616.png)





### 索引

![微信截图_20221225020742](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221225020742.png)





### 对比

![微信截图_20221225020856](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221225020856.png)





### 架构

>和mysql等数据库一起发挥作用，el擅长搜索

![微信截图_20221225021321](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221225021321.png)





### 总结

![微信截图_20221225021340](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221225021340.png)





### 分词器

>决定搜索关键词怎么样分词的，默认分词器对中文不太友好，keyword不分词

![微信截图_20230103035544](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230103035544.png)



>我们要自动引入分词器，看上面笔记

![微信截图_20230103041051](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230103041051.png)







### **mapping**

>类似于约束条件，keyword类型不分词，精准查询

![微信截图_20230103043229](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230103043229.png)







## 三、DSL

### 索引库

#### 创建

![微信截图_20230103043446](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230103043446.png)



![微信截图_20230103045814](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230103045814.png)





#### 查看和删除

![微信截图_20230103045834](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230103045834.png)





#### 修改

>只能添加新的字段

![微信截图_20230103045938](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230103045938.png)





![微信截图_20230103050255](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230103050255.png)









### 文档

#### 添加

![微信截图_20230103100117](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230103100117.png)





#### 查看和删除

![微信截图_20230103100639](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230103100639.png)







#### 修改

>一种是删除旧文档，一种是修改指定值

![微信截图_20230103101114](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230103101114.png)











### 和数据库对应

数据库结构

![微信截图_20230103220459](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230103220459.png)





![微信截图_20230103221812](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230103221812.png)





### 关联

可以让多个字段关联，然后指定一个新的字段，这样子分词的时候就会考虑多个字段

![微信截图_20230103222050](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230103222050.png)





### **查询**(重要)

#### 分类

![微信截图_20230104180614](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230104180614.png)







#### 基本查询

>match_all查询全部

![微信截图_20230104180831](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230104180831.png)





#### 全文检索

![微信截图_20230104182127](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230104182127.png)



![微信截图_20230104183204](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230104183204.png)





#### 精准查询

![微信截图_20230104183712](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230104183712.png)



![微信截图_20230104183934](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230104183934.png)





#### 地理查询

![微信截图_20230104184204](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230104184204.png)



![微信截图_20230104184230](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230104184230.png)







#### 复合查询

![微信截图_20230105022216](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230105022216.png)



#### 算分

![微信截图_20230105022652](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230105022652.png)



![微信截图_20230105182500](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230105182500.png)





![微信截图_20230105182527](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230105182527.png)





#### 布尔查询

![微信截图_20230105185957](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230105185957.png)



案例

![微信截图_20230105190333](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230105190333.png)





#### 排序

![微信截图_20230105192420](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230105192420.png)



两种写法

![微信截图_20230105192748](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230105192748.png)



![微信截图_20230105192936](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230105192936.png)







#### 分页

![微信截图_20230105193801](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230105193801.png)





![微信截图_20230105194033](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230105194033.png)





![微信截图_20230105194051](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230105194051.png)









#### **高亮**

![微信截图_20230105194246](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230105194246.png)



#### 总结

![微信截图_20230105195023](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230105195023.png)











## 四、JAVA操作



### 依赖

![微信截图_20230103222352](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230103222352.png)



![微信截图_20230103223343](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230103223343.png)





### RestHighLeveLClient注入

>这里用了spring的aop执行操作前先创建对象，最后关闭连接

![微信截图_20230103223849](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230103223849.png)







### 索引库

#### 创建

>这里要传进去一个json

![微信截图_20230103224054](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230103224054.png)



![微信截图_20230103224758](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230103224758.png)





数据

![微信截图_20230103224811](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230103224811.png)







#### 删除和判断索引库是否存在

![微信截图_20230103224941](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230103224941.png)







### 文档操作

![微信截图_20230103225344](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230103225344.png)





#### 添加



![微信截图_20230103225801](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230103225801.png)



![微信截图_20230103230817](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230103230817.png)





#### 查询

![微信截图_20230103231023](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230103231023.png)



![微信截图_20230103231456](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230103231456.png)





#### 修改

![微信截图_20230103232244](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230103232244.png)





#### 删除

![微信截图_20230104171022](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230104171022.png)







#### 批量导入

![微信截图_20230104171632](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230104171632.png)



![微信截图_20230104174532](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230104174532.png)











### **查询操作(重要)**

#### 注意

```tex
must：返回的文档必须满足must子句的条件，并且参与计算分值
filter：返回的文档必须满足filter子句的条件。但是跟Must不一样的是，不会计算分值， 并且可以使用缓存
must和filter是一样的。区别是场景不一样。如果结果需要算分就使用must，否则可以考虑使用filter，使查询更高效。
```



#### 查询全部

![微信截图_20230108230007](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230108230007.png)



解析

![微信截图_20230108231414](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230108231414.png)





#### 字段分词查询

![微信截图_20230108233410](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230108233410.png)







#### 精准查询

![微信截图_20230108233550](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230108233550.png)



![微信截图_20230108233650](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230108233650.png)

```java

SearchRequest request = new SearchRequest("hotel");

BoolQueryBuilder boolQueryBuilder = QueryBuilders.boolQuery();
//添加Must条件
boolQueryBuilder.must(QueryBuilders.termQuery("city","杭州"));
//添加range条件
boolQueryBuilder.filter(QueryBuilders.rangeQuery("price").lt(250));

request.source().query(QueryBuilders.multiMatchQuery("如家","name","business"));
SearchResponse response = restHighLevelClient.search(request, RequestOptions.DEFAULT);

//解析
SearchHits hits = response.getHits();
SearchHit[] hits1 = hits.getHits();
for(SearchHit searchHit : hits1){
    String sourceAsString = searchHit.getSourceAsString();
    Hotel hotel = JSON.parseObject(sourceAsString, Hotel.class);
    HotelDoc hotelDoc = new HotelDoc(hotel);
    System.out.println(hotelDoc);
}
```



#### 排序和分页

![微信截图_20230108234452](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230108234452.png)





#### 高亮

![微信截图_20230108234700](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230108234700.png)



```Java
SearchRequest request = new SearchRequest("hotel");
//查询
 request.source().query(QueryBuilders.multiMatchQuery("如家","name","business"));
// request.source().query(QueryBuilders.matchQuery("{all}","如家"));

//添加高亮
request.source().highlighter(new HighlightBuilder()
                .field("name").requireFieldMatch(false));
SearchResponse response = restHighLevelClient.search(request, RequestOptions.DEFAULT);
//解析
SearchHits hits = response.getHits();
SearchHit[] hits1 = hits.getHits();
for(SearchHit searchHit : hits1){
    Map<String, HighlightField> highlightFields = searchHit.getHighlightFields();
    HighlightField name = highlightFields.get("name");
    System.out.println(name);
}
```









### 黑马旅游

#### 定义接受类

>key是查询字段

![微信截图_20230111025718](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230111025718.png)





![微信截图_20230111030804](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230111030804.png)



#### 导入bean

```Java
/**
 * 注入el的bean
 * @return
 */
@Bean
public RestHighLevelClient client(){
   return  new RestHighLevelClient(RestClient.builder(
            HttpHost.create("ip地址")
    ));
}
```







#### 条件过滤

![微信截图_20230112212106](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230112212106.png)



![微信截图_20230112212507](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230112212507.png)





#### 距离排序

![微信截图_20230112221128](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230112221128.png)





#### 广告置顶

![微信截图_20230112222803](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230112222803.png)



![微信截图_20230112223512](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230112223512.png)



算分控制

![微信截图_20230112224246](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230112224246.png)







#### 总代码

```java

    @Autowired
    private RestHighLevelClient client;

    /**
     * 搜索功能
     * @param requestParam
     * @return
     */
    @Override
    public PageResult search(RequestParams requestParam) {
        System.out.println(requestParam);
        //准备request
        SearchRequest request = new SearchRequest("hotel");
        //准备DSL
        String key = requestParam.getKey();
        //构建booleanQuery  因为要多个条件查询
        BoolQueryBuilder boolQueryBuilder = QueryBuilders.boolQuery();
        //判断是否为空
        if(key == null || key.equals("")){
           boolQueryBuilder.must(QueryBuilders.matchAllQuery());
        }else {
            boolQueryBuilder.must(QueryBuilders.matchQuery("all",key));
        }
        //条件过滤
        //城市
        if(requestParam.getCity() != null && !requestParam.getCity().equals("") ){
            boolQueryBuilder.filter(QueryBuilders.termQuery("city",requestParam.getCity()));
        }
        //品牌
        if(requestParam.getBrand() != null && !requestParam.getBrand().equals("") ){
            boolQueryBuilder.filter(QueryBuilders.termQuery("brand",requestParam.getBrand()));
        }
        //星级
        if(requestParam.getStarName() != null && !requestParam.getStarName().equals("")){
            boolQueryBuilder.filter(QueryBuilders.termQuery("starName",requestParam.getStarName()));
        }

        if(requestParam.getMinPrice() != null && !requestParam.getMinPrice().equals("")){
            boolQueryBuilder.filter(QueryBuilders.rangeQuery("price")
                    .gte(requestParam.getMinPrice())
                    .lte(requestParam.getMaxPrice()));
        }

        //算分查询
        FunctionScoreQueryBuilder functionScoreQueryBuilder =
                QueryBuilders.functionScoreQuery(
                        //原始查询
                        boolQueryBuilder,
                        //算法数组
                        new FunctionScoreQueryBuilder.FilterFunctionBuilder[]{
                                new FunctionScoreQueryBuilder.FilterFunctionBuilder(
                                        //过滤条件
                                        QueryBuilders.termQuery("isAD","true"),
                                        //算分函数
                                        ScoreFunctionBuilders.weightFactorFunction(10)
                                )
                        });

        request.source().query(functionScoreQueryBuilder);

        //地理坐标排序功能
        String location = requestParam.getLocation();
        if(location !=null && !location.equals("")){
            request.source().sort(SortBuilders
                    .geoDistanceSort("location",new GeoPoint(location))
                    .order(SortOrder.ASC)
                    .unit(DistanceUnit.KILOMETERS));
        }

        //分页
         int page = requestParam.getPage();
         int size = requestParam.getSize();
        request.source().from((page - 1)*size).size(size);

        //发送请求
        SearchResponse response = null;
        try {
            response = client.search(request, RequestOptions.DEFAULT);
        } catch (IOException e) {
            throw new RuntimeException(e);
        }

        //解析
        SearchHits hits = response.getHits();
        SearchHit[] hits1 = hits.getHits();
        //获取总的数量  包括不在分页里面的
        Long value = hits.getTotalHits().value;
        //返回对象
        PageResult pageResult = new PageResult();
        List<HotelDoc>list = new ArrayList<>();

        for (SearchHit searchHit : hits1) {
            String sourceAsString = searchHit.getSourceAsString();
            HotelDoc hotel = JSON.parseObject(sourceAsString, HotelDoc.class);
            //获取排序值(距离)
            Object[] sortValues = searchHit.getSortValues();
            if(sortValues !=null && sortValues.length > 0){
                 hotel.setDistance(sortValues[0]);
            }
            list.add(hotel);
        }
        pageResult.setHotels(list);
        pageResult.setTotal((long) list.size());
        return new PageResult(value,list);
```







#### 聚合

分类

![微信截图_20230114233931](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230114233931.png)





![微信截图_20230114235519](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230114235519.png)





![微信截图_20230115000011](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230115000011.png)





![微信截图_20230115000151](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230115000151.png)





![微信截图_20230115000522](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230115000522.png)





![微信截图_20230115000945](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230115000945.png)



![微信截图_20230115001144](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230115001144.png)



解析聚合

![微信截图_20230115002521](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230115002521.png)







#### 实现代码

![微信截图_20230115003332](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230115003332.png)





```java
/**
 * 根据dsl聚合查询标签
 * @return
 */
@Override
public Map<String, List<String>> filters(RequestParams requestParam) {
    //准备request
    SearchRequest request = new SearchRequest("hotel");
    //准备DSL
    String key = requestParam.getKey();
    //构建booleanQuery  因为要多个条件查询
    BoolQueryBuilder boolQueryBuilder = QueryBuilders.boolQuery();
    //判断是否为空
    if(key == null || key.equals("")){
        boolQueryBuilder.must(QueryBuilders.matchAllQuery());
    }else {
        boolQueryBuilder.must(QueryBuilders.matchQuery("{all}",key));
    }
    //条件过滤
    //城市
    if(requestParam.getCity() != null && !requestParam.getCity().equals("") ){
        boolQueryBuilder.filter(QueryBuilders.termQuery("city",requestParam.getCity()));
    }
    //品牌
    if(requestParam.getBrand() != null && !requestParam.getBrand().equals("") ){
        boolQueryBuilder.filter(QueryBuilders.termQuery("brand",requestParam.getBrand()));
    }
    //星级
    if(requestParam.getStarName() != null && !requestParam.getStarName().equals("")){
        boolQueryBuilder.filter(QueryBuilders.termQuery("starName",requestParam.getStarName()));
    }

    if(requestParam.getMinPrice() != null && !requestParam.getMinPrice().equals("")){
        boolQueryBuilder.filter(QueryBuilders.rangeQuery("price")
                .gte(requestParam.getMinPrice())
                .lte(requestParam.getMaxPrice()));
    }

    //算分查询
    FunctionScoreQueryBuilder functionScoreQueryBuilder =
            QueryBuilders.functionScoreQuery(
                    //原始查询
                    boolQueryBuilder,
                    //算法数组
                    new FunctionScoreQueryBuilder.FilterFunctionBuilder[]{
                            new FunctionScoreQueryBuilder.FilterFunctionBuilder(
                                    //过滤条件
                                    QueryBuilders.termQuery("isAD","true"),
                                    //算分函数
                                    ScoreFunctionBuilders.weightFactorFunction(10)
                            )
                    });

    request.source().query(functionScoreQueryBuilder);
    //设置size
    request.source().size(0);
    //设置聚合
    request.source().aggregation(AggregationBuilders
            .terms("brandAgg")
            .field("brand")
            .size(100));
    request.source().aggregation(AggregationBuilders
            .terms("cityAgg")
            .field("city")
            .size(100));
    request.source().aggregation(AggregationBuilders
            .terms("starNameAgg")
            .field("starName")
            .size(100));

    SearchResponse response = null;
    try {
        response = client.search(request, RequestOptions.DEFAULT);
    } catch (IOException e) {
        throw new RuntimeException(e);
    }
    Map<String,List<String>>map = new HashMap<>();
    Aggregations aggregations = response.getAggregations();
    List<String> brandAgg = parse(aggregations, "brandAgg");
    List<String> cityAgg = parse(aggregations, "cityAgg");
    List<String> starNameAgg = parse(aggregations, "starNameAgg");
    map.put("品牌",brandAgg);
    map.put("城市",cityAgg);
    map.put("星级",starNameAgg);
    return map;
}
```

```java
/**
 * 解析
 * @return
 */
static List<String> parse(Aggregations aggregations,String str){
    List<String> list = new ArrayList<>();
    Terms term = aggregations.get(str);
    List<? extends Terms.Bucket> buckets = term.getBuckets();
    for (Terms.Bucket bucket : buckets) {
        String key = bucket.getKeyAsString();
        list.add(key);
    }
    return  list;
}
```









## 五、自动补全

### 拼音分词

![微信截图_20230120224425](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230120224425.png)



### 自定义分词

![微信截图_20230120231142](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230120231142.png)



创建索引库配置分词器

![微信截图_20230120231421](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230120231421.png)





### 使用注意

![微信截图_20230120232618](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230120232618.png)



搜索时候用ik_smart分词器

![微信截图_20230120232702](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230120232702.png)





![微信截图_20230120232835](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230120232835.png)





### completion suggester查询

![微信截图_20230120234003](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230120234003.png)





![微信截图_20230120234116](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230120234116.png)







![微信截图_20230127080333](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230127080333.png)







### 项目实现自动补全

![微信截图_20230127081542](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230127081542.png)



![微信截图_20230127083752](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230127083752.png)



![微信截图_20230127083902](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230127083902.png)



>创建索引库

```json
PUT /hotel
{
  "settings": {
    "analysis": {
      "analyzer": {
        "text_anlyzer": {
          "tokenizer": "ik_max_word",
          "filter": "py"
        },
        "completion_analyzer": {
          "tokenizer": "keyword",
          "filter": "py"
        }
      },
      "filter": {
        "py": {
          "type": "pinyin",
          "keep_full_pinyin": false,
          "keep_joined_full_pinyin": true,
          "keep_original": true,
          "limit_first_letter_length": 16,
          "remove_duplicated_term": true,
          "none_chinese_pinyin_tokenize": false
        }
      }
    }
  },
  "mappings": {
    "properties": {
      "id":{
        "type": "keyword"
      },
      "name":{
        "type": "text",
        "analyzer": "text_anlyzer",
        "search_analyzer": "ik_smart",
        "copy_to": "all"
      },
      "address":{
        "type": "keyword",
        "index": false
      },
      "price":{
        "type": "integer"
      },
      "score":{
        "type": "integer"
      },
      "brand":{
        "type": "keyword",
        "copy_to": "all"
      },
      "city":{
        "type": "keyword"
      },
      "starName":{
        "type": "keyword"
      },
      "business":{
        "type": "keyword",
        "copy_to": "all"
      },
      "location":{
        "type": "geo_point"
      },
      "pic":{
        "type": "keyword",
        "index": false
      },
      "all":{
        "type": "text",
        "analyzer": "text_anlyzer",
        "search_analyzer": "ik_smart"
      },
      "suggestion":{
          "type": "completion",
          "analyzer": "completion_analyzer"
      }
    }
  }
}

```





![微信截图_20230127091330](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230127091330.png)





![微信截图_20230127092440](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230127092440.png)





```java
/**
 * 自动补全
 * @param prefix
 * @return
 */
@Override
public List<String> getSuggestions(String prefix) {
    List<String> list  = new ArrayList<>();
    try {
        //准备request
        SearchRequest request = new SearchRequest("hotel");
        //准备dsl
        request.source().suggest(new SuggestBuilder().addSuggestion(
                "suggestions",
                SuggestBuilders.completionSuggestion("suggestion")
                        .prefix(prefix)
                        .skipDuplicates(true)
                        .size(10)
        ));
        SearchResponse response = client.search(request, RequestOptions.DEFAULT);
        Suggest suggest = response.getSuggest();
        CompletionSuggestion suggestions = suggest.getSuggestion("suggestions");
        List<CompletionSuggestion.Entry.Option> options = suggestions.getOptions();
        for (CompletionSuggestion.Entry.Option option : options) {
            list.add(option.getText().toString());
        }
    } catch (IOException e) {
        throw new RuntimeException(e);
    }
    return list;
}
```



