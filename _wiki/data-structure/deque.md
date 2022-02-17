---
layout  : wiki
title   : 덱(deq)
summary : 
date    : 2022-02-17 23:03:26 +0900
updated : 2022-02-17 23:12:08 +0900
tags    : 
toc     : true
public  : true
parent  : [[data-structure/index]]
latex   : false
---
* TOC
{:toc}

## 소개
- 덱은 앞으로도 뒤로도 넣을 수 있고, 앞으로도 뒤로도 뺄 수 있는 자료구조
(<-> 큐는 뒤로 넣고 앞으로 빼는 자료구조)
- 배열을 기반으로, 연결 리스트를 기반으로 모두 구현 가능하지만, 덱의 구현에는 '양방향 연결 리스트'를 사용하는 것이 적합한 선택

## main.c 
```c
#include <stdio.h>
#include "Deque.h"

int main(void) {
    Deque deq;
    DequeInit(&deq);

    DQAddFirst(&deq, 3);
    DQAddFirst(&deq, 2);
    DQAddFirst(&deq, 1);

    DQAddLast(&deq, 4);
    DQAddLast(&deq, 5);
    DQAddLast(&deq, 6);

    while (!DQIsEmpty(&deq))
        printf("%d ", DQRemoveFirst(&deq));

    printf("\n");

    DQAddFirst(&deq, 3);
    DQAddFirst(&deq, 2);
    DQAddFirst(&deq, 1);

    DQAddLast(&deq, 4);
    DQAddLast(&deq, 5);
    DQAddLast(&deq, 6);

    while (!DQIsEmpty(&deq))
        printf("%d ", DQRemoveLast(&deq));

    printf("\n");

    return 0;
}
```

## Deque.h
```c
#ifndef __DEQUE_H__
#define __DEQUE_H__

#define TRUE    1
#define FALSE   0

typedef int Data;

typedef struct _node {
    Data data;
    struct _node *next;
    struct _node *prev;
} Node;

typedef struct _dlDeque {
    Node *head;
    Node *tail;
} DLDequeue;

typedef DLDequeue Deque;

void DequeInit(Deque *pdeq);

int DQIsEmpty(Deque *pdeq);

void DQAddFirst(Deque *pdeq, Data data);

void DQAddLast(Deque *pdeq, Data data);

Data DQRemoveFirst(Deque *pdeq);

Data DQRemoveLast(Deque *pdeq);

Data DQGetFirst(Deque *pdeq);

Data DQGetLast(Deque *pdeq);

#endif
```

## Deque.c
```c
#include <stdio.h>
#include <stdlib.h>
#include "Deque.h"

void DequeInit(Deque *pdeq) {
    pdeq->head = NULL;
    pdeq->tail = NULL;
}

int DQIsEmpty(Deque *pdeq) {
    if (pdeq->head == NULL)
        return TRUE;
    else
        return FALSE;
}

void DQAddFirst(Deque *pdeq, Data data) {
    Node *newNode = (Node *) malloc(sizeof(Node));
    newNode->data = data;

    newNode->next = pdeq->head;

    if (DQIsEmpty(pdeq))
        pdeq->tail = newNode;
    else
        pdeq->head->prev = newNode;

    newNode->prev = NULL;
    pdeq->head = newNode;
}

void DQAddLast(Deque *pdeq, Data data) {
    Node *newNode = (Node *) malloc(sizeof(Node));
    newNode->data = data;
    newNode->prev = pdeq->tail;

    if (DQIsEmpty(pdeq))
        pdeq->head = newNode;
    else
        pdeq->tail->next = newNode;

    newNode->next = NULL;
    pdeq->tail = newNode;
}

Data DQRemoveFirst(Deque *pdeq) {
    Node *rnode = pdeq->head;
    Data rdata;

    if (DQIsEmpty(pdeq)) {
        printf("Deque Memory Error!");
        exit(-1);
    }

    rdata = pdeq->head->data;

    pdeq->head = pdeq->head->next;
    free(rnode);

    if (pdeq->head == NULL)
        pdeq->tail = NULL;
    else
        pdeq->head->prev = NULL;

    return rdata;
}

Data DQRemoveLast(Deque *pdeq) {
    Node *rnode = pdeq->tail;
    Data rdata;

    if (DQIsEmpty(pdeq)) {
        printf("Deque Memory Error!");
        exit(-1);
    }
    rdata = pdeq->tail->data;

    pdeq->tail = pdeq->tail->prev;
    free(rnode);

    if (pdeq->tail == NULL)
        pdeq->head = NULL;
    else
        pdeq->tail->next = NULL;

    return rdata;
}

Data DQGetFirst(Deque *pdeq) {
    if (DQIsEmpty(pdeq)) {
        printf("Deque Memory Error!");
        exit(-1);
    }

    return pdeq->head->data;
}

Data DQGetLast(Deque *pdeq) {
    if (DQIsEmpty(pdeq)) {
        printf("Deque Memory Error!");
        exit(-1);
    }

    return pdeq->tail->data;
}
```
