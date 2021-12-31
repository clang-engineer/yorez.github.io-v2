---
layout  : wiki
title   : 이진탐색
summary : 
date    : 2021-12-31 17:12:43 +0900
updated : 2021-12-31 17:15:44 +0900
tags    : 
toc     : true
public  : true
parent  : [[data-structure/index]]
latex   : false
---
* TOC
{:toc}

## 이진탐색

- 탐색 범위를 절반씩 줄여가면서 원소를 찾는 알고리즘
```c
#include <stdio.h>

int BSearch(int ar[], int len, int target);

int main(void) {
    int arr1[500] = {0,};
    int arr2[5000] = {0,};
    int arr3[50000] = {0,};
    int idx;

    idx = BSearch(arr1, sizeof(arr1) / sizeof(int), 1);
    if (idx == -1)
        printf("can not find factor. \n\n");
    else
        printf("position is: %d. \n\n", idx);

    idx = BSearch(arr2, sizeof(arr2) / sizeof(int), 1);
    if (idx == -1)
        printf("can not find factor. \n\n");
    else
        printf("position is: %d. \n\n", idx);

    idx = BSearch(arr3, sizeof(arr3) / sizeof(int), 1);
    if (idx == -1)
        printf("can not find factor. \n\n");
    else
        printf("position is: %d. \n\n", idx);

    return 0;
}

int BSearch(int ar[], int len, int target) {
    int first = 0;
    int last = len - 1;
    int mid;
    int opCount = 0;

    while (first <= last) {
        mid = (first + last) / 2;

        if (target == ar[mid]) {
            return mid;
        } else {
            if (target < ar[mid])
                last = mid - 1;
            else
                first = mid + 1;
        }
        opCount += 1;
    }

    printf("operator count: %d\n", opCount);
    return -1;
}
```
