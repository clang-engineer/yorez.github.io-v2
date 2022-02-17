---
layout  : wiki
title   : 원형 연결 리스트(Circular Linked List)
summary : 
date    : 2022-02-13 22:18:16 +0900
updated : 2022-02-17 23:34:26 +0900
tags    : 
toc     : true
public  : true
parent  : [[data-structure/index]]
latex   : false
---
* TOC
{:toc}

## 소개 
- 마지막 노드가 첫 번째 노드를 가리키는 자료구조. 
- 단순 연결 리스트처럼 머리와 꼬리를 가리키는 포인터 변수를 각각 두지 않아도, 하나의 포인터 변수만 있어도 머리 또는 꼬리에 노드를 간단히 추가할 수 있다.
- 하나의 포인터 변수가, 머리가 아닌 꼬리를 가리키게 하는 것이 효율적임.

## main.c
```c
#include <stdio.h>
#include "CLInkedList.h"

int main(void) {
    List list;
    int data, i, nodeNum;
    ListInit(&list);

    LInsert(&list, 3);
    LInsert(&list, 4);
    LInsert(&list, 5);

    LInsertFront(&list, 2);
    LInsertFront(&list, 1);

    if (LFirst(&list, &data)) {
        printf("%d ", data);

        for (i = 0; i < LCount(&list) * 3 - 1; i++) {
            if (LNext(&list, &data))
                printf("%d ", data);
        }
    }
    printf("\n");

    nodeNum = LCount(&list);

    if (nodeNum != 0) {
        LFirst(&list, &data);
        if (data % 2 == 0)
            LRemove(&list);

        for (i = 0; i < nodeNum - 1; i++) {
            LNext(&list, &data);
            if (data % 2 == 0)
                LRemove(&list);
        }
    }

    if (LFirst(&list, &data)) {
        printf("%d ", data);

        for (i = 0; i < LCount(&list) - 1; i++) {
            if (LNext(&list, &data))
                printf("%d ", data);
        }
    }

    return 0;
}
```

## CLinkedList.h
```c
#ifndef __C_LINKED_LIST_H__
#define __C_LINKED_LIST_H__

#define TRUE    1
#define FALSE   0

typedef int Data;

typedef struct _node {
    Data data;
    struct _node *next;
} Node;

typedef struct _CLL {
    Node *tail;
    Node *cur;
    Node *before;
    int numOfData;
} CList;

typedef CList List;

void ListInit(List *plist);

void LInsert(List *plist, Data data);

void LInsertFront(List *plist, Data data);

int LFirst(List *plist, Data *pdata);

int LNext(List *plist, Data *pdata);

Data LRemove(List *plist);

int LCount(List *plist);

#endif
```

## CLinkedList.c
```c
#include <stdio.h>
#include <stdlib.h>
#include "CLInkedList.h"

void ListInit(List *plist) {
    plist->tail = NULL;
    plist->cur = NULL;
    plist->before = NULL;
    plist->numOfData = 0;
}

void LInsertFront(List *plist, Data data) {
    Node *newNode = (Node *) malloc(sizeof(Node));
    newNode->data = data;

    if (plist->tail == NULL) {
        plist->tail = newNode;
        newNode->next = newNode;
    } else {
        newNode->next = plist->tail->next;
        plist->tail->next = newNode;
    }
    (plist->numOfData)++;
};

void LInsert(List *plist, Data data) {
    Node *newNode = (Node *) malloc(sizeof(Node));
    newNode->data = data;

    if (plist->tail == NULL) {
        plist->tail = newNode;
        newNode->next = newNode;
    } else {
        newNode->next = plist->tail->next;
        plist->tail->next = newNode;
        plist->tail = newNode;
    };
    (plist->numOfData)++;
}

int LFirst(List *plist, Data *pdata) {
    if (plist->tail == NULL)
        return FALSE;

    plist->before = plist->tail;
    plist->cur = plist->tail->next;

    *pdata = plist->cur->data;
    return TRUE;
}

int LNext(List *plist, Data *pdata) {
    if (plist->tail == NULL)
        return FALSE;

    plist->before = plist->cur;
    plist->cur = plist->cur->next;

    *pdata = plist->cur->data;

    return TRUE;
}

Data LRemove(List *plist) {
    Node *rpos = plist->cur;
    Data rdata = rpos->data;

    if (rpos == plist->tail) {
        if (plist->tail == plist->tail->next)
            plist->tail = NULL;
        else
            plist->tail = plist->before;
    }

    plist->before->next = plist->cur->next;
    plist->cur = plist->before;

    free(rpos);
    (plist->numOfData)--;
    return rdata;
}

int LCount(List *plist) {
    return plist->numOfData;
}
```
