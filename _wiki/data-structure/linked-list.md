---
layout  : wiki
title   : Node로 만든 연결된 리스트 자료구조
summary : 
date    : 2022-01-07 09:36:42 +0900
updated : 2022-01-07 09:47:09 +0900
tags    : 
toc     : true
public  : true
parent  : [[data-structure/index]]
latex   : false
---
* TOC
{:toc}

## Node로 연결된 리스트 자료구조 (<-> 배열)

## main.c

```c
#include <stdio.h>
#include "DLinkedList.h"

int WhoIsPrecede(int d1, int d2) {
    if(d1 < d2)
        return 0;
    else
        return 1;
}

int main(void) {

    List list;
    int data;

    ListInit(&list);

    SetSortRule(&list, WhoIsPrecede);

    LInsert(&list, 11);
    LInsert(&list, 11);
    LInsert(&list, 22);
    LInsert(&list, 22);
    LInsert(&list, 33);

    printf("현재 데이터의 수: %d\n", LCount(&list));

    if (LFirst(&list, &data)) {
        printf("%d ", data);

        while (LNext(&list, &data)) {
            printf("%d ", data);
        }
    }
    printf("\n\n");

    // 22를 가지고 있는 데이터 삭제
    if (LFirst(&list, &data)) {
        if (data == 22)
            LRemove(&list);

        while (LNext(&list, &data)) {
            if (data == 22)
                LRemove(&list);
        }
    }
    printf("현재 데이터의 수: %d\n", LCount(&list));

    if (LFirst(&list, &data)) {
        printf("%d ", data);

        while (LNext(&list, &data)) {
            printf("%d ", data);
        }
    }
    printf("\n\n");
    return 0;
}
```


## DLinkedList.h

```c
#ifndef __D_LINKED_LIST_H__
#define __D_LINKED_LIST_H__

#define TRUE 1
#define FALSE 0

typedef int LData;

typedef struct _node {
    LData data;
    struct _node *next;
} Node;

typedef struct _linkedList {
    Node *head;
    Node *cur;
    Node *before;

    int numOfData;
    int (*comp)(LData d1, LData d2);
} LinkedList;

typedef LinkedList List;

void ListInit(List *plist);
void LInsert(List *plist, LData data);
int LFirst(List *plist, LData *pdata);
int LNext(List *plist, LData *pdata);
LData LRemove(List *plist);
int LCount(List *plist);

void SetSortRule(List *plist, int (*comp)(LData d1, LData d2));
#endif
```

## DLinkedList.c

```c
#include <stdio.h>
#include <stdlib.h>
#include "DLinkedList.h"

// head에 빈노드를 할당하는 이유는 어디서든 첫번째 노드와 첫번째 노드가 아닌 노드의 crud로직을 동일하게 하기 위해
void ListInit(List *plist) {
    plist->head = (Node *) malloc(sizeof(Node));
    plist->head->next = NULL;
    plist->comp = NULL;
    plist->numOfData = 0;
}

void FInsert(List *plist, LData data) {
    Node *newNode = (Node *) malloc(sizeof(Node));
    newNode->data = data;
    newNode->next = plist->head->next;
    
    plist->head->next = newNode;
    (plist->numOfData)++;
}

void SInsert(List *plist, LData data) {
    Node *newNode = (Node *) malloc(sizeof(Node));
    Node *pred = plist->head;
    newNode->data = data;

    while (pred->next != NULL && plist->comp(data, pred->next->data) != 0) {
        pred = pred->next;
    }

    newNode->next = pred->next;
    pred->next = newNode;

    (plist->numOfData)++;
}

void LInsert(List *plist, LData data) {
    if (plist->comp == NULL)
        FInsert(plist, data);
    else
        SInsert(plist, data);
}

int LFirst(List *plist, LData *pdata) {
    if (plist->head->next == NULL)
        return FALSE;

    plist->before = plist->head;
    plist->cur = plist->head->next;

    *pdata = plist->cur->data;

    return TRUE;
}

int LNext(List *plist, LData *pdata) {
    if (plist->cur->next == NULL)
        return FALSE;

    plist->before = plist->cur;
    plist->cur = plist->cur->next;

    *pdata = plist->cur->data;
    return TRUE;
}

LData LRemove(List *plist) {
    Node *rpos = plist->cur;
    LData rdata = rpos->data;

    plist->before->next = plist->cur->next;
    plist->cur = plist->before;

    free(rpos);

    (plist->numOfData)--;
    return rdata;
}

int LCount(List *plist) {
    return plist->numOfData;
}

void SetSortRule(List *plist, int (*comp)(LData d1, LData d2)) {
    plist->comp = comp;
}
```
