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







### 2、看电影

题目

有n个人，每个人有一个数字a[i],一个人有以下情况之一会伤心，设有sum个人去看电影

+ 自己去看电影，sum - 1 小于a[i]
+ 自己不去，sum 大于等于a[i]

如果要让所有人都开心，sum有几种取法

> 思路
>
> 可以从大到小排序，然后记录当前去了多少个人，sum初始值等于n，说明一开始n个人去
> 满足以下要求，sum才符合
>
> + sum - 1 >= a[i]
> + sum  < a[i - 1]
>
> 从前往后遍历，如果符合的话计数加一
> 最后遍历结束的时候，特判一下sum =0的情况，是否大于a[n - 1]

```cpp

void solve(){
   int n;
   cin>>n;
   vector<long long>v(n);
   for(int i = 0 ; i < n ; i ++){
     scanf("%lld",&v[i]);
   }
   sort(v.rbegin(),v.rend());
   int sum = n;
   int c = 0;
   for(int i  = 0 ; i < n ; i ++){
       if(i > 0){
          if(v[i] <= sum - 1 && v[i - 1] > sum)c++;
       }else {
         if(v[i] <= sum - 1){
          c ++;
         }
       }
       sum --;
   }
   if(v[n - 1] > 0)c++;
   cout<<c<<endl;
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





### 5、构造

构造一个字符串

有两个选择：

1、随便选择一个字母放到末尾

2、选择已经选择字符串的子字符串加入末尾

问能否在字符串长度步骤内构造出来



思路：

只有找有两段一样的字符串就行了

```cpp
#include<iostream>
#include<algorithm>
#include<cstring>
#include<vector>
using namespace std;
#include<map>
int main(){
	int n;
	cin>>n;
	vector<string>v;
	while(n --){
		int t;
		cin>>t;
		string s;
		cin>>s;
		map<string,int>m;
		int flag = 0;
		for(int i = 0 ; i < t - 1 ; i ++){
		 string str = s.substr(i,2);
		   if(s[i] == s[i + 1]){
			   if(m[str] >=2 || (i > 0 && s[i - 1] != s[i] && m[str] >= 1)){
				   flag = 1;
				   break;
			   }
		   }else {
              if(m[str] >= 1){
				   flag = 1;
				   break;
			   }
		   }
		   m[str] ++;
		}
		if(flag == 1)v.push_back("YES");
		else v.push_back("NO");
	}

	for(int i = 0 ; i < v.size() ; i ++){
		cout<<v[i]<<endl;
	}
	return 0;
}
```





### 6、区间数（837）

<img src="https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221213023506.png" style="zoom: 80%;" />

```cpp
#include<iostream>
#include<algorithm>
#include<cstring>
#include<vector>
using namespace std;
#include<map>
void solve(){
	int n,m;
	cin>>n>>m;
	vector<long long >f(n + 1,n);
	while(m --){
		long long  x,y;
		cin>>x>>y;
		if(x >y)swap(x,y);
		f[x] = min(f[x], y - 1);
	}
	for(int i = n -1 ; i >= 1 ; i --){
		f[i] = min(f[i + 1],f[i]);
	}
	long long  sum = 0;
	for(int i = 1 ; i <= n ; i ++){
		sum += f[i] - i +1;
	}
	cout<<sum<<endl;
}
int main(){
	int n;
	cin>>n;
	while(n --){
	  solve();	
	}
	return 0;
}
```





### 7、好数组

把一个数组变成  每一个大的数都是小数的倍数   最多n次

思路:全部变成2的倍数







### 8、花环

出自小白月赛

![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20221216212628.png)

```cpp
#include<iostream>
#include<algorithm>
#include<cstring>
#include<vector>
using namespace std;
#include<map>
#include<queue>
#include<cmath>

int main(){
	int n,k;
	cin>>n>>k;
	vector<long long >v(k + 1,0);
	for(int i = 1; i <= k ; i ++){
		cin>>v[i];
	}
	if(k == 1)cout<<"Ginger666";
	else {
		sort(v.begin() + 1,v.end());
		long long sum = 0;
        if(n % 3 ==0)sum = n/3*(2*v[1] + v[2]);
        else if(n %3 == 1)sum = n/3*(2*v[1] + v[2])+v[2];
         else if(n %3 == 2)sum = n/3*(2*v[1] + v[2])+v[1] + v[2];
		cout<<sum<<endl;
	}
	return 0;
}
```





### 9、quick_sort  842(div2)  

给一个数组和一个k

每一次可以从数组取出k个数然后排序后加到末尾

问多少次可以把整个数组变有序



我们可以计算满足相对位置为1到n  有多少个数

剩下的就是要重新排的

对k做整除

```cpp
#include<iostream>
#include<algorithm>
#include<cstring>
#include<vector>
using namespace std;
#include<map>
#include<queue>
#include<cmath>

void solve(){
  long long n;
  long long k;
  cin>>n>>k;
  long long index = 0;
  long long c = 0;
  for(int i = 0 ; i < n ; i ++){
     long long x;
     cin>>x;
     if(index + 1 == x){
       index = x;
       c ++;
     }
  }
  long long count = n - c;
  if(count % k == 0)cout<<count/k<<endl;
  else cout<<(count/k+1)<<endl;
}

int main(){
	int n;
	cin>>n;
	while(n --)
	solve();
	return 0;
}
```





### 10、表演话剧(div2 edu专场)

题目：

**一个人，他会演奏四种话剧，分别是a,b,c,d  给出 四种话剧的数量**
**两个人bob 和 tom来听话剧**
**如果 a 话剧：bob 和tom的开心程度+1**
**b: bob + 1,tom - 1**
**c :  bob - 1, tom +1**
**d:  两个都减一**

**如果两个人有一个人的开心程度变为-1  那么停止演出，请问最多可以演多少话剧，种类顺序没有限制**



分析

> 我们可以看出，如果a话剧为0那么就一场都演不了
> 如果a有话剧，那么可以让 b c 轮流演一次，直到吧最小的消耗完，最后又恢复成两个人都有a的开心度
> 最后看能不能消耗完这a的开心度，取小就行了

```cpp
 
void solove(){
  int a = 0, b = 0,c = 0,d = 0;
  cin>>a>>b>>c>>d;
   long long sum = 0;
  if(a == 0){
      if(!(b == 0 && c == 0 && d == 0))
      cout<<1<<endl;
      else cout<<0<<endl;
  }
  else {
      int w = a;
      sum += a;
      int mx = max(b,c);
      int mn = min(b,c);
      sum += mn*2;
      int s = a ;
      sum += min(a + 1,d + mx - mn);
      cout<<sum<<endl;
  }
}
```





11、操作数组(接上一题)

**给一个长为 n的 的排列，每次操作可以任选两个数，其中小的挪到开头，大的挪到末尾，问最少几次操作可以使得排列有序。**

思路

> 注意到，操作不影响没有被操作过的数字的相对位置，因此考虑排列中不需要操作的数字。显然，最终被保留的数字应该是连续上升的一个子序列，如 `23456` 是，而 `13456` 不是因为 11 和 33 中间没有 22 。
>
> 假设我们操作了某一组数 (x,y) ，那么 (x,y),(x−1,y+1),⋯,(1,n) 一定都需要操作一遍才能保证这些数字有序。因此只有中间的数我们不需要操作，所以我们保留的数字应该从中间开始往外拓展。
>
> 若 n 为奇数，则从中点 (1 + n)/2 开始往两边扩展；若 n为偶数，先保证 (1 + n )/ 2 和 (1 + n + 1 )/2 有序，再从这两个数两边扩展，如果不有序直接输出 n2/2 。
>
> 为了方便找到某个数的位置，我们可以先处理数到位置的映射 pos ，再利用双指针 l,r 指向扩展的边界，向两边同时扩展，如果有一边扩展不了那就不需要继续了，最后结果是 l−1 。



```cpp
void solove(){
  int n;
  cin>>n;
  vector<int>pos(n + 1);
  for(int i = 1 ; i<= n ; i ++){
     int a;
     cin>>a;
     pos[a]  = i;
  }
  int l = (n + 1)/2,r = (n + 1 + 1)/2;
  if(pos[l] > pos[r]){
    cout<<n/2<<endl;
  }else {
     while(l >1 && r < n){
        if(pos[l] < pos[l - 1] || pos[r] > pos[r + 1])break;
        l --;
        r ++;
     }
     cout<<l - 1<<endl;
  }
}
```







### 11、相邻反转

题目
给一个数组，可以操作任意次：
把a[i] 变成- a[i ]  把 a[i + 1] 变成 - a[i + 1] 
 问最终可以得到数组最大和是多少

>我们可以想象把符号左右移动
>
>+ 当符数个数为偶数，那么全部取绝对值
>+ 为奇数，那么把绝对值最小的数变成负数，其他全部取绝对值
>
>注意点：当n == 1时候要特判

```cpp
  int n;
   cin>>n;
   vector<long long>v(n + 1);
   long long sum = 0;
   int count = 0;
   long long mx = 100000000000000;
   int index = 1;
   
   for(int i = 1 ;i <= n; i  ++){
       cin>>v[i];
       if(v[i] <= 0){
           count ++;
       };
       if(abs(v[i]) < mx){
          mx = abs(v[i]);
          index = i;
       }
   }
   if(n == 1){
       int a = abs(v[1]);
       cout<<a<<endl;
       return;
   }
   
   if(count % 2 == 0){
       for(int i = 1 ; i<= n ; i ++){
           sum += abs(v[i]);
       }
       cout<<sum<<endl;
   }else {
       for(int i =1 ; i <= n ; i ++){
           if(i == index)sum -= abs(v[i]);
           else sum += abs(v[i]);
       }
       cout<<sum<<endl;
   }
```



### 12、(x + y == n)

如果 x + y == n 并且x各位数字之和 与y的各位数字之和的差的绝对值小于等于1，写出一组x y
否则否则输出-1

>思路：可以从前往后枚举每一位，如果是偶数，平分给两个字符串，否则分别分给两个字符串
>注意首数字不能为0

```cpp
string n;
  cin>>n;
  string s1 = "";
  string s2 ="";
  int flag  = 0;
  for(int i =0 ; i < n.size() ; i ++){
      int s = n[i] - '0';
      int a = s/2;
      if(s % 2 == 0){
         if(!(s1.size() == 0 && a == 0))
         s1 += (char)(a + '0');
         if(!(s2.size() == 0 && a == 0))
         s2 += (char)( a + '0');
      }else {
          if(flag % 2 == 1){
               s1 += (char)(a + '0' + 1);
               if(!(s2.size() == 0 && a == 0))
               s2 += (char)( a + '0');
          }else {
                s2 += (char)(a + '0' + 1);
                if(!(s1.size() == 0 && a == 0))
                s1 += (char)(a + '0');
          }
          flag ++;
      }
  }
  if(s1.size() == 0)s1 = "0";
  if(s2.size() == 0)s2 = "0";
  cout<<s1<<" "<<s2<<endl;
```





### 13、2n组合数

给一个n  然后你要给出n对，没对两个数，他们再[1，2*n]  范围
并且  后一对的和比前一对和数量多一，求是否可以构造整个序列(可以不按顺序)，如果是输出，否则输出no
比如n == 3
有  2 4   1  6  35

>不管n是偶数还是奇数，2*n肯定是偶数，1 加到2n  就是(1 + 2n)*2n/2   =   n + 2n * n
>因为第二项开始，比1前一项多以，所以多出来的有 1 加到 n - 1 =  n(n - 1)/2

```cpp
 int n;
   cin>>n;
   if(n % 2 == 0)cout<<"NO"<<endl;
   else {
       cout<<"YES"<<endl;
       int x = 1;
       int y = 2*n - 1;
       while(y > n){
           cout<<x<<" "<<y<<endl;
           x ++;
           y -= 2;
       }
       y = 2 * n;
       while(y > n){
           cout<<x<<" "<<y<<endl;
           x++;
           y -= 2;
       }
   }
```





### 14、障碍(小白月赛)

>暴力就行，x范围是1到n的平方

![](https://gitee.com/hongshenghyj/typora/raw/master/img/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20230210211839.png)

```cpp
#include <iostream>
#include <cstring>
#include <algorithm>
#include<vector>
#include<cmath>
using namespace std;

void solve(){  
   int n,m;
   cin>>n>>m;
   vector<int>v(m +2);
   for(int i = 1 ; i<= m ; i ++){
       cin>>v[i];
   }
    v[0] = 0;
    v[m + 1] = n;
   int mx = 0;
   int l = 0;
   int index = 0;
   for(int i = 0 ; i * i <=  n ; i ++){
       l = v[0];
       for(int j = 0; j  <= m + 1 && j + i + 1 <= m + 1 ; j ++){
          l = max(l,v[j + i + 1] - v[j]);
       }
       mx = max(mx,l - i * i);
   }
   cout<<mx<<endl;
}

int main(){
  int n;
  solve();
}
```





### 15、不同字符串

题目
给一个字符串，去除i 和 i + 1
剩下字符串有多少种

>最多n - 1
>如果当前位置前一个等于后一个，就- -

```cpp
void solve(){  
   int n;
   cin>>n;
   string s;
   cin>>s;
   int mx = n - 1;
   for(int i = 1 ;i < n - 1 ; i ++){
     if(s[i - 1] == s[i + 1])mx --;
   }
   cout<<mx<<endl;
}
```







### 16、**Unforgivable Curse**(div855)

题目
给定 n , k
给两个长度为n的字符串s1,s2
可以让a [i] 和a[i + k]  或者  a[i + k + 1]的数交换
问能不能使得s1 ==  s2

> 思路：
> a[i] 和 a[i + k + 1]交换
> a[i + 1]和a[i + k + 1]交换
> a[i] 和 a[i + k + 1]交换
> 我们可以交换a[i] 和a[i + 1]
>
> + 也就是i 可以到达的点i + 1也可以到达
>   我们找出不能交换的点  也就是 i + k >= n   -> i >= n - k
> + 同理往前也是， i- k <= -1   - >   i <= k - 1
>
> 最后要取并集

```cpp
void solve(){
  int n,k;
  cin>>n>>k;
  string s1,s2;
  cin>>s1>>s2;
  map<char,int>m1,m2;
  for(auto k : s1)m1[k] ++;
  for(auto k : s2)m2[k] ++;
  if(m1 != m2){
    cout<<"NO"<<endl;
    return;
  }
  for(int i = max(n - k,0); i <= min(n - 1,k - 1);  i ++){
    if(s1[i] != s2[i]){
      cout<<"NO"<<endl;
      return;
    }
  }
  cout<<"YES"<<endl;
}
```





### 17、判断只有三个因数的cf142

给一个数组，判断每一个数是否只有3个因数

>方法
>其实两个已经确定，1和本身
>我们将其开方，其开发数必须为质数并且可以被开方

```cpp

void solve(){
   int n;
   cin>>n;
   vector<int>v(n);
   long long N = 1e6;
   vector<long long>prime(N + 1,0);
   prime[0] = prime[1] = 1;
   for(long long i = 2 ; i <= N ; i ++){
     if(prime[i] == 0){
        for(long long j = i + i ; (long long)j<= N; j += i){
            prime[j] = 1;
        }
     }
   }
   for(int i = 0 ; i < n ; i ++){
     long long a;
     cin>>a;
     long long m  = sqrt(a);
     if(m * m == a && prime[m] == 0){
       cout<<"YES"<<endl;
     } 
     else cout<<"NO"<<endl;
   }
}
```



### 18、公倍数

题目
给一个n ，求两个数，保证a + b = b 同时保证a 和b的最小公倍数最小

>假设a <= b, 保证lcm(b,a) = b  ，也就是a可以被b整除，因为a + b == n
>所以a可以正常n  ，我们要让a尽可能大，b尽可能小
>所以我们找到n的最大约数，把n分成k份，k - 1是b  ，1 份是a





### 19、111

给出一个数，判断他是否由a*11 + b * 111 + k*11111...相加得出

>最后我们可以得出  由a*11+ b * 111，只要判断能构成这个就行了
>直接暴力

```cpp
void solve(){
   f = 0;
   cin>>n;
     for(int j = 0 ; j *111<= n ; j ++){
       if((n -j * 111)%11 == 0){
         f = 1;
         break;
       }
   }
   if(f == 1)cout<<"YES"<<endl;
   else cout<<"NO"<<endl;
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







### 18、按钮

两个数n  m  可以把n  * 2 或者 n - 1,求把n -> m要最少多少步

>可以反过来，m可以除以2或者加一
>我们可以看成二进制，如果m比n大，并且可以除以2，就右移
>否则就加一，直到可以右移



```cpp
void solve(){
  int n,m;
  cin>>n>>m;
  int sum=0;
   while( n < m){
    if(m%2!=0){
        m++;
        sum++;
    }
    else{
      m/=2;
      sum++;
    }
  }
  cout<<sum + abs(m - n)<<'\n';
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







## 五、二分

### 1、找出最后一个小于等于当前数的下标

```cpp
void solove(){
  int n;
  cin>>n;
  vector<int>v(n,0);
  for(int i = 0 ; i  < n ; i ++){
    cin>>v[i];
  }
  sort(v.begin(),v.end());
  int q;
  cin>>q;
  for(int i = 0  ; i < q ; i ++){
      int a;
      cin>>a;
      int l = 0;
      int r = n - 1;
      int flag = 0;
      while(l <= r){
         int mid = l + r >> 1;
         if(v[mid] > a)r = mid - 1;
         else l = mid + 1,flag = mid + 1;
      }
      cout<<flag<<endl;
  }
}
```







## 六、回溯

### 1、按钮(cf295)

题目
给n 和 m,可以将n*2或者将n - 1  求吧n变为m的最小次数

>回溯就行了，用数组记录变到当前数要多少步数，如果当前步数大于它，就不要回溯

```cpp
int n,m;
int mn = 100000000;
const int N = 100;
int vist[1000000];
void dfs(int x,int sum){
  if(x < 0 || x >= 2 * m)return;
  if(x == m){
     mn = min(mn,sum);
     return;
  }
  if(vist[x] <= sum)return;
  vist[x] = sum;
  dfs(x * 2,sum + 1);
  dfs(x - 1,sum + 1);
}
void solve(){
  memset(vist,100,sizeof(vist));
  cin>>n>>m;
  if(n >= m){
    cout<<n - m<<endl;
    return;
  }
  dfs(n,0);
  cout<<mn<<endl;
}
```

