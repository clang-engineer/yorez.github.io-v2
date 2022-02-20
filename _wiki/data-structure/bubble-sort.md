---
layout  : wiki
title   : 버블 정렬 알고리즘
summary : 
date    : 2022-02-20 19:00:20 +0900
updated : 2022-02-20 19:04:44 +0900
tags    : 
toc     : true
public  : true
parent  : 
latex   : false
---
* TOC
{:toc}

## 소개
인접한 두 개의 데이터를 비교해가면서 정렬을 진행하는 방식

## 성능
O(n^2)

## BubbleSort.c
```c
#include <stdio.h>

void BubbleSort(int arr[], int n) {
    int i, j;
    int temp;

    for (i = 0; i < n - 1; i++) {
        for (j = 0; j < (n - i) - 1; j++) {
            if (arr[j] > arr[j + 1]) {
                temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
}

int main(void) {
    int arr[4] = {3, 2, 4, 1};
    int i;

    BubbleSort(arr, sizeof(arr) / sizeof(int));

    for (i = 0; i < 4; i++)
        printf("%d ", arr[i]);

    printf("\n");
    return 0;
}
```
