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







### 2、温度计  div834

![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221120005822.png)





```cpp
#include<iostream>
#include<cstring>
#include<algorithm>
#include<vector>
#include<cmath>
#include<map>
#include<queue>
using namespace std;
int main(){
   int n;
   cin>>n;
   while(n --){
      int l,r,x,a,b;
      cin>>l>>r>>x>>a>>b;
      if(a == b)cout<<0<<endl;
      else if(abs(a - b) >=x)cout<<1<<endl;
      else {
         if(b - l >= x && r - b >= x){
             cout<<2<<endl;
         }
         else if(b - l >= x){
            if(a - l >= x)cout<<2<<endl;
            else if(r - a >= x)cout<<3<<endl;
            else cout<<-1<<endl;
         }
         else if(r - b >= x){
            if(r - a >= x)cout<<2<<endl;
            else if(a - l >= x)cout<<3<<endl;
            else cout<<-1<<endl;
         }
         else cout<<-1<<endl;
      }
   }
   return 0;
}
```





### 3、反转逆序对  (835)



![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221122044354.png)

```cpp
#include<iostream>
#include<cstring>
#include<algorithm>
#include<vector>
#include<cmath>
#include<map>
#include<queue>
using namespace std;
int lowbit(int x){
    return x & -x;
};

//求和
long long  count(int x,vector<int>tre){
    long long  sum = 0;
    for(int i = x; i ; i = i -lowbit(i)){
        sum += tre[i];
    }
    return sum;
};

//改变某个数
void add(int x,int k,vector<int>&tre){
    for(int i = x ; i <= 2 ; i = i + lowbit(i)){
        tre[i] +=k;
    }
    
};
int main(){
   int n;
   cin>>n;
   vector<long long >num;
   while(n --){
      int m;
      cin>>m;
      vector<int>tre(3,0);
      vector<int>v(m + 1,0);
      long long sum = 0;
      vector<int>sumz(m + 1,0);
      vector<int>sumo(m + 1,0);  
      for(int i = 1; i  <= m ; i ++){
         cin>>v[i];
         if(v[i] == 0){
            sum += count(2,tre) - count(1,tre);
         }
         add(v[i] + 1,1,tre);
         sumz[i] = sumz[i - 1];
         sumo[i] = sumo[i - 1];
         if(v[i] == 0){
            sumz[i] ++;
         }else {
            sumo[i] ++;
         }
      }
      long long mx = sum;
      for(int i = 1 ; i <= m ;i ++){
          long long a;
         if(v[i] == 0){
             a = sum  - sumo[i] + sumz[m] - sumz[i] ;
         }else {
            a = sum - (sumz[m] - sumz[i]) + sumo[i - 1];
         }
         mx = max(a,mx);
      }
      num.push_back(mx);
   }
   for(int i = 0 ;i < num.size() ; i ++){
      cout<<num[i]<<endl;
   }
   return 0;
}
```





### 4、异或和



思路：

当n为奇数 直接全部是1

当n为偶数：

我们可以 用 1^3 = 2 = 1+3 /2来构造

如果n/2  是奇数  那么就把  分成 n/2组 1 3

如果有奇数组 1 3 那么最后消去  只剩下 1^3   =  sum/n

如果偶数组  那么久要拆出 一组 1 ，3   变成 2 2  使得sum不变

比如  8  ：  1 3 1 3 1 3 2 2  ->   2 == 2

构造出以下式子

![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221126012453.png)

```cpp
#include<iostream>
#include<cstring>
#include<algorithm>
#include<vector>
#include<cmath>
#include<map>
#include<queue>
using namespace std;

int main(){
   int n;
   cin>>n;
   while(n --){
     int m;
     cin>>m;
     if(m % 2){
        for(int i = 0 ;i < m ; i ++)
        cout<<1<<" ";
        cout<<endl;
     }else {
         if(m /2% 2 == 1){
           for(int i = 0 ;i  < m ;i = i + 2)
             cout<<1<<" "<<3<<" ";
         }else {
            for(int i = 0 ;i < m /2 - 1 ; i ++){
               cout<<1<<" "<<3<<" ";
            }
            cout<<2<<" "<<2<<" ";
         }
         cout<<endl;
     }
   }
   return 0;
}
```



## 三、动态规划

### 1、妖塔(华东交通牛客月赛)



思路：

假设当前需要从第 层开始挑战，考虑战力至少为多少时，才能恰好不受阻碍（指不需要中途修炼）的挑战成 功。假设该临界战力是 ，那么挑战者的战力如果大于等于 ，那么直接一路平推过去即可。如果战力小于 ，我 们不妨在挑战之前，先把战力修炼到 ，然后在出发挑战。否则，我们一定会在挑战某一层的时候需要修炼。而 我们只是将所有的中途修炼改为了提前修炼。 我们定义 表示从第 层开始挑战，战力至少为多少，才能不受阻碍的挑战成功。显然我们需要提前预处理出来 这个 数组。其可以使用递推的方式进行求解。递推方程为 。 时间复杂度 。



![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221119041835.png)



```cpp
#include<iostream>
#include<cstring>
#include<algorithm>
#include<vector>
#include<cmath>
#include<map>
#include<queue>
using namespace std;
int main(){
   int n,m;
   cin>>n>>m;
   vector<int>v(n+1);
   for(int i = 1; i <= n  ; i ++){
      cin>>v[i];
   }
   long long  f[n + 1];
   f[n] = v[n] + 1;
   for(int i = n -1 ; i >= 1; i --){
      f[i] = max((long long )v[i] + 1,f[i + 1] - 1);
   }
   while(m --){
      int a,b;
      cin>>a>>b;
      if(a >= f[b]){
         cout<<n-b + 1<<endl;
      }
      else {
         cout<<(n - b + f[b] - a + 1)<<endl;
      }
   }
   return 0;
}
```





## 四、图论

### 1、火车(来自华东交通小白月赛)

思路：

floyed算法：

先进行一次floyed

然后每次更新边的时候都进行一次更新





![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221119042327.png)





![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221119042216.png)









```cpp
#include<iostream>
#include<cstring>
#include<algorithm>
#include<vector>
#include<cmath>
#include<map>
#include<queue>
 long long  a[300][300];
using namespace std;
int n;
void floyed(){
      for(int k = 1 ; k<=n ; k ++){
      for(int i = 1; i <= n ; i ++){
         for(int j = 1 ; j <= n ; j ++){
            if(a[i][j] > a[i][k] + a[k][j])
            a[i][j]  = a[i][k] + a[k][j];
         }
      }
   }
}
int main(){
   int m,q;
   cin>>n>>m>>q;
   memset(a,0x3f,sizeof a );
    for(int i = 1 ; i<= n ; i ++)a[i][i] = 0;
   for(int i = 0; i < m ; i ++){
      int  c,d;
      long long f;
      scanf("%d %d %lld",&c,&d,&f);
      a[c][d] = a[d][c] = min(a[c][d],f);
   }
    floyed();
      int opt;
   while(q --){
      cin>>opt;
      int k1,k2;
      cin>>k1>>k2;
      if(opt == 1){
          cout<<a[k1][k2]<<endl;
      }else {
            long long k;
            cin>>k;
            a[k1][k2] = a[k2][k1] = min(k,a[k1][k2]);
            for(int i = 1 ;  i<= n ;i ++){
                for(int j = 1 ;j <= n ; j ++){
                  a[i][j] = min(a[i][j],
                                  min(a[i][k1] + a[k1][k2] + a[k2][j],a[i][k2] +a[k2][k1] + a[k1][j]));
                }
            }
      }
   }
   return 0;
}
```

