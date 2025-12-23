---
layout: article
title: 算法
tags: CS
cover: /assets/images/axure/page-single.jpg
---

<!--more-->
# 排序
### 快速排序
这种方法只能选第一个元素作为pivot
```c
#include<iostream>
using namespace std;
const int N = 1e5+5;
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
### 归并排序


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