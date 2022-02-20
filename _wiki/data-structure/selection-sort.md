---
layout  : wiki
title   : 선택 정렬 (Seletion Sort)
summary : 
date    : 2022-02-20 19:37:59 +0900
updated : 2022-02-20 19:43:45 +0900
tags    : 
toc     : true
public  : true
parent  : [[data-structure/index]]
latex   : false
---
* TOC
{:toc}

## 소개
정렬순서상 가장 앞서는 것을 선택해서 가장 왼쪽으로 이동시키고, 원래 그 자리에 있던 데이터는 빈 자리에 가져다 놓는다.
1. 주어진 리스트 중에 최소값을 찾는다.
2. 그 값을 맨 앞에 위치한 값과 교체한다(패스(pass)).
3. 맨 처음 위치를 뺀 나머지 리스트를 같은 방법으로 교체한다.

## 성능
O(n^2)

## SelectionSort.c
```c
#include <stdio.h>

void SelSort(int arr[], int n) {
    int i, j;
    int maxIdx;
    int temp;

    for (i = 0; i < n - 1; i++) {
        maxIdx = i;

        for (j = i + 1; j < n; j++) {
            if (arr[j] < arr[maxIdx])
                maxIdx = j;
        }

        temp = arr[i];
        arr[i] = arr[maxIdx];
        arr[maxIdx] = temp;
    }
}

int main(void) {
    int arr[4] = {3, 4, 1, 2};
    int i;

    SelSort(arr, sizeof(arr) / sizeof(int));

    for (i = 0; i < 4; i++)
        printf("%d ", arr[i]);

    printf("\n");

    return 0;
}
```
