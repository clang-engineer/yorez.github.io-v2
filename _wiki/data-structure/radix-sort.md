---
layout  : wiki
title   : 기수 정렬(Radix Sort)
summary : 
date    : 2022-02-25 19:16:17 +0900
updated : 2022-02-25 19:36:03 +0900
tags    : 
toc     : true
public  : true
parent  : [[data-structure/index]]
latex   : false
---
* TOC
{:toc}

## 소개
낮은 자리수부터 비교하여 정렬하는 알고리즘.
비교 연산을 하지 않으며 정렬 속도가 빠르지만 데이터 전체 크기에 기수 테이블의 크기만한 메모리가 더 필요함.

## 정렬 방식
1. 0~9 까지의 Bucket(Queue 자료구조의)을 준비한다.
2. 모든 데이터에 대하여 가장 낮은 자리수에 해당하는 Bucket에 차례대로 데이터를 둔다.
3. 0부터 차례대로 버킷에서 데이터를 다시 가져온다.
4. 가장 높은 자리수를 기준으로 하여 자리수를 높여가며 2번 3번 과정을 반복한다.

## 성능
- O(n)
- 정렬대상의 수가 n이고, 모든 정렬대상의 길이가 l이라 할 때, 시간 복잡도에 대한 기수 정렬의 빅오는 O(ln)이므로 O(n)으로 표현해도 무방

## RadixSort.c
```c
#include <stdio.h>
#include "ListBaseQueue.h"

#define BUCKET_NUM 10

void RadixSort(int arr[], int num, int maxLen) {
    Queue buckets[BUCKET_NUM];
    int bi;
    int pos;
    int di;
    int divfac = 1;
    int radix;

    for (bi = 0; bi < BUCKET_NUM; bi++)
        QueueInit(&buckets[bi]);

    for (pos = 0; pos < maxLen; pos++) {
        for (di = 0; di < num; di++) {
            radix = (arr[di] / divfac) % 10;
            Enqueue(&buckets[radix], arr[di]);
        }

        for (bi = 0, di = 0; bi < BUCKET_NUM; bi++) {
            while (!QIsEmpty(&buckets[bi]))
                arr[di++] = Dequeue(&buckets[bi]);
        }

        divfac *= 10;
    }
}

int main(void) {
    int arr[7] = {13, 212, 14, 7141, 10987, 6, 15};

    int len = sizeof(arr) / sizeof(int);
    int i;

    RadixSort(arr, len, 5);

    for (i = 0; i < len; i++)
        printf("%d ", arr[i]);

    printf("\n");
    return 0;
}
```
