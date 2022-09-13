#  Cpp



## 一、头文件

//解决爆栈，手动加栈，必须放在头文件之前
#pragma comment(linker,"/STACK:1024000000,1024000000") 

//万能头文件，部分比赛中可能不让用
#include <bits/stdc++.h> //C++

//STL专用，使用了哪种数据结构，就要用到哪种头文件
#include <map> //C++
#include <vector> //C++
#include <set> //C++

//C++必备头文件，cin、cout及其相关函数在这里
#include <isotream> //C++

//strlen()、strcat()等字符串操作函数在这里
#include <cstring> //C++
#include <string.h> //C语言

//min()、max()等在这里
#include <cstdlib> //C++
#include <stdlib.h> //C语言

//scanf()、printf()以及和它们长得像的函数在这里
#include <cstdio> //C++
#include <stdio.h> //C语言

//sort()在这里
#include <algorithm>> //C++

//log()、sin()、pow()等数学运算的函数在这里
#include <cmath>> //C++
#include <math.h> //C语言





## 二、stl基础

![微信截图_20220825162003](C:\Users\waili\Desktop\usual\微信截图\cpp\微信截图_20220825162003.png)



### 1、基本构成

![微信截图_20220825162753](C:\Users\waili\Desktop\usual\微信截图\cpp\微信截图_20220825162753.png)

![微信截图_20220825163309](C:\Users\waili\Desktop\usual\微信截图\cpp\微信截图_20220825163309.png)



### 2、for循环

![微信截图_20220825164835](C:\Users\waili\Desktop\usual\微信截图\cpp\微信截图_20220825164835.png)



### 3、基本容器

![微信截图_20220825165313](C:\Users\waili\Desktop\usual\微信截图\cpp\微信截图_20220825165313.png)

![微信截图_20220825165650](C:\Users\waili\Desktop\usual\微信截图\cpp\微信截图_20220825165650.png)

![微信截图_20220825165925](C:\Users\waili\Desktop\usual\微信截图\cpp\微信截图_20220825165925.png)

![微信截图_20220825173019](C:\Users\waili\Desktop\usual\微信截图\cpp\微信截图_20220825173019.png)

![微信截图_20220825174628](C:\Users\waili\Desktop\usual\微信截图\cpp\微信截图_20220825174628.png)

![微信截图_20220825174657](C:\Users\waili\Desktop\usual\微信截图\cpp\微信截图_20220825174657.png)

![微信截图_20220825174810](C:\Users\waili\Desktop\usual\微信截图\cpp\微信截图_20220825174810.png)



## 三、详细

### 1、map

遍历：

for(auto t:map)

t.first  ->key

t.second ->value



2、查询元素

m.count(x)  如果为0就是不存在







### 2、pair<int,int> 

定义键值对，在搜索时候经常用





### 3、set

c++中的set是默认排序的

同时set,begin取出头元素的指针

如果要用值加上*(set.begin())



### 4、字符串

#### 读取

char a[10];

sacnf("%s",a+1);

从第一个位置开始读入，方便操作



#### 包含

一个字符串是否包含另一个字符串

(s + s).find(goal) != string::npos;



#### 字符串和整数转换

to_string(num);

stoi(string）



#### 排序

```
 string s(str.rbegin(),str.rend());  降序
```

### 5、注意事项

从一个容器取出另一个容器，最好用&

比如set s=&map[index]





### 6、堆

 //定义小顶堆  priority_queue<int,vector<int>,greater<int>>heap;



### 7、vector

#### 排序

```cpp
sort默认排序从小到大，使用greater<int>()

        #include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

        int main() {
        int a[] = {8,6,2,9,3,5,4,1,7,10};
        vector<int> arr(a, a+5);
        sort(arr.begin(),arr.end(),greater<int>());
        for(int i = 0; i <arr.size(); ++i){
        cout <<arr[i] << " ";
        }
        return 0 ;
        }

        方法二：自定义函数
        #include <iostream>
         #include <vector>
         #include <algorithm>
         using namespace std;

        bool cmp_max(int x,int y){
              return x > y;
        }

        int main() {
        int a[] = {8,6,2,9,3,5,4,1,7,10};
        vector<int> arr(a, a+5);
        sort(arr.begin(),arr.end(),cmp_max);
        for(int i = 0; i <arr.size(); ++i){
             cout <<arr[i] << " ";
        }
        return 0 ;
        }
```



#### 二维

 vector<vector<int>>a(m,vector<int>(n));
