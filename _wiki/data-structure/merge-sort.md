---
layout  : wiki
title   : 병합 정렬(Merge Sort)
summary : 
date    : 2022-02-21 00:16:10 +0900
updated : 2022-02-21 00:28:35 +0900
tags    : 
toc     : true
public  : true
parent  : [[data-structure/index]]
latex   : false
---
* TOC
{:toc}

## 소개
1. 분할: 해결이 용이한 단계까지 문제를 분할
2. 정복: 해결이 용이한 수준까지 분할된 문제를 해결
3. 결합: 분할해서 해결한 결과를 결합하여 마무리

## 성능
O(nlog_2_n)

## MergeSort.c
```c
#include <stdio.h>
#include <stdlib.h>

void MergeTwoArea(int arr[], int left, int mid, int right) {
    int fIdx = left;
    int rIdx = mid + 1;
    int i;

    int *sortArr = (int *) malloc(sizeof(int) * (right + 1));
    int sIdx = left;

    while (fIdx <= mid && rIdx <= right) {
        if (arr[fIdx] <= arr[rIdx])
            sortArr[sIdx] = arr[fIdx++];
        else
            sortArr[sIdx] = arr[rIdx++];

        sIdx++;
    }

    if (fIdx > mid) {
        for (i = rIdx; i <= right; i++, sIdx++)
            sortArr[sIdx] = arr[i];
    } else {
        for (i = fIdx; i <= mid; i++, sIdx++)
            sortArr[sIdx] = arr[i];
    }

    for (i = left; i <= right; i++)
        arr[i] = sortArr[i];

    free(sortArr);
}

void MergeSort(int arr[], int left, int right) {
    int mid;

    if (left < right) {
        mid = (left + right) / 2;

        MergeSort(arr, left, mid);
        MergeSort(arr, mid + 1, right);

        MergeTwoArea(arr, left, mid, right);
    }
}

int main(void) {
    int arr[7] = {3, 2, 4, 1, 7, 6, 5};
    int i;

    MergeSort(arr, 0, sizeof(arr) / sizeof(int) - 1);

    for (i = 0; i < 7; i++)
        printf("%d ", arr[i]);

    printf("\n");
    return 0;
}
```
