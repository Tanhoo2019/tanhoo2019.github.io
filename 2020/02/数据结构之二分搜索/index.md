# 数据结构之二分搜索


### 二分搜索的优点

> 效率高， 搜索次数为log<sub>2</sub>N，随着数组增大，搜索次数的增速缓慢。



### 如何理解二分搜索

二分搜索是建立在有序数组条件下的。假设一组顺序数组:

```c 
a[] = {2,4,7,11,13,16,21,24,27,32,36,40,46};
```

下面我们用二分搜索来查找36的索引值。

```c
0  1  2  3  4  5  6  7  8  9  10  11  12 
2  4  7  11 13 16 21 24 27 32 36  40  46
```

**Step1:**

left = 0, right = 12;

mid = (left + right) / 2, 所以此时mid = 6;

我们要查找的数是36，设k = 36;

因为 a[mid] = 21, 所以 k > a[mid]。

因此要舍弃21左边的数，往右边继续找，因此有 left = mid + 1 = 7。  

 

**Step2:**

同样，此时left = 7, right = 12, mid = 9。

因为 a[mid] = 32 < k， 所以舍弃 32左边，继续往右找。 left = mid + 1 = 10。  

  

**Step3:** 

此时left = 10, right = 12, mid = 11。

a[mid] = 40 > k, 说明正确值在40左边，因此舍弃右边，继续往左找。right = mid -1。  

 

**Step4:**

此时left = 10, right = 10。

a[mid] = 10 = k，因此我们成功找到了36的索引值：10 。

 

从上述过程来看，二分搜索完成36的索引值查找过程只需4步，而在同样条件下用线性搜索则需要11步，所以可以看出二分搜索要比线性搜索高效得多。



### 二分搜索c语言代码实现

```c
#include <stdio.h>
// 搜索--二分搜索(需要排好序)
int searchp(int k, int a[], int len)
{
    int left = 0;
    int ret = -1;
    int right = len-1;
  // 好好琢磨下这个终止调节的原因
    while (right >= left) 
    {
        int mid = (left+right)/2;
        if ( a[mid] == k)
        {
            ret = mid;
            break;
        } else if ( a[mid]>k){
            right = mid-1;
        } else{
            left = mid +1;
        }
    }
    return ret;
}
    
int main()
{
    int n;
    int a[] = {2,4,7,11,13,16,21,24,27,32,36,40,46};
    printf("请输入您想搜索的数：");
    scanf("%d",&n);
    int r = searchp(n, a, sizeof(a)/sizeof(a[0]));
    printf("%d\n",r);
    return 0;
}
```



