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



