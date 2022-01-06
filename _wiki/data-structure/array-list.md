---
layout  : wiki
title   : 배열을 이용한 리스트
summary : 
date    : 2022-01-05 17:08:10 +0900
updated : 2022-01-06 09:07:10 +0900
tags    : 
toc     : true
public  : true
parent  : [[index/data-structure]]
latex   : false
---
* TOC
{:toc}

## main.c
```c
#include <stdio.h>
#include "ArrayList.h"

int main(void) {
    List list;
    int data;
    ListInit(&list);

    LInsert(&list, 11);
    LInsert(&list, 22);
    LInsert(&list, 33);
    LInsert(&list, 44);
    LInsert(&list, 55);

    printf("현재 데이터의 수: %d \n", LCount(&list));

    if(LFirst(&list, &data))
    {
        printf("%d ", data);

        while(LNext(&list, &data))
            printf("%d ", data);
    }

    printf("\n\n");
    return 0;
}
```

## ArrayList.h

```c
#ifndef __ARRAY_LIST_H__
#define __ARRAY_LIST_H__
#define TRUE 1
#define FALSE 0

#define LIST_LEN 100
typedef int LData;

typedef struct __ArrayList {
    LData arr[LIST_LEN];
    int numOfData;
    int curPosition;
} ArrayList;

typedef ArrayList List;

void ListInit(List *plist);
void LInsert(List *plist, LData data);
int LFirst(List *plist, LData *data);
int LNext(List *plist, LData *data);
LData LRemove(List *plist);
int LCount(List *plist);

#endif
```

## ArrayList.c

```c
#include <stdio.h>
#include "ArrayList.h"

void ListInit(List *plist) {
    (plist->numOfData) = 0;
    (plist->curPosition) = -1;
};

void LInsert(List *plist, LData data) {
    if (plist->numOfData > LIST_LEN) {
        puts("배열이 가득 찼습니다.");
        return;
    }

    plist->arr[plist->numOfData] = data;
    (plist->numOfData)++;
};

int LFirst(List *plist, LData *pdata) {
    if (plist->numOfData == 0)
        return FALSE;

    (plist->curPosition) = 0;
    *pdata = plist->arr[0];
    return TRUE;
};

int LNext(List *plist, LData *pdata) {
    if (plist->curPosition >= (plist->numOfData)-1)
        return FALSE;

    (plist->curPosition)++;

    *pdata = plist->arr[plist->curPosition];
    return TRUE;
};

LData LRemove(List *plist) {
    int rpos = plist->curPosition;
    int num = plist->numOfData;
    int i;

    LData rdata = plist->arr[rpos];

    for (i = rpos; i < num - 1; i++)
        plist->arr[i] = plist->arr[i + 1];

    (plist->numOfData)--;
    (plist->curPosition)--;

    return rdata;
};

int LCount(List *plist) {
    return plist->numOfData;
};
```
