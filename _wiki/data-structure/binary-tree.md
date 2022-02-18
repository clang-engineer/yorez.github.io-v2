---
layout  : wiki
title   : 이진트리
summary : 
date    : 2022-02-18 22:07:30 +0900
updated : 2022-02-18 22:12:39 +0900
tags    : 
toc     : true
public  : true
parent  : 
latex   : false
---
* TOC
{:toc}

# 소개
- 트리를 표현가기에는 배열보다 연결 리스트가 더 유연하고 용이. 연결 리스트의 구성 형태가 트리와 일치하기 때문.
- '트리가 완성된 이후부터 그 트리를 대상으로 매우 빈번한 탐색이 이루어진다'의 특징이 있을 때는 배열 기반으로 트리를 구성하는 것을 고려해볼만 하다. 

## main.c
```c
#include <stdio.h>
#include "BinaryTree.h"

int main(void) {
    BTreeNode *bt1 = MakeBTreeNode();
    BTreeNode *bt2 = MakeBTreeNode();
    BTreeNode *bt3 = MakeBTreeNode();
    BTreeNode *bt4 = MakeBTreeNode();

    SetData(bt1, 1);
    SetData(bt2, 2);
    SetData(bt3, 3);
    SetData(bt4, 4);

    MakeLeftSubTree(bt1, bt2);
    MakeRightSubTree(bt1, bt3);
    MakeLeftSubTree(bt2, bt4);

    printf("%d \n", GetData(GetLeftSubTree(bt1)));
    printf("%d \n", GetData(GetLeftSubTree(GetLeftSubTree(bt1))));

    return 0;
}
```

## BinaryTree.h
```c
#ifndef __BINARY_TREE_H__
#define __BINARY_TREE_H__

typedef int BTData;

typedef struct _bTreeNode {
    BTData data;
    struct _bTreeNode *left;
    struct _bTreeNode *right;
} BTreeNode;

BTreeNode *MakeBTreeNode(void);

BTData GetData(BTreeNode *bt);

void SetData(BTreeNode *bt, BTData data);

BTreeNode *GetLeftSubTree(BTreeNode *bt);

BTreeNode *GetRightSubTree(BTreeNode *bt);

void MakeLeftSubTree(BTreeNode *main, BTreeNode *sub);

void MakeRightSubTree(BTreeNode *main, BTreeNode *sub);

#endif
```

## BibaryTree.c
```c
#include <stdio.h>
#include <stdlib.h>
#include "BinaryTree.h"

BTreeNode *MakeBTreeNode(void) {
    BTreeNode *nd = (BTreeNode *) malloc(sizeof(BTreeNode));
    nd->left = NULL;
    nd->right = NULL;
    return nd;
}

BTData GetData(BTreeNode *bt) {
    return bt->data;
}

void SetData(BTreeNode *bt, BTData data) {
    bt->data = data;
}

BTreeNode *GetLeftSubTree(BTreeNode *bt) {
    return bt->left;
}

BTreeNode *GetRightSubTree(BTreeNode *bt) {
    return bt->right;
}

void MakeLeftSubTree(BTreeNode *main, BTreeNode *sub) {
    if (main->left != NULL)
        free(main->left);

    main->left = sub;
}

void MakeRightSubTree(BTreeNode *main, BTreeNode *sub) {
    if (main->right != NULL)
        free(main->right);

    main->right = sub;
}
```
