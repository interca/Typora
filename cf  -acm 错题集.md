# cf  -acm 错题集

## 一、贪心

### 1、背包找最值  (cf 831)

**题意：**

给定n个石头和三个空背包，将n个石头放入三个背包中。从三个背包中拿出三个石头，假设冲三个包中拿出的石头的质量为 a,b,c ，最终的分数为 |a−b|+|b−c| ，取石头的人会最小化这个值，请问如何分配石头可以使得最终的分数最大。

分析：

-  给一个数组
- 然后分三个组
- 然后拿的人每次最小化取出三个数 保证   a-b的绝对值加b - c 的绝对值最小
- 求出最大可能多少

![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221106032843.png)

代码：

```c++
#include<iostream>
#include<cstring>
#include<algorithm>
#include<queue>
#include<vector>
#include<cmath>
using namespace std;
int main(){
     int n;
     cin>>n;
     vector<int>num;
     while(n --){
         int a;
         cin>>a;
         vector<int>v;
         for(int i = 0 ;i <a ; i ++){
             int c;
             cin>>c;
             v.push_back(c);
         }
         sort(v.begin(),v.end());
         int res = 0;
         for(int i = 0 ; i<= a - 2 ;i  ++){
             res = max(res,v[a - 1] - v[i] + v[i + 1] - v[i]);
         }
         for(int i =a -1 ;i >=1 ; i--){
             res = max(res,v[i] - v[0] + v[i] - v[i - 1]);
         }
         num.push_back(res);
     }
     for(int i = 0; i < num.size(); i ++){
         cout<<num[i]<<endl;
     }
    return 0;
}
```





## 二、思维题

### 1、暴力思维来自div833

给一个字符串  然后定义  出现次数最多的字符个数为a 字符的种类为b    然后如果a<=b  那么这个字符就符合要求

问一个字符串多少子串符合要求  字符由 0 到1构成



思路：

暴力就行  总共十个字符  那么如果符号要求  那么极端情况就是每个字符出现十次 最多100次  所以暴力解就行了  
