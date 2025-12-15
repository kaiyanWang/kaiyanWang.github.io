---
layout: article
title: 算法
tags: CS
cover: /assets/images/axure/page-single.jpg
---

<!--more-->

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