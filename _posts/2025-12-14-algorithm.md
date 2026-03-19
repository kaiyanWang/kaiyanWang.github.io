---
layout: article
title: 算法
tags: CS
cover: /assets/images/axure/page-single.jpg
---

<!--more-->
# 基础算法
### 快速排序
方法一（课本方法）：这种方法只能选第一个元素作为pivot（如果要以数组中的其他的值作为pivotal，需要将其和第一个元素交换）

经过一次快排后（i = j），i左边的都 <= pivotal，i右边的都 >= pivotal，然后将pivotal放入位置i。接下来递归处理（l, i - 1）和（i + 1, r）。
```c
#include <iostream>
using namespace std;
const int N = 1e6 + 5;
int n;
int a[N];

void quick_sort(int *q, int l, int r) {
    if (l > r) return ;
    int pivotal = a[l];
    int i = l, j = r;
    while(i < j) {
        while(i < j && a[j] >= pivotal) j--;
        a[i] = a[j];
        while(i < j && a[i] <= pivotal) i++;
        a[j] = a[i];
    }
    a[i] = pivotal; 
    quick_sort(q, l, i-1);
    quick_sort(q, i+1, r);
}
int main() {
    cin >> n;
    for (int i=0; i < n; i ++) {
        cin >> a[i];
    }
    quick_sort(a, 0, n - 1);
    for (int i = 0; i < n; i ++) {
        cout << a[i] << " ";
    }
    cout<<endl;
    return 0;
}
```

方法二（模版）：

一次快排后，i左边都 <= x（不包括i），j右边都 >= x（不包括j）。示例：3 1 2 3 5，选3作为x，一轮后，i指向第4个位置的3，j指向第3个位置的2。

```c
#include <iostream>
using namespace std;
const int N = 1e6 + 5;
int q[N];
int n;

void quicksort(int *q, int l, int r) {
    if (l >= r) return ;
    int i = l - 1, j = r + 1, x = q[(l + r) >> 1];
    while (i < j) {
        do i ++; while(q[i] < x);
        do j --; while(q[j] > x);
        if (i < j) swap(q[i], q[j]);
    }
    quicksort(q, l, j);
    quicksort(q, j + 1, r);
}

int main() {
    scanf("%d", &n);
    for (int i = 0; i < n; i ++ ) scanf("%d", &q[i]);

    quicksort(q, 0, n - 1);

    for (int i = 0; i < n; i ++ ) printf("%d ", q[i]);
    return 0; 
}
```

### 归并排序

归并排序要求(l, mid)，和(mid + 1, r)为有序，因此先递归处理这两部分，然后将两个有序序列合并为一个有序序列，可用用辅助数组temp[]存放有序序列。

模版：
```c
#include<iostream>
using namespace std;

const int N = 1e5 + 5;
int n;
int q[N], temp[N];

void mergesort(int *q, int l, int r) {
    if (l >= r) return ;
    
    int mid = (l + r) >> 1;
    mergesort(q, l, mid);
    mergesort(q, mid + 1, r);

    int i = l, j = mid + 1, k = 0;
    while (i <= mid && j <= r) {
        if (q[i] < q[j]) temp[k ++ ] = q[i ++ ];
        else temp[k ++ ] = q[j ++ ];
    }
    while(i <= mid) temp[k ++ ] = q[i ++ ];
    while(j <= r) temp[k ++ ] = q[j ++ ];

    for (int i = l, j = 0; i <= r; i ++, j ++ ) {
        q[i] = temp[j];
    }
}

int main() {
    scanf("%d", &n);
    for (int i = 0; i < n; i ++ ) scanf("%d", &q[i]);
    mergesort(q, 0, n - 1);
    for (int i = 0; i < n; i ++ ) printf("%d ", q[i]);
    return 0;
}
```
经典例题：求逆序对个数。让mergesort()能够排序同时能够求逆序对个数，所以左半边和右半边逆序对个数递归就可以得到。因此只需在左右两边排好序后，求分布在左右两边的逆序对个数：由于左右两个序列都有序，右边序列的数如果小，那么对应该数的逆序对有(mid - i + 1)个，因为左边序列递增，所以比它大的数有(mid - i + 1)个。

### 整数二分

递增数列，如1 2 2 3 3 4，3的起始位置和终止位置是3，5，求3的左端点用bsearch_l()。二分一定有答案，比如求5的左端点用的性质a[mid] >= k，找到的边界l和r为5，但是a[5] = 4不等于要求的5，因此输出-1 -1。

模版：
```c
#include <iostream>
using namespace std;

const int N = 1e5 + 5;
int n, q;
int a[N];

int bsearch_l(int l, int r, int k) {
    while (l < r) {
        int mid = (l + r) >> 1;
        if (a[mid] >= k) r = mid;  // check(mid)判断mid是否满足性质，这里的为a[mid] >= k
        else l = mid + 1;
    }
    return l;  // 返回l或r都可（l和r相等）
}

int bsearch_r(int l, int r, int k) {
    while (l < r) {
        int mid = (l + r + 1) >> 1;
        if (a[mid] <= k) l = mid;
        else r = mid - 1;
    }
    return l;
}
int main() {
    scanf("%d %d", &n, &q);
    for (int i = 0; i < n; i ++ ) scanf("%d", &a[i]);
    int k;
    for (int i = 0; i < q; i ++ ) {
        scanf("%d", &k);
        int l = bsearch_l(0, n - 1, k);
        if (a[l] != k) printf("-1 -1\n");
        else printf("%d %d\n", l, bsearch_r(0, n - 1, k));
    }
    return 0;
}
```

### 浮点数二分

模版：
```c
#include <iostream>
using namespace std;

double n;

double bsearch(double l, double r, double n) {
    double eps = 1e-8;  // 保留6位小数
    while (r - l > eps) {
        double mid = (l + r) / 2;
        if (mid * mid * mid > n) r = mid;
        else l = mid;
    }
    return l;
}

int main() {
    scanf("%lf", &n);
    printf("%.6lf\n", bsearch(-10000, 10000, n));
    return 0;
}
```

### 高精度加法
```c
#include <iostream>
using namespace std;

int main() {
    
}
```

### 高精度减法

### 高精度乘法

### 高精度除法


# dfs

全排列
```c
#include<iostream>
using namespace std;
int a[10]; 
int vis[10];
int n;
void dfs(int x){
	if(x==n+1){ 
		for(int i=1;i<=n;i++){
			cout<<a[i]<<" ";
		}
		cout<<endl;
		return ;
	}
	
	for(int i=1;i<=n;i++){
		if(!vis[i]){  // 如果i没有被用过，将i放在第x位置上，即a[x] = i
			vis[i]=1;
			a[x]=i;
			dfs(x+1);
			vis[i]=0;//回溯
		}
	}
}
int main(){
	cin >> n;
	dfs(1);  // 从第1个位置开始放
	return 0;
}
```