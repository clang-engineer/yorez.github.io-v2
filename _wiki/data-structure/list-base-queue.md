---
layout  : wiki
title   : 연결 리스트 기반 큐
summary : 
date    : 2022-02-17 20:56:40 +0900
updated : 2022-02-17 21:00:18 +0900
tags    : 
toc     : true
public  : true
parent  : [[data-structure/index]]
latex   : false
---
* TOC
{:toc}

## main.c 
```c
#include <stdio.h>
#include "ListBaseQueue.h"

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

## ListBaseQueue.h
```c
#ifndef __LB_QUEUE_H__
#define __LB_QUEUE_H__

#define TRUE    1
#define FALSE   0

typedef int Data;

typedef struct _node {
    Data data;
    struct _node *next;
} Node;

typedef struct _lQueue {
    Node *front;
    Node *rear;
} LQueue;

typedef LQueue Queue;

void QueueInit(Queue *pq);

int QIsEmpty(Queue *pq);

void Enqueue(Queue *pq, Data data);

Data Dequeue(Queue *pq);

Data QPeek(Queue *pq);

#endif
```

## ListBaseQueue.c
```c
#include <stdio.h>
#include <stdlib.h>
#include "ListBaseQueue.h"

void QueueInit(Queue *pq) {
    pq->front = NULL;
    pq->rear = NULL;
}

int QIsEmpty(Queue *pq) {
    if (pq->front == NULL)
        return TRUE;
    else
        return FALSE;
}

void Enqueue(Queue *pq, Data data) {
    Node *newNode = (Node *) malloc(sizeof(Node));
    newNode->next = NULL;
    newNode->data = data;

    if (QIsEmpty(pq)) {
        pq->front = newNode;
        pq->rear = newNode;
    } else {
        pq->rear->next = newNode;
        pq->rear = newNode;
    }
}

Data Dequeue(Queue *pq) {
    Node *delNode;
    Data retData;

    if (QIsEmpty(pq)) {
        printf("Queue Memory Error!");
        exit(-1);
    }

    delNode = pq->front;
    retData = delNode->data;
    pq->front = pq->front->next;

    free(delNode);
    return retData;
}

Data QPeek(Queue *pq) {
    if (QIsEmpty(pq)) {
        printf("Queue Memory Error!");
        exit(-1);
    }

    return pq->front->data;
}
```
