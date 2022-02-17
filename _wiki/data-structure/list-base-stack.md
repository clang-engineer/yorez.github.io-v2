---
layout  : wiki
title   : 연결 리스트 기반 스택
summary : 
date    : 2022-02-17 14:46:56 +0900
updated : 2022-02-17 14:51:12 +0900
tags    : 
toc     : true
public  : true
parent  : [[data-structure/index]]
latex   : false
---
* TOC
{:toc}

## 연결 리스트 기반 스택

## main.c
```c
#include <stdio.h>
#include "ListBaseStack.h"

int main(void) {
    Stack stack;
    StackInit(&stack);

    SPush(&stack, 1);
    SPush(&stack, 2);
    SPush(&stack, 3);
    SPush(&stack, 4);
    SPush(&stack, 5);

    while (!SIsEmpty(&stack))
        printf("%d ", SPop(&stack));

    return 0;
}
```

## ListBaseStack.h
```c
#ifndef __LB_STACK_H__
#define __LB_STACK_H__

#define TRUE 1
#define FALSE 0

typedef int Data;

typedef struct _node {
    Data data;
    struct _node *next;
} Node;

typedef struct _listStack {
    Node *head;
} ListStack;

typedef ListStack Stack;

void StackInit(Stack *pstack);

int SIsEmpty(Stack *pstack);

void SPush(Stack *pstack, Data data);

Data SPop(Stack *pstack);

Data SPeek(Stack *pstack);

#endif
```

## ListBaseStack.c
```c
#include <stdio.h>
#include <stdlib.h>
#include "ListBaseStack.h"

void StackInit(Stack *pstack) {
    pstack->head = NULL;
}

int SIsEmpty(Stack *pstack) {
    if (pstack->head == NULL)
        return TRUE;
    else
        return FALSE;
}

void SPush(Stack *pstack, Data data) {
    Node *newNode = (Node *) malloc(sizeof(Node));

    newNode->data = data;
    newNode->next = pstack->head;

    pstack->head = newNode;
}

Data SPop(Stack *pstack) {
    Data rdata;
    Node *rnode;

    if (SIsEmpty(pstack)) {
        printf("Stack Memory Error!");
        exit(-1);
    }

    rdata = pstack->head->data;
    rnode = pstack->head;

    pstack->head = pstack->head->next;
    free(rnode);

    return rdata;
}

Data SPeek(Stack *pstack) {
    if (SIsEmpty(pstack)) {
        printf("Stack Memory Error!");
        exit(-1);
    }

    return pstack->head->data;
}
```
