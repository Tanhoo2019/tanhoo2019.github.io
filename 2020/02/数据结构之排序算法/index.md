# 数据结构之排序算法


### 选择排序

#### 原理

选择数组中最大值，并将最后一位替换成最大值，然后缩小选择范围，重复而为之，最后得到顺序。

  

#### 过程

假设有以下数组：

```c
int a[] = {2,43,45,66,4,21,67,88,24,35,21};
```

**Step1**

先定义一个max函数，求数组中的最大值。

max = 88;

把最后一位21替换成88。

  

**Step2**

范围缩小一位，求数组中的最大值。

max = 67;

把倒数第二位35替换成67。

  

**Step3**

重复上述过程



### c语言代码实现

```c
#include <stdio.h>
// 排序算法- 选择排序
int max(int a[], int len)
{
    int maxid = 0;
    for ( int i=1; i<len; i++ )
    {
        if ( a[i] > a[maxid] )
        {
            maxid = i;
        }
    }
    return maxid;
}

int main()
{
    int a[] = {2,43,45,66,4,21,67,88,24,35,21};
    int len = sizeof(a)/sizeof(a[0]);
    
    for ( int i = len-1; i>0; i-- )
    {
        int maxid = max(a, i+1);
        // swap a[maxid], a[len-1]
        int t = a[maxid];
        a[maxid] = a[i];
        a[i] = t;
    }
    for ( int i=0; i<len; i++ )
    {
        printf("%d ", a[i]);
    }
    printf("\n");
    
    return 0;
}


```



