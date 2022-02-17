---
layout  : wiki
title   : 배열기반 stack
summary : 
date    : 2022-02-15 22:54:56 +0900
updated : 2022-02-17 23:21:49 +0900
tags    : 
toc     : true
public  : true
parent  : [[data-structure/index]]
latex   : false
---
* TOC
{:toc}

## 소개
- 나중에 들어간 것이 먼저 나오는 구조.
- 후입후출 방식의 자료구조, LIFO(Last-In, First-Out)구조의 자료구조.

## main.c

```c
#include <stdio.h>
#include "ArrayBaseStack.h"

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

## ArrayBaseStack.h

```c
#ifndef __AB_STACK_H__
#define __AB_STACK_H__

#define TRUE 1
#define FALSE 0
#define STACK_LEN 100

typedef int Data;

typedef struct _arrayStack {
    Data stackArr[STACK_LEN];
    int topIndex;
} ArrayStack;

typedef ArrayStack Stack;

void StackInit(Stack *pstack);

int SIsEmpty(Stack *pstack);

void SPush(Stack *pstack, Data data);

Data SPop(Stack *pstack);

Data SPeek(Stack *pstack);

#endif
```

## ArrayBaseStack.c

```c
#include <stdio.h>
#include <stdlib.h>
#include "ArrayBaseStack.h"

void StackInit(Stack *pstack) {
    pstack->topIndex = -1;
}

int SIsEmpty(Stack *pstack) {
    if (pstack->topIndex == -1)
        return TRUE;
    else
        return FALSE;
}

void SPush(Stack *pstack, Data data) {
    pstack->topIndex += 1;
    pstack->stackArr[pstack->topIndex] = data;
}

Data SPop(Stack *pstack) {
    int rIdx;

    if (SIsEmpty(pstack)) {
        printf("Stack Memory Error!");
        exit(-1);
    }

    rIdx = pstack->topIndex;
    pstack->topIndex -= 1;

    return pstack->stackArr[rIdx];
}

Data SPeek(Stack *pstack) {
    if (SIsEmpty(pstack)) {
        printf("Stack Memory Error!");
        exit(-1);
    }

    return pstack->stackArr[pstack->topIndex];
}
```
