---
layout  : wiki
title   : 보간탐색
summary : 
date    : 2022-02-25 22:33:13 +0900
updated : 2022-02-25 23:20:35 +0900
tags    : 
toc     : true
public  : true
parent  : [[data-structure/index]]
latex   : false
---
* TOC
{:toc}

## 소개
- 정렬이 이미 되어 있는 리스트에서 탐색키가 존재할 위치를 예측하여 탐색하는 방법
- 이진 탐색과 유사하나 리스트를 반으로 분할하지 않고 불균등하게 분할하여 탐색함 (이진탐색의 업그레이드 버전)

## RecuriveBinarySearch.c
```c
#include <stdio.h>

int ISearch(int ar[], int first, int last, int target) {
    int mid;

    if (ar[first] > target || ar[last] < target)
        return -1;

    mid = ((double) (target - ar[first]) / (ar[last] - ar[first]) * (last - first)) + first;

    if (ar[mid] == target)
        return mid;
    else if (target < ar[mid])
        return ISearch(ar, first, mid - 1, target);
    else
        return ISearch(ar, mid + 1, last, target);
}

int main(void) {
    int arr[] = {1, 3, 5, 7, 9};
    int idx;

    idx = ISearch(arr, 0, sizeof(arr) / sizeof(int) - 1, 7);
    if (idx == -1)
        printf("탐색 실패");
    else
        printf("타겟 저장 인덱스: %d \n", idx);

    idx = ISearch(arr, 0, sizeof(arr) / sizeof(int) - 1, 2);
    if (idx == -1)
        printf("탐색 실패");
    else
        printf("타겟 저장 인덱스: %d \n", idx);

    return 0;
}
```
