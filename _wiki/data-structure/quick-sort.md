---
layout  : wiki
title   : 퀵 정렬(Quick Sort)
summary : 
date    : 2022-02-25 10:37:18 +0900
updated : 2022-02-25 10:56:21 +0900
tags    : 
toc     : true
public  : true
parent  : [[data-structure/index]]
latex   : false
---
* TOC
{:toc}

## 소개
1. 배열 가운데서 하나의 원소를 고른다. 이렇게 고른 원소를 피벗(pivot) 이라고 한다.
2. 피벗 앞에는 피벗보다 값이 작은 모든 원소들이 오고, 피벗 뒤에는 피벗보다 값이 큰 모든 원소들이 오도록 피벗을 기준으로 배열을 둘로 나눈다. 이렇게 배열을 둘로 나누는 것을 분할(Divide) 이라고 한다. 분할을 마친 뒤에 피벗은 더 이상 움직이지 않는다.
3. 분할된 두 개의 작은 배열에 대해 재귀(Recursion)적으로 이 과정을 반복한다.

## 성능
O(nlog_2_n)

## QuickSort.c
```c
#include <stdio.h>

void Swap(int arr[], int idx1, int idx2) {
    int temp = arr[idx1];
    arr[idx1] = arr[idx2];
    arr[idx2] = temp;
}

int Partition(int arr[], int left, int right) {
    int pivot = arr[left];
    int low = left + 1;
    int high = right;

    while (low <= high) {
        while (pivot >= arr[low] && low <= right)
            low++;

        while (pivot <= arr[high] && high >= (left + 1))
            high--;

        if (low <= high)
            Swap(arr, low, high);
    }

    Swap(arr, left, high);
    return high;
}

void QuickSort(int arr[], int left, int right) {
    if (left <= right) {
        int pivot = Partition(arr, left, right);
        QuickSort(arr, left, pivot - 1);
        QuickSort(arr, pivot + 1, right);
    }
}

int main(void) {
    int arr[7] = {3, 2, 4, 1, 7, 6, 5};
//    int arr[3] = {3, 3, 3};

    int len = sizeof(arr) / sizeof(int);
    int i;

    QuickSort(arr, 0, sizeof(arr) / sizeof(int) - 1);

    for (i = 0; i < len; i++)
        printf("%d ", arr[i]);

    printf("\n");
    return 0;
}
```
