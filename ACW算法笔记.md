# 	ACW算法笔记

## 一、基础

### 1、快速排序

```java
import java.util.*;
public class Main{
    public static void main(String[]args){
        Scanner in=new Scanner(System.in);
        int n=in.nextInt();
        long []num=new long[n];
        for(int i=0;i<n;i++){
            num[i]=in.nextLong();
        }
        quick_sort(num,0,n-1);
        for(int i=0;i<n;i++){
            System.out.print(num[i]+" ");
        }
    }
    public static void quick_sort(long[]num,int l,int r){
        if(l>=r)return;
        int left=l-1;
        int right=r+1;
        long mid=num[(l+r)/2];
        while(left<right){
            while(num[++left]<mid);
            while(num[--right]>mid);
            if(left<right){
                long temp=num[left];
                num[left]=num[right];
                num[right]=temp;
            }
        }

        quick_sort(num,l,right);
        quick_sort(num,right+1,r);
    }
}
```



### 2、二分

普通二分

还有给一个不降序的数组，让你找出一个数，小于等于这个数的最右边，大于等于这个数的最左边

也就是 1 2 2 2 2 3 找出2区间的头和尾坐标

具体题目看代码笔记本

```Java
while(l<=r){
    mid=(r+l)/2;
    if(num[mid]>=target){
        index1=mid;
        r=mid-1;
    }else l=mid+1;
  
}
```

```Java
while(l<=r){
    mid=(r+l)/2;
    if(num[mid]<=target){
        index2=mid;
        l=mid+1;
    }else r=mid-1;
}
```



### 3、前缀和

#### 一维

概念：比如一个数组a   a0 a1 a2 a3 a4.... an

又有一个数组S    s1=s1   s2=a1+a2  s3 =a1+a2+a3  前缀和一般数组重下标为1开始

**求S：所以  Sn=an+Sn-1**

用途 求数组中a一个区间[l,r]的和

可以用Sr-Sl-1;

<img src="C:\Users\waili\Desktop\usual\微信截图\错题力扣\微信截图_20220715163138.png" style="zoom:67%;" />

```java
public class Main{
    public static void main(String[]args){
        Scanner in=new Scanner(System.in);
        int n=in.nextInt();
        int m=in.nextInt();
        int l;
        int r;
        //下标从一开始
        int []num=new int[n+1];
        int []dp=new int[n+1];
        for(int i=1;i<=n;i++){
            num[i]=in.nextInt();
            dp[i]=dp[i-1]+num[i];
        }
        for(int i=0;i<m;i++){
            l=in.nextInt();
            r=in.nextInt();
            System.out.println(dp[r]-dp[l-1]+" ");
        }
    }
}
```





#### **二维**

求一块区域的面积,一般让下标从零开始

  a00         a01       a02      a03     a04

  a10        a11        a12       a13     a14

  a20        a21        a22      a23     a24

  a30         a31       a32      a33     a34

 a40         a41         a42     a 43     a44

Sij左下角下标为i j 的矩形的面积

这时候有递推Sij=s(i-1)j+si(j-1)-s[i-1] [j-1]+a[i]  [i]

比如要求x1,y1为左上角，x2,y2为右下角面积

减去重复的，要加上

总的面积是S(x2)(y2) -S(x2)(y-1)-S(x1-1)(y2)+S(x1-1)(y1-1)

最后算出结果

输入一个数组，并且循环次数，给出左上角和右下角下标，求子矩阵的面积

```Java
public class Main{
    public static void main(String[]args){
        Scanner in=new Scanner(System.in);
        int n=in.nextInt();
        int m=in.nextInt();
        int q=in.nextInt();
        int [][]num=new int[n+1][m+1];
        int [][]s=new int[n+1][m+1];
        for(int i=1;i<=n;i++){
            for(int j=1;j<=m;j++){
                num[i][j]=in.nextInt();
            }
        }
        //构造S
        for(int i=1;i<=n;i++){
            for(int j=1;j<=m;j++){
                s[i][j]=s[i-1][j]+s[i][j-1]-s[i-1][j-1]+num[i][j];
                //System.out.println(s[i][j]);
            }
        }
        for(int i=0;i<q;i++){
            int x1=in.nextInt();
            int y1=in.nextInt();
            int x2=in.nextInt();
            int y2=in.nextInt();
            int sum=s[x2][y2]-s[x2][y1-1]-s[x1-1][y2]+s[x1-1][y1-1];
            System.out.println(sum);
        }
    }
}
```



### **4、差分**

#### 一维差分

差分就是前缀和的逆运算

a数组

b数组

ai=b0+...bi

a是b的前缀和，b是a的差分数组

**b1=a1    b2=a2-a1   b3=a3-a2    b4=a4-a3       大概是这样**

具体运用：比如要在原数组a中一段【l,r】中的每一个数都加c，那么可以运用差分数组，降低时间复杂度

可以让 b(l)+c    让 b(r+1)-c；

一般下标从一开始，比较好处理数据

原理可以看：b1   b2  b3  b4  b5  b6  b7 

要在a1到a4每个数加一

**可以让b1+1     结果是a1到后面每一个前缀和都加一   但是我们只希望加到下标为4的地方 ，所以b(5)-1  让a5后面的数减一，一加一减抵消了，只有1到4是加了1**



因为a是b的前缀和，最后在求一遍前缀和  b[i]=b[i-1]+b[i];

输出b[i]就行了，就是改变后的a数组

下面看一道例题：

```java
import java.util.*;
public class Main{
    public static void main(String[]args){
        Scanner in=new Scanner(System.in);
        int n=in.nextInt();
        int m=in.nextInt();
        int []num=new int[n+2];
        int []b=new int[n+2];
        for(int i=1;i<=n;i++){
            num[i]=in.nextInt();
            insert(b,i,i,num[i]);
        }
        for(int i=0;i<m;i++){
            int l=in.nextInt();
            int r=in.nextInt();
            int c=in.nextInt();
            insert(b,l,r,c);
        }
        for(int i=1;i<=n;i++){
            b[i]=b[i]+b[i-1];
        }
        for(int i=1;i<=n;i++)System.out.print(b[i]+" ");
    }
    public static void insert(int []num,int i,int j,int c){
        num[i]+=c;
        num[j+1]-=c;
    }
}
```

值得注意的是，我们不用特意构造b数组，我们可以想象a数组初始为0，然后，然后在i到i上加a[i],也就是差分运算，最后得出的就是b数组



#### 二维差分

二维差分也是一样，我们的目的是让子矩阵中的每个元素加一个常数c

  a00         a01       a02      a03     a04

  a10        a11        a12       a13     a14

  a20        a21        a22      a23     a24

  a30         a31       a32      a33     a34

 a40         a41         a42     a 43     a44

再次说明，我们下标一般从一开始，这样子就不用判断下标等于0的时候怎么操作了，比较方便

我们假设子矩阵的左上角x1,y1,右下角为x2,y2

我们让b(x1)(y1)+=c这样右下角整块大的矩阵就全部加上了c

所以b(x2+1)(y1)-=c       b(x1)(y2+1)-=c    又因为重复减了   所以b(x2+1)(y2+1)+=c

最后我们在用老办法前缀和求二维数组b

**记住，我们初始化b也可以用上面的公式，不用刻意去记住怎么初始化b**

下面是例题，给出，n,m,q 然后输入数组，在输入q组数据x1,y1,x2,y2  c 这块区域加c最后输出数组的样子

```java
import java.util.*;
public class Main{
    public static void main(String[]args){
        Scanner in=new Scanner(System.in);
        int n=in.nextInt();
        int m=in.nextInt();
        int q=in.nextInt();
        int [][]a=new int[n+2][m+2];
        int [][]b=new int[n+2][m+2];
        //构造a数组和b数组
        for(int i=1;i<=n;i++){
            for(int j=1;j<=m;j++){
                a[i][j]=in.nextInt();
                insert(i,j,i,j,b,a[i][j]);
            }
        }
        //差分数组b的构建
        for(int i=0;i<q;i++){
            int x1=in.nextInt();
            int y1=in.nextInt();
            int x2=in.nextInt();
            int y2=in.nextInt();
            int c=in .nextInt();
            insert(x1,y1,x2,y2,b,c);
        }
        //和前缀和数组一样，求出来
        for(int i=1;i<=n;i++){
            for(int j=1;j<=m;j++){
                a[i][j]=b[i][j]+a[i-1][j]+a[i][j-1]-a[i-1][j-1];
                System.out.print(a[i][j]+" ");
            }
            System.out.println();
        }


    }
    public static void insert(int x1,int y1,int x2,int y2,int [][]b,int c){
        b[x1][y1]+=c;
        b[x2+1][y1]-=c;
        b[x1][y2+1]-=c;
        b[x2+1][y2+1]+=c;
    }

}
```
