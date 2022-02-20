---
layout  : wiki
title   : 우선순위 큐(Priority Queue)와 힙(Heap)
summary : 
date    : 2022-02-20 14:10:10 +0900
updated : 2022-02-20 15:02:22 +0900
tags    : 
toc     : true
public  : true
parent  : 
latex   : false
---
* TOC
{:toc}

## 소개
- 우선순위 큐란? 들어간 순서에 상관없이 우선 순위가 높은 데이터가 먼저 나오는 자료구조

### 우선순위 큐의 구현 방법
- 배열을 기반으로 구현하는 방법
- 연결 리스트를 기반으로 구현하는 방법
- 힙을 이용하는 방법

### 배열, 연결 리스트를 이용한 우선순위 큐의 단점
- 데이터를 삽입 및 삭제하는 과정에서 데이터를 한 칸씩 뒤로 밀거나 한 칸씩 앞으로 당기는 연산을 수반해야 함. (배열)
- 삽입의 위치를 찾기 위해서 첫 번째 노드에서부터 시작해서 마지막 노드에 저장된 데이터와 우선순위의 비교를 진행해야 할 수도 있음. (배열, 연결 리스트)

### 각 구현 방법의 시간복잡도 
- 배열 기반 데이터 저장, 삭제의 시간 복잡도: O(n), O(1)
- 연결 리스트 기반 데이터 저장, 삭제의 시간 복잡도: O(n), O(1) 
- 힙 기반 데이터 저장, 삭제의 시간 복잡도: O(log_2_n), O(log_2_n) <br>
  (힙은 완전 이진 트리이므로, 힙에 저장할 수 있는 데이터의 수는 트리의 높이가 하나 늘 때마다 두배씩 증가함.
  때문에 데이터의 수가 두 배 늘 때마다, 비교연산의 횟수는 1회 증가함.)

## 힙의 소개
- 힙은 '이진 트리'이되 '완전 이진 트리'이다. 그리고 모든 노드에 저장된 값은 자식 노드에 저장된 값보다 크거나 값아야 함. 
즉 루트 노드에 저장된 값이 가장 커야 함. 
- 루트 노드로 올라갈수록 저장된 값이 커지는 완전 이진 트리를 가리켜 '최대 힙(max heap)', 반대로 루트 노드로 올라갈수록 저장된 값이 작아지는 완전 이진트리를
 가리켜 '최소 힙(min heap)'이라 함.

### 힙에서의 데이터 저장 과정
- 새로운 데이터는 우선순위가 제일 낮다는 가정하에서 '마지막 위치에' 저장함. 
그리고 부모 노드와 우선순위를 비교해가면서 제대로된 위치가 될 때까지 바꿔줌. 

### 힙에서의 데이터 삭제 과정
- 우선순위 큐의 삭제는 '가장 높은 우선순위의 데이터를 삭제'를 의미함.
- 마지막 노드를 루트 노드의 자리로 옮긴 다음에, 자식 노드와의 비교를 통해서 제대로된 위치가 될 때까지 바꿔줌.

### 힙의 구현에 어울리는 것은 연결 리스트? 아니면 배열?
- 연결 리스트를 기반으로 힙을 구현하면, 새로운 노드를 힙의 '마지막 위치'에 추가하는 것이 쉽지 않음.
때문에, 힙과 같이 새로운 노드를 추가한 이후에도 완전 이진 트리를 유지해야하는 경우에는 연결 리스트가 아닌 배열을 기반으로 트리를 구현해야 함.


## main.c
```c
#include <stdio.h>
#include "UsefulHeap.h"

int DataPriorityComp(char ch1, char ch2) {
    return ch2 - ch1;
//    return ch1 - ch2;
}

int main(void) {
    Heap heap;
    HeapInit(&heap, DataPriorityComp);

    HInsert(&heap, 'A');
    HInsert(&heap, 'B');
    HInsert(&heap, 'C');
    printf("%c \n", HDelete(&heap));

    HInsert(&heap, 'A');
    HInsert(&heap, 'B');
    HInsert(&heap, 'C');
    printf("%c \n", HDelete(&heap));

    while (!HIsEmpty(&heap))
        printf("%c \n", HDelete(&heap));

    return 0;
}
```

## UsefulHeap.h
```c
#ifndef __USEFUL_HEAP_H__
#define __USEFUL_HEAP_H__

#define TRUE 1
#define FALSE 0

#define HEAP_LEN 100

typedef char HData;
typedef int PriorityComp(HData d1, HData d2);

typedef struct _heap {
    PriorityComp* comp;
    int numOfData;
    HData heapArr[HEAP_LEN];
} Heap;

void HeapInit(Heap *ph, PriorityComp pc);

int HIsEmpty(Heap *ph);

void HInsert(Heap *ph, HData data);

HData HDelete(Heap *ph);

#endif
```

## UsefulHeap.c
```c
#include "UsefulHeap.h"

void HeapInit(Heap *ph, PriorityComp pc) {
    ph->numOfData = 0;
    ph->comp = pc;
}

int HIsEmpty(Heap *ph) {
    if (ph->numOfData == 0)
        return TRUE;
    else
        return FALSE;
}

int GetParentIDX(int idx) {
    return idx / 2;
}

int GetLChildIDX(int idx) {
    return idx * 2;
}

int GetRChildIDX(int idx) {
    return GetLChildIDX(idx) + 1;
}

int GetHiPriChildIDX(Heap *ph, int idx) {
    if (GetLChildIDX(idx) > ph->numOfData)
        return 0;
    else if (GetLChildIDX(idx) == ph->numOfData)
        return GetLChildIDX(idx);
    else {
        if (ph->comp(ph->heapArr[GetLChildIDX(idx)], ph->heapArr[GetRChildIDX(idx)]) < 0)
            return GetRChildIDX(idx);
        else
            return GetLChildIDX(idx);
    }
}

void HInsert(Heap *ph, HData data) {
    int idx = ph->numOfData + 1;

    while (idx != 1) {
        if (ph->comp(data, ph->heapArr[GetParentIDX(idx)]) > 0) {
            ph->heapArr[idx] = ph->heapArr[GetParentIDX(idx)];
            idx = GetParentIDX(idx);
        } else
            break;
    }

    ph->heapArr[idx] = data;
    ph->numOfData += 1;
}

HData HDelete(Heap *ph) {
    HData retData = ph->heapArr[1];
    HData lastElem = ph->heapArr[ph->numOfData];

    int parentIdx = 1;
    int childIdx;

    while ((childIdx = GetHiPriChildIDX(ph, parentIdx))) {
        if (ph->comp(lastElem, ph->heapArr[childIdx]) >= 0)
            break;

        ph->heapArr[parentIdx] = ph->heapArr[childIdx];
        parentIdx = childIdx;
    }

    ph->heapArr[parentIdx] = lastElem;
    ph->numOfData -= 1;
    return retData;
}
```
