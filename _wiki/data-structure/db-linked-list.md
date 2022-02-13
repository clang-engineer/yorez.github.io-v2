---
layout  : wiki
title   : 양방향 연결 리스트
summary : 
date    : 2022-02-13 23:03:27 +0900
updated : 2022-02-13 23:05:59 +0900
tags    : 
toc     : true
public  : true
parent  : [[data-structure/index]]
latex   : false
---
* TOC
{:toc}

## 양방향 연결 리스트

왼쪽 노드가 오른쪽 노드를 가리키는 동시에 오른쪽 노드도 왼쪽 노드를 가리키는 구조

## main.c
```c
#include <stdio.h>
#include "DBLinkedList.h"

int main(void) {
    List list;
    int data;
    ListInit(&list);

    LInsert(&list, 1);
    LInsert(&list, 2);
    LInsert(&list, 3);
    LInsert(&list, 4);
    LInsert(&list, 5);
    LInsert(&list, 6);
    LInsert(&list, 7);
    LInsert(&list, 8);

    if (LFirst(&list, &data)) {
        printf("%d ", data);

        while (LNext(&list, &data))
            printf("%d ", data);

        while (LPrevious(&list, &data))
            printf("%d ", data);

        printf("\n\n");
    }

    return 0;
}
```

## DBLinkedList.h
```c
#ifndef __DB_LINKED_LIST_H__
#define __DB_LINKED_LIST_H__

#define TRUE    1
#define FALSE   0

typedef int Data;

typedef struct _node {
    Data data;
    struct _node *next;
    struct _node *prev;
} Node;

typedef struct _DLinkedList {
    Node *head;
    Node *cur;
    int numOfData;
} DBLinkedList;

typedef DBLinkedList List;

void ListInit(List *plist);

void LInsert(List *plist, Data data);

int LFirst(List *plist, Data *pdata);

int LNext(List *plist, Data *pdata);

int LPrevious(List *plist, Data *pdata);

int LCount(List *plist);

#endif
```

## DBLinkedList.c
```c
#include <stdio.h>
#include <stdlib.h>
#include "DBLinkedList.h"

void ListInit(List *plist) {
    plist->head = NULL;
    plist->numOfData = 0;
}

void LInsert(List *plist, Data data) {
    Node *newNode = (Node *) malloc(sizeof(Node));
    newNode->data = data;

    newNode->next = plist->head;
    if (plist->head != NULL)
        plist->head->prev = newNode;

    newNode->prev = NULL;
    plist->head = newNode;

    (plist->numOfData)++;
}

int LFirst(List *plist, Data *pdata) {
    if (plist->head == NULL)
        return FALSE;

    plist->cur = plist->head;
    *pdata = plist->cur->data;

    return TRUE;
}

int LNext(List *plist, Data *pdata) {
    if (plist->cur->next == NULL)
        return FALSE;

    plist->cur = plist->cur->next;
    *pdata = plist->cur->data;

    return TRUE;
}

int LPrevious(List *plist, Data *pdata) {
    if (plist->cur->prev == NULL)
        return FALSE;

    plist->cur = plist->cur->prev;
    *pdata = plist->cur->data;

    return TRUE;
}

int LCount(List *plist) {
    return plist->numOfData;
}
```
