---
layout: post
title: "摆花" 
category: noip
tags: [noip, 信息竞赛]
---

# 摆花

## 【问题描述】

小明的花店新开张，为了吸引顾客，他想在花店的门口摆上一排花，共 m 盆。通过调查顾客的喜好，小明列出了顾客最喜欢的 n 种花，从 1 到 n 标号。为了在门口展出更多种花，规定第 i 种花不能超过 ai盆，摆花时同一种花放在一起，且不同种类的花需按标号的从小到大的顺序依次摆列。
试编程计算，一共有多少种不同的摆花方案。

## 【输入】

输入文件 flower.in，共 2 行。
第一行包含两个正整数 n 和 m，中间用一个空格隔开。
第二行有 n 个整数，每两个整数之间用一个空格隔开，依次表示 a1、a2、……an。

## 【输出】
输出文件名为 flower.out。
输出只有一行，一个整数，表示有多少种方案。注意：因为方案数可能很多，请输出方案数对 1000007 取模的结果。

## 【输入输出样例 1】

flower.in

2 4

3 2

flower.out

2

## 分析
 
a[i]表示第i种花最多使用的盆数

f[i][j]表示前i种花，摆j盆的摆放方案数。对于第i种花可以使用0、1、2...a[i]盆,对应的前i-1种花摆放的盆数为j-0、j-1、j-2、...j-a[i]

即f[i][j]=f[i-1][j]+f[i-1][j-1]+f[i-1][j-2]+...+f[i-1][j-a[i]] = 求和(f[i-1][j-k])      【0<=k<=a[i],j>=k】

状态转移方程写出来后，最关键的就是赋初始值

初始值f[1][0]=1,f[1][1]=1,...f[1][a[1]]=1; 

初始值f[i][0]=1;

以

2 4

3 2

为例：

很显然f[1][1]=f[1][2]=f[1][3]=1;

f[2][1]=2,前2种花，放一盆，则有1,2两种方法。又

f[2][1]=f[1][0]+f[1][1]=f[1][0]+1可以推出f[1][0]=1；

同样的方法可以推出f[2][0]=f[3][0]=...=f[n][0]=1;

(f[2][2]=f[1][0]+f[1][1]+f[1][2]

f[2][3]=f[1][1]+f[1][2]+f[1][3]

f[2][4]=f[1][2]+f[1][3]+f[1][4])

```Java
#include <iostream>
#include <cstdio>

using namespace std;

int main()
{
    int a[105]={0};
    int f[105][105];
    int m, n;
    
    cin >> n >> m;
    
    for (int i = 1; i <= n; i++ )
        cin >> a[i];
    
    for (int i = 1; i <= a[1]; i++)
        f[1][i] = 1;
    
    for (int i =1 ; i <= n; i++)
        f[i][0] = 1;
    
    for (int i = 2; i <= n; i++ )
        for (int j = 1; j <= m; j++ )
            for (int k = 0; (k <= a[i]) && (j >= k); k++)
            {
                f[i][j] += f[i-1][j-k];
                f[i][j] %= 1000007;
            }
    cout << f[n][m] << endl;
    
    return 0;
}
```
