---
layout  : wiki
title   : 삽입 정렬(Insertion Sort)
summary : 
date    : 2022-02-20 19:59:55 +0900
updated : 2022-02-20 20:02:12 +0900
tags    : 
toc     : true
public  : true
parent  : [[data-structure/index]]
latex   : false
---
* TOC
{:toc}

## 소개
자료 배열의 모든 요소를 앞에서부터 차례대로 이미 정렬된 배열 부분과 비교하여, 자신의 위치를 찾아 삽입함으로써 정렬을 완성하는 알고리즘.

## 성능
O(n^2)

## InsertionSort.c
```c
#include <stdio.h>

void InsertSort(int arr[], int n) {
    int i, j;
    int insData;

    for (i = 1; i < n; i++) {
        insData = arr[i];

        for (j = i - 1; j >= 0; j--) {
            if (arr[j] > insData)
                arr[j + 1] = arr[j];
            else
                break;
        }

        arr[j + 1] = insData;
    }
}

int main(void) {
    int arr[5] = {5, 3, 2, 4, 1};
    int i;

    InsertSort(arr, sizeof(arr) / sizeof(int));

    for (i = 0; i < 5; i++)
        printf("%d ", arr[i]);

    printf("\n");
    return 0;
}
```
