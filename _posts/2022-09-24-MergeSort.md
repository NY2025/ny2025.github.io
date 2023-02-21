---
layout: post
title: "【代码模板】归并排序求逆序对"
date:   2023-02-15
comments: true
tags: [code]
author: NY2025
---

归并排序求逆序对

```c++
#include <iostream>
using namespace std;


int a[10000], b[10000];
int cnt;

void merge(int L, int mid, int R)
{
    int i = L, j = mid + 1, k = L;
    while (i <= mid && j <= R)
    {
        if (a[i] <= a[j]) b[k++] = a[i++];
        else
        {
            b[k++] = a[j++];
            cnt += mid - i + 1;
        }
    }

    while (i <= mid)
        b[k++] = a[i++];
    while (j <= R)
        b[k++] = a[j++];

    for (int m = L; m <= R; m++) b[m] = a[m];
}

void mergesort(int L, int R)
{
    if (L < R)
    {
        int mid = (L + R) / 2;
        mergesort(L, mid);
        mergesort(mid + 1, R);
        merge(L, mid, R);
    }
}

int main()
{
    int n;

    scanf("%d", &n);
    for (int i = 0; i < n; i++)
        scanf("%d", a + i);

    mergesort(0, n - 1);

    printf("%d", cnt);

    return 0;
}
```
