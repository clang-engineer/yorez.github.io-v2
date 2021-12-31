---
layout  : wiki
title   : 이진탐색
summary : 
date    : 2021-12-31 17:12:43 +0900
updated : 2021-12-31 17:38:19 +0900
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
- 탐색 범위 확장에 따른 연산 횟수 증가량이 크지 않으므로 다량 데이터 검색에 유리
 
```c
#include <stdio.h>

int BSearch(int ar[], int len, int target);

int main(void) {
    #include <stdio.h>

int BSearch(int ar[], int len, int target) {
    int first = 0;
    int last = len - 1;
    int mid;

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
    }
    return -1;
}

int main(void) {
    int arr[] = {1, 3, 5, 7, 9};
    int idx;

    idx = BSearch(arr, sizeof(arr) / sizeof(int), 7);
    if (idx == -1)
        printf("can not find factor. \n");
    else
        printf("position is: %d. \n", idx);

    idx = BSearch(arr, sizeof(arr) / sizeof(int), 4);
    if (idx == -1)
        printf("can not find factor. \n");
    else
        printf("position is: %d. \n", idx);
}

```
