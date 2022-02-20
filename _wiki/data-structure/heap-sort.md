---
layout  : wiki
title   : 힙 정렬(Heap Sort) 
summary : 
date    : 2022-02-20 23:06:58 +0900
updated : 2022-02-20 23:16:51 +0900
tags    : 
toc     : true
public  : true
parent  : [[data-structure/heap-sort]]
latex   : false
---
* TOC
{:toc}

## 성능
- 힙의 데이터 저장 시간 복잡도: O(log_2_n)
- 힙의 데이터 삭제 시간 복잡도: O(log_2_n)
- 힙의 정렬에 대한 시간 복잡도: O(nlog_2_n)

## HeapSort.c 
```c
#include <stdio.h>
#include "UsefulHeap.h"

int PriComp(int n1, int n2) {
    return n2 - n1;
//	return n1-n2;
}

void HeapSort(int arr[], int n, PriorityComp pc) {
    Heap heap;
    int i;

    HeapInit(&heap, pc);

    for (i = 0; i < n; i++)
        HInsert(&heap, arr[i]);

    for (i = 0; i < n; i++)
        arr[i] = HDelete(&heap);
}

int main(void) {
    int arr[4] = {3, 4, 2, 1};
    int i;

    HeapSort(arr, sizeof(arr) / sizeof(int), PriComp);

    for (i = 0; i < 4; i++)
        printf("%d ", arr[i]);

    printf("\n");
    return 0;
}
```
