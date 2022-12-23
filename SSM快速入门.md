# SSM快速入门

## 注意事项

配置文件最上面的命名空间有缺少，要什么引入什么，比如mvc,context，复制一下改一下名字就行

数据库如果是8.0以上。链接时候要加jc

启动tmcat时候  创建maven工程 选webapp  然后配置tmocat  最后启动

## 补内容

aop

事物

源码

## 一、了解spring

### 1、简介

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220720033750.png" alt="微信截图_20220720033750" style="zoom:50%;" />

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20220720035104.png" alt="微信截图_20220720035104" style="zoom:50%;" />

<img src="C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220720035544.png" alt="微信截图_20220720035544" style="zoom: 50%;" />

<img src="C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220720035807.png" alt="微信截图_20220720035807" style="zoom:50%;" />



### 2、分层思想

spring是将一些内容配置到文件中，从而降低耦合性，让代码维护起来更加方便

![微信截图_20220825201750](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220825201750.png)



<img src="C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220720040417.png" alt="微信截图_20220720040417" style="zoom:67%;" />

### 3、简介

![微信截图_20220825202241](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220825202241.png)



![微信截图_20220825203144](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220825203144.png)

![微信截图_20220825203655](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220825203655.png)

## 二、开发

### 第一个程序

![微信截图_20220825211113](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220825211113.png)

```java
ApplicationContext app=new ClassPathXmlApplicationContext("applicationContext.xml");
UserService service= (UserService) app.getBean("userService");//获取id
service.save();
```

![微信截图_20220825211128](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220825211128.png)

这时候serviceImpl里面的dao还是new生成的，还没有注入

### 1、开发步骤

spring是基于maven的，所以maven要有一定了解，包括坐标什么的一定要清楚

![微信截图_20220720040711](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220720040711.png)



### 2、导入坐标

<img src="C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220721054311.png" alt="微信截图_20220721054311" style="zoom:67%;" />

### 3、常见错误

有时候会找不到文件，可以把JDK设置为8就可以了，可能是版本问题

<img src="C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220721060654.png" alt="微信截图_20220721060654" style="zoom:50%;" />



<img src="C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220721060816.png" alt="微信截图_20220721060816" style="zoom:50%;" />

### **4、bean**(重要)

![微信截图_20220825221935](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220825221935.png)



![微信截图_20220825223259](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220825223259.png)

<img src="C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220721061755.png" alt="微信截图_20220721061755" style="zoom:50%;" />



#### 4.1配置范围

![微信截图_20220825223808](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220825223808.png)



<img src="C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220721061937.png" alt="微信截图_20220721061937" style="zoom:50%;" />

<img src="C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220721141645.png" alt="微信截图_20220721141645" style="zoom:67%;" />

![微信截图_20220825224035](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220825224035.png)



#### 4.2生命周期

![微信截图_20220721142522](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220721142522.png)

![微信截图_20220825235117](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220825235117.png)

![微信截图_20220825235136](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220825235136.png)

总结：

![微信截图_20220825235224](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220825235224.png)



#### 4.3实例化(重要)



![微信截图_20220721143445](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220721143445.png)

![微信截图_20220825224958](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220825224958.png)



**在UserviceImpl里面有UserDao对象，先在文件里面创建，然后在外面直接调service层**

**第一个userDao是set方法后的名字，第一个字母变成小写，第二个是指定id**

```xml
<bean id="userDao" class="com.it.dao.impl.UserDaoImpl"></bean>
<bean id="userService" class="com.it.service.impl.UserServiceImpl">
    //配置service和dao关系
    <property name="userDao" ref="userDao"></property>
</bean>
```

```java
public static void main(String[] args) {
    ApplicationContext app=new ClassPathXmlApplicationContext("applicationContext.xml");
    UserService service= (UserService) app.getBean("userService");
    service.save();
}
```



第二种：

![微信截图_20220825225634](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220825225634.png)

![微信截图_20220721143511](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220721143511.png)



第三种：

![微信截图_20220825232024](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220825232024.png)

![微信截图_20220721143521](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220721143521.png)

![微信截图_20220721144113](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220721144113.png)



第四种

![微信截图_20220825233421](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220825233421.png)

依赖配置文件

第二种更加方便

<img src="C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220721145911.png" alt="微信截图_20220721145911" style="zoom:50%;" />

<img src="C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220721150305.png" alt="微信截图_20220721150305" style="zoom:50%;" />





#### 总结

如果容器多个一样类型的bean  那么自动注入的时候字段名字要和id一样 否则无法装配

![微信截图_20220826233615](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220826233615.png)





### **5、依赖注入**(重要)

<img src="C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220721150305.png" alt="微信截图_20220721150305" style="zoom: 67%;" />



set方法用的比较多

这里的id如果是唯一的  自动注入的变量不用和id一致

![](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220825221422.png)

![微信截图_20220721152525](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220721152525.png)

<img src="C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220721155318.png" alt="微信截图_20220721155318" style="zoom:50%;" />



#### 1、set方法注入

name是set方法后面的名字，首字母小写，ref是指向哪个id

![微信截图_20220721155422](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220721155422.png)

引用类型：

name要和set方法一样，首字母小写

<img src="C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220826002447.png" alt="微信截图_20220826002447" style="zoom:67%;" />



基本数据类型：

<img src="C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220826003041.png" alt="微信截图_20220826003041" style="zoom:67%;" />







#### 2、构造器注入

![微信截图_20220721160656](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220721160656.png)

![微信截图_20220721160628](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220721160628.png)



![微信截图_20220826004003](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220826004003.png)

#### **3、注入数据类型**

![微信截图_20220721160827](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220721160827.png)



引用

![微信截图_20220721163336](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220721163336.png)

![微信截图_20220721170007](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220721170007.png)

这里的map中的key是一个类，所以要引用下面的user1

![微信截图_20220721171408](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220721171408.png)



#### **4、自动装配**

![微信截图_20220826010940](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220826010940.png)





![微信截图_20220826010952](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220826010952.png)



#### 5、集合

![微信截图_20220826215747](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220826215747.png)

![微信截图_20220826215803](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220826215803.png)

![微信截图_20220826215814](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220826215814.png)



### 6、注入依赖总结

<img src="C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220721171435.png" alt="微信截图_20220721171435" style="zoom:67%;" />

![微信截图_20220826233735](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220826233735.png)

### 7、API

![微信截图_20220721171841](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220721171841.png)



![微信截图_20220721172300](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220721172300.png)

![微信截图_20220722015848](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220722015848.png)





### 8、数据源

#### 1、作用

![微信截图_20220722020420](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220722020420.png)

#### 2、步骤



![微信截图_20220722020620](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220722020620.png)

#### 3、注意事项

记住这里导入包要等级高一点，要不然报错

![微信截图_20220722023722](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220722023722.png)



#### **4、配置数据源文件**

![微信截图_20220722032118](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220722032118.png)



![微信截图_20220722032131](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220722032131.png)

和加载类是一样的，先加载文件，然后加载bean

#### 5、抽取配置文件

<img src="C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220722032659.png" alt="微信截图_20220722032659" style="zoom:67%;" />

加载数据源

![微信截图_20220722033600](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220722033600.png)

![微信截图_20220826224748](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220826224748.png)



### 9、配置文件加载

![微信截图_20220826225835](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220826225835.png)









### 10、容器

![微信截图_20220826231748](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220826231748.png)



![微信截图_20220826231758](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220826231758.png)

![微信截图_20220826232446](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220826232446.png)

## 三、注解

用注解可以代替配置，简化开发

### 1、初始注解

![微信截图_20220722033817](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220722033817.png)

在这Com[onent相当于在文件中国配置bean

下面三个作用一样，只是为了可读性区分

Autowired相当于注入属性



### **2、组件扫描(重点)**

只有扫描才能知道配了注解

![微信截图_20220722160135](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220722160135.png)



### 3、注意事项

引入约束，要不然扫描会报错

![微信截图_20220722170941](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220722170941.png)



### 4、具体代码如下

配置扫描器和数据源

![微信截图_20220722170959](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220722170959.png)

![微信截图_20220722171010](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220722171010.png)

![微信截图_20220722171028](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220722171028.png)

这里为了辨别service层,所以用service代替了Component



![微信截图_20220722173256](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220722173256.png)



数据库

![微信截图_20220722183453](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220722183453.png)

![微信截图_20220722183700](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220722183700.png)



### 9、bean注解总结

![微信截图_20220827001225](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220827001225.png)



![微信截图_20220827001234](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220827001234.png)



![微信截图_20220827011042](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220827011042.png)

![微信截图_20220827011723](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220827011723.png)



![微信截图_20220827011733](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220827011733.png)





### 5、新注解(重要)

配置类写到config中

![微信截图_20220827003213](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220827003213.png)



![微信截图_20220827003631](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220827003631.png)

<img src="C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220722184705.png" alt="微信截图_20220722184705" style="zoom:67%;" />

<img src="C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220722184722.png" alt="微信截图_20220722184722" style="zoom:67%;" />

#### 5.1加载文件

多个用数组就行了

```Java
@Configuration
@ComponentScan({"com.it.domain","com.it.mapper","com.it.service","com.it.controller"})//扫描的地方
@PropertySources({@PropertySource("classpath:jdbc.properties")})//加载外部文件
@Import({jdbcConfig.class,mybatisConfig.class})//导入其他配置
public class springConfig {

}
```

![微信截图_20220827012033](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220827012033.png)

#### 5.2导入其他配置类

![微信截图_20220827012819](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220827012819.png)



![微信截图_20220827012911](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220827012911.png)



#### 5.3第三方bean注入

![微信截图_20220827013250](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220827013250.png)



![微信截图_20220827013308](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220827013308.png)

代码如下：

![微信截图_20220723001027](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723001027.png)

![微信截图_20220723001037](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723001037.png)

![微信截图_20220723001049](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723001049.png)

![微信截图_20220723001102](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723001102.png)



![微信截图_20220723001113](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723001113.png)

![微信截图_20220723001122](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723001122.png)





### **6、junit**



![微信截图_20220723001322](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723001322.png)

![微信截图_20220723003056](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723003056.png)

![微信截图_20220723020926](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723020926.png)



![](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220828200841.png)





### 7、application和监听器的应用

![微信截图_20220723031917](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723031917.png)

![微信截图_20220723033842](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723033842.png)

监听器放到最上面

![微信截图_20220723033857](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723033857.png)

![微信截图_20220723033908](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723033908.png)



### 8、监听器优化

![微信截图_20220723035943](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723035943.png)

![微信截图_20220723040940](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723040940.png)

![微信截图_20220723041014](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723041014.png)



### **10、注解和xml**

![微信截图_20220827013735](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220827013735.png)

## **四、springmvc**

直接创建maven工程，导入web就行了

### 1、简介

![微信截图_20220723041455](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723041455.png)

![微信截图_20220723131649](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723131649.png)





### **2、配置和快速入门**(重点记住)

![微信截图_20220723131813](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723131813.png)

命名空间

![微信截图_20220723180109](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723180109.png)

导入坐标和配置是关键

导入坐标



<img src="C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723135118.png" alt="微信截图_20220723135118" style="zoom: 200%;" />

这里可以用requestmapping获取请求

![微信截图_20220723135129](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723135129.png)

![微信截图_20220723135153](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723135153.png)



配置核心控制器

**并且引入springmvc和核心配置文件     下面的/代表地址加/加requestmapping直接访问到相关地址**

加载mvc配置文件

![微信截图_20220723135343](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723135343.png)

![微信截图_20220723140011](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723140011.png)

![微信截图_20220723140135](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723140135.png)





### 3、流程解析

![微信截图_20220723142141](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723142141.png)

![微信截图_20220723143117](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723143117.png)

![微信截图_20220723143351](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723143351.png)



这里创建Controller 用注解

然后可以通过/xxx/quick访问到save里面的方法

和web阶段差不多，return 是直接return到指定页面

![微信截图_20220723144304](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723144304.png)

​	也可以指定请求方法

![微信截图_20220723144407](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723144407.png)



### 4、mvc注解

![微信截图_20220723144517](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723144517.png)

如果指定了params，那么传过来地址也要有相关的参数



### 5、数据响应(回显)

![微信截图_20220723190157](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723190157.png)

#### **5.1页面跳转**(请求转发和重定向)

![微信截图_20220723204621](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723204621.png)

如果没有配置视图解析器，那么要写全称

#### 5.2ModeandView

![微信截图_20220723210713](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723210713.png)

可以封装数据，然后返回页面

![微信截图_20220723210635](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723210635.png)

#### 5.3自动生成对象

![微信截图_20220723215904](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723215904.png)

#### 5.4回写数据

![微信截图_20220723220207](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723220207.png)

![微信截图_20220723221454](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723221454.png)

#### 5.5乱码问题

![微信截图_20220723221511](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220723221511.png)

#### **5.6 jakson**



先导入坐标

![微信截图_20220724032532](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220724032532.png)

![微信截图_20220724032542](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220724032542.png)

![微信截图_20220724030502](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220724030502.png)



#### **5.7返回对象或者集合**

![微信截图_20220724032554](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220724032554.png)

![微信截图_20220724032757](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220724032757.png)



配置注解驱动

![微信截图_20220724033245](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220724033245.png)



#### 5.8获取请求参数

![微信截图_20220724034502](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220724034502.png)

![微信截图_20220724035344](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220724035344.png)



获取pojo

就是将数据封装为对象

![微信截图_20220724041356](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220724041356.png)



数组

![微信截图_20220724042103](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220724042103.png)



集合

![微信截图_20220724183942](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220724183942.png)

![微信截图_20220724184005](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220724184005.png)



![微信截图_20220724184045](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220724184045.png)

![微信截图_20220724184013](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220724184013.png)

![微信截图_20220724184028](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220724184028.png)

![微信截图_20220724190259](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220724190259.png)

#### 5.8乱码设置拦截器

![微信截图_20220724201834](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220724201834.png)





#### 5.9参数绑定

![微信截图_20220725032424](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220725032424.png)

就是前端传过来的参数和你的类名不一样时候，如果不指定，就匹配不上

![微信截图_20220725032557](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220725032557.png)

#### **5.10参数**

![微信截图_20220725034026](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220725034026.png)

![微信截图_20220725034208](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220725034208.png)

![微信截图_20220725034811](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220725034811.png)



#### 5.11请求头

![微信截图_20220725043911](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220725043911.png)

![微信截图_20220725044155](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220725044155.png)



### 6、文件上传

#### 1、简介

![微信截图_20220725044332](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220725044332.png)

![微信截图_20220725044907](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220725044907.png)

#### 2、坐标

![微信截图_20220725045220](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220725045220.png)

#### 3、配置上传解析器

![微信截图_20220725051002](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220725051002.png)



4、编写代码

![微信截图_20220725050953](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220725050953.png)

![微信截图_20220725051540](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220725051540.png)



### 7、jdbc模版

#### 1、简介

![微信截图_20220725102805](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220725102805.png)

![微信截图_20220725103941](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220725103941.png)

#### 2、步骤

![微信截图_20220725112530](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220725112530.png)

![微信截图_20220725164417](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220725164417.png)

![微信截图_20220725164434](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220725164434.png)

![微信截图_20220729121707](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220729121707.png)

![微信截图_20220725191134](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220725191134.png)

### 8、拦截器

#### 1、简介

![微信截图_20220727070933](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220727070933.png)

#### 2、入门

![微信截图_20220727163858](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220727163858.png)

在mvc文件配置拦截器

![微信截图_20220727164418](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220727164418.png)

![微信截图_20220727165146](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220727165146.png)

#### 3、相关方法

![微信截图_20220727170256](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220727170256.png)





#### 4、判断用户是否登录

![微信截图_20220729122338](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220729122338.png)

![](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220729124130.png)



### 9、异常处理

![微信截图_20220727190610](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220727190610.png)



#### 1、两种异常处理方式

![微信截图_20220727191723](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220727191723.png)

![微信截图_20220727191927](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220727191927.png)



#### 2、步骤

![微信截图_20220727194201](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220727194201.png)





## 五、AOP

### 1、简介

![微信截图_20220727194750](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220727194750.png)





![微信截图_20220727210025](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220727210025.png)



### 2、代理

![微信截图_20220727212646](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220727212646.png)





### 3、动态代理

![微信截图_20220727214245](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220727214245.png)





![微信截图_20220727214245](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220727214245.png)





### **4、回顾动态代理**

![微信截图_20220728002303](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728002303.png)

![微信截图_20220728002508](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728002508.png)

![微信截图_20220728002739](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728002739.png)

![微信截图_20220728003237](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728003237.png)

![微信截图_20220728010158](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728010158.png)

![微信截图_20220728010410](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728010410.png)



### 5、aop

![微信截图_20220728003712](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728003712.png)

![微信截图_20220728011635](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728011635.png)





### 6、aop知识点(重要)

![微信截图_20220728022703](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728022703.png)



![微信截图_20220728023131](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728023131.png)

7、快速入门

![微信截图_20220728023934](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728023934.png)

#### 6.1切点表达式

![微信截图_20220728043639](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728043639.png)



#### 6.2通知类型

![微信截图_20220728045554](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728045554.png)



#### 6.3xml配置例子

![微信截图_20220728050709](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728050709.png)

![微信截图_20220728050204](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728050204.png)



<img src="C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728160226.png" alt="微信截图_20220728160226" style="zoom: 150%;" />

![微信截图_20220728160234](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728160234.png)

![微信截图_20220728160242](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728160242.png)

测试

![微信截图_20220802053301](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220802053301.png)





#### 6.4注解配置

![微信截图_20220728160301](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728160301.png)

![微信截图_20220728160308](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728160308.png)

![微信截图_20220728160342](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728160342.png)

![微信截图_20220728160952](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728160952.png)

![微信截图_20220728161055](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728161055.png)

![微信截图_20220728161119](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728161119.png)

总结

![微信截图_20220728162745](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728162745.png)





## 六、事物(先跳过)

### 1、简介

![微信截图_20220828201825](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220828201825.png)



### 2、添加事物

![微信截图_20220828202413](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220828202413.png)



![微信截图_20220828202425](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220828202425.png)

![微信截图_20220828202435](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220828202435.png)



### 3、事物分配

![微信截图_20220828211555](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220828211555.png)



![微信截图_20220828211704](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220828211704.png)

### 4、事物分离

让信息事物不受总事物控制

![微信截图_20220828212431](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220828212431.png)





![微信截图_20220828220332](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220828220332.png)

![微信截图_20220828220552](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220828220552.png)



![微信截图_20220828220602](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220828220602.png)



## **七、Mybatis**

### 直接写sql





![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221124215023.png)



### 返回值为map

![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221124225707.png)



### 注意事项

```
1 .#将传入的数据都当成一个字符串，会对自动传入的数据加一个双引号。
2. $将传入的数据直接显示生成在sql中。
3. #方式能够很大程度防止sql注入。　
4.$方式无法防止Sql注入。
5.$方式一般用于传入数据库对象，例如传入表名.　
6.一般能用#的就别用$.

```



### 1、原始jdbc

![微信截图_20220728170247](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728170247.png)



![微信截图_20220728174309](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728174309.png)





### 2、mybatis简介

![微信截图_20220728174804](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728174804.png)





### **3、开发步骤**(核心)

![微信截图_20220728175312](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728175312.png)





### **4、测试代码**

![微信截图_20220728182834](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728182834.png)





### **5、配置(两个核心的配置文件)**

![微信截图_20220728193752](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728193752.png)

加载文件可以直接加载dao层

![微信截图_20220827202508](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220827202508.png)

写sql的

![微信截图_20220728193800](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728193800.png)



测试的，也是模版代码

![微信截图_20220728193809](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728193809.png)



![微信截图_20220728200816](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728200816.png)

![微信截图_20220728202743](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220728202743.png)



### 6、一些基本操作

通过对象来操作

![微信截图_20220729160217](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220729160217.png)



![微信截图_20220729160250](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220729160250.png)

![微信截图_20220729160308](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220729160308.png)



### 7、核心配置文件概述

![微信截图_20220729160745](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220729160745.png)

![微信截图_20220729161313](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220729161313.png)

![微信截图_20220729161559](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220729161559.png)

![微信截图_20220729162535](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220729162535.png)



### 8、api

![微信截图_20220729163157](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220729163157.png)

![微信截图_20220729163524](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220729163524.png)

![微信截图_20220729163821](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220729163821.png)









### **9、代理开发(非常重要)**

![微信截图_20220729164700](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220729164700.png)



这里写错了，是userDao

![微信截图_20220729165524](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220729165524.png)



![微信截图_20220729171648](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220729171648.png)





### 10、sql例子

防止值为空

![微信截图_20220729231408](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220729231408.png)

![微信截图_20220729231503](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220729231503.png)

![微信截图_20220729232914](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220729232914.png)

![微信截图_20220729232929](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220729232929.png)





### 11、标签

![微信截图_20220729234629](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220729234629.png)

![微信截图_20220730163349](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220730163349.png)

![微信截图_20220730164010](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220730164010.png)



### 12、分页

![微信截图_20220730164142](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220730164142.png)

![微信截图_20220730164855](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220730164855.png)

![微信截图_20220730165145](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220730165145.png)

![微信截图_20220730172640](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220730172640.png)

![微信截图_20220730172701](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220730172701.png)

![微信截图_20220730172715](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220730172715.png)

![微信截图_20220730174018](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220730174018.png)







### **13、一对一操作(重要)**

![微信截图_20220731023631](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220731023631.png)

![微信截图_20220802053301](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220802053301.png)

![微信截图_20220802214305](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220802214305.png)

![微信截图_20220802214328](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220802214328.png)

![微信截图_20220802214350](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220802214350.png)

![微信截图_20220802214400](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220802214400.png)



![微信截图_20220802225815](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220802225815.png)





### 15、一对多

![微信截图_20220802230145](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220802230145.png)

![微信截图_20220803002818](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220803002818.png)

### 16、多对多



![微信截图_20220803002855](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220803002855.png)



![微信截图_20220803180801](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220803180801.png)

### 17、注解

![微信截图_20220803181456](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220803181456.png)

![微信截图_20220803210718](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220803210718.png)

![微信截图_20220803210728](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220803210728.png)

![微信截图_20220803210737](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220803210737.png)

![微信截图_20220803210823](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220803210823.png)

![微信截图_20220803210852](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220803210852.png)

![微信截图_20220803213756](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220803213756.png)

![微信截图_20220803213808](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220803213808.png)

![微信截图_20220803221543](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220803221543.png)





## 八、SSM整合

### 1、原始

![微信截图_20220803221851](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220803221851.png)

![微信截图_20220803222902](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220803222902.png)

![微信截图_20220803222918](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220803222918.png)

![微信截图_20220803222944](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220803222944.png)

![微信截图_20220803222956](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220803222956.png)

![微信截图_20220803223043](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220803223043.png)

![微信截图_20220803223117](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220803223117.png)

![微信截图_20220803223228](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220803223228.png)

![微信截图_20220803223429](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220803223429.png)

![微信截图_20220803223439](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220803223439.png)

![微信截图_20220803223527](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220803223527.png)





### **2、spring**

具体见代码spring-ssm

![微信截图_20220804104459](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220804104459.png)





![微信截图_20220804104712](C:\Users\waili\Desktop\usual\微信截图\ssm入门\微信截图_20220804104712.png)





### 3、mybatis



![微信截图_20220827220154](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220827220154.png)

![微信截图_20220827220207](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220827220207.png)

![微信截图_20220827220219](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220827220219.png)



![微信截图_20220827220420](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220827220420.png)

![微信截图_20220827230424](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220827230424.png)

包相同才能扫到配置文件





## 九、MVC注解版

### 配置类

spring类加载路径的时候不要加controller层

```Java
@Configuration
@ComponentScan({"com.it.domain","com.it.mapper","com.it.service","com.it.controller"})//扫描的地方
@PropertySources({@PropertySource("classpath:jdbc.properties")})//加载外部文件
@Import({jdbcConfig.class,mybatisConfig.class})//导入其他配置
public class springConfig {

}
```



```java
@Configuration
@ComponentScan("com.it.controller")//扫描bean
@EnableWebMvc
public class springmvcConfig {

}
```

这里的jdbcconfig可以加  configuration也可以在spring配置类中直接导入

### 1、坐标

![微信截图_20220828235556](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220828235556.png)



### 2、控制器(controller)

![微信截图_20220828235612](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220828235612.png)







### 3、mvc配置类(相当于Mvc配置文件)

![微信截图_20220828235933](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220828235933.png)





### 4、初始化servlet容器

![微信截图_20220829000029](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220829000029.png)



让servlet启动的时候能够加载mvc和spring配置类

类似于web.xml文件

第三个方法和第一个一样，加载spring配置类

第二个方法是决定哪个路径给mvc管理



### 5、过程

![微信截图_20220829023833](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220829023833.png)





### 6、扫描重复

![微信截图_20220829024351](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220829024351.png)

![微信截图_20220829025553](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220829025553.png)

![微信截图_20220829025609](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220829025609.png)





### 7、请求

#### 1、普通参数

![微信截图_20220829031515](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220829031515.png)



#### 2、表单

![微信截图_20220829031535](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220829031535.png)



#### 3、请求参数名和变量名不同

![微信截图_20220829164540](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220829164540.png)



#### 4、pojo

![微信截图_20220829164607](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220829164607.png)



嵌套

![微信截图_20220829164644](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220829164644.png)



#### 5、数组

![微信截图_20220829164701](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220829164701.png)



#### 6、集合

![微信截图_20220829164718](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220829164718.png)



#### **7、json(重要)**

坐标

![微信截图_20220829165541](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220829165541.png)



发送

![微信截图_20220829165549](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220829165549.png)





接受要有注解

![微信截图_20220829165600](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220829165600.png)



![微信截图_20220829165616](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220829165616.png)

![微信截图_20220829165636](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220829165636.png)

![微信截图_20220829165649](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220829165649.png)



集合

![微信截图_20220829165718](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220829165718.png)



#### 8、请求和响应

![微信截图_20220829165800](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220829165800.png)



![微信截图_20220829183906](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220829183906.png)

![微信截图_20220829183925](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220829183925.png)

![微信截图_20220829184157](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220829184157.png)

![微信截图_20220829190247](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220829190247.png)*

![微信截图_20220829190305](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220829190305.png)



#### 9、统一返回

![微信截图_20220830113238](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220830113238.png)





### 8、异常

#### 1、异常处理器

![微信截图_20220830114344](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220830114344.png)

![微信截图_20220830115802](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220830115802.png)

![微信截图_20220830115902](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220830115902.png)

![微信截图_20220830123416](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220830123416.png)



![微信截图_20220830124430](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220830124430.png)

![微信截图_20220830123916](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220830123916.png)







### 9、拦截器



![微信截图_20220830161302](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220830161302.png)

![微信截图_20220830161318](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220830161318.png)

![微信截图_20220830161354](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220830161354.png)

![微信截图_20220830162028](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220830162028.png)

![微信截图_20220830162828](C:\Users\waili\Desktop\usual\微信截图\spring\微信截图_20220830162828.png)
