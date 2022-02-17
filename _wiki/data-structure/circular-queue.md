---
layout  : wiki
title   : 원형큐
summary : 
date    : 2022-02-17 20:33:58 +0900
updated : 2022-02-17 23:18:28 +0900
tags    : 
toc     : true
public  : true
parent  : 
latex   : false
---
* TOC
{:toc}

## 소개
- 큐는 '선입선출'구조의 자료구조. FIFO(First-In, First-Out)구조의 자료구조.
- 큐를 배열 기반으로 구현할 때, 큐를 구성하는 배열을 효율적으로 사용하기 위해 원형 큐를 사용.
- 배열 기반의 큐라하면 대부분의 경우 원형 큐를 의미한다고 봐도 무방.

## main.c
```c
#include <stdio.h>
#include "CircularQueue.h"

int main(void) {
    Queue q;
    QueueInit(&q);

    Enqueue(&q, 1);
    Enqueue(&q, 2);
    Enqueue(&q, 3);
    Enqueue(&q, 4);
    Enqueue(&q, 5);

    while (!QIsEmpty(&q))
        printf("%d ", Dequeue(&q));

    return 0;
}
```

## CircularQueue.h
```c
#ifndef __C_QUEUE_H__
#define __C_QUEUE_H__

#define TRUE    1
#define FALSE    0

#define QUE_LEN    100
typedef int Data;

typedef struct _cQueue {
    int front;
    int rear;
    Data queArr[QUE_LEN];
} CQueue;

typedef CQueue Queue;

void QueueInit(Queue *pq);

int QIsEmpty(Queue *pq);

void Enqueue(Queue *pq, Data data);

Data Dequeue(Queue *pq);

Data QPeek(Queue *pq);

#endif
```

## CircularQueue.c
```c
#include <stdio.h>
#include <stdlib.h>
#include "CircularQueue.h"

void QueueInit(Queue *pq) {
    pq->front = 0;
    pq->rear = 0;
}

int QIsEmpty(Queue *pq) {
    if (pq->front == pq->rear)
        return TRUE;
    else
        return FALSE;
}

int NextPosIdx(int pos) {
    if (pos == QUE_LEN - 1)
        return 0;
    else
        return pos + 1;
}

void Enqueue(Queue *pq, Data data) {
    if (NextPosIdx(pq->rear) == pq->front) {
        printf("Queue Memory Error!");
        exit(-1);
    }

    pq->rear = NextPosIdx(pq->rear);
    pq->queArr[pq->rear] = data;
}

Data Dequeue(Queue *pq) {
    if (QIsEmpty(pq)) {
        printf("Queue Memory Error!");
        exit(-1);
    }

    pq->front = NextPosIdx(pq->front);
    return pq->queArr[pq->front];
}

Data QPeek(Queue *pq) {
    if (QIsEmpty(pq)) {
        printf("Queue Memory Error!");
        exit(-1);
    }

    return pq->queArr[NextPosIdx(pq->front)];
}
```
